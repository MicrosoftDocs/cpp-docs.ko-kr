---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 4/2/2020
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
- _o__wctime32
- _o__wctime64
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: 6056ad8bac6561c0ce2902928364996b2be9ae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348242"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

시간 값을 문자열로 변환하고 현지 표준 시간대 설정에 맞게 조정합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>매개 변수

*소스 타임*<br/>
변환 할 저장된 시간에 대한 포인터입니다.

## <a name="return-value"></a>Return Value

문자열 결과에 대한 포인터입니다. 다음과 같은 경우 **NULL이** 반환됩니다.

- *sourceTime은* UTC인 1970년 1월 1일 자정 이전의 날짜를 나타냅니다.

- **_ctime32** 또는 **_wctime32** 사용하는 경우 *sourceTime은* UTC2038년 1월 18일 23:59:59 이후의 날짜를 나타냅니다.

- **_ctime64** 또는 **_wctime64** 사용하는 *경우sourceTime은* UTC 3000년 12월 31일 23:59:59 이후의 날짜를 나타냅니다.

**ctime은** **_ctime64** 평가하는 인라인 함수이며 **time_t** **__time64_t**같습니다. 컴파일러가 **time_t** 이전 32비트 **time_t**해석하도록 강제해야 하는 경우 **_USE_32BIT_TIME_T**. 이렇게 하면 **ctime이** **_ctime32**평가합니다. 2038년 1월 18일 이후에는 애플리케이션에서 오류가 발생할 수 있으므로 이 방식은 사용하지 않는 것이 좋으며, 64비트 플랫폼에서는 이러한 방식이 허용되지 않습니다.

## <a name="remarks"></a>설명

**ctime** 함수는 [time_t](../../c-runtime-library/standard-types.md) 값으로 저장된 시간 값을 문자 문자열로 변환합니다. *sourceTime* 값은 일반적으로 자정(00:00:00), 1970년 1월 1일, 조정된 유니버설 시간(UTC) 이후 경과된 초 수를 반환하는 시간 호출에서 가져옵니다. [time](time-time32-time64.md) 반환 값 문자열은 정확히 26자를 포함하며 그 형식은 다음과 같습니다.

```Output
Wed Jan 02 02:03:55 1980\n\0
```

24시간제가 사용됩니다. 모든 필드에는 상수 너비가 있습니다. 줄 바꿈 문자('\n') 및 null 문자('\0')는 문자열의 마지막 두 자리를 차지합니다.

또한 변환된 문자열은 현지 표준 시간대 설정에 따라 조정됩니다. 표준 시간대 환경 및 전역 변수 정의에 대한 자세한 내용은 현지 시간 및 [_tzset](tzset.md) 함수 구성에 대한 자세한 내용은 [시간,](time-time32-time64.md) [_ftime](ftime-ftime32-ftime64.md)및 [현지 시간](localtime-localtime32-localtime64.md) 함수를 참조하십시오.

**ctime** 에 대한 호출은 **gmtime** 및 **로컬타임** 함수에서 사용하는 정적으로 할당된 단일 버퍼를 수정합니다. 이러한 루틴 중 하나를 호출할 때마다 이전 호출의 결과가 삭제됩니다. **ctime은** **asctime** 함수와 정적 버퍼를 공유합니다. 따라서 **ctime에** 대한 호출은 **asctime,** **로컬 타임**또는 **gmtime에**대한 이전 호출의 결과를 파괴합니다.

**_wctime** **_wctime64** **ctime** 및 **_ctime64**와이드 문자 버전입니다. 와이드 문자 문자열에 대한 포인터를 반환합니다. 그렇지 않으면 **_ctime64**, **_wctime**및 **_wctime64** **ctime과**동일하게 작동합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *sourceTime이* null 포인터이거나 *sourceTime* 값이 음수인 경우 이러한 함수는 [매개 변수 유효성 검사에](../../c-runtime-library/parameter-validation.md)설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 실행을 계속할 수 있는 경우 함수는 **NULL을** 반환하고 **errno를** **EINVAL로**설정합니다.

기본적으로 이 함수의 전역 상태는 응용 프로그램에 대한 범위가 조정됩니다. 이를 변경하려면 [CRT의 전역 상태를](../global-state.md)참조하십시오.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**ctime**|**ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**ctime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> 또는 \<wchar.h>|
|**_wctime32**|\<time.h> 또는 \<wchar.h>|
|**_wctime64**|\<time.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
