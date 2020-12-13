---
description: '다음에 대 한 자세한 정보: wcsrtombs_s'
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 4a25be8bf1c61fec10c54a4ecdb870a383b31e9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340530"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

와이드 문자열을 멀티바이트 문자열 표현으로 변환합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [wcsrtombs](wcsrtombs.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>매개 변수

*pReturnValue*<br/>
Null 종결자를 포함 하 여 변환 된 문자열의 크기 (바이트)입니다.

*mbstr*<br/>
결과 변환된 멀티바이트 문자열에 대한 버퍼 주소입니다.

*sizeInBytes*<br/>
*Mbstr* 버퍼의 크기 (바이트)입니다.

*wcstr*<br/>
변환할 와이드 문자열을 가리킵니다.

*count*<br/>
*Mbstr* 버퍼에 저장할 최대 바이트 수 또는 [_TRUNCATE](../../c-runtime-library/truncate.md)입니다.

*mbstate*<br/>
**Mbstate_t** 변환 상태 개체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

성공시 0, 실패시 오류 코드.

|오류 조건|반환 값 및 **errno**|
|---------------------|------------------------------|
|*mbstr* 은 **NULL** 및 *sizeinbytes* > 0입니다.|**EINVAL**|
|*wcstr* 가 **NULL** 입니다.|**EINVAL**|
|대상 버퍼가 너무 작아서 변환 된 문자열을 포함할 수 없습니다 ( *개수가* **_TRUNCATE** 않는 경우 아래 설명 참조).|**ERANGE**|

이러한 조건 중 하나라도 발생하는 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 예외가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는 오류 코드를 반환 하 고 테이블에 표시 된 대로 **errno** 을 설정 합니다.

## <a name="remarks"></a>설명

**Wcsrtombs_s** 함수는 *mbstr* 에 포함 된 변환 상태를 사용 하 여 *wcstr* 가 가리키는 와이드 문자 문자열을 *mbstr* 에서 가리키는 버퍼에 저장 된 멀티 바이트 문자로 변환 합니다. 이러한 조건 중 하나가 충족될 때까지 변환은 문자마다 계속합니다.

- null 와이드 문자가 있는 경우

- 변환할 수 없는 와이드 문자가 있는 경우

- *Mbstr* 버퍼에 저장 된 바이트 수는 *count* 와 같습니다.

대상 문자열은 항상 null로 끝납니다(오류 발생 시도 포함).

*Count* 가 특수 값 [_TRUNCATE](../../c-runtime-library/truncate.md)경우에는 **wcsrtombs_s** 가 대상 버퍼에 맞는 만큼의 문자열을 변환 하는 동시에 null 종결자를 위한 공간을 남겨 둡니다.

**Wcsrtombs_s** 에서 소스 문자열을 성공적으로 변환 하는 경우 null 종결자를 포함 하 여 변환 된 문자열의 크기 (바이트)를 *&#42;pReturnValue* ( *pReturnValue* 가 **null** 이 아닌 경우)에 넣습니다. 이는 *mbstr* 인수가 **NULL** 인 경우에도 발생 하며 필요한 버퍼 크기를 결정 하는 방법을 제공 합니다. *Mbstr* 이 **NULL** 인 경우 *count* 는 무시 됩니다.

**Wcsrtombs_s** 멀티 바이트 문자로 변환할 수 없는 와이드 문자가 있는 경우 *\* pReturnValue* 에-1을 배치 하 고, 대상 버퍼를 빈 문자열로 설정 하 고, **errno** 를 **Eilseq** 로 설정 하 고, **eilseq** 를 반환 합니다.

*Wcstr* 및 *mbstr* 가 가리키는 시퀀스가 겹치면 **wcsrtombs_s** 의 동작이 정의 되지 않습니다. **wcsrtombs_s** 은 현재 로캘의 LC_TYPE 범주에 영향을 받습니다.

> [!IMPORTANT]
> *Wcstr* 및 *mbstr* 이 겹치지 않도록 하 고, 변환할 와이드 문자 수 *를 정확 하* 게 반영 합니다.

**Wcsrtombs_s** 함수는 다시 시작할에 의해 [_wcstombs_s_l wcstombs_s](wcstombs-s-wcstombs-s-l.md) 와 다릅니다. 동일 하거나 다른 다시 시작 가능 함수에 대 한 후속 호출의 경우 변환 상태가 *mbstate* 에 저장 됩니다. 다시 시작할 수 있는 함수와 다시 시작할 수 없는 함수를 함께 사용할 때는 결과가 정의되지 않습니다. 예를 들어, **wcstombs_s** 대신 **wcsrtombs_s** 에 대 한 후속 호출을 사용 하는 경우 응용 프로그램은 **wcslen** 이 아닌 **wcsrlen** 을 사용 합니다.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="exceptions"></a>예외

**Wcsrtombs_s** 함수는이 함수가 실행 되 고 *mbstate* 가 null 일 때 현재 스레드의 함수에서 **setlocale** 을 호출 하지 않는 한 다중 스레드 안전 합니다.

## <a name="example"></a>예제

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

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
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
