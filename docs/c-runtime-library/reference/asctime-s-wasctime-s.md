---
title: asctime_s, _wasctime_s | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
dev_langs:
- C++
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
caps.latest.revision: 29
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5a60bf3bae862be3b8fad98f4fa1346957b6590
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="asctimes-wasctimes"></a>asctime_s, _wasctime_s

변환 된 **tm** 시간 문자열에는 구조입니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 강화된 [asctime, _wasctime](asctime-wasctime.md)의 버전입니다.

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

*buffer*<br/>
문자 문자열 결과를 저장할 버퍼에 대 한 포인터입니다. 이 함수는 유효한 메모리 위치에 대 한 포인터 크기가 하 여 지정 된 것으로 가정 *numberOfElements*합니다.

*numberOfElements*<br/>
결과 저장 하는 데 사용 되는 버퍼의 크기입니다.

*tmSource*<br/>
시간/날짜 구조체입니다. 이 함수에 대 한 포인터를 올바른 것으로 가정 **구조체** **tm** 개체입니다.

## <a name="return-value"></a>반환 값

정상적으로 실행되는 경우 0입니다. 실패할 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속해서 실행하도록 허용된 경우 반환 값은 오류 코드입니다. 오류 코드는 ERRNO.H에서 정의됩니다. 자세한 내용은 [errno 상수](../../c-runtime-library/errno-constants.md)를 참조하세요. 각 오류 조건에 대해 반환되는 실제 오류 코드가 다음 표에 나와 있습니다.

### <a name="error-conditions"></a>오류 조건

|*buffer*|*numberOfElements*|*tmSource*|반환|값을 *버퍼*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|임의의 값|임의의 값|**EINVAL**|수정 안 됨|
|하지 **NULL** (올바른 메모리를 가리킴)|0|임의의 값|**EINVAL**|수정 안 됨|
|하지 **NULL**|0< 크기 < 26|임의의 값|**EINVAL**|빈 문자열|
|하지 **NULL**|>= 26|**NULL**|**EINVAL**|빈 문자열|
|하지 **NULL**|>= 26|시간 구성 요소에 대한 잘못된 시간 구조체 또는 범위를 벗어난 값|**EINVAL**|빈 문자열|

> [!NOTE]
> 오류 조건을 **wasctime_s** 비슷합니다 **asctime_s** 예외로 크기 제한을 단어 단위로 측정 됩니다.

## <a name="remarks"></a>설명

**asctime** 함수는 문자열에 구조로 저장 시간으로 변환 합니다. *tmSource* 값에 대 한 호출에서 가져온 일반적으로 **gmtime** 또는 **localtime**합니다. 두 함수 모두 채우는 데 사용 될 수는 **tm** 시간에 정의 된 구조체입니다. 8.

|timeptr 멤버|값|
|--------------------|-----------|
|**tm_hour**|자정 (0-23)|
|**tm_isdst**|일광 절약 시간이 적용되면 양수, 일광 절약 시간이 적용되지 않으면 0, 일광 절약 시간의 상태를 알 수 없으면 음수입니다. C 런타임 라이브러리에서는 DST(일광 절약 시간) 계산 구현을 위한 미국의 규칙이 사용된다고 가정합니다.|
|**tm_mday**|월 (1-31)의 날짜|
|**tm_min**|분 후에 시간 (0-59)|
|**tm_mon**|월 (0-11; 1 월 = 0)|
|**tm_sec**|초 후 분 (0-59)|
|**tm_wday**|요일 (0-6; 일요일 = 0)|
|**tm_yday**|(0-365; 연간 일자 1 월 1 일 = 0)|
|**tm_year**|연도(현재 연도 빼기 1900)|

또한 변환된 문자열은 현지 표준 시간대 설정에 따라 조정됩니다. 현지 시간 구성에 대한 정보는 [time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) 및 [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md) 함수를 참조하고 표준 시간대 환경 및 전역 변수 정의에 대한 정보는 [_tzset](tzset.md) 함수를 참조하세요.

생성 되는 문자열 결과 **asctime_s** 정확 하 게 26 개 문자를 포함 하 고 양식은 `Wed Jan 02 02:03:55 1980\n\0`합니다. 24시간제가 사용됩니다. 모든 필드에는 상수 너비가 있습니다. 줄 바꿈 문자 및 null 문자는 문자열의 마지막 두 자리를 차지합니다. 두 번째 매개 변수로서 전달된 값은 이 크기 이상이어야 합니다. 오류 코드를 보려면 이하인 경우 **EINVAL**, 반환 됩니다.

**_wasctime_s** 의 와이드 문자 버전이 **asctime_s**합니다. **_wasctime_s** 및 **asctime_s** 동일 하 게 작동 합니다.

### <a name="generic-text-routine-mapping"></a>제네릭 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

C++에서는 템플릿 오버로드를 통해 이러한 함수를 사용하는 것이 더욱 간단해집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> 또는 \<wchar.h>|

## <a name="security"></a>보안

버퍼 포인터 없으면 **NULL** 및 포인터가 유효한 버퍼를 가리키지 않습니다, 함수는 위치에 관계 없이 덮어쓰게 됩니다. 이 경우 액세스 위반이 발생할 수도 있습니다.

전달된 크기 인수가 버퍼의 실제 크기보다 크면 [버퍼 오버런](http://msdn.microsoft.com/library/windows/desktop/ms717795)이 발생할 수 있습니다.

## <a name="example"></a>예제

이 프로그램은 정수 (long)에 시스템 시간을 배치 **aclock**, 구조로 변환 **newtime** 출력을 사용 하는 문자열 형식에 대 한 변환 하 고는 **asctime_s**함수입니다.

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

## <a name="see-also"></a>참고자료

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
