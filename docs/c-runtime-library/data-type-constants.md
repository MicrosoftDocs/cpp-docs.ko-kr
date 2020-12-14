---
description: '자세한 정보: 데이터 형식 상수'
title: 데이터 형식 상수
ms.date: 06/25/2018
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
ms.openlocfilehash: eb1c16cb730ea40a60a5929867fa8a36b17190ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258839"
---
# <a name="data-type-constants"></a>데이터 형식 상수

데이터 형식 상수는 정수 및 부동 소수점 데이터 형식에 대해 허용되는 값의 구현에 따라 다른 값입니다.

## <a name="integral-type-constants"></a>정수 형식 상수

이러한 상수는 정수 계열 데이터 형식에 대한 범위를 지정합니다. 이러한 상수를 사용하려면 소스 파일에 limits.h 헤더를 포함시킵니다.

```C
#include <limits.h>
```

> [!NOTE]
> [`/J`](../build/reference/j-default-char-type-is-unsigned.md)컴파일러 옵션은 기본 **`char`** 형식을에서로 변경 **`signed char`** 합니다 **`unsigned char`** .

|상수|값|설명|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|의 비트 수 **`char`**|
|**SCHAR_MIN**|(-128)|최 솟 **`signed char`** 값|
|**SCHAR_MAX**|127|최 댓 **`signed char`** 값|
|**UCHAR_MAX**|255(0Xff)|최 댓 **`unsigned char`** 값|
|**CHAR_MIN**|(-128) (옵션을 **`/J`** 사용 하는 경우 0)|최 솟 **`char`** 값|
|**CHAR_MAX**|127 (255 **`/J`** 옵션을 사용한 경우)|최 댓 **`char`** 값|
|**MB_LEN_MAX**|5|멀티 바이트의 최대 바이트 수 **`char`**|
|**SHRT_MIN**|-32768|최 솟 **`signed short`** 값|
|**SHRT_MAX**|32767|최 댓 **`signed short`** 값|
|**USHRT_MAX**|65535(0xffff)|최 댓 **`unsigned short`** 값|
|**INT_MIN**|(-2147483647 - 1)|최 솟 **`signed int`** 값|
|**INT_MAX**|2147483647|최 댓 **`signed int`** 값|
|**UINT_MAX**|4294967295(0xffffffff)|최 댓 **`unsigned int`** 값|
|**LONG_MIN**|(-2147483647L - 1)|최 솟 **`signed long`** 값|
|**LONG_MAX**|2147483647L|최 댓 **`signed long`** 값|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|최 댓 **`unsigned long`** 값|
|**LLONG_MIN**|(-9223372036854775807LL - 1)|최소값 **`signed long long`** 또는 **`__int64`** 값|
|**LLONG_MAX**|9223372036854775807LL|최대값 **`signed long long`** 또는 **`__int64`** 값|
|**ULLONG_MAX**|0xffffffffffffffffull|최 댓 **`unsigned long long`** 값|
|**_I8_MIN**|(-127i8 - 1)|최소 signed 8비트 값|
|**_I8_MAX**|127i8|최대 signed 8비트 값|
|**_UI8_MAX**|0xffui8|최대 unsigned 8비트 값|
|**_I16_MIN**|(-32767i16 - 1)|최소 signed 16비트 값|
|**_I16_MAX**|32767i16|최대 signed 16비트 값|
|**_UI16_MAX**|0xffffui16|최대 unsigned 16비트 값|
|**_I32_MIN**|(-2147483647i32 - 1)|최소 signed 32비트 값|
|**_I32_MAX**|2147483647i32|최대 signed 32비트 값|
|**_UI32_MAX**|0xffffffffui32|최대 unsigned 32비트 값|
|**_I64_MIN**|(-9223372036854775807 - 1)|최소 signed 64비트 값|
|**_I64_MAX**|9223372036854775807|최대 signed 64비트 값|
|**_UI64_MAX**|0xffffffffffffffffui64|최대 unsigned 64비트 값|
|**_I128_MIN**|(-170141183460469231731687303715884105727i128 - 1)|최소 signed 128비트 값|
|**_I128_MAX**|170141183460469231731687303715884105727i128|최대 signed 128비트 값|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|최대 unsigned 128비트 값|
|**SIZE_MAX**|**_WIN64** 가 정의된 경우 **_UI64_MAX** 와 동일하거나, **UINT_MAX**|최대 기본 정수 크기|
|**RSIZE_MAX**|(**SIZE_MAX** >> 1)와 동일|최대 보안 라이브러리 정수 크기|

## <a name="floating-point-type-constants"></a>부동 소수점 형식 상수

다음 상수는 **`long double`** , **`double`** 및 데이터 형식의 범위와 기타 특성을 제공 합니다 **`float`** . 이러한 상수를 사용하려면 소스 파일에 float.h 헤더를 포함시킵니다.

```C
#include <float.h>
```

|상수|값|설명|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|반올림한 소수점 이하 자릿수(#)|
|**DBL_DIG**|15|전체 자릿수|
|**DBL_EPSILON**|2.2204460492503131e-016|1.0 + **DBL_EPSILON** ! = 1.0인 최솟값|
|**DBL_HAS_SUBNORM**|1|형식은 비정상(비정규) 숫자를 지원함|
|**DBL_MANT_DIG**|53|유효 숫자(가수)의 비트 수(#)|
|**DBL_MAX**|1.7976931348623158e+308|최대값|
|**DBL_MAX_10_EXP**|308|최대 10진수 지수|
|**DBL_MAX_EXP**|1024|최대 이진 지수|
|**DBL_MIN**|2.2250738585072014e-308|최소 정규화된 양수 값|
|**DBL_MIN_10_EXP**|(-307)|최소 10진수 지수|
|**DBL_MIN_EXP**|(-1021)|최소 이진 지수|
|**_DBL_RADIX**|2|지수 기수|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|최소 비정상 양수 값|
|**FLT_DECIMAL_DIG**|9|반올림한 소수점 이하 자릿수|
|**FLT_DIG**|6|전체 자릿수|
|**FLT_EPSILON**|1.192092896e-07F|1.0 + **FLT_EPSILON** ! = 1.0인 최솟값|
|**FLT_HAS_SUBNORM**|1|형식은 비정상(비정규) 숫자를 지원함|
|**FLT_MANT_DIG**|24|유효 숫자(가수)의 비트 수|
|**FLT_MAX**|3.402823466e+38F|최대값|
|**FLT_MAX_10_EXP**|38|최대 10진수 지수|
|**FLT_MAX_EXP**|128|최대 이진 지수|
|**FLT_MIN**|1.175494351e-38F|최소 정규화된 양수 값|
|**FLT_MIN_10_EXP**|(-37)|최소 10진수 지수|
|**FLT_MIN_EXP**|(-125)|최소 이진 지수|
|**FLT_RADIX**|2|지수 기수|
|**FLT_TRUE_MIN**|1.401298464e-45F|최소 비정상 양수 값|
|**LDBL_DIG**|15|전체 자릿수|
|**LDBL_EPSILON**|2.2204460492503131e-016|1.0 + **LDBL_EPSILON** ! = 1.0인 최솟값|
|**LDBL_HAS_SUBNORM**|1|형식은 비정상(비정규) 숫자를 지원함|
|**LDBL_MANT_DIG**|53|유효 숫자(가수)의 비트 수(#)|
|**LDBL_MAX**|1.7976931348623158e+308|최대값|
|**LDBL_MAX_10_EXP**|308|최대 10진수 지수|
|**LDBL_MAX_EXP**|1024|최대 이진 지수|
|**LDBL_MIN**|2.2250738585072014e-308|최소 정규화된 양수 값|
|**LDBL_MIN_10_EXP**|(-307)|최소 10진수 지수|
|**LDBL_MIN_EXP**|(-1021)|최소 이진 지수|
|**_LDBL_RADIX**|2|지수 기수|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|최소 비정상 양수 값|
|**DECIMAL_DIG**|**DBL_DECIMAL_DIG** 와 동일|반올림한 소수점 이하 기본(double) 자릿수|

## <a name="see-also"></a>참고 항목

[전역 상수](../c-runtime-library/global-constants.md)
