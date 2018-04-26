---
title: _mkgmtime, _mkgmtime32, _mkgmtime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
dev_langs:
- C++
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b6c9547a26f8497b15cfbc4aba7c76efe9d1830
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

가 나타내는 UTC 시간으로 변환는 **구조체** **tm** UTC 시간으로 표시 한 **time_t** 유형입니다.

## <a name="syntax"></a>구문

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>매개 변수

*timeptr*<br/>
UTC 시간 형식에 대 한 포인터는 **구조체** **tm** 변환 합니다.

## <a name="return-value"></a>반환 값

형식의 수량 **__time32_t** 또는 **__time64_t** 자정, 1970 년 1 월 1 일 utc (협정 세계시) 이후 경과 된 시간 (초)의 수를 나타내는입니다. 날짜 범위를 벗어나면 (설명 부분 참조) 또는 입력 유효한 시간으로 해석할 수 없습니다, 반환 값은-1입니다.

## <a name="remarks"></a>설명

**_mkgmtime32** 및 **_mkgmtime64** 함수는 UTC 시간을 변환는 **__time32_t** 또는 **__time64_t** 에 시간을 나타내는 형식 UTC입니다. 현지 시간을 UTC 시간으로 변환 하려면 사용 하 여 **mktime**, **_mktime32**, 및 **_mktime64** 대신 합니다.

**_mkgmtime** 으로 계산 되는 인라인 함수 이며 **_mkgmtime64**, 및 **time_t** 같습니다 **__time64_t**합니다. 컴파일러가 해석 하도록 하는 경우 **time_t** 이전 32 비트로 **time_t**를 정의할 수 있습니다 **_USE_32BIT_TIME_T**합니다. 응용 프로그램은 2038 년 1 월 18 일 후 실패할 수 있으므로 권장 되지는 않습니다 (32 비트의 최대 범위 **time_t**), 64 비트 플랫폼에서 전혀 되어서는 안 됩니다.

에 전달 하는 구조 시간 바뀝니다 다음과 같이 동일한 방식으로 변경 되는 **_mktime** 함수:는 **tm_wday** 및 **tm_yday** 필드가 새로 설정 된 값의 값에 기반 **tm_mday** 및 **tm_year**합니다. 지정 하는 경우는 **tm** 구조 시간을 설정는 **tm_isdst** 필드:

- 0은 표준 시간이 적용 중임을 나타냅니다.

- 0보다 큰 값은 일광 절약 시간이 적용 중임을 나타냅니다.

- 0보다 작은 값은 C 런타임 라이브러리 코드가 표준 시간 또는 일광 절약 시간이 적용 중인지 여부를 계산하도록 합니다.

C 런타임 라이브러리는 TZ 환경 변수를 사용하여 올바른 일광 절약 시간을 결정합니다. TZ가 설정되어 있지 않으면 운영 체제를 쿼리하여 올바른 국가별 일광 절약 시간 동작을 가져옵니다. **tm_isdst** 필수 필드입니다. 을 설정 하지 값 정의 되지 않습니다 및 반환 값을 **mktime** 를 예측할 수 없습니다.

범위는 **_mkgmtime32** 23시 59분: 59 2038 년 1 월 18 일, UTC는 UTC 1970 년 1 월 1 일 자정에서 함수입니다. 범위의 **_mkgmtime64** UTC 23시 59분: 59를 3000 년 12 월 31 일에 1970 년 1 월 1 일 자정, utc에서입니다. 범위를 벗어난 날짜는-1의 반환 값에 발생합니다. 범위의 **_mkgmtime** 여부에 따라 달라 집니다 **_USE_32BIT_TIME_T** 정의 됩니다. 범위는의 (기본값) 정의 되지 않은 경우 **_mkgmtime64**, 그렇지 않으면 32 비트 범위 제한의 범위는 **_mkgmtime32**합니다.

**gmtime** 및 **localtime** 변환에 대해 단일 정적으로 할당 된 버퍼를 사용 합니다. 이 버퍼를 제공 하는 경우 **mkgmtime**, 이전 내용이 소멸 됩니다.

## <a name="example"></a>예제

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

### <a name="sample-output"></a>샘플 출력

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

다음 예제에서는 계산된 요일과 날짜 값을 사용하여 불완전한 구조체를 채우는 방법을 보여 줍니다.

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

### <a name="output"></a>출력

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>참고자료

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
