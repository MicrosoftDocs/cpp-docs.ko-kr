---
description: '자세한 정보: 관리 코드에서 네이티브 함수 호출'
title: 관리 코드에서 네이티브 함수 호출
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: b037027f863ff12ac83429715cdf50bff4549a93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282538"
---
# <a name="calling-native-functions-from-managed-code"></a>관리 코드에서 네이티브 함수 호출

공용 언어 런타임에서는 관리 코드에서 네이티브 Dll (동적 연결 라이브러리)의 C 스타일 함수를 호출할 수 있도록 하는 플랫폼 호출 서비스 또는 PInvoke를 제공 합니다. 런타임과의 COM 상호 운용성과 "It만 작동" 또는 IJW, 메커니즘과 동일한 데이터 마샬링이 사용 됩니다.

자세한 내용은 다음을 참조하세요.

- [C + +에서 명시적 PInvoke 사용 (DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

이 단원의 샘플에서는를 사용 하는 방법을 보여 줍니다 `PInvoke` . `PInvoke` 는 프로시저 마샬링 코드를 작성 하는 대신 특성에서 마샬링 정보를 선언적으로 제공 하므로 사용자 지정 된 데이터 마샬링을 간소화할 수 있습니다.

> [!NOTE]
> 마샬링 라이브러리는 최적화 된 방식으로 네이티브 및 관리 되는 환경 간에 데이터를 마샬링하는 대체 방법을 제공 합니다. 마샬링 라이브러리에 대 한 자세한 내용은 [c + +의 마샬링 개요](../dotnet/overview-of-marshaling-in-cpp.md) 를 참조 하세요. 마샬링 라이브러리는 함수에 대 한 것이 아니라 데이터에만 사용할 수 있습니다.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 및 DllImport 특성

다음 예에서는 Visual C++ 프로그램에서를 사용 하는 방법을 보여 줍니다 `PInvoke` . 네이티브 함수 put은 msvcrt.dll에서 정의 됩니다. DllImport 특성은 put의 선언에 사용 됩니다.

```cpp
// platform_invocation_services.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", CharSet=CharSet::Ansi)]
extern "C" int puts(String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

다음 샘플은 이전 샘플과 동일 하지만 IJW를 사용 합니다.

```cpp
// platform_invocation_services_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <stdio.h>

int main() {
   String ^ pStr = "Hello World!";
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();
   puts(pChars);

   Marshal::FreeHGlobal((IntPtr)pChars);
}
```

### <a name="advantages-of-ijw"></a>IJW의 장점

- `DLLImport`프로그램에서 사용 하는 관리 되지 않는 api에 대 한 특성 선언을 작성할 필요가 없습니다. 헤더 파일을 포함 하 고 가져오기 라이브러리에 연결 합니다.

- IJW 메커니즘은 약간 더 빠릅니다. 예를 들어, IJW 스텁은 개발자가 명시적으로 수행 하므로 데이터 항목을 고정 하거나 복사 해야 하는지 확인할 필요가 없습니다.

- 성능 문제를 명확 하 게 보여 줍니다. 이 경우에는 유니코드 문자열에서 ANSI 문자열로 변환 하 고 수행자 메모리 할당 및 할당 취소를 사용할 수 있습니다. 이 경우 IJW를 사용 하 여 코드를 작성 하는 개발자는를 호출 하 고를 사용 하는 것이 성능을 향상 시키는 것을 알 `_putws` `PtrToStringChars` 수 있습니다.

- 동일한 데이터를 사용 하 여 여러 관리 되지 않는 Api를 호출 하는 경우 한 번 마샬링하고 마샬링된 복사본을 전달 하는 것이 매번 다시 마샬링하는 것 보다 훨씬 더 효율적입니다.

### <a name="disadvantages-of-ijw"></a>IJW의 단점

- 마샬링은 일반적으로 적절 한 기본값이 있는 특성이 아닌 코드에서 명시적으로 지정 해야 합니다.

- 마샬링 코드는 응용 프로그램 논리의 흐름에서 더 침입 하는 인라인 코드입니다.

- 명시적 마샬링 Api는 `IntPtr` 32 비트의 64 비트 이식성에 대 한 형식을 반환 하므로 추가 호출을 사용 해야 합니다 `ToPointer` .

C + +에서 제공 하는 특정 메서드는 더 효율적이 고 명시적인 방법으로, 몇 가지 복잡성이 있습니다.

응용 프로그램에서 주로 관리 되지 않는 데이터 형식을 사용 하거나 .NET Framework Api 보다 더 관리 되지 않는 Api를 호출 하는 경우에는 IJW 기능을 사용 하는 것이 좋습니다. 대부분의 관리 되는 응용 프로그램에서 때때로 관리 되지 않는 API를 호출 하려면 더 미묘한 선택이 있습니다.

## <a name="pinvoke-with-windows-apis"></a>Windows Api를 사용 하는 PInvoke

PInvoke는 Windows에서 함수를 호출 하는 데 편리 합니다.

이 예제에서 Visual C++ 프로그램은 Win32 API의 일부인 MessageBox 함수와 상호 작용 합니다.

```cpp
// platform_invocation_services_4.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
typedef void* HWND;
[DllImport("user32", CharSet=CharSet::Ansi)]
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);

int main() {
   String ^ pText = "Hello World! ";
   String ^ pCaption = "PInvoke Test";
   MessageBox(0, pText, pCaption, 0);
}
```

출력은 제목 PInvoke 테스트를 포함 하 고 Hello World! 텍스트를 포함 하는 메시지 상자입니다.

마샬링 정보는 PInvoke에서 DLL의 함수를 조회 하는 데도 사용 됩니다. user32.dll 실제로 MessageBox 함수는 없지만 CharSet = CharSet:: Ansi를 사용 하면 PInvoke에서 유니코드 버전인 Messageboxa 대신 ANSI 버전을 사용할 수 있습니다. 일반적으로 유니코드 버전의 관리 되지 않는 Api를 사용 하는 것이 좋습니다. 이렇게 하면 .NET Framework string 개체의 네이티브 유니코드 형식에서 ANSI로 변환 오버 헤드가 발생 하지 않습니다.

## <a name="when-not-to-use-pinvoke"></a>PInvoke를 사용 하지 않는 경우

Ddl의 모든 C 스타일 함수에는 PInvoke를 사용 하지 않는 것이 좋습니다. 예를 들어 다음과 같이 선언 된 mylib.dll MakeSpecial 함수가 있다고 가정 합니다.

`char * MakeSpecial(char * pszString);`

Visual C++ 응용 프로그램에서 PInvoke를 사용 하는 경우 다음과 유사한 항목을 작성할 수 있습니다.

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

여기에서 어려움은 MakeSpecial에서 반환 하는 관리 되지 않는 문자열에 대 한 메모리를 삭제할 수 없다는 점입니다. PInvoke를 통해 호출 되는 다른 함수는 사용자가 할당 취소할 필요가 없는 내부 버퍼에 대 한 포인터를 반환 합니다. 이 경우에는 IJW 기능을 사용 하는 것이 좋습니다.

## <a name="limitations-of-pinvoke"></a>PInvoke의 제한 사항

매개 변수로 사용한 네이티브 함수에서 동일한 정확한 포인터를 반환할 수 없습니다. 네이티브 함수가 PInvoke에 의해 마샬링되는 포인터를 반환 하는 경우 메모리 손상 및 예외가 뒤따르게 수 있습니다.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

다음 샘플에서는이 문제를 보여 줍니다. 프로그램이 올바른 출력을 제공 하는 것 처럼 보이는 경우에도 출력은 해제 된 메모리에서 제공 됩니다.

```cpp
// platform_invocation_services_5.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
#include <limits.h>

ref struct MyPInvokeWrap {
public:
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]
   static String^ CharLower([In, Out] String ^);
};

int main() {
   String ^ strout = "AabCc";
   Console::WriteLine(strout);
   strout = MyPInvokeWrap::CharLower(strout);
   Console::WriteLine(strout);
}
```

## <a name="marshaling-arguments"></a>마샬링 인수

`PInvoke`에서는 동일한 형식의 관리 되는 네이티브 기본 형식과 c + + 네이티브 기본 형식 간에 마샬링이 필요 하지 않습니다. 예를 들어 Int32와 int 또는 Double과 double 사이에는 마샬링이 필요 하지 않습니다.

그러나 형식이 다른 형식을 마샬링해야 합니다. 여기에는 char, string 및 struct 형식이 포함 됩니다. 다음 표에서는 마샬러에서 다양 한 형식에 사용 하는 매핑을 보여 줍니다.

|wtypes .h|Visual C++|/Clr을 사용 하 여 Visual C++|공용 언어 런타임|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|void \*|void \*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|SHORT|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|부호 없는 정수|부호 없는 정수|UInt32|
|LONG|long|long|Int32|
|BOOL|long|bool|부울|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPSTR|문자가 \*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const 문자 \*|문자열 ^|String|
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|const wchar_t \*|문자열 ^|String|
|FLOAT|float|float|Single|
|DOUBLE|double|double|Double|

마샬러는 해당 주소가 관리 되지 않는 함수에 전달 되는 경우 런타임 힙에 할당 된 메모리를 자동으로 고정 합니다. 고정은 가비지 수집기가 압축 중에 할당 된 메모리 블록을 이동 하지 않도록 합니다.

이 항목의 앞부분에 나와 있는 예제에서 DllImport의 CharSet 매개 변수는 관리 되는 문자열을 마샬링하는 방법을 지정 합니다. 이 경우 네이티브 쪽의 ANSI 문자열로 마샬링됩니다.

MarshalAs 특성을 사용 하 여 네이티브 함수의 개별 인수에 대 한 마샬링 정보를 지정할 수 있습니다. 문자열 인수를 마샬링하는 데는 \* BStr, ANSIBStr, TBStr, LPStr, LPWStr 및 LPTStr 등의 여러 가지 옵션을 사용할 수 있습니다. 기본값은 LPStr입니다.

이 예제에서 문자열은 더블 바이트 유니코드 문자열 LPWStr로 마샬링됩니다. 출력은 Hello World의 첫 글자입니다. 마샬링된 문자열의 두 번째 바이트가 null 이기 때문에가이를 문자열 끝 표식으로 해석 합니다.

```cpp
// platform_invocation_services_3.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", EntryPoint="puts")]
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

MarshalAs 특성은 System:: Runtime:: T e m 네임 스페이스에 있습니다. 특성은 배열과 같은 다른 데이터 형식과 함께 사용할 수 있습니다.

이 항목의 앞부분에서 설명한 것 처럼 마샬링 라이브러리는 네이티브 및 관리 되는 환경 간에 데이터를 마샬링하는 새로운 최적화 된 방법을 제공 합니다. 자세한 내용은 [c + +의 마샬링 개요](../dotnet/overview-of-marshaling-in-cpp.md)를 참조 하세요.

## <a name="performance-considerations"></a>성능 고려 사항

PInvoke에는 호출 당 x86 명령 10 ~ 30 개 사이에서 오버 헤드가 발생 합니다. 이 고정 비용 외에도 마샬링은 추가 오버 헤드를 생성 합니다. 관리 코드와 비관리 코드에서 동일한 표현이 있는 blittable 형식 간의 마샬링 비용은 없습니다. 예를 들어 int와 Int32 사이에서 변환할 비용이 없습니다.

성능 향상을 위해, 호출 당 더 작은 데이터를 마샬링하는 더 많은 호출 대신 최대한 많은 데이터를 마샬링하는 PInvoke 호출 수가 줄어듭니다.

## <a name="see-also"></a>참고 항목

[네이티브 및 .NET 상호 운용성](../dotnet/native-and-dotnet-interoperability.md)
