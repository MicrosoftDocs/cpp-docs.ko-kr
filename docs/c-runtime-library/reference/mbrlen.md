---
description: '자세한 정보: mbrlen'
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 1a485090c056cb1e5f075bfd226ac7d4717ec0ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336493"
---
# <a name="mbrlen"></a>mbrlen

현재 로캘에서 멀티바이트 문자열을 완성하는 데 필요한 바이트 수를 결정합니다. 이때 멀티바이트 문자의 중간에서 다시 시작할 수 있습니다.

## <a name="syntax"></a>구문

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
멀티바이트 문자열에서 검사할 다음 바이트에 대한 포인터입니다.

*count*<br/>
검사할 최대 바이트 수입니다.

*mbstate*<br/>
*Str* 의 초기 바이트의 현재 이동 상태에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

다음 값 중 하나입니다.

| 값 | 설명 |
|--|--|
| 0 | 다음 *개수* 이하의 바이트가 와이드 null 문자를 나타내는 멀티 바이트 문자를 완성 합니다. |
| 1- *개수*, 포함 | 다음 *개수* 이하의 바이트가 올바른 멀티 바이트 문자를 완성 합니다. 반환되는 값은 멀티바이트 문자를 완성하는 바이트 수입니다. |
| (size_t)(-2) | 다음 *카운트* 바이트는 불완전 하지만 잠재적으로 유효한 멀티 바이트 문자에 영향을 주지만 모든 바이트 *수가* 처리 되었습니다. |
| (size_t)(-1) | 인코딩 오류가 발생했습니다. 다음 *개수* 이하의 바이트는 완전 하 고 유효한 멀티 바이트 문자에 영향을 주지 않습니다. 이 경우 **errno** 는 EILSEQ로 설정 되 고 *mbstate* 의 변환 상태는 지정 되지 않습니다. |

## <a name="remarks"></a>설명

**Mbrlen** 함수는 모든 이동 시퀀스를 포함 하 여 다음 멀티 바이트 문자를 완료 하는 데 필요한 바이트 수를 결정 하기 위해 *str* 가 가리키는 바이트로 시작 하는 최대 *개수* 바이트를 검사 합니다. `mbrtowc(NULL, str, count, &mbstate)` *Mbstate* 가 사용자 제공 **mbstate_t** 개체 이거나 라이브러리에서 제공 되는 정적 내부 개체 인 호출과 동일 합니다.

**Mbrlen** 함수는 *mbstate* 매개 변수에서 불완전 한 멀티 바이트 문자의 이동 상태를 저장 하 고 사용 합니다. 이를 통해 **mbrlen** 은 필요한 경우 멀티 바이트 문자 중간에서 다시 시작 하 여 최대 *카운트* 바이트를 검사 하는 기능을 제공 합니다. *Mbstate* 가 null 포인터인 경우 **mbrlen** 은 내부 정적 **mbstate_t** 개체를 사용 하 여 이동 상태를 저장 합니다. 내부 **mbstate_t** 개체는 스레드로부터 안전 하지 않으므로 항상 고유한 *mbstate* 매개 변수를 할당 하 고 전달 하는 것이 좋습니다.

**Mbrlen** 함수는 다시 시작할에 의해 [_mblen_l _mbclen mblen](mbclen-mblen-mblen-l.md) 다릅니다. 동일 하거나 다른 다시 시작 가능 함수에 대 한 후속 호출의 경우 이동 상태가 *mbstate* 에 저장 됩니다. 다시 시작할 수 있는 함수와 다시 시작할 수 없는 함수를 함께 사용할 때는 결과가 정의되지 않습니다.  예를 들어 **wcstombs** 대신 **wcsrtombs** 에 대 한 후속 호출을 사용 하는 경우 응용 프로그램은 **wcslen** 대신 **wcsrlen** 을 사용 해야 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|적용할 수 없음|적용할 수 없음|**mbrlen**|적용할 수 없음|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 예제에서는 멀티 바이트 문자의 해석이 현재 코드 페이지에 따라 달라 지는 방법과 **mbrlen** 의 다시 시작 기능을 보여 줍니다.

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
