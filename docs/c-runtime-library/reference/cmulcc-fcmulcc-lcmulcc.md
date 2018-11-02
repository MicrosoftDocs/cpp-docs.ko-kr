---
title: _Cmulcc, _FCmulcc, _LCmulcc
ms.date: 03/30/2018
apiname:
- _Cmulcc
- _FCmulcc
- _LCmulcc
apilocation:
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
apitype: DLLExport
f1_keywords:
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
ms.openlocfilehash: f81ccb641a80ab264e8bc54ba1987e2c2c8469f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656770"
---
# <a name="cmulcc-fcmulcc-lcmulcc"></a>_Cmulcc, _FCmulcc, _LCmulcc

두 복소수를 곱합니다.

## <a name="syntax"></a>구문

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>매개 변수

*x*<br/>
곱할 복잡 한 피연산자 중 하나입니다.

*y*<br/>
다른 복잡 한 피연산자 곱할입니다.

## <a name="return-value"></a>반환 값

A **_Dcomplex**를 **_Fcomplex**, 또는 **_Lcomplex** 복소수의 복잡 한 제품을 나타내는 구조 *x* 및 *y*합니다.

## <a name="remarks"></a>설명

복합 형식에서의 Microsoft 구현에 기본 제공 산술 연산자를 적용할 수 없습니다 때문에 합니다 **_Cmulcc**를 **_FCmulcc**, 및 **_LCmulcc** 함수 복합 형식의 곱하기를 간소화 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|C 헤더|C++ 헤더|
|-------------|--------------|------------------|
|**_Cmulcc**하십시오 **_FCmulcc**, **_LCmulcc**|\<complex.h>|\<complex.h>|

이러한 함수는 Microsoft 전용입니다. 형식을 **_Dcomplex**를 **_Fcomplex**, 및 **_Lcomplex** 구현 되지 않은 C99 네이티브 형식에 해당 하는 Microsoft 전용은 **double _Complex** 하십시오 **float _Complex**, 및 **long double _Complex**각각. 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
