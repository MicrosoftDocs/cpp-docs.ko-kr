---
description: '자세한 정보: C 및 C++ 정수 제한'
title: C 및 C++ 정수 제한
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: c9d15e5366acb482f688e1c5020c43ee83e4e802
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292977"
---
# <a name="c-and-c-integer-limits"></a>C 및 C++ 정수 제한

**Microsoft 전용**

다음 표에서는 C 및 C++의 정수 형식에 대한 제한 사항을 보여 줍니다. 이 제한 사항은 C 표준 헤더 파일 `<limits.h>`에 정의되어 있습니다. C++ 표준 라이브러리 헤더 `<limits>`에는 `<limits.h>`를 비롯한 `<climits>`가 포함되어 있습니다.

Microsoft C에서는 정수 변수를 8비트, 16비트, 32비트 또는 64비트의 정수 계열 형식으로 크기를 지정하여 선언할 수 있습니다. C에서 크기가 지정된 정수에 대한 자세한 내용은 [크기 지정 정수 형식](../c-language/c-sized-integer-types.md)을 참조하세요.

## <a name="limits-on-integer-constants"></a>정수 상수에 대한 제한

|**상수**|의미|값|
|------------------|-------------|-----------|
|**CHAR_BIT**|비트 필드가 없는 가장 작은 변수의 비트 수입니다.|8|
|**SCHAR_MIN**|**`signed char`** 형식 변수의 최소값입니다.|-128|
|**SCHAR_MAX**|**`signed char`** 형식 변수의 최대값입니다.|127|
|**UCHAR_MAX**|**`unsigned char`** 형식 변수의 최대값입니다.|255(0Xff)|
|**CHAR_MIN**|**`char`** 형식 변수의 최소값입니다.|–128, /J 옵션이 사용된 경우 0|
|**CHAR_MAX**|**`char`** 형식 변수의 최대값입니다.|127, /J 옵션이 사용된 경우, 255|
|**MB_LEN_MAX**|여러 문자 상수에서의 최대 바이트 수입니다.|5|
|**SHRT_MIN**|**`short`** 형식 변수의 최소값입니다.|-32768|
|**SHRT_MAX**|**`short`** 형식 변수의 최대값입니다.|32767|
|**USHRT_MAX**|**`unsigned short`** 형식 변수의 최대값입니다.|65535(0xffff)|
|**INT_MIN**|**`int`** 형식 변수의 최소값입니다.|-2147483647 - 1|
|**INT_MAX**|**`int`** 형식 변수의 최대값입니다.|2147483647|
|**UINT_MAX**|**`unsigned int`** 형식 변수의 최대값입니다.|4294967295(0xffffffff)|
|**LONG_MIN**|**`long`** 형식 변수의 최소값입니다.|-2147483647 - 1|
|**LONG_MAX**|**`long`** 형식 변수의 최대값입니다.|2147483647|
|**ULONG_MAX**|**`unsigned long`** 형식 변수의 최대값입니다.|4294967295(0xffffffff)|
|**LLONG_MIN**|**`long long`** 형식 변수의 최소값입니다.|-9,223,372,036,854,775,807 - 1|
|**LLONG_MAX**|**`long long`** 형식 변수의 최대값입니다.|9,223,372,036,854,775,807|
|**ULLONG_MAX**|**`unsigned long long`** 형식 변수의 최대값입니다.|18,446,744,073,709,551,615 (0xffffffffffffffff)|

값이 최대 정수 표현을 초과하는 경우 Microsoft 컴파일러에서 오류가 발생합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 정수 상수](../c-language/c-integer-constants.md)
