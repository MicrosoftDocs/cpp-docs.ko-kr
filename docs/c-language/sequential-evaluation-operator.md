---
description: '자세한 정보: 순차적 확인 연산자'
title: 순차적 확인 연산자
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
ms.openlocfilehash: 7bbe9bd6f70f32bd51e46df28f6e072edf9b6c15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292795"
---
# <a name="sequential-evaluation-operator"></a>순차적 확인 연산자

"쉼표 연산자"라고도 하는 순차 계산 연산자는 두 피연산자를 왼쪽에서 오른쪽으로 순차적으로 계산합니다.

## <a name="syntax"></a>구문

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **,** *assignment-expression*

순차 계산 연산자의 왼쪽 피연산자는 **`void`** 식으로 계산됩니다. 연산 결과의 값 및 형식은 오른쪽 피연산자와 같습니다. 각 피연산자는 어떤 형식이든 될 수 있습니다. 순차 계산 연산자는 해당 피연산자 간에 형식 변환을 수행하지 않으며 l-value를 생성하지 않습니다. 첫째 피연산자 다음에 시퀀스 위치가 있는데, 이것은 왼쪽 피연산자의 계산으로 인해 발생한 의도하지 않은 모든 결과가 오른쪽 피연산자의 계산을 시작하기 전에 완료됨을 의미합니다. 자세한 내용은 [시퀀스 위치](../c-language/c-sequence-points.md)를 참조하세요.

순차 계산 연산자는 하나의 식만 사용할 수 있는 컨텍스트에서 두 개 이상의 식을 계산하는 데 사용됩니다.

일부 컨텍스트에서는 쉼표를 구분 기호로 사용할 수 있습니다. 그러나 쉼표를 구분 기호로 사용하는 경우와 연산자로 사용하는 경우는 완전히 다르기 때문에 둘을 혼동하지 않도록 주의해야 합니다.

## <a name="example"></a>예제

다음 예제에서는 순차 계산 연산자를 보여 줍니다.

```
for ( i = j = 1; i + j < 20; i += i, j-- );
```

이 예제에서 **`for`** 문의 세 번째 식에 대한 각 피연산자는 독립적으로 계산됩니다. 왼쪽 피연산자 `i += i`가 먼저 계산된 다음 오른쪽 피연산자 `j--`가 계산됩니다.

```
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

`func_one`에 대한 함수 호출에서 쉼표로 구분된 세 인수(`x`, `y + 2`, `z`)가 전달됩니다. `func_two`에 대한 함수 호출에서 괄호는 컴파일러가 첫 번째 쉼표를 순차적 계산 연산자로 해석하도록 합니다. 이 함수 호출은 두 인수를 `func_two`에 전달합니다. 첫 번째 인수는 `(x--, y + 2)` 식의 값과 형식을 가진 순차적 계산 연산 `y + 2`의 결과이며, 두 번째 인수는 `z`입니다.

## <a name="see-also"></a>참조

[쉼표 연산자: ,](../cpp/comma-operator.md)
