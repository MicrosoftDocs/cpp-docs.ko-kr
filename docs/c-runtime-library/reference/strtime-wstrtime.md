---
description: '자세히 알아보기: _strtime, _wstrtime'
title: _strtime, _wstrtime
ms.date: 4/2/2020
api_name:
- _wstrtime
- _strtime
- _o__strtime
- _o__wstrtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
ms.openlocfilehash: 0cb5d5deaa89d832ed1cecd231ed1c8f456ccace
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337748"
---
# <a name="_strtime-_wstrtime"></a>_strtime, _wstrtime

버퍼에 시간을 복사합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_strtime_s, _wstrtime_s](strtime-s-wstrtime-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>매개 변수

*timestr*<br/>
시간 문자열입니다.

## <a name="return-value"></a>반환 값

결과 문자열 *timestr* 에 대 한 포인터를 반환 합니다.

## <a name="remarks"></a>설명

**_Strtime** 함수는 *timestr* 가 가리키는 버퍼에 현재 현지 시간을 복사 합니다. 시간은 **hh: mm: ss** 형식으로 지정 됩니다. 여기서 **hh** 는 24 시간 표기법의 시간을 나타내는 두 자리 숫자, **mm** 은 분을 나타내는 두 자리 숫자, **ss** 는 초를 나타내는 두 자리 숫자입니다. 예를 들어, **18:23:44** 문자열은 23 분 및 44 초 (오후 6 시)를 나타냅니다. 버퍼는 9바이트 이상이어야 합니다.

**_wstrtime** 은 **_strtime** 의 와이드 문자 버전입니다. **_wstrtime** 의 인수 및 반환 값은 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다. *Timestr* 가 **NULL** 포인터 이거나 *timestr* 의 형식이 잘못 된 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 예외가 계속 허용 되는 경우 이러한 함수는 **null** 을 반환 하 고 *Timestr* 이 **Null** 인 경우 **errno** 를 **EINVAL** 로 설정 하 고 *timestr* 의 형식이 잘못 된 경우 **errno** 를 **ERANGE** 로 설정 합니다.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<time.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
```

## <a name="see-also"></a>참고 항목

[시간 관리](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
