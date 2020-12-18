---
description: '자세한 정보: 가감 연산자 사용'
title: 가감 연산자 사용
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: d56a1b2e2696ae88598306271ed02c417ef63b0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318366"
---
# <a name="using-the-additive-operators"></a>가감 연산자 사용

더하기 및 빼기 연산자를 보여 주는 다음 예제는 이러한 선언을 사용합니다.

```
int i = 4, j;
float x[10];
float *px;
```

이 문은 다음에 해당합니다.

```
px = &x[4 + i];
px = &x[4] + i;
```

`i` 값은 **`float`** 의 길이를 곱한 다음 `&x[4]`에 추가됩니다. 결과 포인터 값은 `x[8]`의 주소입니다.

```
j = &x[i] - &x[i-2];
```

이 예제에서는 `x`의 세 번째 요소의 주소(`x[i-2]`에서 지정)가 `x`의 다섯 번째 요소의 주소(`x[i]`에서 지정)에서 차감됩니다. 차이는 **`float`** 의 길이로 나눠지며 결과는 정수 값 2입니다.

## <a name="see-also"></a>참조

[C 가감 연산자](../c-language/c-additive-operators.md)
