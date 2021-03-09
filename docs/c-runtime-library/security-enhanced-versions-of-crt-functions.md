---
description: Security-Enhanced 버전의 CRT 함수에 대해 자세히 알아보세요.
title: 보안이 강화된 CRT 함수 버전
ms.date: 03/21/2018
helpviewer_keywords:
- security [CRT]
- security-enhanced CRT
- CRT, security enhancements
ms.assetid: f87e5a01-4cb2-4379-9e8f-d4693828c55a
ms.openlocfilehash: eda9a98593bb0951c9be357c35492eaf129e3582
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514722"
---
# <a name="security-enhanced-versions-of-crt-functions"></a>보안이 강화된 CRT 함수 버전

런타임 라이브러리 루틴의 더 안전한 버전을 사용할 수 있습니다. CRT의 강화된 보안 기능과 관련된 자세한 내용은 [CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md)을 참조하세요.

## <a name="secure-functions"></a>보안 함수

|CRT 함수|보안이 강화된 함수|Windows Server Update Services와 함께|
|------------------|--------------------------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md)|[_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|파일 액세스 권한을 결정합니다.|
|[_alloca](../c-runtime-library/reference/alloca.md)|[_malloca](../c-runtime-library/reference/malloca.md)|스택에 메모리를 할당합니다.|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md)|[asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|`struct tm` 형식에서 문자열로 시간을 변환합니다.|
|[bsearch](../c-runtime-library/reference/bsearch.md)|[bsearch_s](../c-runtime-library/reference/bsearch-s.md)|정렬된 배열의 이진 검색을 수행합니다.|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|콘솔에서 문자열을 가져옵니다.|
|[_chsize](../c-runtime-library/reference/chsize.md)|[_chsize_s](../c-runtime-library/reference/chsize-s.md)|파일 크기를 변경합니다.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|[clearerr_s](../c-runtime-library/reference/clearerr-s.md)|스트림 오류 표시기를 다시 설정합니다.|
|[_control87, _controlfp, \_ _control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|부동 소수점 제어 단어를 가져오고 설정합니다.|
|[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|형식을 지정하고 콘솔에 출력합니다.|
|[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)|[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|콘솔에서 형식이 지정된 데이터를 읽습니다.|
|[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)|[_ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|`time_t`, `__time32_t` 또는 `__time64_t` 형식에서 문자열로 시간을 변환합니다.|
|[_ecvt](../c-runtime-library/reference/ecvt.md)|[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|숫자를 문자열로 변환 합니다. **`double`**|
|[_fcvt](../c-runtime-library/reference/fcvt.md)|[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|부동 소수점 숫자를 문자열로 변환합니다.|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)|[fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|파일 열기|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|형식이 지정된 데이터를 스트림에 출력합니다.|
|[fread](../c-runtime-library/reference/fread.md)|[fread_s](../c-runtime-library/reference/fread-s.md)|파일에서 읽습니다.|
|[_fread_nolock](../c-runtime-library/reference/fread-nolock.md)|[_fread_nolock_s](../c-runtime-library/reference/fread-nolock-s2.md)|다중 스레드 쓰기 잠금을 사용하지 않고 파일에서 읽습니다.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)|[freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|파일을 다시 엽니다.|
|[fscanf, _fscanf_l, fwscanf, _fwscanf_l](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|스트림에서 형식이 지정된 데이터를 읽습니다.|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)|[_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|현재 시간을 가져옵니다.|
|[_gcvt](../c-runtime-library/reference/gcvt.md)|[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|부동 소수점 값을 문자열로 변환하고 버퍼에 저장합니다.|
|[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)|[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|현재 환경에서 값을 가져옵니다.|
|[, getws를 가져옵니다.](../c-runtime-library/gets-getws.md)|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|`stdin` 스트림에서 한 줄을 가져옵니다.|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)|[_gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|`time_t` 형식에서 `struct tm`으로 또는 `__time64_t` 형식에서 `struct tm`으로 변환|
|[itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md)|[_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|정수 형식을 문자열로 변환|
|[_lfind](../c-runtime-library/reference/lfind.md)|[_lfind_s](../c-runtime-library/reference/lfind-s.md)|지정된 키에 대한 선형 검색을 수행합니다.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)|[localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|시간을 `time_t` 형식에서 `struct tm`으로 또는 `__time64_t` 형식에서 `struct tm`(로컬 수정 포함)으로 변환|
|[_lsearch](../c-runtime-library/reference/lsearch.md)|[_lsearch_s](../c-runtime-library/reference/lsearch-s.md)|값에 대한 선형 검색을 수행합니다. 찾을 수 없는 경우 목록의 끝에 추가합니다.|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md)|[_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|구성 요소에서 경로 이름을 만듭니다.|
|[_mbccpy, _mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md)|[_mbccpy_s, _mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|한 문자열에서 다른 문자열로 멀티바이트 문자를 복사합니다.|
|[_mbsnbcat, _mbsnbcat_l](../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)|[_mbsnbcat_s, _mbsnbcat_s_l](../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)|한 멀티바이트 문자열의 처음 *n* 바이트 이하를 다른 문자열에 추가|
|[_mbsnbcpy, _mbsnbcpy_l](../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)|[_mbsnbcpy_s, _mbsnbcpy_s_l](../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)|문자열의 *n* 바이트를 대상 문자열에 복사|
|[_mbsnbset, _mbsnbset_l](../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)|[_mbsnbset_s, _mbsnbset_s_l](../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md)|문자열의 처음 *n* 바이트를 지정된 문자로 설정|
|[mbsrtowcs](../c-runtime-library/reference/mbsrtowcs.md)|[mbsrtowcs_s](../c-runtime-library/reference/mbsrtowcs-s.md)|멀티바이트 문자열을 해당 와이드 문자열로 변환합니다.|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)|[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|멀티바이트 문자 시퀀스를 해당 와이드 문자 시퀀스로 변환합니다.|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)|[memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|버퍼 간에 문자를 복사합니다.|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md)|[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|한 버퍼를 다른 버퍼로 이동합니다.|
|[_mktemp, _wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)|[_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|고유한 파일 이름을 만듭니다.|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|형식이 지정된 출력을 표준 출력 스트림에 출력합니다.|
|[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)|[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|환경 변수를 생성, 수정 또는 제거합니다.|
|[qsort](../c-runtime-library/reference/qsort.md)|[qsort_s](../c-runtime-library/reference/qsort-s.md)|빠른 정렬을 수행합니다.|
|[rand](../c-runtime-library/reference/rand.md)|[rand_s](../c-runtime-library/reference/rand-s.md)|의사 난수를 생성합니다.|
|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|표준 입력 스트림에서 형식이 지정된 데이터를 읽습니다.|
|[_searchenv, _wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md)|[_searchenv_s, _wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|환경 경로를 사용하여 파일을 검색합니다.|
|[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|[_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|문자열에 형식이 지정된 데이터를 씁니다.|
|[_snscanf, _snscanf_l, _snwscanf, _snwscanf_l](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)|[_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|문자열에서 지정된 길이의 형식이 지정된 데이터를 읽습니다.|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)|[_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|공유할 파일을 엽니다.|
|[_splitpath, _wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)|[_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|경로 이름을 구성 요소로 분해합니다.|
|[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|문자열에 형식이 지정된 데이터를 씁니다.|
|[sscanf, _sscanf_l, swscanf, _swscanf_l](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)|[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|문자열에서 형식이 지정된 데이터를 읽습니다.|
|[strcat, wcscat, _mbscat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)|[strcat_s, wcscat_s, _mbscat_s](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)|문자열을 추가합니다.|
|[strcpy, wcscpy, _mbscpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|[strcpy_s, wcscpy_s, _mbscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)|문자열을 복사합니다.|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md)|[_strdate_s, _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|현재 시스템 날짜를 문자열로 반환합니다.|
|[strerror, _strerror, _wcserror, \_ _wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)|[strerror_s, _strerror_s, _wcserror_s, \_ _wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|시스템 오류 메시지(`strerror`, `_wcserror`)를 가져오거나, 사용자가 제공한 오류 메시지(`_strerror`, `__wcserror`)를 출력합니다.|
|[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)|[_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|문자열을 소문자로 변환합니다.|
|[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|문자열에 문자를 추가합니다.|
|[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)|한 문자열의 문자를 다른 문자열에 복사합니다.|
|[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)|[_strnset_s, _strnset_s_l, _wcsnset_s, _wcsnset_s_l, _mbsnset_s, _mbsnset_s_l](../c-runtime-library/reference/strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md)|문자열의 처음 n자를 지정된 문자로 설정합니다.|
|[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[_strset_s, _strset_s_l, _wcsset_s, _wcsset_s_l, _mbsset_s, _mbsset_s_l](../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md)|문자열의 모든 문자를 지정된 문자로 설정합니다.|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md)|[_strtime_s, _wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|현재 시스템 시간을 문자열로 반환합니다.|
|[strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)|[strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)|현재 로캘이나 전달된 로캘을 사용하여 문자열에서 다음 토큰을 찾습니다.|
|[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)|[_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|문자열을 대문자로 변환합니다.|
|[tmpfile](../c-runtime-library/reference/tmpfile.md)|[tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|임시 파일을 만듭니다.|
|[_tempnam, _wtempnam, tmpnam, _wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|[tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|임시 파일을 만드는 데 사용할 수 있는 이름을 생성합니다.|
|[_umask](../c-runtime-library/reference/umask.md)|[_umask_s](../c-runtime-library/reference/umask-s.md)|기본 파일 사용 권한 마스크를 설정합니다.|
|[_vcprintf, _vcprintf_l, _vcwprintf, _vcwprintf_l](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|인수 목록에 대한 포인터를 사용하여 콘솔에 형식이 지정된 출력을 씁니다.|
|[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 씁니다.|
|[vfscanf, vfwscanf](../c-runtime-library/reference/vfscanf-vfwscanf.md)|[vfscanf_s, vfwscanf_s](../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)|스트림에서 형식이 지정된 데이터를 읽습니다.|
|[vprintf, _vprintf_l, vwprintf, _vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 씁니다.|
|[vscanf, vwscanf](../c-runtime-library/reference/vscanf-vwscanf.md)|[vscanf_s, vwscanf_s](../c-runtime-library/reference/vscanf-s-vwscanf-s.md)|표준 입력 스트림에서 형식이 지정된 데이터를 읽습니다.|
|[vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|[vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 씁니다.|
|[vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, \_ _vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 씁니다.|
|[vsscanf, vswscanf](../c-runtime-library/reference/vsscanf-vswscanf.md)|[vsscanf_s, vswscanf_s](../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)|문자열에서 형식이 지정된 데이터를 읽습니다.|
|[wcrtomb](../c-runtime-library/reference/wcrtomb.md)|[wcrtomb_s](../c-runtime-library/reference/wcrtomb-s.md)|와이드 문자를 멀티바이트 문자 표현으로 변환합니다.|
|[wcsrtombs](../c-runtime-library/reference/wcsrtombs.md)|[wcsrtombs_s](../c-runtime-library/reference/wcsrtombs-s.md)|와이드 문자열을 멀티바이트 문자열 표현으로 변환합니다.|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)|[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|와이드 문자 시퀀스를 해당 멀티바이트 문자 시퀀스로 변환합니다.|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)|[wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|와이드 문자를 해당 멀티바이트 문자로 변환합니다.|

## <a name="see-also"></a>추가 정보

[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
