---
description: '자세한 정보: 부동 소수점 형식에서 변환'
title: 부동 소수점 형식에서 변환
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: 2e2a78a68b39d9109a2304d78070bddef36e9b52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293237"
---
# <a name="conversions-from-floating-point-types"></a>부동 소수점 형식에서 변환

다른 부동 소수점 형식으로 변환되는 부동 소수점 값은 원래 값을 결과 형식에서 정확하게 표현할 수 있는 경우 값이 변경되지 않습니다. 원래 값이 숫자이지만 정확하게 표현할 수 없는 경우 결과는 다음으로 크거나 다음으로 작은 표현할 수 있는 값입니다. 부동 소수점 형식의 범위에 대해서는 [부동 소수점 상수에 대한 제한](../c-language/limits-on-floating-point-constants.md)을 참조하세요.

정수 형식으로 변환되는 부동 소수점 값은 먼저 소수 부분을 제거하여 잘립니다. 이 잘린 값을 결과 형식에서 표현할 수 있는 경우 결과는 해당 값이어야 합니다. 표현할 수 없는 경우 결과 값은 정의되지 않습니다.

**Microsoft 전용**

Microsoft 컴파일러는 **`float`** 값에 IEEE-754 binary32 표현을 사용하고, **`long double`** 및 **`double`** 에 binary64 표현을 사용합니다. **`long double`** 과 **`double`** 은 동일한 표현을 사용하므로 범위 및 전체 자릿수가 동일합니다.

컴파일러가 **`double`** 또는 **`long double`** 부동 소수점 숫자를 **`float`** 로 변환하는 경우 부동 소수점 환경 컨트롤에 따라 결과를 반올림합니다. 이 컨트롤은 기본적으로 "짝수로 반올림(round to nearest, ties to even)"합니다. 숫자 값이 너무 크거나 너무 작아서 숫자 **`float`** 값으로 나타낼 수 없는 경우 변환 결과는 원래 값의 부호에 따라 양 또는 음의 무한대이고, 사용하도록 설정된 경우 오버플로 예외가 발생합니다.

정수 형식으로 변환하는 경우 **`long`** 보다 작은 형식으로의 변환 결과는 값을 **`long`** 으로 변환한 다음 결과 형식으로 변환하는 결과입니다.

**`long`** 이상의 정수 형식으로 변환하는 경우 너무 크거나 작아 결과 형식으로 나타낼 수 없는 값의 변환은 다음 값 중 하나를 반환할 수 있습니다.

- 결과는 0에서 가장 먼 표현할 수 있는 값인 ‘센티널 값’일 수 있습니다. 부호 있는 형식의 경우 표현할 수 있는 가장 낮은 값(0x800...0)입니다. 부호 없는 형식의 경우 표현할 수 있는 가장 높은 값(0xFF...F)입니다.

- 결과는 ‘포화’될 수 있습니다. 즉,  너무 높아 표현할 수 없는 값은 표현할 수 있는 가장 높은 값으로 변환되고, 너무 낮아 표현할 수 없는 값은 표현할 수 있는 가장 낮은 값으로 변환됩니다. 관련 두 값 중 하나가 센티널 값으로도 사용됩니다.

- **`unsigned long`** 또는 **`unsigned long long`** 으로 변환하는 경우 범위를 벗어난 값을 변환하는 결과는 표현할 수 있는 가장 높거나 가장 낮은 값이 아닌 값이 될 수 있습니다. 결과가 센티널 또는 포화 값인지 여부는 컴파일러 옵션 및 대상 아키텍처에 따라 달라집니다. 이후 컴파일러 릴리스에서는 대신 포화 또는 센티널 값을 반환할 수 있습니다.

**Microsoft 전용 종료**

다음 표에서는 부동 형식의 변환을 요약합니다.

## <a name="table-of-conversions-from-floating-point-types"></a>부동 소수점 형식에서 변환표

|시작|대상|메서드|
|----------|--------|------------|
|**`float`**|**`char`**|**`long`** 으로 변환, **`long`** 을 **`char`** 로 변환|
|**`float`**|**`short`**|**`long`** 으로 변환, **`long`** 을 **`short`** 로 변환|
|**`float`**|**`int`**|소수점에서 자릅니다. 결과가 커서 **`int`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`float`**|**`long`**|소수점에서 자릅니다. 결과가 커서 **`long`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`float`**|**`long long`**|소수점에서 자릅니다. 결과가 커서 **`long long`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`float`**|**`unsigned char`**|**`long`** 으로 변환, **`long`** 을 **`unsigned char`** 로 변환|
|**`float`**|**`unsigned short`**|**`long`** 으로 변환, **`long`** 을 **`unsigned short`** 로 변환|
|**`float`**|**`unsigned`**|소수점에서 자릅니다. 결과가 커서 **`unsigned`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`float`**|**`unsigned long`**|소수점에서 자릅니다. 결과가 커서 **`unsigned long`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`float`**|**`unsigned long long`**|소수점에서 자릅니다. 결과가 커서 **`unsigned long long`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`float`**|**`double`**|**`double`** 로 나타냅니다.|
|**`float`**|**`long double`**|**`long double`** 로 나타냅니다.|
|**`double`**|**`char`**|**`float`** 로 변환, **`float`** 를 **`char`** 로 변환|
|**`double`**|**`short`**|**`float`** 으로 변환, **`float`** 을 **`short`** 로 변환|
|**`double`**|**`int`**|소수점에서 자릅니다. 결과가 커서 **`int`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`double`**|**`long`**|소수점에서 자릅니다. 결과가 커서 **`long`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`double`**|**`unsigned char`**|**`long`** 으로 변환, **`long`** 을 **`unsigned char`** 로 변환|
|**`double`**|**`unsigned short`**|**`long`** 으로 변환, **`long`** 을 **`unsigned short`** 로 변환|
|**`double`**|**`unsigned`**|소수점에서 자릅니다. 결과가 커서 **`unsigned`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`double`**|**`unsigned long`**|소수점에서 자릅니다. 결과가 커서 **`unsigned long`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`double`**|**`unsigned long long`**|소수점에서 자릅니다. 결과가 커서 **`unsigned long long`** 으로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`double`**|**`float`**|**`float`** 로 나타냅니다. **`double`** 값을 **`float`** 로 정확히 나타낼 수 없는 경우 정밀도가 손실됩니다. 값이 커서 **`float`** 로 나타낼 수 없는 경우 결과가 정의되지 않습니다.|
|**`double`**|**`long double`**|**`long double`** 값은 **`double`** 로 처리됩니다.|

**`long double`** 변환은 **`double`** 변환과 동일한 방법을 따릅니다.

## <a name="see-also"></a>참조

[할당 변환](../c-language/assignment-conversions.md)
