---
description: '자세한 정보: 다차원 배열 (C)'
title: 다차원 배열 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
ms.openlocfilehash: e940ccdd61aa6c2c4b3b5f85b355b80f86c8a165
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243369"
---
# <a name="multidimensional-arrays-c"></a>다차원 배열 (C)

첨자 식에는 다음과 같이 여러 첨자가 있을 수도 있습니다.

```
expression1 [ expression2 ] [ expression3 ] ...
```

첨자 식은 왼쪽에서 오른쪽으로 연결합니다. 맨 왼쪽 첨자 식인 *expression1* **[** *expression2* **]** 이 먼저 계산됩니다. *expression1* 및 *expression2* 를 추가한 결과인 주소는 포인터 식을 형성합니다. 그런 다음 이 포인터 식에 *expression3* 이 추가되어 새 포인터 식을 형성하고 마지막 첨자 식이 추가될 때까지 계속됩니다. 최종 포인터 값이 배열 형식의 주소를 지정하지 않으면 마지막 첨자 식이 계산된 후 간접 참조 연산자(<strong>\*</strong>)가 적용됩니다(아래 예제 참조).

여러 첨자가 포함된 식은 "다차원 배열"의 요소를 참조합니다. 다차원 배열은 요소가 배열인 배열입니다. 예를 들어 3차원 배열의 첫 번째 요소는 2차원 배열입니다.

## <a name="examples"></a>예

다음 예제의 경우 이름이 `prop`인 배열이 세 요소로 선언되며 각각 **`int`** 값의 4x6 배열입니다.

```
int prop[3][4][6];
int i, *ip, (*ipp)[6];
```

`prop` 배열에 대한 참조는 다음과 같습니다.

```
i = prop[0][0][1];
```

위의 예제에서는 `prop`의 두 번째 개별 **`int`** 요소를 참조하는 방법을 보여 줍니다. 배열은 행별로 저장되므로 마지막 첨자는 가장 빠르게 변합니다. 식 `prop[0][0][2]`는 배열의 다음(세 번째) 요소를 나타냅니다.

```
i = prop[2][1][3];
```

이 문은 `prop`의 개별 요소에 대한 다소 복잡한 참조입니다. 이 식은 다음과 같이 계산됩니다.

1. 첫 번째 첨자인 `2`는 4x6 **`int`** 배열의 크기를 곱한 다음 포인터 값 `prop`에 추가됩니다. 결과는 `prop`의 세 번째 4x6 배열을 가리킵니다.

1. 두 번째 첨자인 `1`은 6개 요소 **`int`** 배열의 크기를 곱한 다음 `prop[2]`으로 표현된 주소에 추가됩니다.

1. 6개 요소 배열의 각 요소는 **`int`** 값이므로 마지막 첨자인 `3`은 **`int`** 의 크기를 곱한 다음 `prop[2][1]`에 추가됩니다. 결과 포인터는 6개 요소 배열의 네 번째 요소의 주소를 지정합니다.

1. 간접 참조 연산자가 포인터 값에 적용됩니다. 결과는 해당 주소의 **`int`** 요소입니다.

다음 두 예제에서는 간접 참조 연산자가 적용되지 않는 경우를 보여 줍니다.

```
ip = prop[2][1];

ipp = prop[2];
```

이러한 문 중 첫 번째 문에서 `prop[2][1]` 식은 3차원 배열 `prop`에 대한 유효한 참조입니다. 이 식은 6개 요소 배열을 참조합니다(위에서 선언됨). 포인터 값은 배열의 주소를 지정하기 때문에 간접 참조 연산자가 적용되지 않습니다.

마찬가지로 두 번째 문 `prop[2]`의 `ipp = prop[2];` 식의 결과는 2차원 배열의 주소를 지정하는 포인터 값입니다.

## <a name="see-also"></a>참조

[아래 첨자 연산자:](../cpp/subscript-operator.md)
