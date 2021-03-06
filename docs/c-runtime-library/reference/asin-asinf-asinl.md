---
title: asin, asinf, asinl
description: Asin, asinf 및 asinl에 대 한 API 참조 부동 소수점 값의 아크사인을 계산 합니다.
ms.date: 1/15/2021
api_name:
- asinf
- asinl
- asin
- _o_asin
- _o_asinf
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
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.openlocfilehash: 04b68e9b5933d763cecbdc06af3e34a5b7c01223
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564045"
---
# <a name="asin-asinf-asinl"></a>`asin`, `asinf`, `asinl`

아크사인을 계산합니다.

## <a name="syntax"></a>구문

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
#define asin(X) // Requires C11 or higher

float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>매개 변수

*`x`*\
아크사인을 계산해야 하는 값입니다.

## <a name="return-value"></a>반환 값

**`asin`** 함수는 *`x`* -π/2 ~ π/2 라디안 범위에서의 아크사인 (역 사인 함수)을 반환 합니다.

기본적으로 *`x`* 가-1 보다 작거나 1 보다 큰 경우는 무한을 **`asin`** 반환 합니다.

|입력|SEH 예외|Matherr 예외|
|-----------|-------------------|-----------------------|
|± ∞|**`INVALID`**|**`_DOMAIN`**|
|± **`QNAN`**, **`IND`**|없음|**`_DOMAIN`**|
|&#124;x&#124;>1|**`INVALID`**|**`_DOMAIN`**|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 및 값을 사용 하 여의 오버 로드를 호출할 수 있습니다 **`asin`** **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`asin`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `asin()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------|-|
|**`asin`**, **`asinf`**, **`asinl`**|`<math.h>`|`<cmath>` 또는 `<math.h>`|
|**`asin()`** 매크로나 | `<tgmath.h>` ||

## <a name="example"></a>예제

자세한 내용은, [ `acos` `acosf` , `acosl` ](acos-acosf-acosl.md)을 참조 하십시오.

## <a name="see-also"></a>추가 정보

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`acos`, `acosf`, `acosl`](acos-acosf-acosl.md)\
[`atan`, `atanf`, `atanl`, `atan2`, `atan2f`, `atan2l`](atan-atanf-atanl-atan2-atan2f-atan2l.md)\
[`cos`, `cosf`, `cosl`](cos-cosf-cosl.md)\
[`_matherr`](matherr.md)\
[`sin`, `sinf`, `sinl`](sin-sinf-sinl.md)\
[`tan`, `tanf`, `tanl`](tan-tanf-tanl.md)