---
title: _Noreturn 키워드 및 noreturn 매크로(C11)
description: '`_Noreturn` 키워드 및 `noreturn` 매크로에 대해 설명합니다.'
ms.date: 10/19/2020
f1_keywords:
- _Noreturn_c
- noreturn
helpviewer_keywords:
- keywords [C]
ms.openlocfilehash: 68448d8b8c999c92fb240100c25048fa94a559b9
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274690"
---
# <a name="_noreturn-keyword-and-noreturn-macro-c11"></a>`_Noreturn` 키워드 및 `noreturn` 매크로(C11)

`_Noreturn` 키워드는 C11에 도입되었습니다. 컴파일러가 적용되는 함수가 호출자에게 반환되지 않는다는 것을 컴파일러에 알립니다. 그러면 컴파일러는 `_Noreturn` 함수 호출 후의 코드에 접근할 수 없다는 사실을 인식합니다. 반환하지 않는 함수의 예는 [abort](../c-runtime-library/reference/abort.md)입니다. 제어 흐름이 호출자에 반환될 가능성이 있는 경우 함수에 `_Noreturn` 특성이 있어서는 안 됩니다.

키워드는 일반적으로 `_Noreturn` 키워드에 매핑되는 <stdnoreturn.h>에 제공되는 편의 매크로인 `noreturn`을 통해 사용됩니다.

`_Noreturn`(또는 동등한 `noreturn`)을 사용할 경우의 주요 이점은 이후 판독기의 코드에서 함수의 의도를 명확히 하고 의도치 않게 접근 불가능한 코드를 검색하는 것입니다.

`noreturn`이 표시된 함수는 호출자에 값을 반환하지 않으므로 반환 형식을 포함해서는 안 됩니다. 값이 `void`이어야 합니다.

## <a name="example-using-noreturn-macro-and-_noreturn-keyword"></a>`noreturn` 매크로 및 `_Noreturn ` 키워드 사용 예제

다음 예제에서는 `_Noreturn` 키워드와 해당 `noreturn` 매크로를 보여 줍니다.

무시할 수 있는 매크로 `noreturn`을 사용하는 경우 IntelliSense는 의사 오류 `E0065`를 생성할 수도 있습니다. 샘플이 실행되는 것을 막지 않습니다.

```C
// Compile with Warning Level4 (/W4) and /std:c11
#include <stdio.h>
#include <stdlib.h>
#include <stdnoreturn.h>

noreturn void fatal_error(void)
{
    exit(3);
}

_Noreturn void not_coming_back(void)
{
    puts("There's no coming back");
    fatal_error();
    return; // warning C4645 - function declared with noreturn has a return statement
}

void done(void)
{
    puts("We'll never get here");
}

int main(void)
{
    not_coming_back();
    done(); // warning c4702 - unreachable code

    return 0;
}
```

## <a name="requirements"></a>요구 사항

|매크로|필수 헤더|
|-------------|---------------------|
|**`noreturn`**|\<stdnoreturn.h>|

## <a name="see-also"></a>참고 항목

[/std(언어 표준 버전 지정)](../build/reference/std-specify-language-standard-version.md)\
[/W4(경고 수준 지정)](../build/reference/compiler-option-warning-level.md)\
[C4702 경고](../error-messages\compiler-warnings\compiler-warning-level-4-c4702.md)\
[__declspec(noreturn)](../cpp/noreturn.md)
