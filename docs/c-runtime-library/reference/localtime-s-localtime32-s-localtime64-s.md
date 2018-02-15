---
title: "localtime_s, _localtime32_s, _localtime64_s | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
dev_langs:
- C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e30705867a9114fd44b8850d5cf950c2c1d8c4ce
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s
시간 값을 변환하고 현지 표준 시간대에 맞게 수정합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)의 버전입니다.  
  
## <a name="syntax"></a>구문  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `_tm`  
 입력할 시간 구조체에 대한 포인터입니다.  
  
 `time`  
 저장된 시간에 대한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 정상적으로 실행되는 경우 0입니다. 오류가 있을 경우 반환 값은 오류 코드입니다. 오류 코드는 Errno.h에서 정의됩니다. 이러한 오류의 목록은 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.  
  
### <a name="error-conditions"></a>오류 조건  
  
|`_tm`|`time`|반환 값|`_tm`의 값|잘못된 매개 변수 처리기 호출|  
|-----------|------------|------------------|--------------------|---------------------------------------|  
|`NULL`|any|`EINVAL`|수정 안 됨|예|  
|`NULL` 아님(유효한 메모리를 가리킴)|`NULL`|`EINVAL`|모든 필드가 -1로 설정됨|예|  
|`NULL` 아님(유효한 메모리를 가리킴)|0보다 작거나 `_MAX__TIME64_T`보다 큼|`EINVAL`|모든 필드가 -1로 설정됨|아니요|  
  
 처음 두 오류 조건의 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수가 호출됩니다. 계속해서 실행하도록 허용된 경우 이러한 함수는 `errno`를 `EINVAL`로 설정하고 `EINVAL`을 반환합니다.  
  
## <a name="remarks"></a>설명  
 `_localtime32_s` 함수는 [time_t](../../c-runtime-library/standard-types.md) 값으로 저장된 시간을 변환하고 그 결과를 `tm` 형식의 구조체에 저장합니다. `long` 값 `timer`는 1970년 1월 1일 자정(00:00:00)(UTC) 이후 경과된 초를 나타냅니다. 이 값은 일반적으로 `time` 함수에서 가져옵니다.  
  
 `_localtime32_s`는 사용자가 먼저 전역 환경 변수 `TZ`를 설정한 경우 현지 표준 시간대에 맞게 수정됩니다. `TZ`를 설정하면 세 가지 다른 환경 변수(`_timezone`, `_daylight` 및 `_tzname`)도 자동으로 설정됩니다. `TZ` 변수를 설정하지 않으면 `localtime32_s`는 제어판의 날짜/시간 응용 프로그램에 지정된 표준 시간대 정보를 사용하려고 시도합니다. 이 정보를 가져올 수 없으면 기본적으로 태평양 표준 시간대를 의미하는 PST8PDT가 사용됩니다. 이러한 변수에 대한 설명은 [_tzset](../../c-runtime-library/reference/tzset.md)을 참조하세요. `TZ`는 Microsoft 확장이며 `localtime`의 ANSI 표준 정의의 일부가 아닙니다.  
  
> [!NOTE]
>  대상 환경에서는 일광 절약 시간이 적용되는지 확인해야 합니다.  
  
 `__time64_t` 구조체를 사용하는 `_localtime64_s`는 3001년 1월 18일 23:59:59(UTC - 협정 세계시)까지 날짜를 표현할 수 있습니다. 반면, `_localtime32_s`는 2038년 1월 18일 23:59:59(UTC)까지의 날짜를 나타냅니다.  
  
 `localtime_s`는 `_localtime64_s`로 계산되는 인라인 함수이며 `time_t`는 `__time64_t`와 동일합니다. 컴파일러에서 `time_t` 를 이전의 32비트 `time_t`로 해석하게 해야 하는 경우 `_USE_32BIT_TIME_T`를 정의할 수 있습니다. 이렇게 하면 `localtime_s`가 `_localtime32_s`로 계산됩니다. 2038년 1월 18일 이후에는 응용 프로그램에서 오류가 발생할 수 있으므로 이 방식은 사용하지 않는 것이 좋으며, 64비트 플랫폼에서는 이러한 방식이 허용되지 않습니다.  
  
 구조체 형식 [tm](../../c-runtime-library/standard-types.md)의 필드는 다음 값을 저장하며, 각 값은 `int`입니다.  
  
 `tm_sec`  
 초 후 1 분 (0-59).  
  
 `tm_min`  
 분 후에 시간 (0-59).  
  
 `tm_hour`  
 자정 이후의 시간 (0-23).  
  
 `tm_mday`  
 날짜 (1-31)입니다.  
  
 `tm_mon`  
 월 (0-11; 1 월 = 0).  
  
 `tm_year`  
 연도(현재 연도 - 1900).  
  
 `tm_wday`  
 요일 (0-6; 일요일 = 0).  
  
 `tm_yday`  
 연간 일자 (0-365; 1 월 1 일 = 0).  
  
 `tm_isdst`  
 일광 절약 시간이 적용되면 양수, 일광 절약 시간이 적용되지 않으면 0, 일광 절약 시간의 상태를 알 수 없으면 음수입니다. `TZ` 환경 변수가 설정된 경우 C 런타임 라이브러리에서는 DST(일광 절약 시간) 계산을 구현하기 위해 미국에 적절한 규칙이 사용된다고 가정합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`localtime_s`|\<time.h>|  
|`_localtime32_s`|\<time.h>|  
|`_localtime64_s`|\<time.h>|  
  
 호환성에 대한 자세한 내용은 소개 단원의 [호환성](../../c-runtime-library/compatibility.md) 부분을 참조하세요.  
  
## <a name="example"></a>예  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## <a name="sample-output"></a>샘플 출력  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## <a name="see-also"></a>참고 항목  
 [시간 관리](../../c-runtime-library/time-management.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)
