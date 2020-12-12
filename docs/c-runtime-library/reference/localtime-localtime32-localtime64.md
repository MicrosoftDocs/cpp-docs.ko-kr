---
description: Localtime, _localtime32, _localtime64에 대해 자세히 알아보세요.
title: localtime, _localtime32, _localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: e19e419be52788bfd0e4f4a67c72ef8a6737993e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326297"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime, _localtime32, _localtime64

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

구조체 결과에 대 한 포인터를 반환 하거나 함수에 전달 된 날짜가 인 경우 **NULL** 을 반환 합니다.

- 1970년 1월 1일 자정 이전

- 03:14:07 년 1 월 2038 19 일, UTC ( **_time32** 및 **time32_t** 사용).

- 23:59:59 이후, 3000 년 12 월 31 일, UTC ( **_time64** 및 **__time64_t** 사용).

**__time64_t** 구조를 사용 하는 **_localtime64** 에 따라 날짜를 23:59:59 년 12 월 31 일까 지 3000, utc (협정 세계시)까지 표시 하는 반면, **_Localtime32** 는 23:59:59 년 1 월 18 일 년 1 월 2038 18 일을 기준으로 날짜를 나타냅니다.

**localtime** 는 **_localtime64** 로 계산 되는 인라인 함수 이며 **time_t** 는 **__time64_t** 와 같습니다. 컴파일러가 **time_t** 이전 32 비트 **time_t** 으로 해석 해야 하는 경우 **_USE_32BIT_TIME_T** 를 정의할 수 있습니다. 이렇게 하면 **localtime** 이 **_localtime32** 로 평가 됩니다. 2038년 1월 18일 이후에는 애플리케이션에서 오류가 발생할 수 있으므로 이 방식은 사용하지 않는 것이 좋으며, 64비트 플랫폼에서는 이러한 방식이 허용되지 않습니다.

구조체 형식 [tm](../../c-runtime-library/standard-types.md) 의 필드는 다음 값을 저장 하며, 각 값은입니다 **`int`** .

|필드|설명|
|-|-|
|**tm_sec**|분 이후의 초 (0-59)입니다.|
|**tm_min**|시간 이후 분 (0-59)|
|**tm_hour**|자정 이후의 시간 (0-23)입니다.|
|**tm_mday**|월의 일자 (1-31)|
|**tm_mon**|월 (0-11; 1 월 = 0).|
|**tm_year**|연도(현재 연도 - 1900).|
|**tm_wday**|요일 (0-6; 일요일 = 0).|
|**tm_yday**|연간 일자 (0-365; 1 월 1 일 = 0).|
|**tm_isdst**|일광 절약 시간이 적용되면 양수, 일광 절약 시간이 적용되지 않으면 0, 일광 절약 시간의 상태를 알 수 없으면 음수입니다.|

**TZ** 환경 변수가 설정 된 경우 C 런타임 라이브러리에서는 dst (일광 절약 시간) 계산을 구현 하기 위해 미국에 적절 한 규칙을 가정 합니다.

## <a name="remarks"></a>설명

**Localtime** 함수는 [time_t](../../c-runtime-library/standard-types.md) 값으로 저장 된 시간을 변환 하 고 결과를 [tm](../../c-runtime-library/standard-types.md)형식의 구조에 저장 합니다. **`long`** *Sourcetime* 값은 자정 (00:00:00), 1970 년 1 월 1 일 자정 이후 경과 된 시간 (초)을 나타냅니다. 이 값은 일반적으로 [time](time-time32-time64.md) 함수에서 가져옵니다.

[Gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)및 **localtime** 의 32 비트 및 64 비트 버전은 모두 변환에 대해 스레드 당 단일 **tm** 구조를 사용 합니다. 이러한 루틴 중 하나를 호출할 때마다 이전 호출의 결과가 삭제됩니다.

**localtime** 는 사용자가 먼저 전역 환경 변수 **TZ** 를 설정 하는 경우 현지 표준 시간대를 수정 합니다. **TZ** 를 설정 하면 다른 세 가지 환경 변수 (**_timezone**, **_daylight** 및 **_tzname**)도 자동으로 설정 됩니다. **TZ** 변수가 설정 되지 않은 경우 **localtime** 는 제어판의 날짜/시간 응용 프로그램에 지정 된 표준 시간대 정보를 사용 하려고 시도 합니다. 이 정보를 가져올 수 없으면 기본적으로 태평양 표준 시간대를 의미하는 PST8PDT가 사용됩니다. 이러한 변수에 대한 설명은 [_tzset](tzset.md)을 참조하세요. **TZ** 는 **localtime** 의 ANSI 표준 정의의 일부가 아니라 Microsoft 확장입니다.

> [!NOTE]
> 대상 환경에서는 일광 절약 시간이 적용되는지 확인해야 합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *Sourcetime* 이 null 포인터 이거나 *sourcetime* 값이 음수 이면 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 C 헤더|필수 C++ 헤더|
|-------------|---------------------|-|
|**localtime**, **_localtime32**, **_localtime64**|\<time.h>|\<ctime> 또는 \<time.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

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

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
