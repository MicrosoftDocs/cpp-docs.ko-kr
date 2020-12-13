---
description: '자세히 알아보기: 로캘'
title: 로캘
ms.date: 04/11/2018
f1_keywords:
- c.international
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
ms.openlocfilehash: 660a4fb0103de8c1ac06272c711e02fcd6d12289
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331074"
---
# <a name="locale"></a>로캘

*로캘* 은 프로그램을 사용자 지정하는 데 사용할 수 있는 국가/지역 및 언어 설정을 참조합니다. 일부 로캘 종속 범주는 날짜 및 통화 값의 표시 형식을 포함합니다. 자세한 내용은 [로캘 범주](../c-runtime-library/locale-categories.md)를 참조하세요.

**_l** 접미사가 없는 함수를 사용하면서 현재 프로그램 또는 스레드 로캘 정보의 일부 또는 모두를 변경하거나 쿼리하려면 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 함수를 사용합니다. **_l** 접미사가 있는 함수는 특정 함수만 실행하는 동안 해당 로캘 정보에 대해 전달되는 로캘 매개 변수를 사용합니다. **_l** 접미사가 있는 함수와 함께 사용할 로캘을 만들려면 [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)을 사용합니다. 이 로캘을 해제하려면 [_free_locale](../c-runtime-library/reference/free-locale.md)을 사용합니다. 현재 로캘을 가져오려면 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md)을 사용합니다.

[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)을 사용하여 각 스레드가 자체 로캘을 포함하는지 또는 프로그램의 모든 스레드가 동일한 로캘을 공유하는지를 제어합니다. 자세한 내용은 [로캘 및 코드 페이지](../text/locales-and-code-pages.md)를 참조하세요.

다음 표에서 **_s**("보안") 접미사로 표시된 함수는 더 안전한 버전의 함수로 사용할 수 있습니다. 자세한 내용은 [CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md)을 참조하세요.

## <a name="locale-dependent-routines"></a>로캘 종속 루틴

|루틴에서 반환된 값|기능|**setlocale** 범주 설정 종속성|
|-------------|---------|---------------------------------------------|
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|문자를 부동 소수점 값으로 변환합니다.|**LC_NUMERIC**|
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|문자를 정수 값으로 변환합니다.|**LC_NUMERIC**|
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|문자를 64비트 정수 값으로 변환합니다.|**LC_NUMERIC**|
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|문자를 long 값으로 변환합니다.|**LC_NUMERIC**|
|[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|문자를 double-long 값으로 변환합니다.|**LC_NUMERIC**|
|[is 루틴](../c-runtime-library/is-isw-routines.md)|지정된 정수를 특정 조건에 대해 테스트합니다.|**LC_CTYPE**|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|선행 바이트를 테스트합니다.|**LC_CTYPE**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|숫자 수량 형식 지정에 대한 적합한 값을 읽습니다.|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|현재 로캘(STDLIB.H에 정의된 매크로) 내의 모든 멀티바이트 문자의 최대 길이(바이트)입니다.|**LC_CTYPE**|
|[_mbccpy, _mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[_mbccpy_s, _mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|하나의 멀티바이트 문자를 복사합니다.|**LC_CTYPE**|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|멀티바이트 문자의 바이트 수의 유효성을 검사하고 해당 수를 반환합니다.|**LC_CTYPE**|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|멀티바이트 문자열의 경우: 문자열의 각 문자의 유효성을 검사합니다. 문자열 길이를 반환합니다.|**LC_CTYPE**|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|멀티바이트 문자의 시퀀스를 해당되는 와이드 문자 시퀀스로 변환합니다.|**LC_CTYPE**|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|멀티바이트 문자를 해당되는 와이드 문자로 변환합니다.|**LC_CTYPE**|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 함수|형식이 지정된 출력을 씁니다.|**LC_NUMERIC**(기수 문자 출력 여부 결정)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 함수|형식이 지정된 입력을 읽습니다.|**LC_NUMERIC**(기수 문자 인식 여부 결정)|
|[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|프로그램에 대한 로캘을 선택합니다.|해당 없음|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|두 문자열의 문자를 비교합니다.|**LC_COLLATE**|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|대/소문자에 상관없이 두 문자열을 비교합니다.|**LC_CTYPE**|
|[_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|두 문자열의 문자를 비교합니다(대/소문자 구분 없음).|**LC_COLLATE**|
|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|두 문자열의 처음 **n** 개 문자를 비교합니다.|**LC_COLLATE**|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|대/소문자에 상관없이 두 문자열의 문자를 비교합니다.|**LC_CTYPE**|
|[_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|두 문자열의 처음 **n** 개 문자를 비교합니다(대/소문자 구분 없음).|**LC_COLLATE**|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|제공된 **format** 인수에 따라 날짜 및 시간 값의 형식을 지정합니다.|**LC_TIME**|
|[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|현재 위치에서 제공된 문자열의 각 대문자를 소문자로 변환합니다.|**LC_CTYPE**|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|문자열을 값으로 변환 합니다. **`double`**|**LC_NUMERIC**(기수 문자 인식 여부 결정)|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|문자열을 값으로 변환 합니다. **`long`**|**LC_NUMERIC**(기수 문자 인식 여부 결정)|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|문자열을 부호 없는 long 값으로 변환합니다.|**LC_NUMERIC**(기수 문자 인식 여부 결정)|
|[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|현재 위치에서 문자열의 각 소문자를 대문자로 변환합니다.|**LC_CTYPE**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|문자열을 로캘에 따라 데이터 정렬된 형식으로 변형합니다.|**LC_COLLATE**|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|제공된 문자를 해당 소문자로 변환합니다.|**LC_CTYPE**|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|제공된 문자를 해당 대문자로 변환합니다.|**LC_CTYPE**|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|와이드 문자의 시퀀스를 해당되는 멀티바이트 문자의 시퀀스로 변환합니다.|**LC_CTYPE**|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|와이드 문자를 해당되는 멀티바이트 문자로 변환합니다.|**LC_CTYPE**|

> [!NOTE]
> 멀티바이트 루틴의 경우 멀티바이트 코드 페이지는 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)로 설정된 로캘과 동일해야 합니다. **_MB_CP_LOCALE** 의 인수를 사용하는 [_setmbcp](../c-runtime-library/reference/setmbcp.md)는 멀티바이트 코드 페이지를 **setlocale** 코드 페이지와 동일하게 만듭니다.

## <a name="see-also"></a>참고 항목

[국제화](../c-runtime-library/internationalization.md)<br/>
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
