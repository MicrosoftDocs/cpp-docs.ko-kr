---
description: '자세한 정보: 부동 소수점 상수에 대한 제한'
title: 부동 소수점 상수에 대한 제한
ms.date: 11/04/2016
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
ms.openlocfilehash: 345e57348843a62b99b1565b8966df682d5fed8c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257162"
---
# <a name="limits-on-floating-point-constants"></a>부동 소수점 상수에 대한 제한

**Microsoft 전용**

다음 표에는 부동서 소수점 상수 값에 대한 제한이 나와 있습니다. 이 정보는 FLOAT.H 헤더 파일에 있습니다.

### <a name="limits-on-floating-point-constants"></a>부동 소수점 상수에 대한 제한

|상수|의미|값|
|--------------|-------------|-----------|
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|소수 자릿수가 *q* 인 부동 소수점 수가 부동 소수점 표현으로 반올림되고 정밀도의 손실 없이 다시 복원될 수 있는 자릿수 *q* 입니다.|6<br />15<br />15|
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|*x* + 1.0이 1.0과 같지 않은 가장 작은 양수 *x* 입니다.|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|
|**FLT_GUARD**||0|
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|부동 소수점 유효 숫자에서 **FLT_RADIX** 로 지정된 기수의 자릿수입니다. 기수는 2입니다. 따라서 이러한 값이 비트를 지정합니다.|24<br />53<br />53|
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|표현 가능한 최대 부동 소수점 수입니다.|3.402823466e+38F<br />1.7976931348623158e+308<br />1.7976931348623158e+308|
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|숫자에 10이 더해진 최대 정수는 표현 가능한 부동 소수점 숫자입니다.|38<br />308<br />308|
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|**FLT_RADIX** 를 해당 수만큼 거듭제곱한 값이 표현 가능한 부동 소수점 수인 최대 정수입니다.|128<br />1024<br />1024|
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|최소 양수 값입니다.|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|숫자에 10이 더해진 최소 음의 정수는 표현 가능한 부동 소수점 숫자입니다.|-37<br />-307<br />-307|
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|**FLT_RADIX** 를 해당 수만큼 거듭제곱한 값이 표현 가능한 부동 소수점 수인 최소 음의 정수입니다.|-125<br />-1021<br />-1021|
|**FLT_NORMALIZE**||0|
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|지수를 표현하는 기수입니다.|2<br />2<br />2|
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|부동 소수점 더하기의 반올림 모드입니다.|1(근사값)<br />1(근사값)<br />1(근사값)|

상기 표의 정보는 이후 구현에서 다를 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 부동 소수점 상수](../c-language/c-floating-point-constants.md)
