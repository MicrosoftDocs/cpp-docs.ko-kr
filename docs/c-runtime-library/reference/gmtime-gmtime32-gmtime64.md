---
title: gmtime, _gmtime32, _gmtime64
description: Gmtime, _gmtime32 및 _gmtime64에 대 한 API 참조 time_t 값을 tm 구조체로 변환 합니다.
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: b3dd09e828b972f05a4c45c30ebc3e5edb68f551
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556465"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

**Time_t** 시간 값을 **tm** 구조체로 변환 합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>매개 변수

*sourceTime*<br/>
저장된 시간에 대한 포인터입니다. 시간은 1970년 1월 1일 자정(00:00:00)(UTC(협정 세계시)) 이후 경과한 시간(초)으로 표현됩니다.

## <a name="return-value"></a>반환 값

[tm](../../c-runtime-library/standard-types.md) 형식의 구조체에 대한 포인터입니다. 반환 된 구조체의 필드는 현지 시간이 아닌 UTC로 *Sourcetime* 인수의 계산 된 값을 보유 합니다. 각 구조 필드는 다음과 같이 형식입니다 **`int`** .

|필드|Description|
|-|-|
|**tm_sec**|분 이후의 초 (0-59)입니다.|
|**tm_min**|시간 이후 분 (0-59)|
|**tm_hour**|자정 이후의 시간 (0-23)입니다.|
|**tm_mday**|월의 일자 (1-31)|
|**tm_mon**|월 (0-11; 1 월 = 0).|
|**tm_year**|연도(현재 연도 - 1900).|
|**tm_wday**|요일 (0-6; 일요일 = 0).|
|**tm_yday**|연간 일자 (0-365; 1 월 1 일 = 0).|
|**tm_isdst**|**Gmtime**의 경우 항상 0입니다.|

**Gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)및 [localtime](localtime-localtime32-localtime64.md) 의 32 비트 및 64 비트 버전은 모두 변환에 대해 스레드 당 하나의 공통 **tm** 구조를 사용 합니다. 이러한 함수 중 하나를 호출할 때마다 이전 호출의 결과가 삭제됩니다. *Sourcetime* 이 1970 년 1 월 1 일 자정 이전의 날짜를 나타내는 경우 **gmtime** 는 **NULL**을 반환 합니다. 오류가 반환 되지 않습니다.

**__time64_t** 구조를 사용 하는 **_gmtime64**에 따라 날짜를 23:59:59 년 12 월 31 일까 지 3000, utc로 표현할 수 있으며, **_gmtime32** 23:59:59 1 월 2038 18 일를 사용 하는 경우에만 날짜를 표시 합니다. 1970년 1월 1일 자정은 두 함수 모두에 대한 날짜 범위의 하한입니다.

**gmtime** 는 **_gmtime64**로 계산 되는 인라인 함수 이며 **time_t** **_USE_32BIT_TIME_T** 정의 되지 않은 경우 **__time64_t** 와 동일 합니다. 컴파일러가 **time_t** 를 이전 32 비트 **time_t**로 해석 하도록 강제 해야 하는 경우 **_USE_32BIT_TIME_T**를 정의할 수 있지만 이렇게 하면 **gmtime** 가 **_gmtime32** 로 줄 **되어 time_t로** 정의 **됩니다.** 이 방법은 64비트 플랫폼에서 허용되지 않고 2038년 1월 18일 이후 애플리케이션이 작동하지 않을 수 있기 때문에 권장되지 않습니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *Sourcetime* 이 null 포인터 이거나 *sourcetime* 값이 음수 이면 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL**로 설정 합니다.

## <a name="remarks"></a>설명

**_Gmtime32** 함수는 *sourcetime* 값을 분할 하 고, TIME. H에 정의 된 **tm**형식의 정적으로 할당 된 구조에 저장 합니다. *Sourcetime* 값은 일반적으로 [time](time-time32-time64.md) 함수 호출에서 가져옵니다.

> [!NOTE]
> 대부분의 경우 대상 환경에서는 일광 절약 시간이 적용되는지 확인하려고 합니다. C 런타임 라이브러리에서는 DST(일광 절약 시간) 계산 구현을 위한 미국 규칙이 사용된다고 가정합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 C 헤더|필수 C++ 헤더|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<ctime> 또는 \<time.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
