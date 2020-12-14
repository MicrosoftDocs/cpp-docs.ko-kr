---
description: '다음에 대 한 자세한 정보: mbsrtowcs_s'
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: c7c53d3213bbe552dd63eb527a635660e803e9a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240171"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

현재 로캘의 멀티바이트 문자열을 와이드 문자열 표현으로 변환합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [mbsrtowcs](mbsrtowcs.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>매개 변수

*pReturnValue*<br/>
변환된 문자 수입니다.

*wcstr*<br/>
결과로 생성되는 와이드 문자열을 저장할 버퍼의 주소입니다.

*sizeInWords*<br/>
*Wcstr* 의 크기 (와이드 문자)입니다.

*mbstr*<br/>
변환할 멀티바이트 문자열의 위치에 대한 간접 포인터입니다.

*count*<br/>
*Wcstr* 버퍼에 저장할 최대 와이드 문자 수 이며 종료 null을 포함 하거나 [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
**Mbstate_t** 변환 상태 개체에 대 한 포인터입니다. 이 값이 null 포인터이면 정적 내부 변환 상태 개체가 사용됩니다. 내부 **mbstate_t** 개체는 스레드로부터 안전 하지 않으므로 항상 고유한 *mbstate* 매개 변수를 전달 하는 것이 좋습니다.

## <a name="return-value"></a>반환 값

변환이 완료되면 0이 반환되고, 실패하면 오류 코드가 반환됩니다.

|오류 조건|반환 값 및 **errno**|
|---------------------|------------------------------|
|*wcstr* 은 null 포인터 및 *sizeinwords* > 0입니다.|**EINVAL**|
|*mbstr* 은 null 포인터입니다.|**EINVAL**|
|*Mbstr* 가 간접적으로 가리키는 문자열에 현재 로캘에 대해 잘못 된 멀티 바이트 시퀀스가 포함 되어 있습니다.|**EILSEQ**|
|대상 버퍼가 너무 작아서 변환 된 문자열을 포함할 수 없습니다 ( *개수가* **_TRUNCATE** 않는 경우). 자세한 내용은 설명 부분을 참조 하십시오.|**ERANGE**|

이러한 상황 중 하나라도 발생하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 예외가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는 오류 코드를 반환 하 고 테이블에 표시 된 대로 **errno** 을 설정 합니다.

## <a name="remarks"></a>설명

**Mbsrtowcs_s** 함수는 *mbstr* 에 포함 된 변환 상태를 사용 하 여 *mbstr* 에서 간접적으로 가리키는 멀티 바이트 문자 문자열을 *wcstr* 가 가리키는 버퍼에 저장 된 와이드 문자로 변환 합니다. 이러한 조건 중 하나가 충족될 때까지 변환은 문자마다 계속합니다.

- 멀티바이트 null 문자가 발견되는 경우

- 잘못된 멀티바이트 문자가 발견되는 경우

- *Wcstr* 버퍼에 저장 된 와이드 문자 수는 *count* 와 같습니다.

*Wcstr* 가 null 포인터인 경우를 제외 하 고는 오류가 발생 하더라도 대상 문자열 *wcstr* 항상 null로 종료 됩니다.

*Count* 가 특수 값 [_TRUNCATE](../../c-runtime-library/truncate.md)인 경우 **mbsrtowcs_s** 은 대상 버퍼에 맞는 만큼의 문자열을 변환 하는 동시에 null 종결자를 위한 공간을 남겨 둡니다.

**Mbsrtowcs_s** 에서 소스 문자열을 성공적으로 변환 하는 경우 변환 된 문자열의 와이드 문자 크기와 null 종결자를 *&#42;pReturnValue* 에 배치 하 고 *pReturnValue* 가 null 포인터가 아닌 경우 *Wcstr* 인수가 null 포인터인 경우에도이 오류가 발생 하 여 필요한 버퍼 크기를 결정할 수 있습니다. *Wcstr* 가 null 포인터인 경우 *count* 는 무시 됩니다.

*Wcstr* 이 null 포인터가 아닌 경우 null 종결 문자에 도달 하 여 변환이 중지 된 경우 *mbstr* 가 가리키는 포인터 개체에 null 포인터가 할당 됩니다. 그렇지 않으면 변환된 마지막 멀티바이트 문자 바로 다음의 주소(있는 경우)가 할당됩니다. 그러므로 후속 함수에서 이 호출이 중지된 변환을 다시 시작할 수 있습니다.

*Mbstate* 가 null 포인터 이면 라이브러리 내부 **mbstate_t** 변환 상태 정적 개체가 사용 됩니다. 이 내부 정적 개체는 스레드로부터 안전 하지 않으므로 자신의 *mbstate* 값을 전달 하는 것이 좋습니다.

**Mbsrtowcs_s** 현재 로캘에서 잘못 된 멀티 바이트 문자를 발견 하면 *&#42;pReturnValue* 에-1을 배치 하 고, 대상 버퍼 *wcstr* 를 빈 문자열로 설정 하 고, **errno** 를 **Eilseq** 로 설정 하 고, **eilseq** 를 반환 합니다.

*Mbstr* 및 *wcstr* 가 가리키는 시퀀스가 겹치면 **mbsrtowcs_s** 의 동작이 정의 되지 않습니다. **mbsrtowcs_s** 은 현재 로캘의 LC_TYPE 범주에 영향을 받습니다.

> [!IMPORTANT]
> *Wcstr* 및 *mbstr* 이 겹치지 않도록 하 고, 변환할 멀티 바이트 문자 수 *를 정확 하* 게 반영 합니다.

**Mbsrtowcs_s** 함수는 다시 시작할에 의해 [_mbstowcs_s_l mbstowcs_s](mbstowcs-s-mbstowcs-s-l.md) 와 다릅니다. 동일 하거나 다른 다시 시작 가능 함수에 대 한 후속 호출의 경우 변환 상태가 *mbstate* 에 저장 됩니다. 다시 시작할 수 있는 함수와 다시 시작할 수 없는 함수를 함께 사용할 때는 결과가 정의되지 않습니다. 예를 들어, **mbstowcs_s** 대신 **mbsrtowcs_s** 에 대 한 후속 호출을 사용 하는 경우 응용 프로그램은 **mbsrlen** 대신 **mbsrlen** 을 사용 해야 합니다.

C++에서는 템플릿 오버로드로 이러한 함수를 간편하게 사용할 수 있습니다. 즉, 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 또한 기존의 비보안 함수를 그에 해당하는 안전한 최신 함수로 자동 교체할 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="exceptions"></a>예외

이 함수가 실행 중이 고 *mbstate* 인수가 null 포인터가 아닌 경우 현재 스레드의 함수가 **setlocale** 을 호출 하지 않는 경우 **mbsrtowcs_s** 함수는 다중 스레드 안전 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
