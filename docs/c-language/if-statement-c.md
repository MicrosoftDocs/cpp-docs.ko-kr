---
title: if 문 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else
- if
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b01db4d842775dcb239aef9d40c661328d1544
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107881"
---
# <a name="if-statement-c"></a>if 문 (C)

**if** 문은 조건부 분기를 제어합니다. **if** 문의 본문은 식의 값이 0이 아닌 경우 실행되지 않습니다. **if** 문의 구문에는 두 가지 형태가 있습니다.

## <a name="syntax"></a>구문

*selection-statement*: **if (**  *expression*  **)**  *statement*

**if (**  *expression*  **)**  *statement*  **else**  *statement*

**if** 문의 두 형태에서 구조체를 제외한 모든 값을 포함할 수 있는 식과 모든 파생 작업이 계산됩니다.

구문의 첫 번째 형태에서 *expression*이 true(0이 아님)이면 *statement*가 실행되고, *expression*이 false이면 *statement*가 무시됩니다. **else**를 사용하는 구문의 두 번째 형태에서 *expression*이 false인 경우 두 번째 *statement*가 실행됩니다. 두 형태 모두에서 문 중 하나에 **break**, **continue** 또는 `goto`가 포함되지 않는 한 **if** 문에서 프로그램의 다음 문으로 제어가 전달됩니다.

**if** 문의 예는 다음과 같습니다.

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

이 예제에서 `y = x/i;` 문은 `i`가 0보다 큰 경우에 실행됩니다. `i`가 0보다 작거나 같은 경우 `i`는 `x`에 할당되고 `f( x )`는 `y`에 할당됩니다. **if** 절을 형성하는 문은 세미콜론으로 끝납니다.

**if** 문과 **else** 절을 중첩하는 경우, 중괄호를 사용하여 의도를 명확히 나타내는 복합 문으로 문과 절을 그룹화합니다. 중괄호가 없는 경우 컴파일러는 **else**가 없는 가장 가까운 **if**와 각 **else**를 연결하여 모호성을 해결합니다.

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

이 예제에서 **else** 절은 내부 **if** 문과 연결되어 있습니다. `i`가 0보다 작거나 같으면 `x`에 값이 할당되지 않습니다.

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

이 예제에서 내부 **if** 문을 묶은 중괄호 때문에 **else** 절이 외부 **if** 문의 부분이 됩니다. `i`가 0보다 작거나 같으면 `i`가 `x`에 할당됩니다.

## <a name="see-also"></a>참고 항목

[if-else 문(C++)](../cpp/if-else-statement-cpp.md)