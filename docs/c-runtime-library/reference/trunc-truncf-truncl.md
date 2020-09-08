---
title: trunc, truncf, truncl
description: Trunc, truncf, truncl에 대 한 API 참조 지정 된 부동 소수점 값 보다 작거나 같은 가장 가까운 정수를 결정 하는입니다.
ms.date: 9/1/2020
api_name:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: f1f2fde95bb944aa461bb95a9ad30fac204552b9
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556634"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

지정한 부동 소수점 값보다 작거나 같은 가장 가까운 정수를 확인합니다.

## <a name="syntax"></a>구문

```C
double trunc( double x );
long double truncl( long double x );
#define trunc(X) // Requires C11 or higher

long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>매개 변수

*.x*\
자를 값입니다.

## <a name="return-value"></a>반환 값

성공 하면 0으로 반올림 되 고 *x*의 정수 값을 반환 합니다.

그렇지 않으면 다음 중 하나를 반환할 수 있습니다.

|문제|반환 값|
|-----------|------------|
|*x* = ± INFINITY|x|
|*x* = ± 0|x|
|*x* = NaN|NaN|

오류는 [_matherr](matherr.md)에 지정된 대로 보고됩니다.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 및 형식을 사용 하 고 반환 하는 **trunc** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **trunc** 는 항상를 사용 하 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `trunc()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

가장 큰 부동 소수점 값은 정확한 정수이므로 이 함수는 자체적으로는 오버플로되지 않습니다. 그러나 값을 정수값으로 반환하여 함수가 오버플로되도록 할 수 있습니다.

부동 소수점에서 정수 계열로 암시적으로 변환하여 값을 내릴 수도 있습니다. 단, 대상 종류에 저장할 수 있는 값만 이렇게 변환할 수 있습니다.

## <a name="requirements"></a>요구 사항

|기능|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**trunc**, **truncf**, **truncl**|\<math.h>|\<cmath>|
|**trunc** 매크로 | \<tgmath.h> ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
