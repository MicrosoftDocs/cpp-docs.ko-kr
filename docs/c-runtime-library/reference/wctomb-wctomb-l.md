---
description: Wctomb, _wctomb_l에 대해 자세히 알아보세요.
title: wctomb, _wctomb_l
ms.date: 4/2/2020
api_name:
- _wctomb_l
- wctomb
- _o__wctomb_l
- _o_wctomb
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: f49915d062aa602ab361084cbcc7a9a034599de2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136814"
---
# <a name="wctomb-_wctomb_l"></a>wctomb, _wctomb_l

와이드 문자를 해당 멀티바이트 문자로 변환합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*mbchar*<br/>
멀티바이트 문자의 주소입니다.

*wchar*<br/>
와이드 문자입니다.

## <a name="return-value"></a>반환 값

**Wctomb** 는 와이드 문자를 멀티 바이트 문자로 변환 하는 경우 와이드 문자의 바이트 수 ( **MB_CUR_MAX** 보다 크지 않음)를 반환 합니다. *Wchar* 가 와이드 문자 null 문자 (L ' \ 0 ') 이면 **wctomb** 는 1을 반환 합니다. 대상 포인터 *mbchar* 가 **NULL** 인 경우 **wctomb** 는 0을 반환 합니다. 현재 로캘에서 변환할 수 없는 경우 **wctomb** 는-1을 반환 하 고 **Errno** 는 **eilseq** 로 설정 됩니다.

## <a name="remarks"></a>설명

**Wctomb** 함수는 *wchar* 인수를 해당 멀티 바이트 문자로 변환 하 고 결과를 *mbchar* 에 저장 합니다. 모든 프로그램에서 언제든지 이 함수를 호출할 수 있습니다. **wctomb** 는 로캘 종속 동작에 대해 현재 로캘을 사용 합니다. **_wctomb_l** 은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고 **wctomb** 와 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

**wctomb** 은 매개 변수의 유효성을 검사 합니다. *Mbchar* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는-1을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 프로그램은 wctomb 함수의 동작을 보여 줍니다.

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
