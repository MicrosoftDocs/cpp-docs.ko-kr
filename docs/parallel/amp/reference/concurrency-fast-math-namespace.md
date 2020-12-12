---
description: '자세히 알아보기: Concurrency:: fast_math 네임 스페이스'
title: Concurrency::fast_math 네임스페이스
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 99638e3d8b0a452774d1e92d408ce3edddfa861c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122371"
---
# <a name="concurrencyfast_math-namespace"></a>Concurrency::fast_math 네임스페이스

네임 스페이스의 함수는 `fast_math` 정확도가 낮고, 단 정밀도 ()만 지원 **`float`** 하며, DirectX 내장 함수를 호출 합니다. 각 함수의 두 가지 버전 (예: 및)이 있습니다 `cos` `cosf` . 두 버전 모두를 사용 하 여 반환 **`float`** 하지만 각각 동일한 DirectX 내장 함수를 호출 합니다.

## <a name="syntax"></a>구문

```cpp
namespace fast_math;
```

## <a name="members"></a>멤버

### <a name="functions"></a>Functions

|Name|설명|
|----------|-----------------|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|인수의 아크코사인을 계산 합니다.|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|인수의 아크코사인을 계산 합니다.|
|[asin](concurrency-fast-math-namespace-functions.md#asin)|인수의 아크사인을 계산 합니다.|
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|인수의 아크사인을 계산 합니다.|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|인수의 아크탄젠트를 계산합니다.|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|_Y/_X의 아크탄젠트를 계산 합니다.|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|_Y/_X의 아크탄젠트를 계산 합니다.|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|인수의 아크탄젠트를 계산합니다.|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|인수의 최대값을 계산 합니다.|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|인수의 최대값을 계산 합니다.|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|인수의 코사인을 계산합니다.|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|인수의 코사인을 계산합니다.|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|인수의 하이퍼볼릭 코사인 값을 계산 합니다.|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|인수의 하이퍼볼릭 코사인 값을 계산 합니다.|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|인수의 밑이 e 인 지 수를 계산 합니다.|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|인수의 밑이 2 인 지 수를 계산 합니다.|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|인수의 밑이 2 인 지 수를 계산 합니다.|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|인수의 밑이 e 인 지 수를 계산 합니다.|
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|인수의 절대 값을 반환 합니다.|
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|인수의 절대 값을 반환 합니다.|
|[평면](concurrency-fast-math-namespace-functions.md#floor)|인수의 바닥을 계산 합니다.|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|인수의 바닥을 계산 합니다.|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|인수의 최대 숫자 값을 결정 합니다.|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|인수의 최대 숫자 값을 결정 합니다.|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|인수의 최소 숫자 값을 확인 합니다.|
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|인수의 최소 숫자 값을 확인 합니다.|
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|_X/_Y의 부동 소수점 나머지를 계산 합니다.|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|_X/_Y의 부동 소수점 나머지를 계산 합니다.|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|의가 수와 지 수를 가져옵니다 _X|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|의가 수와 지 수를 가져옵니다 _X|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|인수에 유한 값이 있는지 여부를 확인 합니다.|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|인수가 무한대 인지 여부를 확인 합니다.|
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|인수가 NaN 인지 여부를 확인 합니다.|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|가 수 및 지 수에서 실수를 계산 합니다.|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|가 수 및 지 수에서 실수를 계산 합니다.|
|[로깅할](concurrency-fast-math-namespace-functions.md#log)|인수의 밑이 e 인 로그를 계산 합니다.|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|인수의 밑이 10 인 로그를 계산 합니다.|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|인수의 밑이 10 인 로그를 계산 합니다.|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|인수의 밑이 2 인 로그를 계산 합니다.|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|인수의 밑이 2 인 로그를 계산 합니다.|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|인수의 밑이 e 인 로그를 계산 합니다.|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|_X을 소수 부분과 정수 부분으로 분할 합니다.|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|_X을 소수 부분과 정수 부분으로 분할 합니다.|
|[pow](concurrency-fast-math-namespace-functions.md#pow)|_Y의 거듭제곱으로 발생 한 _X 계산 합니다.|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|_Y의 거듭제곱으로 발생 한 _X 계산 합니다.|
|[둥근](concurrency-fast-math-namespace-functions.md#round)|_X를 가장 가까운 정수로 반올림 합니다.|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|_X를 가장 가까운 정수로 반올림 합니다.|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|인수의 제곱근의 역을 반환 합니다.|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|인수의 제곱근의 역을 반환 합니다.|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|인수의 부호를 반환 합니다.|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|인수의 부호를 반환 합니다.|
|[사인](concurrency-fast-math-namespace-functions.md#sin)|인수의 사인 값을 계산 합니다.|
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|_X의 사인 및 코사인 값을 계산 합니다.|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|_X의 사인 및 코사인 값을 계산 합니다.|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|인수의 사인 값을 계산 합니다.|
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|인수의 하이퍼볼릭 사인 값을 계산 합니다.|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|인수의 하이퍼볼릭 사인 값을 계산 합니다.|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|인수의 제곱근을 계산 합니다.|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|인수의 제곱근을 계산 합니다.|
|[tan](concurrency-fast-math-namespace-functions.md#tan)|인수의 탄젠트 값을 계산 합니다.|
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|인수의 탄젠트 값을 계산 합니다.|
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|인수의 하이퍼볼릭 탄젠트 값을 계산 합니다.|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|인수의 하이퍼볼릭 탄젠트 값을 계산 합니다.|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|인수를 정수 구성 요소로 자릅니다.|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|인수를 정수 구성 요소로 자릅니다.|

## <a name="requirements"></a>요구 사항

**헤더:** amp_math. h

**네임 스페이스:** Concurrency:: fast_math

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
