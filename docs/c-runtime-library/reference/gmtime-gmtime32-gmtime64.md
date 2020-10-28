---
title: gmtime, _gmtime32, _gmtime64
description: '`gmtime` `_gmtime32` `_gmtime64` 값을 구조체로 변환 하는, 및에 대 한 API 참조입니다 `time_t` `tm` .'
ms.date: 10/27/2020
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
ms.openlocfilehash: bb8bee6b752f64d85dfb0f8c9e5ba7acf204a76f
ms.sourcegitcommit: 9c801a43ee0d4d84956b03fd387716c818705e0d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907547"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>`gmtime`, `_gmtime32`, `_gmtime64`

`time_t`시간 값을 `tm` 구조체로 변환 합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [ `gmtime_s` , `_gmtime32_s` ,를 `_gmtime64_s` ](gmtime-s-gmtime32-s-gmtime64-s.md)참조 하세요.

## <a name="syntax"></a>구문

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>매개 변수

*`sourceTime`*\
저장된 시간에 대한 포인터입니다. 시간은 1970년 1월 1일 자정(00:00:00)(UTC(협정 세계시)) 이후 경과한 시간(초)으로 표현됩니다.

## <a name="return-value"></a>반환 값

형식의 구조에 대 한 포인터입니다 [`tm`](../../c-runtime-library/standard-types.md) . 반환 된 구조체의 필드에는 현지 시간이 아닌 UTC로 계산 된 인수의 값이 포함 *`sourceTime`* 됩니다. 각 구조체 필드는 다음과 같이 `int` 형식입니다.

|필드|Description|
|-|-|
|`tm_sec`|분 이후의 초 (0-59)입니다.|
|`tm_min`|시간 이후 분 (0-59)|
|`tm_hour`|자정 이후의 시간 (0-23)입니다.|
|`tm_mday`|월의 일자 (1-31)|
|`tm_mon`|월 (0-11; 1 월 = 0).|
|`tm_year`|연도(현재 연도 - 1900).|
|`tm_wday`|요일 (0-6; 일요일 = 0).|
|`tm_yday`|연간 일자 (0-365; 1 월 1 일 = 0).|
|`tm_isdst`|**Gmtime** 의 경우 항상 0입니다.|

,, 및의 32 비트 및 64 비트 버전은 **`gmtime`** 모두 [`mktime`](mktime-mktime32-mktime64.md) [`mkgmtime`](mkgmtime-mkgmtime32-mkgmtime64.md) [`localtime`](localtime-localtime32-localtime64.md) `tm` 변환에 대해 스레드 당 하나의 공통 구조를 사용 합니다. 이러한 함수 중 하나를 호출할 때마다 이전 호출의 결과가 삭제됩니다. 가 *`sourceTime`* 1970 년 1 월 1 일 자정 이전의 날짜를 나타내면는를 **`gmtime`** 반환 `NULL` 합니다. 오류가 반환 되지 않습니다.

구조를 사용 하는 **_gmtime64** 에 따라 `__time64_t` 날짜를 23:59:59 년 12 월 31 일 3000, UTC까지 표현할 수 있습니다. **`_gmtime32`** 날짜를 23:59:59 년 1 월 18 일 2038 년 1 월 18 일 까지만 표시 합니다. 1970년 1월 1일 자정은 두 함수 모두에 대한 날짜 범위의 하한입니다.

**`gmtime`** 는로 계산 되는 인라인 함수 **`_gmtime64`** 이며 `time_t` `__time64_t` 는가 정의 되지 않은 경우와 동일 `_USE_32BIT_TIME_T` 합니다. 컴파일러가 이전 32 비트로 해석 되도록 강제로 지정 해야 하는 경우를 `time_t` `time_t` 정의할 수 있지만 이렇게 하면 `_USE_32BIT_TIME_T` 에서로 **`gmtime`** **`_gmtime32`** `time_t` 정의 되 고로 정의 됩니다 `__time32_t` . 64 비트 플랫폼에서는 허용 되지 않기 때문에이 작업을 수행 하지 않는 것이 좋습니다. 어떤 경우이 든 응용 프로그램은 2038 년 1 월 18 일 후에 실패할 수 있습니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *`sourceTime`* 가 null 포인터 이거나 *`sourceTime`* 값이 음수 이면 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속해서 실행하도록 허용된 경우 이 함수는 `NULL`을 반환하며 `errno`를 `EINVAL`로 설정합니다.

## <a name="remarks"></a>설명

**`_gmtime32`** 함수는 값을 분할 *`sourceTime`* 하 여에 정의 된 형식의 정적으로 할당 된 구조체에 저장 `tm` `TIME.H` 합니다. 값은 *`sourceTime`* 일반적으로 함수 호출에서 가져옵니다 [`time`](time-time32-time64.md) .

> [!NOTE]
> 대부분의 경우 대상 환경에서는 일광 절약 시간이 적용되는지 확인하려고 합니다. C 런타임 라이브러리에서는 DST(일광 절약 시간) 계산 구현을 위한 미국 규칙이 사용된다고 가정합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 C 헤더|필수 C++ 헤더|
|-------------|---------------------|-|
|**`gmtime`** , **`_gmtime32`** , **`_gmtime64`**|`<time.h>`| `<ctime>` 또는 `<time.h>`|

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

int main(void)
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

[시간 관리](../../c-runtime-library/time-management.md)\
[`asctime`, `_wasctime`](asctime-wasctime.md)\
[`ctime`, `_ctime32`, `_ctime64`, `_wctime`, `_wctime32`, `_wctime64`](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)\
[`_ftime`, `_ftime32`, `_ftime64`](ftime-ftime32-ftime64.md)\
[`gmtime_s`, `_gmtime32_s`, `_gmtime64_s`](gmtime-s-gmtime32-s-gmtime64-s.md)\
[`localtime`, `_localtime32`, `_localtime64`](localtime-localtime32-localtime64.md)\
[`_mkgmtime`, `_mkgmtime32`, `_mkgmtime64`](mkgmtime-mkgmtime32-mkgmtime64.md)\
[`mktime`, `_mktime32`, `_mktime64`](mktime-mktime32-mktime64.md)\
[`time`, `_time32`, `_time64`](time-time32-time64.md)
