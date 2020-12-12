---
description: '자세히 알아보기: strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l'
title: strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l
ms.date: 4/2/2020
api_name:
- strncpy
- _strncpy_l
- _mbsncpy
- wcsncpy
- _mbsncpy_l
- _wcsncpy_l
- _o__mbsncpy
- _o__mbsncpy_l
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
- _fstrncpy
- strncpy
- _ftcsncpy
- _tcsnccpy_l
- _tcsnccpy
- _mbsncpy
- wcsncpy
- _tcsncpy
- _strncpy_l
- _mbsncpy_l
- _wcsncpy_l
helpviewer_keywords:
- wcsncpy_l function
- characters [C++], copying
- mbsncpy_l function
- strncpy_l function
- wcsncpy function
- tcsnccpy function
- ftcsncpy function
- copying characters of strings
- _wcsncpy_l function
- _tcsnccpy function
- _tcsnccpy_l function
- strncpy function
- _tcsncpy function
- mbsncpy function
- _fstrncpy function
- _mbsncpy_l function
- tcsncpy_l function
- tcsnccpy_l function
- fstrncpy function
- strings [C++], copying
- _ftcsncpy function
- _tcsncpy_l function
- _mbsncpy function
- tcsncpy function
- _strncpy_l function
ms.assetid: ac4345a1-a129-4f2f-bb8a-373ec58ab8b0
ms.openlocfilehash: 28d3998ccfe1e7460fa628d462732f233c553b10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306107"
---
# <a name="strncpy-_strncpy_l-wcsncpy-_wcsncpy_l-_mbsncpy-_mbsncpy_l"></a>strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l

한 문자열의 문자를 다른 문자열로 복사합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)을 참조하세요.

> [!IMPORTANT]
> **_mbsncpy** 및 **_mbsncpy_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *strncpy(
   char *strDest,
   const char *strSource,
   size_t count
);
char *_strncpy_l(
   char *strDest,
   const char *strSource,
   size_t count,
   locale_t locale
);
wchar_t *wcsncpy(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
wchar_t *_wcsncpy_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   locale_t locale
);
unsigned char *_mbsncpy(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count
);
unsigned char *_mbsncpy_l(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
char *strncpy(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
char *_strncpy_l(
   char (&strDest)[size],
   const char *strSource,
   size_t count,
   locale_t locale
); // C++ only
template <size_t size>
wchar_t *wcsncpy(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
wchar_t *_wcsncpy_l(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count,
   locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbsncpy(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncpy_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*strDest*<br/>
대상 문자열입니다.

*strSource*<br/>
원본 문자열입니다.

*count*<br/>
복사할 문자의 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*Strdest* 를 반환 합니다. 반환 값 없음은 오류를 나타내는 데 예약되어 있습니다.

## <a name="remarks"></a>설명

**Strncpy** 함수는 *strsource* 의 초기 *카운트* 문자를 *Strsource* 에 복사 하 고 *strsource* 를 반환 합니다. *Count* 가 *strsource* 의 길이 보다 작거나 같으면 복사 된 문자열에 null 문자가 자동으로 추가 되지 않습니다. *Count* 가 *strsource* 의 길이 보다 큰 경우 대상 문자열은 최대 길이 *개수* 까지 null 문자로 채워집니다. 원본 및 대상 문자열이 겹치면 **strncpy** 의 동작이 정의 되지 않습니다.

> [!IMPORTANT]
> **strncpy** 는 *strdest* 에 충분 한 공간을 확인 하지 않습니다. 이로 인해 버퍼 오버런이 발생할 수 있습니다. *Count* 인수는 복사 되는 문자 수를 제한 합니다. *Strdest* 의 크기에는 제한이 없습니다. 다음 예제를 참조하세요. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

*Strdest* 또는 *Strdest* 가 **NULL** 포인터 이거나 *Count* 가 0 보다 작거나 같으면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는-1을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

**wcsncpy** 및 **_mbsncpy** 는 **strncpy** 의 와이드 문자 및 멀티 바이트 문자 버전입니다. **Wcsncpy** 및 **_mbsncpy** 의 인수 및 반환 값은 그에 따라 다릅니다. 그 외의 경우에는 이들 6개 함수가 동일하게 작동합니다.

**_L** 접미사가 있는 이러한 함수 버전은 로캘 종속 동작에 현재 로캘 대신 전달 된 로캘을 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncpy**|**strncpy**|**_mbsnbcpy**|**wcsncpy**|
|**_tcsncpy_l**|**_strncpy_l**|**_mbsnbcpy_l**|**_wcsncpy_l**|

> [!NOTE]
> **_strncpy_l** 및 **_wcsncpy_l** 에는 로캘 종속성이 없습니다. 이러한 기능은 **_tcsncpy_l** 에 대해서만 제공 되며 직접 호출할 수 없습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strncpy**|\<string.h>|
|**wcsncpy**|\<string.h> 또는 \<wchar.h>|
|**_mbsncpy**, **_mbsncpy_l**|\<mbstring.h>|

플랫폼 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 **strncpy** 를 사용 하는 방법과 프로그램 버그 및 보안 문제를 일으킬 수 있는 오용 방법을 보여 줍니다. 컴파일러는 crt_strncpy_x86 **에 대** 한 각 호출에 대 한 경고를 생성 **합니다. c (15): 경고 C4996: ' Strncpy ':이 함수 또는 변수는 안전 하지 않을 수 있습니다. 대신 strncpy_s를 사용 하는 것이 좋습니다. 사용 중단을 사용 하지 않도록 설정 하려면 _CRT_SECURE_NO_WARNINGS을 사용 합니다. 자세한 내용은 온라인 도움말을 참조 하십시오.**

```C
// crt_strncpy_x86.c
// Use this command in an x86 developer command prompt to compile:
// cl /TC /W3 crt_strncpy_x86.c

#include <stdio.h>
#include <string.h>

int main() {
   char t[20];
   char s[20];
   char *p = 0, *q = 0;

   strcpy_s(s, sizeof(s), "AA BB CC");
   // Note: strncpy is deprecated; consider using strncpy_s instead
   strncpy(s, "aa", 2);     // "aa BB CC"         C4996
   strncpy(s + 3, "bb", 2); // "aa bb CC"         C4996
   strncpy(s, "ZZ", 3);     // "ZZ",              C4996
                            // count greater than strSource, null added
   printf("%s\n", s);

   strcpy_s(s, sizeof(s), "AA BB CC");
   p = strstr(s, "BB");
   q = strstr(s, "CC");
   strncpy(s, "aa", p - s - 1);   // "aa BB CC"   C4996
   strncpy(p, "bb", q - p - 1);   // "aa bb CC"   C4996
   strncpy(q, "cc",  q - s);      // "aa bb cc"   C4996
   strncpy(q, "dd", strlen(q));   // "aa bb dd"   C4996
   printf("%s\n", s);

   // some problems with strncpy
   strcpy_s(s, sizeof(s), "test");
   strncpy(t, "this is a very long string", 20 ); // C4996
   // Danger: at this point, t has no terminating null,
   // so the printf continues until it runs into one.
   // In this case, it will print "this is a very long test"
   printf("%s\n", t);

   strcpy_s(t, sizeof(t), "dogs like cats");
   printf("%s\n", t);

   strncpy(t + 10, "to chase cars.", 14); // C4996
   printf("%s\n", t);

   // strncpy has caused a buffer overrun and corrupted string s
   printf("Buffer overrun: s = '%s' (should be 'test')\n", s);
   // Since the stack grows from higher to lower addresses, buffer
   // overruns can corrupt function return addresses on the stack,
   // which can be exploited to run arbitrary code.
}
```

출력

```Output
ZZ
aa bb dd
this is a very long test
dogs like cats
dogs like to chase cars.
Buffer overrun: s = 'ars.' (should be 'test')
```

자동 변수의 레이아웃과 오류 검색 및 코드 보호의 수준은 변경된 컴파일러 설정에 따라 달라질 수 있습니다. 이 예제에서는 다른 컴파일러 옵션을 사용하거나 다른 컴파일 환경에서 빌드하는 경우 서로 다른 결과가 발생할 수 있습니다.

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
