---
description: '자세한 정보: 방법: PInvoke를 사용 하 여 함수 포인터 마샬링'
title: '방법: PInvoke를 사용하여 함수 포인터 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: bfe3f669cf023ed914bdccb3ae15ccafefbb49c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302584"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>방법: PInvoke를 사용하여 함수 포인터 마샬링

이 항목에서는 .NET Framework P/Invoke 기능을 사용 하 여 관리 되지 않는 함수와 상호 작용할 때 함수 포인터 대신 관리 되는 대리자를 사용 하는 방법을 설명 합니다. 그러나 Visual C++ 프로그래머는 c + + Interop 기능을 대신 사용 하는 것이 좋습니다. P/Invoke는 컴파일 타임 오류 보고 기능을 제공 하 고 형식이 안전 하지 않으며 구현 하기가 번거로울 수 있으므로이 기능을 사용 하는 것이 좋습니다. 관리 되지 않는 API가 DLL로 패키지 되 고 소스 코드를 사용할 수 없는 경우 P/Invoke는 유일한 옵션입니다. 그렇지 않으면 다음 항목을 참조 하세요.

- [C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [방법: c + + Interop를 사용 하 여 콜백 및 대리자 마샬링](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

함수 포인터를 인수로 사용 하는 관리 되지 않는 Api는 네이티브 함수 포인터 대신 관리 되는 대리자를 사용 하 여 관리 코드에서 호출할 수 있습니다. 컴파일러는 대리자를 관리 되지 않는 함수에 대 한 함수 포인터로 자동으로 마샬링하고 필요한 관리 되는/관리 되지 않는 전환 코드를 삽입 합니다.

## <a name="example"></a>예제

다음 코드는 관리 되지 않는 및 관리 모듈로 구성 됩니다. 관리 되지 않는 모듈은 함수 포인터를 허용 하는 TakesCallback 이라는 함수를 정의 하는 DLL입니다. 이 주소는 함수를 실행 하는 데 사용 됩니다.

관리 되는 모듈은 네이티브 코드에 함수 포인터로 마샬링되는 대리자를 정의 하 고 특성을 사용 하 여 <xref:System.Runtime.InteropServices.DllImportAttribute> 네이티브 TakesCallback 함수를 관리 코드에 노출 합니다. Main 함수에서 대리자의 인스턴스가 만들어지고 TakesCallback 함수에 전달 됩니다. Program output은 네이티브 TakesCallback 함수에서이 함수를 실행 하는 것을 보여 줍니다.

관리 되는 함수는 네이티브 함수가 실행 되는 동안 가비지 수집이 대리자를 재배치할 .NET Framework 수 없도록 관리 되는 대리자에 대 한 가비지 수집을 억제 합니다.

```cpp
// TraditionalDll5.cpp
// compile with: /LD /EHsc
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   /* Declare an unmanaged function type that takes two int arguments
      Note the use of __stdcall for compatibility with managed code */
   typedef int (__stdcall *CALLBACK)(int);
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);
}

int TakesCallback(CALLBACK fp, int n) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n);
}
```

```cpp
// MarshalDelegate.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

public delegate int GetTheAnswerDelegate(int);
public value struct TraditionalDLL {
   [DllImport("TraditionalDLL5.dll")]
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);
};

int GetNumber(int n) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;
   return x + n;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TraditionalDLL::TakesCallback(fp, 42);
}
```

기존 #include 지시어를 사용 하 여 관리 코드에 노출 되는 DLL 부분은 없습니다. 실제로 DLL은 런타임에만 액세스 되므로로 가져온 함수 관련 문제 <xref:System.Runtime.InteropServices.DllImportAttribute> 는 컴파일 타임에 검색 되지 않습니다.

## <a name="see-also"></a>참고 항목

[C + +에서 명시적 PInvoke 사용 (DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
