---
title: _ftime, _ftime32, _ftime64 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ftime64
- _ftime
- _ftime32
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
- _ftime32
- _ftime
- _ftime64
- ftime64
- ftime
- ftime32
dev_langs:
- C++
helpviewer_keywords:
- ftime64 function
- _ftime64 function
- current time
- _ftime function
- ftime function
- _ftime32 function
- ftime32 function
- time, getting current
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8942dbaddcc1f4ab1ec5d571d08d95d8669d302d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107057"
---
# <a name="ftime-ftime32-ftime64"></a>_ftime, _ftime32, _ftime64

현재 시간을 가져옵니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_ftime_s, _ftime32_s, _ftime64_s](ftime-s-ftime32-s-ftime64-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void _ftime( struct _timeb *timeptr );
void _ftime32( struct __timeb32 *timeptr );
void _ftime64( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>매개 변수

*timeptr*<br/>
에 대 한 포인터를 **_timeb**를 **__timeb32**, 또는 **__timeb64** 구조입니다.

## <a name="remarks"></a>설명

합니다 **_ftime** 함수는 현재 현지 시간을 가져옵니다 가리키는 구조체에 저장 합니다 *timeptr*합니다. 합니다 **_timeb**를 **__timeb32**, 및 **__timeb64** 구조에 정의 된 \<sys\\timeb.h >. 구조체에는 다음 표에 나와 있는 4개 필드가 포함됩니다.

|필드|설명|
|-|-|
|**dstflag**|현지 시간대에 현재 일광 절약 시간이 적용된 경우 0이 아닌 값. 일광 절약 시간을 결정하는 방법에 대한 자세한 내용은 [_tzset](tzset.md)를 참조하세요.|
|**millitm**|1초 미만의 시간(밀리초)입니다.|
|**time**|1970년 1월 1일 자정(00:00:00)(UTC(협정 세계시)) 이후의 시간(초)입니다.|
|**timezone**|서쪽으로 이동할 경우 UTC와 현지 시간 사이의 차이(분)입니다. 변수의 **표준 시간대** 전역 변수의 값에서 설정 됩니다 **_timezone** (참조 **_tzset**).|

합니다 **_ftime64** 함수를 사용 하는 **__timeb64** 구조체, 파일 생성 날짜를 23시 59분: 59 까지의 3000 년 12 월 31 일, UTC; 표현할 수 있습니다. 반면 **_ftime32**만 23시 59분: 59 까지의 2038 년 1 월 18 일 UTC 날짜를 나타냅니다. 1970년 1월 1일 자정은 이러한 모든 함수에 대한 날짜 범위의 하한입니다.

합니다 **_ftime** 함수는 동일 **_ftime64**, 및 **_timeb** 경우가 아니면 64 비트 시간을 포함 합니다. **_USE_32BIT_TIME_T** 에 정의 된 이 경우 이전 동작이 적용 됩니다. **_ftime** 32 비트 시간을 사용 하 고 **_timeb** 는 32 비트 시간을 포함 합니다.

**_ftime** 해당 매개 변수 유효성을 검사 합니다. 로 null 포인터를 전달 하는 경우 *timeptr*에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 하는 함수 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 함수를 설정 하는 경우는 계속 실행 하도록 허용 합니다 **errno** 하 **EINVAL**합니다.

## <a name="requirements"></a>요구 사항

|기능|필수 헤더|
|--------------|---------------------|
|**_ftime**|\<sys/types.h> 및 \<sys/timeb.h>|
|**_ftime32**|\<sys/types.h> 및 \<sys/timeb.h>|
|**_ftime64**|\<sys/types.h> 및 \<sys/timeb.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_ftime.c
// compile with: /W3
// This program uses _ftime to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime( &timebuffer ); // C4996
   // Note: _ftime is deprecated; consider using _ftime_s instead

   time1 = timebuffer.time;
   millitm1 = timebuffer.millitm;
   timezone1 = timebuffer.timezone;
   dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>참고자료

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
