---
description: '자세한 정보:/Zc: implicitNoexcept (암시적 예외 지정자)'
title: /Zc:implicitNoexcept(암시적 예외 지정자)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: 8c6aabe2878282b42ad0f2ce1e205ac387bd9a96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114639"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept(암시적 예외 지정자)

**/Zc: implicitNoexcept** 옵션을 지정 하면 컴파일러는 암시적 [noexcept](../../cpp/noexcept-cpp.md) exception 지정자를 컴파일러 정의 특수 멤버 함수 및 사용자 정의 소멸자 및 deallocators에 추가 합니다. 기본적으로 **/zc: implicitNoexcept** 는 ISO c + + 11 표준을 준수 하도록 설정 됩니다. 이 옵션을 해제 하면 **`noexcept`** 사용자 정의 소멸자 및 dealloacators 및 컴파일러 정의 특수 멤버 함수가 암시적으로 사용 하지 않도록 설정 됩니다.

## <a name="syntax"></a>Syntax

> **/Zc: implicitNoexcept**[ **-** ]

## <a name="remarks"></a>설명

**/Zc: implicitNoexcept** 는 ISO c + + 11 표준의 15.4 섹션을 따르도록 컴파일러에 지시 합니다. **`noexcept`** 암시적으로 선언 되거나 명시적으로 지정 된 특수 멤버 함수 (기본 생성자, 복사 생성자, 이동 생성자, 소멸자, 복사 할당 연산자 또는 이동 할당 연산자)와 각 사용자 정의 소멸자 또는 비 할당자 함수에 암시적으로 예외 지정자를 추가 합니다. 사용자 정의 비할당자에는 암시적 `noexcept(true)` 예외 지정자가 있습니다. 사용자 정의 소멸자의 경우 포함된 멤버 클래스 또는 기본 클래스에 `noexcept(true)`가 아닌 소멸자가 없는 한, 암시적 예외 지정자는 `noexcept(true)`입니다. 컴파일러에서 생성된 특수 멤버 함수의 경우 이 함수에 의해 직접 호출되는 함수는 실질적으로 `noexcept(false)`이며 암시적 예외 지정자는 `noexcept(false)`입니다. 그렇지 않은 경우 암시적 예외 지정자는 `noexcept(true)`입니다.

컴파일러는 명시적 **`noexcept`** 또는 **`throw`** 지정자 또는 특성을 사용 하 여 선언 된 함수에 대해 암시적 예외 지정자를 생성 하지 않습니다 `__declspec(nothrow)` .

기본적으로 **/zc: implicitNoexcept** 가 사용 됩니다. [/Permissive-](permissive-standards-conformance.md) 옵션은 **/zc: implicitNoexcept** 에 영향을 주지 않습니다.

**/Zc: implicitNoexcept-** 를 지정 하 여이 옵션을 사용 하지 않도록 설정 하면 컴파일러에서 암시적 예외 지정 자가 생성 되지 않습니다. 이 동작은 Visual Studio 2013와 동일 합니다 .이 경우 예외 지정 자가 없는 소멸자 및 deallocators에는 문이 있을 수 있습니다 **`throw`** . 기본적으로 **/zc: implicitNoexcept** 를 지정 하는 경우 및가 **`throw`** 암시적 지정자를 사용 하는 함수에서 런타임에 발생 하면 `noexcept(true)` 의 즉각적인 호출이 발생 `std::terminate` 하 고 예외 처리기에 대 한 일반적인 해제 동작이 보장 되지 않습니다. 이러한 상황을 확인 하기 위해 컴파일러는 [컴파일러 경고 (수준 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)를 생성 합니다. **`throw`** 가 의도적인 경우 `noexcept(false)` **/zc: implicitNoexcept-** 를 사용 하는 대신 명시적 지정자를 사용 하도록 함수 선언을 변경 하는 것이 좋습니다.

이 샘플은 **/zc: implicitNoexcept** 옵션을 설정 하거나 해제할 때 명시적 예외 지정 자가 없는 사용자 정의 소멸자가 작동 하는 방법을 보여 줍니다. 설정 시 동작을 표시 하려면를 사용 하 여 컴파일합니다 `cl /EHsc /W4 implicitNoexcept.cpp` . 사용 하지 않도록 설정 된 경우 동작을 표시 하려면를 사용 하 여 컴파일합니다 `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` .

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

기본 설정인 **/zc: implicitNoexcept** 를 사용 하 여 컴파일하면 샘플에서 다음과 같은 출력을 생성 합니다.

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

**/Zc: implicitNoexcept** 설정을 사용 하 여 컴파일하면 샘플이 다음 출력을 생성 합니다.

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Zc: implicitNoexcept** 또는 **/zc: implicitNoexcept** 를 포함 하도록 **추가 옵션** 속성을 수정한 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[/Zc(규칙)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[예외 사양 (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[끝나야](../../standard-library/exception-functions.md#terminate)<br/>
