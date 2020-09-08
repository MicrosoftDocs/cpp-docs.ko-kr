---
title: expm1, expm1f, expm1l
description: Expm1, expm1f 및 expm1에 대 한 API 참조 값의 밑이 e 인 지 수를 계산 하는 1을 뺀 값입니다.
ms.date: 9/1/2020
api_name:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 6d352e91d895cd63c7134faff90bc1bc43a50708
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556504"
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

값의 밑이 e인 지수 - 1을 계산합니다.

## <a name="syntax"></a>구문

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
#define expm1(X) // Requires C11 or higher
```

### <a name="parameters"></a>매개 변수

*.x*\
부동 소수점 지수 값입니다.

## <a name="return-value"></a>반환 값

**Expm1** 함수는 성공 하면 e<sup>x</sup> -1을 나타내는 부동 소수점 값을 반환 합니다. 오버플로 시 **expm1** 는 **HUGE_VAL**을 반환 하 고, **expm1f** 는 **HUGE_VALF**를 반환 하며, **Expm1l** 는 **HUGE_VALL**을 반환 하 고 **errno** 는 **ERANGE**로 설정 됩니다. 반환 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 및 값을 사용 하 고 반환 하는 **expm1** 의 오버 로드를 호출할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 매크로를 사용 하 여이 함수를 호출 하지 않는 한 \<tgmath.h> **expm1** 는 항상를 사용 하 고 반환 **`double`** 합니다.

매크로를 사용 하는 경우 \<tgmath.h> `expm1()` 인수의 형식에 따라 선택 되는 함수 버전이 결정 됩니다. 자세한 내용은 [형식-제네릭](../../c-runtime-library/tgmath.md) 계산을 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**expm1**, **expm1f**, **expm1l**|\<math.h>|
|**expm1** 매크로 | \<tgmath.h> |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
