---
title: fmod, fmodf, fmodl
description: Fmod, fmodf 및 fmodl에 대 한 API 참조 부동 소수점 나머지를 계산 합니다.
ms.date: 9/1/2020
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: 2b610dec79c98b973af09f8efb147ad6797f7946
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556088"
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf, fmodl

부동 소수점 나머지를 계산합니다.

## <a name="syntax"></a>구문

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);

#define fmod(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*x*, *y*\
부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**fmod** 는 *x*y의 부동 소수점 나머지를 반환 합니다  /  *y*. *Y* 값이 0.0 이면 **fmod** 가 자동 NaN을 반환 합니다. **Printf** 패밀리의 자동 NaN 표현에 대 한 자세한 내용은 [printf](printf-printf-l-wprintf-wprintf-l.md)를 참조 하세요.

## <a name="remarks"></a>설명

**Fmod** 함수는 x i y f 인 x y의 *부동*소수점 나머지 *f* 를 계산 합니다  /  *y* *x*  =  *i* \* *y*  +  *f*. 여기서 *i* 는 정수이 고 *f* 는 *x*와 같으며 f의 절대값은 *y*의 절대값 보다 작은 *f* 값입니다.

C + +에서는 오버 로드를 허용 하므로 및 값을 사용 하 고 반환 하는 **fmod** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **fmod** 는 항상 두 개의 **`double`** 인수를 사용 하 고을 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `fmod()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|필수 헤더|
|--------------|---------------------|
|**fmod**, **fmodf**, **fmodl**|\<math.h>|
|**fmod** 매크로 | \<tgmath.h> |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
