---
description: '자세한 정보: 일반적인 산술 변환'
title: 일반적인 산술 변환
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
ms.openlocfilehash: 443d61b3ff295431a5c1507886cb0821a1f5b205
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198897"
---
# <a name="usual-arithmetic-conversions"></a>일반적인 산술 변환

대부분의 C 연산자는 형식 변환을 수행하여 식의 피연산자를 공용 형식으로 변환하거나 short 값을 컴퓨터 연산에서 사용되는 정수 크기로 확장합니다. C 연산자로 수행되는 변환은 특정 연산자와 피연산자의 형식에 따라 달라집니다. 하지만 많은 연산자는 정수 계열 및 부동 형식의 피연산자에 대해 비슷한 변환을 수행합니다. 이러한 변환을 "산술 변환"이라고 합니다. 피연산자 값을 호환되는 형식으로 변환하는 경우 해당 값이 변경되지 않습니다.

아래에 요약된 산술 변환은 "일반적인 산술 변환"이라고 합니다. 이러한 단계는 산술 형식을 예상하는 이항 연산자에만 적용됩니다. 목적은 결과의 형식이기도 한 공용 형식을 생성하는 것입니다. 실제로 발생하는 변환을 확인하기 위해 컴파일러는 식의 이항 연산에 다음 알고리즘을 적용합니다. 아래의 단계는 우선 순위가 아닙니다.

1. 피연산자 중 하나가 **`long double`** 형식인 경우 다른 피연산자가 **`long double`** 형식으로 변환됩니다.

1. 위의 조건이 충족되지 않고 피연산자 중 하나가 **`double`** 형식인 경우 다른 피연산자가 **`double`** 형식으로 변환됩니다.

1. 위의 두 조건이 충족되지 않고 피연산자 중 하나가 **`float`** 형식인 경우 다른 피연산자가 **`float`** 형식으로 변환됩니다.

1. 위의 세 조건이 충족되지 않는 경우(부동 형식인 피연산자가 없는 경우) 피연산자에 대한 정수 계열 변환이 다음과 같이 수행됩니다.

   - 피연산자 중 하나가 **`unsigned long`** 형식인 경우 다른 피연산자가 **`unsigned long`** 형식으로 변환됩니다.

   - 위의 조건이 충족되지 않고 피연산자 중 하나는 **`long`** 형식이고 다른 피연산자는 **`unsigned int`** 형식인 경우 두 피연산자가 **`unsigned long`** 형식으로 변환됩니다.

   - 위의 두 조건이 충족되지 않고 피연산자 중 하나가 **`long`** 형식인 경우 다른 피연산자가 **`long`** 형식으로 변환됩니다.

   - 위의 세 조건이 충족되지 않고 피연산자 중 하나가 **`unsigned int`** 형식인 경우 다른 피연산자가 **`unsigned int`** 형식으로 변환됩니다.

   - 위의 조건이 모두 충족되지 않는 경우 두 피연산자가 **`int`** 형식으로 변환됩니다.

다음 코드에서는 이러한 변환 규칙을 보여 줍니다.

```
float   fVal;
double  dVal;
int   iVal;
unsigned long ulVal;

dVal = iVal * ulVal; /* iVal converted to unsigned long
                      * Uses step 4.
                      * Result of multiplication converted to double
                      */
dVal = ulVal + fVal; /* ulVal converted to float
                      * Uses step 3.
                      * Result of addition converted to double
                      */
```

## <a name="see-also"></a>참조

[C 연산자](../c-language/c-operators.md)
