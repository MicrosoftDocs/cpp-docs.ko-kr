---
description: '자세히 알아보기: strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l'
title: strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l
ms.date: 1/20/2021
api_name:
- strncat
- _strncat_l
- _mbsncat
- _mbsncat_l
- wcsncat
- wcsncat_l
- _o__mbsncat
- _o__mbsncat_l
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
- _tcsncat_l
- _wcsncat_l
- _tcsnccat_l
- _mbsncat
- _strncat_l
- strncat
- _tcsnccat
- _mbsncat_l
- _ftcsncat
- wcsncat
- _tcsncat
helpviewer_keywords:
- concatenating strings
- ftcsncat function
- tcsncat_l function
- _tcsnccat_l function
- _tcsncat function
- strncat function
- _ftcsncat function
- mbsncat function
- mbsncat_l function
- strings [C++], appending
- wcsncat function
- tcsnccat function
- tcsnccat_l function
- _tcsnccat function
- string concatenation [C++]
- appending strings
- characters [C++], appending to strings
- _mbsncat function
- _tcsncat_l function
- _mbsncat_l function
- tcsncat function
ms.openlocfilehash: 4b5ae812560cb42498ebed71bb9b8791581ef332
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667021"
---
# <a name="strncat-_strncat_l-wcsncat-_wcsncat_l-_mbsncat-_mbsncat_l"></a>strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l

문자열의 문자를 추가합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다 `[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l` .] (strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)를 참조 하십시오.

> [!IMPORTANT]
> **`_mbsncat`** 및는 **`_mbsncat_l`** Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *strncat(
   char *strDest,
   const char *strSource,
   size_t count
);
wchar_t *wcsncat(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
unsigned char *_mbsncat(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count
);
unsigned char *_mbsncat_l(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
char *strncat(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
wchar_t *wcsncat(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*`strDest`*\
Null 종료 대상 문자열입니다.

*`strSource`*\
Null 종료 소스 문자열입니다.

*`count`*\
추가할 문자 수입니다.

*`locale`*\
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

대상 문자열에 대한 포인터를 반환합니다. 반환 값 없음은 오류를 나타내는 데 예약되어 있습니다.

## <a name="remarks"></a>설명

**`strncat`** 함수는의 처음 개 문자를에 추가 *`count`* *`strSource`* *`strDest`* 합니다. 의 초기 문자는 *`strSource`* 의 종료 null 문자를 덮어씁니다 *`strDest`* . 문자가 추가 되기 전에에 null 문자가 표시 되 면에서 *`strSource`* *`count`* **`strncat`** 모든 문자를 *`strSource`* null 문자까지 추가 합니다. *`count`* 가의 길이 보다 크면의 *`strSource`* 길이가 대신 *`strSource`* 사용 됩니다 *`count`* . 모든 경우 결과 문자열은 null 문자로 종료됩니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

> [!IMPORTANT]
> **`strncat`** 는의 공간이 충분 한지 확인 하지 않으므로 *`strDest`* 버퍼 오버런이 발생할 수 있습니다. 추가 되는 문자 수를 제한 한다는 점에 유의 *`count`* 하세요 .의 크기에는 제한이 없습니다 *`strDest`* . 아래 예제를 참조하세요. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

**`wcsncat`** 및 **`_mbsncat`** 는의 와이드 문자 및 멀티 바이트 문자 버전입니다 **`strncat`** . 의 문자열 인수와 반환 값은 와이드 문자열이 며의 문자열 인수와 반환 값은 **`wcsncat`** **`_mbsncat`** 멀티 바이트 문자열입니다. 그렇지 않으면 이들 세 함수는 동일하게 작동합니다.

출력 값은 로캘의 범주 설정에 영향을 받습니다 **`LC_CTYPE`** . 자세한 내용은를 참조 하십시오 [`setlocale`](setlocale-wsetlocale.md) . 접미사가 없는 이러한 함수 버전은 **`_l`** 이 로캘 종속 동작에 현재 로캘을 사용 합니다. 접미사가 있는 버전은 **`_l`** 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

C++에서 이러한 함수에는 템플릿 오버로드가 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|`TCHAR.H `일반|`_UNICODE & _MBCS` 정의 되지 않음|`_MBCS` 지정|`_UNICODE` 지정|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tcsncat`**|**`strncat`**|**`_mbsnbcat`**|**`wcsncat`**|
|**`_tcsncat_l`**|**`_strncat_l`**|**`_mbsnbcat_l`**|**`_wcsncat_l`**|

> [!NOTE]
> **`_strncat_l`** 및 **`_wcsncat_l`** 는 로캘 종속성이 없으며 직접 호출할 수 없습니다. 에서 내부적으로 사용 하기 위해 제공 됩니다 **`_tcsncat_l`** .

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`strncat`**|\<string.h>|
|**`wcsncat`**|\<string.h> 또는 \<wchar.h>|
|**`_mbsncat`**|\<mbstring.h>|
|**`_mbsncat_l`**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strncat.c
// Use strcat and strncat to append to a string.
#include <stdlib.h>

#define MAXSTRINGLEN 39

char string[MAXSTRINGLEN+1];
// or char *string = malloc(MAXSTRINGLEN+1);

void BadAppend( char suffix[], int n )
{
   strncat( string, suffix, n );
}

void GoodAppend( char suffix[], size_t n )
{
   strncat( string, suffix, __min( n, MAXSTRINGLEN-strlen(string)) );
}

int main( void )
{
   string[0] = '\0';
   printf( "string can hold up to %d characters\n", MAXSTRINGLEN );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   BadAppend( "Extra text to add to the string...", 20 );
   printf( "After BadAppend :  %s (%d chars)\n", string, strlen(string) );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   GoodAppend( "Extra text to add to the string...", 20 );
   printf( "After GoodAppend:  %s (%d chars)\n", string, strlen(string) );
}
```

### <a name="output"></a>출력

```Output
string can hold up to 39 characters
After BadAppend :  This is the initial string!Extra text to add to (47 chars)
After GoodAppend:  This is the initial string!Extra text t (39 chars)
```

**Badappend** 로 인해 버퍼 오버런이 발생 했습니다.

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)\
[`_mbsnbcat, _mbsnbcat_l`](mbsnbcat-mbsnbcat-l.md)\
[`strcat, wcscat, _mbscat`](strcat-wcscat-mbscat.md)\
[`strcmp, wcscmp, _mbscmp`](strcmp-wcscmp-mbscmp.md)\
[`strcpy, wcscpy, _mbscpy`](strcpy-wcscpy-mbscpy.md)\
[`strncmp, wcsncmp, _mbsncmp, _mbsncmp_l`](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)\
[`strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l`](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)\
[`_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l`](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)\
[`strrchr, wcsrchr, _mbsrchr, _mbsrchr_l`](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)\
[`_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l`](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)\
[`strspn, wcsspn, _mbsspn, _mbsspn_l`](strspn-wcsspn-mbsspn-mbsspn-l.md)\
[로캘을](../../c-runtime-library/locale.md)\
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
