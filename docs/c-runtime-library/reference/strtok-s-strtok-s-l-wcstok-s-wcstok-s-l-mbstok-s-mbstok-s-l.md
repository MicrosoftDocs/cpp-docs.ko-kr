---
description: '자세한 정보: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l'
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: fb02682abac8655964051d780e9e84e644256aa2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288713"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

현재 로캘 또는 전달된 로캘을 사용하여 문자열의 다음 토큰을 찾습니다. 이러한 버전의 [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.

> [!IMPORTANT]
> **_mbstok_s** 및 **_mbstok_s_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
찾을 토큰을 포함 하는 문자열입니다.

*구분 기호*<br/>
사용할 구분 기호 문자 집합입니다.

*context*<br/>
함수 호출 간의 위치 정보를 저장 하는 데 사용 됩니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*Str* 에서 찾은 다음 토큰에 대 한 포인터를 반환 합니다. 더 이상 토큰을 찾을 수 없는 경우 **NULL** 을 반환 합니다. 각 호출은 반환 된 토큰 후에 발생 하는 첫 번째 구분 기호에서 null 문자를 대체 하 여 *str* 을 수정 합니다.

### <a name="error-conditions"></a>오류 조건

|*str*|*구분 기호*|*context*|반환 값|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|any|null 포인터에 대한 포인터|**NULL**|**EINVAL**|
|any|**NULL**|any|**NULL**|**EINVAL**|
|any|any|**NULL**|**NULL**|**EINVAL**|

*Str* 이 **NULL** 이지만 *context* 가 유효한 컨텍스트 포인터에 대 한 포인터 이면 오류가 발생 하지 않습니다.

## <a name="remarks"></a>설명

함수 패밀리 **strtok_s** *str* 에서 다음 토큰을 찾습니다. *구분 기호의* 문자 집합은 현재 호출에서 *str* 에 있는 토큰의 가능한 구분 기호를 지정 합니다. **wcstok_s** 및 **_mbstok_s** 는 **strtok_s** 의 와이드 문자 및 멀티 바이트 문자 버전입니다. **Wcstok_s** 및 **_wcstok_s_l** 의 인수 및 반환 값은 와이드 문자열입니다. **_mbstok_s** 및 **_mbstok_s_l** 는 멀티 바이트 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

이 함수는 해당 매개 변수의 유효성을 검사합니다. 오류 조건 테이블과 같이 오류 조건이 발생 하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **NULL** 을 반환 합니다.

**Strtok_s** 에 대 한 첫 번째 호출에서 함수는 선행 구분 기호를 건너뛰고 *str* 의 첫 번째 토큰에 대 한 포인터를 반환 하 여 null 문자로 토큰을 종료 합니다. **Strtok_s** 에 대 한 일련의 호출로 *str* 의 나머지 부분에서 더 많은 토큰을 분할할 수 있습니다. **Strtok_s** 를 호출할 때마다 해당 호출에서 반환 된 토큰 뒤에 null 문자를 삽입 하 여 *str* 를 수정할 수 있습니다. *컨텍스트* 포인터는 읽고 있는 문자열 및 다음 토큰을 읽을 문자열의 위치를 추적 합니다. *Str* 에서 다음 토큰을 읽으려면 *str* 인수에 대해 **NULL** 값을 사용 하 여 **strtok_s** 를 호출 하 고 동일한 *컨텍스트* 매개 변수를 전달 합니다. **NULL** *str* 인수를 설정 하면 **strtok_s** 은 수정 된 *str* 에서 다음 토큰을 검색 합니다. 구분 *기호 인수는* 구분 기호 집합이 다를 수 있도록 다음에 대 한 호출에서 임의의 값을 사용할 수 있습니다.

*Context* 매개 변수는 **strtok** 및 **_strtok_l** 에 사용 된 정적 버퍼를 대체 하므로 동일한 스레드에서 두 문자열을 동시에 구문 분석할 수 있습니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따라 영향을 받습니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요.

**_L** 접미사가 없는 이러한 함수 버전은이 로캘 종속 동작에 현재 스레드 로캘을 사용 합니다. **_L** 접미사가 있는 버전은 *로캘* 매개 변수로 지정 된 로캘을 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> 또는 \<wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|\_유니코드 & \_ MBCS가 정의 되지 않았습니다.|\_MBCS 정의|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>예제

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
