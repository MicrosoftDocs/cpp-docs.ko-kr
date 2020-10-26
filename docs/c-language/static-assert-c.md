---
title: _Static_assert 키워드 및 static_assert 매크로(C11)
description: C11 _Static_assert 키워드와 C11 static_assert 매크로를 설명합니다.
ms.date: 10/13/2020
f1_keywords:
- static_assert_c
- _Static_assert
helpviewer_keywords:
- assertions [C], _Static_assert, static_assert
ms.openlocfilehash: dbe49b1dcbb8dd4e0d9df678f4456bc605e01c3f
ms.sourcegitcommit: 651348f8cd92ab0d52f09e9225a7eb41562559db
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92060980"
---
# <a name="_static_assert-keyword-and-static_assert-macro-c11"></a>_Static_assert 키워드 및 static_assert 매크로(C11)

컴파일 시간에 어설션을 테스트합니다. 지정된 상수 식이 **`false`** 인 경우 컴파일러는 지정된 메시지를 표시하고 컴파일은 C2338 오류와 함께 실패합니다. 그렇지 않을 경우 영향이 없습니다. C11의 새로운 기능입니다.

**`_Static_assert`** 는 C11에 도입된 키워드입니다.
**`static_assert`** 는 C11에 도입된 것으로, **`_Static_assert`** 키워드에 매핑되는 매크로입니다.

## <a name="syntax"></a>구문

```C
_Static_assert(constant-expression, string-literal);
static_assert(constant-expression, string-literal);
```

### <a name="parameters"></a>매개 변수

*constant-expression*\
컴파일 시간에 계산될 수 있는 정수 계열 상수 식입니다. 계산된 식이 0이면(false) *string-literal* 매개 변수가 표시되고 컴파일이 오류와 함께 실패합니다. 식이 0이 아니면(true) 영향이 없습니다.

*string-literal*\
*constant-expression* 이 0으로 계산되는 경우(false) 메시지가 표시됩니다. 컴파일러의 [기본 문자 집합](../c-language/ascii-character-set.md)을 사용하여 메시지를 작성해야 합니다. 문자는 [멀티바이트 또는 와이드 문자](../c-language/multibyte-and-wide-characters.md)일 수 없습니다.

## <a name="remarks"></a>설명

**`_Static_assert`** 키워드와 **`static_assert`** 매크로는 모두 컴파일 시간에 소프트웨어 어설션을 테스트합니다. 전역 또는 함수 범위에서 사용할 수 있습니다.

이와 대조적으로 [assert 매크로와 _assert 및 _wassert 함수](../c-runtime-library/reference/assert-macro-assert-wassert.md)는 런타임 시 소프트웨어 어설션을 테스트하고 런타임 비용을 발생시킵니다.

**Microsoft 전용 동작**

C에서 `<assert.h>`를 포함하지 않는 경우 Microsoft Visual C/C++ 컴파일러는 **`static_assert`** 를 **`_Static_assert`** 에 매핑되는 키워드로 처리합니다. 동일한 코드가 C와 C++ 모두에서 작동하기 때문에 **`static_assert`** 를 사용하는 것이 좋습니다.

## <a name="example-of-a-compile-time-assert"></a>컴파일 시간 어설션의 예

다음 예제에서는 **`static_assert`** 및 **`_Static_assert`** 를 사용하여 열거형에 있는 요소의 수를 확인하고 해당 정수를 32비트 너비로 확인합니다.

```C
// requires /std:c11 or higher
#include <assert.h>

enum Items
{
    A,
    B,
    C,
    LENGTH
};

int main()
{
    // _Static_assert is a C11 keyword
    _Static_assert(LENGTH == 3, "Expected Items enum to have three elements");

    // Preferred: static_assert maps to _Static_Assert and is compatible with C++
    static_assert(sizeof(int) == 4, "Expecting 32 bit integers"); 

    return 0;
}
```

## <a name="requirements"></a>요구 사항

|매크로|필수 헤더|
|-------------|---------------------|
|**`static_assert`**|\<assert.h>|

## <a name="see-also"></a>참고 항목

[_STATIC_ASSERT 매크로](../c-runtime-library/reference/static-assert-macro.md)\
[assert 매크로와 _assert 및 _wassert 함수](../c-runtime-library/reference/assert-macro-assert-wassert.md)
[/std(언어 표준 버전 지정)](../build/reference/std-specify-language-standard-version.md)