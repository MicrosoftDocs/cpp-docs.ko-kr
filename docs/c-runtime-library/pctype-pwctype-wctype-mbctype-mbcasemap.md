---
description: _Pctype, _pwctype, _wctype, _mbctype, _mbcasemap에 대해 자세히 알아보세요.
title: _pctype, _pwctype, _wctype, _mbctype, _mbcasemap
ms.date: 11/04/2016
api_name:
- _pctype
- _pwctype
- _wctype
- _mbctype
- _mbcasemap
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- pwctype
- pctype
- mbctype
- mbcasemap
- _mbcasemap
- _mbctype
- _pctype
- _wctype
- _pcwtype
helpviewer_keywords:
- _wctype function
- _pwctype function
- _pctype function
- _mbctype function
- wctype function
- pwctype function
- pctype function
- mbcasemap function
- mbctype function
- _mbcasemap function
ms.assetid: 7f5e1107-c43b-4b9b-b387-781e6d2373cb
ms.openlocfilehash: 4122d282b3b205af3d6fb67f9755f9c13c4bb5e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213457"
---
# <a name="_pctype-_pwctype-_wctype-_mbctype-_mbcasemap"></a>_pctype, _pwctype, _wctype, _mbctype, _mbcasemap

이러한 전역 변수에는 문자 분류 함수에서 사용하는 정보가 포함되어 있습니다. 내부용으로만 사용됩니다.

## <a name="syntax"></a>구문

```
extern const unsigned short *_pctype;
extern const wctype_t *_pwctype;
extern const unsigned short _wctype[];
extern unsigned char _mbctype[];
extern unsigned char _mbcasemap[];
```

## <a name="remarks"></a>설명

`_pctype`, `_pwctype` 및 `_wctype`의 정보는 [isupper, _isupper_l, iswupper, _iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [islower, iswlower, _islower_l, _iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [isdigit, iswdigit, _isdigit_l, _iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md), [isspace, iswspace, _isspace_l, _iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [isalnum, iswalnum, _isalnum_l, _iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [ispunct, iswpunct, _ispunct_l, _iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [isgraph, iswgraph, _isgraph_l, _iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md), [toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [tolower, _tolower, towlower, _tolower_l 및 _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md) 함수에서 내부적으로 사용됩니다. 이러한 전역 변수를 액세스하는 대신 이러한 함수를 사용해야 합니다.

`_mbctype` 및 `_mbcasemap`의 정보는 [_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md), [_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md), [_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md), [_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md), [_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md), [_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md), [_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md), [_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md), [_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md), [_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md), [_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md), [_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md), [_ismbslead, _ismbstrail, _ismbslead_l 및 _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)에서 내부적으로 사용됩니다. 전역 변수를 액세스하는 대신 이러한 함수를 사용합니다.

## <a name="requirements"></a>요구 사항

공용으로 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[is, isw 루틴](../c-runtime-library/is-isw-routines.md)<br/>
[__pctype_func](../c-runtime-library/pctype-func.md)
