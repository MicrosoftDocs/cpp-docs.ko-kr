---
description: '자세한 정보: wcrtomb'
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: effa442cee4aa0924fa976ee9138f40b22217375
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331060"
---
# <a name="wcrtomb"></a>wcrtomb

와이드 문자를 멀티바이트 문자 표현으로 변환합니다. 이 함수의 더 안전한 버전을 사용할 수 있습니다. [wcrtomb_s](wcrtomb-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>매개 변수

*mbchar*<br/>
멀티바이트로 변환된 결과 문자입니다.

*wchar*<br/>
변환할 와이드 문자입니다.

*mbstate*<br/>
**Mbstate_t** 개체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

변환된 멀티바이트 문자를 표시하는 데 필요한 바이트 수를 반환하고, 오류가 발생하면 -1을 반환합니다.

## <a name="remarks"></a>설명

**Wcrtomb** 함수는 *mbstate* 에 포함 된 지정 된 변환 상태에서 시작 하 여 *wchar* 에 포함 된 값에서 *mbstate* 로 표시 되는 주소로 와이드 문자를 변환 합니다. 반환 값은 해당 멀티 바이트 문자를 나타내는 데 필요한 바이트 수 이지만 **MB_CUR_MAX** 바이트를 초과 하 여 반환 되지 않습니다.

*Mbstate* 가 null 이면 *mbstate* 의 변환 상태를 포함 하는 내부 **mbstate_t** 개체가 사용 됩니다. 문자 시퀀스의 *wchar* 에 해당 하는 멀티 바이트 문자 표현이 없으면-1이 반환 되 고 **Errno** 가 **eilseq** 로 설정 됩니다.

**Wcrtomb** 함수는 다시 시작할에 의해 [_wctomb_l wctomb](wctomb-wctomb-l.md) 와 다릅니다. 동일 하거나 다른 다시 시작 가능 함수에 대 한 후속 호출의 경우 변환 상태가 *mbstate* 에 저장 됩니다. 다시 시작할 수 있는 함수와 다시 시작할 수 없는 함수를 함께 사용할 때는 결과가 정의되지 않습니다. 예를 들어 **wcstombs** 대신 **wcsrtombs** 에 대 한 후속 호출을 사용 하는 경우 응용 프로그램은 **wcsnlen** 대신 **wcsrlen** 을 사용 합니다.

C++에서 이 함수는 해당 최신 보안 버전을 호출하는 템플릿 오버로드를 포함합니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="exceptions"></a>예외

**Wcrtomb** 함수는이 함수가 실행 되는 동안, 그리고 *mbstate* 가 null 인 동안 현재 스레드의 함수가 **setlocale** 을 호출 하지 않는 한 다중 스레드 안전을 보장 합니다.

## <a name="example"></a>예제

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
