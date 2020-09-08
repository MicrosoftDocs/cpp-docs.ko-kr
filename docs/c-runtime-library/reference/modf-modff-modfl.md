---
title: modf, modff, modfl
description: Modf, modf 및 modf에 대 한 API 참조 부동 소수점 값을 소수 부분과 정수 부분으로 분할 합니다.
ms.date: 4/2/2020
api_name:
- modff
- modf
- modfl
- _o_modf
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: 0d3522079acc8a9d2c8409b1cad78e7f50a7f788
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556764"
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl

부동 소수점 값을 소수 부분과 정수 부분으로 분할합니다.

## <a name="syntax"></a>구문

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 값입니다.

*intptr*<br/>
저장된 정수 부분에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

이 함수는 *x*의 부호 있는 소수 부분을 반환합니다. 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

**Modf** 함수는 부동 소수점 값 *x* 를 소수 부분과 정수 부분으로 분할 하 고 각각은 *x*와 동일한 부호를 가집니다. *X* 의 부호 있는 소수 부분이 반환 됩니다. 정수 부분은 *intptr*에 부동 소수점 값으로 저장 됩니다.

**modf** 에는 SSE2 (스트리밍 SIMD 확장 2)를 사용 하는 구현이 있습니다. SSE2 구현의 사용 제한 사항 및 사용 방법에 대한 자세한 내용은 [_set_SSE2_enable](set-sse2-enable.md)을 참조하세요.

C + +에서는 오버 로드를 허용 하므로 또는 매개 변수를 사용 하 고 반환 하는 **modf** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 **modf** 는 항상 두 개의 double 값을 사용 하 고 double 값을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**modf**, **modf**, **modf**|C \<math.h><br /><br /> C + +: \<cmath> 또는 \<math.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
