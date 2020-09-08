---
title: sqrt, sqrtf, sqrtl
description: Sqrt, sqrtf 및 sqrtf에 대 한 API 참조 부동 소수점 숫자의 제곱근을 계산 합니다.
ms.date: 08/31/2020
api_name:
- sqrtl
- sqrtf
- sqrt
- _o_sqrt
- _o_sqrtf
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- sqrt
- sqrtf
- _sqrtl
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
ms.openlocfilehash: 17526b4e4a7eca5d36c01069dbe975bb035d1f58
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556777"
---
# <a name="sqrt-sqrtf-sqrtl"></a>sqrt, sqrtf, sqrtl

제곱근을 계산합니다.

## <a name="syntax"></a>구문

```C
double sqrt(
   double x
);
float sqrt(
   float x
);  // C++ only
long double sqrt(
   long double x
);  // C++ only
float sqrtf(
   float x
);
long double sqrtl(
   long double x
);
#define sqrt(x) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*.x*\
음수가 아닌 부동 소수점 값

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 또는 형식을 사용 하는 **sqrt** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우 sqrt는 항상를 사용 하 \<tgmath.h> 고 반환 **sqrt** **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `sqrt()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="return-value"></a>반환 값

**Sqrt** 함수는 *x*의 제곱근을 반환 합니다. 기본적으로 *x* 가 음수 이면 **Sqrt** 가 무한 NaN을 반환 합니다.

|입력|SEH 예외|**_matherr** 발생할|
|-----------|-------------------|--------------------------|
|± QNAN,IND|없음|_DOMAIN|
|- ∞|없음|_DOMAIN|
|x<0|없음|_DOMAIN|

## <a name="requirements"></a>요구 사항

|기능|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**sqrt**, **sqrtf**, **sqrtf**|\<math.h>|\<cmath>|
|**sqrt ()** 매크로 | \<tgmath.h> ||

호환성에 대한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_sqrt.c
// This program calculates a square root.

#include <math.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   double question = 45.35, answer;
   answer = sqrt( question );
   if( question < 0 )
      printf( "Error: sqrt returns %f\n", answer );
   else
      printf( "The square root of %.2f is %.2f\n", question, answer );
}
```

```Output
The square root of 45.35 is 6.73
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
[_CIsqrt](../../c-runtime-library/cisqrt.md)<br/>
