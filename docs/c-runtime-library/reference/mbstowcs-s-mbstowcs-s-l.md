---
description: '자세히 알아보기: mbstowcs_s, _mbstowcs_s_l'
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 4/2/2020
api_name:
- _mbstowcs_s_l
- mbstowcs_s
- _o__mbstowcs_s_l
- _o_mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 800cb64c62498cfea93c6fc600207ad1e2309b98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240119"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

멀티바이트 문자 시퀀스를 해당 와이드 문자 시퀀스로 변환합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*pReturnValue*<br/>
변환된 문자 수입니다.

*wcstr*<br/>
결과로 변환된 와이드 문자열을 위한 버퍼의 주소입니다.

*sizeInWords*<br/>
*Wcstr* 버퍼의 크기 (단어)입니다.

*mbstr*<br/>
null로 끝나는 멀티바이트 문자 시퀀스의 주소입니다.

*count*<br/>
*Wcstr* 버퍼에 저장할 최대 와이드 문자 수 이며 종료 null을 포함 하거나 [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

성공시 0, 실패시 오류 코드.

|오류 조건|반환 값 및 **errno**|
|---------------------|------------------------------|
|*wcstr* 는 **NULL** 및 *sizeinwords* > 0입니다.|**EINVAL**|
|*mbstr* 가 **NULL** 입니다.|**EINVAL**|
|대상 버퍼가 너무 작아서 변환 된 문자열을 포함할 수 없습니다 ( *개수가* **_TRUNCATE** 않는 경우 아래 설명 참조).|**ERANGE**|
|*wcstr* Is not **NULL** 및 *sizeinwords* = = 0|**EINVAL**|

이러한 조건 중 하나라도 발생하는 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 예외가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는 오류 코드를 반환 하 고 테이블에 표시 된 대로 **errno** 을 설정 합니다.

## <a name="remarks"></a>설명

**Mbstowcs_s** 함수는 *mbstr* 가 가리키는 멀티 바이트 문자 문자열을 *wcstr* 가 가리키는 버퍼에 저장 된 와이드 문자로 변환 합니다. 이러한 조건 중 하나가 충족될 때까지 변환은 문자마다 계속합니다.

- 멀티바이트 null 문자가 발견되는 경우

- 잘못된 멀티바이트 문자가 발견되는 경우

- *Wcstr* 버퍼에 저장 된 와이드 문자 수는 *count* 와 같습니다.

대상 문자열은 항상 null로 끝납니다(오류 발생 시도 포함).

*Count* 가 특수 값 [_TRUNCATE](../../c-runtime-library/truncate.md)경우에는 **mbstowcs_s** 가 대상 버퍼에 맞는 만큼의 문자열을 변환 하는 동시에 null 종결자를 위한 공간을 남겨 둡니다.

**Mbstowcs_s** 에서 소스 문자열을 성공적으로 변환 하는 경우 null 종결자를 포함 하 여 변환 된 문자열의 와이드 문자 크기를 *&#42;pReturnValue* ( *pReturnValue* 가 **null** 이 아닌 경우)에 넣습니다. *Wcstr* 인수가 **NULL** 이 고 필요한 버퍼 크기를 결정 하는 방법을 제공 하는 경우에도이 오류가 발생 합니다. *Wcstr* 이 **NULL** 이면 *Count* 는 무시 되 고 *sizeinwords* 는 0 이어야 합니다.

**Mbstowcs_s** 잘못 된 멀티 바이트 문자를 발견 하면 *&#42;pReturnValue* 에 0을 배치 하 고, 대상 버퍼를 빈 문자열로 설정 하 고, **errno** 를 **Eilseq** 로 설정 하 고, **eilseq** 를 반환 합니다.

*Mbstr* 및 *wcstr* 가 가리키는 시퀀스가 겹치면 **mbstowcs_s** 의 동작이 정의 되지 않습니다.

> [!IMPORTANT]
> *Wcstr* 및 *mbstr* 이 겹치지 않도록 하 고, 변환할 멀티 바이트 문자 수 *를 정확 하* 게 반영 합니다.

**mbstowcs_s** 은 모든 로캘 종속 동작에 대해 현재 로캘을 사용 합니다. **_mbstowcs_s_l** 은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
