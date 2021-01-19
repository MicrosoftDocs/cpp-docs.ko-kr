---
title: tan, tanf, tanl
description: Tan, tanf 및 tanl에 대 한 API 참조 부동 소수점 값의 탄젠트를 계산 합니다.
ms.date: 1/15/2021
api_name:
- tan
- tanf
- tanl
- _o_tan
- _o_tanf
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
- tan
- tanf
- _tanl
- tanl
helpviewer_keywords:
- tanl function
- _tanl function
- tan function
- calculating tangents
- tangent
- tanf function
- trigonometric functions
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
ms.openlocfilehash: 056afdf0bbac422c498bd54c2a154472bfd97c34
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564058"
---
# <a name="tan-tanf-tanl"></a>`tan`, `tanf`, `tanl`

탄젠트를 계산 합니다.

## <a name="syntax"></a>구문

```C
double tan( double x );
float tanf( float x );
long double tanl( long double x );
#define tan(x) // Requires C11 or higher
```

```cpp
float tan( float x );  // C++ only
long double tan( long double x );  // C++ only
```

### <a name="parameters"></a>매개 변수

*`x`*\
각도(라디안)입니다.

## <a name="return-value"></a>반환 값

**`tan`** 함수는의 탄젠트를 반환 합니다 *`x`* . *`x`* 가 263 보다 크거나 같은 경우 또는-263 보다 작거나 같은 경우 결과에 중요 한 손실이 발생 합니다.

|입력|SEH 예외|**`Matherr`** 발생할|
|-----------|-------------------|-------------------------|
|`± QNAN`,`IND`|없음|`_DOMAIN`|
|`± INF`|**올바르지 않음**|`_DOMAIN`|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **`tan`** 또는 값을 사용 하 고 반환 하는의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서이 함수를 호출 하는 매크로를 사용 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`tan`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `tan()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------|-|
|**`tan`**, **`tanf`**, **`tanl`**|`<math.h>`|`<cmath>` 또는 `<math.h>`|
|**`tan()`** 매크로나 | `<tgmath.h>` ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_tan.c
// This program displays the tangent of pi / 4
// Compile by using: cl crt_tan.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x;

   x = tan( pi / 4 );
   printf( "tan( %f ) = %f\n", pi/4, x );
}
```

```Output
tan( 0.785398 ) = 1.000000
```

## <a name="see-also"></a>참조

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`acos, acosf, acosl`](acos-acosf-acosl.md)\
[`asin, asinf, asinl`](asin-asinf-asinl.md)\
[`atan, atanf, atanl, atan2, atan2f, atan2l`](atan-atanf-atanl-atan2-atan2f-atan2l.md)\
[`cos, cosf, cosl`](cos-cosf-cosl.md)\
[`sin, sinf, sinl`](sin-sinf-sinl.md)\
[`_CItan`](../../c-runtime-library/citan.md)