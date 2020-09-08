---
title: fma, fmaf, fmal
description: Fma, fmaf 및 fand에 대 한 API 참조 두 값을 곱하여 세 번째 값을 더한 다음 중간 반올림으로 인 한 전체 자릿수를 잃지 않고 결과를 반올림 합니다.
ms.date: 9/1/2020
api_name:
- fma
- fmaf
- fmal
- _o_fma
- _o_fmaf
- _o_fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: e9ae92c28f24b6281d73450c7cabaad775a84d42
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556699"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

두 값을 곱하여 세 번째 값을 추가한 다음 중간 반올림으로 인 한 전체 자릿수를 잃지 않고 결과를 반올림 합니다.

## <a name="syntax"></a>구문

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);

#define fma(X, Y, Z) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*.x*\
곱할 첫 번째 값입니다.

*x.y*\
곱할 두 번째 값입니다.

*-*\
추가할 값입니다.

## <a name="return-value"></a>반환 값

`(x * y) + z`를 반환합니다. 반환 값은 현재 반올림 형식을 사용하여 반올림됩니다.

그렇지 않으면 다음 값 중 하나를 반환할 수 있습니다.

|문제|반환 값|
|-----------|------------|
|*x* = 무한대, *y* = 0 또는<br /><br /> *x* = 0, *y* = 무한대|NaN|
|*x* 또는 *y* = 정확한 ± infinity, *z* = 반대 기호가 있는 무한대|NaN|
|*x* 또는 *y* = NaN|NaN|
|not (*x* = 0, *y*= 무한) 및 *z* = NaN<br /><br /> not (*x*= 무한, *y*= 0) 및 *z* = NaN|NaN|
|오버플로 범위 오류|± HUGE_VAL, ± HUGE_VALF 또는 ± HUGE_VALL|
|언더플로 범위 오류|올바른 값, 반올림 후.|

오류는 [_matherr](matherr.md)에 지정된 대로 보고됩니다.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 및 형식을 사용 하 고 반환 하는 **fma** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **fma** 는 항상를 사용 하 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `fma()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

이 함수는 무한 정밀도에 도달한 것처럼 값을 계산하고 최종 결과를 반올림합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fanf**|\<math.h>|\<cmath>|
|**fma** 매크로 | \<tgmath.h> ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
