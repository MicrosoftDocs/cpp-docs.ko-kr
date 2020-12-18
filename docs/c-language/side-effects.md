---
description: '자세한 정보: 파생 작업'
title: 파생 작업
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
ms.openlocfilehash: 78a08cb2c6290a3cb9c0c61a714cb2bcfe61a4cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292782"
---
# <a name="side-effects"></a>파생 작업

식의 계산 순서는 언어에서 특정 계산 순서를 보장하는 경우([우선 순위 및 계산 순서](../c-language/precedence-and-order-of-evaluation.md) 참조)를 제외하고 특정 구현에서 정의됩니다. 예를 들어 다음 함수 호출에서 의도하지 않은 결과가 발생합니다.

```
add( i + 1, i = j + 2 );
myproc( getc(), getc() );
```

함수 호출의 인수는 어떤 순서로든 계산될 수 있습니다. `i + 1` 식이 `i = j + 2`보다 먼저 계산되거나, `i = j + 2`가 `i + 1`보다 먼저 계산될 수 있습니다. 각 경우에 결과가 다릅니다. 마찬가지로 `myproc`에 실제로 전달되는 문자를 보장할 수 없습니다. 단항 증가 및 감소 연산에는 할당이 포함되므로 이러한 연산은 다음 예제와 같이 의도하지 않은 결과를 발생시킬 수 있습니다.

```
x[i] = i++;
```

이 예제에서 수정되는 `x`의 값은 예측할 수 없습니다. 첨자의 값은 `i`의 새 값이거나 이전 값일 수 있습니다. 결과는 컴파일러나 최적화 수준에 따라 달라질 수 있습니다.

C에서는 의도하지 않은 결과에 대한 계산 순서를 정의하지 않으므로 위에서 설명한 두 계산 방법 모두 올바르며 둘 중 하나가 구현될 수 있습니다. 코드가 이식 가능하고 명확하도록 하려면 의도하지 않은 결과에 대한 특정 계산 순서에 의존하는 문을 사용하지 않아야 합니다.

## <a name="see-also"></a>참조

[식 계산](../c-language/expression-evaluation-c.md)
