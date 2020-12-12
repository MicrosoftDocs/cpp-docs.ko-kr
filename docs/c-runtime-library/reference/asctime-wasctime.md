---
description: Asctime, _wasctime에 대해 자세히 알아보세요.
title: asctime, _wasctime
ms.date: 4/2/2020
api_name:
- _wasctime
- asctime
- _o__wasctime
- _o_asctime
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: 3ae075481b364af01bfa75f1cc29423de9fcdbf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260802"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

**Tm** 시간 구조를 문자열로 변환 합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [asctime_s, _wasctime_s](asctime-s-wasctime-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>매개 변수

*timeptr*<br/>
시간/날짜 구조체입니다.

## <a name="return-value"></a>반환 값

**asctime** 는 문자열 결과에 대 한 포인터를 반환 합니다. **_wasctime** 는 와이드 문자 문자열 결과에 대 한 포인터를 반환 합니다. 오류 반환 값이 없습니다.

## <a name="remarks"></a>설명

이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [asctime_s, _wasctime_s](asctime-s-wasctime-s.md)를 참조하세요.

**Asctime** 함수는 구조체로 저장 된 시간을 문자열로 변환 합니다. *Timeptr* 값은 일반적으로 **gmtime** 또는 localtime에 대 한 호출에서 가져옵니다 .이 값은 에 정의 된 **tm** 구조체에 대 한 포인터를 반환 합니다.

|timeptr 멤버|값|
|--------------------|-----------|
|**tm_hour**|자정 이후의 시간 (0-23)|
|**tm_isdst**|일광 절약 시간이 적용되면 양수, 일광 절약 시간이 적용되지 않으면 0, 일광 절약 시간의 상태를 알 수 없으면 음수입니다. C 런타임 라이브러리에서는 DST(일광 절약 시간) 계산 구현을 위한 미국의 규칙이 사용된다고 가정합니다.|
|**tm_mday**|월간 일자 (1-31)|
|**tm_min**|시간 이후 분 (0-59)|
|**tm_mon**|월 (0-11; 1 월 = 0)|
|**tm_sec**|분 이후의 초 (0-59)|
|**tm_wday**|요일 (0-6; 일요일 = 0)|
|**tm_yday**|연간 일자 (0-365; 1 월 1 일 = 0)|
|**tm_year**|연도(현재 연도 빼기 1900)|

또한 변환된 문자열은 현지 표준 시간대 설정에 따라 조정됩니다. 현지 시간 구성에 대한 정보는 [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md) 및 [localtime](localtime-localtime32-localtime64.md) 함수를 참조하고 표준 시간대 환경 및 전역 변수 정의에 대한 정보는 [_tzset](tzset.md) 함수를 참조하세요.

**Asctime** 에 의해 생성 된 문자열 결과에는 정확히 26 자가 포함 되 고 형식이 `Wed Jan 02 02:03:55 1980\n\0` 있습니다. 24시간제가 사용됩니다. 모든 필드에는 상수 너비가 있습니다. 줄 바꿈 문자 및 null 문자는 문자열의 마지막 두 자리를 차지합니다. **asctime** 는 정적으로 할당 된 단일 버퍼를 사용 하 여 반환 문자열을 포함 합니다. 이 함수를 호출할 때마다 이전 호출의 결과가 삭제됩니다.

**_wasctime** 는 **asctime** 의 와이드 문자 버전입니다. **_wasctime** 및 **asctime** 는 동일 하 게 동작 합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *Timeptr* 이 null 포인터 이거나 범위를 벗어난 값을 포함 하는 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mapping"></a>제네릭 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> 또는 \<wchar.h>|

## <a name="example"></a>예제

이 프로그램은 시스템 시간을 정수 (long) **aclock** 에 배치 하 고,이를 **newtime** 으로 변환한 다음 **asctime** 함수를 사용 하 여 출력에 대 한 문자열 형식으로 변환 합니다.

```C
// crt_asctime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
    struct tm   *newTime;
    time_t      szClock;

    // Get time in seconds
    time( &szClock );

    // Convert time to struct tm form
    newTime = localtime( &szClock );

    // Print local time as a string.
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996
    // Note: asctime is deprecated; consider using asctime_s instead
}
```

```Output
Current date and time: Sun Feb 03 11:38:58 2002
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
