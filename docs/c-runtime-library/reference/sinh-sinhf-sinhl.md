---
title: sinh, sinhf, sinhl
description: 부동 소수점 값의 하이퍼볼릭 사인을 계산 하기 위한 API 참조입니다.
ms.date: 1/15/2021
api_name:
- sinh
- sinhl
- sinhf
- sinhl
- _o_sinh
- _o_sinhf
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
- sinh
- sinhf
- sinhl
helpviewer_keywords:
- sinh function
- sinhl function
- sinhf function
- calculating hyperbolic sines
- trigonometric functions
- sinhf function
- sinhl function
- hyperbolic functions
ms.openlocfilehash: 73f7210105419c4b8cb9a6e47e5c5f0e43437738
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563798"
---
# <a name="sinh-sinhf-sinhl"></a>`sinh`, `sinhf`, `sinhl`

하이퍼볼릭 사인을 계산 합니다.

## <a name="syntax"></a>구문

```C
double sinh(double x);
float sinhf(float x);
long double sinhl(long double x);
#define sinh(x) // Requires C11 or higher

float sinh(float x);  // C++ only
long double sinh(long double x);  // C++ only
```

### <a name="parameters"></a>매개 변수

*`x`*\
각도(라디안)입니다.

## <a name="return-value"></a>반환 값

**`sinh`** 함수는의 쌍곡선 사인을 반환 합니다 *`x`* . 기본적으로 결과가 너무 클 경우를 **`sinh`** 로 설정 하 **`errno`** **`ERANGE`** 고 ±를 반환 **`HUGE_VAL`** 합니다.

|입력|SEH 예외|`Matherr` 발생할|
|-----------|-------------------|-----------------------|
|± `QNAN`,`IND`|없음|`_DOMAIN`|
|&#124;x&#124; ≥ 7.104760 e + 002|`OVERFLOW+INEXACT`|`OVERFLOW`|

반환 코드에 대 한 자세한 내용은,, [ `errno` `_doserrno` `_sys_errlist` 및 `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하십시오.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **`sinh`** 또는 값을 사용 하 고 반환 하는의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서이 함수를 호출 하는 매크로를 사용 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`sinh`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `sinh()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-|-|-|
|**`sinh`**, **`sinhf`**, **`sinhl`**|`<math.h>`|`<cmath>` 또는 `<math.h>`|
|**`sinh()`** 매크로나 | `<tgmath.h>` ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_sinhcosh.c
// This program displays the hyperbolic
// sine and hyperbolic cosine of pi / 2.
// Compile by using: cl /W4 crt_sinhcosh.c

#include <math.h>
#include <stdio.h>

int main( void)
{
   double pi = 3.1415926535;
   double x, y;

   x = pi / 2;
   y = sinh( x );
   printf( "sinh( %f ) = %f\n",x, y );
   y = cosh( x );
   printf( "cosh( %f ) = %f\n",x, y );
}
```

```Output
sinh( 1.570796 ) = 2.301299
cosh( 1.570796 ) = 2.509178
```

## <a name="see-also"></a>참조

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`acosh`, `acoshf`, `acoshl`](acosh-acoshf-acoshl.md)\
[`asinh`, `asinhf`, `asinhl`](asinh-asinhf-asinhl.md)\
[`atanh`, `atanhf`, `atanhl`](atanh-atanhf-atanhl.md)\
[`cosh`, `coshf`, `coshl`](cosh-coshf-coshl.md)\
[`tanh`, `tanhf`, `tanhl`](tanh-tanhf-tanhl.md)