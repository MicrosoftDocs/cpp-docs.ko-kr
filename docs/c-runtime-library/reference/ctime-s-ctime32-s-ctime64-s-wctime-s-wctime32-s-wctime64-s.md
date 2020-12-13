---
description: '자세한 정보: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s'
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 4/2/2020
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
- _o__ctime32_s
- _o__ctime64_s
- _o__wctime32_s
- _o__wctime64_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
ms.openlocfilehash: 8a0f7b281bab32de5c6b5d7f2cf83fb5e1ed811f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339620"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

시간 값을 문자열로 변환하고 현지 표준 시간대 설정에 맞게 조정합니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [ctime, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
26자를 포함할 만큼 충분히 커야 합니다. 문자열 결과에 대 한 포인터 이거나, 다음과 같은 경우 **NULL** 입니다.

- *Sourcetime* 은 1970 년 1 월 1 일 자정 (UTC) 이전의 날짜를 나타냅니다.

- **_Ctime32_s** 또는 **_wctime32_s** 를 사용 하 고 *Sourcetime* 은 2038 년 1 월 18 일 23:59:59 이후의 날짜를 나타냅니다.

- **_Ctime64_s** 또는 **_wctime64_s** 를 사용 하는 경우 *Sourcetime* 은 3000 년 12 월 31 일 23:59:59 이후의 날짜를 나타냅니다.

- **_Ctime_s** 또는 **_wctime_s** 를 사용 하는 경우 이러한 함수는 이전 함수에 대 한 래퍼입니다. 주의 섹션을 참조하십시오.

*이면 numberofelements 이벤트가*<br/>
버퍼의 크기입니다.

*sourceTime*<br/>
저장된 시간에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

성공할 경우 0입니다. 잘못된 매개 변수로 인해 실패할 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 실행하도록 허용된 경우 오류 코드가 반환됩니다. 오류 코드는 ERRNO.H에 정의됩니다. 이러한 오류의 목록을 보려면 [errno](../../c-runtime-library/errno-constants.md)를 참조하세요. 각 오류 조건에 대해 throw되는 실제 오류 코드가 다음 표에 나와 있습니다.

## <a name="error-conditions"></a>오류 조건

|*버퍼*|*이면 numberofelements 이벤트가*|*sourceTime*|반환 값|*버퍼* 의 값|
|--------------|------------------------|------------|------------|-----------------------|
|**NULL**|any|any|**EINVAL**|수정 안 됨|
|Not **NULL** (유효한 메모리를 가리킴)|0|any|**EINVAL**|수정 안 됨|
|**NULL** 이 아님|0< 크기 < 26|any|**EINVAL**|빈 문자열|
|**NULL** 이 아님|>= 26|NULL|**EINVAL**|빈 문자열|
|**NULL** 이 아님|>= 26|< 0|**EINVAL**|빈 문자열|

## <a name="remarks"></a>설명

**Ctime_s** 함수는 [time_t](../../c-runtime-library/standard-types.md) 구조체로 저장 된 시간 값을 문자열로 변환 합니다. 일반적으로 *sourcetime* 값은 자정 (00:00:00), 1 월 1 일, 1970, utc (협정 세계시) 이후 경과 된 시간 (초)을 반환 하는 [시간](time-time32-time64.md)에 대 한 호출에서 가져옵니다. 반환 값 문자열은 정확히 26자를 포함하며 그 형식은 다음과 같습니다.

`Wed Jan 02 02:03:55 1980\n\0`

24시간제가 사용됩니다. 모든 필드에는 상수 너비가 있습니다. 줄 바꿈 문자('\n') 및 null 문자('\0')는 문자열의 마지막 두 자리를 차지합니다.

또한 변환된 문자열은 현지 표준 시간대 설정에 따라 조정됩니다. 표준 시간대 환경 및 전역 변수를 정의 하는 방법에 대 한 자세한 내용은 [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)및 [localtime32_s](localtime-s-localtime32-s-localtime64-s.md) 함수를 참조 하 여 현지 시간과 [_tzset](tzset.md) 함수를 구성 하는 방법에 대 한 정보를 참조 하십시오.

**_wctime32_s** 및 **_wctime64_s** 은 **_ctime32_s** 및 **_ctime64_s** 의 와이드 문자 버전입니다. 와이드 문자 문자열에 대 한 포인터 반환 그렇지 않으면 **_ctime64_s**, **_wctime32_s** 및 **_wctime64_s** **_ctime32_s** 와 동일 하 게 작동 합니다.

**ctime_s** 은 **_ctime64_s** 으로 계산 되는 인라인 함수 이며 **time_t** **__time64_t** 와 동일 합니다. 컴파일러가 **time_t** 이전 32 비트 **time_t** 으로 해석 해야 하는 경우 **_USE_32BIT_TIME_T** 를 정의할 수 있습니다. 이렇게 하면 **ctime_s** **_ctime32_s** 으로 평가 됩니다. 2038년 1월 18일 이후에는 애플리케이션에서 오류가 발생할 수 있으므로 이 방식은 사용하지 않는 것이 좋으며, 64비트 플랫폼에서는 이러한 방식이 허용되지 않습니다.

C++에서는 템플릿 오버로드를 통해 이러한 함수를 사용하는 것이 더욱 간단해집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이러한 함수의 디버그 라이브러리 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s**|\<time.h>|
|**_wctime_s**, **_wctime32_s**, **_wctime64_s**|\<time.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
