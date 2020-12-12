---
description: '자세한 정보: difftime, _difftime32, _difftime64'
title: difftime, _difftime32, _difftime64
ms.date: 4/2/2020
api_name:
- _difftime32
- difftime
- _difftime64
- _o__difftime32
- _o__difftime64
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
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
ms.openlocfilehash: 3f2c4f713f5e4dd667bd4e0a557170e9d23e6700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327022"
---
# <a name="difftime-_difftime32-_difftime64"></a>difftime, _difftime32, _difftime64

두 시간의 차이를 찾습니다.

## <a name="syntax"></a>구문

```C
double difftime( time_t timeEnd, time_t timeStart );
double _difftime32( __time32_t timeEnd, __time32_t timeStart );
double _difftime64( __time64_t timeEnd, __time64_t timeStart );
```

### <a name="parameters"></a>매개 변수

*timeEnd*<br/>
종료 시간입니다.

*timeStart*<br/>
시작 시간입니다.

## <a name="return-value"></a>반환 값

**difftime** 은 *Timestart* 에서 *timestart* 까지 경과 된 시간 (초)을 반환 합니다. 반환되는 값은 배정밀도 부동 소수점 숫자입니다. 반환 값은 오류를 나타내는 0일 수 있습니다.

## <a name="remarks"></a>설명

**Difftime** 함수는 제공 된 두 시간 값 *Timestart* 와 *timestart* 사이의 차이를 계산 합니다.

제공 된 시간 값은 **time_t** 범위에 맞아야 합니다. **time_t** 는 64 비트 값입니다. 따라서 범위의 끝은 2038년 1월 18일 23:59:59(UTC)에서 3000년 12월 31일 23:59:59로 확장되었습니다. **Time_t** 의 하한값은 여전히 1970 년 1 월 1 일 자정입니다.

**difftime** 은 **_USE_32BIT_TIME_T** 정의 되었는지 여부에 따라 **_difftime32** 또는 **_difftime64** 로 계산 되는 인라인 함수입니다. _difftime32 및 _difftime64는 시간 형식의 특정 크기를 강제로 사용하도록 직접 사용될 수 있습니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. 매개 변수가 0 또는 음수인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 0을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**difftime**|\<time.h>|
|**_difftime32**|\<time.h>|
|**_difftime64**|\<time.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
// crt_difftime.c
// This program calculates the amount of time
// needed to do a floating-point multiply 100 million times.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <float.h>

double RangedRand( float range_min, float range_max)
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min);
}

int main( void )
{
   time_t   start, finish;
   long     loop;
   double   result, elapsed_time;
   double   arNums[3];

   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   arNums[0] = RangedRand(1, FLT_MAX);
   arNums[1] = RangedRand(1, FLT_MAX);
   arNums[2] = RangedRand(1, FLT_MAX);
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );

   printf( "Multiplying 2 numbers 100 million times...\n" );

   time( &start );
   for( loop = 0; loop < 100000000; loop++ )
      result = arNums[loop%3] * arNums[(loop+1)%3];
   time( &finish );

   elapsed_time = difftime( finish, start );
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );
}
```

```Output
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038
Multiplying 2 floating point numbers 100 million times...
Program takes      3 seconds.
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[시간 관리](../../c-runtime-library/time-management.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
