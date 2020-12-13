---
description: Wcstombs, _wcstombs_l에 대해 자세히 알아보세요.
title: wcstombs, _wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: 070ba4dbf574ccd6b1afaec074dc9eb9f311e728
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136840"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

와이드 문자의 시퀀스를 멀티바이트 문자의 해당 시퀀스로 변환합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*mbstr*<br/>
멀티바이트 문자 시퀀스의 주소입니다.

*wcstr*<br/>
와이드 문자 시퀀스의 주소입니다.

*count*<br/>
멀티바이트 출력 문자열에 저장할 수 있는 최대 바이트 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**Wcstombs** 가 멀티 바이트 문자열을 성공적으로 변환 하는 경우에는 종료 null (있는 경우)을 제외 하 고 멀티 바이트 출력 문자열에 쓴 바이트 수를 반환 합니다. *Mbstr* 인수가 **NULL** 이면 **wcstombs** 는 대상 문자열의 필요한 크기 (바이트)를 반환 합니다. **Wcstombs** 가 멀티 바이트 문자로 변환할 수 없는 와이드 문자를 발견 하는 경우 **size_t** 형식으로-1 캐스트를 반환 하 고 **errno** 를 **eilseq** 로 설정 합니다.

## <a name="remarks"></a>설명

**Wcstombs** 함수는 *wcstr* 가 가리키는 와이드 문자 문자열을 해당 멀티 바이트 문자로 변환 하 고 그 결과를 *mbstr* 배열에 저장 합니다. *Count* 매개 변수는 멀티 바이트 출력 문자열 ( *mbstr* 의 크기)에 저장할 수 있는 최대 바이트 수를 나타냅니다. 일반적으로는 와이드 문자열을 변환할 때 필요한 바이트의 수를 알 수 없습니다. 출력 문자열에서 1바이트만 사용하면 되면 되는 와이드 문자도 있고 2바이트를 사용해야 하는 문자도 있습니다. 와이드 문자 null을 포함 하 여 입력 문자열의 모든 와이드 문자에 대해 멀티 바이트 출력 문자열에 2 바이트가 있으면 결과가 일치 하도록 보장 됩니다.

**Wcstombs** 가 발생 하기 전이나 후에 와이드 문자 null 문자 (L ' \ 0 ')를 발견 *하면이* 를 8 비트 0으로 변환 하 고 중지 합니다. 따라서 **wcstombs** 는 변환 중에 와이드 문자 null 문자를 발견 하는 경우에만 *mbstr* 의 멀티 바이트 문자열을 null로 종료 합니다. *Wcstr* 및 *mbstr* 가 가리키는 시퀀스가 겹치면 **wcstombs** 의 동작이 정의 되지 않습니다.

*Mbstr* 인수가 **NULL** 이면 **wcstombs** 는 대상 문자열의 필요한 크기 (바이트)를 반환 합니다.

**wcstombs** 은 매개 변수의 유효성을 검사 합니다. *Wcstr* 가 **NULL** 이거나 *count* 가 **INT_MAX** 보다 큰 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

**wcstombs** 는 로캘 종속 동작에 대해 현재 로캘을 사용 합니다. **_wcstombs_l** 은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 프로그램은 **wcstombs** 함수의 동작을 보여 줍니다.

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
