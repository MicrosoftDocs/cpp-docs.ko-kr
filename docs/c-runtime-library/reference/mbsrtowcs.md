---
description: '자세히 알아보기: mbsrtowcs'
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 83979058e33ffc3874f26cb8ef70f888195e6644
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240184"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

현재 로캘의 멀티바이트 문자열을 해당하는 와이드 문자열로 변환합니다. 이때 멀티바이트 문자의 중간에서 변환을 다시 시작할 수 있습니다. 이 함수의 더 안전한 버전을 사용할 수 있습니다. [mbsrtowcs_s](mbsrtowcs-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>매개 변수

*wcstr*<br/>
변환된 결과 와이드 문자열을 저장하는 주소입니다.

*mbstr*<br/>
변환할 멀티바이트 문자열의 위치에 대한 간접 포인터입니다.

*count*<br/>
*Wcstr* 에서 변환 하 고 저장할 최대 문자 수 (바이트 아님)입니다.

*mbstate*<br/>
**Mbstate_t** 변환 상태 개체에 대 한 포인터입니다. 이 값이 null 포인터이면 정적 내부 변환 상태 개체가 사용됩니다. 내부 **mbstate_t** 개체는 스레드로부터 안전 하지 않으므로 항상 고유한 *mbstate* 매개 변수를 전달 하는 것이 좋습니다.

## <a name="return-value"></a>반환 값

종결 null 문자(있는 경우)를 포함하지 않고 정상적으로 변환된 문자 수를 반환합니다. 오류가 발생 한 경우 (size_t) (-1)을 반환 하 고 **errno** 를 EILSEQ로 설정 합니다.

## <a name="remarks"></a>설명

**Mbsrtowcs** 함수는 *mbstr* 에 포함 된 변환 상태를 사용 하 여 *mbstr* 에서 간접적으로 가리키는 멀티 바이트 문자 문자열을 *wcstr* 가 가리키는 버퍼에 저장 된 와이드 문자로 변환 합니다. 종료 null 멀티 바이트 문자가 발견 되거나, 현재 로캘의 유효한 문자에 해당 하지 않는 멀티 바이트 시퀀스가 발견 되거나, *count* 문자가 변환 될 때까지 각 문자에 대해 변환이 계속 됩니다. **Mbsrtowcs** 가 발생 하기 전후에 멀티 바이트 null 문자 (' \ 0 ')를 발견 *한 경우에* 는이를 16 비트 종료 null 문자로 변환 하 고 중지 합니다.

따라서 *wcstr* 의 와이드 문자열은 변환 하는 동안 **mbsrtowcs** 가 멀티 바이트 null 문자를 발견 하는 경우에만 null로 종결 됩니다. *Mbstr* 및 *wcstr* 가 가리키는 시퀀스가 겹치면 **mbsrtowcs** 의 동작이 정의 되지 않습니다. **mbsrtowcs** 은 현재 로캘의 LC_TYPE 범주에 의해 영향을 받습니다.

**Mbsrtowcs** 함수는 다시 시작할에 의해 [_mbstowcs_l mbstowcs](mbstowcs-mbstowcs-l.md) 와 다릅니다. 동일 하거나 다른 다시 시작 가능 함수에 대 한 후속 호출의 경우 변환 상태가 *mbstate* 에 저장 됩니다. 다시 시작할 수 있는 함수와 다시 시작할 수 없는 함수를 함께 사용할 때는 결과가 정의되지 않습니다.  예를 들어 **mbsrlen** 대신 **mbsrtowcs** 에 대 한 후속 호출을 사용 하는 경우 응용 프로그램은 **mbsrlen** 대신 **mbsrlen** 을 사용 해야 합니다.

*Wcstr* 이 null 포인터가 아닌 경우 null 종결 문자에 도달 하 여 변환이 중지 된 경우 *mbstr* 가 가리키는 포인터 개체에 null 포인터가 할당 됩니다. 그렇지 않으면 변환된 마지막 멀티바이트 문자 바로 다음의 주소(있는 경우)가 할당됩니다. 그러므로 후속 함수에서 이 호출이 중지된 변환을 다시 시작할 수 있습니다.

*Wcstr* 인수가 null 포인터인 경우 *count* 인수는 무시 되 고 **mbsrtowcs** 는 대상 문자열에 대해 필요한 크기 (와이드 문자)를 반환 합니다. *Mbstate* 가 null 포인터인 경우이 함수는 스레드로부터 안전 하지 않은 정적 내부 **mbstate_t** 변환 상태 개체를 사용 합니다. 문자 시퀀스 *mbstr* 에 해당 하는 멀티 바이트 문자 표현이 없으면-1이 반환 되 고 **Errno** 가 **eilseq** 로 설정 됩니다.

*Mbstr* isa null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

C++에서 이 함수는 해당 최신 보안 버전을 호출하는 템플릿 오버로드를 포함합니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="exceptions"></a>예외

**Mbsrtowcs** 함수는이 함수가 실행 중이 고 *mbstate* 인수가 null 포인터가 아닌 경우 현재 스레드의 함수가 **setlocale** 을 호출 하지 않는 한 다중 스레드 안전입니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
