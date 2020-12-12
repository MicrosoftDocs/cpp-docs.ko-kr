---
description: '자세한 정보: 클록'
title: clock
ms.date: 11/04/2016
api_name:
- clock
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 7a766a34518d7658768f3ea390eb4d87076b1d01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260750"
---
# <a name="clock"></a>clock

호출 프로세스에서 사용하는 벽시계 시간을 계산합니다.

## <a name="syntax"></a>구문

```C
clock_t clock( void );
```

## <a name="return-value"></a>Return Value

프로세스 시작 시 CRT 초기화 이후 경과 된 시간으로, 초당 **CLOCKS_PER_SEC** 단위로 측정 됩니다. 경과 된 시간을 사용할 수 없거나 **clock_t** 형식으로 기록할 수 있는 최대 양의 시간을 초과 하는 경우 함수는 값을 반환 `(clock_t)(-1)` 합니다.

## <a name="remarks"></a>설명

**Clock** 함수는 프로세스를 시작 하는 동안 CRT 초기화 이후 경과 된 벽 시계 시간을 알려 줍니다. 이 함수는 ISO C를 엄격하게 준수하지는 않으며, 순 CPU 시간을 반환 값으로 지정합니다. CPU 시간을 가져오려면 Win32 [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) 함수를 사용합니다. 경과 된 시간 (초)을 확인 하려면 **clock** 함수에서 반환 된 값을 매크로 **CLOCKS_PER_SEC** 로 나눕니다.

시간이 충분 하면 **clock** 에서 반환 하는 값이 **clock_t** 의 최대 양수 값을 초과할 수 있습니다. 프로세스가 더 이상 실행 되 면  `(clock_t)(-1)` C99 표준 (7.23.2.1) 및 iso C11 표준 (7.27.2.1)에 지정 된 대로 clock에서 반환 된 값은 항상입니다. Microsoft는 **clock_t** **`long`** 를 부호 있는 32 비트 정수로 구현 하 고 **CLOCKS_PER_SEC** 매크로는 1000로 정의 됩니다. 최대 **클록** 함수 반환 값인 2147483.647 초 또는 약 24.8 일을 제공 합니다. 이 시간 보다 오래 실행 된 프로세스에서 **clock** 이 반환 하는 값을 사용 하지 마십시오. 64 비트 [시간](time-time32-time64.md) 함수 또는 Windows [queryperformancecounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) 함수를 사용 하 여 많은 연도의 프로세스 경과 시간을 기록할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**클럭을**|\<time.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of clock cycles.
void do_sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}

const long num_loops = 600000000L;

int main( void )
{
   long    i = num_loops;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   start = clock();
   while( i-- )
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "Time to do %ld empty loops is ", num_loops );
   printf( "%2.3f seconds\n", duration );
}
```

```Output
Delay for three seconds
Done!
Time to do 600000000 empty loops is 1.354 seconds
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[difftime, _difftime32, _difftime64](difftime-difftime32-difftime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
