---
description: '자세히 알아보기: _mbccpy_s, _mbccpy_s_l'
title: _mbccpy_s, _mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: 6764c100fb52b025db2d8f79a72c7c6420a64bee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303533"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

한 문자열에서 다른 문자열로 멀티바이트 문자를 복사합니다. 이러한 버전의 [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 포함되어 있습니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*dest*<br/>
복사 대상입니다.

*buffSizeInBytes*<br/>
대상 버퍼의 크기입니다.

*pCopied 됨*<br/>
복사된 바이트 수로 채워집니다(성공할 경우 1 또는 2). 숫자에 대해 걱정 하지 않는 경우 **NULL** 을 전달 합니다.

*src*<br/>
복사할 멀티바이트 문자입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

성공 시 0이고, 실패 시 오류 코드입니다. *Src* 또는 *dest* 가 **NULL** 이거나 **buffSizeinBytes** 바이트를 초과 하는 바이트를 *Dest* 로 복사 하는 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **EINVAL** 를 반환 하 고 **errno** 은 **EINVAL** 로 설정 됩니다.

## <a name="remarks"></a>설명

**_Mbccpy_s** 함수는 *src* 에서 *dest* 로 하나의 멀티 바이트 문자를 복사 합니다. *Src* 가 [_ismbblead](ismbblead-ismbblead-l.md)에 대 한 암시적 호출에 의해 결정 된 멀티 바이트 문자의 선행 바이트를 가리키지 않는 경우 *src* 가 가리키는 단일 바이트가 복사 됩니다. *Src* 에서 선행 바이트를 가리키지만 다음 바이트가 0 이므로 유효 하지 않으면 0이 *dest* 로 복사 되 고 **errno** 가 **eilseq** 로 설정 되며 함수는 **eilseq** 를 반환 합니다.

**_mbccpy_s** 는 null 종결자를 추가 하지 않습니다. 그러나 *src* 가 null 문자를 가리키는 경우 null이 *dest* 로 복사 됩니다 (일반 싱글바이트 복사본 임).

*Pcopied* 의 값은 복사 된 바이트 수로 채워집니다. 연산이 성공할 경우 가능한 값은 1과 2입니다. **NULL** 이 전달 되 면이 매개 변수는 무시 됩니다.

|*src*|*대상* 에 복사 됨|*pCopied 됨*|반환 값|
|-----------|----------------------|---------------|------------------|
|비선행 바이트|비선행 바이트|1|0|
|0|0|1|0|
|선행 바이트와 그 뒤의 0이 아닌 값|선행 바이트와 그 뒤의 0이 아닌 값|2|0|
|선행 바이트와 그 뒤의 0|0|1|**EILSEQ**|

두 번째 행은 첫 번째 행의 특수 사례일 뿐입니다. 또한 테이블에서는 *buffSizeInBytes*  >=  *pcopied* 를 가정 합니다.

**_mbccpy_s** 은 모든 로캘 종속 동작에 현재 로캘을 사용 합니다. **_mbccpy_s_l** 은 모든 로캘 종속 동작에 대해 전달 된 로캘을 사용 **_mbccpy_s_l** 한다는 점을 제외 하 고 **_mbccpy_s** 와 동일 합니다.

C++에서는 템플릿 오버로드를 통해 이러한 함수를 사용하는 것이 더욱 간단해집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|매크로 또는 인라인 함수에 매핑됩니다.|**_mbccpy_s**|매크로 또는 인라인 함수에 매핑됩니다.|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
