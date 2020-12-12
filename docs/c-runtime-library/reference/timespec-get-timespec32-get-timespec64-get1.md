---
description: Timespec_get, _timespec32_get, _timespec64_get에 대해 자세히 알아보세요.
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 4/2/2020
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
- _o__timespec32_get
- _o__timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: c6fc7c84d21bdeb8394602565dfe83fe22b59cb2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299529"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get, _timespec32_get, _timespec64_get

첫 번째 인수를 통해 지정된 간격을 지정된 기본 시간을 기준으로 현재 일정 시간으로 설정합니다.

## <a name="syntax"></a>구문

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>매개 변수

*time_spec*<br/>
epoch 시작 이후 지난 시간(초 및 나노초)으로 설정된 구조체 포인터입니다.

*base*<br/>
기본 시간을 지정하는 0이 아닌 구현 특정 값입니다.

## <a name="return-value"></a>반환 값

성공 하면 *base* 의 값이 고, 그렇지 않으면 0을 반환 합니다.

## <a name="remarks"></a>설명

**Timespec_get** 함수는 *time_spec* 인수에 의해 가리키는 구조체의 현재 시간을 설정 합니다. 이 구조체의 모든 버전에는 **tv_sec** 및 **tv_nsec** 라는 두 개의 멤버가 있습니다. **Tv_sec** 값은 정수로 지정 된 epoch 시작 이후 시스템 클록의 해상도로 반올림 된 시간 (초)으로 설정 되 고 정수 나노초 수로 **tv_nsec** *됩니다.*

**Microsoft 전용**

이러한 함수는 **TIME_UTC** *기본* 값 으로만 지원 합니다. 이는 *time_spec* 값을 epoch 시작, 자정, 1 월 1 일, 1970 Utc (협정 세계시) 이후의 시간 (초) 및 나노초 수로 설정 합니다. **`struct`** **_Timespec32** 에서 **tv_sec** 는 **__time32_t** 값입니다. **`struct`** **_Timespec64** 에서 **tv_sec** 는 **__time64_t** 값입니다. **`struct`** **Timespec** 에서 **tv_sec** 은 전처리기 매크로 _USE_32BIT_TIME_T 정의 되었는지 여부에 따라 32 비트 또는 64 비트 길이의 **time_t** 형식입니다. **Timespec_get** 함수는 _USE_32BIT_TIME_T 정의 된 경우 **_timespec32_get** 를 호출 하는 인라인 함수입니다. 그렇지 않으면 **_timespec64_get** 를 호출 합니다.

**Microsoft 전용 종료**

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<time.h> , c + +: \<ctime> 또는 \<time.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
