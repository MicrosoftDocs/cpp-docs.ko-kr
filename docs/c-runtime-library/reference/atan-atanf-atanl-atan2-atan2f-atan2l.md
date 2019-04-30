---
title: atan, atanf, atanl, atan2, atan2f, atan2l
ms.date: 04/05/2018
apiname:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
apilocation:
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
apitype: DLLExport
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
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
ms.openlocfilehash: 59a67b0d213a11630f551fd7582b44aab60e314f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341719"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

아크탄젠트를 계산 **x** (**atan**하십시오 **atanf**, 및 **atanl**) 또는의 아크탄젠트 **y** / **x** (**atan2**하십시오 **atan2f**, 및 **atan2l**).

## <a name="syntax"></a>구문

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
```

```cpp
float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>매개 변수

*x*, *y*<br/>
임의의 숫자입니다.

## <a name="return-value"></a>반환 값

**atan** 의 아크탄젠트를 반환 *x* 는 범위-π/2 ~ π/2 라디안에서에서. **atan2** 의 아크탄젠트를 반환 *y*/*x* 범위-π ~ π 라디안에서에서. 하는 경우 *x* 가 0 이면 **atan** 0을 반환 합니다. 하는 경우의 매개 변수가 모두 **atan2** 0, 함수가 0을 반환 합니다. 모든 결과는 라디안 단위입니다.

**atan2** 두 매개 변수의 기호를 사용 하 여 반환 값의 사분면을 결정 합니다.

|입력|SEH 예외|Matherr 예외|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|없음|**_DOMAIN**|

## <a name="remarks"></a>설명

합니다 **atan** 의 아크탄젠트 (역 탄젠트 함수)를 계산 하는 함수 *x*합니다. **atan2** 의 아크탄젠트를 계산 *y*/*x* (있으면 *x* 0 이면 **atan2** 경우 π/2를 반환 합니다 *y* 가 양수 이면-π/2 이면 *y* 음수 또는 0 이면 *y* 은 0입니다.)

**atan** sse2(스트리밍 SIMD 확장 2 ()를 사용 하는 구현 합니다. SSE2 구현의 사용 제한 사항 및 그 사용 방법에 대한 자세한 내용은 [_set_SSE2_enable](set-sse2-enable.md)을 참조하세요.

때문에 C++ 오버 로드를 사용 하면 오버 로드를 호출할 수 있습니다 **atan** 하 고 **atan2** 사용 하는 **float** 또는 **긴**  **double** 인수입니다. C 프로그램에서 **atan** 하 고 **atan2** 항상 **double** 인수 및 반환을 **double**합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------|-|
|**atan**, **atan2**, **atanf**, **atan2f**, **atanl**, **atan2l**|\<math.h>|\<cmath> 또는 \<math.h>|

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

## <a name="see-also"></a>참고자료

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
