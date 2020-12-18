---
title: C 키워드
description: 표준 C 및 Microsoft C 컴파일러 확장의 키워드입니다.
ms.date: 12/8/2020
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.openlocfilehash: 23a701333220ca58b6e28323fb6aced156337b3f
ms.sourcegitcommit: be469dd87453255b0e35e333712c8207b09b3dd4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97412442"
---
# <a name="c-keywords"></a>C 키워드

키워드는 C 컴파일러에서 특별한 의미를 가진 단어입니다. 7번째 및 8번째 변환 단계에서는 식별자가 C 키워드와 같은 철자 및 대/소문자를 사용할 수 없습니다. 자세한 내용은 전처리기 참조의 [변환 단계](../preprocessor/phases-of-translation.md)를 참조하세요. 식별자에 대한 자세한 내용은 [식별자](../c-language/c-identifiers.md)를 참조하세요.

## <a name="standard-c-keywords"></a>표준 C 키워드

C 언어는 다음의 키워드를 사용합니다.

:::row:::
    :::column:::
        **`auto`**\
        **`break`**\
        **`case`**\
        **`char`**\
        **`const`**\
        **`continue`**\
        **`default`**\
        **`do`**\
        **`double`**\
        **`else`**\
        **`enum`**
    :::column-end:::
    :::column:::
        **`extern`**\
        **`float`**\
        **`for`**\
        **`goto`**\
        **`if`**\
        **`inline`** <sup>1, a</sup>\
        **`int`**\
        **`long`**\
        **`register`**\
        **`restrict`** <sup>1, a</sup>\
        **`return`**
    :::column-end:::
    :::column:::
        **`short`**\
        **`signed`**\
        **`sizeof`**\
        **`static`**\
        **`struct`**\
        **`switch`**\
        **`typedef`**\
        **`union`**\
        **`unsigned`**\
        **`void`**\
        **`volatile`**
    :::column-end:::
    :::column:::
        **`while`**\
        **[`_Alignas`](alignment-c.md#alignas-and-_alignas-c11)** <sup>2, a</sup>\
        **[`_Alignof`](alignment-c.md#alignof-and-_alignof-c11)** <sup>2, a</sup>\
        **`_Atomic`** <sup>2, b</sup>\
        **`_Bool`** <sup>1, a</sup>\
        **`_Complex`** <sup>1, b</sup>\
        **[`_Generic`](generic_selection.md)** <sup>2, a</sup>\
        **`_Imaginary`** <sup>1, b</sup>\
        **`_Noreturn`** <sup>2, a</sup>\
        **`_Static_assert`** <sup>2, a</sup>\
        **`_Thread_local`** <sup>2, b</sup>
    :::column-end:::
:::row-end:::

<sup>1</sup>  ISO C99에 도입된 키워드입니다.

<sup>2</sup>  ISO C11에 도입된 키워드입니다.

<sup>a</sup>  Visual Studio 2019 버전 16.8부터 **`/std:c11`** 또는 **`/std:c17`** 컴파일러 옵션이 지정된 경우 이러한 키워드가 C로 컴파일된 코드에서 지원됩니다.

<sup>b</sup>  Visual Studio 2019 버전 16.8부터 **`/std:c11`** 또는 **`/std:c17`** 컴파일러 옵션이 지정된 경우 이러한 키워드가 인식되지만 C로 컴파일된 코드의 컴파일러에서는 지원되지 않습니다.

키워드를 다시 정의할 수는 없습니다. 그러나 컴파일 전에 C [전처리기 지시문](../preprocessor/preprocessor-directives.md)을 사용하여 키워드를 대체할 텍스트를 지정할 수 있습니다.

## <a name="microsoft-specific-c-keywords"></a>Microsoft 전용 C 키워드

ANSI 및 ISO C 표준을 사용하면 두 개의 선행 밑줄이 쳐진 식별자를 컴파일러의 구현용으로 예약할 수 있습니다. Microsoft 규칙은 이중 밑줄이 쳐진 Microsoft 전용 키워드 이름 앞에 있게 됩니다. 이들 단어는 식별자 이름으로 사용할 수 없습니다. 두 개의 밑줄을 사용하는 경우를 포함하여 식별자 명명 규칙에 대한 자세한 내용은 [식별자](../c-language/c-identifiers.md)를 참조하세요.

Microsoft C 컴파일러에서 다음 키워드 및 특수 식별자가 인식됩니다.

:::row:::
    :::column:::
        **`__asm`** <sup>5</sup>\
        **`__based`** <sup>3, 5</sup>\
        **`__cdecl`** <sup>5</sup>\
        **`__declspec`** <sup>5</sup>\
        **`__except`** <sup>5</sup>\
        **`__fastcall`**\
        **`__finally`** <sup>5</sup>
    :::column-end:::
    :::column:::
        **`__inline`** <sup>5</sup>\
        **`__int16`** <sup>5</sup>\
        **`__int32`** <sup>5</sup>\
        **`__int64`** <sup>5</sup>\
        **`__int8`** <sup>5</sup>\
        **`__leave`** <sup>5</sup>\
        **`__restrict`**
    :::column-end:::
    :::column:::
        **`__stdcall`** <sup>5</sup>\
        **`__try`** <sup>5</sup>\
        **`dllexport`** <sup>4</sup>\
        **`dllimport`** <sup>4</sup>\
        **`naked`** <sup>4</sup>\
        **`static_assert`** <sup>6</sup>\
        **`thread`** <sup>4</sup>
    :::column-end:::
:::row-end:::

<sup>3</sup> **`__based`** 키워드의 경우 32 비트 및 64 비트 대상 컴파일에서 제한적으로 사용됩니다.

<sup>4</sup> 이들은 **`__declspec`** 과 함께 사용되는 특수 식별자이며 다른 컨텍스트에서는 사용이 제한되지 않습니다.

<sup>5</sup> 이전 버전과의 호환성을 위해 이러한 키워드는 Microsoft 확장이 사용하도록 설정된 경우 두 개의 선행 밑줄과 단일 선행 밑줄 둘 다와 함께 사용할 수 있습니다.

<sup>6</sup> <assert.h>를 포함하지 않는 경우 Microsoft Visual C 컴파일러는 **`static_assert`** 를 C11 **`_Static_assert`** 키워드에 매핑합니다.

Microsoft 확장은 기본적으로 사용하도록 설정됩니다. 이식 가능한 코드 작성을 지원하려면 [/Za\(언어 확장 사용 안 함)](../build/reference/za-ze-disable-language-extensions.md) 옵션을 지정하여 Microsoft 확장을 사용하지 않을 수 있습니다. 이 옵션을 사용하면 몇 가지 Microsoft 관련 키워드를 사용할 수 없습니다.

Microsoft 확장을 사용하면 위에 나열된 키워드를 프로그램에서 사용할 수 있습니다. 표준 준수를 위해 이러한 키워드의 대부분에는 두 개의 밑줄이 앞에 옵니다. 네 가지 예외 사항인 **`dllexport`** , **`dllimport`** , **`naked`** 및 **`thread`** 는 **`__declspec`** 과 함께만 사용되며 선행 밑줄이 필요하지 않습니다. 이전 버전과의 호환성을 위해 나머지 키워드에는 밑줄 한 개가 옵니다.

## <a name="see-also"></a>참조

[C 요소](../c-language/elements-of-c.md)
