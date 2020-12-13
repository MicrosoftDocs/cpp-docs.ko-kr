---
description: '자세히 알아보기: wcsrtombs'
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: 34fabe44c0e239eba4201b180df026655a4277f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340514"
---
# <a name="wcsrtombs"></a>wcsrtombs

와이드 문자열을 멀티바이트 문자열 표현으로 변환합니다. 이 함수의 더 안전한 버전을 사용할 수 있습니다. [wcsrtombs_s](wcsrtombs-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>매개 변수

*mbstr*<br/>
변환된 결과 멀티바이트 문자열의 주소 위치입니다.

*wcstr*<br/>
변환할 와이드 문자열의 위치를 간접적으로 가리킵니다.

*count*<br/>
변환할 문자의 수입니다.

*mbstate*<br/>
**Mbstate_t** 변환 상태 개체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

정상적으로 변환된 바이트의 수를 반환합니다. null 종결 null 바이트(있는 경우)는 포함되지 않습니다. 오류가 발생하면 -1을 반환합니다.

## <a name="remarks"></a>설명

**Wcsrtombs** 함수는 *mbstate* 에 포함 된 지정 된 변환 상태에서 시작 하는 와이드 문자의 문자열을 *wcstr* 의 간접 가리키는 값에서 *mbstate* 의 주소로 변환 합니다. Null 종결 와이드 문자가 발생 한 후, 해당 문자가 없거나 다음 문자가 *개수* 에 포함 된 제한을 초과 하는 경우에는 각 문자에 대해 변환이 계속 됩니다. **Wcsrtombs** 가 발생 하기 전이나 후에 와이드 문자 null 문자 (L ' \ 0 ')를 발견 *하면이* 를 8 비트 0으로 변환 하 고 중지 합니다.

따라서 *mbstr* 의 멀티 바이트 문자열은 변환 하는 동안 **wcsrtombs** 가 와이드 문자 null 문자를 발견 하는 경우에만 null로 종결 됩니다. *Wcstr* 및 *mbstr* 가 가리키는 시퀀스가 겹치면 **wcsrtombs** 의 동작이 정의 되지 않습니다. **wcsrtombs** 은 현재 로캘의 LC_TYPE 범주에 의해 영향을 받습니다.

**Wcsrtombs** 함수는 다시 시작할에 의해 [_wcstombs_l wcstombs](wcstombs-wcstombs-l.md) 와 다릅니다. 동일 하거나 다른 다시 시작 가능 함수에 대 한 후속 호출의 경우 변환 상태가 *mbstate* 에 저장 됩니다. 다시 시작할 수 있는 함수와 다시 시작할 수 없는 함수를 함께 사용할 때는 결과가 정의되지 않습니다.  예를 들어 **wcstombs** 대신 **wcsrtombs** 에 대 한 후속 호출을 사용 하는 경우 응용 프로그램은 **wcsnlen** 대신 **wcsrlen** 을 사용 합니다.

*Mbstr* 인수가 **NULL** 이면 **wcsrtombs** 는 대상 문자열의 필요한 크기 (바이트)를 반환 합니다. *Mbstate* 가 null 이면 내부 **mbstate_t** 변환 상태가 사용 됩니다. 문자 시퀀스의 *wchar* 에 해당 하는 멀티 바이트 문자 표현이 없으면-1이 반환 되 고 **Errno** 가 **eilseq** 로 설정 됩니다.

C++에서 이 함수는 해당 최신 보안 버전을 호출하는 템플릿 오버로드를 포함합니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="exceptions"></a>예외

**Wcsrtombs** 함수는 현재 스레드의 함수가 **setlocale** 을 호출 하 고이 함수가 실행 되 고 *mbstate* 가 null이 아닌 경우 다중 스레드 안전 합니다.

## <a name="example"></a>예제

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
