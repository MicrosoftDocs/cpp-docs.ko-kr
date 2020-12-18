---
description: '자세한 정보: 부호 있는 정수 계열 형식에서 변환'
title: 부호 있는 정수 계열 형식에서 변환
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: 25ee07f0b3bac9cd954bc217a4a71e579e4eacda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293159"
---
# <a name="conversions-from-signed-integral-types"></a>부호 있는 정수 계열 형식에서 변환

부호 있는 정수가 정수 또는 부동 소수점 형식으로 변환될 때 결과 형식에서 원래 값을 표현할 수 있으면 값이 변경되지 않습니다.

부호 있는 정수를 더 큰 크기의 정수로 변환하는 경우 값은 부호 확장됩니다. 더 작은 크기의 정수로 변환한 경우에는 상위 비트가 잘립니다. 결과는 다음 예제와 같이 결과 형식을 사용하여 해석됩니다.

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

부호 있는 정수를 부동 소수점 형식으로 변환할 때 원래 값을 결과 형식에서 정확하게 표현할 수 없는 경우 결과는 다음으로 높거나 낮은 표현할 수 있는 값입니다.

(정수 및 부동 소수점 형식의 크기에 대한 자세한 내용은 [기본 형식 스토리지](../c-language/storage-of-basic-types.md)를 참조하세요.)

다음 표에서는 부호 있는 정수 계열 형식으로부터의 변환을 요약하여 보여 줍니다. **`char`** 형식은 기본적으로 부호가 있다고 간주합니다. 컴파일 시간 옵션을 사용하여 **`char`** 형식의 기본값을 unsigned로 변경할 경우 이 표의 변환 대신 **`unsigned char`** 형식에 대한 [부호 없는 정수 계열 형식에서 변환](../c-language/conversions-from-unsigned-integral-types.md) 표에 나와 있는 변환이 적용됩니다.

**Microsoft 전용**

Microsoft 컴파일러에서 **`int`** 와 **`long`** 은 고유하지만 같은 형식입니다. **`int`** 값의 변환은 **`long`** 의 변환과 동일하게 진행됩니다.

**Microsoft 전용 종료**

## <a name="table-of-conversions-from-signed-integral-types"></a>부호 있는 정수 계열 형식에서 변환표

|시작|대상|메서드|
|----------|--------|------------|
|**`char`** <sup>1</sup>|**`short`**|부호 확장|
|**`char`**|**`long`**|부호 확장|
|**`char`**|**`long long`**|부호 확장|
|**`char`**|**`unsigned char`**|패턴 유지(상위 비트가 부호 비트로의 기능을 잃음)|
|**`char`**|**`unsigned short`**|**`short`** 으로 부호 확장, **`short`** 을 **`unsigned short`** 으로 변환|
|**`char`**|**`unsigned long`**|**`long`** 으로 부호 확장, **`long`** 을 **`unsigned long`** 으로 변환|
|**`char`**|**`unsigned long long`**|**`long long`** 으로 부호 확장, **`long long`** 을 **`unsigned long long`** 로 변환|
|**`char`**|**`float`**|**`long`** 으로 부호 확장 **`long`** 을 **`float`** 로 변환|
|**`char`**|**`double`**|**`long`** 으로 부호 확장 **`long`** 을 **`double`** 로 변환|
|**`char`**|**`long double`**|**`long`** 으로 부호 확장 **`long`** 을 **`double`** 로 변환|
|**`short`**|**`char`**|하위 바이트 유지|
|**`short`**|**`long`**|부호 확장|
|**`short`**|**`long long`**|부호 확장|
|**`short`**|**`unsigned char`**|하위 바이트 유지|
|**`short`**|**`unsigned short`**|비트 패턴 유지(상위 비트가 부호 비트로의 기능을 잃음)|
|**`short`**|**`unsigned long`**|**`long`** 으로 부호 확장, **`long`** 을 **`unsigned long`** 으로 변환|
|**`short`**|**`unsigned long long`**|**`long long`** 으로 부호 확장, **`long long`** 을 **`unsigned long long`** 로 변환|
|**`short`**|**`float`**|**`long`** 으로 부호 확장 **`long`** 을 **`float`** 로 변환|
|**`short`**|**`double`**|**`long`** 으로 부호 확장 **`long`** 을 **`double`** 로 변환|
|**`short`**|**`long double`**|**`long`** 으로 부호 확장 **`long`** 을 **`double`** 로 변환|
|**`long`**|**`char`**|하위 바이트 유지|
|**`long`**|**`short`**|하위 단어 유지|
|**`long`**|**`long long`**|부호 확장|
|**`long`**|**`unsigned char`**|하위 바이트 유지|
|**`long`**|**`unsigned short`**|하위 단어 유지|
|**`long`**|**`unsigned long`**|비트 패턴 유지(상위 비트가 부호 비트로의 기능을 잃음)|
|**`long`**|**`unsigned long long`**|**`long long`** 으로 부호 확장, **`long long`** 을 **`unsigned long long`** 으로 변환|
|**`long`**|**`float`**|**`float`** 로 나타냅니다. **`long`** 을 정확히 나타낼 수 없는 경우 일부 정밀도가 손실됩니다.|
|**`long`**|**`double`**|**`double`** 로 나타냅니다. **`long`** 을 **`double`** 로 정확히 나타낼 수 없는 경우 일부 정밀도가 손실됩니다.|
|**`long`**|**`long double`**|**`double`** 로 나타냅니다. **`long`** 을 **`double`** 로 정확히 나타낼 수 없는 경우 일부 정밀도가 손실됩니다.|
|**`long long`**|**`char`**|하위 바이트 유지|
|**`long long`**|**`short`**|하위 단어 유지|
|**`long long`**|**`long`**|하위 dword 유지|
|**`long long`**|**`unsigned char`**|하위 바이트 유지|
|**`long long`**|**`unsigned short`**|하위 단어 유지|
|**`long long`**|**`unsigned long`**|하위 dword 유지|
|**`long long`**|**`unsigned long long`**|비트 패턴 유지(상위 비트가 부호 비트로의 기능을 잃음)|
|**`long long`**|**`float`**|**`float`** 로 나타냅니다. **`long long`** 을 정확히 나타낼 수 없는 경우 일부 정밀도가 손실됩니다.|
|**`long long`**|**`double`**|**`double`** 로 나타냅니다. **`long long`** 을 **`double`** 로 정확히 나타낼 수 없는 경우 일부 정밀도가 손실됩니다.|
|**`long long`**|**`long double`**|**`double`** 로 나타냅니다. **`long long`** 을 **`double`** 로 정확히 나타낼 수 없는 경우 일부 정밀도가 손실됩니다.|

<sup>1</sup> 모든 **`char`** 항목에서는 **`char`** 형식에 기본적으로 부호가 있다고 간주됩니다.

## <a name="see-also"></a>참조

[할당 변환](../c-language/assignment-conversions.md)
