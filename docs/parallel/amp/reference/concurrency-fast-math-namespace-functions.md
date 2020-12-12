---
description: '자세히 알아보기: Concurrency:: fast_math 네임 스페이스 함수'
title: Concurrency::fast_math 네임스페이스 함수
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: aef9b660b0f707baeb0b7b87da520a0510f89cc2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122436"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math 네임스페이스 함수

:::row:::
   :::column span="":::
      [`acos`](#acos)\
      [`acosf`](#acosf)\
      [`asin`](#asin)\
      [`asinf`](#asinf)\
      [`atan`](#atan)\
      [`atan2`](#atan2)\
      [`atan2f`](#atan2f)\
      [`atanf`](#atanf)\
      [`ceil`](#ceil)\
      [`ceilf`](#ceilf)\
      [`cos`](#cos)\
      [`cosf`](#cosf)\
      [`cosh`](#cosh)\
      [`coshf`](#coshf)\
      [`exp`](#exp)\
      [`exp2`](#exp2)\
      [`exp2f`](#exp2f)
   :::column-end:::
   :::column span="":::
      [`expf`](#expf)\
      [`fabs`](#fabs)\
      [`fabsf`](#fabsf)\
      [`floor`](#floor)\
      [`floorf`](#floorf)\
      [`fmax`](#fmax)\
      [`fmaxf`](#fmaxf)\
      [`fmin`](#fmin)\
      [`fminf`](#fminf)\
      [`fmod`](#fmod)\
      [`fmodf`](#fmodf)\
      [`frexp`](#frexp)\
      [`frexpf`](#frexpf)\
      [`isfinite`](#isfinite)\
      [`isinf`](#isinf)\
      [`isnan`](#isnan)
   :::column-end:::
   :::column span="":::
      [`ldexp`](#ldexp)\
      [`ldexpf`](#ldexpf)\
      [`log`](#log)\
      [`log10`](#log10)\
      [`log10f`](#log10f)\
      [`log2`](#log2)\
      [`log2f`](#log2f)\
      [`logf`](#logf)\
      [`modf`](#modf)\
      [`modff`](#modff)\
      [`pow`](#pow)\
      [`powf`](#powf)\
      [`round`](#round)\
      [`roundf`](#roundf)\
      [`rsqrt`](#rsqrt)\
      [`rsqrtf`](#rsqrtf)
   :::column-end:::
   :::column span="":::
      [`signbit`](#signbit)\
      [`signbitf`](#signbitf)\
      [`sin`](#sin)\
      [`sincos`](#sincos)\
      [`sincosf`](#sincosf)\
      [`sinf`](#sinf)\
      [`sinh`](#sinh)\
      [`sinhf`](#sinhf)\
      [`sqrt`](#sqrt)\
      [`sqrtf`](#sqrtf)\
      [`tan`](#tan)\
      [`tanf`](#tanf)\
      [`tanh`](#tanh)\
      [`tanhf`](#tanhf)\
      [`trunc`](#trunc)\
      [`truncf`](#truncf)
   :::column-end:::
:::row-end:::

## <a name="acos"></a><a name="acos"></a> acos

인수의 아크코사인을 계산 합니다.

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 아크코사인 값을 반환합니다.

## <a name="acosf"></a><a name="acosf"></a> acosf

인수의 아크코사인을 계산 합니다.

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 아크코사인 값을 반환합니다.

## <a name="asin"></a><a name="asin"></a> asin

인수의 아크사인을 계산 합니다.

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 아크사인 값을 반환합니다.

## <a name="asinf"></a><a name="asinf"></a> asinf

인수의 아크사인을 계산 합니다.

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 아크사인 값을 반환합니다.

## <a name="atan"></a><a name="atan"></a> atan

인수의 아크탄젠트를 계산합니다.

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 아크탄젠트 값을 반환합니다.

## <a name="atan2"></a><a name="atan2"></a> atan2

_Y/_X의 아크탄젠트를 계산 합니다.

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Y*<br/>
부동 소수점 값

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_Y/_X의 아크탄젠트 값을 반환합니다.

## <a name="atan2f"></a><a name="atan2f"></a> atan2f

_Y/_X의 아크탄젠트를 계산 합니다.

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Y*<br/>
부동 소수점 값

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_Y/_X의 아크탄젠트 값을 반환합니다.

## <a name="atanf"></a><a name="atanf"></a> atanf

인수의 아크탄젠트를 계산합니다.

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 아크탄젠트 값을 반환합니다.

## <a name="ceil"></a><a name="ceil"></a> ceil

인수의 최대값을 계산 합니다.

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 한계를 반환합니다.

## <a name="ceilf"></a><a name="ceilf"></a> ceilf

인수의 최대값을 계산 합니다.

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 한계를 반환합니다.

## <a name="cosf"></a><a name="cosf"></a> cosf

인수의 코사인을 계산합니다.

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 코사인 값을 반환합니다.

## <a name="coshf"></a><a name="coshf"></a> coshf

인수의 하이퍼볼릭 코사인 값을 계산 합니다.

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 하이퍼볼릭 코사인 값을 반환합니다.

## <a name="cos"></a><a name="cos"></a> cos

인수의 코사인을 계산합니다.

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 코사인 값을 반환합니다.

## <a name="cosh"></a><a name="cosh"></a> cosh

인수의 하이퍼볼릭 코사인 값을 계산 합니다.

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 하이퍼볼릭 코사인 값을 반환합니다.

## <a name="exp"></a><a name="exp"></a> .exp

인수의 밑이 e 인 지 수를 계산 합니다.

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 e인 지수 값을 반환합니다.

## <a name="exp2"></a><a name="exp2"></a> exp2

인수의 밑이 2 인 지 수를 계산 합니다.

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 2인 지수 값을 반환합니다.

## <a name="exp2f"></a><a name="exp2f"></a> exp2f

인수의 밑이 2 인 지 수를 계산 합니다.

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 2인 지수 값을 반환합니다.

## <a name="expf"></a><a name="expf"></a> expf

인수의 밑이 e 인 지 수를 계산 합니다.

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 e인 지수 값을 반환합니다.

## <a name="fabs"></a><a name="fabs"></a> fabs

인수의 절대 값을 반환 합니다.

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
정수 값

### <a name="return-value"></a>반환 값

인수의 절대 값을 반환 합니다.

## <a name="fabsf"></a><a name="fabsf"></a> fabsf

인수의 절대 값을 반환 합니다.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 절대 값을 반환 합니다.

## <a name="floor"></a><a name="floor"></a> 평면

인수의 바닥을 계산 합니다.

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑을 반환합니다.

## <a name="floorf"></a><a name="floorf"></a> floorf

인수의 바닥을 계산 합니다.

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑을 반환합니다.

## <a name="fmax"></a><a name="fmax"></a> fmax

인수의 최대 숫자 값을 결정 합니다.

```cpp
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
정수 값

*_Y*<br/>
정수 값

### <a name="return-value"></a>반환 값

인수의 최대 숫자 값을 반환 합니다.

## <a name="fmaxf"></a><a name="fmaxf"></a> fmaxf

인수의 최대 숫자 값을 결정 합니다.

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Y*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 최대 숫자 값을 반환 합니다.

## <a name="fmin"></a><a name="fmin"></a> fmin

인수의 최소 숫자 값을 확인 합니다.

```cpp
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
정수 값

*_Y*<br/>
정수 값

### <a name="return-value"></a>반환 값

인수의 최소 숫자 값을 반환 합니다.

## <a name="fminf"></a><a name="fminf"></a> fminf

인수의 최소 숫자 값을 확인 합니다.

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Y*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 최소 숫자 값을 반환 합니다.

## <a name="fmod"></a><a name="fmod"></a> fmod

_X/_Y의 부동 소수점 나머지를 계산 합니다.

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Y*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_X/_Y의 부동 소수점 나머지를 반환합니다.

## <a name="fmodf"></a><a name="fmodf"></a> fmodf

_X/_Y의 부동 소수점 나머지를 계산합니다.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Y*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_X/_Y의 부동 소수점 나머지를 반환합니다.

## <a name="frexp"></a><a name="frexp"></a> frexp

의가 수와 지 수를 가져옵니다 _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Exp*<br/>
부동 소수점 값의 _X의 정수 지수를 반환합니다.

### <a name="return-value"></a>반환 값

_X의 가수를 반환합니다.

## <a name="frexpf"></a><a name="frexpf"></a> frexpf

의가 수와 지 수를 가져옵니다 _X

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Exp*<br/>
부동 소수점 값의 _X의 정수 지수를 반환합니다.

### <a name="return-value"></a>반환 값

_X의 가수를 반환합니다.

## <a name="isfinite"></a><a name="isfinite"></a> isfinite

인수에 유한 값이 있는지 여부를 확인 합니다.

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수가 유한인 값인 경우에만 0이 아닌 값을 반환합니다.

## <a name="isinf"></a><a name="isinf"></a> isinf

인수가 무한대 인지 여부를 확인 합니다.

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수가 무한대 값인 경우에 0이 아닌 값을 반환합니다.

## <a name="isnan"></a><a name="isnan"></a> isnan

인수가 NaN 인지 여부를 확인 합니다.

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수가 NaN 값을 갖는 경우에만 0이 아닌 값을 반환합니다.

## <a name="ldexp"></a><a name="ldexp"></a> ldexp

가 수 및 지 수에서 실수를 계산 합니다.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값, 가수

*_Exp*<br/>
정수 지수

### <a name="return-value"></a>반환 값

_X 2 ^ _Exp을 반환 합니다. \*

## <a name="ldexpf"></a><a name="ldexpf"></a> ldexpf

가 수 및 지 수에서 실수를 계산 합니다.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값, 가수

*_Exp*<br/>
정수 지수

### <a name="return-value"></a>반환 값

_X 2 ^ _Exp을 반환 합니다. \*

## <a name="log"></a><a name="log"></a> 로깅할

인수의 밑이 e 인 로그를 계산 합니다.

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 e인 로그 값을 반환합니다.

## <a name="log10"></a><a name="log10"></a> log10

인수의 밑이 10 인 로그를 계산 합니다.

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 10인 로그 값을 반환합니다.

## <a name="log10f"></a><a name="log10f"></a> log10f

인수의 밑이 10 인 로그를 계산 합니다.

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 10인 로그 값을 반환합니다.

## <a name="log2"></a><a name="log2"></a> log2

인수의 밑이 2 인 로그를 계산 합니다.

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 2 인 로그를 반환 합니다.

## <a name="log2f"></a><a name="log2f"></a> log2f

인수의 밑이 2 인 로그를 계산 합니다.

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 10인 로그 값을 반환합니다.

## <a name="logf"></a><a name="logf"></a> logf

인수의 밑이 e 인 로그를 계산 합니다.

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 밑이 e인 로그 값을 반환합니다.

## <a name="modf"></a><a name="modf"></a> modf

_X을 소수 부분과 정수 부분으로 분할 합니다.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Ip*<br/>
값의 정수 부분을 받습니다.

### <a name="return-value"></a>반환 값

_X의 부호 있는 소수 부분을 반환합니다.

## <a name="modff"></a><a name="modff"></a> modff

_X을 소수 부분과 정수 부분으로 분할 합니다.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_Ip*<br/>
값의 정수 부분을 받습니다.

### <a name="return-value"></a>반환 값

_X의 부호 있는 소수 부분을 반환합니다.

## <a name="pow"></a><a name="pow"></a> pow

_Y의 거듭제곱으로 발생 한 _X 계산 합니다.

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값, 밑

*_Y*<br/>
부동 소수점 값, 지수

### <a name="return-value"></a>반환 값

_X의 거듭제곱 값을 반환 _Y

## <a name="powf"></a><a name="powf"></a> powf

_Y의 거듭제곱으로 발생 한 _X 계산 합니다.

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값, 밑

*_Y*<br/>
부동 소수점 값, 지수

### <a name="return-value"></a>반환 값

## <a name="round"></a><a name="round"></a> 둥근

_X를 가장 가까운 정수로 반올림 합니다.

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_X의 가장 가까운 정수를 반환합니다.

## <a name="roundf"></a><a name="roundf"></a> roundf

_X를 가장 가까운 정수로 반올림 합니다.

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_X의 가장 가까운 정수를 반환합니다.

## <a name="rsqrt"></a><a name="rsqrt"></a> rsqrt

인수의 제곱근의 역을 반환 합니다.

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 제곱근의 역을 반환 합니다.

## <a name="rsqrtf"></a><a name="rsqrtf"></a> rsqrtf

인수의 제곱근의 역을 반환 합니다.

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 제곱근의 역을 반환 합니다.

## <a name="signbit"></a><a name="signbit"></a> signbit

_X의 부호가 음수인지 결정합니다.

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_X의 부호가 음수인 경우에만 0이 아닌 값을 반환합니다.

## <a name="signbitf"></a><a name="signbitf"></a> signbitf

_X의 부호가 음수인지 결정합니다.

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

_X의 부호가 음수인 경우에만 0이 아닌 값을 반환합니다.

## <a name="sin"></a><a name="sin"></a> 사인

인수의 사인 값을 계산 합니다.

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 사인 값을 반환합니다.

## <a name="sinf"></a><a name="sinf"></a> sinf

인수의 사인 값을 계산 합니다.

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 사인 값을 반환합니다.

## <a name="sincos"></a><a name="sincos"></a> sincos

_X의 사인 및 코사인 값을 계산 합니다.

```cpp
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_S*<br/>
_X의 사인 값을 반환합니다.

*_C*<br/>
_X의 코사인 값을 반환합니다.

## <a name="sincosf"></a><a name="sincosf"></a> sincosf

_X의 사인 및 코사인 값을 계산 합니다.

```cpp
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

*_S*<br/>
_X의 사인 값을 반환합니다.

*_C*<br/>
_X의 코사인 값을 반환합니다.

## <a name="sinh"></a><a name="sinh"></a> sinh

인수의 하이퍼볼릭 사인 값을 계산 합니다.

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 하이퍼볼릭 사인 값을 반환합니다.

## <a name="sinhf"></a><a name="sinhf"></a> sinhf

인수의 하이퍼볼릭 사인 값을 계산 합니다.

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 하이퍼볼릭 사인 값을 반환합니다.

## <a name="sqrt"></a><a name="sqrt"></a> sqrt

인수의 제곱근을 계산합니다.

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 제곱근을 반환합니다.

## <a name="sqrtf"></a><a name="sqrtf"></a> sqrtf

인수의 제곱근을 계산합니다.

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 제곱근을 반환합니다.

## <a name="tan"></a><a name="tan"></a> tan

인수의 탄젠트 값을 계산 합니다.

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 탄젠트 값을 반환합니다.

## <a name="tanf"></a><a name="tanf"></a> tanf

인수의 탄젠트 값을 계산 합니다.

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 탄젠트 값을 반환합니다.

## <a name="tanh"></a><a name="tanh"></a> tanh

인수의 하이퍼볼릭 탄젠트 값을 계산 합니다.

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 하이퍼볼릭 탄젠트 값을 반환합니다.

## <a name="tanhf"></a><a name="tanhf"></a> tanhf

인수의 하이퍼볼릭 탄젠트 값을 계산 합니다.

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 하이퍼볼릭 탄젠트 값을 반환합니다.

## <a name="trunc"></a><a name="trunc"></a> trunc

인수를 정수 구성 요소로 자릅니다.

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 정수 구성 요소를 반환합니다.

## <a name="truncf"></a><a name="truncf"></a> truncf

인수를 정수 구성 요소로 자릅니다.

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_X*<br/>
부동 소수점 값

### <a name="return-value"></a>반환 값

인수의 정수 구성 요소를 반환합니다.

## <a name="requirements"></a>요구 사항

**헤더:** Amp_math **네임 스페이스:** Concurrency:: fast_math

## <a name="see-also"></a>참고 항목

[Concurrency::fast_math 네임스페이스](concurrency-fast-math-namespace.md)
