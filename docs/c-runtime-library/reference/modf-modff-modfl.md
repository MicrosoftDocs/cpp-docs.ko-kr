---
title: modf, modff, modfl
description: Modf, modf 및 modf에 대 한 API 참조 부동 소수점 값을 소수 부분과 정수 부분으로 분할 합니다.
ms.date: 1/15/2021
api_name:
- modff
- modf
- modfl
- _o_modf
- _o_modff
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
ms.openlocfilehash: fbc68c3369e8b992350534e3baa5f19b0f2a5e39
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564020"
---
# <a name="modf-modff-modfl"></a>`modf`, `modff`, `modfl`

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

*`x`*\
부동 소수점 값입니다.

*`intptr`*\
저장된 정수 부분에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

이 함수는의 부호 있는 소수 부분을 반환 합니다 *`x`* . 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

**Modf** 함수는 부동 소수점 값을 *`x`* 소수 부분과 정수 부분으로 분할 합니다. 각 부분은 동일한 부호를 가집니다 *`x`* . 의 부호 있는 소수 부분이 *`x`* 반환 됩니다. 정수 부분은에서 부동 소수점 값으로 저장 됩니다 *`intptr`* .

**modf** 에는 SSE2 (스트리밍 SIMD 확장 2)를 사용 하는 구현이 있습니다. [`_set_SSE2_enable`](set-sse2-enable.md)SSE2 구현 사용에 대 한 자세한 내용은을 참조 하십시오.

C + +에서는 오버 로드를 허용 하므로 **`modf`** **`float`** 또는 매개 변수를 사용 하 고 반환 하는의 오버 로드를 호출할 수 있습니다 **`long double`** . C 프로그램에서은 **`modf`** 항상 두 개의 double 값을 사용 하 고 double 값을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`modf`**, **`modff`**, **`modfl`**|C `<math.h>`<br /><br /> C + +: `<cmath>` 또는 `<math.h>`|

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

## <a name="see-also"></a>참조

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`frexp`](frexp.md)\
[`ldexp`](ldexp.md)