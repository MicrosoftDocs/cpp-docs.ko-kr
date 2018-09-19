---
title: 가감 연산자 사용 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 050db08d00d79e3cfee0ab7549532d78a51b1ade
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078870"
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

값 `i`는 **float**의 길이로 곱해지고 `&x[4]`에 더해집니다. 결과 포인터 값은 `x[8]`의 주소입니다.

```
j = &x[i] - &x[i-2];
```

이 예제에서는 `x`의 세 번째 요소의 주소(`x[i-2]`에서 지정)가 `x`의 다섯 번째 요소의 주소(`x[i]`에서 지정)에서 차감됩니다. 차이는 **float**의 길이로 나눠지며 결과는 정수 값 2입니다.

## <a name="see-also"></a>참고 항목

[C 가감 연산자](../c-language/c-additive-operators.md)