---
description: pragmaMicrosoft C/c + +의 inline_recursion 지시문에 대해 자세히 알아보세요.
title: inline_recursion pragma
ms.date: 01/22/2021
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragma, inline_recursion
- inline_recursion pragma
no-loc:
- pragma
ms.openlocfilehash: b4e377d4c97c46a20e44a2c41f872a8762cdea4d
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713560"
---
# <a name="inline_recursion-no-locpragma"></a>`inline_recursion` pragma

직접 또는 상호 재귀 함수 호출의 인라인 확장을 제어합니다.

## <a name="syntax"></a>구문

> **`#pragma inline_recursion(`** [ { **`on`** | **`off`** } ] **`)`**

## <a name="remarks"></a>설명

이 옵션을 사용 하 여 pragma , 또는 함수로 표시 된 함수를 제어 하 [`inline`](../cpp/inline-functions-cpp.md) 고, [`__inline`](../cpp/inline-functions-cpp.md) 컴파일러에서 자동으로 옵션을 확장 합니다 **`/Ob2`** . 이를 사용 pragma 하려면 [`/Ob`](../build/reference/ob-inline-function-expansion.md) 컴파일러 옵션을 1 또는 2로 설정 해야 합니다. 의 기본 상태는 **`inline_recursion`** off입니다. 이는 pragma 가 표시 된 후 첫 번째 함수 호출에 적용 pragma 되며 함수 정의에 영향을 주지 않습니다.

는 **`inline_recursion`** pragma 재귀 함수를 확장 하는 방법을 제어 합니다. **`inline_recursion`** 가 off이 고 인라인 함수에서 직접 또는 간접적으로 자신을 호출 하는 경우 함수는 한 번만 확장 됩니다. **`inline_recursion`** 가 on 인 경우 함수는로 설정 된 값에 도달할 때까지 여러 번 확장 [`inline_depth`](../preprocessor/inline-depth.md) pragma 되거나,에 정의 된 재귀 함수의 기본값 `inline_depth` pragma 또는 용량 제한에 도달할 때까지 여러 번 확장 됩니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)\
[`inline_depth`](../preprocessor/inline-depth.md)\
[`/Ob` (인라인 함수 확장)](../build/reference/ob-inline-function-expansion.md)
