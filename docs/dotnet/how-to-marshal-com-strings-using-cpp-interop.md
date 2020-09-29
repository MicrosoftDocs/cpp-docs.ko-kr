---
title: '방법: C++ Interop를 사용하여 COM 문자열 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: 3113f0bd04fc8433dc4c7f443914fca9245a54f4
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414336"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>방법: C++ Interop를 사용하여 COM 문자열 마샬링

이 항목에서는 BSTR (COM 프로그래밍에서 선호 되는 기본 문자열 형식)을 관리 되는 함수에서 관리 되지 않는 함수로 전달 하는 방법 및 그 반대로를 전달할 수 있는 방법을 보여 줍니다. 다른 문자열 형식과의 상호 운용을 위해 다음 항목을 참조 하십시오.

- [방법: c + + Interop를 사용 하 여 유니코드 문자열 마샬링](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 ANSI 문자열 마샬링](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

다음 코드 예제에서는 관리 되는 관리 [되지 않는](../preprocessor/managed-unmanaged.md) #pragma 지시문을 사용 하 여 동일한 파일에서 관리 되는 함수 및 관리 되지 않는 함수를 구현 하지만 이러한 함수는 별도의 파일에 정의 된 경우와 동일한 방식으로 상호 운용 됩니다 관리 되지 않는 함수만 포함 하는 파일은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일할 필요가 없습니다.

## <a name="example-pass-bstr-from-managed-to-unmanaged-function"></a>예: 관리 되는 함수에서 관리 되지 않는 함수로 BSTR 전달

다음 예제에서는 BSTR (COM 프로그래밍에서 사용 되는 문자열 형식)을 관리 되는 함수에서 관리 되지 않는 함수로 전달할 수 있는 방법을 보여 줍니다. 호출 하는 관리 되는 함수는 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 를 사용 하 여 .Net system.string의 내용에 대 한 BSTR 표현의 주소를 가져옵니다. 이 포인터는 관리 되지 않는 함수가 실행 되는 동안 가비지 수집 주기 동안 실제 주소가 변경 되지 않도록 [pin_ptr (c + +/cli)](../extensions/pin-ptr-cpp-cli.md) 를 사용 하 여 고정 됩니다. 가비지 수집기는 [pin_ptr (c + +/cli)](../extensions/pin-ptr-cpp-cli.md) 가 범위를 벗어날 때까지 메모리를 이동 하는 것이 금지 됩니다.

```cpp
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example-pass-bstr-from-unmanaged-to-managed-function"></a>예: 관리 되지 않는 함수에서 관리 되는 함수로 BSTR 전달

다음 예제에서는 BSTR을 관리 되지 않는 함수에서 관리 되는 함수로 전달 하는 방법을 보여 줍니다. 수신 관리 함수는의 문자열을 BSTR로 사용 하거나를 사용 하 여 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> <xref:System.String> 다른 관리 되는 함수와 함께 사용할 수 있습니다. BSTR을 나타내는 메모리는 관리 되지 않는 힙에 할당 되기 때문에 관리 되지 않는 힙에서 가비지 수집이 수행 되지 않으므로 고정이 필요 하지 않습니다.

```cpp
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
