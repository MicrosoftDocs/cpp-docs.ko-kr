---
description: '자세히 알아보기: asctime_s, _wasctime_s'
title: asctime_s, _wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: d743aea81abdba2e1aa2b470f71081cb92e6fc64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211325"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

**Tm** 시간 구조를 문자열로 변환 합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 강화된 [asctime, _wasctime](asctime-wasctime.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
문자열 결과를 저장할 버퍼에 대 한 포인터입니다. 이 함수는 *Numberofelements* 에 의해 지정 된 크기의 유효한 메모리 위치에 대 한 포인터를 가정 합니다.

*이면 numberofelements 이벤트가*<br/>
결과를 저장 하는 데 사용 되는 버퍼의 크기입니다.

*tmSource*<br/>
시간/날짜 구조체입니다. 이 함수는 유효한 tm 개체에 대 한 포인터를 가정 **`struct`**  합니다.

## <a name="return-value"></a>반환 값

성공할 경우 0입니다. 실패할 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속해서 실행하도록 허용된 경우 반환 값은 오류 코드입니다. 오류 코드는 ERRNO.H에서 정의됩니다. 자세한 내용은 [errno 상수](../../c-runtime-library/errno-constants.md)를 참조하세요. 각 오류 조건에 대해 반환되는 실제 오류 코드가 다음 표에 나와 있습니다.

### <a name="error-conditions"></a>오류 조건

|*버퍼*|*이면 numberofelements 이벤트가*|*tmSource*|반환 값|*버퍼* 의 값|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|모두|모두|**EINVAL**|수정 안 됨|
|Not **NULL** (유효한 메모리를 가리킴)|0|모두|**EINVAL**|수정 안 됨|
|**NULL** 이 아님|0< 크기 < 26|모두|**EINVAL**|빈 문자열|
|**NULL** 이 아님|>= 26|**NULL**|**EINVAL**|빈 문자열|
|**NULL** 이 아님|>= 26|시간 구성 요소에 대한 잘못된 시간 구조체 또는 범위를 벗어난 값|**EINVAL**|빈 문자열|

> [!NOTE]
> **Wasctime_s** 에 대 한 오류 조건은 크기 제한을 단어로 측정 하는 예외를 제외 하 고 **asctime_s** 와 비슷합니다.

## <a name="remarks"></a>설명

**Asctime** 함수는 구조체로 저장 된 시간을 문자열로 변환 합니다. *Tmsource* 값은 일반적으로 **gmtime** 또는 **localtime** 에 대 한 호출에서 가져옵니다. 두 함수를 사용 하 여 타임에 정의 된 대로 **tm** 구조를 채울 수 있습니다.

|timeptr 멤버|값|
|--------------------|-----------|
|**tm_hour**|자정 이후의 시간 (0-23)|
|**tm_isdst**|일광 절약 시간이 적용되면 양수, 일광 절약 시간이 적용되지 않으면 0, 일광 절약 시간의 상태를 알 수 없으면 음수입니다. C 런타임 라이브러리에서는 DST(일광 절약 시간) 계산 구현을 위한 미국의 규칙이 사용된다고 가정합니다.|
|**tm_mday**|월간 일자 (1-31)|
|**tm_min**|시간 이후 분 (0-59)|
|**tm_mon**|월 (0-11; 1 월 = 0)|
|**tm_sec**|분 이후의 초 (0-59)|
|**tm_wday**|요일 (0-6; 일요일 = 0)|
|**tm_yday**|연간 일자 (0-365; 1 월 1 일 = 0)|
|**tm_year**|연도(현재 연도 빼기 1900)|

또한 변환된 문자열은 현지 표준 시간대 설정에 따라 조정됩니다. 현지 시간 구성에 대한 정보는 [time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) 및 [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md) 함수를 참조하고 표준 시간대 환경 및 전역 변수 정의에 대한 정보는 [_tzset](tzset.md) 함수를 참조하세요.

**Asctime_s** 에서 생성 되는 문자열 결과는 정확히 26 자를 포함 하며 형식은 `Wed Jan 02 02:03:55 1980\n\0` 입니다. 24시간제가 사용됩니다. 모든 필드에는 상수 너비가 있습니다. 줄 바꿈 문자 및 null 문자는 문자열의 마지막 두 자리를 차지합니다. 두 번째 매개 변수로서 전달된 값은 이 크기 이상이어야 합니다. 더 작은 경우 오류 코드 **EINVAL** 이 반환 됩니다.

**_wasctime_s** 은 **asctime_s** 의 와이드 문자 버전입니다. **_wasctime_s** 와 **asctime_s** 는 동일 하 게 동작 합니다.

이러한 함수의 디버그 라이브러리 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mapping"></a>제네릭 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

C++에서는 템플릿 오버로드를 통해 이러한 함수를 사용하는 것이 더욱 간단해집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> 또는 \<wchar.h>|

## <a name="security"></a>보안

버퍼 포인터가 **NULL** 이 아니고 포인터가 유효한 버퍼를 가리키지 않는 경우 함수는 위치에 있는 항목을 모두 덮어씁니다. 이 경우 액세스 위반이 발생할 수도 있습니다.

전달된 크기 인수가 버퍼의 실제 크기보다 크면 [버퍼 오버런](/windows/win32/SecBP/avoiding-buffer-overruns)이 발생할 수 있습니다.

## <a name="example"></a>예제

이 프로그램은 시스템 시간을 정수 (long) **aclock** 에 배치 하 고,이를 n e n t e n t e n t e n t e n t e n t a **time** 으로 변환한 다음, **asctime_s** 함수를 사용

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
