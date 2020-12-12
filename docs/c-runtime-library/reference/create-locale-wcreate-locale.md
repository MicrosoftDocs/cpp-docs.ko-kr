---
description: '자세히 알아보기: _create_locale, _wcreate_locale'
title: _create_locale, _wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: feb2fee7befbaf3f798dc36466674eaa4aec55fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341526"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale, _wcreate_locale

로캘 개체를 만듭니다.

## <a name="syntax"></a>구문

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>매개 변수

*category*<br/>
범주입니다.

*locale*<br/>
로캘 지정자입니다.

## <a name="return-value"></a>반환 값

유효한 *로캘* 및 *범주가* 지정 된 경우는 지정 된 로캘 설정을 **_locale_t** 개체로 반환 합니다. 프로그램의 현재 로캘 설정은 변경되지 않습니다.

## <a name="remarks"></a>설명

**_Create_locale** 함수를 사용 하면 다양 한 CRT 함수 ( **_l** 접미사가 있는 함수)의 로캘별 버전에서 사용할 특정 지역 특정 설정을 나타내는 개체를 만들 수 있습니다. 이 동작은 지정 된 로캘 설정을 현재 환경에 적용 하는 대신 설정이 반환 되는 **_locale_t** 구조로 저장 된다는 점을 제외 하 고 **setlocale** 과 비슷합니다. **_Locale_t** 구조는 더 이상 필요 하지 않을 때 [_free_locale](free-locale.md) 를 사용 하 여 해제 해야 합니다.

**_wcreate_locale** 은 **_create_locale** 의 와이드 문자 버전입니다. **_wcreate_locale** 에 대 한 *로캘* 인수는 와이드 문자 문자열입니다. **_wcreate_locale** 와 **_create_locale** 는 동일 하 게 동작 합니다.

*Category* 인수는 영향을 받는 로캘별 동작의 부분을 지정 합니다. *범주* 에 사용 되는 플래그와 이러한 플래그는 영향을 주는 프로그램의 일부에 대 한 것입니다.

| *범주* 플래그 | 영향 |
|-----------------|---------|
| **LC_ALL** |아래에 나열된 모든 범주입니다. |
| **LC_COLLATE** |**Strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll** 및 **wcsxfrm** 함수를 말합니다. |
| **LC_CTYPE** | 문자 처리 함수 ( **isdigit**, **isxdigit**, **mbstowcs** 및 **mbtowc** 는 영향을 받지 않음)입니다. |
| **LC_MONETARY** | **Localeconv** 함수에서 반환 된 통화 형식 정보입니다. |
| **LC_NUMERIC** | 형식이 지정 된 출력 루틴 (예: **printf**), 데이터 변환 루틴 및 **localeconv** 에서 반환 하는 비 통화 서식 지정 정보에 대 한 소수점 문자입니다. 소수점 문자 외에도 **LC_NUMERIC** 는 천 단위 구분 기호와 [localeconv](localeconv.md)에서 반환 하는 grouping 컨트롤 문자열을 설정 합니다. |
| **LC_TIME** | **Strftime** 및 **wcsftime** 함수 |

이 함수는 *범주* 및 *로캘* 매개 변수의 유효성을 검사 합니다. Category 매개 변수가 이전 표에 지정 된 값 중 하나가 아니거나 *로캘이* **null** 인 경우이 함수는 **null** 을 반환 합니다.

*Locale* 인수는 로캘을 지정 하는 문자열에 대 한 포인터입니다. *로캘* 인수의 형식에 대 한 자세한 내용은 [로캘 이름, 언어 및 국가/지역 문자열](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)을 참조 하세요.

*로캘* 인수는 로캘 이름, 언어 문자열, 언어 문자열 및 국가/지역 코드, 코드 페이지, 언어 문자열, 국가/지역 코드 및 코드 페이지를 사용할 수 있습니다. 사용 가능한 로캘 이름, 언어, 국가/지역 코드 및 코드 페이지의 집합에는 Windows NLS API에서 지 원하는 모든 항목이 포함 됩니다. **_Create_locale** 에서 지 원하는 로캘 이름 집합은 [로캘 이름, 언어 및 국가/지역 문자열](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)에 설명 되어 있습니다. **_Create_locale** 에서 지 원하는 언어 및 국가/지역 문자열 집합은 [언어 문자열](../../c-runtime-library/language-strings.md) 및 [국가/지역 문자열](../../c-runtime-library/country-region-strings.md)에 나열 됩니다.

로캘 설정에 대한 자세한 내용은 [setlocale, _wsetlocale](setlocale-wsetlocale.md)을 참조하세요.

이 함수의 이전 이름인 **__create_locale** (선행 밑줄 두 개 포함)은 더 이상 사용 되지 않습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>참고 항목

[로캘 이름, 언어 및 국가/지역 문자열](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[언어 문자열](../../c-runtime-library/language-strings.md)<br/>
[국가/지역 문자열](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
