---
description: '자세한 정보: cab, cabsf, cabsf'
title: cabs, cabsf, cabsl
ms.date: 11/04/2016
api_name:
- cabs
- cabsf
- cabsl
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
- cabs
- cabsf
- cabsl
- complex/cabs
- complex/cabsf
- complex/cabsl
helpviewer_keywords:
- cabs function
- cabsf function
- cabsl function
ms.assetid: 6b8eb453-cc8f-4972-bebf-351cbdfdfc15
ms.openlocfilehash: 2ae24a0b7c158c2a13a595e946ee79b0760d75ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171662"
---
# <a name="cabs-cabsf-cabsl"></a>cabs, cabsf, cabsl

복소수의 절대값을 검색합니다.

## <a name="syntax"></a>구문

```C
double cabs(
   _Dcomplex z
);
float cabs(
   _Fcomplex z
);  // C++ only
long double cabs(
   _Lcomplex z
);  // C++ only
float cabsf(
   _Fcomplex z
);
long double cabsl(
   _Lcomplex z
);
```

### <a name="parameters"></a>매개 변수

*z*<br/>
복소수입니다.

## <a name="return-value"></a>반환 값

*Z* 의 절대값입니다.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **_Fcomplex** 또는 **_Lcomplex** 값을 사용 하는 **cab** 의 오버 로드를 호출 하 고 또는 값을 반환할 수 있습니다 **`float`** **`long double`** . C 프로그램에서 **cab** 는 항상 **_Dcomplex** 값을 사용 하 고 값을 반환 **`double`** 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|C 헤더|C++ 헤더|
|-------------|--------------|------------------|
|**cab**,               **cabsf**, **cabsf**|\<complex.h>|\<ccomplex>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
