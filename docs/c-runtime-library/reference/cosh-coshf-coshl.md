---
title: cosh, coshf, coshl
description: Cosh, coshf 및 coshl에 대 한 API 참조 부동 소수점 값의 하이퍼볼릭 코사인을 계산 합니다.
ms.date: 1/15/2021
api_name:
- cosh
- coshf
- coshl
- _o_cosh
- _o_coshf
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: c010dcdc30b16f94f55fca99d67b58e5c19370c7
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564097"
---
# <a name="cosh-coshf-coshl"></a>`cosh`, `coshf`, `coshl`

쌍곡선 코사인을 계산 합니다.

## <a name="syntax"></a>구문

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
#define cosh(X) // Requires C11 or higher

float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>매개 변수

*`x`*\
각도(라디안)입니다.

## <a name="return-value"></a>반환 값

의 하이퍼볼릭 코사인입니다 *`x`* .

기본적으로, 또는 호출에서 결과가 너무 클 경우 **`cosh`** **`coshf`** **`coshl`** 함수는를 반환 하 **`HUGE_VAL`** 고 **`errno`** 를로 설정 합니다 **`ERANGE`** .

|입력|SEH 예외|`Matherr` 발생할|
|-----------|-------------------|-----------------------|
|± **`QNAN`**, **`IND`**|없음|**`_DOMAIN`**|
|*`x`* ≥ 7.104760 e + 002|**`INEXACT`**+**`OVERFLOW`**|**`OVERFLOW`**|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **`cosh`** 또는 값을 사용 하 고 반환 하는의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`cosh`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `cosh()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------|-|
|**`coshf`**, **`cosl`**, **`coshl`**|`<math.h>`|`<cmath>` 또는 `<math.h>`|
|**`coshf()`** 매크로나 | `<tgmath.h>` ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[ `sinh` , `sinhf` , `sinhl` ](sinh-sinhf-sinhl.md)의 예제를 참조 하세요.

## <a name="see-also"></a>추가 정보

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`acosh, acoshf, acoshl`](acosh-acoshf-acoshl.md)\
[`asinh, asinhf, asinhl`](asinh-asinhf-asinhl.md)\
[`atanh, atanhf, atanhl`](atanh-atanhf-atanhl.md)\
[`_matherr`](matherr.md)\
[`sinh, sinhf, sinhl`](sinh-sinhf-sinhl.md)\
[`tanh, tanhf, tanhl`](tanh-tanhf-tanhl.md)