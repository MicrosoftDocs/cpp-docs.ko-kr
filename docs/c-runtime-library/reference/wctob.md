---
description: '자세히 알아보기: wctob'
title: wctob
ms.date: 4/2/2020
api_name:
- wctob
- _o_wctob
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 184c9858aebcdecf3b5d9857980f27be45a5d2d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136867"
---
# <a name="wctob"></a>wctob

와이드 문자가 멀티바이트 문자에 해당하는지 확인하고 해당 멀티바이트 문자 표현을 반환합니다.

## <a name="syntax"></a>구문

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>매개 변수

*wchar*<br/>
변환할 값입니다.

## <a name="return-value"></a>반환 값

**Wctob** 가 와이드 문자를 성공적으로 변환 하는 경우 멀티 바이트 문자의 길이가 정확히 1 바이트 인 경우에만 멀티 바이트 문자 표현을 반환 합니다. **Wctob** 가 멀티 바이트 문자로 변환할 수 없는 와이드 문자를 발견 하거나 멀티 바이트 문자의 길이가 정확히 1 바이트는 아닌 경우-1을 반환 합니다.

## <a name="remarks"></a>설명

**Wctob** 함수는  **`int`** 멀티 바이트 문자의 길이가 정확히 1 바이트 이면 wchar에 포함 된 와이드 문자를 반환 값으로 전달 된 해당 멀티 바이트 문자로 변환 합니다.

**Wctob** 이 실패 하 고 해당 하는 멀티 바이트 문자를 찾을 수 없는 경우 함수는 **Errno** 를 **eilseq** 로 설정 하 고-1을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 프로그램은 **wcstombs** 함수의 동작을 보여 줍니다.

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
