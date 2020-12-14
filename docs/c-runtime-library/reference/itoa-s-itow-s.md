---
description: '자세히 알아보기: _itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s'
title: _itoa_s, _itow_s 함수
ms.date: 4/2/2020
api_name:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
- _o__i64toa_s
- _o__i64tow_s
- _o__itoa_s
- _o__itow_s
- _o__ltoa_s
- _o__ltow_s
- _o__ui64toa_s
- _o__ui64tow_s
- _o__ultoa_s
- _o__ultow_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
- _itot_s
- _ltot_s
- _ultot_s
- _i64tot_s
- _ui64tot_s
- itoa_s
- ltoa_s
- ultoa_s
- i64toa_s
- ui64toa_s
- itow_s
- ltow_s
- ultow_s
- i64tow_s
- ui64tow_s
- itot_s
- ltot_s
- ultot_s
- i64tot_s
- ui64tot_s
helpviewer_keywords:
- _ui64toa_s function
- _itow_s function
- _i64tow_s function
- _itot_s function
- converting integers
- itow_s function
- i64toa_s function
- _ui64tow_s function
- integers, converting
- _i64tot_s function
- itoa_s function
- _itoa_s function
- ui64toa_s function
- i64tow_s function
- converting numbers, to strings
- _ui64tot_s function
- _i64toa_s function
ms.assetid: eb746581-bff3-48b5-a973-bfc0a4478ecf
ms.openlocfilehash: c02ca2e6090c9396a3a6c91cd6353604d5df8096
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254237"
---
# <a name="_itoa_s-_ltoa_s-_ultoa_s-_i64toa_s-_ui64toa_s-_itow_s--_ltow_s--_ultow_s-_i64tow_s-_ui64tow_s"></a>_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s

정수를 문자열로 변환합니다. 이러한 버전은 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명 된 대로 보안 기능이 향상 된 [기능을 _itow](itoa-itow.md) 하는 _itoa 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _itoa_s( int value, char * buffer, size_t size, int radix );
errno_t _ltoa_s( long value, char * buffer, size_t size, int radix );
errno_t _ultoa_s( unsigned long value, char * buffer, size_t size, int radix );
errno_t _i64toa_s( long long value, char *buffer,
   size_t size, int radix );
errno_t _ui64toa_s( unsigned long long value, char *buffer,
   size_t size, int radix );

errno_t _itow_s( int value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ltow_s( long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ultow_s( unsigned long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _i64tow_s( long long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ui64tow_s( unsigned long long value, wchar_t *buffer,
   size_t size, int radix
);

// These template functions are C++ only:
template <size_t size>
errno_t _itoa_s( int value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ltoa_s( long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ultoa_s( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _itow_s( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ltow_s( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ultow_s( unsigned long value, wchar_t (&buffer)[size], int radix );
```

### <a name="parameters"></a>매개 변수

*value*<br/>
변환할 숫자입니다.

*버퍼*<br/>
변환 결과를 포함 하는 출력 버퍼입니다.

*size*<br/>
문자 또는 와이드 문자 단위의 *버퍼* 크기입니다.

*기 수*<br/>
*값* 을 변환 하는 데 사용할 기 수 또는 숫자 기준으로, 2-36 범위 내에 있어야 합니다.

## <a name="return-value"></a>반환 값

성공 시 0이고, 실패 시 오류 코드입니다. 다음 조건 중 하나가 적용되는 경우 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다.

### <a name="error-conditions"></a>오류 조건

|값|buffer|크기|radix|반환 값|
|-----------|------------|----------------------|-----------|------------|
|any|**NULL**|any|any|**EINVAL**|
|any|any|<=0|any|**EINVAL**|
|any|any|<= length of the result string required|any|**EINVAL**|
|any|any|any|*기* < 2 개 또는 *기* > 36|**EINVAL**|

### <a name="security-issues"></a>보안 문제

이러한 함수는 *버퍼가* 유효한 메모리를 가리키지 않거나 **NULL** 이 아닌 경우 또는 버퍼의 길이가 결과 문자열을 저장할 만큼 길지 않은 경우 액세스 위반을 생성할 수 있습니다.

## <a name="remarks"></a>설명

매개 변수와 반환 값을 제외 하 고 **_itoa_s** 및 **_itow_s** 함수 패밀리의 동작은 해당 하는 보안 수준이 낮은 **_itoa** 및 **_itow** 버전과 동일 합니다.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이러한 함수의 디버그 라이브러리 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)를 사용하세요.

CRT에는 몇 가지 일반적인 기본에 대해 null 종결자와 부호 문자를 포함 하 여 각 정수 형식의 가능한 가장 긴 값을 변환 하는 데 필요한 버퍼 크기를 정의 하는 편리한 매크로가 포함 되어 있습니다. 자세한 내용은 [최대 변환 수 매크로](itoa-itow.md#maximum-conversion-count-macros)를 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot_s**|**_itoa_s**|**_itoa_s**|**_itow_s**|
|**_ltot_s**|**_ltoa_s**|**_ltoa_s**|**_ltow_s**|
|**_ultot_s**|**_ultoa_s**|**_ultoa_s**|**_ultow_s**|
|**_i64tot_s**|**_i64toa_s**|**_i64toa_s**|**_i64tow_s**|
|**_ui64tot_s**|**_ui64toa_s**|**_ui64toa_s**|**_ui64tow_s**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_itoa_s**, **_ltoa_s**, **_ultoa_s**, **_i64toa_s**, **_ui64toa_s**|\<stdlib.h>|
|**_itow_s**, **_ltow_s**, **_ultow_s**, **_i64tow_s**, **_ui64tow_s**|\<stdlib.h> 또는 \<wchar.h>|

이러한 함수는 Microsoft 전용입니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 샘플에서는 몇 가지 정수 변환 함수를 사용 하는 방법을 보여 줍니다. [_Countof](countof-macro.md) 매크로는 배열 선언이 컴파일러에 표시 되는 경우에만 버퍼 크기를 확인 하는 데 사용할 수 있으며 포인터에 대 한 decayed 있는 매개 변수가 아닙니다.

```C
// crt_itoa_s.c
// Compile by using: cl /W4 crt_itoa_s.c
#include <stdlib.h>     // for _itoa_s functions, _countof, count macro
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen

int main( void )
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;
    for ( r = 10; r >= 2; --r )
    {
        _itoa_s( -1, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _i64toa_s( -1LL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _ui64toa_s( 0xffffffffffffffffULL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[_itoa, _itow 함수](itoa-itow.md)<br/>
