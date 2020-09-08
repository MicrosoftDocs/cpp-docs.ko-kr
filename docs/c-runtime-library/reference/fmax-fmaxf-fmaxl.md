---
title: fmax, fmaxf, fmaxl
description: Fmax, fmaxf 및 fmaxl에 대 한 API 참조 두 숫자 값 중 더 큰 값을 결정 합니다.
ms.date: 9/1/2020
api_name:
- fmax
- fmaxf
- fmaxl
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 4f38db64b30598e7cfb4eb4d0f57dccf257dabc5
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556686"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

지정된 두 개의 숫자 값 중 더 큰 값을 확인합니다.

## <a name="syntax"></a>구문

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

#define fmax(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*.x*\
비교할 첫 번째 값입니다.

*x.y*\
비교할 두 번째 값입니다.

## <a name="return-value"></a>반환 값

성공 하면 *x* 또는 *y*중 더 큰 값을 반환 합니다. 반환 값은 정확하고 반올림 형식의 영향을 받지 않습니다.

그렇지 않으면 다음 값 중 하나를 반환할 수 있습니다.

|문제|반환 값|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* 및 *y* = NaN|NaN|

이 함수는 [_matherr](matherr.md)에 지정된 오류를 사용하지 않습니다.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 및 형식을 사용 하 고 반환 하는 fmax의 오버 로드를 호출할 수 있습니다 `float` `long double` . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우는 \<tgmath.h> `fmax` 항상 double을 사용 하 고 반환 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `fmax()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**fmax**, **fmaxf**, **fmaxl**|\<math.h>|\<cmath> 또는 \<math.h>|
|**fmax** 매크로 | \<tgmath.h> ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
