---
title: '방법: C++ Interop를 사용하여 ANSI 문자열 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: 3bdffa761bef74b9956842122b913e8213c736e9
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414570"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>방법: C++ Interop를 사용하여 ANSI 문자열 마샬링

이 항목에서는 c + + Interop를 사용 하 여 ANSI 문자열을 전달 하는 방법을 보여 주지만 .NET Framework는 <xref:System.String> 유니코드 형식의 문자열을 나타내므로 ansi로의 변환은 추가 단계입니다. 다른 문자열 형식과의 상호 운용을 위해 다음 항목을 참조 하십시오.

- [방법: c + + Interop를 사용 하 여 유니코드 문자열 마샬링](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 COM 문자열 마샬링](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

다음 코드 예제에서는 관리 되는 관리 [되지 않는](../preprocessor/managed-unmanaged.md) #pragma 지시문을 사용 하 여 동일한 파일에서 관리 되는 함수 및 관리 되지 않는 함수를 구현 하지만 이러한 함수는 별도의 파일에 정의 된 경우와 동일한 방식으로 상호 운용 됩니다 관리 되지 않는 함수만 포함 하는 파일은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일할 필요가 없기 때문에 성능 특성을 유지할 수 있습니다.

## <a name="example-pass-ansi-string"></a>예: ANSI 문자열 전달

이 예제에서는를 사용 하 여 관리 되는에서 관리 되지 않는 함수로 ANSI 문자열을 전달 하는 방법을 보여 줍니다 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> . 이 메서드는 관리 되지 않는 힙에서 메모리를 할당 하 고 변환을 수행한 후 주소를 반환 합니다. 즉, GC 힙의 메모리가 관리 되지 않는 함수로 전달 되지 않기 때문에 고정이 필요 하지 않으며에서 반환 된 IntPtr이 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 명시적으로 해제 되거나 메모리 누수가 발생 합니다.

```cpp
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example-data-marshaling-required-to-access-ansi-string"></a>예: ANSI 문자열에 액세스 하는 데 필요한 데이터 마샬링

다음 예제에서는 관리 되지 않는 함수에서 호출 하는 관리 되는 함수의 ANSI 문자열에 액세스 하는 데 필요한 데이터 마샬링을 보여 줍니다. 네이티브 문자열을 수신 하는 관리 되는 함수는 표시 된 것 처럼 메서드를 사용 하 여 직접 사용 하거나 관리 되는 문자열로 변환할 수 있습니다 <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> .

```cpp
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
