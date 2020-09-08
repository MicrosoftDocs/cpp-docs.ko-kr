---
title: frexp, frexpf, frexpl
description: Frexp, frexpf 및 frexpl에 대 한 API 참조 부동 소수점 숫자의가 수와 지 수를 가져옵니다.
ms.date: 9/1/2020
api_name:
- frexp
- _o_frexp
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
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: a23de4160abcfab2518125bfa0fd35a389901674
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555750"
---
# <a name="frexp-frexpf-frexpl"></a>frexp, frexpf, frexpl

부동 소수점 숫자의 가수 및 지수를 가져옵니다.

## <a name="syntax"></a>구문

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
#define frexpl(X, INT_PTR) // Requires C11 or higher
```

```cpp
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>매개 변수

*.x*\
부동 소수점 값입니다.

*예기치 않은 ptr*\
저장된 정수 지수에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

**frexp** 는가 나를 반환 합니다. *X* 가 0 이면 함수는가 수와 지 수 모두에 대해 0을 반환 합니다. *예기치 않은 ptr* 이 **NULL**인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 0을 반환 합니다.

## <a name="remarks"></a>설명

**Frexp** 함수는 부동 소수점 값 (*x*)을가 수 (*m*)로, 지 수 (*n*)를 구분 합니다 .이 값은 *m* 의 절대값은 0.5 보다 크거나 같고 1.0 보다 작은 경우 *x*  =  *m* * 2<sup>*n*</sup>입니다. 정수 지 수 *n* 은 임의의 *ptr*에서 가리키는 위치에 저장 됩니다.

C + +에서는 오버 로드를 허용 하므로 **frexp**의 오버 로드를 호출할 수 있습니다. C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **frexp** 는 항상 **`double`** 및 포인터를 사용 **`int`** 하 고를 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `frexp()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|필수 헤더|
|--------------|---------------------|
|**frexp**, **frexpf**, **frexpl**|\<math.h>|
|**frexp** 매크로 | \<tgmath.h> |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
