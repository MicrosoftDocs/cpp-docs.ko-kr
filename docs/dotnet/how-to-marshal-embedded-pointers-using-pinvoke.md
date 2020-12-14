---
description: '자세한 정보: 방법: PInvoke를 사용 하 여 포함 포인터 마샬링'
title: '방법: PInvoke를 사용하여 포함 포인터 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
ms.openlocfilehash: d31660a9a8ba345b380d442bb4484e332fe9d7cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302558"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>방법: PInvoke를 사용하여 포함 포인터 마샬링

관리 되지 않는 Dll에서 구현 되는 함수는 플랫폼 호출 (P/Invoke) 기능을 사용 하 여 관리 코드에서 호출할 수 있습니다. DLL에 대 한 소스 코드를 사용할 수 없는 경우에는 P/Invoke가 상호 운용을 위한 유일한 옵션입니다. 그러나 다른 .NET 언어와 달리 Visual C++ P/Invoke에 대 한 대안을 제공 합니다. 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) 및 [방법: c + + Interop를 사용 하 여 포함 포인터 마샬링](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)을 참조 하세요.

## <a name="example"></a>예제

구조체를 네이티브 코드에 전달 하려면 네이티브 구조에 대 한 데이터 레이아웃 측면에 해당 하는 관리 되는 구조체가 생성 되어야 합니다. 그러나 포인터를 포함 하는 구조체에는 특수 한 처리가 필요 합니다. 네이티브 구조체의 포함 된 각 포인터에 대 한 관리 되는 버전의 구조체에는 형식의 인스턴스가 포함 되어야 합니다 <xref:System.IntPtr> . 또한, 및 메서드를 사용 하 여 이러한 인스턴스에 대 한 메모리를 명시적으로 할당, 초기화 및 해제 해야 합니다 <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A> <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A> <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> .

다음 코드는 관리 되지 않는 및 관리 모듈로 구성 됩니다. 관리 되지 않는 모듈은 포인터가 포함 된 ListString 이라는 구조와 TakesListStruct 라는 함수를 정의 하는 함수를 정의 하는 DLL입니다. 관리 되는 모듈은 TakesListStruct 함수를 가져오고, double *이 인스턴스로 표시 된다는 점을 제외 하 고 네이티브 ListStruct와 동일한 MListStruct 라는 구조를 정의 하는 명령줄 응용 프로그램입니다 <xref:System.IntPtr> . TakesListStruct를 호출 하기 전에 main 함수는이 필드가 참조 하는 메모리를 할당 하 고 초기화 합니다.

```cpp
// TraditionalDll6.cpp
// compile with: /EHsc /LD
#include <stdio.h>
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct ListStruct {
   int count;
   double* item;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API void TakesListStruct(ListStruct);
}

void TakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}
```

```cpp
// EmbeddedPointerMarshalling.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MListStruct {
   int count;
   IntPtr item;
};

value struct TraditionalDLL {
    [DllImport("TraditionalDLL6.dll")]
   static public void TakesListStruct(MListStruct);
};

int main() {
   array<double>^ parray = gcnew array<double>(10);
   Console::WriteLine("[managed] count = {0}", parray->Length);

   Random^ r = gcnew Random();
   for (int i=0; i<parray->Length; i++) {
      parray[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);
   }

   int size = Marshal::SizeOf(double::typeid);
   MListStruct list;
   list.count = parray->Length;
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);

   for (int i=0; i<parray->Length; i++) {
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);
      Marshal::StructureToPtr(parray[i], t, false);
   }

   TraditionalDLL::TakesListStruct( list );
   Marshal::FreeCoTaskMem(list.item);
}
```

기존 #include 지시어를 사용 하 여 관리 코드에 노출 되는 DLL 부분은 없습니다. 실제로 DLL은 런타임에만 액세스 되므로로 가져온 함수 관련 문제 <xref:System.Runtime.InteropServices.DllImportAttribute> 는 컴파일 타임에 검색 되지 않습니다.

## <a name="see-also"></a>참고 항목

[C + +에서 명시적 PInvoke 사용 (DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
