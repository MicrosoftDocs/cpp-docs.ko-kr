---
title: _mbccpy, _mbccpy_l
ms.date: 11/04/2016
apiname:
- _mbccpy
- _mbccpy_l
apilocation:
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
apitype: DLLExport
f1_keywords:
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
ms.openlocfilehash: 852097ebea41ef99b1a53f7bc344eb0c08911a4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533746"
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l

한 문자열에서 다른 문자열로 멀티바이트 문자를 복사합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_mbccpy_s, _mbccpy_s_l](mbccpy-s-mbccpy-s-l.md)을 참조하세요.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void _mbccpy(
   unsigned char *dest,
   const unsigned char *src
);
void _mbccpy_l(
   unsigned char *dest,
   const unsigned char *src,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*dest*<br/>
복사 대상입니다.

*src*<br/>
복사할 멀티바이트 문자입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="remarks"></a>설명

합니다 **_mbccpy** 함수에서 하나의 멀티 바이트 문자를 복사 *src* 하 *dest*합니다.

이 함수는 해당 매개 변수의 유효성을 검사합니다. 하는 경우 **_mbccpy** 에 대 한 null 포인터가 전달 됩니다 *dest* 하거나 *src*에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md). 실행을 계속 하도록 허용 된 경우 **errno** 로 설정 된 **EINVAL**합니다.

**_mbccpy** 모든 로캘 종속 동작에 현재 로캘을 사용 합니다. **_mbccpy_l** 동일 **_mbccpy** 한다는 **_mbccpy_l** 로캘 종속 동작에 대해 전달 된 로캘을 사용 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

**보안 정보** null로 끝나는 문자열을 사용하세요. null로 끝나는 문자열은 대상 버퍼의 크기를 초과할 수 없습니다. 자세한 내용은 [버퍼 오버런 방지](/windows/desktop/SecBP/avoiding-buffer-overruns)를 참조하세요. 버퍼 오버런 문제는 자주 사용되는 시스템 공격 방법으로, 불필요한 권한 상승을 초래합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy**|매크로 또는 인라인 함수에 매핑|**_mbccpy**|매크로 또는 인라인 함수에 매핑|
|**_tccpy_l**|N/A|**_mbccpy_l**|N/A|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[로캘](../../c-runtime-library/locale.md)<br/>
[멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
