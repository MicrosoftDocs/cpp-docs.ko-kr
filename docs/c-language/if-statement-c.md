---
title: if 문 (C)
ms.date: 11/04/2016
f1_keywords:
- else
- if
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
ms.openlocfilehash: 6fe92d3f2927cd6c5b3df16850e2925fc42055d0
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684146"
---
# <a name="if-statement-c"></a>if 문 (C)

**`if`** 문은 조건부 분기를 제어합니다. **`if`** 문의 본문은 식의 값이 0이 아닌 경우 실행되지 않습니다. **`if`** 문의 구문에는 두 가지 형태가 있습니다.

## <a name="syntax"></a>구문

*selection-statement*: **if (**  *expression*  **)**  *statement*

**if (**  *expression*  **)**  *statement*  **`else`**  *statement*

**`if`** 문의 두 형태에서 구조체를 제외한 모든 값을 포함할 수 있는 식과 모든 파생 작업이 계산됩니다.

구문의 첫 번째 형태에서 *expression*이 true(0이 아님)이면 *statement*가 실행되고, *expression*이 false이면 *statement*가 무시됩니다. **`else`** 를 사용하는 구문의 두 번째 형태에서 *expression*이 false인 경우 두 번째 *statement*이 실행됩니다. 두 형태 모두에서 문 중 하나에 **`break`** , **`continue`** 또는 **`goto`** 가 포함되지 않는 한 **`if`** 문에서 프로그램의 다음 문으로 제어가 전달됩니다.

다음은 **`if`** 문의 예제입니다.

```C
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

이 예제에서 `y = x/i;` 문은 `i`가 0보다 큰 경우에 실행됩니다. `i`가 0보다 작거나 같은 경우 `i`는 `x`에 할당되고 `f( x )`는 `y`에 할당됩니다. **`if`** 절을 형성하는 문은 세미콜론으로 끝납니다.

**`if`** 문과 **`else`** 절을 중첩하는 경우, 중괄호를 사용하여 의도를 명확히 나타내는 복합 문으로 문과 절을 그룹화합니다. 중괄호가 없는 경우 컴파일러는 각 **`else`** 를 **`else`** 가 없는 가장 가까운 **`if`** 와 연결하여 모호성을 해결합니다.

```C
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

이 예제에서 **`else`** 절은 내부 **`if`** 문과 연결되어 있습니다. `i`가 0보다 작거나 같으면 `x`에 값이 할당되지 않습니다.

```C
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

이 예제에서 내부 **`if`** 문을 묶은 중괄호 때문에 **`else`** 절이 외부 **`if`** 문의 부분이 됩니다. `i`가 0보다 작거나 같으면 `i`가 `x`에 할당됩니다.

## <a name="see-also"></a>참조

[if-else 문(C++)](../cpp/if-else-statement-cpp.md)
