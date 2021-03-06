---
title: logb, logbf, logbl, _logb, _logbf
description: Logb, logb, logbl, _logb 및 _logbf에 대 한 API 참조 는 부동 소수점 인수의 지 수 값을 추출 합니다.
ms.date: 1/15/2021
api_name:
- logb
- _logb
- _logbl
- logbf
- _logbf
- logbl
- _o__logb
- _o_logb
- _o_logbf
- _o_logbl
- _o__logbf
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.openlocfilehash: 5d64b315a502f7d1794d7726f14a94ed66a67cd5
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564032"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>`logb`, `logbf`, `logbl`, `_logb`, `_logbf`

부동 소수점 인수의 지수 값을 추출합니다.

## <a name="syntax"></a>구문

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
#define logb(X) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*`x`*\
부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**`logb`** 의 비편향 지 수 값을 *`x`* 부동 소수점 값으로 표현 되는 부호 있는 정수로 반환 합니다.

## <a name="remarks"></a>설명

**`logb`** 함수는 *`x`* 무한 범위로 표현 된 것 처럼 부동 소수점 인수의 지 수 값을 추출 합니다 *`x`* . 인수가 정규화 *`x`* 되지 않은 경우 정규화 된 것 처럼 처리 됩니다.

C + +에서는 오버 로드를 허용 하므로 **`logb`** 또는 값을 사용 하 고 반환 하는의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`logb`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `logb()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

|입력|SEH 예외|`Matherr` 발생할|
|-----------|-------------------|-----------------------|
|`± QNAN`,`IND`|없음|`_DOMAIN`|
|± 0|`ZERODIVIDE`|`_SING`|

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`_logb`**|`<float.h>`|
|**`logb`**, **`logbf`**, **`logbl`**, **`_logbf`**|`<math.h>`|
|**`logb`** 매크로나 | `<tgmath.h>` |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>추가 정보

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`frexp`](frexp.md)