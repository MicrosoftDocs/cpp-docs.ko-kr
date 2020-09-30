---
title: 형식-제네릭 수학
description: 인수 형식에 따라 올바른 수학 함수를 호출 하는 C 코드를 더 쉽게 작성할 수 있도록 하는 <tgmath>의 매크로에 대해 설명 합니다.
ms.topic: conceptual
ms.date: 9/3/2020
helpviewer_keywords:
- CRT tgmath.h
ms.openlocfilehash: 98c786d91963973ad9384cea2fe6563d1e3174ac
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590227"
---
# <a name="type-generic-math"></a>형식-제네릭 수학

ISO C 표준 11 (C11) 이상의 경우 \<tgmath.h> 및를 포함 하 여 헤더는 \<math.h> \<complex.h> 매개 변수의 형식을 기반으로 해당 수학 함수를 호출 하는 매크로를 제공 합니다.

C 런타임 라이브러리 수학 함수는 실제 및 복합 변형에서 제공 됩니다. 각 변형은 인수의 형식에 따라, 및의 세 가지 형식으로 제공 `float` 됩니다. `double` `long double` C는 c + +와 같은 오버 로드를 지원 하지 않으므로 각 변형은 다른 이름을 갖습니다. 예를 들어 실수 부동 소수점 값의 절대값을 가져오기 위해, 또는 `fabsf` `fabs` 값을 `fabsl` 각각 전달 하는지 여부에 따라, 또는를 호출 `float` `double` `long double` 합니다. 복합 절대값을 가져오기 위해, `cabsf` `cabs` `cabsl` 및 복합 값을 각각 전달 하는지 여부에 따라, 또는 중 하나를 호출 `float` `double` `long double` 합니다. 인수가 위에 언급 된 형식과 일치 하지 않으면 인수가 두 배가 되는 것 처럼 함수가 선택 됩니다.

\<tgmath.h> 호출할 오른쪽 수학 함수를 간편 하 게 선택할 수 있는 매크로를 포함 합니다. 매크로는 전달 된 형식을 검사 한 다음 right 함수를 호출 합니다. 예를 들어 매크로는에 바인딩되고,는에 `sqrt` `sqrt(9.9f)` `sqrtf()` 바인딩됩니다 `sqrt(9.9)` `sqrt()` . 제네릭 매개 변수에 대 한 매크로 인수가 하나 이상 복잡 한 경우 매크로는 복잡 한 함수에 바인딩됩니다. 그렇지 않으면 실제 함수를 호출 합니다.

의 형식-일반 매크로를 \<tgmath.h> 사용 하면 인수의 형식에 따라 캐스트를 관리 하거나 다른 함수 이름을 선택할 필요가 없기 때문에 더 많은 이식 가능한 코드를 작성할 수 있습니다.

이러한 매크로는 헤더를 사용 하 여 작성 된 프로그램이 중단 되지 않도록 자체 헤더에 있습니다 `<math.h>` . `double x = sin(42);`는를 포함 하는 경우 항상에 있는 것 처럼 동작 \<math.h> 합니다. 이러한 경우에도 대부분의 기존 C 프로그램은 \<tgmath.h> 헤더가 또는 대신 포함 될 때 영향을 받지 \<math.h> 않습니다 \<complex.h> .

다음 표에서는에서 사용할 수 있는 매크로와 해당 매크로 \<tgmath.h> 를 확장 하는 방법을 보여 줍니다. `modf` 는 복잡 한 형식 확인 없이 안전 하 게 만드는 방법을 명확 하 게 알 수 없기 때문에이 테이블에 포함 되지 않습니다.

|매크로  |Real</br>`float`  | Real</br>`double` | Real</br>`long double` | Complex</br>`float` | Complex</br>`double` | Complex</br>`long double` |
|---------|---------|---------|---------|---------|---------|---------|
`acos` | [acosf](reference/mbsnbicmp-mbsnbicmp-l.md) | [acos](reference/mbsnbicmp-mbsnbicmp-l.md) | [acosl](reference/mbsnbicmp-mbsnbicmp-l.md) | [cacosf](reference/cacos-cacosf-cacosl.md) | [cacos](reference/cacos-cacosf-cacosl.md) | [cacosl](reference/cacos-cacosf-cacosl.md) |
`acosh` | [acoshf](reference/acosh-acoshf-acoshl.md) | [acosh](reference/acosh-acoshf-acoshl.md) | [acoshl](reference/acosh-acoshf-acoshl.md) | [cacoshf](reference/cacosh-cacoshf-cacoshl.md) | [cacosh](reference/cacosh-cacoshf-cacoshl.md) | [cacoshl](reference/cacosh-cacoshf-cacoshl.md) |
`asin` | [asinf](reference/asin-asinf-asinl.md) | [asin](reference/asin-asinf-asinl.md) | [asinl](reference/asin-asinf-asinl.md) | [casinf](reference/casin-casinf-casinl.md) | [casin](reference/casin-casinf-casinl.md) | [casinl](reference/casin-casinf-casinl.md) |
`asinh` | [asinhf](reference/asin-asinf-asinl.md) | [asinh](reference/asin-asinf-asinl.md) | [asinhl](reference/asin-asinf-asinl.md) | [casinhf](reference/casinh-casinhf-casinhl.md) | [casinh](reference/casinh-casinhf-casinhl.md) | [casinhl](reference/casinh-casinhf-casinhl.md) |
`atan` | [atanf](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atan](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atanl](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [catanf](reference/catan-catanf-catanl.md) | [catan](reference/catan-catanf-catanl.md) | [catanl](reference/catan-catanf-catanl.md) |
`atanh` | [atanhf](reference/atanh-atanhf-atanhl.md) | [atanh](reference/atanh-atanhf-atanhl.md) | [atanhl](reference/atanh-atanhf-atanhl.md) | [catanhf](reference/catanh-catanhf-catanhl.md) | [catanh](reference/catanh-catanhf-catanhl.md) | [catanhl](reference/catanh-catanhf-catanhl.md) |
`cos` | [cosf](reference/cos-cosf-cosl.md) | [cos](reference/cos-cosf-cosl.md) | [cosl](reference/cos-cosf-cosl.md) | [ccosf](reference/ccos-ccosf-ccosl.md) | [ccos](reference/ccos-ccosf-ccosl.md) | [ccosl](reference/ccos-ccosf-ccosl.md) |
`cosh` | [coshf](reference/cosh-coshf-coshl.md) | [cosh](reference/cosh-coshf-coshl.md) | [coshl](reference/cosh-coshf-coshl.md) | [ccoshf](reference/ccosh-ccoshf-ccoshl.md) | [ccosh](reference/ccosh-ccoshf-ccoshl.md) | [ccoshl](reference/ccosh-ccoshf-ccoshl.md) |
`exp` | [expf](reference/exp-expf.md) | [exp](reference/exp-expf.md) | [expl](reference/exp-expf.md) | [cexpf](reference/cexp-cexpf-cexpl.md) | [cexp](reference/cexp-cexpf-cexpl.md) | [cexpl](reference/cexp-cexpf-cexpl.md) |
`fabs` | [fabsf](reference/fabs-fabsf-fabsl.md) | [fabs](reference/fabs-fabsf-fabsl.md) | [fabsl](reference/fabs-fabsf-fabsl.md) | [cabsf](reference/cabs-cabsf-cabsl.md) | [cab](reference/cabs-cabsf-cabsl.md) | [cabsl](reference/cabs-cabsf-cabsl.md) |
`log` | [logf](reference/log-logf-log10-log10f.md) | [로깅할](reference/log-logf-log10-log10f.md) | [logl](reference/log-logf-log10-log10f.md) | [clogf](reference/clog-clogf-clogl.md) | [clog](reference/clog-clogf-clogl.md) | [clogl](reference/clog-clogf-clogl.md) |
`pow` | [powf](reference/pow-powf-powl.md) | [pow](reference/pow-powf-powl.md) | [powl](reference/pow-powf-powl.md) | [cpowf](reference/cpow-cpowf-cpowl.md) | [cpow](reference/cpow-cpowf-cpowl.md) | [cpowl](reference/cpow-cpowf-cpowl.md) |
`sin` | [sinf](reference/sin-sinf-sinl.md) | [사인](reference/sin-sinf-sinl.md) | [sinl](reference/sin-sinf-sinl.md) | [csinf](reference/csin-csinf-csinl.md) | [csin](reference/csin-csinf-csinl.md) | [csinl](reference/csin-csinf-csinl.md) |
`sinh` | [sinhf](reference/sinh-sinhf-sinhl.md) | [sinh](reference/sinh-sinhf-sinhl.md) | [sinhl](reference/sinh-sinhf-sinhl.md) | [csinhf](reference/csinh-csinhf-csinhl.md) | [csinh](reference/csinh-csinhf-csinhl.md) | [csinhl](reference/csinh-csinhf-csinhl.md) |
`sqrt` | [sqrtf](reference/sqrt-sqrtf-sqrtl.md) | [sqrt](reference/sqrt-sqrtf-sqrtl.md) | [sqrtl](reference/sqrt-sqrtf-sqrtl.md) | [csqrtf](reference/csqrt-csqrtf-csqrtl.md) | [csqrt](reference/csqrt-csqrtf-csqrtl.md) | [csqrtl](reference/csqrt-csqrtf-csqrtl.md) |
`tan` | [tanf](reference/tan-tanf-tanl.md) | [tan](reference/tan-tanf-tanl.md) | [tanl](reference/tan-tanf-tanl.md) | [ctanf](reference/ctan-ctanf-ctanl.md) | [ctan](reference/ctan-ctanf-ctanl.md) | [ctanl](reference/ctan-ctanf-ctanl.md) |
`tanh` | [tanhf](reference/tanh-tanhf-tanhl.md) | [tanh](reference/tanh-tanhf-tanhl.md) | [tanhl](reference/tanh-tanhf-tanhl.md) | [ctanhf](reference/ctanh-ctanhf-ctanhl.md) | [ctanh](reference/ctanh-ctanhf-ctanhl.md) | [ctanhl](reference/ctanh-ctanhf-ctanhl.md) |
`atan2` | [atan2f](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atan2](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atan2l](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | - | - | - |
`cbrt` | [cbrtf](reference/cbrt-cbrtf-cbrtl.md) | [cbrt](reference/cbrt-cbrtf-cbrtl.md) | [cbrtl](reference/cbrt-cbrtf-cbrtl.md) | - | - | - |
`ceil` | [ceilf](reference/ceil-ceilf-ceill.md) | [ceil](reference/ceil-ceilf-ceill.md) | [ceill](reference/ceil-ceilf-ceill.md) | - | - | - |
`copysign` | [copysignf](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [copysign](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [copysignl](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | - | - | - |
`erf` | [erff](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erf](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erfl](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`erfc` | [erfcf](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erfc](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erfcl](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`exp2` | [exp2f](reference/exp2-exp2f-exp2l.md) | [exp2](reference/exp2-exp2f-exp2l.md) | [exp2l](reference/exp2-exp2f-exp2l.md) | - | - | - |
`expm1` | [expm1f](reference/expm1-expm1f-expm1l.md) | [expm1](reference/expm1-expm1f-expm1l.md) | [expm1l](reference/expm1-expm1f-expm1l.md) | - | - | - |
`fdim` | [fdimf](reference/fdim-fdimf-fdiml.md) | [fdim](reference/fdim-fdimf-fdiml.md) | [fdiml](reference/fdim-fdimf-fdiml.md) | - | - | - |
`floor` | [floorf](reference/floor-floorf-floorl.md) | [평면](reference/floor-floorf-floorl.md) | [floorl](reference/floor-floorf-floorl.md) | - | - | - |
`fma` | [fmaf](reference/fma-fmaf-fmal.md) | [fma](reference/fma-fmaf-fmal.md) | [fmal](reference/fma-fmaf-fmal.md) | - | - | - |
`fmax` | [fmaxf](reference/fmax-fmaxf-fmaxl.md) | [fmax](reference/fmax-fmaxf-fmaxl.md) | [fmaxl](reference/fmax-fmaxf-fmaxl.md) | - | - | - |
`fmin` | [fminf](reference/fmin-fminf-fminl.md) | [fmin](reference/fmin-fminf-fminl.md) | [fminl](reference/fmin-fminf-fminl.md) | - | - | - |
`fmod` | [fmodf](reference/fmod-fmodf.md) | [fmod](reference/fmod-fmodf.md) | [fmodl](reference/fmod-fmodf.md) | - | - | - |
`frexp` | [frexpf](reference/frexp.md) | [frexp](reference/frexp.md) | [frexpl](reference/frexp.md) | - | - | - |
`hypot` | [hypotf](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [hypot](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [hypotl](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | - | - | - |
`ilogb` | [ilogbf](reference/ilogb-ilogbf-ilogbl2.md) | [ilogb](reference/ilogb-ilogbf-ilogbl2.md) | [ilogbl](reference/ilogb-ilogbf-ilogbl2.md) | - | - | - |
`ldexp` | [ldexpf](reference/ldexp.md) | [ldexp](reference/ldexp.md) | [ldexpl](reference/ldexp.md) | - | - | - |
`lgamma` | [lgammaf](reference/lgamma-lgammaf-lgammal.md) | [lgamma](reference/lgamma-lgammaf-lgammal.md) | [lgammal](reference/lgamma-lgammaf-lgammal.md) | - | - | - |
`llrint` | [llrintf](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [llrint](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [llrintl](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`llround` | [llroundf](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [llround](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [llroundl](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`log10` | [log10f](reference/log-logf-log10-log10f.md) | [log10](reference/log-logf-log10-log10f.md) | [log10l](reference/log-logf-log10-log10f.md) | - | - | - |
`log1p` | [log1pf](reference/log1p-log1pf-log1pl2.md) | [log1p](reference/log1p-log1pf-log1pl2.md) | [log1pl](reference/log1p-log1pf-log1pl2.md) | - | - | - |
`log2` | [log2f](reference/log2-log2f-log2l.md) | [log2](reference/log2-log2f-log2l.md) | [log2l](reference/log2-log2f-log2l.md) | - | - | - |
`logb` | [logbf](reference/logb-logbf-logbl-logb-logbf.md) | [logb](reference/logb-logbf-logbl-logb-logbf.md) | [logbl](reference/logb-logbf-logbl-logb-logbf.md) | - | - | - |
`lrint` | [lrintf](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [lrint](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [lrintl](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`lround` | [lroundf](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [lround](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [lroundl](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`nearbyint` | [nearbyintf](reference/nearbyint-nearbyintf-nearbyintl1.md) | [nearbyint](reference/nearbyint-nearbyintf-nearbyintl1.md) | [nearbyintl](reference/nearbyint-nearbyintf-nearbyintl1.md) | - | - | - |
`nextafter` | [nextafterf](reference/nextafter-functions.md) | [nextafter](reference/nextafter-functions.md) | [nextafterl](reference/nextafter-functions.md) | - | - | - |
`nexttoward` | [nexttowardf](reference/nextafter-functions.md) | [nexttoward](reference/nextafter-functions.md) | [nexttowardl](reference/nextafter-functions.md) | - | - | - |
`remainder` | [remainderf](reference/remainder-remainderf-remainderl.md) | [남은](reference/remainder-remainderf-remainderl.md) | [remainderl](reference/remainder-remainderf-remainderl.md) | - | - | - |
`remquo` | [remquof](reference/remquo-remquof-remquol.md) | [remquo](reference/remquo-remquof-remquol.md) | [remquol](reference/remquo-remquof-remquol.md) | - | - | - |
`rint` | [rintf](reference/rint-rintf-rintl.md) | [rint](reference/rint-rintf-rintl.md) | [rintl](reference/rint-rintf-rintl.md) | - | - | - |
`round` | [roundf](reference/round-roundf-roundl.md) | [둥근](reference/round-roundf-roundl.md) | [roundl](reference/round-roundf-roundl.md) | - | - | - |
`scalbln` | [scalblnf](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalbln](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalblnl](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`scalbn` | [scalbnf](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalbn](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalbnl](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`tgamma` | [tgammaf](reference/tgamma-tgammaf-tgammal.md) | [tgamma](reference/tgamma-tgammaf-tgammal.md) | [tgammal](reference/tgamma-tgammaf-tgammal.md) | - | - | - |
`trunc` | [truncf](reference/trunc-truncf-truncl.md) | [trunc](reference/trunc-truncf-truncl.md) | [truncl](reference/trunc-truncf-truncl.md) | - | - | - |
`carg` | - | - | - | [cargf](reference/carg-cargf-cargl.md) | [carg](reference/carg-cargf-cargl.md) | [cargl](reference/carg-cargf-cargl.md) |
`conj` | - | - | - | [conjf](reference/conj-conjf-conjl.md) | [conj](reference/conj-conjf-conjl.md) | [conjl](reference/conj-conjf-conjl.md) |
`creal` | - | - | - | [crealf](reference/creal-crealf-creall.md) | [creal](reference/creal-crealf-creall.md) | [creall](reference/creal-crealf-creall.md) |
`cimag` | - | - | - | [cimagf](reference/cimag-cimagf-cimagl.md) | [cimag](reference/cimag-cimagf-cimagl.md) | [cimagl](reference/cimag-cimagf-cimagl.md) |
`cproj` | - | - | - | [cprojf](reference/cproj-cprojf-cprojl.md) | [cproj](reference/cproj-cprojf-cprojl.md) | [cprojl](reference/cproj-cprojf-cprojl.md) |

## <a name="requirements"></a>요구 사항

[std: c + + 11](../build/reference/std-specify-language-standard-version.md) 이상이 필요 합니다.

10.0.20201.0 이상 버전을 Windows SDK 합니다.

## <a name="see-also"></a>참고 항목

[C 런타임 라이브러리 참조](c-run-time-library-reference.md)
