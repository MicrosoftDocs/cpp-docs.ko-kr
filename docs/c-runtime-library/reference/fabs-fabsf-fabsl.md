---
title: fabs, fabsf, fabsl
description: Fabs, fabsf 및 fabsl에 대 한 API 참조 이 값은 부동 소수점 값의 절대값을 계산 합니다.
ms.date: 1/15/2021
api_name:
- fabsf
- fabs
- fabsl
- _o_fabs
- _o_fabsf
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.openlocfilehash: 453965b846dff9affb3fa6dce99ea8b6189a5d6c
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563928"
---
# <a name="fabs-fabsf-fabsl"></a>`fabs`, `fabsf`, `fabsl`

부동 소수점 인수의 절대값을 계산합니다.

## <a name="syntax"></a>구문

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);

#define fabs(X) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*`x`*\
부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**`fabs`** 함수는 인수 *x* 의 절대값을 반환 합니다. 오류가 반환 되지 않습니다.

|입력|SEH 예외|`Matherr` 발생할|
|-----------|-------------------|-----------------------|
|± `QNAN`,`IND`|없음|`_DOMAIN`|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **`fabs`** 헤더를 포함 하는 경우의 오버 로드를 호출할 수 있습니다 `<cmath>` . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 경우는 항상를 사용 하 `<tgmath.h>` **`fabs`** 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 `<tgmath.h>` `fabs()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 C 헤더|필수 C++ 헤더|
|--------------|-----------------------|---------------------------|
|**`fabs`**, **`fabsf`**, **`fabsl`**|`<math.h>`|`<cmath>` 또는 `<math.h>`|
|**`fabs`** 매크로나 | `<tgmath.h>` ||

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

의 예제를 참조 하세요 [`abs`](abs-labs-llabs-abs64.md) .

## <a name="see-also"></a>추가 정보

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`abs, labs, llabs, _abs64`](abs-labs-llabs-abs64.md)\
[`_cabs`](cabs.md)
