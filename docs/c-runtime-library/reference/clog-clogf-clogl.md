---
title: clog, clogf, clogl
description: Clog, clogf 및 clogf에 대 한 API 참조 복소수의 자연 로그를 검색 하는 것은 음의 실수 축을 따라 분기를 잘라냅니다.
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 255f83a93c5c7a0c724fad143f028c2832be3173
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555074"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

음의 실수 축을 따라 분기를 사용하여 복소수의 자연 로그를 검색합니다.

## <a name="syntax"></a>구문

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>매개 변수

*-*\
로그의 밑입니다.

## <a name="return-value"></a>반환 값

*Z*의 자연 로그입니다. 결과는 실수 축을 따라 제한이 없으며, 허수 축을 따라 [-iπ, + iπ] 간격 내에 있습니다.

가능한 반환 값은 다음과 같습니다.

|z 매개 변수|반환 값|
|-----------------|------------------|
|양수|z의 밑이 10인 로그|
|0|- ∞|
|음수|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **_Fcomplex** 및 **_Lcomplex** 값을 사용 하 고 반환 하는 **clog** 의 오버 로드를 호출할 수 있습니다. C 프로그램에서 **clog** 는 항상 **_Dcomplex** 값을 사용 하 고 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|C 헤더|C++ 헤더|
|-------------|--------------|------------------|
|**clog**,               **clogf**, **clogf**|\<complex.h>|\<ccomplex>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
