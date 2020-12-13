---
description: '다음에 대 한 자세한 정보: _get_tzname'
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: b98a068d6f2d2643df43078c5a274fd761ac8e95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338951"
---
# <a name="_get_tzname"></a>_get_tzname

표준 시간대 이름 또는 일광 표준 시간대 이름(DST)의 문자열 표현을 검색합니다.

## <a name="syntax"></a>구문

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>매개 변수

*pReturnValue*<br/>
Null 종결자를 포함 하는 *Timezonename* 의 문자열 길이입니다.

*timeZoneName*<br/>
*인덱스* 에 따라 표준 시간대 이름 또는 일광 표준 시간대 이름 (DST) 표현에 대 한 문자열의 주소입니다.

*sizeInBytes*<br/>
*Timezonename* 문자열의 크기 (바이트)입니다.

*index*<br/>
검색할 두 표준 시간대 이름 중 하나의 인덱스입니다.

|*index*|*Timezonename* 의 내용|*Timezonename* 기본값|
|-|-|-|
|0|표준 시간대 이름|"PST"|
|1|일광 표준 시간대 이름|"PDT"|
|> 1 또는 < 0|**errno** 를 **EINVAL** 로 설정|수정 안 됨|

런타임에 값을 명시적으로 변경하는 경우가 아니면 기본값은 각각 "PST" 및 "PDT"입니다.

## <a name="return-value"></a>반환 값

성공 하면 0이 고, 그렇지 않으면 **errno** 형식 값입니다.

*Timezonename* 이 **NULL** 이거나 *sizeinbytes* 가 0 이거나 0 보다 작은 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

### <a name="error-conditions"></a>오류 조건

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|반환 값|*Timezonename* 의 내용|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|TZ 이름의 크기|**NULL**|0|0 또는 1|0|수정 안 됨|
|TZ 이름의 크기|any|> 0|0 또는 1|0|TZ 이름|
|수정 안 됨|**NULL**|> 0|any|**EINVAL**|수정 안 됨|
|수정 안 됨|any|0|any|**EINVAL**|수정 안 됨|
|수정 안 됨|any|> 0|> 1|**EINVAL**|수정 안 됨|

## <a name="remarks"></a>설명

**_Get_tzname** 함수는 현재 표준 시간대 이름 또는 일광 표준 시간대 이름 (DST)의 문자열 표현을 *pReturnValue* 의 문자열 크기와 함께 인덱스 값에 따라 *timezonename* 의 주소로 검색 합니다. *Timezonename* 이 **NULL** 이 고 *sizeinbytes* 가 0 인 경우에는 지정 된 표준 시간대를 보유 하는 데 필요한 문자열의 크기와 *pReturnValue* 에서 종료 NULL을 바이트 단위로 반환 합니다. 인덱스 값은 표준 시간대의 경우 0 또는 일광 표준 시간대의 경우 1 이어야 합니다. *인덱스* 의 다른 값은 결과를 결정 하지 않습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="example"></a>예제

이 샘플은 **_get_tzname** 를 호출 하 여 현재 일광 표준 시간대 이름을 표시 하 고, 해당 크기의 버퍼를 할당 하 고, **_get_tzname** 를 다시 호출 하 여 버퍼에 이름을 로드 하 고 콘솔에 출력 합니다.

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>출력

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
