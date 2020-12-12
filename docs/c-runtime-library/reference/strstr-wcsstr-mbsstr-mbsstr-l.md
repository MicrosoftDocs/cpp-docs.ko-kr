---
description: Strstr, wcsstr, _mbsstr, _mbsstr_l에 대해 자세히 알아보세요.
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 4/2/2020
api_name:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
- _o__mbsstr
- _o__mbsstr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 05f7cd3b03a56cb5e0e9343bd8cdee98af124988
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181685"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

문자열에서 처음 나오는 검색 문자열에 대한 포인터를 반환합니다.

> [!IMPORTANT]
> Windows 런타임에서 실행되는 애플리케이션에서는 `_mbsstr` 및 `_mbsstr_l`을 사용할 수는 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*str*<br/>
검색할 Null 종료 문자열입니다.

*strSearch*<br/>
검색할 Null 종료 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*Str* 에서 처음 발견 되는 *strsearch* 에 대 한 포인터를 반환 하거나 *strsearch* 가 *str* 에 표시 되지 않는 경우 NULL을 반환 합니다. *Strsearch* 가 길이가 0 인 문자열을 가리키는 경우이 함수는 *str* 을 반환 합니다.

## <a name="remarks"></a>설명

`strstr`함수는 *str* 에서 처음 발견 되는 *strsearch* 에 대 한 포인터를 반환 합니다. 종료 null 문자는 검색에 포함되지 않습니다. `wcsstr`은 `strstr`의 와이드 문자 버전이고 `_mbsstr`은 멀티바이트 버전입니다. `wcsstr`의 인수 및 반환 값은 와이드 문자열이며 `_mbsstr`의 인수와 반환 값은 멀티바이트 문자열입니다. `_mbsstr`는 매개 변수의 유효성을 검사합니다. *Str* 또는 *STRSEARCH* 가 NULL 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 `_mbsstr` 는 `errno` EINVAL로 설정 하 고 0을 반환 합니다. `strstr` 및 `wcsstr`는 매개 변수의 유효성을 검사하지 않습니다. 그렇지 않으면 이들 세 함수는 동일하게 작동합니다.

> [!IMPORTANT]
> 이러한 함수에서는 버퍼 오버런 문제로 인한 위협이 발생할 수 있습니다. 버퍼 오버런은 시스템 공격에 이용될 수 있습니다. 버퍼 오버런 문제가 발생하면 임의 코드를 실행할 수 있게 되어 보증하지 않은 방식으로 권한이 상승할 수 있기 때문입니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

C에서 이러한 함수는 **`const`** 첫 번째 인수에 대 한 포인터를 사용 합니다. C++에서는 두 오버로드를 모두 사용할 수 있습니다. 에 대 한 포인터를 사용 하는 오버 로드는에 대 한 포인터를 반환 합니다 .가 아닌에 대 한 포인터를 사용 하는 **`const`** **`const`** 버전은 **`const`** 이외의에 대 한 포인터를 반환 **`const`** 합니다 **`const`** 이러한 함수의 및 비 버전을 모두 사용할 수 있는 경우 매크로 _CRT_CONST_CORRECT_OVERLOADS 정의 됩니다 **`const`** . **`const`** 두 c + + 오버 로드에 대 한 비 동작이 필요한 경우 기호 _CONST_RETURN 정의 합니다.

출력 값은 LC_CTYPE의 로캘 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale, _wsetlocale](setlocale-wsetlocale.md)를 참조 하세요. **_L** 접미사가 없는 이러한 함수 버전은이 로캘 종속 동작에 현재 로캘을 사용 합니다. **_l** 접미사가 있는 버전은 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**해당 없음**|**해당 없음**|`_mbsstr_l`|**해당 없음**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> 또는 \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string:: find](../../standard-library/basic-string-class.md#find)<br/>
