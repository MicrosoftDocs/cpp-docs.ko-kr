---
title: trunc, truncf, truncl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- trunc
- truncf
- truncl
apilocation:
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
apitype: DLLExport
f1_keywords:
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
dev_langs:
- C++
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67c179065a6b2c6fc10a4ba6ba87868c8306a2aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409461"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

지정한 부동 소수점 값보다 작거나 같은 가장 가까운 정수를 확인합니다.

## <a name="syntax"></a>구문

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>매개 변수

*x*<br/>
자를 값입니다.

## <a name="return-value"></a>반환 값

성공 하면의 정수 값을 반환 합니다. *x*0으로 반올림 합니다.

그렇지 않으면 다음 중 하나를 반환할 수 있습니다.

|문제|반환|
|-----------|------------|
|*x* ±INFINITY =|x|
|*x* ±0 =|x|
|*x* = NaN|NaN|

오류는 [_matherr](matherr.md)에 지정된 대로 보고됩니다.

## <a name="remarks"></a>설명

C + +는 오버 로딩을 허용 하기 때문에 오버 로드를 호출할 수 있습니다 **trunc** 사용 하 고 반환 **float** 및 **긴** **double** 형식입니다. C 프로그램에서 **trunc** 항상 사용 하 고 반환 된 **double**합니다.

가장 큰 부동 소수점 값은 정확한 정수이므로 이 함수는 자체적으로는 오버플로되지 않습니다. 그러나 값을 정수값으로 반환하여 함수가 오버플로되도록 할 수 있습니다.

부동 소수점에서 정수 계열로 암시적으로 변환하여 값을 내릴 수도 있습니다. 단, 대상 종류에 저장할 수 있는 값만 이렇게 변환할 수 있습니다.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**trunc**, **truncf**, **truncl**|\<math.h>|\<cmath>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
