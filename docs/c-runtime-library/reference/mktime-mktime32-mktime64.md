---
description: Mktime, _mktime32, _mktime64에 대해 자세히 알아보세요.
title: mktime, _mktime32, _mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: aebb12324de5a18dfac6ab84b3b7b2c3da15a2ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256421"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

현지 시간을 달력 값으로 변환합니다.

## <a name="syntax"></a>구문

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>매개 변수

*timeptr*<br/>
시간 구조에 대한 포인터입니다. [asctime](asctime-wasctime.md)을 참조하세요.

## <a name="return-value"></a>반환 값

**_mktime32** [time_t](../../c-runtime-library/standard-types.md)형식 값으로 인코딩된 지정 된 일정 시간을 반환 합니다. *Timeptr* 이 1970 년 1 월 1 일 자정 이전의 날짜를 참조 하거나 달력 시간을 표현할 수 없는 경우 **_mktime32** 은 **time_t** 형식으로-1 캐스트를 반환 합니다. **_Mktime32** 를 사용할 때 *timeptr* 에서 2038 년 1 월 18 일 23:59:59 이후 날짜를 참조 하는 경우 **time_t** 형식으로-1 캐스트를 반환 합니다.

*timeptr* 이 3000 년 12 월 31 일 23:59:59 이후 날짜를 참조 하는 경우 **_mktime64** 은 **__time64_t** 형식으로 캐스팅을 반환 합니다.

## <a name="remarks"></a>설명

**Mktime**, **_mktime32** 및 **_mktime64** 함수는 *timeptr* 에서 가리키는 제공 된 시간 구조 (불완전 한 경우)를 정규화 된 값이 있는 완전히 정의 된 구조로 변환한 다음 **time_t** 달력 시간 값으로 변환 합니다. 변환된 시간은 [time](time-time32-time64.md) 함수가 반환한 값과 인코딩이 동일합니다. *Timeptr* 구조의 **tm_wday** 및 **tm_yday** 구성 요소에 대 한 원래 값은 무시 되며 다른 구성 요소의 원래 값은 정상 범위로 제한 되지 않습니다.

**mktime** 는 **_mktime64** 에 해당 하는 인라인 함수입니다. **_USE_32BIT_TIME_T** 정의 되어 있지 않으면 **_mktime32** 와 동일 합니다.

UTC로 조정한 후에는 **_mktime32** 1970 년 1 월 1 일 자정에서 23:59:59 년 1 월 18 일 2038, UTC로 날짜를 처리 합니다. **_mktime64** 은 1970 년 1 월 1 일 자정부터 23:59:59 년 12 월 3000 31 일 까지의 날짜를 처리 합니다. 이렇게 조정 하면 지정 된 날짜가 범위 내에 있는 경우에도 이러한 함수가-1을 반환 하 고 ( **time_t** **__time32_t** 또는 **__time64_t** 으로 캐스팅) 반환 될 수 있습니다. 예를 들어 UTC보다 2시간 빠른 이집트의 카이로에 있으면 *timeptr* 에 지정한 날짜에서 먼저 2시간을 뺍니다. 그러면 해당 날짜가 범위를 벗어날 수 있습니다.

이러한 함수는 tm 구조의 유효성을 검사하고 시간 구조를 채우는 데 사용할 수 있습니다. 성공 하는 경우 이러한 함수는 **tm_yday** **tm_wday** 값을 적절 하 게 설정 하 고 지정 된 달력 시간을 나타내도록 다른 구성 요소를 설정 하지만 해당 값이 정상 범위에 적용 되도록 합니다. **Tm_mday** 의 최종 값은 **tm_mon** 및 **tm_year** 결정 될 때까지 설정 되지 않습니다. **Tm** 구조 시간을 지정 하는 경우 **tm_isdst** 필드를로 설정 합니다.

- 0은 표준 시간이 적용 중임을 나타냅니다.

- 0보다 큰 값은 일광 절약 시간이 적용 중임을 나타냅니다.

- 0보다 작은 값은 C 런타임 라이브러리 코드가 표준 시간 또는 일광 절약 시간이 적용 중인지 여부를 컴퓨팅하도록 합니다.

C 런타임 라이브러리는 [TZ](tzset.md) 환경 변수에서 일광 절약 시간 동작을 결정합니다. **TZ** 를 Win32 API 설정 하지 않으면 [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) 호출을 사용 하 여 운영 체제에서 일광 절약 시간 정보를 가져옵니다. 이러한 정보를 가져오지 못하면 라이브러리에서는 일광 절약 시간 계산 구현을 위한 미국의 규칙이 사용된다고 가정합니다. **tm_isdst** 은 필수 필드입니다. 이 필드를 설정하지 않으면 해당 값이 정의되지 않고 이러한 함수의 반환 값을 예측할 수 없습니다. *Timeptr* 이 [asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)또는 [localtime](localtime-localtime32-localtime64.md) 에 대 한 이전 호출에서 반환 된 **tm** 구조를 가리키는 경우 (또는 이러한 함수의 변형) **tm_isdst** 필드에 올바른 값이 포함 됩니다.

**Gmtime** 및 **localtime** (및 **_gmtime32**, **_gmtime64**, **_localtime32** 및 **_localtime64**)는 스레드 당 단일 버퍼를 변환 하는 데 사용 합니다. 이 버퍼를 **mktime**, **_mktime32** 또는 **_mktime64** 에 제공 하면 이전 내용이 소멸 됩니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *timeptr* 이 null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>샘플 출력

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
