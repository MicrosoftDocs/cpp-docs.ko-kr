---
description: _Daylight, _dstbias, _timezone 및 _tzname에 대해 자세히 알아보세요.
title: _daylight, _dstbias, _timezone 및 _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
ms.openlocfilehash: aaa1d76276e4b4117d5f07695875481215c4122e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258785"
---
# <a name="_daylight-_dstbias-_timezone-and-_tzname"></a>_daylight, _dstbias, _timezone 및 _tzname

`_daylight`, `_dstbias`, `_timezone` 및 `_tzname`은 일부 시간 및 날짜 루틴에서 현지 시간을 조정하는 데 사용됩니다. 이러한 전역 변수는 전역 변수 대신 사용되어야 할 보안 기능이 보다 강화된 버전에 대해서는 더 이상 사용되지 않습니다.

|전역 변수|해당 기능|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

이 전역 변수는 Time.h에서 다음과 같이 선언됩니다.

## <a name="syntax"></a>구문

```
extern int _daylight;
extern int _dstbias;
extern long _timezone;
extern char *_tzname[2];
```

## <a name="remarks"></a>설명

`_ftime`, `localtime` 또는 `_tzset` 호출 시 `_daylight`, `_dstbias`, `_timezone` 및 `_tzname` 값은 `TZ` 환경 변수 값에 따라 결정됩니다. `TZ` 값을 명시적으로 설정하지 않으면 `_tzname[0]` 및 `_tzname[1]`에는 각각 기본 설정인 "PST" 및 "PDT"가 포함됩니다.  시간 조작 함수([_tzset](../c-runtime-library/reference/tzset.md), [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 및 [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md))는 운영 체제에 각 변수의 기본값을 쿼리하여 `_daylight`, `_dstbias` 및 `_timezone` 값을 설정하려고 합니다. 시간대 전역 변수 값은 다음 표에 나와 있습니다.

|변수|값|
|--------------|-----------|
|`_daylight`|DST(일광 절약 시간) 영역이 `TZ`에서 지정되거나 운영 체제에 따라 결정될 경우 0이 아닌 값이고, 그렇지 않으면 0입니다. 기본값은 1입니다.|
|`_dstbias`|일광 절약 시간의 오프셋입니다.|
|`_timezone`|협정 세계시와 현지 시간의 차이(초)입니다. 기본값은 28,800입니다.|
|`_tzname[0]`|`TZ` 환경 변수에서 파생된 시간대 이름입니다. 기본값은 "PST"입니다.|
|`_tzname[1]`|`TZ` 환경 변수에서 파생된 DST 영역 이름입니다. 기본값은 "PDT"(태평양 일광 절약 시간)입니다.|

## <a name="see-also"></a>참고 항목

[전역 변수](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
