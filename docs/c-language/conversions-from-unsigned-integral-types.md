---
title: 부호 없는 정수 계열 형식에서 변환
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 3099f0113103223e392dc20560899b4a6e3ebf20
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998793"
---
# <a name="conversions-from-unsigned-integral-types"></a>부호 없는 정수 계열 형식에서 변환

부호 없는 정수가 정수 또는 부동 소수점 형식으로 변환 될 때 결과 형식에서 원래 값을 표현할 수 있으면 값이 변경 되지 않습니다.

부호 없는 정수를 더 큰 크기의 정수로 변환 하는 경우 값은 0으로 확장 됩니다. 더 작은 크기의 정수로 변환할 경우 상위 비트가 잘립니다. 결과는 다음 예제와 같이 결과 형식을 사용 하 여 해석 됩니다.

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

부호 없는 정수를 부동 소수점 형식으로 변환 하는 경우 원래 값을 결과 형식에 정확 하 게 나타낼 수 없는 경우 그 결과는 다음으로 높거나 낮은 표현 가능한 값입니다.

정수 계열 및 부동 소수점 형식의 크기에 대 한 자세한 내용은 [기본 형식의 저장소](../c-language/storage-of-basic-types.md) 를 참조 하세요.

**Microsoft 전용**

Microsoft 컴파일러에서 **부호** 없는 (또는 **부호 없는 정수**)와 **unsigned long** 은 고유 하지만 동일한 형식입니다. **unsigned int** 값의 변환은 **unsigned long**의 변환과 동일하게 진행됩니다.

**Microsoft 전용 종료**

다음 표에서는 부호 없는 정수 계열 형식으로부터의 변환을 요약하여 보여 줍니다.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>부호 없는 정수 계열 형식에서 변환 테이블

|보낸 사람|수행할 작업|메서드|
|----------|--------|------------|
|**unsigned char**|**char**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**unsigned char**|**short**|0 확장|
|**unsigned char**|**long**|0 확장|
|**unsigned char**|**long long**|0 확장|
|**unsigned char**|**unsigned short**|0 확장|
|**unsigned char**|**unsigned long**|0 확장|
|**unsigned char**|**부호 없는 long long**|0 확장|
|**unsigned char**|**float**|**long**으로 변환(**long**을 **float**로 변환)|
|**unsigned char**|**double**|**long**으로 변환(**long**을 **double**로 변환)|
|**unsigned char**|**long double**|**long**으로 변환(**long**을 **double**로 변환)|
|**unsigned short**|**char**|하위 바이트 유지|
|**unsigned short**|**short**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**unsigned short**|**long**|0 확장|
|**unsigned short**|**long long**|0 확장|
|**unsigned short**|**unsigned char**|하위 바이트 유지|
|**unsigned short**|**unsigned long**|0 확장|
|**unsigned short**|**부호 없는 long long**|0 확장|
|**unsigned short**|**float**|**long**으로 변환(**long**을 **float**로 변환)|
|**unsigned short**|**double**|**long**으로 변환(**long**을 **double**로 변환)|
|**unsigned short**|**long double**|**long**으로 변환(**long**을 **double**로 변환)|
|**unsigned long**|**char**|하위 바이트 유지|
|**unsigned long**|**short**|하위 단어 유지|
|**unsigned long**|**long**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**unsigned long**|**long long**|0 확장|
|**unsigned long**|**unsigned char**|하위 바이트 유지|
|**unsigned long**|**unsigned short**|하위 단어 유지|
|**unsigned long**|**부호 없는 long long**|0 확장|
|**unsigned long**|**float**|**long**으로 변환(**long**을 **float**로 변환)|
|**unsigned long**|**double**|**double**로 직접 변환|
|**unsigned long**|**long double**|**long**으로 변환(**long**을 **double**로 변환)|
|**부호 없는 long long**|**char**|하위 바이트 유지|
|**부호 없는 long long**|**short**|하위 단어 유지|
|**부호 없는 long long**|**long**|낮은 순서 dword 유지|
|**부호 없는 long long**|**long long**|비트 패턴 유지(상위 비트가 부호 비트가 됨)|
|**부호 없는 long long**|**unsigned char**|하위 바이트 유지|
|**부호 없는 long long**|**unsigned short**|하위 단어 유지|
|**부호 없는 long long**|**unsigned long**|낮은 순서 dword 유지|
|**부호 없는 long long**|**float**|**long**으로 변환(**long**을 **float**로 변환)|
|**부호 없는 long long**|**double**|**double**로 직접 변환|
|**부호 없는 long long**|**long double**|**long**으로 변환(**long**을 **double**로 변환)|

## <a name="see-also"></a>참조

[할당 변환](../c-language/assignment-conversions.md)
