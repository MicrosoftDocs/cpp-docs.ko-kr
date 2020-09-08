---
title: fmin, fminf, fminl
description: Fmin, fminf 및 fminl에 대 한 API 참조 두 값 중 더 작은 값을 결정 합니다.
ms.date: 9/1/2020
api_name:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: 6a070835d809c6adcb5b7bfd57b5373886b348ca
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556712"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

지정된 두 값 중 더 작은 값을 확인합니다.

## <a name="syntax"></a>구문

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);

#define fmin(x) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*.x*\
비교할 첫 번째 값입니다.

*x.y*\
비교할 두 번째 값입니다.

## <a name="return-value"></a>반환 값

성공 하면 *x* 또는 *y*중 더 작은 값을 반환 합니다.

|입력|결과|
|-----------|------------|
|*x* 는 NaN입니다.|*y*|
|*y* 는 NaN입니다.|*x*|
|*x* 및 *y* 는 NaN입니다.|NaN|

함수는 [_matherr](matherr.md) 호출 되거나 부동 소수점 예외를 발생 시키거나 **errno**의 값을 변경 하지 않습니다.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 및 형식을 사용 하 고 반환 하는 **fmin** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **fmin** 은 항상를 사용 하 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `fmin()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**fmin**, **fminf**, **fminl**|C \<math.h><br />C + +: \<math.h> 또는 \<cmath>|
|**fmin** 매크로 | \<tgmath.h> ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
