---
description: pragmaMicrosoft C/c + +의 inline_depth 지시문에 대해 자세히 알아보세요.
title: inline_depth pragma
ms.date: 01/22/2021
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragma, inline_depth
- inline_depth pragma
no-loc:
- pragma
ms.openlocfilehash: 6daffdbcb598304925675c15c955941eb8369d23
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713573"
---
# <a name="inline_depth-no-locpragma"></a>`inline_depth` pragma

인라인 추론 검색 깊이를 지정 합니다. 호출 그래프에서 지정 된 값 보다 큰 깊이의 함수는 인라인되지 않습니다.

## <a name="syntax"></a>구문

> **`#pragma inline_depth(`** [ *n* ] **`)`**

## <a name="remarks"></a>설명

이 pragma 는 및로 표시 된 함수의 인라인을 제어 [`inline`](../cpp/inline-functions-cpp.md) [`__inline`](../cpp/inline-functions-cpp.md) 하거나 컴파일러 옵션에서 자동으로 인라인 합니다 **`/Ob`** . 자세한 내용은 [ `/Ob` (인라인 함수 확장)](../build/reference/ob-inline-function-expansion.md)를 참조 하세요.

*n* 은 0에서 255 사이의 값이 될 수 있습니다. 여기서 255은 호출 그래프에서 무제한 깊이를 의미 합니다. 0 값은 인라인 확장을 금지 합니다. *N* 을 지정 하지 않으면 기본값 254이 사용 됩니다.

는 **`inline_depth`** pragma 일련의 함수 호출이 확장 될 수 있는 횟수를 제어 합니다. 예를 들어 인라인 깊이가 4 인 것으로 가정 합니다. A가 B를 호출 하 고 B가 C를 호출 하는 경우 세 호출은 모두 인라인으로 확장 됩니다. 그러나 가장 가까운 인라인 수준 확장이 2 인 경우 A와 B만 확장 되 고 C는 함수 호출로 유지 됩니다.

이를 사용 하려면 pragma **`/Ob`** 컴파일러 옵션을 1 이상으로 설정 해야 합니다. 이를 사용 하 여 설정한 깊이는 pragma 의 첫 번째 함수 호출에 적용 pragma 됩니다.

인라인 깊이는 확장 하는 동안 감소할 수 있지만 증가 되지는 않습니다. 인라인 깊이가 6이 고 확장 하는 동안 전처리기에서 **`inline_depth`** pragma 값이 8 인가 발견 되 면 깊이는 6으로 유지 됩니다.

는 **`inline_depth`** pragma 로 표시 된 함수에는 영향을 주지 않습니다 **`__forceinline`** .

> [!NOTE]
> 재귀 함수는 최대 16 깊이의 호출까지 인라인을 대체할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)\
[`inline_recursion`](../preprocessor/inline-recursion.md)
