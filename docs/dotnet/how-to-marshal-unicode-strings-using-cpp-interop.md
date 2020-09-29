---
title: '방법: C++ Interop를 사용하여 유니코드 문자열 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: da320dbd41e7158e3bc2482b96a73c1f4728a01b
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414310"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>방법: C++ Interop를 사용하여 유니코드 문자열 마샬링

이 항목에서는 Visual C++ 상호 운용성의 한 패싯을 보여 줍니다. 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)을 참조 하세요.

다음 코드 예제에서는 관리 되는 관리 [되지 않는](../preprocessor/managed-unmanaged.md) #pragma 지시문을 사용 하 여 동일한 파일에서 관리 되는 함수 및 관리 되지 않는 함수를 구현 하지만 이러한 함수는 별도의 파일에 정의 된 경우와 동일한 방식으로 상호 운용 됩니다 관리 되지 않는 함수만 포함 하는 파일은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일할 필요가 없습니다.

이 항목에서는 관리 되는 함수에서 관리 되지 않는 함수로 유니코드 문자열을 전달 하는 방법 및 그 반대로를 전달 하는 방법을 보여 줍니다. 다른 문자열 형식과의 상호 운용을 위해 다음 항목을 참조 하십시오.

- [방법: c + + Interop를 사용 하 여 ANSI 문자열 마샬링](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 COM 문자열 마샬링](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example-pass-unicode-string-from-managed-to-unmanaged-function"></a>예: 관리 되는 함수에서 관리 되지 않는 함수로 유니코드 문자열 전달

관리 되는 함수에서 관리 되지 않는 함수로 유니코드 문자열을 전달 하기 위해 PtrToStringChars 함수 (Vcclr에 선언 됨)를 사용 하 여 관리 되는 문자열이 저장 된 메모리에서에 액세스할 수 있습니다. 이 주소는 네이티브 함수에 전달 되기 때문에 관리 되지 않는 함수가 실행 되는 동안 가비지 수집 주기가 발생 해야 하는 경우에는 [pin_ptr (c + +/cli)](../extensions/pin-ptr-cpp-cli.md) 를 사용 하 여 메모리를 고정 해야 합니다.

```cpp
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example-data-marshaling-required-to-access-unicode-string"></a>예: 유니코드 문자열에 액세스 하는 데 필요한 데이터 마샬링

다음 예제에서는 관리 되지 않는 함수에서 호출 하는 관리 되는 함수의 유니코드 문자열에 액세스 하는 데 필요한 데이터 마샬링을 보여 줍니다. 관리 되는 함수는 네이티브 유니코드 문자열을 받을 때 메서드를 사용 하 여 관리 되는 문자열로 변환 합니다 <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> .

```cpp
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
