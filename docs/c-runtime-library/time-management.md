---
description: '자세히 알아보기: 시간 관리'
title: 시간 관리
ms.date: 11/04/2016
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: c8a5b65c66ab89506149c92bd32999be3503c700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326910"
---
# <a name="time-management"></a>시간 관리

다음 함수를 사용하여 현재 시간을 가져오고 필요에 따라 변환, 조정 및 저장할 수 있습니다. 현재 시간은 시스템 시간입니다.

**_ftime** 및 **localtime** 루틴은 **TZ** 환경 변수를 사용합니다. **TZ** 를 설정하지 않으면 런타임 라이브러리는 운영 체제에서 지정한 표준 시간대 정보를 사용하려고 합니다. 이 정보를 사용할 수 없는 경우 이러한 함수는 기본값 PST8PDT를 사용합니다. **TZ** 에 대한 자세한 내용은 [_tzset](../c-runtime-library/reference/tzset.md)를 참조하세요. [_daylight, timezone 및 _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)도 참조하세요.

### <a name="time-routines"></a>시간 루틴

|함수|기능|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|**struct tm** 형식의 시간을 문자열로 변환합니다. **_s** 접미사가 있는 버전의 함수가 더 안전합니다.|
|[클럭을](../c-runtime-library/reference/clock.md)|프로세스의 경과된 벽시계 시간을 반환합니다.|
|[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|**time_t**, **__time32_t** 또는 **__time64_t** 형식의 시간을 문자열로 변환합니다. **_s** 접미사가 있는 버전의 함수가 더 안전합니다.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|두 시간 사이의 차이를 컴퓨팅합니다.|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|현재 시스템 시간을 **struct _timeb** 또는 **struct __timeb64** 형식의 변수에 저장합니다. **_s** 접미사가 있는 버전의 함수가 더 안전합니다.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|열린 파일의 수정 시간을 설정합니다.|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|시간을 **time_t** 에서 **struct tm** 형식으로 변환하거나 **__time64_t** 에서 **struct tm** 형식으로 변환합니다. **_s** 접미사가 있는 버전의 함수가 더 안전합니다.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|로컬 수정 내용과 함께 시간을 **time_t** 에서 **struct tm** 형식으로 변환하거나 **__time64_t** 에서 **struct tm** 형식으로 변환합니다. **_s** 접미사가 있는 버전의 함수가 더 안전합니다.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|시간을 그리니치 표준시의 달력 값으로 변환합니다.|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|시간을 달력 값으로 변환합니다.|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s, _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|현재 시스템 날짜를 문자열로 반환합니다. **_s** 접미사가 있는 버전의 함수가 더 안전합니다.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|국가별 사용을 위해 날짜 및 시간 형식 문자열을 지정합니다.|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s, _wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|현재 시스템 시간을 문자열로 반환합니다. **_s** 접미사가 있는 버전의 함수가 더 안전합니다.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|현재 시스템 시간을 **time_t**, **__time32_t** 또는 **__time64_t** 형식으로 가져옵니다.|
|[_tzset](../c-runtime-library/reference/tzset.md)|**TZ** 환경 시간 변수에서 외부 시간 변수를 설정합니다.|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|현재 시간 또는 구조체에 저장된 시간 값을 사용하여 지정된 파일의 수정 시간을 설정합니다.|

> [!NOTE]
> Microsoft C/C++ 버전 7.0을 제외한 모든 버전의 Microsoft C/C++과 모든 버전의 Visual C++에서, 시간 함수는 1970년 1월 1일 자정 이후 경과된 초 시간으로 현재 시간을 반환합니다. Microsoft C/C++ 버전 7.0에서 **time** 은 현재 시간을 1899년 12월 31일 자정 이후 경과된 시간(초)으로 반환했습니다.

> [!NOTE]
> Visual Studio 2005 이전 버전의 Visual C++ 및 Microsoft C/c + +에서는 **time_t** **`long int`** (32 비트) 이기 때문에 년 1 월 19 일, 년 1 월 2038 19 일 3:14:07 이전 날짜에는 사용할 수 없습니다. 이제 **time_t** 는 기본적으로 **__time64_t** 와 동일하지만, **_USE_32BIT_TIME_T** 를 정의하면 **time_t** 가 **__time32_t** 로 변경되고 많은 시간 함수에서 32비트 **time_t** 를 사용하는 버전을 호출하도록 합니다. 자세한 내용은 [표준 형식](../c-runtime-library/standard-types.md) 및 개별 시간 함수 문서의 설명을 참조하세요.

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
