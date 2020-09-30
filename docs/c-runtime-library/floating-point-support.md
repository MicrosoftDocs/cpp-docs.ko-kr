---
title: 수학식 및 부동 소수점 지원
description: Microsoft CRT (유니버설 C 런타임 라이브러리)의 부동 소수점 지원에 대해 설명 합니다.
ms.date: 9/14/2020
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: d1caaf5c9c0cfc7a3b6650bcb72a66b4c0028e28
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502115"
---
# <a name="math-and-floating-point-support"></a>수학식 및 부동 소수점 지원

UCRT(유버니설 C 런타임) 라이브러리는 ISO C99에 필요한 모든 함수를 포함하여 많은 정수 및 부동 소수점 수학 라이브러리 함수를 제공합니다. 부동 소수점 함수는 성능과 정확성을 균형 있게 유지하도록 구현됩니다. 올바르게 반올림된 결과를 생성하는 것은 막대한 비용이 들 수 있으므로 이러한 함수는 올바르게 반올림된 결과에 대한 근사치를 효율적으로 생성하도록 설계됩니다. 부정확성이 더 큰 경우도 있을 수 있지만 대부분은 생성된 결과가 올바르게 반올림된 결과의 +/-1 ulp 내에 있습니다.

ISO C 표준 11 (C11) 이상의 경우 \<tgmath.h> 및를 포함 하 여 헤더는 \<math.h> \<complex.h> 매개 변수의 형식을 기반으로 해당 수학 함수를 호출 하는 매크로를 제공 합니다. 자세한 내용은 [형식-제네릭](tgmath.md) 계산을 참조 하세요.

대부분의 부동 소수점 수학 라이브러리 함수에는 다양한 CPU 아키텍처에 대한 다양한 구현이 있습니다. 예를 들어 32비트 x86 CRT에는 64비트 x64 CRT와 다른 구현이 있을 수 있습니다. 또한 일부 함수에는 지정된 CPU 아키텍처에 대한 여러 구현이 있을 수 있습니다. 가장 효율적인 구현은 CPU에서 지원되는 명령 집합에 따라 런타임에 동적으로 선택됩니다. 예를 들어 32비트 x86 CRT에서 일부 함수에는 x87 구현 및 an SSE2 구현이 둘 다 있습니다. SSE2를 지원하는 CPU에서 실행될 경우 더 빠른 SSE2 구현이 사용됩니다. SSE2를 지원하지 않는 CPU에서 실행될 경우 더 느린 x87 구현이 사용됩니다. 수학 라이브러리 함수의 구현에 따라 다른 CPU 명령 및 다른 알고리즘을 사용하여 결과를 생성할 수 있으므로 CPU에 따라 함수에서 다른 결과가 생성될 수 있습니다. 대부분은 결과가 올바르게 반올림된 결과의 +/-1 ulp 내에 있지만 실제 결과는 CPU에 따라 달라질 수 있습니다.

이전 16 비트 버전의 Microsoft C/c + + 및 Microsoft Visual C++는 **`long double`** 형식을 80 비트 정밀도 부동 소수점 데이터 형식으로 지원 했습니다. Visual C++의 이후 버전에서 **`long double`** 데이터 형식은 형식과 동일한 64 비트 정밀도 부동 소수점 데이터 형식입니다 **`double`** . 컴파일러는 **`long double`** 및를 **`double`** 고유한 형식으로 처리 하지만 **`long double`** 함수는 해당 함수와 동일 합니다 **`double`** . CRT는 **`long double`** ISO C99 소스 코드 호환성을 위한 수학 함수 버전을 제공 하지만 이진 표현은 다른 컴파일러와 다를 수 있습니다.

## <a name="supported-math-and-floating-point-routines"></a>지원되는 수학식 및 부동 소수점 루틴

|루틴에서 반환된 값|기능|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|정수 형식의 절대값을 계산합니다.
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|아크코사인을 계산합니다.
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|쌍곡선 아크코사인을 계산합니다.
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|아크사인을 계산합니다.
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|쌍곡선 아크사인을 계산합니다.
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|아크탄젠트를 계산합니다.
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|쌍곡선 아크탄젠트를 계산합니다.
[_atodbl, _atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|로캘별 문자열을으로 변환 합니다. **`double`**
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|문자열을로 변환 합니다. **`double`**
[_atoflt, _atoflt_l, _atoldbl, _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|로캘별 문자열을 또는로 변환 합니다. **`float`****`long double`**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|세제곱근을 계산합니다.
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|최곳값을 계산합니다.
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|덧셈 역원을 계산합니다.
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|부동 소수점 상태 레지스터를 가져오고 지웁니다.
[_control87, \__control87_2, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|부동 소수점 제어 단어를 가져오고 설정합니다.
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|**_controlfp**의 안전한 버전입니다.
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|한 인수의 크기 및 다른 인수의 부호가 있는 값을 반환합니다.
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|사인을 계산합니다.
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|쌍곡선 사인을 계산합니다.
[div, ldiv, lldiv](../c-runtime-library/reference/div.md)|두 정수 값의 몫과 나머지를 계산합니다.
[_ecvt](../c-runtime-library/reference/ecvt.md), [ecvt](../c-runtime-library/reference/posix-ecvt.md)|을 문자열로 변환 합니다. **`double`**
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|**_ecvt**의 안전한 버전입니다.
[erf, erff, erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|오차 함수를 계산합니다.
[erfc, erfcf, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|보상 오차 함수를 계산합니다.
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|지수 *e*<sup>x</sup>를 계산합니다.
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|지수 2<sup>x</sup>를 계산합니다.
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|*e*<sup>x</sup>-1를 계산합니다.
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|부동 소수점 형식의 절대값을 계산합니다.
[_fcvt](../c-runtime-library/reference/fcvt.md), [fcvt](../c-runtime-library/reference/posix-fcvt.md)|부동 소수점 숫자를 문자열로 변환합니다.
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|**_fcvt**의 안전한 버전입니다.
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|두 값의 양수 차이를 결정합니다.
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|지정된 부동 소수점 예외를 지웁니다.
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|현재 부동 소수점 환경을 저장합니다.
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|지정된 부동 소수점 예외 상태를 가져옵니다.
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|부동 소수점 반올림 모드를 가져옵니다.
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|중단 없는 부동 소수점 예외 모드를 설정합니다.
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|지정된 부동 소수점 예외를 발생시킵니다.
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|현재 부동 소수점 환경을 설정합니다.
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|지정된 부동 소수점 상태 플래그를 설정합니다.
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|지정된 부동 소수점 반올림 모드를 설정합니다.
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|설정된 부동 소수점 예외 상태 플래그를 결정합니다.
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|부동 소수점 환경을 복원한 다음, 이전 예외를 발생시킵니다.
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|최젓값을 계산합니다.
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|단일 곱셈 누산기(Fused Multiply-Add)를 계산합니다.
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|인수의 최댓값을 계산합니다.
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|인수의 최소값을 계산 합니다.
[fmod, fmodf, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|부동 소수점 나머지를 계산합니다.
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|부동 소수점 값의 분류를 반환합니다.
[fpclassify](../c-runtime-library/reference/fpclassify.md)|부동 소수점 값의 분류를 반환합니다.
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|부동 소수점 예외에 대한 처리기를 설정합니다.
[_fpreset](../c-runtime-library/reference/fpreset.md)|부동 소수점 환경을 다시 설정합니다.
[frexp, frexpf, frexpl](../c-runtime-library/reference/frexp.md)|부동 소수점 숫자의 가수와 지수를 가져옵니다.
[_gcvt](../c-runtime-library/reference/gcvt.md), [gcvt](../c-runtime-library/reference/posix-gcvt.md)|부동 소수점 숫자를 문자열로 변환합니다.
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|**_gcvt**의 안전한 버전입니다.
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|x64에서 FMA3 명령을 사용하기 위한 플래그를 가져오거나 설정합니다.
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|빗변을 계산합니다.
[ilogb, ilogbf, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|밑이 2인 정수 지수를 계산합니다.
[imaxabs](../c-runtime-library/reference/imaxabs.md)|정수 형식의 절대값을 계산합니다.
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|두 정수 값의 몫과 나머지를 계산합니다.
[isfinite, _finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|유한 값인지 여부를 결정합니다.
[isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered](../c-runtime-library/reference/floating-point-ordering.md)|두 부동 소수점 값의 순서 비교
[isinf](../c-runtime-library/reference/isinf.md)|부동 소수점 값이 무한인지 확인
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|NaN에 대한 부동 소수점 값을 테스트합니다.
[isnormal](../c-runtime-library/reference/isnormal.md)|부동 소수점 값이 유한하고 비정상적인지 여부를 테스트합니다.
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Bessel 함수를 계산합니다.
[ldexp, ldexpf, ldexpl](../c-runtime-library/reference/ldexp.md)|x*2<sup>n</sup>을 계산합니다.
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|감마 함수의 절대값에 대한 자연 로그를 계산합니다.
[llrint, llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|부동 소수점 값을 가장 가까운 값으로 반올림 합니다. **`long long`**
[llround, llroundf, llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|부동 소수점 값을 가장 가까운 값으로 반올림 합니다. **`long long`**
[log, logf, logl, log10, log10f, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|자연 로그 또는 상용 로그를 계산합니다.
[log1p, log1pf, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|1 + x의 자연 로그를 계산합니다.
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|밑이 2인 로그를 계산합니다.
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|부동 소수점 값의 지수를 반환합니다.
[lrint, lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|부동 소수점 값을 가장 가까운 값으로 반올림 합니다. **`long`**
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|정수 값을 왼쪽 또는 오른쪽으로 회전합니다.
[lround, lroundf, lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|부동 소수점 값을 가장 가까운 값으로 반올림 합니다. **`long`**
[_matherr](../c-runtime-library/reference/matherr.md)|기본 수학 오류 처리기입니다.
[__max](../c-runtime-library/reference/max.md)|두 값 중 큰 값을 반환하는 매크로입니다.
[__min](../c-runtime-library/reference/min.md)|두 값 중 작은 값을 반환하는 매크로입니다.
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|부동 소수점 값을 소수 부분과 정수 부분으로 분할합니다.
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|QNaN(Quiet NaN) 값을 반환합니다.
[nearbyint, nearbyintf, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|반올림된 값을 반환합니다.
[nextafter, nextafterf, nextafterl, _nextafter, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|표현 가능한 다음 부동 소수점 값을 반환합니다.
[nexttoward, nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|표현 가능한 다음 부동 소수점 값을 반환합니다.
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|*x*<sup>*y*</sup>의 값을 반환합니다.
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|두 부동 소수점 값의 몫과 나머지를 계산합니다.
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|두 정수 값의 나머지를 계산합니다.
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|부동 소수점 값을 반올림합니다.
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|비트를 정수 형식으로 회전합니다.
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|부동 소수점 값을 반올림합니다.
[_scalb, _scalbf](../c-runtime-library/reference/scalb.md)|인수의 크기를 2의 거듭제곱으로 조정합니다.
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|부동 소수점 숫자를 **FLT_RADIX**의 정수 거듭제곱으로 곱합니다.
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|부동 소수점 제어 단어를 설정합니다.
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|SSE2 명령을 사용하거나 사용하지 않도록 설정합니다.
[signbit](../c-runtime-library/reference/signbit.md)|부동 소수점 값의 부호 비트를 테스트합니다.
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|사인을 계산합니다.
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|쌍곡선 사인을 계산합니다.
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|제곱근을 계산합니다.
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|부동 소수점 상태 단어를 가져옵니다.
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|문자열을로 변환 합니다. **`float`**
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|문자열을로 변환 합니다. **`long double`**
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|탄젠트를 계산합니다.
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|쌍곡선 탄젠트를 계산합니다.
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|감마 함수를 계산합니다.
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|소수 부분을 자릅니다.
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|와이드 문자열을으로 변환 합니다. **`double`**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Bessel 함수를 계산합니다.

## <a name="see-also"></a>참고 항목

[범주별 유니버설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)\
[부동 소수점 기본 형식](../c-runtime-library/reference/floating-point-primitives.md)
