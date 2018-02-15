---
title: strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mbsncpy_s_l
- wcsncpy_s
- _strncpy_s_l
- strncpy_s
- _mbsncpy_s
- _wcsncpy_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsncpy_s
- _wcsncpy_s_l
- strncpy_s
- _strncpy_s_l
- wcsncpy_s
- _tcsncpy_s_l
dev_langs:
- C++
helpviewer_keywords:
- _wcsncpy_s_l function
- _mbsnbcpy_s function
- _tcsncpy_s_l function
- mbsncpy_s function
- strncpy_s_l function
- _strncpy_s_l function
- strncpy_s function
- mbsncpy_s_l function
- wcsncpy_s function
- copying strings
- strings [C++], copying
- _mbsnbcpy_s_l function
- _tcsncpy_s function
- wcsncpy_s_l function
ms.assetid: a971c800-94d1-4d88-92f3-a2fe236a4546
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b439ead7628366a358da5fadb354dbc9ca070074
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="strncpys-strncpysl-wcsncpys-wcsncpysl-mbsncpys-mbsncpysl"></a>strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l
한 문자열의 문자를 다른 문자열에 복사합니다.  이러한 버전의 [strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.  
  
> [!IMPORTANT]
>  Windows 런타임에서 실행되는 응용 프로그램에서는 `_mbsncpy_s` 및 `_mbsncpy_s_l`을 사용할 수는 없습니다. 자세한 내용은 참조 [CRT 함수는 유니버설 Windows 플랫폼 앱에서 지원 되지 않습니다](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
errno_t strncpy_s(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count  
);  
errno_t _strncpy_s_l(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t wcsncpy_s(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count   
);  
errno_t _wcsncpy_s_l(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t _mbsncpy_s(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count   
);  
errno_t _mbsncpy_s_l(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count,  
   locale_t locale  
);  
template <size_t size>  
errno_t strncpy_s(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
errno_t _strncpy_s_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t wcsncpy_s(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcsncpy_s_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsncpy_s(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsncpy_s_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>매개 변수  
 `strDest`  
 대상 문자열입니다.  
  
 `numberOfElements`  
 대상 문자열의 크기(문자)입니다.  
  
 `strSource`  
 소스 문자열입니다.  
  
 `count`  
 복사할 문자 수 또는 [_TRUNCATE](../../c-runtime-library/truncate.md)입니다.  
  
 `locale`  
 사용할 로캘입니다.  
  
## <a name="return-value"></a>반환 값  
 정상적으로 실행되는 경우 0이고 자르기가 수행되는 경우 `STRUNCATE`이며 그 외의 경우에는 오류 코드입니다.  
  
### <a name="error-conditions"></a>오류 조건  
  
|`strDest`|`numberOfElements`|`strSource`|반환 값|`strDest`의 내용|  
|---------------|------------------------|-----------------|------------------|---------------------------|  
|`NULL`|any|any|`EINVAL`|수정 안 됨|  
|any|any|`NULL`|`EINVAL`|`strDest`[0]을 0으로 설정합니다.|  
|any|0|any|`EINVAL`|수정 안 됨|  
|`NULL` 아님|너무 작음|any|`ERANGE`|`strDest`[0]을 0으로 설정합니다.|  
  
## <a name="remarks"></a>설명  
 이러한 함수는 `strSource`의 처음 `D`자를 `strDest`에 복사하려고 합니다. 여기서 `D`는 `count`와 `strSource`의 길이 중 더 작은 값입니다. 이 `D`자를 `strDest`(해당 크기는 `numberOfElements`로 제공됨) 내에 복사한 후에도 null 종결자를 위한 공간이 남으면 해당 문자가 복사되며 종료 null이 추가됩니다. 그렇지 않으면 `strDest`[0]은 null 문자로 설정되고 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다.  
  
 위 단락의 설명에는 예외가 적용됩니다. `count`가 `_TRUNCATE`이면 `strDest`에 포함할 수 있는 만큼의 `strSource`가 복사되며 종료 null(항상 추가됨)을 위한 공간을 남겨 둡니다.  
  
 예를 들어 개체에 적용된  
  
 `char dst[5];`  
  
 `strncpy_s(dst, 5, "a long string", 5);`  
  
 위의 코드는 5바이트 길이의 버퍼에 5자를 복사하도록 `strncpy_s`에 명령함을 의미합니다. 이렇게 하면 null 종결자를 위한 공간이 남지 않으므로, `strncpy_s`는 문자열을 0으로 설정하고 잘못된 매개 변수 처리기를 호출합니다.  
  
 잘라내기 동작 필요한 경우 사용 `_TRUNCATE` 또는 (`size` -1):  
  
 `strncpy_s(dst, 5, "a long string", _TRUNCATE);`  
  
 `strncpy_s(dst, 5, "a long string", 4);`  
  
 `strncpy`와는 달리 `count`가 `strSource`의 길이보다 크면 대상 문자열은 `count` 길이까지는 null 문자로 채워지지 않습니다.  
  
 소스 문자열과 대상 문자열이 겹치는 경우 `strncpy_s`의 동작이 정의되지 않습니다.  
  
 `strDest` 또는 `strSource`가 `NULL`이거나 `numberOfElements`가 0이면 잘못된 매개 변수 처리기가 호출됩니다. 계속해서 실행하도록 허용된 경우 함수가 `EINVAL`를 반환하며 `errno`를 `EINVAL`로 설정합니다.  
  
 `wcsncpy_s` 및 `_mbsncpy_s`는 `strncpy_s`의 와이드 문자 및 멀티바이트 문자 버전입니다. 인수 및 반환 값이 `wcsncpy_s` 및 `mbsncpy_s` 그에 따라 다를 수행 합니다. 그 외의 경우에는 이들 6개 함수가 동일하게 작동합니다.  
  
 출력값은 로캘의 `LC_CTYPE` 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. `_l` 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, `_l` 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.  
  
 C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)을 참조하세요.  
  
 이러한 함수의 디버그 버전은 우선 0xFD로 버퍼를 채웁니다. 이 동작을 사용하지 않으려면 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)를 사용하세요.  
  
### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑  
  
|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsncpy_s`|`strncpy_s`|`_mbsnbcpy_s`|`wcsncpy_s`|  
|`_tcsncpy_s_l`|`_strncpy_s_l`|`_mbsnbcpy_s_l`|`_wcsncpy_s_l`|  
  
> [!NOTE]
>  _strncpy_s_l, `_wcsncpy_s_l` 및 `_mbsncpy_s_l`은 로캘에 종속되지 않습니다. 이러한 함수는 `_tcsncpy_s_l`용으로만 제공되며 직접 호출하면 안 됩니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`strncpy_s`, `_strncpy_s_l`|\<string.h>|  
|`wcsncpy_s`, `_wcsncpy_s_l`|\<string.h> 또는 \<wchar.h>|  
|`_mbsncpy_s`, `_mbsncpy_s_l`|\<mbstring.h>|  
  
 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="example"></a>예  
  
```  
// crt_strncpy_s_1.cpp  
// compile with: /MTd  
  
// these #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
errno_t strncpy_s_tester( const char * src,  
                          int count )  
{  
   char dest[10];  
  
   printf( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf( "Copying '%s' to %d-byte buffer dest with truncation semantics\n",  
               src, _countof(dest) );  
   else  
      printf( "Copying %d chars of '%s' to %d-byte buffer dest\n",  
              count, src, _countof(dest) );  
  
   errno_t err = strncpy_s( dest, _countof(dest), src, count );  
  
   printf( "    new contents of dest: '%s'\n", dest );  
  
   return err;  
}  
  
void Examples()  
{  
   strncpy_s_tester( "howdy", 4 );  
   strncpy_s_tester( "howdy", 5 );  
   strncpy_s_tester( "howdy", 6 );  
  
   printf( "\nDestination buffer too small:\n" );  
   strncpy_s_tester( "Hi there!!", 10 );  
  
   printf( "\nTruncation examples:\n" );  
  
   errno_t err = strncpy_s_tester( "How do you do?", _TRUNCATE );  
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   err = strncpy_s_tester( "Howdy.", _TRUNCATE );  
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   printf( "\nSecure template overload example:\n" );  
  
   char dest[10];  
   strncpy( dest, "very very very long", 15 );  
   // With secure template overloads enabled (see #defines at  
   // top of file), the preceding line is replaced by  
   //    strncpy_s( dest, _countof(dest), "very very very long", 15 );  
   // Instead of causing a buffer overrun, strncpy_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, strncpy would  
   // copy 15 characters and overrun the dest buffer.  
   printf( "    new contents of dest: '%s'\n", dest );  
}  
  
void myInvalidParameterHandler(  
   const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);  
}  
  
int main( void )  
{  
   _invalid_parameter_handler oldHandler, newHandler;  
  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   Examples();  
}  
```  
  
```Output  
Copying 4 chars of 'howdy' to 10-byte buffer dest  
    new contents of dest: 'howd'  
  
Copying 5 chars of 'howdy' to 10-byte buffer dest  
    new contents of dest: 'howdy'  
  
Copying 6 chars of 'howdy' to 10-byte buffer dest  
    new contents of dest: 'howdy'  
  
Destination buffer too small:  
  
Copying 10 chars of 'Hi there!!' to 10-byte buffer dest  
Invalid parameter handler invoked: (L"Buffer is too small" && 0)  
    new contents of dest: ''  
  
Truncation examples:  
  
Copying 'How do you do?' to 10-byte buffer dest with truncation semantics  
    new contents of dest: 'How do yo'  
    truncation did occur  
  
Copying 'Howdy.' to 10-byte buffer dest with truncation semantics  
    new contents of dest: 'Howdy.'  
    truncation did not occur  
  
Secure template overload example:  
Invalid parameter handler invoked: (L"Buffer is too small" && 0)  
    new contents of dest: ''  
```  
  
## <a name="example"></a>예  
  
```  
// crt_strncpy_s_2.c  
// contrasts strncpy and strncpy_s  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char a[20] = "test";  
   char s[20];  
  
   // simple strncpy usage:  
  
   strcpy_s( s, 20, "dogs like cats" );  
   printf( "Original string:\n   '%s'\n", s );  
  
   // Here we can't use strncpy_s since we don't   
   // want null termination  
   strncpy( s, "mice", 4 );  
   printf( "After strncpy (no null-termination):\n   '%s'\n", s );  
   strncpy( s+5, "love", 4 );  
   printf( "After strncpy into middle of string:\n   '%s'\n", s );  
  
   // If we use strncpy_s, the string is terminated   
   strncpy_s( s, _countof(s), "mice", 4 );  
   printf( "After strncpy_s (with null-termination):\n   '%s'\n", s );  
  
}  
```  
  
```Output  
Original string:  
   'dogs like cats'  
After strncpy (no null-termination):  
   'mice like cats'  
After strncpy into middle of string:  
   'mice love cats'  
After strncpy_s (with null-termination):  
   'mice'  
```  
  
## <a name="see-also"></a>참고 항목  
 [문자열 조작](../../c-runtime-library/string-manipulation-crt.md)   
 [로캘](../../c-runtime-library/locale.md)   
 [멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcpy, _mbsnbcpy_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [strcat_s, wcscat_s, _mbscat_s](../../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)   
 [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy_s, wcscpy_s, _mbscpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)