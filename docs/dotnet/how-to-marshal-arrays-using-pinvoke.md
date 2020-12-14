---
description: '자세한 정보: 방법: PInvoke를 사용 하 여 배열 마샬링'
title: '방법: PInvoke를 사용하여 배열 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
ms.openlocfilehash: 90fd7b2cbefe2fb3621f512d49fbc088240922a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258227"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>방법: PInvoke를 사용하여 배열 마샬링

이 항목에서는 <xref:System.String> .NET Framework 플랫폼 호출을 사용 하 여 CLR 문자열 형식을 사용 하 여 C 스타일 문자열을 허용 하는 네이티브 함수를 호출할 수 있는 방법에 대해 설명 합니다. Visual C++ 프로그래머는 c + + Interop 기능을 대신 사용 하는 것이 좋습니다 (가능한 경우). P/Invoke는 컴파일 타임 오류 보고 기능을 제공 하 고 형식이 안전 하지 않으며 구현 하기가 번거로울 수 있기 때문입니다. 관리 되지 않는 API가 DLL로 패키지 되 고 소스 코드를 사용할 수 없는 경우 P/Invoke는 유일한 옵션입니다 (그렇지 않으면 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)참조).

## <a name="example"></a>예제

네이티브 및 관리 되는 배열이 메모리에서 다르게 배치 되기 때문에 관리 되는/관리 되지 않는 경계에서 성공적으로 전달 하려면 변환이 나 마샬링이 필요 합니다. 이 항목에서는 단순 (blitable) 항목 배열을 관리 코드에서 네이티브 함수에 전달 하는 방법을 보여 줍니다.

일반적으로 관리 되는/관리 되지 않는 데이터 마샬링과 마찬가지로 <xref:System.Runtime.InteropServices.DllImportAttribute> 특성은 사용할 각 네이티브 함수에 대 한 관리 되는 진입점을 만드는 데 사용 됩니다. 배열을 인수로 사용 하는 함수의 경우 특성을 사용 하 여 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 데이터가 마샬링되는 방법을 컴파일러에 지정 해야 합니다. 다음 예제에서는 열거형을 사용 하 여 관리 되는 <xref:System.Runtime.InteropServices.UnmanagedType> 배열이 C 스타일 배열로 마샬링되는 것을 표시 합니다.

다음 코드는 관리 되지 않는 및 관리 모듈로 구성 됩니다. 관리 되지 않는 모듈은 정수 배열을 허용 하는 함수를 정의 하는 DLL입니다. 두 번째 모듈은이 함수를 가져오는 관리 되는 명령줄 응용 프로그램이 며,이 함수를 관리 되는 배열 측면에서 정의 하 고, 특성을 사용 하 여를 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 호출할 때 배열을 네이티브 배열로 변환 하도록 지정 합니다.

관리 되는 모듈은/clr을 사용 하 여 컴파일됩니다.

```cpp
// TraditionalDll4.cpp
// compile with: /LD /EHsc
#include <iostream>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);
}

void TakesAnArray(int len, int a[]) {
   printf_s("[unmanaged]\n");
   for (int i=0; i<len; i++)
      printf("%d = %d\n", i, a[i]);
}
```

```cpp
// MarshalBlitArray.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL {
   [DllImport("TraditionalDLL4.dll")]
   static public void TakesAnArray(
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);
};

int main() {
   array<int>^ b = gcnew array<int>(3);
   b[0] = 11;
   b[1] = 33;
   b[2] = 55;
   TraditionalDLL::TakesAnArray(3, b);

   Console::WriteLine("[managed]");
   for (int i=0; i<3; i++)
      Console::WriteLine("{0} = {1}", i, b[i]);
}
```

기존 #include 지시문을 통해 관리 코드에 노출 되는 DLL 부분은 없습니다. 실제로 DLL은 런타임에만 액세스 되기 때문에로 가져온 함수와 관련 된 문제 <xref:System.Runtime.InteropServices.DllImportAttribute> 는 컴파일 타임에 검색 되지 않습니다.

## <a name="see-also"></a>참고 항목

[C + +에서 명시적 PInvoke 사용 (DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
