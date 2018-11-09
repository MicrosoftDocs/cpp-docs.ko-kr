---
title: C 후위 증가 및 감소 연산자
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
ms.openlocfilehash: 8d45ce34457779e668124d9f48b82a5b74da1c56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506848"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>C 후위 증가 및 감소 연산자

후위 증가 및 감소 연산자의 피연산자는 수정 가능한 l-value인 스칼라 형식입니다.

## <a name="syntax"></a>구문

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

후위 증가 또는 감소 연산의 결과는 피연산자의 값입니다. 결과를 얻은 후에는 피연산자의 값이 증가 또는 감소합니다. 다음 코드에서는 후위 증가 연산자를 보여 줍니다.

```
if( var++ > 0 )
    *p++ = *q++;
```

이 예제에서 `var` 변수는 0과 비교된 다음 증가됩니다. `var`이 증가되기 전에 양수였던 경우 다음 문이 실행됩니다. 먼저 `q`가 가리키는 개체의 값이 `p`가 가리키는 개체에 할당됩니다. 그런 다음 `q` 및 `p`가 증가됩니다.

## <a name="see-also"></a>참고 항목

[후위 증가 및 감소 연산자: ++ 및 --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)