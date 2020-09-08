---
title: remainder, remainderf, remainderl
description: 나머지, remainderf 및 remainderl에 대 한 API 참조 가장 가까운 정수 값으로 반올림 되는 두 부동 소수점 값 몫의 나머지를 계산 하는입니다.
ms.date: 9/1/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: ef2b326bef2288b52dba8988749e030ff0b46077
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556011"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

두 부동 소수점 값 몫의 나머지를 가장 가까운 적분 값으로 반올림하여 계산합니다.

## <a name="syntax"></a>구문

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
#define remainder(X, Y) // Requires C11 or higher

float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>매개 변수

*.x*\
분자입니다.

*x.y*\
분모입니다.

## <a name="return-value"></a>반환 값

*X*y의 부동 소수점 나머지입니다  /  *y*. *Y* 값이 0.0 이면 **나머지가** 자동 NaN을 반환 합니다. **Printf** 패밀리의 자동 NaN 표현에 대 한 자세한 내용은 [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)를 참조 하세요.

## <a name="remarks"></a>설명

**나머지** 함수는 x n y r과 같은 *x*y의 부동 소수점 나머지 *r* 을 계산 합니다  /  *y* *x*  =  *n* \* *y*  +  *r*. 여기서 *n*은 *x*y의 값에 가장 가까운 정수이  /  *y* 고 *n*은 *n*  -  *x*  /  *y* &#124; = 1/2 일 경우에도 &#124; 마찬가지입니다. *R* = 0 인 경우 *r* 은 *x*와 동일한 부호를 가집니다.

C + +에서는 오버 로드를 허용 하므로 또는 값을 사용 하 고 반환 하는 **나머지** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **나머지** 는 항상 두 개의 **`double`** 인수를 사용 하 고를 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `remainder()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|필수 헤더(C)|필수 헤더(C++)|
|--------------|---------------------|-|
|**나머지**, **remainderf**, **remainderl**|\<math.h>|\<cmath> 또는 \<math.h>|
|**나머지** 매크로 | \<tgmath.h> ||

호환성에 대한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[ldiv, lldiv](ldiv-lldiv.md)\
[imaxdiv](imaxdiv.md)\
[fmod, fmodf](fmod-fmodf.md)\
[remquo, remquof, remquol](remquo-remquof-remquol.md)
