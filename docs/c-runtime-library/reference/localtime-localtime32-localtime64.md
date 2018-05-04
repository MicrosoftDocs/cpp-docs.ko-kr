---
title: localtime, _localtime32, _localtime64 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _localtime64
- _localtime32
- localtime
apilocation:
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
apitype: DLLExport
f1_keywords:
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
dev_langs:
- C++
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 778b2d214551c5848dd091e33dbbab1814544fb4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="localtime-localtime32-localtime64"></a>localtime, _localtime32, _localtime64

시간 값을 변환하고 현지 표준 시간대에 맞게 수정합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>매개 변수

*sourceTime*<br/>
저장된 시간에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

구조 결과에 대 한 포인터를 반환 하거나 **NULL** 날짜 함수에 전달 하는 경우:

- 1970년 1월 1일 자정 이전

- 03시 14분: 07 2038 년 1 월 19 일 UTC 이후 (사용 하 여 **_time32** 및 **time32_t**).

- 23시 59분: 59를 3000 년 12 월 31 일 UTC 이후 (사용 하 여 **_time64** 및 **__time64_t**).

**_localtime64**를 사용 하 여 **__time64_t** 구조을 사용 하면 날짜 23시 59분: 59 까지의 3000 년 12 월 31 일 (UTC) 협정 세계시를 표현할 수 있지만 **_localtime32** 23시 59분: 59 까지의 2038 년 1 월 18 일 UTC 날짜를 나타냅니다.

**localtime** 계산 되는 인라인 함수 인지 **_localtime64**, 및 **time_t** 같습니다 **__time64_t**합니다. 컴파일러가 해석 하도록 하는 경우 **time_t** 이전 32 비트로 **time_t**를 정의할 수 있습니다 **_USE_32BIT_TIME_T**합니다. 이렇게 하면이로 인해 **localtime** 로 평가 되려면 **_localtime32**합니다. 2038년 1월 18일 이후에는 응용 프로그램에서 오류가 발생할 수 있으므로 이 방식은 사용하지 않는 것이 좋으며, 64비트 플랫폼에서는 이러한 방식이 허용되지 않습니다.

필드는 구조체 형식의 [tm](../../c-runtime-library/standard-types.md) 각각 나타내는 다음 값을 저장 한 **int**:

|필드|설명|
|-|-|
|**tm_sec**|초 후 1 분 (0-59).|
|**tm_min**|분 후에 시간 (0-59).|
|**tm_hour**|자정 이후의 시간 (0-23).|
|**tm_mday**|날짜 (1-31)입니다.|
|**tm_mon**|월 (0-11; 1 월 = 0).|
|**tm_year**|연도(현재 연도 - 1900).|
|**tm_wday**|요일 (0-6; 일요일 = 0).|
|**tm_yday**|연간 일자 (0-365; 1 월 1 일 = 0).|
|**tm_isdst**|일광 절약 시간이 적용되면 양수, 일광 절약 시간이 적용되지 않으면 0, 일광 절약 시간의 상태를 알 수 없으면 음수입니다.|

경우는 **TZ** 환경 변수는 설정, C 런타임 라이브러리 간주 규칙 미국에 적합 한 일광 절약 시간제가 (DST) 계산 구현을 위한 합니다.

## <a name="remarks"></a>설명

**localtime** 함수 변환으로 저장 하는 한 번은 [time_t](../../c-runtime-library/standard-types.md) 값 형식의 구조에 결과 저장 하 고 [tm](../../c-runtime-library/standard-types.md)합니다. **긴** 값 *sourceTime* 자정 이후 경과 된 초를 나타냅니다 (00: 00:00), 1970 년 1 월 1 일 UTC입니다. 이 값에서 가져온 일반적으로 [시간](time-time32-time64.md) 함수입니다.

32 비트 및 64 비트 버전의 두 [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md), 및 **localtime** 단일을 사용 하 여 모든 **tm** 변환에 대 한 스레드당 구조입니다. 이러한 루틴 중 하나를 호출할 때마다 이전 호출의 결과가 삭제됩니다.

**localtime** 사용자 먼저 전역 환경 변수를 설정 하는 경우 현지 표준 시간대에 대 한 수정 **TZ**합니다. 때 **TZ** 설정 되어 다른 세 가지 변수 (**_timezone**, **_daylight**, 및 **_tzname**)도 자동으로 설정 됩니다. 경우는 **TZ** 변수를 설정 하지 않으면 **localtime** 제어판의 날짜/시간 응용 프로그램에 지정 된 표준 시간대 정보를 사용 하려고 시도 합니다. 이 정보를 가져올 수 없으면 기본적으로 태평양 표준 시간대를 의미하는 PST8PDT가 사용됩니다. 이러한 변수에 대한 설명은 [_tzset](tzset.md)을 참조하세요. **TZ** Microsoft 확장 이며 ANSI 표준 정의의 일부가 아닌 **localtime**합니다.

> [!NOTE]
> 대상 환경에서는 일광 절약 시간이 적용되는지 확인해야 합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. 경우 *sourceTime* 가 null 포인터인 경우는 *sourceTime* 값이 음수인 경우에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 하는이 함수를 이러한 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) . 실행을 계속 허용 된 경우 함수는 반환 **NULL** 설정 **errno** 를 **EINVAL**합니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 C 헤더|필수 C++ 헤더|
|-------------|---------------------|-|
|**localtime**, **_localtime32**, **_localtime64**|\<time.h>|\<ctime > 또는 \<. h >|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
    if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime->tm_hour = 12;

    char buff[30];
    asctime_s( buff, sizeof(buff), newtime );
    printf( "%.19s %s\n", buff, am_pm );
}
```

```Output
Tue Feb 12 10:05:58 AM
```

## <a name="see-also"></a>참고자료

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
