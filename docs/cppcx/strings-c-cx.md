---
description: '다음에 대 한 자세한 정보: 문자열 (c + +/CX)'
title: 문자열(C++/CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: 83ea4cd86b57e8bfd81968cbb617b7b8af81b978
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307615"
---
# <a name="strings-ccx"></a>문자열(C++/CX)

Windows 런타임 텍스트는 [Platform:: String 클래스](../cppcx/platform-string-class.md)에 의해 c + +/cx로 표시 됩니다. `Platform::String Class`Windows 런타임 클래스에서 메서드로 앞뒤로 전달 하거나 ABI (응용 프로그램 이진 인터페이스) 경계에서 다른 Windows 런타임 구성 요소와 상호 작용할 때를 사용 합니다. `Platform::String Class` 는 몇 가지 일반적인 문자열 작업에 대한 메서드를 제공하지만 완전한 기능의 문자열 클래스로 설계되지 않았습니다. C++ 모듈에서는 중요한 텍스트 처리에 [wstring](../standard-library/basic-string-class.md) 과 같은 표준 C++ 문자열 형식을 사용한 다음 최종 결과를 공용 인터페이스로 전달하거나 공용 인터페이스로부터 전달받기 전에 [Platform::String^](../cppcx/platform-string-class.md) 으로 변환합니다. `wstring` 또는 `wchar_t*` 와 `Platform::String`간의 변환은 쉽고 효율적입니다.

**빠른 전달**

경우에 따라 컴파일러는 `Platform::String` 을 안전하게 생성하거나 내부 문자열 데이터를 복사하지 않고 `String` 을 함수에 전달할 수 있는지 확인할 수 있습니다. 이러한 작업을 *빠른 전달* 이라고 하며 투명하게 발생합니다.

## <a name="string-construction"></a>문자열 생성

`String` 개체의 값은 `char16` (16비트 유니코드) 문자의 변경할 수 없는(읽기 전용) 시퀀스입니다. `String` 개체는 변경할 수 없으므로 `String` 변수에 새 문자열 리터럴을 할당하면 실제로는 원래 `String` 개체를 새 `String` 개체로 대체하는 것입니다. 연결 연산 작업은 원래 `String` 개체 제거 및 새 개체 생성으로 구성됩니다.

**리터럴**

*리터럴 문자* 는 작은따옴표로 묶인 문자이며, *리터럴 문자열* 은 큰따옴표로 묶인 문자 시퀀스입니다. 리터럴을 사용하여 String^ 변수를 초기화하면 컴파일러는 리터럴이 `char16` 문자로 구성되어 있다고 간주합니다. 즉, 리터럴 앞에 'L' 문자열 한정자가 오거나 리터럴을 **_T()** 또는 **TEXT()** 매크로로 묶을 필요가 없습니다. 유니코드에 대한 C++ 지원에 대한 자세한 내용은 [Unicode Programming Summary](../text/unicode-programming-summary.md)을 참조하세요.

다음 예제에서는 `String` 개체를 생성하는 여러 가지 방법을 보여 줍니다.

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>문자열 처리 작업

`String` 클래스는 연결 연산, 문자열 비교 및 기타 기본 문자열 작업을 위한 메서드 및 연산자를 제공합니다. 더욱 광범위한 문자열 조작을 수행하려면 `String::Data()` 멤버 함수를 사용하여 `String^` 개체의 값을 `const wchar_t*`로 검색하세요. 그런 다음 해당 값을 사용하여 다양한 문자열 처리 함수를 제공하는 `std::wstring`을 초기화합니다.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>문자열 변환

`Platform::String` 에는 `char16` 문자 또는 `NULL` 문자만 포함될 수 있습니다. 응용 프로그램이 8 비트 문자로 작업 해야 하는 경우 [문자열::D ata](../cppcx/platform-string-class.md#data) 를 사용 하 여 텍스트를로 추출 `const wchar_t*` 합니다. 그런 다음 적절한 Windows 함수 또는 표준 라이브러리 함수를 사용하여 데이터에 대해 작업을 수행하고 다시 `wchar_t*` 또는 [wstring](../standard-library/basic-string-class.md)으로 변환하여 새로운 `Platform::String`에 표시됩니다.

다음 코드 조각에서는 `String^` 변수와 `wstring` 변수 간에 변환하는 방법을 보여 줍니다. 이 예제에서 사용하는 문자열 조작에 대한 자세한 내용은 [basic_string::replace](../standard-library/basic-string-class.md#replace)를 참조하세요.

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>문자열 길이 및 포함된 NULL 값

[String:: Length](../cppcx/platform-string-class.md#length) 는 바이트 수가 아니라 문자열의 문자 수를 반환 합니다. 스택 의미 체계를 사용하여 문자열을 생성할 때 명시적으로 지정하지 않는 한 NULL 종결 문자는 계산되지 않습니다.

`Platform::String` 에는 포함된 NULL 값이 있을 수 있지만 NULL이 연결 연산 작업의 결과일 경우에만 가능합니다. 문자열 리터럴에서는 포함된 NULL이 지원되지 않으므로 포함된 NULL을 이러한 방식으로 사용하여 `Platform::String`을 초기화할 수 없습니다. 예를 들어 `Platform::String` 에 포함된 NULL 값이 `TextBlock::Text` 속성에 할당된 경우 문자열이 표시될 때 무시됩니다. 문자열 값이 `Data` 속성을 사용하여 반환되는 경우 포함된 NULL이 제거됩니다.

## <a name="stringreference"></a>StringReference

경우에 따라 코드 (a)가 std:: wstring 또는 wchar_t string 또는 L "" 문자열 리터럴을 수신 하 고 String ^을 입력 매개 변수로 사용 하는 다른 메서드에 전달 하기만 하면 됩니다. 원본 문자열 버퍼 자신이 유효한 상태로 유지되고 함수가 반환하기 전에 변경되지 않는 한 `wchar_t*` 문자열 또는 [Platform::StringReference](../cppcx/platform-stringreference-class.md)에 대한 문자열 리터럴을 변환할 수 있으며, `Platform::String^`대신 이 문자열 또는 문자열 리터럴을 전달합니다. 이는 `StringReference` 에 `Platform::String^`에 대한 사용자 정의 변환이 있기 때문에 허용됩니다. `StringReference` 를 사용하여 문자열 데이터의 추가 복사본을 만들지 못하게 할 수 있습니다. 많은 수의 문자열을 전달하는 루프에서나 매우 큰 문자열을 전달하는 경우 `StringReference`를 사용하여 잠재적으로 성능이 크게 향상될 수 있습니다. 그러나 `StringReference` 가 기본적으로 원본 문자열 버퍼를 빌리기 때문에 메모리 손상을 방지하려면 상당한 주의를 기울여야 합니다. 비동기 메서드가 반환될 때 원본 문자열이 범위 내에 있음이 보장되지 않는 한 `StringReference` 를 비동기 메서드에 전달해서는 안 됩니다. StringReference에서 초기화된 String^는 두 번째 할당 작업이 발생한 경우 문자열 데이터의 할당 및 복사본 생성을 강제로 수행합니다. 이 경우 `StringReference`의 성능 이점을 잃게 됩니다.

`StringReference` 는 ref 클래스가 아닌 표준 C++ 클래스 형식이며 사용자가 정의한 ref 클래스의 공용 인터페이스에서 사용할 수 없습니다.

다음 예제에서는 StringReference를 사용하는 방법을 보여 줍니다.

```cpp
void GetDecodedStrings(std::vector<std::wstring> strings)
{
    using namespace Windows::Security::Cryptography;
    using namespace Windows::Storage::Streams;

    for (auto&& s : strings)
    {
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)
        // Call using StringReference:
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));

        //...do something with buffer
    }
}
```
