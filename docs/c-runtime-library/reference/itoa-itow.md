---
title: _itoa, _itow 함수
description: _Itoa 및 _itow에 대 한 API 참조 정수를 문자열로 변환 합니다.
ms.date: 4/2/2020
api_name:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- _o__i64toa
- _o__i64tow
- _o__itoa
- _o__itow
- _o__ltoa
- _o__ltow
- _o__ui64toa
- _o__ui64tow
- _o__ultoa
- _o__ultow
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
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: c8d64dcc1efdb9371feb98d8674a7a2c41c7ab3a
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555465"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

정수를 문자열로 변환합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_itoa_s _itow_s 함수](itoa-s-itow-s.md)를 참조 하세요.

## <a name="syntax"></a>구문

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These POSIX versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>매개 변수

*value*<br/>
변환할 숫자입니다.

*버퍼*<br/>
변환 결과를 포함 하는 버퍼입니다.

*기 수*<br/>
2-36 범위에 있어야 하는 *값*의 변환에 사용할 기본입니다.

*size*<br/>
문자 형식의 단위에 있는 버퍼의 길이입니다. 이 매개 변수는 c + +의 *buffer* 인수에서 유추 됩니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 *버퍼*에 대 한 포인터를 반환 합니다. 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

**_Itoa**, **_ltoa**, **_ultoa**, **_i64toa**및 **_ui64toa** 함수는 지정 된 *값* 인수의 숫자를 null로 끝나는 문자열로 변환 하 고 결과 (_itoa, **_ltoa**, **_ultoa**의 경우 33 자, **_i64toa 및** **_ui64toa** **의 경우**65)를 *버퍼*에 저장 합니다. *기* 수가 10이 고 *값* 이 음수인 경우 저장 된 문자열의 첫 번째 문자는 빼기 기호 ( **-** )입니다. **_Itow**, **_ltow**, **_ultow**, **_i64tow**및 **_ui64tow** 함수는 각각 **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**및 **_ui64toa**의 와이드 문자 버전입니다.

> [!IMPORTANT]
> 이러한 함수는 너무 작은 버퍼의 끝을 지나서 쓸 수 있습니다. 버퍼 오버런을 방지 하려면 *버퍼가* 변환 된 숫자와 후행 null 문자 및 부호 문자를 포함할 만큼 충분히 큰지 확인 합니다. 이러한 함수를 잘못 사용할 경우 코드에서 심각한 보안 문제가 발생할 수 있습니다.

보안 문제가 발생할 수 있기 때문에 기본적으로 이러한 함수는 사용 중단 경고를 [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)발생 시킵니다. **이 함수 또는 변수는 안전 하지 않을 수 있습니다 C4996. 대신 safe_function를 사용 하는 것이 좋습니다** *safe_function* **. 사용 중단을 사용 하지 않도록 설정 하려면 _CRT_SECURE_NO_WARNINGS을 사용 합니다.** 경고 메시지에서 제안 하는 *safe_function* 사용 하도록 소스 코드를 변경 하는 것이 좋습니다. 더 안전한 함수는 지정 된 버퍼 크기 보다 더 많은 문자를 쓰지 않습니다. 자세한 내용은 [_itoa_s, _itow_s 함수](itoa-s-itow-s.md)를 참조 하세요.

사용 중단 경고 없이 이러한 함수를 사용 하려면 CRT 헤더를 포함 하기 전에 **_CRT_SECURE_NO_WARNINGS** 전처리기 매크로를 정의 합니다. **D_CRT_SECURE_NO_WARNINGS** 컴파일러 옵션을 **cl** 명령에 추가 하 여 개발자 명령 프롬프트의 명령줄에서이 작업을 수행할 수 있습니다. 그렇지 않으면 소스 파일에서 매크로를 정의 합니다. 미리 컴파일된 헤더를 사용 하는 경우 미리 컴파일된 헤더의 맨 위에 매크로를 정의 *합니다 (Visual* Studio 2017 및 이전 버전의*stdafx.h* ). 소스 코드에서 매크로를 정의 하려면 다음 예제와 같이 CRT 헤더를 포함 하기 전에 **#define** 지시문을 사용 합니다.

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

C + +에서 이러한 함수는 보다 안전한 대응 함수를 호출 하는 템플릿 오버 로드를 포함 합니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

POSIX 이름 **itoa**, **ltoa**및 **ultoa** 는 **_itoa**, **_ltoa**및 **_ultoa** 함수의 별칭으로 존재 합니다. POSIX 이름은 ISO C의 구현 관련 전역 함수 이름 규칙을 따르지 않으므로 더 이상 사용 되지 않습니다. 기본적으로 이러한 함수는 사용 중단 경고를 발생 시킵니다. [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) **이 항목에 대 한 POSIX 이름은 사용 되지 않습니다. 대신 ISO C 및 c + +와 호환 되는 이름: new_name을 사용** *new_name*합니다. 이러한 함수, **_itoa_s** **_ltoa_s**또는 **_ultoa_s**의 안전한 버전을 사용 하도록 소스 코드를 변경 하는 것이 좋습니다. 자세한 내용은 [_itoa_s, _itow_s 함수](itoa-s-itow-s.md)를 참조 하세요.

소스 코드 이식성의 경우 코드에 POSIX 이름을 유지할 수 있습니다. 사용 중단 경고 없이 이러한 함수를 사용 하려면 CRT 헤더를 포함 하기 전에 **_CRT_NONSTDC_NO_WARNINGS** 및 **_CRT_SECURE_NO_WARNINGS** 전처리기 매크로를 모두 정의 합니다. **D_CRT_SECURE_NO_WARNINGS** 및 **/D_CRT_NONSTDC_NO_WARNINGS** 컴파일러 옵션을 **cl** 명령에 추가 하 여 개발자 명령 프롬프트의 명령줄에서이 작업을 수행할 수 있습니다. 그렇지 않으면 소스 파일에서 매크로를 정의 합니다. 미리 컴파일된 헤더를 사용 하는 경우 미리 컴파일된 헤더 포함 파일의 맨 위에 있는 매크로를 정의 합니다. 소스 코드에서 매크로를 정의 하려면 다음 예제와 같이 CRT 헤더를 포함 하기 전에 **#define** 지시문을 사용 합니다.

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>최대 변환 수 매크로

변환에 대 한 보안 버퍼를 만들 수 있도록 CRT에는 몇 가지 편리한 매크로가 포함 되어 있습니다. 이러한 값은 몇 가지 일반적인 기본에 대해 null 종결자 및 sign 문자를 포함 하 여 각 정수 형식의 가능한 가장 긴 값을 변환 하는 데 필요한 버퍼 크기를 정의 합니다. 변환 버퍼가 *기*수로 지정 된 기준에서 변환을 수신 하기에 충분히 큰지 확인 하려면 버퍼를 할당할 때 정의 된 매크로 중 하나를 사용 합니다. 이를 통해 정수 형식을 문자열로 변환할 때 버퍼 오버런 오류를 방지할 수 있습니다. 이러한 매크로는 소스에 stdlib.h 또는 wchar를 포함 하는 경우에 정의 됩니다.

문자열 변환 함수에서 이러한 매크로 중 하나를 사용 하려면 해당 문자 형식의 변환 버퍼를 선언 하 고 정수 형식에 대 한 매크로 값과 기반을 버퍼 차원으로 사용 합니다. 다음 표에서는 나열 된 기본에 대 한 각 함수에 적합 한 매크로를 나열 합니다.

|Functions|radix|매크로|
|-|-|-|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

이 예제에서는 변환 횟수 매크로를 사용 하 여 기본 2에를 포함할 수 있을 만큼 충분히 많은 버퍼를 정의 합니다 **`unsigned long long`** .

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> 또는 \<wchar.h>|

이러한 함수와 매크로는 Microsoft 전용입니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 샘플에서는 일부 정수 변환 함수를 사용 하는 방법을 보여 줍니다. **_CRT_SECURE_NO_WARNINGS** 매크로를 사용 하 여 대기 경고 C4996를 확인 합니다.

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
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
[_itoa_s, _itow_s 함수](itoa-s-itow-s.md)<br/>
