---
title: /Zc:noexceptTypes(C++17 noexcept 규칙)
description: 'Microsoft c + +/Zc: noexceptTypes 컴파일러 옵션에 대 한 자세한 내용은 준수 하거나 완화 된 c + + 17 noexcept 소스 코드 호환성을 확인 하세요.'
ms.date: 06/04/2020
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: c15d4203f343eced7c112757b2665aa71a982c7c
ms.sourcegitcommit: 25f6d52eb9e5d84bd0218c46372db85572af81da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94448505"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes(C++17 noexcept 규칙)

C + + 17 표준에서는 `throw()` 에 대 한 별칭을 사용 하 고, **`noexcept`** `throw(` *`type-list`* `)` 및를 제거 하 `throw(...)` 고, 특정 형식에 포함 될 수 있습니다 **`noexcept`** . 이렇게 변경 하면 c + + 14 이전 버전을 따르는 코드에서 많은 소스 호환성 문제가 발생할 수 있습니다. **`/Zc:noexceptTypes`** 옵션은 c + + 17 표준에 대 한 준수를 지정 합니다. **`/Zc:noexceptTypes-`**  코드를 c + + 17 모드로 컴파일할 때 c + + 14 및 이전 동작을 허용 합니다.

## <a name="syntax"></a>구문

> **`/Zc:noexceptTypes`**\[**`-`** ]

## <a name="remarks"></a>설명

**`/Zc:noexceptTypes`** 옵션이 지정 된 경우 컴파일러는 c + + 17 표준을 준수 하 고 [`throw()`](../../cpp/exception-specifications-throw-cpp.md) 에 대 한 별칭으로를 처리 하 고, [`noexcept`](../../cpp/noexcept-cpp.md) `throw(` *`type-list`* `)` 및를 제거 하 `throw(...)` 고, 특정 형식에 포함 될 수 있도록 **`noexcept`** 합니다. **`/Zc:noexceptTypes`** 옵션은 [`/std:c++17`](std-specify-language-standard-version.md) 또는을 사용 하는 경우에만 사용할 수 있습니다 [`/std:c++latest`](std-specify-language-standard-version.md) . **`/Zc:noexceptTypes`** 는 ISO c + + 17 표준을 준수 하도록 기본적으로 사용 하도록 설정 되어 있습니다. 이 [`/permissive-`](permissive-standards-conformance.md) 옵션은 영향을 받지 않습니다 **`/Zc:noexceptTypes`** . **`/Zc:noexceptTypes-`** **`noexcept`** **`/std:c++17`** 또는가 지정 된 경우의 c + + 14 동작으로 되돌리려면를 지정 하 여이 옵션을 해제 **`/std:c++latest`** 합니다.

Visual Studio 2017 버전 15.5부터 c + + 컴파일러는 c + + 17 모드의 선언에서 더 일치 하지 않는 예외 사양을 진단 하거나 옵션을 지정 합니다 [`/permissive-`](permissive-standards-conformance.md) .

이 샘플에서는 **`/Zc:noexceptTypes`** 옵션을 설정 하거나 해제할 때 예외 지정자를 사용한 선언이 동작 하는 방식을 보여 줍니다. 설정 시 동작을 표시 하려면를 사용 하 여 컴파일합니다 `cl /EHsc /W4 noexceptTypes.cpp` . 사용 하지 않도록 설정 된 경우 동작을 표시 하려면를 사용 하 여 컴파일합니다 `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp` .

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

기본 설정을 사용 하 여 컴파일하면 **`/Zc:noexceptTypes`** 샘플에서 나열 된 경고가 생성 됩니다. 코드를 업데이트 하려면 대신 다음을 사용 합니다.

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 또는를 포함 하도록 **추가 옵션** 속성을 수정한 *`/Zc:noexceptTypes`* *`/Zc:noexceptTypes-`* 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참조

[`/Zc` 규칙](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[예외 사양(throw)](../../cpp/exception-specifications-throw-cpp.md)
