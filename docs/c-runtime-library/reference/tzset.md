---
description: '다음에 대 한 자세한 정보: _tzset'
title: _tzset
ms.date: 4/2/2020
api_name:
- _tzset
- _o__tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: 3841acf0a0fa13b23a8c41dcf955feec76bc82d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304534"
---
# <a name="_tzset"></a>_tzset

시간 환경 변수를 설정합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void _tzset( void );
```

## <a name="remarks"></a>설명

**_Tzset** 함수는 **TZ** 환경 변수의 현재 설정을 사용 하 여 세 개의 전역 변수 **_daylight**, **_timezone** 및 **_tzname** 에 값을 할당 합니다. 이러한 변수는 [_ftime](ftime-ftime32-ftime64.md) 및 [LOCALTIME](localtime-localtime32-localtime64.md) 함수에서 utc (협정 세계시)를 현지 시간으로 수정 하는 데 사용 되 고 [시간](time-time32-time64.md) 함수는 시스템 시간에서 utc를 계산 하는 데 사용 됩니다. 다음 구문을 사용 하 여 **TZ** 환경 변수를 설정 합니다.

> **set TZ =**_tzn_ \[ **+**&#124;**-** ]*hh* \[ **:**_mm_ \[ **:**_ss_]] [*dzn*]

 *tzn* \
 3자의 표준 시간대 이름(예: PST)입니다. 현지 시간에서 UTC로의 올바른 오프셋을 지정해야 합니다.

 *hh* \
 UTC와 현지 시간 사이의 차이(시간)입니다. 양수 값에 선택적인 (+) 부호입니다.

 *1* \
 분. *Hh* 에서 콜론 (**:**)으로 구분 합니다.

 *ss* \
 초. *Mm* 에서 콜론 (**:**)으로 구분 합니다.

 *dzn* \
 3자의 일광 절약 시간 표준 시간대(예: PDT)입니다. 표준 시간대에 일광 절약 시간이 적용 되지 않는 경우에는 *dzn* 에 대 한 값 없이 **TZ** 를 설정 합니다. C 런타임 라이브러리에서는 DST(일광 절약 시간) 계산 구현을 위한 미국의 규칙이 사용된다고 가정합니다.

> [!NOTE]
> 계산할 때는 시간 차이의 부호에 주의해야 합니다. 시간 차이는 현지 시간에서 UTC로의 오프셋(역방향 아님)이므로 부호가 직관적으로 예상하는 것과 반대일 수 있습니다. UTC보다 빠른 표준 시간대의 경우 시간 차이가 음수이고, UTC보다 늦은 표준 시간대의 경우 차이가 양수입니다.

예를 들어 독일의 현재 표준 시간대에 해당 하는 **TZ** 환경 변수를 설정 하려면 명령줄에 다음을 입력 합니다.

> **설정 TZ = GST-1GDT**

이 명령은 GST를 사용하여 독일 표준 시간을 나타내고, UTC는 독일보다 한 시간 뒤, 즉 독일은 UTC보다 한 시간 앞이라고 가정하며, 독일은 일광 절약 시간을 준수한다고 가정합니다.

**TZ** 값이 설정 되지 않은 경우 **_tzset** 는 운영 체제에서 지정한 표준 시간대 정보를 사용 하려고 시도 합니다. Windows 운영 체제에서 이 정보는 제어판의 날짜/시간 애플리케이션에 지정되어 있습니다. **_Tzset** 이 정보를 얻을 수 없는 경우 기본적으로 태평양 표준 시간대를 의미 하는 PST8PDT를 사용 합니다.

**TZ** 환경 변수 값에 따라 **_tzset** 를 호출할 때 **_daylight**, **_timezone** 및 **_tzname** 전역 변수에 다음 값이 할당 됩니다.

|전역 변수|설명|기본값|
|---------------------|-----------------|-------------------|
|**_daylight**|**TZ** 설정에서 일광 절약 시간 표준 시간대를 지정 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.|1|
|**_timezone**|현지 시간과 UTC 사이의 차이(초)입니다.|28800(28800초 = 8시간)|
|**_tzname**[0]|**TZ** 환경 변수에서 표준 시간대 이름의 문자열 값입니다. **TZ** 가 설정 되지 않은 경우 비어 있습니다.|PST|
|**_tzname**[1]|일광 절약 시간 표준 시간대의 문자열 값입니다. **TZ** 환경 변수에서 일광 절약 시간 표준 시간대가 생략 된 경우 비어 있습니다.|PDT|

위의 표에 나와 있는 **_daylight** 및 **_tzname** 배열의 기본값은 "PST8PDT"에 해당 합니다. DST 영역을 **TZ** 환경 변수에서 생략 하는 경우 **_daylight** 값은 0이 고 [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)및 [localtime](localtime-localtime32-localtime64.md) 함수는 dst 플래그에 대해 0을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_tzset**|\<time.h>|

**_Tzset** 함수는 Microsoft 전용입니다. 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_tzset.cpp
// This program uses _tzset to set the global variables
// named _daylight, _timezone, and _tzname. Since TZ is
// not being explicitly set, it uses the system time.

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    _tzset();
    int daylight;
    _get_daylight( &daylight );
    printf( "_daylight = %d\n", daylight );
    long timezone;
    _get_timezone( &timezone );
    printf( "_timezone = %ld\n", timezone );
    size_t s;
    char tzname[100];
    _get_tzname( &s, tzname, sizeof(tzname), 0 );
    printf( "_tzname[0] = %s\n", tzname );
    exit( 0 );
}
```

```Output
_daylight = 1
_timezone = 28800
_tzname[0] = Pacific Standard Time
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
