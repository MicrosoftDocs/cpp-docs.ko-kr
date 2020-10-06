---
title: 표준 형식
ms.date: 11/04/2016
f1_keywords:
- __time64_t
- _diskfree_t
- _CRT_DUMP_CLIENT
- _fsize_t
- __timeb64
- File
- __utimeb64
- jmp_buf
- __finddata64_t
- _wfinddata_t
- _finddata_t
- utimbuf64
- wint_t
- wctrans_t
- wctype_t
- _HFILE
- _secerr_handler_func
- clock_t
- fpos_t
- _dev_t
- time64_t
- wfinddata64_t
- stat64
- ldiv_t
- _EXCEPTION_POINTERS
- terminate_function
- size_t
- timeb64
- tm
- _HEAPINFO
- unexpected_function
- _CrtMemState
- _se_translator_function
- sig_atomic_t
- _CRT_REPORT_HOOK
- _complex
- _w_finddatai64_t
- _timeb
- _onexit_t
- _RTC_ErrorNumber
- lconv
- _PNH
- _off_t
- ptrdiff_t
- time_t
- _FPIEEE_RECORD
- _exception
- __w_finddata64_t
- __stat64
- _utimbuf
- __utimbuf64
- div_t
- _CRT_ALLOC_HOOK
- int8_t
- uint8_t
- int16_t
- uint16_t
- int32_t
- uint32_t
- int64_t
- int_least8_t
- uint_least8_t
- int_least16_t
- uint_least16_t
- int_least32_t
- uint_least32_t
- int_least64_t
- uint_least64_t
- int_fast8_t
- uint_fast8_t
- int_fast16_t
- uint_fast16_t
- int_fast32_t
- uint_fast32_t
- int_fast64_t
- uint_fast64_t
- intmax_t
- uintmax_t
helpviewer_keywords:
- __timeb64 type
- tm type
- clock_t type
- intptr_t type
- diskfree_t type
- wctype_t type
- CRT_DUMP_CLIENT type
- sig_atomic_t type
- _PNH type
- time_t type
- wfinddata_t type
- timeb64
- CRT, standard types
- wint_t type
- _RTC_ErrorNumber type
- _diskfree_t type
- _dev_t type
- _wfinddata_t type
- HFILE type
- __utimbuf64 type
- div_t type
- _onexit_t type
- _secerr_handler_func type
- FPIEEE_RECORD type
- HEAPINFO type
- PNH type
- _CRT_ALLOC_HOOK type
- _se_translater_function type
- va_list type
- wctrans_t type
- secerr_handler_func type
- _locale_t type
- timeb type
- lconv type
- utimbuf type
- dev_t type
- unexpected_function typedef
- _complex type
- _off_t type
- off_t type
- RTC_ErrorNumber type
- _FPIEEE_RECORD type
- exception type
- _CRT_REPORT_HOOK type
- _HEAPINFO type
- ldiv_t type
- terminate_function type
- uintptr_t type
- _CRT_DUMP_CLIENT type
- _utimbuf type
- wfinddatai64_t type
- fpos_t type
- wchar_t type
- CRT_ALLOC_HOOK type
- _HFILE type
- __time64_t type
- _timeb type
- CrtMemState type
- __finddata64_t type
- _exception type
- stat type
- onexit_t type
- FILE constant
- _stat type
- finddata_t type
- __wfinddata64_t type
- ptrdiff_t type
- complex types
- _wfinddatai64_t type
- _EXCEPTION_POINTERS type
- jmp_buf type
- se_translater_function type
- size_t type
- EXCEPTION_POINTERS type
- __stat64 type
- _fsize_t type
- CRT_REPORT_HOOK type
- _finddata_t type
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
ms.openlocfilehash: 376c29371fb9213ed46435b41bea1666058c7b4e
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765307"
---
# <a name="standard-types"></a>표준 형식

Microsoft 런타임 라이브러리는 다음과 같은 표준 형식 및 typedefs를 정의합니다.

### <a name="fixed-width-integral-types-stdinth"></a>고정 너비 정수 계열 형식(stdint.h)

|속성|해당하는 기본 제공 형식|
|----------|-------------------------------|
|int8\_t, uint8\_t|signed char, unsigned char|
|int16\_t, uint16\_t|short, unsigned short|
|int32\_t, uint32\_t|int, unsigned int|
|int64\_t, uint64\_t|long long, unsigned long long|
|int_least8_t, uint_least8_t|signed char, unsigned char|
|int_least16_t, uint_least16_t|short, unsigned short|
|int_least32_t, uint_least32_t|int, unsigned int|
|int_least64_t, uint_least64_t|long long, unsigned long long|
|int_fast8_t, uint_fast8_t|signed char, unsigned char|
|int_fast16_t, uint_fast16_t|int, unsigned int|
|int_fast32_t, uint_fast32_t|int, unsigned int|
|int_fast64_t, uint_fast64_t|long long, unsigned long long|
|intmax_t, uintmax_t|long long, unsigned long long|

|Type|Description|선언됨|
|----------|-----------------|-----------------|
|`clock_t`(long)|시간 값을 저장합니다. [clock](../c-runtime-library/reference/clock.md)에 의해 사용됩니다.|TIME.H|
|`_complex` 구조체|복소수의 실수와 허수 부분을 저장합니다. [_cabs](../c-runtime-library/reference/cabs.md)에 의해 사용됩니다.|MATH.H|
|`_CRT_ALLOC_HOOK`|사용자 정의 후크 함수에 대한 형식이 정의됩니다. [_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)에서 사용됩니다.|CRTDBG.H|
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)에서 호출되는 콜백 함수에 대한 형식이 정의됩니다.|CRTDBG.H|
|`_CrtMemState` 구조체|C 런타임 디버그 힙의 현재 상태에 대한 정보를 제공합니다.|CRTDBG.H|
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|[_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)에서 호출되는 콜백 함수에 대한 형식이 정의됩니다.<br /><br /> 이 함수에 대한 매개 변수는 보고서 유형, 출력 메시지 및 콜백 함수의 반환 값입니다.|CRTDBG.H|
|`dev_t`, `_dev_t` short 또는 부호 없는 정수|디바이스 핸들을 나타냅니다.|SYS\TYPES.H|
|`_diskfree_t` 구조체|디스크 드라이브에 대한 정보가 들어 있습니다. [_getdiskfree](../c-runtime-library/reference/getdiskfree.md)**.** 에 의해 사용됩니다.|DOS.H 및 DIRECT.H|
|`div_t`, `ldiv_t` 및 `lldiv_t` 구조|[div](reference/div.md), [ldiv](./reference/div.md) 및 [lldiv](./reference/div.md)에 의해 반환된 값을 각각 저장합니다.|STDLIB.H|
|`errno_t` 정수|`errno`의 오류 코드를 처리하는 매개 변수 또는 함수 반환 형식에 사용됩니다.|STDDEF.H,<br /><br /> CRTDEFS.H|
|`_exception` 구조체|[_matherr](../c-runtime-library/reference/matherr.md)에 대한 오류 정보를 저장합니다.|MATH.H|
|`_EXCEPTION_POINTERS`|예외 레코드를 포함합니다. 자세한 내용은 [예외 포인터](/windows/win32/api/winnt/ns-winnt-exception_pointers)를 참조하세요.|FPIEEE.H|
|`FILE` 구조체|스트림의 현재 상태에 대한 정보를 저장합니다. 모든 스트림 I/O 작업에 사용됩니다.|STDIO.H|
|`_finddata_t`, `_wfinddata_t`, `_finddata32_t`, `_wfinddata32_t`, `_finddatai64_t`, `_wfinddatai64_t`, `__finddata64_t`, `__wfinddata64_t`, `__finddata32i64_t`, `__wfinddata32i64_t`, `__finddata64i32_t`, `__wfinddata64i32_t` 구조|[_findfirst, _wfindfirst 및 관련 함수](../c-runtime-library/reference/findfirst-functions.md)와 [_findnext, _wfindnext 및 관련 함수](../c-runtime-library/reference/findnext-functions.md)에 의해 반환되는 file-attribute 정보를 저장합니다. 구조체 멤버에 대한 자세한 내용은 [파일 이름 검색 함수](../c-runtime-library/filename-search-functions.md)를 참조하세요.|IO.H, WCHAR.H|
|`_FPIEEE_RECORD` 구조체|IEEE 부동 소수점 예외에 대한 정보를 포함합니다. [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)로 사용자 정의 트랩 처리기에 전달됩니다.|FPIEEE.H|
|`fpos_t` ( **`__int64`** 대상 플랫폼에 따라 long 정수, 또는 구조체)|[fgetpos](../c-runtime-library/reference/fgetpos.md) 및 [fsetpos](../c-runtime-library/reference/fsetpos.md)에서 파일 내의 모든 위치를 고유하게 지정하기 위한 정보를 기록하는 데 사용됩니다.|STDIO.H|
|`_fsize_t`(부호 없는 long 정수)|파일의 크기를 나타내는 데 사용됩니다.|IO.H,<br /><br /> WCHAR.H|
|`_HEAPINFO` 구조체|[_heapwalk](../c-runtime-library/reference/heapwalk.md)의 다음 힙 항목에 대한 정보가 포함됩니다.|MALLOC.H|
|`_HFILE`(void \*)|운영 체제 파일 핸들입니다.|CRTDBG.H|
|`imaxdiv_t`|몫과 나머지를 모두 포함하여 [imaxdiv](../c-runtime-library/reference/imaxdiv.md) 함수에서 반환되는 값의 형식입니다.|inttypes.h|
|`ino_t`, `_ino_t`(부호 없는 short)|상태 정보를 반환하기 위해 사용됩니다.|WCHAR.H|
|`intmax_t`|부호 있는 정수 형식 값을 표시할 수 있는 부호 있는 정수 형식입니다.|stdint.h|
|`intptr_t` ( **`__int64`** 대상 플랫폼에 따라 long 정수 또는)|Win32와 Win64 플랫폼에서 포인터 또는 핸들을 저장합니다.|STDDEF.H 및 기타 포함 파일|
|`jmp_buf` 배열|[setjmp](../c-runtime-library/reference/setjmp.md) 및 [longjmp](../c-runtime-library/reference/longjmp.md)에서 프로그램 환경을 저장하고 복원하는 데 사용됩니다.|SETJMP.H|
|`lconv` 구조체|다른 국가/지역의 숫자 값에 대한 서식 규칙을 포함합니다. [localeconv](../c-runtime-library/reference/localeconv.md)에서 사용됩니다.|LOCALE.H|
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12`(long double 또는 부호 없는 문자 배열)|long double 값을 나타내는 데 사용합니다.|STDLIB.H|
|`_locale_t` 구조체|현재 로캘 값을 저장합니다. 모든 로캘 특정 C 런타임 라이브러리에서 사용됩니다.|CRTDEFS.H|
|`mbstate_t`|멀티 바이트 문자 변환의 상태를 추적합니다.|WCHAR.H|
|`off_t`, `_off_t` long 정수|파일 오프셋 값을 나타냅니다.|WCHAR.H, SYS\TYPES.H|
|`_onexit_t`,<br /><br /> `_onexit_m_t` 포인터|[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)에서 반환됩니다.|STDLIB.H|
|`_PNH` 함수 포인터|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)에 대한 인수의 형식입니다.|NEW.H|
|`ptrdiff_t` ( **`__int64`** 대상 플랫폼에 따라 long 정수 또는)|두 개의 포인터 구독 결과입니다.|CRTDEFS.H|
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|순수 가상 함수를 호출할 때 호출되는 콜백 함수에 대한 형식을 정의합니다. [_get_purecall_handler, _set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)에서 사용됩니다. `_purecall_handler` 함수에 void 반환 형식이 있어야 합니다.|STDLIB.H|
|`_RTC_error_fn` 형식 정의|런타임 오류 검사를 처리하는 함수에 대한 형식을 정의합니다. [_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)에서 사용됩니다.|RTCAPI.H|
|`_RTC_error_fnW` 형식 정의|런타임 오류 검사를 처리하는 함수에 대한 형식을 정의합니다. [_RTC_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md)에서 사용됩니다.|RTCAPI.H|
|`_RTC_ErrorNumber` 열거형|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) 및 [_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)에 대한 오류 조건을 정의합니다.|RTCAPI.H|
|`_se_translator_function`|예외를 변환하는 콜백 함수에 대한 형식을 정의합니다. 첫 번째 매개 변수는 예외 코드이고, 두 번째 매개 변수는 예외 기록입니다. [_set_se_translator](../c-runtime-library/reference/set-se-translator.md)에 의해 사용됩니다.|EH.H|
|`sig_atomic_t` 정수|비동기 인터럽트의 출현에도 원자 항목으로 수정할 수 있는 개체의 형식입니다. [signal](../c-runtime-library/reference/signal.md)과 함께 사용됩니다.|SIGNAL.H|
|`size_t`(대상 플랫폼에 따라 부호 없는 __int64 또는 부호 없는 정수)|연산자의 결과 **`sizeof`** 입니다.|CRTDEFS.H 및 기타 포함 파일|
|`_stat` 구조체|[_stat](../c-runtime-library/reference/stat-functions.md) 및 [_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)에서 반환되는 파일 상태 정보가 포함됩니다.|SYS\STAT.H|
|`__stat64` 구조체|[_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)[_stat64](../c-runtime-library/reference/stat-functions.md) 및 [_wstat64](../c-runtime-library/reference/stat-functions.md)에서 반환되는 파일 상태 정보가 포함됩니다.|SYS\STAT.H|
|`_stati64` 구조체|[_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [_stati64](../c-runtime-library/reference/stat-functions.md) 및 [_wstati64](../c-runtime-library/reference/stat-functions.md)에서 반환되는 파일 상태 정보가 포함됩니다.|SYS\STAT.H|
|`terminate_function` 형식 정의|[terminate](../c-runtime-library/reference/terminate-crt.md)가 호출될 때 호출되는 콜백 함수에 대한 유형을 정의합니다. [set_terminate](../c-runtime-library/reference/set-terminate-crt.md)에 의해 사용됩니다.|EH.H|
|`time_t`(__int64 또는 long 정수)|시간 값을 [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [time](../c-runtime-library/reference/time-time32-time64.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) 및 [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)로 나타냅니다. 1970년 1월 1일 0:00 UTC 이후의 초 수 _USE_32BIT_TIME_T가 정의된 경우 `time_t`는 long 정수입니다. 정의 되지 않은 경우 64비트 정수입니다.|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time32_t`(long 정수)|시간 값을 [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 및 [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)로 나타냅니다.|CRTDEFS.H, SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time64_t` (**`__int64`**)|시간 값을 [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [_ctime64, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) 및 [_time64](../c-runtime-library/reference/time-time32-time64.md)로 나타냅니다.|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`_timeb` 구조체|[_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 및 [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)에서 현재 시스템 시간을 저장하는 데 사용됩니다.|SYS\TIMEB.H|
|`__timeb32` 구조체|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 및 [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)에서 현재 시스템 시간을 저장하는 데 사용됩니다.|SYS\TIMEB.H|
|`__timeb64` 구조체|[_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 및 [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)에서 현재 시스템 시간을 저장하는 데 사용됩니다.|SYS\TIMEB.H|
|`tm` 구조체|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) 및 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)에서 시간 정보를 저장하고 검색하는 데 사용됩니다.|TIME.H|
|`uintmax_t`|부호 없는 정수 계열 형식 값을 표시할 수 있는 부호 없는 정수 형식입니다.|stdint.h|
|`uintptr_t` ( **`__int64`** 대상 플랫폼에 따라 long 정수 또는)|`intptr_t`의 부호 없는 정수 또는 부호 없는 __int64 버전입니다.|STDDEF.H 및 기타 포함 파일|
|`unexpected_function`|[unexpected](../c-runtime-library/reference/unexpected-crt.md)가 호출될 때 호출되는 콜백 함수에 대한 형식을 정의합니다. [set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)에 의해 사용됩니다.|EH.H|
|`_utimbuf` 구조체|[_utime, _wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 및 [_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)에서 파일 수정 날짜를 변경하는 데 사용되는 파일 액세스 및 수정 시간을 저장합니다.|SYS\UTIME.H|
|`_utimbuf32` 구조체|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 및 [_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)에서 파일 수정 날짜를 변경하는 데 사용되는 파일 액세스 및 수정 시간을 저장합니다.|SYS\UTIME.H|
|`__utimbuf64` 구조체|[_utime64, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 및 [_futime64](../c-runtime-library/reference/futime-futime32-futime64.md)에서 현재 시간을 저장하는 데 사용됩니다.|SYS\UTIME.H|
|`va_list` 구조체|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 및 [va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 매크로에서 필요한 정보를 보관하는 데 사용됩니다. 호출된 함수가 다른 함수에 인수로 전달할 수 있는 `va_list` 형식의 변수를 선언합니다.|STDARG.H,<br /><br /> CRTDEFS.H|
|**`wchar_t`** 와이드 문자|국제 시장을 겨냥한 이식 가능한 프로그램을 작성하는 데 유용합니다.|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\STAT.H|
|`wctrans_t` 정수|로캘별 문자 매핑을 나타냅니다.|WCTYPE.H|
|`wctype_t` 정수|모든 언어 문자 집합의 모든 문자를 나타낼 수 있습니다.|WCHAR.H,<br /><br /> CRTDEFS.H|
|`wint_t` 정수|모든 와이드 문자 또는 넓은 끝-파일의 값을 보유할 수 있는 데이터 개체의 형식입니다.|WCHAR.H,<br /><br /> CRTDEFS.H|

## <a name="see-also"></a>참조

[C 런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)
