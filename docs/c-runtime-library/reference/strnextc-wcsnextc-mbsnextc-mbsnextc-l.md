---
description: '자세한 정보: _strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l'
title: _strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l
ms.date: 4/2/2020
api_name:
- _strnextc
- _mbsnextc_l
- _mbsnextc
- _wcsnextc
- _o__mbsnextc
- _o__mbsnextc_l
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
- strnextc
- tcsnextc
- _mbsnextc_l
- _mbsnextc
- mbsnextc_l
- ftcsnextc
- mbsnextc
- _tcsnextc
- _wcsnextc
- _ftcsnextc
- _strnextc
- wcsnextc
helpviewer_keywords:
- _mbsnextc function
- _tcsnextc function
- _wcsnextc function
- tcsnextc function
- strnextc function
- mbsnextc function
- _strnextc function
- _mbsnextc_l function
- mbsnextc_l function
- wcsnextc function
ms.assetid: e3086173-9eb5-4540-a23a-5d866bd05340
ms.openlocfilehash: 8eb1af549e3ef983441870350cbfdc4361f26e9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306094"
---
# <a name="_strnextc-_wcsnextc-_mbsnextc-_mbsnextc_l"></a>_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l

문자열에서 다음 문자를 찾습니다.

> [!IMPORTANT]
> **_mbsnextc** 및 **_mbsnextc_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
unsigned int _strnextc(
   const char *str
);
unsigned int _wscnextc(
   const wchar_t *str
);
unsigned int _mbsnextc(
   const unsigned char *str
);
unsigned int _mbsnextc_l(
   const unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
원본 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 *str* 에서 다음 문자의 정수 값을 반환 합니다.

## <a name="remarks"></a>설명

**_Mbsnextc** 함수는 문자열 포인터를 이동 하지 않고 *str* 에서 다음 멀티 바이트 문자의 정수 값을 반환 합니다. **_mbsnextc** 는 현재 사용 중인 [멀티 바이트 코드 페이지](../../c-runtime-library/code-pages.md) 에 따라 멀티 바이트 문자 시퀀스를 인식 합니다.

*Str* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는 0을 반환 합니다.

**보안 정보** 이 API는 버퍼 오버런 문제로 인해 발생하는 잠재적인 위협을 일으킵니다. 버퍼 오버런 문제는 자주 사용되는 시스템 공격 방법으로, 불필요한 권한 상승을 초래합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnextc**|**_strnextc**|**_mbsnextc**|**_wcsnextc**|

**_strnextc** 및 **_wcsnextc** 는 **_mbsnextc** 의 싱글바이트 문자열과 와이드 문자열 버전입니다. **_wcsnextc** 은 *str* 에서 다음 와이드 문자의 정수 값을 반환 합니다. **_strnextc** 은 *str* 에서 다음 싱글바이트 문자의 정수 값을 반환 합니다. **_strnextc** 및 **_wcsnextc** 는이 매핑에 대해서만 제공 되며 그렇지 않으면 사용 하면 안 됩니다. 자세한 내용은 [일반 텍스트 매핑 사용](../../c-runtime-library/using-generic-text-mappings.md) 및 [일반 텍스트 매핑](../../c-runtime-library/generic-text-mappings.md)을 참조하세요.

**_mbsnextc_l** 은 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_mbsnextc**|\<mbstring.h>|
|**_mbsnextc_l**|\<mbstring.h>|
|**_strnextc**|\<tchar.h>|
|**_wcsnextc**|\<tchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
