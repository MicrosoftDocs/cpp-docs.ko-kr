---
description: '자세한 정보: 부동 소수점 기본 형식'
title: 부동 소수점 기본 형식
ms.date: 4/2/2020
api_name:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
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
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: 05422620a4da907820ed86a61d4e8dc16b37d3f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268966"
---
# <a name="floating-point-primitives"></a>부동 소수점 기본 형식

일부 표준 CRT (C 런타임 라이브러리) 부동 소수점 함수를 구현 하는 데 사용 되는 Microsoft 전용 기본 함수입니다. 여기서는 완전성을 위해 설명 했지만 사용 하지 않는 것이 좋습니다. 이러한 함수 중 일부는 전체 자릿수, 예외 처리 및 IEEE-754 동작에 대 한 준수 문제로 알려져 있으므로 사용 되지 않는 것으로 표시 됩니다. 이전 버전과의 호환성을 위해서만 라이브러리에 존재 합니다. 올바른 동작, 이식성 및 표준 준수를 위해 이러한 함수에 대해 표준 부동 소수점 함수를 사용 하는 것이 좋습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>구문

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 함수 인수입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 부동 소수점 형식에 대 한 CRT 매크로 [fpclassify](fpclassify.md) 의 C 버전을 구현 합니다. 인수 *x* 의 분류는 math에 정의 된 다음 상수 중 하나로 반환 됩니다.

|값|설명|
|-----------|-----------------|
| **FP_NAN** | 자동, 신호 또는 비활성화 상태 NaN |
| **FP_INFINITE** | 양수 또는 음수 무한대 |
| **FP_NORMAL** | 정규화된 0이 아닌 양수 또는 음수 값 |
| **FP_SUBNORMAL** | 긍정 또는 부정 된 subnormal (비 정규화 된) 값 |
| **FP_ZERO** | 양수 또는 음수 0 값 |

자세한 내용은 Microsoft 전용 [_fpclass _fpclassf](fpclass-fpclassf.md) 함수를 사용할 수 있습니다. 이식성을 위해 [fpclassify](fpclassify.md) 매크로 또는 함수를 사용 합니다.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>구문

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 함수 인수입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 CRT에서 [signbit](signbit.md) 매크로 또는 함수를 구현 합니다. 인수 *x* 의 significand (가 수)에서 부호 비트가 설정 된 경우 0이 아닌 값을 반환 하 고 부호 비트가 설정 되지 않은 경우 0을 반환 합니다.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>구문

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>매개 변수

*x*, *y*<br/>
부동 소수점 함수 인수입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 *x* 및 *y* 라는 두 개의 인수를 사용 하 고 math에 정의 된 이러한 상수의 비트 or로 표현 되는 순서 관계를 표시 하는 값을 반환 합니다.

| 값 | 설명 |
|------------|-----------------|
| **_FP_LT** | *x* 는 *y* 보다 작은 것으로 간주할 수 있습니다. |
| **_FP_EQ** | *x* 는 *y* 와 동일한 것으로 간주할 수 있습니다. |
| **_FP_GT** | *x* 는 *y* 보다 큰 것으로 간주할 수 있습니다. |

이러한 기본 형식은 CRT에서 [isgreater, isgreaterequal, isgreater, islessequal, islessgreater 및 isgreater](floating-point-ordering.md) 지정 되지 않은 매크로 및 함수를 구현 합니다.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>구문

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>매개 변수

*px*<br/>
부동 소수점 인수에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 부동 소수점 형식에 대 한 CRT 함수 [fpclassify](fpclassify.md) 의 c + + 버전을 구현 합니다. *X* 인수는 평가 되 고, 해당 분류는 math. h에 정의 된 다음 상수 중 하나로 반환 됩니다.

|값|설명|
|-----------|-----------------|
| **FP_NAN** | 자동, 신호 또는 비활성화 상태 NaN |
| **FP_INFINITE** | 양수 또는 음수 무한대 |
| **FP_NORMAL** | 정규화된 0이 아닌 양수 또는 음수 값 |
| **FP_SUBNORMAL** | 긍정 또는 부정 된 subnormal (비 정규화 된) 값 |
| **FP_ZERO** | 양수 또는 음수 0 값 |

자세한 내용은 Microsoft 전용 [_fpclass _fpclassf](fpclass-fpclassf.md) 함수를 사용할 수 있습니다. 이식성에는 [fpclassify](fpclassify.md) 함수를 사용 합니다.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>구문

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>매개 변수

*px*<br/>
부동 소수점 인수에 대 한 포인터입니다.

*exp*<br/>
정수 계열 형식인 지 수입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 부동 소수점 값 *px* 및 지 수 값에 대 한 포인터를 사용 하 고 가능한 경우 지정 된 지 수 아래에서 부동 소수점 값의 소수 *부분을 제거* 합니다. 반환 되는 값은 값이 NaN 또는 무한대 인 경우 *px* 의 입력 값에 대 한 **fpclassify** 의 결과이 고, 그렇지 않은 경우에는 *px* 의 출력 값입니다.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>구문

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>매개 변수

*px*<br/>
부동 소수점 인수에 대 한 포인터입니다.

*exp*<br/>
정수 계열 형식인 지 수입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 부동 소수점 값 *px* 와 지 수 값에 대 한 *포인터를 사용* 하 고 가능 하면 <sup>*값을*</sup> *px* 로 조정 합니다. 반환 되는 값은 값이 NaN 또는 무한대 인 경우 *px* 의 입력 값에 대 한 **fpclassify** 의 결과이 고, 그렇지 않은 경우에는 *px* 의 출력 값입니다. 이식성을 위해 [ldexp, ldexp 및 ldexp](ldexp.md) 함수를 사용 하는 것이 좋습니다.

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>구문

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>매개 변수

*pexp*<br/>
정수 계열 형식인 지 수에 대 한 포인터입니다.

*px*<br/>
부동 소수점 인수에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 *px* 에서 가리키는 부동 소수점 값을 significand (가 수) 및 지 수 (가능한 경우)로 구분 합니다. Significand는 절대값을 0.5 보다 크거나 같고 1.0 보다 작은 값으로 크기를 조정 합니다. 지 수는 값 *n* 입니다. 여기서 원래 부동 소수점 값은 크기 조정 된 significand 시간 2 <sup>*n*</sup>과 같습니다. 이 정수 지 수 *n* 은 *pexp* 가 가리키는 위치에 저장 됩니다. 반환 되는 값은 값이 NaN 또는 무한대 인 경우 *px* 의 입력 값에 대 한 **fpclassify** 의 결과이 고, 그렇지 않으면 출력 값입니다. 이식성을 위해 [frexp, frexpf, frexpl](frexp.md) 함수를 사용 하는 것이 좋습니다.

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>구문

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>매개 변수

*y*<br/>
부동 소수점 함수 인수입니다.

*px*<br/>
부동 소수점 인수에 대 한 포인터입니다.

*exp*<br/>
정수 계열 형식인 지 수입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 *px* 에서 가리키는 위치에서 *y* * 2 <sup>*exp*</sup>와 동일한 부동 소수점 값을 생성 합니다. 반환 되는 값은 NaN 또는 infinity 인 경우 *y* 의 입력 값에 대 한 **fpclassify** 의 결과이 고, 그렇지 않은 경우에는 *px* 의 출력 값입니다. 이식성을 위해 [ldexp, ldexp 및 ldexp](ldexp.md) 함수를 사용 하는 것이 좋습니다.

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>구문

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>매개 변수

*ps*<br/>
배열로 표현 된 부동 소수점 값의 비트 표현에 대 한 포인터입니다 **`unsigned short`** .

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 언더플로 되었습니다 부동 소수점 값의 소수 부분을 정규화 하 고 *특성* 또는 편향 지수가 일치 하도록 조정 합니다. 이 값은 **`unsigned short`** `_double_val` `_ldouble_val` `_float_val` punning에 선언 된, 또는 형식 union을 통해의 배열로 변환 된 부동 소수점 형식의 비트 표현으로 전달 됩니다. 반환 값은 NaN 또는 infinity 인 경우 입력 부동 소수점 값에 대 한 **fpclassify** 의 결과이 고, 그렇지 않으면 출력 값입니다.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>구문

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 함수 인수입니다.

*table*<br/>
다항식의 상수 계수 테이블에 대 한 포인터입니다.

*n*<br/>
계산할 다항식의 순서입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 *테이블* 의 해당 상수 값으로 계수를 나타내는 order *n* 의 다항식에서 *x* 계산을 반환 합니다. 예를 들어 *table* \[ 0] = 3.0, *table* \[ 1] = 4.0, *table* \[ 2] = 5.0 및 *n* = 2 인 경우 다항식 5.0 x <sup>2</sup> + 4.0 x + 3.0를 나타냅니다. 이러한 다항식이 *x* 2.0에 대해 평가 되는 경우 결과는 31.0입니다. 이러한 함수는 내부적으로 사용 되지 않습니다.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>구문

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 함수 인수입니다.

*base_flag*<br/>
사용할 밑수를 제어 하는 플래그입니다. 기본 *e* 의 경우 0, base 10의 경우 0이 아닌 값입니다.

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 *base_flag* 가 0 일 때 *x*, ln (*x*) 또는 log <sub>*e*</sub>(*x*)의 자연 로그를 반환 합니다. 이 값은 0이 아닌 *base_flag* 경우 로그 밑이 10 인 *x* 또는 log <sub>10</sub>(*x*)을 반환 합니다. 이러한 함수는 내부적으로 사용 되지 않습니다. 이식성을 위해 [log, logf, logf, log10, log10f 및 log10l](log-logf-log10-log10f.md)함수를 사용 하는 것이 좋습니다.

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>구문

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 함수 인수입니다.

*제*<br/>
`sin`,, `cos` `-sin` 및 결과를 생성 하는 데 사용할 사분면 오프셋 (0, 1, 2 또는 3)입니다 `-cos` .

### <a name="remarks"></a>설명

이러한 부동 소수점 기본 형식은 4 *사분면* 에 따라 *x* 오프셋의 사인을 반환 합니다. 실제로는 *사분면* 4가 각각 0, 1, 2 또는 3 인 경우 *x* 의 사인, 코사인,-사인 및-코사인을 반환 합니다. 이러한 함수는 내부적으로 사용 되지 않습니다. 이식성을 위해 [sin, sinf, sinf](sin-sinf-sinl.md), [cos, cosf 및 cosf](cos-cosf-cosl.md) 함수를 사용 하는 것이 좋습니다.

## <a name="requirements"></a>요구 사항

헤더: \<math.h>

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexp 및 ldexp](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
