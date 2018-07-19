---
title: strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbslen
- _mbslen_l
- _mbstrlen
- wcslen
- _mbstrlen_l
- strlen
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
- _mbstrlen
- wcslen
- _tcslen
- _ftcslen
- strlen
- _mbslen
dev_langs:
- C++
helpviewer_keywords:
- wcslen function
- string length, getting
- ftcslen function
- lengths, strings
- mbstrlen_l function
- _mbslen_l function
- _tcslen function
- mbslen_l function
- mbslen function
- _mbstrlen function
- strings [C++], getting length
- mbstrlen function
- _mbstrlen_l function
- _ftcslen function
- tcslen function
- strlen function
- _mbslen function
ms.assetid: 16462f2a-1e0f-4eb3-be55-bf1c83f374c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35885dfb6a7432796688e35032e06d0aec863687
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451591"
---
# <a name="strlen-wcslen-mbslen-mbslenl-mbstrlen-mbstrlenl"></a>strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l

현재 로캘 또는 지정된 로캘을 사용하여 문자열의 길이를 가져옵니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l](strnlen-strnlen-s.md)을 참조하세요.

> [!IMPORTANT]
> **_mbslen**, **_mbslen_l**, **_mbstrlen**, 및 **_mbstrlen_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
size_t strlen(
   const char *str
);
size_t wcslen(
   const wchar_t *str
);
size_t _mbslen(
   const unsigned char *str
);
size_t _mbslen_l(
   const unsigned char *str,
   _locale_t locale
);
size_t _mbstrlen(
   const char *str
);
size_t _mbstrlen_l(
   const char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
Null 종료 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수에 있는 문자의 수를 반환 *str*, 터미널 null을 제외 합니다. 반환 값 없음은 제외 하 고 오류를 나타내는 데 예약 되어 **_mbstrlen** 및 **_mbstrlen_l**를 반환 하는 `((size_t)(-1))` 문자열에 잘못 된 멀티 바이트 문자가 포함 되어 있습니다.

## <a name="remarks"></a>설명

**strlen** 단일 바이트 문자 문자열로 문자열을 해석 하므로 문자열 멀티 바이트 문자를 포함 하는 경우에 해당 반환 값은 항상 바이트의 수와 같습니다. **wcslen** 의 와이드 문자 버전이 **strlen**;의 인수 **wcslen** 는 와이드 문자열이 고 문자 수는 와이드 (2 바이트) 문자로 계산 합니다. **wcslen** 및 **strlen** 동일 하 게 작동 합니다.

**보안 정보** 이러한 함수는 버퍼 오버런 문제로 인해 발생하는 잠재적인 위협을 일으킵니다. 버퍼 오버런 문제는 자주 사용되는 시스템 공격 방법으로, 불필요한 권한 상승을 초래합니다. 자세한 내용은 [버퍼 오버런 방지](http://msdn.microsoft.com/library/windows/desktop/ms717795)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslen**|**strlen**|**strlen**|**wcslen**|
|**_tcsclen**|**strlen**|**_mbslen**|**wcslen**|
|**_tcsclen_l**|**strlen**|**_mbslen_l**|**wcslen**|

**_mbslen** 및 **_mbslen_l** 멀티 바이트 문자열의 멀티 바이트 문자 수를 반환 하지만 멀티 바이트 문자의 유효성을 테스트 하지는 않습니다. **_mbstrlen** 및 **_mbstrlen_l** 멀티 바이트 문자의 유효성을 테스트 하 고 멀티 바이트 문자 시퀀스를 인식 합니다. 에 전달 된 문자열이 **_mbstrlen** 또는 **_mbstrlen_l** 에 잘못 된 문자가 멀티 바이트 코드 페이지, 함수 반환 값-1 및 집합에 대 한 **errno** 를**EILSEQ**합니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따른 영향을 받습니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요. **_l** 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**strlen**|\<string.h>|
|**wcslen**|\<string.h> 또는 \<wchar.h>|
|**_mbslen**, **_mbslen_l**|\<mbstring.h>|
|**_mbstrlen**, **_mbstrlen_l**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strlen.c
// Determine the length of a string. For the multi-byte character
// example to work correctly, the Japanese language support for
// non-Unicode programs must be enabled by the operating system.

#include <string.h>
#include <locale.h>

int main()
{
   char* str1 = "Count.";
   wchar_t* wstr1 = L"Count.";
   char * mbstr1;
   char * locale_string;

   // strlen gives the length of single-byte character string
   printf("Length of '%s' : %d\n", str1, strlen(str1) );

   // wstrlen gives the length of a wide character string
   wprintf(L"Length of '%s' : %d\n", wstr1, wcslen(wstr1) );

   // A multibyte string: [A] [B] [C] [katakana A] [D] [\0]
   // in Code Page 932. For this example to work correctly,
   // the Japanese language support must be enabled by the
   // operating system.
   mbstr1 = "ABC" "\x83\x40" "D";

   locale_string = setlocale(LC_CTYPE, "Japanese_Japan");

   if (locale_string == NULL)
   {
      printf("Japanese locale not enabled. Exiting.\n");
      exit(1);
   }
   else
   {
      printf("Locale set to %s\n", locale_string);
   }

   // _mbslen will recognize the Japanese multibyte character if the
   // current locale used by the operating system is Japanese
   printf("Length of '%s' : %d\n", mbstr1, _mbslen(mbstr1) );

   // _mbstrlen will recognize the Japanese multibyte character
   // since the CRT locale is set to Japanese even if the OS locale
   // isnot.
   printf("Length of '%s' : %d\n", mbstr1, _mbstrlen(mbstr1) );
   printf("Bytes in '%s' : %d\n", mbstr1, strlen(mbstr1) );

}
```

```Output
Length of 'Count.' : 6
Length of 'Count.' : 6
Length of 'ABCァD' : 5
Length of 'ABCァD' : 5
Bytes in 'ABCァD' : 6
```

## <a name="see-also"></a>참고자료

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
