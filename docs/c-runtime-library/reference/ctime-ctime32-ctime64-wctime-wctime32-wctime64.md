---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30caa77fee7e15f91ff7c3f089f18fd51a34aa0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404911"
---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

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

*sourceTime*<br/>
포인터 변환에 저장 된 시간입니다.

## <a name="return-value"></a>반환 값

문자열 결과에 대한 포인터입니다. **NULL** 경우 반환 됩니다.

- *sourceTime* 1970 년 1 월 1 일 자정, UTC 이전의 날짜를 나타냅니다.

- 사용 하는 경우 **_ctime32** 또는 **_wctime32** 및 *sourceTime* 23시 59분: 59 2038 년 1 월 18 일 UTC 이후 날짜를 나타냅니다.

- 사용 하는 경우 **_ctime64** 또는 **_wctime64** 및 *sourceTime* 23시 59분: 59를 3000 년 12 월 31 일 UTC 이후 날짜를 나타냅니다.

**ctime** 계산 되는 인라인 함수 인지 **_ctime64** 및 **time_t** 같습니다 **__time64_t**합니다. 컴파일러가 해석 하도록 하는 경우 **time_t** 이전 32 비트로 **time_t**를 정의할 수 있습니다 **_USE_32BIT_TIME_T**합니다. 이렇게 하면이로 인해 **ctime** 로 평가 되려면 **_ctime32**합니다. 2038년 1월 18일 이후에는 응용 프로그램에서 오류가 발생할 수 있으므로 이 방식은 사용하지 않는 것이 좋으며, 64비트 플랫폼에서는 이러한 방식이 허용되지 않습니다.

## <a name="remarks"></a>설명

**ctime** 함수로 저장 하는 시간 값 변환는 [time_t](../../c-runtime-library/standard-types.md) 에 문자열 값입니다. *sourceTime* 값에 대 한 호출에서 가져온 일반적으로 [시간](time-time32-time64.md), 자정 이후 경과 된 시간 (초)을 반환 (00: 00:00), 1970 년 1 월 1 일 협정 세계시 (UTC)입니다. 반환 값 문자열은 정확히 26자를 포함하며 그 형식은 다음과 같습니다.

```Output
Wed Jan 02 02:03:55 1980\n\0
```

24시간제가 사용됩니다. 모든 필드에는 상수 너비가 있습니다. 줄 바꿈 문자('\n') 및 null 문자('\0')는 문자열의 마지막 두 자리를 차지합니다.

또한 변환된 문자열은 현지 표준 시간대 설정에 따라 조정됩니다. 참조는 [시간](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), 및 [localtime](localtime-localtime32-localtime64.md) 현지 시간을 구성에 대 한 함수 및 [_tzset](tzset.md) 에 대 한 함수 표준 시간대 환경 및 전역 변수를 정의 하는 방법에 대 한 세부 정보입니다.

에 대 한 호출 **ctime** 수정 하 여 사용 되는 단일 정적으로 할당 된 버퍼는 **gmtime** 및 **localtime** 함수입니다. 이러한 루틴 중 하나를 호출할 때마다 이전 호출의 결과가 삭제됩니다. **ctime** 정적 버퍼와 공유 하는 **asctime** 함수입니다. 에 대 한 호출 따라서 **ctime** 모든 이전 호출의 결과 소멸 **asctime**, **localtime**, 또는 **gmtime**합니다.

**_wctime** 및 **_wctime64** 은 와이드 문자 버전의 **ctime** 및 **_ctime64**; 와이드 문자 문자열에 대 한 포인터를 반환 합니다. 그렇지 않으면 **_ctime64**, **_wctime**, 및 **_wctime64** 동일 하 게 동작 **ctime**합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. 경우 *sourceTime* 가 null 포인터인 경우는 *sourceTime* 값이 음수인 경우에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 하는이 함수를 이러한 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md). 실행을 계속 허용 된 경우 함수는 반환 **NULL** 설정 **errno** 를 **EINVAL**합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**ctime**|**ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**ctime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> 또는 \<wchar.h>|
|**_wctime32**|\<time.h> 또는 \<wchar.h>|
|**_wctime64**|\<time.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

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

## <a name="see-also"></a>참고자료

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
