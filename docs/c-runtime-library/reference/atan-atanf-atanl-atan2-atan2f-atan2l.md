---
title: atan, atanf, atanl, atan2, atan2f, atan2l
description: Atan, atanf, atanf, atan2, atan2f 및 atan2l에 대 한 API 참조 부동 소수점 값의 아크탄젠트를 계산 합니다.
ms.date: 1/15/2021
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
- _o_atan2f
- _o_atanf
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.openlocfilehash: bbfc08507bd48e1b9eb0b91350b2b39948d19a5f
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564071"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>`atan`, `atanf`, `atanl`, `atan2`, `atan2f`, `atan2l`

**`x`**(, **`atan`** 및)의 아크탄젠트 **`atanf`** **`atanl`** 또는 **`y`** / **`x`** ( **`atan2`** , **`atan2f`** 및)의 아크탄젠트를 계산 **`atan2l`** 합니다.

## <a name="syntax"></a>구문

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );
#define atan(X) // Requires C11 or higher

float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
#define atan2(Y, X) // Requires C11 or higher

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>매개 변수

*`x`*, *`y`*\
임의의 숫자입니다.

## <a name="return-value"></a>반환 값

**`atan`***`x`*-π/2 ~ π/2 라디안 범위에서의 아크탄젠트를 반환 합니다. **`atan2`***`y`* / *`x`* -π에서 π 라디안 까지의 범위에서의 아크탄젠트를 반환 합니다. *`x`* 가 0 이면는 **`atan`** 0을 반환 합니다. 의 두 매개 변수가 모두 **`atan2`** 0 이면 함수는 0을 반환 합니다. 모든 결과는 라디안 단위입니다.

**`atan2`** 두 매개 변수의 부호를 사용 하 여 반환 값의 사분면을 결정 합니다.

|입력|SEH 예외|Matherr 예외|
|-----------|-------------------|-----------------------|
|± **`QNAN`**, **`IND`**|없음|**`_DOMAIN`**|

## <a name="remarks"></a>설명

**`atan`** 함수는의 아크탄젠트 (역 탄젠트 함수)를 계산 합니다 *`x`* . **`atan2`** 가 0 인 경우의 아크탄젠트를 계산 *`y`* / *`x`* *`x`* 하 고, **`atan2`** 가 양수인 경우 π/2를 반환 하 고, *`y`* 가 음수 이면-π/2를 반환 하 고 *`y`* ,가 0 이면 0을 반환 *`y`* 합니다.

또는 매크로를 사용 하는 경우 `<tgmath.h>` `atan()` `atan2()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

**`atan`** 에는 SSE2 (스트리밍 SIMD 확장 2)를 사용 하는 구현이 있습니다. SSE2 구현 사용에 대 한 자세한 내용 및 제한 사항은을 참조 하십시오 [`_set_SSE2_enable`](set-sse2-enable.md) .

C + +에서는 오버 로드를 허용 하므로 **`atan`** **`atan2`** 또는 인수를 사용 하는 및의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 `<tgmath.h>` 이 함수를 호출 하는 데 매크로를 사용 하지 않는 경우 **`atan`** 및 **`atan2`** 는 항상 인수를 사용 하 **`double`** 고을 반환 **`double`** 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------|-|
|**`atan`**, **`atan2`**, **`atanf`**, **`atan2f`**, **`atanl`**, **`atan2l`**|`<math.h>`|`<cmath>` 또는 `<math.h>`|
|**`atan()`**, **`atan2`** 매크로 | `<tgmath.h>` ||

## <a name="example"></a>예제

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>참조

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`acos`, `acosf`, `acosl`](acos-acosf-acosl.md)\
[`asin`, `asinf`, `asinl`](asin-asinf-asinl.md)\
[`cos`, `cosf`, `cosl`](cos-cosf-cosl.md)\
[`_matherr`](matherr.md)\
[`sin`, `sinf`, `sinl`](sin-sinf-sinl.md)\
[`tan`, `tanf`, `tanl`](tan-tanf-tanl.md)\
[`_CIatan`](../../c-runtime-library/ciatan.md)\
[`_CIatan2`](../../c-runtime-library/ciatan2.md)