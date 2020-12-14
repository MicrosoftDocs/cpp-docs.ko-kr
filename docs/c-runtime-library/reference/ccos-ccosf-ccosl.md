---
description: '자세히 알아보기: ccos, ccosf, ccosl'
title: ccos, ccosf, ccosl
ms.date: 11/04/2016
api_name:
- ccos
- ccosf
- ccosl
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
- ccos
- ccosf
- ccosl
- complex/ccos
- complex/ccosf
- complex/ccosl
helpviewer_keywords:
- ccos function
- ccosf function
- ccosl function
ms.assetid: 4ab936ac-ff85-49ac-9418-2b69cf5d4696
ms.openlocfilehash: 54036a2ddd3d61bba1d11a4841eaab1bd546c0ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275141"
---
# <a name="ccos-ccosf-ccosl"></a>ccos, ccosf, ccosl

복소수의 코사인을 검색합니다.

## <a name="syntax"></a>구문

```C
_Dcomplex ccos(
   _Dcomplex z
);
_Fcomplex ccos(
   _Fcomplex z
);  // C++ only
_Lcomplex ccos(
   _Lcomplex z
);  // C++ only
_Fcomplex ccosf(
   _Fcomplex z
);
_Lcomplex ccosl(
   _Lcomplex z
);
```

### <a name="parameters"></a>매개 변수

*z*<br/>
라디안으로 각도를 나타내는 복소수입니다.

## <a name="return-value"></a>반환 값

*Z* 의 코사인 값 (라디안)입니다.

## <a name="remarks"></a>설명

C + +에서는 오버 로드를 허용 하므로 **_Fcomplex** 및 **_Lcomplex** 값을 사용 하 고 반환 하는 **ccos** 의 오버 로드를 호출할 수 있습니다. C 프로그램에서 **ccos** 는 항상 **_Dcomplex** 값을 사용 하 고 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|C 헤더|C++ 헤더|
|-------------|--------------|------------------|
|**ccos**,               **ccosf**, **ccosl**|\<complex.h>|\<ccomplex>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
