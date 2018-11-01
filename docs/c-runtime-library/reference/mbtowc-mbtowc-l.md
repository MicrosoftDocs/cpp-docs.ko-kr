---
title: mbtowc, _mbtowc_l
ms.date: 11/04/2016
apiname:
- mbtowc
- _mbtowc_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbtowc
helpviewer_keywords:
- mbtowc function
- _mbtowc_l function
- mbtowc_l function
ms.assetid: dfd1c8a7-e73a-4307-9353-53b70b45d4d1
ms.openlocfilehash: e5ef6db0f0986b102214229155e1c43c5d029284
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506199"
---
# <a name="mbtowc-mbtowcl"></a>mbtowc, _mbtowc_l

멀티바이트 문자를 해당되는 와이드 문자로 변환합니다.

## <a name="syntax"></a>구문

```C
int mbtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count
);
int _mbtowc_l(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*wchar*<br/>
와이드 문자의 주소입니다 (형식 **wchar_t**).

*mbchar*<br/>
바이트 시퀀스(멀티바이트 문자)의 주소입니다.

*count*<br/>
검사할 바이트 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

하는 경우 **mbchar** 아닙니다 **NULL** 경우에 개체는 *mbchar* forms 유효한 멀티 바이트 문자를 가리키는 **mbtowc** 길이 반환 합니다. 멀티 바이트 문자의 바이트입니다. 하는 경우 *mbchar* 됩니다 **NULL** 또는 가리키는 개체가 와이드 문자 null 문자 (L'\ \0'), 함수가 0을 반환 합니다. 하는 경우 개체는 *mbchar* 가리키는 첫 번째 내에서 유효한 멀티 바이트 문자를 구성 하지 않는 *개수* 문자를-1을 반환 합니다.

## <a name="remarks"></a>설명

합니다 **mbtowc** 변환 함수 *개수* 가리키는 바이트 *mbchar*이면 *mbchar* 아닙니다 **NULL**를 해당 와이드 문자로 합니다. **mbtowc** 결과 와이드 문자를 저장 *wchar* 하는 경우 *wchar* 아닙니다 **NULL**합니다. **mbtowc** 검사 하지 않습니다 둘 **MB_CUR_MAX** 바이트입니다. **mbtowc** 로캘 종속 동작에 현재 로캘을 사용 **_mbtowc_l** 대신 전달 된 로캘을 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**mbtowc**|\<stdlib.h>|
|**_mbtowc_l**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_mbtowc.c
// Illustrates the behavior of the mbtowc function

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc    = (char *)malloc( sizeof( char ) );
    wchar_t  wc      = L'a';
    wchar_t *pwcnull = NULL;
    wchar_t *pwc     = (wchar_t *)malloc( sizeof( wchar_t ) );
    printf( "Convert a wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "  Characters converted: %u\n", i );
    printf( "  Multibyte character: %x\n\n", *pmbc );

    printf( "Convert multibyte character back to a wide "
            "character:\n" );
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
    printf( "   Wide character: %x\n\n", *pwc );
    printf( "Attempt to convert when target is NULL\n" );
    printf( "   returns the length of the multibyte character:\n" );
    i = mbtowc( pwcnull, pmbc, MB_CUR_MAX );
    printf( "   Length of multibyte character: %u\n\n", i );

    printf( "Attempt to convert a NULL pointer to a" );
    printf( " wide character:\n" );
    pmbc = NULL;
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
}
```

```Output
Convert a wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Convert multibyte character back to a wide character:
   Bytes converted: 1
   Wide character: 61

Attempt to convert when target is NULL
   returns the length of the multibyte character:
   Length of multibyte character: 1

Attempt to convert a NULL pointer to a wide character:
   Bytes converted: 0
```

## <a name="see-also"></a>참고자료

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
