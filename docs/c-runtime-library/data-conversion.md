---
title: 데이터 변환 | Microsoft 문서
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12574f9a8a2da2072d1196cbd769ac87cf31c2f7
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="data-conversion"></a>데이터 변환

이러한 루틴은 다른 한 양식에서 다른 양식으로 데이터를 변환합니다. 일반적으로 이러한 루틴은 사용자가 작성할 수 있는 변환보다 더 빠르게 실행됩니다. *to* 접두사로 시작하는 각 루틴은 함수 및 매크로로 구현됩니다. 구현 선택에 대한 자세한 내용은 [함수와 매크로 중 선택](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)을 참조하세요.

## <a name="data-conversion-routines"></a>데이터 변환 루틴

|루틴에서 반환된 값|사용|
|-------------|---------|
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|정수의 절대값 찾기|
|[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|문자열을 **float**로 변환|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|문자열을 **int**로 변환|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|문자열을 **__int64** 또는 **long long**로 변환|
|[atol, _atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|문자열을 **long**으로 변환|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|UTF-16 또는 UTF-32 문자를 해당 멀티 바이트 문자로 변환|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|**double**을 지정된 길이의 문자열로 변환|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|**double**을 소수점 뒤의 자릿수를 지정하는 문자열로 변환|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|**double** 수를 문자열로 변환하고 문자열을 버퍼에 저장|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|정수 형식을 문자열로 변환|
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|**long** 정수의 절대값 찾기|
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|**long long** 정수의 절대값 찾기|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|1바이트 멀티바이트 문자를 해당 2바이트 멀티바이트 문자로 변환|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|JIS(Japan Industry Standard) 문자를 JMS(일본 Microsoft) 문자로 변환|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|JMS 문자를 JIS 문자로 변환|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|멀티바이트 문자를 1바이트 히라가나 코드로 변환|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|멀티바이트 문자를 1바이트 가타카나 코드로 변환|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|2바이트 멀티바이트 문자를 해당 1바이트 멀티바이트 문자로 변환|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|멀티바이트 문자를 해당하는 UTF-16 또는 UTF-32 문자로 변환|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|멀티바이트 문자의 시퀀스를 해당되는 와이드 문자 시퀀스로 변환|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|멀티바이트 문자를 해당되는 와이드 문자로 변환|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|문자열을 **double**로 변환|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|문자열을 **long** 정수로 변환|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|문자열을 **부호 없는 long** 정수로 변환|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|문자열을 로캘별 정보를 기준으로 정렬된 형식으로 변환|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|문자를 ASCII 코드로 변환||
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|문자를 테스트하고 소문자(현재 대문자인 경우)로 변환|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|문자를 무조건 소문자로 변환|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|문자를 테스트하고 대문자(현재 소문자인 경우)로 변환|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|문자를 무조건 대문자로 변환|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|와이드 문자의 시퀀스를 해당되는 멀티바이트 문자의 시퀀스로 변환|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|와이드 문자를 해당되는 멀티바이트 문자로 변환|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|와이드 문자 문자열을 **double**로 변환|
|[_wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|와이드 문자 문자열을 **int**로 변환|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|와이드 문자 문자열을 **__int64** 또는 **long long**으로 변환|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|와이드 문자 문자열을 **long**으로 변환|

## <a name="see-also"></a>참고 항목

[범주별 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
