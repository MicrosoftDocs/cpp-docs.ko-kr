---
description: Strcmp, wcscmp, _mbscmp, _mbscmp_l에 대해 자세히 알아보세요.
title: strcmp, wcscmp, _mbscmp, _mbscmp_l
ms.date: 4/2/2020
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
- _o__mbscmp
- _o__mbscmp_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 0c611b92b39d04e455bbd31f22f98898723ff7c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306159"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

비교 문자열입니다.

> [!IMPORTANT]
> **_mbscmp** 및 **_mbscmp_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*string1*, *문자열 2*<br/>
비교할 Null 종료 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수에 대 한 반환 값은 *문자열* 1에서 *문자열 2* 로의 서 수 관계를 나타냅니다.

|값|문자열 1과 문자열 2의 관계|
|-----------|----------------------------------------|
|< 0|*string1* 이 *문자열 2* 보다 작음|
|0|*string1* 은 *문자열 2* 와 동일 합니다.|
|> 0|*string1* 이 *문자열 2* 보다 큽니다.|

매개 변수 유효성 검사 오류 시 및에 정의 된 **_NLSCMPERROR** 를 반환 하 **_mbscmp_l** **_mbscmp** \<string.h> \<mbstring.h> 합니다.

## <a name="remarks"></a>설명

**Strcmp** 함수는 *문자열* 1과 *문자열 2* 의 서 수 비교를 수행 하 고 해당 관계를 나타내는 값을 반환 합니다. **wcscmp** 및 **_mbscmp** 는 각각 **strcmp** 의 와이드 문자 및 멀티 바이트 문자 버전입니다. **_mbscmp** 는 현재 멀티 바이트 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 하 고 오류 발생 시 **_NLSCMPERROR** 을 반환 합니다. **_mbscmp_l** 는 동일한 동작을 갖지만 현재 로캘 대신 전달 된 로캘 매개 변수를 사용 합니다. 자세한 내용은 [코드 페이지](../../c-runtime-library/code-pages.md) 참조하세요. 또한 *string1* 또는 *문자열* 1이 Null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 **_mbscmp** . 계속 해 서 실행 하도록 허용한 경우 **_mbscmp** 하  고 _mbscmp_l **_NLSCMPERROR** 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다. **strcmp** 및 **wcscmp** 는 해당 매개 변수의 유효성을 검사 하지 않습니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

**Strcmp** 함수는 **strcoll** 함수와 다르며, **strcmp** 비교는 서 수 이며 로캘의 영향을 받지 않습니다. **strcoll** 는 현재 로캘의 **LC_COLLATE** 범주를 사용 하 여 사전순으로 문자열을 비교 합니다. **LC_COLLATE** 범주에 대 한 자세한 내용은 [setlocale, _wsetlocale](setlocale-wsetlocale.md)를 참조 하세요.

"C" 로캘에서 문자 집합(ASCII 문자 집합)의 순서는 사전적 문자 순서와 같습니다. 그러나 다른 로캘에서 문자 집합의 순서는 사전적 순서와 다를 수 있습니다. 예를 들어 특정 유럽 로캘의 문자 집합에서 문자 'a'(값 0x61)는 문자 'ä'(값 0xE4) 앞에 오지만 사전적으로는 문자 'ä'가 'a' 앞에 옵니다.

문자 집합과 사전적 문자 순서가 다른 로캘에서는 **strcmp** 대신 **strcoll** 를 사용 하 여 문자열을 사전적로 비교할 수 있습니다. 또는 원본 문자열에서 **strxfrm** 를 사용한 다음 결과 문자열에 **strcmp** 를 사용할 수 있습니다.

**Strcmp** 함수는 대/소문자를 구분 합니다. **\_ stricmp**, **\_ wcsicmp** 및 **\_ mbsicmp** 는 먼저 문자열을 소문자 형식으로 변환 하 여 문자열을 비교 합니다. ASCII 테이블의 ' Z '와 ' a ' 사이에 있는 문자 (' [', ' \\ ', '] ', ' ^ ', ' _ ' 및 ' ')를 포함 하는 두 문자열은 \` 대/소문자에 따라 서로 다른 방식으로 비교 됩니다. 예를 들어 두 문자열 "ABCDE...Z" 및 "ABCD ^"는 비교가 소문자 ("abcde...z" > "abcd ^") 인 경우와 다른 방법 ("ABCDE...Z" < "ABCD ^")을 비교 하는 경우 한 가지 방법을 비교 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> 또는 \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_strcmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
