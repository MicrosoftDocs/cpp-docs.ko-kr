---
description: '자세한 정보: 부동 소수점 숫자의 정밀도가 떨어지는 이유'
title: 부동 소수점 숫자의 정밀도가 떨어지는 이유
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 97daabd7342e94022f309937c9986b61cbc8668c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120772"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>부동 소수점 숫자의 정밀도가 떨어지는 이유

일반적으로 부동 소수점 10진수 값에는 정확히 일치하는 이진 표현이 없습니다. 이는 CPU가 부동 소수점 데이터를 표현하는 방식의 부작용입니다. 해당 이유로 일부 자릿수가 손실될 수 있으며 일부 부동 소수점 연산으로 인해 예기치 않은 결과가 발생할 수 있습니다.

이 동작은 다음 중 하나에 해당하는 결과입니다.

- 10진수의 이진 표현은 정확하지 않을 수 있습니다.

- 사용된 숫자(예: float과 double 혼합) 간에 형식이 일치하지 않습니다.

프로그래머는 대부분 이 동작을 해결하는 데 필요한 값보다 크거나 작도록 하거나 전체 자릿수를 유지하는 BCD(이진 코딩된 10진수) 라이브러리를 가져와서 사용합니다.

부동 소수점 값의 이진 표현은 부동 소수점 계산의 전체 자릿수 및 정확도에 영향을 줍니다. Microsoft Visual C++는 [IEEE 부동 소수점 형식](ieee-floating-point-representation.md)을 사용합니다.

## <a name="example"></a>예제

```c
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>주석

EPSILON의 경우 float에 대해 1.192092896e-07F로 정의된 상수 FLT_EPSILON 또는 double에 대해 2.2204460492503131e-016으로 정의된 DBL_EPSILON을 사용할 수 있습니다. 관련 상수에는 float.h를 포함해야 합니다. 해당 상수는 x + 1.0이 1.0과 같지 않은 가장 작은 양수 x로 정의됩니다. 매우 작은 수이므로 매우 큰 숫자를 포함하는 계산의 경우 사용자 정의 오차를 사용해야 합니다.

## <a name="see-also"></a>참조

[코드 최적화](optimizing-your-code.md)
