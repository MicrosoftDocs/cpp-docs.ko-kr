---
description: Strncmp, wcsncmp, _mbsncmp, _mbsncmp_l에 대해 자세히 알아보세요.
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 4/2/2020
api_name:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
- _o__mbsncmp
- _o__mbsncmp_l
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
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
ms.openlocfilehash: 91f7351f844425369ccae4bba6d13d177e75910f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344759"
---
# <a name="strncmp-wcsncmp-_mbsncmp-_mbsncmp_l"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

두 문자열의 문자를 지정한 수까지 비교합니다.

> [!IMPORTANT]
> **_mbsncmp** 및 **_mbsncmp_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>매개 변수

*string1*, *문자열 2*<br/>
비교할 문자열입니다.

*count*<br/>
비교할 문자 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

반환 값은 다음과 *같이 문자열 1과 문자열* *2* 의 부분 문자열 관계를 나타냅니다.

|반환 값|설명|
|------------------|-----------------|
|< 0|문자열 *1 부분 문자열이 문자열이 아닌 부분 문자열* *보다 작음*|
|0|*문자열이 아닌 하위 문자열은* *문자열이 아닌 부분 문자열과 같습니다* .|
|> 0|*문자열이 아닌 부분* 문자열이 *문자열 문자열의 하위 문자열 보다 큽니다* .|

매개 변수 유효성 검사 오류 시 및에 정의 된 **_NLSCMPERROR** 를 반환 하 **_mbsncmp_l** **_mbsncmp** \<string.h> \<mbstring.h> 합니다.

## <a name="remarks"></a>설명

**Strncmp** 함수 *는 문자열 1과* *문자열 2* 의 최대 처음 *개수* 문자 수에 대 한 서 수 비교를 수행 하 고 부분 문자열 간의 관계를 나타내는 값을 반환 합니다. **strncmp** 은 대/소문자를 구분 하는 **_strnicmp** 버전입니다. **wcsncmp** 및 **_mbsncmp** 는 대/소문자를 구분 하는 **_wcsnicmp** 및 **_mbsnicmp** 버전입니다.

**wcsncmp** 및 **_mbsncmp** 는 **strncmp** 의 와이드 문자 및 멀티 바이트 문자 버전입니다. **Wcsncmp** 의 인수는 와이드 문자 문자열입니다. **_mbsncmp** 의 이러한 문자열은 멀티 바이트 문자열입니다. **_mbsncmp** 멀티 바이트 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 하 고 오류 발생 시 **_NLSCMPERROR** 을 반환 합니다.

또한 **_mbsncmp** 및 **_mbsncmp_l** 매개 변수 유효성 검사를 수행 합니다. *String1 또는 string1* 이 null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 *처리기가 호출* 됩니다. 계속 해 서 실행 하도록 허용한 경우 **_mbsncmp** 하  고 _mbsncmp_l **_NLSCMPERROR** 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다. **strncmp** 및 **wcsncmp** 는 해당 매개 변수의 유효성을 검사 하지 않습니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

**_Mbsncmp** 및 **_mbsncmp_l** 의 비교 동작은 로캘의 **LC_CTYPE** 범주 설정에 따라 영향을 받습니다. 이 설정은 멀티바이트 문자의 선행 및 후행 바이트 검색을 제어합니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요. **_Mbsncmp** 함수는이 로캘 종속 동작에 현재 로캘을 사용 합니다. **_Mbsncmp_l** 함수는 *로캘* 매개 변수를 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요. 로캘이 싱글바이트 로캘의 경우 이러한 함수의 동작은 **strncmp** 와 동일 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|매크로 또는 인라인 함수에 매핑|**_mbsncmp**|매크로 또는 인라인 함수에 매핑|
|**해당 없음**|**해당 없음**|**_mbsncmp_l**|**해당 없음**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp**|\<string.h> 또는 \<wchar.h>|
|**_mbsncmp**, **_mbsncmp_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
