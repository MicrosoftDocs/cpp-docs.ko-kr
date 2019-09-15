---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 11/04/2016
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
ms.openlocfilehash: 108a3c572174be5048d0bba48a4da0f4a735f458
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940688"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

대소문자를 구분하지 않는 문자열 비교를 수행합니다.

> [!IMPORTANT]
> **_mbsicmp** 및 **_mbsicmp_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*string1*, *string2*<br/>
비교할 Null 종료 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

반환 값은 다음과 같이 *문자열* 1과 *문자열 2* 의 관계를 나타냅니다.

|반환 값|설명|
|------------------|-----------------|
|< 0|*문자열* *2* 보다 작음|
|0|*문자열* *2* 와 같음|
|> 0|*문자열* *2* 보다 큼|

오류가 발생 하면 **_mbsicmp** 는 _NLSCMPERROR > 및 \<mbstring >에 \<정의 된를 반환 합니다.

## <a name="remarks"></a>설명

**_Stricmp** 함수 서 수로는 각 문자를 소문자로 변환한 후 *string1* 과 *문자열* 을 비교 하 고 해당 관계를 나타내는 값을 반환 합니다. **_stricmp** 는 **_stricoll** 와 다릅니다. **_stricmp** 비교는 대문자 및 소문자를 결정 하는 **LC_CTYPE**의 영향을 받습니다. **_Stricoll** 함수는 로캘의 **LC_CTYPE** 및 **LC_COLLATE** 범주 모두에 따라 문자열을 비교 합니다. 여기에는 대/소문자와 데이터 정렬 순서가 모두 포함 됩니다. **LC_COLLATE** 범주에 대 한 자세한 내용은 [Setlocale](setlocale-wsetlocale.md) 및 [로캘 범주](../../c-runtime-library/locale-categories.md)를 참조 하세요. **_L** 접미사가 없는 이러한 함수 버전은 로캘 종속 동작에 현재 로캘을 사용 합니다. 접미사가 있는 버전은 전달된 로캘을 사용한다는 점만 제외하면 동일합니다. 로캘이 설정되지 않은 경우에는 C 로캘이 사용됩니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

> [!NOTE]
> **_stricmp** 는 **_strcmpi**와 동일 합니다. 이러한 두 용어는 서로 바꿔 사용할 수 있지만 **_stricmp** 는 기본 설정 표준입니다.

**_Strcmpi** 함수는 **_stricmp** 에 해당 하며 이전 버전과의 호환성을 위해서만 제공 됩니다.

**_Stricmp** 는 소문자 비교를 수행 하므로 예기치 않은 동작이 발생할 수 있습니다.

**_Stricmp** 에의 한 대/소문자 변환이 비교 결과에 영향을 주는 경우를 설명 하기 위해 JOHNSTON 및 JOHN_HENRY 라는 두 문자열이 있다고 가정 합니다. JOHN_HENRY 문자열은 "_"의 ASCII 값이 소문자 S보다 작기 때문에 JOHNSTON보다 작은 것으로 간주됩니다. 실제로 ASCII 값이 91~96인 문자는 모든 문자보다 작은 것으로 간주됩니다.

**_Stricmp**대신 [strcmp](strcmp-wcscmp-mbscmp.md) 함수를 사용 하는 경우 JOHN_HENRY는 JOHNSTON 보다 큽니다.

**_wcsicmp** 및 **_mbsicmp** 는 **_stricmp**의 와이드 문자 및 멀티 바이트 문자 버전입니다. **_Wcsicmp** 의 인수 및 반환 값은 와이드 문자 문자열입니다. **_mbsicmp** 의 해당 문자는 멀티 바이트 문자열입니다. **_mbsicmp** 는 현재 멀티 바이트 코드 페이지에 따라 멀티 바이트 문자 시퀀스를 인식 하 고 오류 발생 시 **_NLSCMPERROR** 을 반환 합니다. 자세한 내용은 [코드 페이지](../../c-runtime-library/code-pages.md) 참조하세요. 그렇지 않으면 이들 세 함수는 동일하게 작동합니다.

**_wcsicmp** 및 **wcscmp** 는 비교 하기 전에 **wcscmp** 가 인수를 소문자로 변환 하지 않는다는 점을 제외 하 고 동일 하 게 동작 합니다. **_mbsicmp** 및 **_mbscmp** 는 비교 하기 전에 **_mbscmp** 에서 인수를 소문자로 변환 하지 않는다는 점을 제외 하 고 동일 하 게 동작 합니다.

라틴어 1 문자를 사용 하려면 **_wcsicmp** 에 대해 [setlocale](setlocale-wsetlocale.md) 을 호출 해야 합니다. 기본적으로는 C 로캘이 적용되므로 예를 들어 ä와 Ä는 비교 시 같은 항목으로 간주되지 않습니다. **_Wcsicmp**를 호출 하기 전에 C 로캘 이외의 로캘로 **setlocale** 을 호출 합니다. 다음 샘플에서는 **_wcsicmp** 가 로캘로 구분 되는 방법을 보여 줍니다.

```C
// crt_stricmp_locale.c
#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

대안을 호출 하는 것은 [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) 를 호출 하 고 반환 된 로캘 개체를 매개 변수로 **_wcsicmp_l**에 전달 하는 것입니다.

이러한 모든 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *String1* 또는 *문자열* 1이 Null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **_NLSCMPERROR** 를 반환 하 고 **errno** 를 **EINVAL**로 설정 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_stricmp**, **_stricmp_l**|\<string.h>|
|**_wcsicmp**, **_wcsicmp_l**|\<string.h> 또는 \<wchar.h>|
|**_mbsicmp**, **_mbsicmp_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_stricmp.c

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
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
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

## <a name="see-also"></a>참고자료

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
