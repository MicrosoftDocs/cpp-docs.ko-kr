---
title: tanh, tanhf, tanhl
description: Tanh, tanhf 및 tanhl에 대 한 API 참조 부동 소수점 값의 하이퍼볼릭 탄젠트를 계산 합니다.
ms.date: 08/31/2020
api_name:
- tanh
- tanhf
- tanhl
- _o_tanh
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
- tanh
- tanhf
- tanhl
- _tanhl
helpviewer_keywords:
- tanhl function
- _tanhl function
- tanh function
- tanhf function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 5fa93f56ebec5e8aa06c7317534adb12ae9e68e2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556582"
---
# <a name="tanh-tanhf-tanhl"></a>tanh, tanhf, tanhl

하이퍼볼릭 탄젠트를 계산 합니다.

## <a name="syntax"></a>구문

```C
double tanh( double x );
float tanhf( float x );
long double tanhl( long double x );
#define tanh(x) // Requires C11 or higher
```

```cpp
float tanh( float x );  // C++ only
long double tanh( long double x );  // C++ only
```

### <a name="parameters"></a>매개 변수

*.x*\
각도(라디안)입니다.

## <a name="return-value"></a>반환 값

**Tanh** 함수는 *x*의 하이퍼볼릭 탄젠트를 반환 합니다. 오류가 반환 되지 않습니다.

|입력|SEH 예외|**Matherr** 발생할|
|-----------|-------------------|-------------------------|
|± QNAN,IND|없음|_DOMAIN|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 또는 값을 사용 하 고 반환 하는 **tanh** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 tanh는 항상를 사용 하 \<tgmath.h> 고 반환 **tanh** **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `tanh()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C)|
|-------------|---------------------|-|
|**tanh**, **tanhf**, **tanhl**|\<math.h>|\<cmath> 또는 \<math.h>|
|**tanh ()** 매크로 | \<tgmath.h> ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_tanh.c
// This program displays the tangent of pi / 4
// and the hyperbolic tangent of the result.
// Compile by using: cl crt_tanh.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tan( pi / 4 );
   y = tanh( x );
   printf( "tan( %f ) = %f\n", pi/4, x );
   printf( "tanh( %f ) = %f\n", x, y );
}
```

```Output
tan( 0.785398 ) = 1.000000
tanh( 1.000000 ) = 0.761594
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
