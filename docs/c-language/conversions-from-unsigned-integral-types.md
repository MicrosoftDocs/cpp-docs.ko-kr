---
description: '자세한 정보: 부호 없는 정수 계열 형식에서 변환'
title: 부호 없는 정수 계열 형식에서 변환
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: bb8f208a323083afeb4b5b88bc8d6514e1f8c99f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293146"
---
# <a name="conversions-from-unsigned-integral-types"></a>부호 없는 정수 계열 형식에서 변환

부호 없는 정수가 정수 또는 부동 소수점 형식으로 변환될 때 결과 형식에서 원래 값을 표현할 수 있으면 값이 변경되지 않습니다.

부호 없는 정수를 더 큰 크기의 정수로 변환하는 경우 값은 부호 확장됩니다. 더 작은 크기의 정수로 변환하는 경우에는 상위 비트가 잘립니다. 결과는 다음 예제와 같이 결과 형식을 사용하여 해석됩니다.

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

부호 없는 정수를 부동 소수점 형식으로 변환할 때 원래 값을 결과 형식에서 정확하게 표현할 수 없는 경우 결과는 다음으로 높거나 낮은 표현할 수 있는 값입니다.

정수 및 부동 소수점 형식의 크기에 대한 자세한 내용은 [기본 형식 스토리지](../c-language/storage-of-basic-types.md)를 참조하세요.

**Microsoft 전용**

Microsoft 컴파일러에서 **`unsigned`** (또는 **`unsigned int`** )와 **`unsigned long`** 은 고유하지만 같은 형식입니다. **`unsigned int`** 값의 변환은 **`unsigned long`** 의 변환과 동일하게 진행됩니다.

**Microsoft 전용 종료**

다음 표에서는 부호 없는 정수 계열 형식으로부터의 변환을 요약하여 보여 줍니다.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>부호 없는 정수 계열 형식에서 변환표

|시작|대상|메서드|
|----------|--------|------------|
|**`unsigned char`**|**`char`**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**`unsigned char`**|**`short`**|0 확장|
|**`unsigned char`**|**`long`**|0 확장|
|**`unsigned char`**|**`long long`**|0 확장|
|**`unsigned char`**|**`unsigned short`**|0 확장|
|**`unsigned char`**|**`unsigned long`**|0 확장|
|**`unsigned char`**|**`unsigned long long`**|0 확장|
|**`unsigned char`**|**`float`**|**`long`** 으로 변환, **`long`** 을 **`float`** 로 변환|
|**`unsigned char`**|**`double`**|**`long`** 으로 변환, **`long`** 을 **`double`** 로 변환|
|**`unsigned char`**|**`long double`**|**`long`** 으로 변환, **`long`** 을 **`double`** 로 변환|
|**`unsigned short`**|**`char`**|하위 바이트 유지|
|**`unsigned short`**|**`short`**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**`unsigned short`**|**`long`**|0 확장|
|**`unsigned short`**|**`long long`**|0 확장|
|**`unsigned short`**|**`unsigned char`**|하위 바이트 유지|
|**`unsigned short`**|**`unsigned long`**|0 확장|
|**`unsigned short`**|**`unsigned long long`**|0 확장|
|**`unsigned short`**|**`float`**|**`long`** 으로 변환, **`long`** 을 **`float`** 로 변환|
|**`unsigned short`**|**`double`**|**`long`** 으로 변환, **`long`** 을 **`double`** 로 변환|
|**`unsigned short`**|**`long double`**|**`long`** 으로 변환, **`long`** 을 **`double`** 로 변환|
|**`unsigned long`**|**`char`**|하위 바이트 유지|
|**`unsigned long`**|**`short`**|하위 단어 유지|
|**`unsigned long`**|**`long`**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**`unsigned long`**|**`long long`**|0 확장|
|**`unsigned long`**|**`unsigned char`**|하위 바이트 유지|
|**`unsigned long`**|**`unsigned short`**|하위 단어 유지|
|**`unsigned long`**|**`unsigned long long`**|0 확장|
|**`unsigned long`**|**`float`**|**`long`** 으로 변환, **`long`** 을 **`float`** 로 변환|
|**`unsigned long`**|**`double`**|**`double`** 로 직접 변환|
|**`unsigned long`**|**`long double`**|**`long`** 으로 변환, **`long`** 을 **`double`** 로 변환|
|**`unsigned long long`**|**`char`**|하위 바이트 유지|
|**`unsigned long long`**|**`short`**|하위 단어 유지|
|**`unsigned long long`**|**`long`**|하위 dword 유지|
|**`unsigned long long`**|**`long long`**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**`unsigned long long`**|**`unsigned char`**|하위 바이트 유지|
|**`unsigned long long`**|**`unsigned short`**|하위 단어 유지|
|**`unsigned long long`**|**`unsigned long`**|하위 dword 유지|
|**`unsigned long long`**|**`float`**|**`long`** 으로 변환, **`long`** 을 **`float`** 로 변환|
|**`unsigned long long`**|**`double`**|**`double`** 로 직접 변환|
|**`unsigned long long`**|**`long double`**|**`long`** 으로 변환, **`long`** 을 **`double`** 로 변환|

## <a name="see-also"></a>참조

[할당 변환](../c-language/assignment-conversions.md)
