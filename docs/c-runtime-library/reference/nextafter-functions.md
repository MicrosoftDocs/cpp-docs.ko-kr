---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
description: Nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nextafter, nexttowardf 및 nexttowardl에 대 한 API 참조 이는 표현 가능한 다음 부동 소수점 값을 반환 합니다.
ms.date: 1/15/2021
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
- _o__nextafterf
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.openlocfilehash: 664ddb204fa089f83acebf6a9042b17a776ea306
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564136"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>`nextafter`, `nextafterf`, `nextafterl`, `_nextafter`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`

표현 가능한 다음 부동 소수점 값을 반환합니다.

## <a name="syntax"></a>구문

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

#define nextafter(X, Y) // Requires C11 or higher

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );

#define nexttoward(X, Y) // Requires C11 or higher

float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>매개 변수

*`x`*\
시작할 부동 소수점 값입니다.

*`y`*\
종료할 부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

의 방향에서 반환 형식의 다음 표현 가능한 부동 소수점 값을 반환 합니다 *`x`* *`y`* . *`x`* 와 *`y`* 가 같으면 함수는 반환 형식으로 변환 된를 반환 하 고 예외는 트리거하지 *`y`* 않습니다. *`x`* 가와 같지 않고 *`y`* 결과가 denormal 이거나 0 이면 **`FE_UNDERFLOW`** 및 부동 소수점 **`FE_INEXACT`** 예외 상태가 설정 되 고 올바른 결과가 반환 됩니다. *`x`* 또는 *`y`* 가 NAN 이면 반환 값은 입력 nan 중 하나입니다. *`x`* 가 유한 하 고 결과가 무한 하거나 형식에서 표현할 수 없는 경우에는 올바르게 서명 된 infinity 또는 NAN이 반환 되 고 **`FE_OVERFLOW`** , **`FE_INEXACT`** 부동 소수점 예외 상태가 설정 되며, **`errno`** 가로 설정 됩니다 **`ERANGE`** .

## <a name="remarks"></a>설명

**`nextafter`** 및 **`nexttoward`** 함수 패밀리는의 매개 변수 형식을 제외 하 고 동일 합니다 *`y`* . *`x`* 와 *`y`* 가 같으면 반환 되는 값이 *`y`* 반환 형식으로 변환 됩니다.

C + +는 오버 로드를 허용 하므로를 포함 하는 경우 및 `<cmath>` **`nextafter`** **`nexttoward`** 형식을 반환 하는 및의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서이 함수를 호출 하는 데 매크로를 사용 하지 않는 경우를 `<tgmath.h>` **`nextafter`** 반환 하 고 항상를 **`nexttoward`** 반환 **`double`** 합니다.

또는 매크로를 사용 하는 경우 `<tgmath.h>` `nextafter()` `nexttoward()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

**_Nextafter** 및 **_Nextafterf** 함수는 Microsoft 전용입니다. **_Nextafterf** 함수는 x 64 용으로 컴파일하는 경우에만 사용할 수 있습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더(C)|필수 헤더(C++)|
|-------------|---------------------------|-------------------------------|
|**`nextafter`**, **`nextafterf`**, **`nextafterl`**, **`_nextafterf`**, **`nexttoward`**, **`nexttowardf`**, **`nexttowardl`**|`<math.h>`|`<math.h>` 또는 `<cmath>`|
|**`_nextafter`**|`<float.h>`|`<float.h>` 또는 `<cfloat>`|
|**`nextafter`** 매크로,  **`nexttoward`** 매크로| `<tgmath.h>` ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>추가 정보

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`isnan`, `_isnan`, `_isnanf`](isnan-isnan-isnanf.md)
