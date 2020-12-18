---
description: '자세한 정보: float 형식'
title: float 형식
ms.date: 11/04/2016
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
ms.openlocfilehash: 4d2245db663885d084ee231d10b7dc944016ea4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242836"
---
# <a name="type-float"></a>float 형식

부동 소수점 수는 IEEE(Institute of Electrical and Electronics Engineers) 형식을 사용합니다. float 형식의 단정밀도 값은 부호 비트, -127승 이진 지수 8비트 및 가수 23비트로 구성된 4바이트를 사용합니다. 가수는 1.0에서 2.0 사이의 수를 의미합니다. 가수의 상위 비트가 항상 1이기 때문에 가수의 상위 비트는 수에 저장되지 않습니다. 이 표현은 float 형식에 대한 약 3.4E–38 ~ 3.4E+38의 범위를 제공합니다.

애플리케이션의 필요에 따라 변수를 float 또는 double 형식으로 선언할 수 있습니다. 두 형식 간의 주요 차이점은 필요한 스토리지와 해당 범위의 중요성을 나타낼 수 있다는 점입니다. 다음 표에서는 중요성과 스토리지 요구 사항 간의 관계를 보여 줍니다.

### <a name="floating-point-types"></a>부동 소수점 형식

|형식|유효 자릿수|바이트 수|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

부동 소수점 변수는 숫자 값을 포함하는 가수 및 숫자 크기의 순서를 포함하는 지수로 표시됩니다.

다음 표에서는 각 부동 소수점 형식에 대한 가수 및 지수에 할당된 비트 수를 보여 줍니다. 모든 float 또는 double의 가장 중요한 비트는 항상 부호 비트입니다. 1이면 음수로 간주되고, 그렇지 않으면 양수로 간주됩니다.

### <a name="lengths-of-exponents-and-mantissas"></a>지수 및 가수의 길이

|형식|지수 길이|가수 길이|
|----------|---------------------|---------------------|
|float|8비트|23비트|
|double|11비트|52비트|

지수는 부호 없는 형식으로 저장되기 때문에 가능한 값의 절반으로 오차가 지정됩니다. float 형식의 경우 편차는 127이고 double 형식의 경우 편차는 1023입니다. 지수 값에서 편차 값을 빼 실제 지수 값을 계산할 수 있습니다.

가수는 1보다 크거나 같고 2보다 작은 이진 소수로 저장됩니다. Float 및 double 형식의 경우 암시된 선행 1이 가장 중요한 비트 위치의 가수에 있기 때문에 가장 중요한 비트가 메모리에 저장되지 않는 경우라도 가수의 길이는 실제로 각각 24비트 또는 53비트입니다.

위에서 설명한 스토리지 메서드 대신, 부동 소수점 패키지는 이진 부동 소수점 수를 비정규화된 수로 저장할 수 있습니다. "비정규화된 수"는 가수의 가장 중요한 비트가 0인 예약된 지수 값이 있는 0이 아닌 부동 소수점 수입니다. 비정규화된 형식을 사용함으로써 정밀도 대신 부동 소수점 수의 범위를 확장할 수 있습니다. 부동 소수점 수가 정규화된 형식 또는 비정규화된 형식으로 표현되는지 여부를 제어할 수 없습니다. 즉, 부동 소수점 패키지로 표현을 결정합니다. 지수가 정규화된 형식으로 표현될 수 있는 최소값보다 작아지지 않으면 부동 소수점 패키지는 비정규화된 형식을 사용하지 않습니다.

다음 표에서는 각 부동 소수점 형식의 변수에 저장할 수 있는 최소값 및 최대값을 보여 줍니다. 이 표에 나열된 값은 정규화된 부동 소수점 수에만 적용되므로 비정규화된 부동 소수점 수의 최소값은 보다 작습니다. 80 *x* 87 레지스터에 유지되는 수는 항상 80비트의 정규화된 형식으로 표현됩니다. 수는 32비트 또는 64비트 부동 소수점 변수(float 형식 및 long 형식의 변수)에 저장될 때만 비정규화된 형식으로 표현될 수 있습니다.

### <a name="range-of-floating-point-types"></a>부동 소수점 형식의 범위

|형식|최소값|최대값|
|----------|-------------------|-------------------|
|float|1.175494351 E - 38|3.402823466 E + 38|
|double|2.2250738585072014 E - 308|1.7976931348623158 E + 308|

정밀도가 스토리지보다 작으면 부동 소수점 변수에 대해 float 형식을 사용해 보십시오. 반대로 정밀도가 가장 중요한 기준인 경우 double 형식을 사용하십시오.

부동 소수점 변수를 보다 중요한 형식으로 승격할 수 있습니다(float 형식에서 double 형식으로). 부동 소수점 변수에 대한 산술 연산을 수행할 때 확장이 자주 발생합니다. 이 연산은 최고의 정밀도를 가지고 있는 변수와 같은 높은 정밀도에서 항상 수행됩니다. 예를 들어 다음 형식 선언을 참조하십시오.

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

위 예제에서는 `f_short` 변수가 double 형식으로 승격되어 `f_long`으로 곱해지면 결과가 `f_short`에 할당되기 전에 float 형식으로 반올림됩니다.

다음 예제에서(이전 예제의 선언 사용) 변수에 대한 부동 소수점(32비트) 정밀도로 산술이 수행됩니다. 그러면 결과가 double 형식으로 승격됩니다.

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>참조

[기본 형식의 스토리지](../c-language/storage-of-basic-types.md)
