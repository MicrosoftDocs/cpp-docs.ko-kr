---
description: '자세한 정보: C 복합 할당'
title: C 복합 할당
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 73c47a506960d5c80e2a7f5693dcbacf770dbf02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211533"
---
# <a name="c-compound-assignment"></a>C 복합 할당

복합 할당 연산자는 단순 할당 연산자에 다른 이항 연산자를 결합한 것입니다. 복합 할당 연산자는 추가 연산자로 지정된 연산을 수행한 다음 결과를 왼쪽 피연산자에 할당합니다. 예를 들어 다음과 같은 복합 할당 식은

> *expression1* **+=** *expression2*

다음과 같이 해석될 수 있습니다.

> *expression1* **=** *expression1* **+** *expression2*

하지만 복합 대입 식은 *expression1* 을 한 번만 계산하지만, 확장된 버전은 *expression1* 을 두 번(더하기 연산과 대입 연산에서 한 번씩) 계산하기 때문에 복합 대입 식은 확장된 버전과 동일하지 않습니다.

복합 할당 연산자의 피연산자는 정수 계열 또는 부동 형식이어야 합니다. 각 복합 할당 연산자는 해당하는 이항 연산자가 수행하는 변환을 수행하고 그에 따라 피연산자의 형식을 제한합니다. 더하기 대입(`+=`) 및 빼기 대입( **-=** ) 연산자에도 포인터 형식의 왼쪽 피연산자가 있을 수 있으며, 이 경우 오른쪽 피연산자가 정수 형식이어야 합니다. 복합 할당 연산의 결과는 왼쪽 피연산자의 값과 형식입니다.

```C
#define MASK 0xff00

n &= MASK;
```

이 예제에서 `n` 및 `MASK`에 대해 비트 포함 AND 연산이 수행되고 결과가 `n`에 할당됩니다. `MASK` 매니페스트 상수는 [#define](../preprocessor/hash-define-directive-c-cpp.md) 전처리기 지시문을 사용하여 정의됩니다.

## <a name="see-also"></a>참조

[C 할당 연산자](../c-language/c-assignment-operators.md)
