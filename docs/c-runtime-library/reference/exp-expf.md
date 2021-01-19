---
title: exp, expf, expl
description: Exp, ff 및 기타에 대 한 API 참조 지 수를 계산 합니다.
ms.date: 1/15/2021
api_name:
- expf
- expl
- exp
- _o_exp
- _o_expf
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.openlocfilehash: ac51744fe332fbf378139df11e7d07afe44029ca
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564006"
---
# <a name="exp-expf-expl"></a>`exp`, `expf`, `expl`

지수를 계산합니다.

## <a name="syntax"></a>구문

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
#define exp(z) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*`x`*\
자연 *로그 밑에 exponentiate 하는* 부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**`exp`** 함수는 성공 하면 부동 소수점 매개 변수의 지 수 값을 반환 합니다 *`x`* . 즉, 결과는 e입니다  <sup>*`x`*</sup> . 여기서 *e* 는 자연 로그의 밑입니다. 오버플로 시 함수는 `INF` (infinity)를 반환 하 고 언더플로에서 **`exp`** 0을 반환 합니다.

|입력|SEH 예외|`Matherr` 발생할|
|-----------|-------------------|-----------------------|
|± Quiet NaN, 비활성화|없음|`_DOMAIN`|
|± Infinity|`INVALID`|`_DOMAIN`|
|x ≥ 7.097827e+002|`INEXACT+OVERFLOW`|`OVERFLOW`|
|X ≤ -7.083964e+002|`INEXACT+UNDERFLOW`|`UNDERFLOW`|

**`exp`** 함수는 SSE2 (스트리밍 SIMD 확장 2)를 사용 하는 구현을 포함 합니다. [`_set_SSE2_enable`](set-sse2-enable.md)SSE2 구현 사용에 대 한 자세한 내용은을 참조 하십시오.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **`exp`** 또는 인수를 사용 하는 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`exp`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `exp()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 C 헤더|필수 C++ 헤더|
|--------------|---------------------|---|
|**`exp`**, **`expf`**, **`expl`**|`<math.h>`|`<cmath>` 또는 `<math.h>`|
|**`exp`** 매크로나| `<tgmath.h>` ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>참조

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[l-value`og, logf, log10, log10f`](log-logf-log10-log10f.md)\
[`_CIexp`](../../c-runtime-library/ciexp.md)