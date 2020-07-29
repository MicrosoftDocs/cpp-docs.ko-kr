---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 4/2/2020
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
- _o_llrint
- _o_llrintf
- _o_llrintl
- _o_lrint
- _o_lrintf
- _o_lrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: c692b97598e2342628c3171fc22aeead9c864d60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216910"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

현재 반올림 모드 및 방향을 사용하여 지정된 부동 소수점 값을 가장 가까운 정수 값으로 반올림합니다.

## <a name="syntax"></a>구문

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
반올림할 값입니다.

## <a name="return-value"></a>Return Value

성공 하면 *x*의 반올림 된 정수 값을 반환 합니다.

|문제|반환 값|
|-----------|------------|
|*x* 가 반환 형식 범위를 벗어났습니다.<br /><br /> *x* = ± ∞<br /><br /> *x* = NaN|**FE_INVALID** 발생 하 고 0을 반환 합니다.|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 및 형식을 사용 하는 **lrint** 및 **llrint** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 **lrint** 및 **llrint** 는 항상를 사용 **`double`** 합니다.

*X* 가 정수 계열 값에 해당 하는 부동 소수점 값을 나타내지 않는 경우 이러한 함수는 **FE_INEXACT**을 발생 시킵니다.

**Microsoft**전용: 결과가 반환 형식 범위를 벗어났거나 매개 변수가 NaN 또는 무한대 인 경우 반환 값은 정의 된 구현입니다. Microsoft 컴파일러는 0 값을 반환합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
