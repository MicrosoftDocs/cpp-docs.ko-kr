---
description: '자세한 정보: 1차원 배열'
title: 1차원 배열
ms.date: 11/04/2016
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
ms.openlocfilehash: 6c75d4b8d9a64f95f3698e6953949a71df60cad6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256902"
---
# <a name="one-dimensional-arrays"></a>1차원 배열

대괄호( **[ ]** ) 안의 식이 뒤따르는 후위 식은 배열 개체 요소의 첨자가 있는 표현입니다. 첨자식은 다음과 같이 표현될 때 *postfix-expression* 을 벗어나는 *expression* 위치의 주소에 있는 값을 나타냅니다.

```
postfix-expression [ expression ]
```

일반적으로 *postfix-expression* 이 나타내는 값은 배열 식별자와 같은 포인터 값이며 *expression* 은 정수 계열 값입니다. 그러나 구문적 요구 사항은 식 중 하나가 포인터 형식이고 다른 하나는 정수 계열 형식이어야 한다는 것 밖에 없습니다. 따라서 정수 계열 값은 *postfix-expression* 위치에 있을 수 있으며 포인터 값은 *expression* 의 괄호 안 또는 첨자 위치에 있을 수 있습니다. 예를 들어 다음 코드는 올바릅니다.

```c
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

첨자식은 일반적으로 배열 요소를 참조하는 데 사용되지만 포인터에도 첨자를 적용할 수 있습니다. 값의 순서에 관계없이 *expression* 은 대괄호( **[ ]** )로 묶어야 합니다.

첨자식은 정수 계열 값을 포인터 값에 더한 다음 간접 참조 연산자(<strong>\*</strong>)를 결과에 적용하여 평가됩니다. 간접 참조 연산자에 대한 자세한 내용은 [간접 및 주소 연산자](../c-language/indirection-and-address-of-operators.md)를 참조하세요. 1차원 배열의 경우 `a`가 포인터이고 `b`가 정수라고 가정할 때 다음 네 식은 동일합니다.

```
a[b]
*(a + b)
*(b + a)
b[a]
```

더하기 연산자([가감 연산자](../c-language/c-additive-operators.md) 참조)에 대한 변환 규칙에 따라 정수 계열 값은 포인터로 주소가 지정된 형식의 길이를 곱하여 주소 오프셋으로 변환됩니다.

예를 들어 `line` 식별자가 **`int`** 값의 배열을 참조하는 경우, 다음 절차는 첨자식 `line[ i ]`를 평가하는 데 사용됩니다.

1. 정수 값 `i`를 **`int`** 항목의 길이로 정의된 바이트 수와 곱합니다. 변환된 `i`의 값은 `i` **`int`** 개의 위치를 나타냅니다.

1. 이 변환된 값을 원래 포인터 값(`line`)에 더하여 `line`으로부터 `i` **`int`** 개 위치만큼 떨어져 있는 주소를 생성합니다.

1. 간접 참조 연산자가 새 주소에 적용됩니다. 결과는 해당 위치에 있는 배열 요소의 값입니다(직관적으로 `line [ i ]`).

첨자식 `line[0]`은 `line`이 나타내는 주소로부터의 오프셋이 0이므로 line의 첫 번째 요소 값을 나타냅니다. 마찬가지로 `line[5]`와 같은 식은 line으로부터 5개 위치만큼 떨어져 있는 요소나 배열의 6번째 요소를 참조합니다.

## <a name="see-also"></a>참조

[아래 첨자 연산자:](../cpp/subscript-operator.md)
