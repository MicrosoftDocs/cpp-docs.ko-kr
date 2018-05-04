---
title: wctomb_s, _wctomb_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wctomb_s_l
- wctomb_s
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
apitype: DLLExport
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs:
- C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb0a44414b01d0105f911732bc3dd2662a278158
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l

와이드 문자를 해당 멀티바이트 문자로 변환합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [wctomb, _wctomb_l](wctomb-wctomb-l.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*pRetValue*<br/>
결과를 나타내는 코드 또는 바이트 수입니다.

*mbchar*<br/>
멀티바이트 문자의 주소입니다.

*sizeInBytes*<br/>
버퍼의 크기 *mbchar*합니다.

*wchar*<br/>
와이드 문자입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

성공시 0, 실패시 오류 코드.

오류 조건

|*mbchar*|*sizeInBytes*|반환 값|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|수정 안 됨|
|모두|>**INT_MAX**|**EINVAL**|수정 안 됨|
|모두|너무 작음|**EINVAL**|수정 안 됨|

위의 오류 조건 중 하나라도 발생하는 경우, [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 실행을 계속 하도록 허용 된 경우 **wctomb** 반환 **EINVAL** 설정 **errno** 를 **EINVAL**합니다.

## <a name="remarks"></a>설명

**wctomb_s** 변환 함수는 *wchar* 인수를 해당 멀티 바이트 문자로에서 결과 저장 하 고 *mbchar*합니다. 모든 프로그램에서 언제든지 이 함수를 호출할 수 있습니다.

경우 **wctomb_s** 와이드 문자 변환 가져가서 바이트 수는 멀티 바이트 문자 (보다 큰는 **MB_CUR_MAX**) 가리키는정수를와이드문자로*pRetValue*합니다. 경우 *wchar* 와이드 null 문자 (L'\ \0')은 **wctomb_s** 채웁니다 *pRetValue* 1입니다. 하는 경우 대상 포인터 *mbchar* 이 NULL 이면 **wctomb_s** 0에 배치 *pRetValue*합니다. 현재 로캘 변환이 가져올 수 없으면 **wctomb_s** 에-1을 넣습니다 *pRetValue*합니다.

**wctomb_s** 로캘 종속 정보에 대 한 현재 로캘을 사용 **_wctomb_s_l** 대신 전달 된 로캘을 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 프로그램의 동작을 보여 줍니다.는 **wctomb** 함수입니다.

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>참고자료

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
