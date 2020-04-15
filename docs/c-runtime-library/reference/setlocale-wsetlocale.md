---
title: setlocale, _wsetlocale
description: Microsoft C 런타임(CRT) 라이브러리 함수 setlocale _wsetlocale및 에 대해 설명합니다.
ms.date: 4/2/2020
api_name:
- _wsetlocale
- setlocale
- _o__wsetlocale
- _o_setlocale
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: 2834229839153c3154caadf71e5fb30d84ed2f1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353719"
---
# <a name="setlocale-_wsetlocale"></a>setlocale, _wsetlocale

런타임 로캘을 설정하거나 가져옵니다.

## <a name="syntax"></a>구문

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>매개 변수

*범주*\
로캘의 영향을 받는 범주입니다.

*로캘*\
로캘 지정자입니다.

## <a name="return-value"></a>반환 값

유효한 *로캘* 및 *범주가* 부여되면 지정된 로캘 및 *범주와*연결된 문자열에 대한 포인터를 *반환합니다.* *로캘* 또는 *범주가* 유효하지 않으면 null 포인터를 반환하고 프로그램의 현재 로캘 설정은 변경되지 않습니다.

예: 호출

```C
setlocale( LC_ALL, "en-US" );
```

문자열만 반환하는 모든 범주를 설정합니다.

```Output
en-US
```

**setlocale에서** 반환된 문자열을 복사하여 프로그램의 로캘 정보 의 해당 부분을 복원할 수 있습니다. **setlocale에서**반환되는 문자열에 전역 또는 스레드 로컬 저장소가 사용됩니다. 나중에 **setlocale를** 호출하여 문자열을 덮어쓰므로 이전 호출에서 반환된 문자열 포인터를 무효화합니다.

## <a name="remarks"></a>설명

**setlocale** 함수를 사용하여 *로캘* 및 *범주에서*지정한 현재 프로그램 로캘 정보의 일부 또는 전부를 설정, 변경 또는 쿼리합니다. *로캘은* 프로그램의 특정 측면을 사용자 지정할 수 있는 지역(국가/지역 및 언어)을 나타냅니다. 일부 로캘 종속 범주에는 날짜 형식 지정 및 통화 값의 형식 표시가 포함됩니다. 컴퓨터에서 여러 양식이 지원되는 언어의 기본 문자열로 *로캘을* 설정하는 경우 **setlocale** 반환 값을 확인하여 적용 중인 언어를 확인해야 합니다. 예를 들어 *로캘을* "중국어"로 설정하면 반환 값은 "중국어 간체" 또는 "중국어 번체"일 수 있습니다.

**_wsetlocale** **세트로테의**와이드 문자 버전입니다. *_wsetlocale 로캘* 인수 및 반환 **값은** 와이드 문자 문자열입니다. **_wsetlocale 및** **setlocale** 그렇지 않으면 동일하게 작동합니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

*범주* 인수는 영향을 받는 프로그램의 로캘 정보의 일부를 지정합니다. *범주에* 사용되는 매크로와 영향을 받는 프로그램의 일부는 다음과 같습니다.

|*범주* 플래그|영향|
|-|-|
| **Lc_all** | 아래에 나열된 모든 범주입니다. |
| **LC_COLLATE** | **스트콜,** **_stricoll,** **wcscoll,** **_wcsicoll,** **strxfrm , strxfrm**, _strncoll , **_strnicoll**, **_wcsncoll**, **_wcsnicoll**, 및 **wcsxfrm** 기능 . **_strnicoll** |
| **LC_CTYPE** | 문자 처리 **함수(는**영향을 받지 않는 숫자, **isxdigit,** **mbstowcs**및 **mbtowc)** |
| **LC_MONETARY** | **localeconv** 함수에서 반환되는 통화 식 서식 정보입니다. |
| **LC_NUMERIC** | 서식이 지정된 출력 루틴(예: **printf)** 및 데이터 변환 루틴 및 **localeconv에서**반환하는 비금전적 서식 정보의 소수점 문자입니다. LC_NUMERIC 소수점 문자 외에도 수천 **LC_NUMERIC** 개의 구분 기호와 [localeconv에서](localeconv.md)반환되는 그룹화 컨트롤 문자열을 설정합니다. |
| **LC_TIME** | **스트프타임** 및 **wcsftime** 함수입니다. |

이 함수는 범주 매개 변수의 유효성을 검사합니다. 범주 매개 변수가 이전 테이블에 제공된 값 중 하나가 아닌 경우 매개 변수 유효성 [검사에](../../c-runtime-library/parameter-validation.md)설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 실행을 계속할 수 있는 경우 함수는 **errno를** **EINVAL로** 설정하고 **NULL을**반환합니다.

*로캘* 인수는 로캘을 지정하는 문자열에 대한 포인터입니다. *로캘* 인수의 형식에 대한 자세한 내용은 [로캘 이름, 언어 및 국가/지역 문자열을](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)참조하십시오. *locale*에서 빈 문자열을 가리키면 로캘은 구현에서 정의된 네이티브 환경입니다. **C** 값은 C 변환에 대한 최소 ANSI 준수 환경을 지정합니다. **C** 로캘은 모든 **char** 데이터 형식이 1바이트이고 해당 값이 항상 256보다 적다고 가정합니다.

프로그램을 시작할 때 다음 문을 실행합니다.

`setlocale( LC_ALL, "C" );`

*로캘* 인수는 로캘 이름, 언어 문자열, 언어 문자열 및 국가/지역 코드, 코드 페이지 또는 언어 문자열, 국가/지역 코드 및 코드 페이지를 취할 수 있습니다. 사용 가능한 로캘 이름, 언어, 국가/지역 코드 및 코드 페이지 집합에는 Windows NLS API에서 지원하는 모든 이름이 포함됩니다. **setlocale에서** 지원하는 로캘 이름 집합은 [로캘 이름, 언어 및 국가/지역 문자열에 설명되어 있습니다.](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) **setlocale에서** 지원하는 언어 및 국가/지역 문자열 집합은 [언어 문자열](../../c-runtime-library/language-strings.md) 및 [국가/지역 문자열에 나열됩니다.](../../c-runtime-library/country-region-strings.md) 코드에 포함되거나 스토리지에 직렬화된 로캘 문자열의 성능과 유지 관리를 위해 로캘 이름 형식을 사용하는 것이 좋습니다. 로캘 이름 문자열은 언어와 국가/지역 이름 형식보다 운영 체제 업데이트에 의해 변경될 가능성이 적습니다.

*로캘* 인수로 전달되는 null 포인터는 **setlocale에게** 국제 환경을 설정하는 대신 쿼리하도록 지시합니다. *로캘* 인수가 null 포인터인 경우 프로그램의 현재 로캘 설정은 변경되지 않습니다. 대신 **setlocale는** 스레드의 현재 로캘 *범주와* 연결된 문자열에 대한 포인터를 반환합니다. *범주* 인수가 **LC_ALL**경우 함수는 세미콜론으로 구분된 각 범주의 현재 설정을 나타내는 문자열을 반환합니다. 예: 호출 시퀀스

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

다음을 반환합니다.

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

LC_ALL **범주와** 연결된 문자열입니다.

다음 예제는 **LC_ALL** 범주와 관련이 있습니다. 문자열 중 하나 ". OCP"와 ". ACP"는 코드 페이지 번호 대신 사용하여 해당 로캘 이름에 대한 사용자 기본 OEM 코드 페이지 및 사용자 기본 ANSI 코드 페이지의 사용을 각각 지정할 수 있습니다.

- `setlocale( LC_ALL, "" );`

   로캘을 운영 체제에서 가져온 사용자 기본 ANSI 코드 페이지인 기본값으로 설정합니다. 로캘 이름은 [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)에서 반환되는 값으로 설정됩니다. 코드 페이지가 [GetACP](/windows/win32/api/winnls/nf-winnls-getacp)에서 반환되는 값으로 설정됩니다.

- `setlocale( LC_ALL, ".OCP" );`

   로캘을 운영 체제에서 얻은 현재 OEM 코드 페이지로 설정합니다. 로캘 이름은 [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)에서 반환되는 값으로 설정됩니다. 코드 페이지는 [GetLocaleInfo](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex) [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) .

- `setlocale( LC_ALL, ".ACP" );`

   로캘을 운영 체제에서 얻은 ANSI 코드 페이지로 설정합니다. 로캘 이름은 [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)에서 반환되는 값으로 설정됩니다. 코드 페이지는 [GetLocaleInfo](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex) [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) .

- `setlocale( LC_ALL, "<localename>" );`

   * \<로캘을 로캘 *이름으로>로캘 이름으로 표시된 로캘 이름으로 설정합니다. 코드 페이지는 [GetLocaleInfo](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex) [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) .

- `setlocale( LC_ALL, "<language>_<country>" );`

   호스트 운영 체제에서 가져온 기본 코드 페이지와 함께 * \<언어>* 및 * \<국가>* 표시된 언어 및 국가/지역으로 로캘을 설정합니다. 코드 페이지는 [GetLocaleInfo](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex) [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) .

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   언어>, * \<국가>* 및 * \<code_page>* 문자열로 표시된 * \<언어, *국가/지역 및 코드 페이지로 로캘을 설정합니다. 언어, 국가/지역 및 코드 페이지의 다양한 조합을 사용할 수 있습니다. 예를 들어, 이 호출은 코드 페이지 1252에 따라 로캘을 프랑스어(캐나다)로 설정합니다.

   `setlocale( LC_ALL, "French_Canada.1252" );`

   이 호출은 기본 ANSI 코드 페이지에 따라 로캘을 프랑스어(캐나다)로 설정합니다.

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   이 호출은 기본 OEM 코드 페이지에 따라 로캘을 프랑스어(캐나다)로 설정합니다.

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   * \<로캘을 언어>* 지정한 언어로 설정하고 지정된 언어의 기본 국가/지역 및 호스트 운영 체제에서 가져온 해당 국가/지역의 사용자 기본 ANSI 코드 페이지를 사용합니다. 예를 들어 **setlocale에** 대한 다음 호출은 기능적으로 동일합니다.

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   성능 및 유지 관리에 첫 번째 폼을 사용하는 것이 좋습니다.

- `setlocale( LC_ALL, ".<code_page>" );`

   지정한 코드 페이지에 대한 기본 국가/지역 및 언어(호스트 운영 체제에 의해 정의됨)와 함께 *<code_page>* 에 의해 표시되는 값으로 코드 페이지를 설정합니다.

코드 페이지를 변경하려면 **범주가 LC_ALL** 또는 **LC_CTYPE** 있어야 합니다. 예를 들어 호스트 운영 체제의 기본 국가/지역 및 언어가 "미국"과 "영어"인 경우 **setlocale에** 대한 다음 두 호출은 기능적으로 동일합니다.

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

자세한 내용은 [C/C++ 전처리기 참조](../../preprocessor/c-cpp-preprocessor-reference.md)에서 [setlocale](../../preprocessor/setlocale.md) pragma 지시문을 참조하세요.

[_configthreadlocale](configthreadlocale.md) 함수는 **setlocale가** 프로그램의 모든 스레드의 로캘에 영향을 미치는지 또는 호출 스레드의 로캘에만 영향을 미치는지 여부를 제어하는 데 사용됩니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_setlocale.c
//
// This program demonstrates the use of setlocale when
// using two independent threads.
//

#include <locale.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date in the current
// locale's format.
int get_date(unsigned char* str)
{
    __time64_t ltime;
    struct tm  thetime;

    // Retrieve the current time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // "%#x" is the long date representation in the
    // current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm *)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to the argument
// and prints the date.
uintptr_t __stdcall SecondThreadFunc( void* pArguments )
{
    unsigned char str[BUFF_SIZE];
    char * locale = (char *)pArguments;

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, locale));

    // Retrieve the date string from the helper function
    if (get_date(str) == 0)
    {
        printf("The date in %s locale is: '%s'\n", locale, str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread sets the locale to English
// and then spawns a second thread (above) and prints the date.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the locale of the main thread to US English.
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "en-US"));

    // Create the second thread with a German locale.
    // Our thread function takes an argument of the locale to use.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      "de-DE", 0, &threadID );

    if (get_date(str) == 0)
    {
        // Retrieve the date string from the helper function
        printf("The date in en-US locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>참고 항목

[로캘 이름, 언어 및 국가/지역 문자열](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)\
[로캘](../../c-runtime-library/locale.md)\
[로케일콘프](localeconv.md)\
[_mbclen, 음블렌, _mblen_l](mbclen-mblen-mblen-l.md)\
[스트렌, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[스트콜 함수](../../c-runtime-library/strcoll-functions.md)\
[스트레프 타임, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
