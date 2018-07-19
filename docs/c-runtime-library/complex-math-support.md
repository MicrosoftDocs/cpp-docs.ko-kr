---
title: C 복합 수학식 지원 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.complex
dev_langs:
- C++
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 661e1367ea64713cf7a143f276cd195d54fecf85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392080"
---
# <a name="c-complex-math-support"></a>C 복합 수학식 지원

Microsoft CRT(C 런타임 라이브러리)는 ISO C99에 따라 필요한 모든 함수를 포함하여 복합 수학식 라이브러리 함수를 제공합니다. 컴파일러는 **complex** 또는 **_Complex** 키워드를 직접 지원하지 않습니다. 따라서 Microsoft 구현은 구조 형식을 사용하여 복소수를 나타냅니다.

이러한 함수는 수정을 통해 성능을 균형있게 분배하도록 구현됩니다. 올바르게 반올림된 결과를 생성하는 것은 막대한 비용이 들 수 있으므로 이러한 함수는 올바르게 반올림된 결과에 대한 근사치를 효율적으로 생성하도록 설계됩니다. 부정확성이 더 큰 경우도 있을 수 있지만 대부분은 생성된 결과가 올바르게 반올림된 결과의 +/-1 ulp 내에 있습니다.

복합 수학식 루틴은 해당 구현에 대한 부동 소수점 수학식 라이브러리 함수를 사용합니다. 이러한 함수는 다양한 CPU 아키텍처를 다양하게 구현합니다. 예를 들어 32비트 x86 CRT에는 64비트 x64 CRT와 다른 구현이 있을 수 있습니다. 또한 일부 함수에는 지정된 CPU 아키텍처에 대한 여러 구현이 있을 수 있습니다. 가장 효율적인 구현은 CPU에서 지원되는 명령 집합에 따라 런타임에 동적으로 선택됩니다. 예를 들어 32비트 x86 CRT에서 일부 함수에는 x87 구현 및 an SSE2 구현이 둘 다 있습니다. SSE2를 지원하는 CPU에서 실행될 경우 더 빠른 SSE2 구현이 사용됩니다. SSE2를 지원하지 않는 CPU에서 실행될 경우 더 느린 x87 구현이 사용됩니다. 수학 라이브러리 함수의 구현에 따라 다른 CPU 명령 및 다른 알고리즘을 사용하여 결과를 생성할 수 있으므로 CPU에 따라 함수에서 다른 결과가 생성될 수 있습니다. 대부분은 결과가 올바르게 반올림된 결과의 +/-1 ulp 내에 있지만 실제 결과는 CPU에 따라 달라질 수 있습니다.

## <a name="types-used-in-complex-math"></a>복합 수학식에 사용되는 형식

complex.h 헤더의 Microsoft 구현은 C99 표준 기본 복합 형식에 대한 동일한 기능으로 이러한 형식을 정의합니다.

|표준 형식|Microsoft 형식|
|-|-|
|**float complex** 또는 **float _Complex**|**_FComplex**|
|**double complex** 또는 **double _Complex**|**_DComplex**|
|**long double complex** 또는 **long double _Complex**|**_LComplex**|

math.h 헤더는 [_cabs](../c-runtime-library/reference/cabs.md) 함수에 사용되는 별도 형식 **struct _complex**를 정의합니다. **struct _complex** 형식은 동등한 복합 수학 함수 [cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)에서 사용되지 않습니다.

## <a name="complex-constants-and-macros"></a>복합 상수 및 매크로

**I**는 `{ 0.0f, 1.0f }`에 의해 초기화된 **부동** 복합 형식 **_FComplex**로 정의됩니다.

## <a name="trigonometric-functions"></a>삼각 함수

|함수|설명|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|복소수의 복합 아크코사인 계산|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|복소수의 복합 아크사인 계산|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|복소수의 복합 아크탄젠트 계산|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|복소수의 복합 코사인 계산|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|복소수의 복합 사인 계산|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|복소수의 복합 탄젠트 계산|

## <a name="hyperbolic-functions"></a>쌍곡선 함수

|함수|설명|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|복소수의 복합 쌍곡선 아크코사인 계산|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|복소수의 복합 쌍곡선 아크사인 계산|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|복소수의 복합 쌍곡선 아크탄젠트 계산|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|복소수의 복합 쌍곡선 코사인 계산|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|복소수의 복합 쌍곡선 사인 계산|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|복소수의 복합 쌍곡선 탄젠트 계산|

## <a name="exponential-and-logarithmic-functions"></a>지수 및 로그 함수

|함수|설명|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|복소수의 밑이 *e*인 복합 지수 계산|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|복소수의 복합 자연 로그 계산(밑이 *e*)|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|복소수의 밑이 10인 복합 로그 계산|

## <a name="power-and-absolute-value-functions"></a>거듭제곱 및 절대값 함수

|함수|설명|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|복소수의 복합 절대값(기준, 계수 또는 자릿수라고도 함) 계산|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|복합 거듭제곱 함수 x<sup>y</sup> 계산|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|복소수의 복합 제곱근 계산|

## <a name="manipulation-functions"></a>조작 함수

|함수|설명|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|실수 및 허수부에서 복소수 생성|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|복소수의 인수(위상각이라고도 함) 계산|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|복소수의 허수부 계산|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|복소수의 켤레 복소수 계산|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|리만 구(Reimann sphere)에서 복소수의 사영 계산|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|복소수의 실수부 계산|
|[norm, normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|복소수의 제곱 자릿수 계산|

## <a name="operation-functions"></a>연산 함수

복소수가 Microsoft 컴파일러에서 네이티브 형식이 아니기 때문에 표준 산술 연산자는 복합 형식에 정의되지 않습니다. 편의상 이러한 복합 수학식 라이브러리 함수를 제공하여 사용자 코드에서 복소수의 제한된 조작을 가능하게 합니다.

|함수|설명|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|두 복소수 곱셈|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|복합 및 부동 소수점 숫자 곱셈|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
