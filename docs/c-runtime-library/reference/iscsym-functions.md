---
description: Iscsym, iscsymf, __iscsym, __iswcsym, __iscsymf, __iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l에 대해 자세히 알아보세요.
title: iscsym, iscsymf, __iscsym, __iswcsym, __iscsymf, __iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l
ms.date: 11/04/2016
api_name:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
ms.openlocfilehash: e6b979800caf404ee79f8913b0431b941acd20cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332697"
---
# <a name="iscsym-iscsymf-__iscsym-__iswcsym-__iscsymf-__iswcsymf-_iscsym_l-_iswcsym_l-_iscsymf_l-_iswcsymf_l"></a>iscsym, iscsymf, __iscsym, __iswcsym, __iscsymf, __iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l

정수가 식별자로 사용할 수 있는 문자를 나타내는지 여부를 결정합니다.

## <a name="syntax"></a>구문

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수입니다. *c* 는 함수의 좁은 문자 버전에 대해 0-255 범위 내에 있어야 합니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*C* 가 문자, 밑줄 또는 숫자인 경우 **__iscsym** 와 **__iswcsym** 둘 다 0이 아닌 값을 반환 합니다. *C* 가 문자 또는 밑줄 인 경우 **__iscsymf** 와 **__iswcsymf** 둘 다 0이 아닌 값을 반환 합니다. *C* 가 테스트 조건을 충족 하지 않는 경우 이러한 루틴은 각각 0을 반환 합니다. **_L** 접미사가 있는 이러한 함수 버전은 로캘 종속 동작에 현재 로캘 대신 전달 된 *로캘을* 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

## <a name="remarks"></a>설명

전처리기 매크로 _CTYPE_DISABLE_MACROS가 정의되지 않은 경우 이러한 루틴은 매크로로 정의됩니다. 이러한 루틴의 매크로 버전을 사용하는 경우 인수를 두 번 이상 평가할 수 있습니다. 인수 목록 내에서 의도하지 않은 결과를 생성하는 식을 사용할 때는 주의해야 합니다.

이전 버전과의 호환성을 위해 **iscsym** 및 **iscsymf** [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md) 정의 되지 않았거나 0으로 정의 된 경우에만 매크로로 정의 됩니다. 그렇지 않으면 정의 되지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**iscsym**, **iscsymf**, **__iscsym**, **__iswcsym**, **__iscsymf**, **__iswcsymf**, **_iscsym_l, _iswcsym_l** **, _iscsymf_l**,  **_iswcsymf_l**|C \<ctype.h><br /><br /> C + +: \<cctype> 또는 \<ctype.h>|

**Iscsym**, **iscsymf**, **__iscsym**, **__iswcsym**, **__iscsymf**, **__Iswcsymf**, _iscsym_l **, _iswcsym_l**, _iscsymf_l **및**  **_iswcsymf_l** 루틴은 Microsoft 전용입니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자 분류](../../c-runtime-library/character-classification.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[is, isw 루틴](../../c-runtime-library/is-isw-routines.md)<br/>
