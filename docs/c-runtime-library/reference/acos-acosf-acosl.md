---
title: acos, acosf, acosl
description: Acos, acosf, acosf에 대 한 API 참조 부동 소수점 값의 아크코사인을 계산 합니다.
ms.date: 1/15/2021
api_name:
- acosf
- acos
- acosl
- _o_acos
- _o_acosf
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
- acos
- acosl
- acosf
- math/acosf
- math/acosl
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.openlocfilehash: 63a9c9577e252c506191b7a49ec9da6502968095
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563837"
---
# <a name="acos-acosf-acosl"></a>`acos`, `acosf`, `acosl`

아크코사인을 계산합니다.

## <a name="syntax"></a>구문

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
#define acos(X) // Requires C11 or higher

float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>매개 변수

*`x`*\
아크코사인 (역 코사인)을 계산 하는-1과 1 사이의 값입니다.

## <a name="return-value"></a>반환 값

**`acos`** 함수는 0 ~ π 라디안 범위의 *x* 아크코사인을 반환 합니다.

기본적으로 *`x`* 가-1 보다 작거나 1 보다 큰 경우는 무한을 **`acos`** 반환 합니다.

|입력|`SEH` 발생할|`Matherr` 발생할|
|-----------|-------------------|-----------------------|
|`± ∞`|`INVALID`|`_DOMAIN`|
|`± QNAN, IND`|없음|`_DOMAIN`|
|&#124;`x`&#124;>1|`INVALID`|`_DOMAIN`|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **`acos`** 및 형식을 사용 및 반환 하는의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`acos`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `acos()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|----------------------|
|**`acos`**, **`acosf`**, **`acosl`**|`<math.h>`|`<errno.h>`|
|**`acos()`** 매크로나 | `<tgmath.h>` ||

## <a name="example"></a>예제

이 프로그램에서 -1에서 1 사이 범위의 값을 묻는 메시지가 나타납니다. 이 범위를 벗어나는 입력 값은 `_DOMAIN` 오류 메시지를 생성합니다. 올바른 값을 입력하는 경우 프로그램에서 해당 값의 아크사인 및 아크코사인을 인쇄합니다.

```C
// crt_asincos.c
// arguments: 0

#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int ac, char* av[] )
{
    double  x,
            y;
    errno_t err;

    // argument checking
    if (ac != 2)
    {
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",
                   av[0]);
        return 1;
    }

    // Convert argument into a double value
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)
    {
        fprintf_s( stderr, "Error converting argument into ",
                   "double value.\n");
        return 1;
    }

    // Arcsine of X
    y = asin( x );
    printf_s( "Arcsine of %f = %f\n", x, y );

    // Arccosine of X
    y = acos( x );
    printf_s( "Arccosine of %f = %f\n", x, y );
}
```

```Output
Arcsine of 0.000000 = 0.000000
Arccosine of 0.000000 = 1.570796
```

## <a name="see-also"></a>추가 정보

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`asin`, `asinf`, `asinl`](asin-asinf-asinl.md)\
[`atan`, `atanf`, `atanl`, `atan2`, `atan2f`, `atan2l`](atan-atanf-atanl-atan2-atan2f-atan2l.md)\
[`cos`, `cosf`, `cosl`](cos-cosf-cosl.md)\
[`_matherr`](matherr.md)\
[`sin`, `sinf`, `sinl`](sin-sinf-sinl.md)\
[`tan`, `tanf`, `tanl`](tan-tanf-tanl.md)