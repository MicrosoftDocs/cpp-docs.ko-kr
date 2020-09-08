---
title: erf, erff, erfl, erfc, erfcf, erfcl
description: Erf, erff, erff, erfc, erfcf 및 erff에 대 한 API 참조 이는 값의 오류 함수 또는 보완 오류 함수를 계산 합니다.
ms.date: 9/1/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ef83275515c66341798395bbfc2bb5b088e6cfb7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555646"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

값의 오차 함수 또는 보상 오차 함수를 계산합니다.

## <a name="syntax"></a>구문

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
#define erf(X) // Requires C11 or higher
#define erfc(X) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*.x*\
부동 소수점 값입니다.

## <a name="return-value"></a>반환 값

**Erf** 함수는 *x*의 가우스 오차 함수를 반환 합니다. **Erfc** 함수는 *x*의 보완 가우스 오차 함수를 반환 합니다.

## <a name="remarks"></a>설명

**Erf** 함수는 다음과 같이 정의 되는 *x*의 가우스 오차 함수를 계산 합니다.

![x의 오차 함수](media/crt_erf_formula.PNG "x의 오차 함수")

보완적인 가우스 오류 함수는 erf (x)로 정의 됩니다. **Erf** 함수는-1.0 ~ 1.0 범위의 값을 반환 합니다. 오류가 반환 되지 않습니다. **Erfc** 함수는 0 ~ 2 범위의 값을 반환 합니다. *X* 가 **erfc**에 대해 너무 크면 **errno** 변수는 **ERANGE**로 설정 됩니다.

C + +에서는 오버 로드를 허용 하므로 및 형식을 사용 하 고 반환 하는 **erf** 및 **erfc** 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **erf** 및 **erfc** 는 항상를 사용 하 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `erf()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|필수 헤더|
|--------------|---------------------|
|**erf**, **erff**, **erff**, **erfc**, **erfcf**, **erff**|\<math.h>|
|**erf** 매크로 | \<tgmath.h> |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
