---
description: '자세한 정보: 방법: c + + Interop를 사용 하 여 콜백 및 대리자 마샬링'
title: '방법: C++ Interop를 사용하여 콜백 및 대리자 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: 4f32c1918dc3896e43a0055245877ddf4d030ade
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258218"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>방법: C++ Interop를 사용하여 콜백 및 대리자 마샬링

이 항목에서는 Visual C++를 사용 하 여 관리 코드와 비관리 코드 간의 콜백과 대리자 (관리 되는 버전의 콜백)를 마샬링하는 방법을 보여 줍니다.

다음 코드 예제에서는 관리 되는 관리 [되지 않는](../preprocessor/managed-unmanaged.md) #pragma 지시문을 사용 하 여 동일한 파일에서 관리 되는 함수 및 관리 되지 않는 함수를 구현 하지만 함수는 별도의 파일에 정의 될 수도 있습니다. 관리 되지 않는 함수만 포함 하는 파일은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일할 필요가 없습니다.

## <a name="example-configure-unmanaged-api-to-trigger-managed-delegate"></a>예: 관리 되는 대리자를 트리거하기 위해 관리 되지 않는 API 구성

다음 예제에서는 관리 되는 대리자를 트리거하기 위해 관리 되지 않는 API를 구성 하는 방법을 보여 줍니다. 관리 되는 대리자가 만들어지고 interop 메서드 중 하나가 대리자의 <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A> 기본 진입점을 검색 하는 데 사용 됩니다. 그런 다음이 주소는 관리 되지 않는 함수에 전달 됩니다. 관리 되는 함수로 구현 된다는 사실에 대 한 지식 없이 호출 됩니다.

[Pin_ptr (c + +/cli)](../extensions/pin-ptr-cpp-cli.md) 를 사용 하 여 대리자를 고정 하는 것은 가능 하지만, 가비지 수집기에 의해 다시 배치 되거나 삭제 되지 않도록 하는 것을 알 수 있습니다. 중간 가비지 수집에서의 보호가 필요 하지만, 고정은 수집을 방지 하 고 재배치도 방지 하므로 필요한 것 보다 더 많은 보호를 제공 합니다.

가비지 컬렉션에 의해 대리자가 다시 배치 되는 경우에는 가장 가까이 배치 된 관리 되는 콜백에 영향을 주지 않으므로 대리자를 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 재배치할 수 있지만 삭제를 방지 하는 대리자에 대 한 참조를 추가 하는 데 사용 됩니다. Pin_ptr 대신 GCHandle를 사용 하면 관리 되는 힙의 조각화 가능성이 줄어듭니다.

```cpp
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example-function-pointer-stored-by-unmanaged-api"></a>예: 관리 되지 않는 API에 의해 저장 되는 함수 포인터

다음 예제는 이전 예제와 비슷하지만,이 경우 제공 된 함수 포인터는 관리 되지 않는 API에 의해 저장 되므로 언제 든 지 호출할 수 있으므로 임의 시간 동안 가비지 수집이 억제 되어야 합니다. 따라서 다음 예제에서는의 전역 인스턴스를 사용 하 여 <xref:System.Runtime.InteropServices.GCHandle> 함수 범위와는 독립적으로 대리자의 재배치를 방지 합니다. 첫 번째 예제에서 설명한 것 처럼 이러한 예제에서는 pin_ptr을 사용 하지 않아도 되지만,이 경우에는 pin_ptr 범위가 단일 함수로 제한 되기 때문에이 경우에는 작동 하지 않습니다.

```cpp
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
