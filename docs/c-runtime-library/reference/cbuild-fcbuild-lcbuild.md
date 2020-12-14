---
description: _Cbuild, _FCbuild, _LCbuild에 대해 자세히 알아보세요.
title: _Cbuild, _FCbuild, _LCbuild
ms.date: 03/30/2018
api_name:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: bbca2571a10badcfc02da3e0d2f404590a1d7eb3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275231"
---
# <a name="_cbuild-_fcbuild-_lcbuild"></a>_Cbuild, _FCbuild, _LCbuild

실수 및 허수 부분에서 복소수를 생성 합니다.

## <a name="syntax"></a>구문

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>매개 변수

*real*<br/>
생성할 복소수의 실수 부분입니다.

*가상*<br/>
생성할 복소수의 허수 부분입니다.

## <a name="return-value"></a>반환 값

지정 된부동 소수점 형식의 값에 대 한 복소수 (실수, *허수부* )를 나타내는 _Dcomplex, _Fcomplex 또는 **_Lcomplex** 구조체입니다 \* .

## <a name="remarks"></a>설명

**_Cbuild**, **_FCbuild** 및 **_LCbuild** 함수는 복합 형식 만들기를 간소화 합니다. [Creal, crealf, creal](creal-crealf-creall.md) 및 [cimag, cimagf, cimagf](cimag-cimagf-cimagl.md) 함수를 사용 하 여 표현 된 복소수의 실수 및 허수 부분을 검색 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|C 헤더|C++ 헤더|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild**, **_LCbuild**|\<complex.h>|\<ccomplex>|

이러한 함수는 Microsoft 전용입니다. **_Dcomplex**, **_Fcomplex** 및 **_Lcomplex** 형식은 각각 구현 되지 않은 C99 네이티브 형식, 및에 해당 **`double _Complex`** **`float _Complex`** **`long double _Complex`** 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
