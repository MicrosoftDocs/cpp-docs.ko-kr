---
title: '`_mbsnbcat_s`, `_mbsnbcat_s_l`'
description: Microsoft Visual C++ `_mbsnbcat_s` 및 함수에 대 한 API `_mbsnbcat_s_l` 설명
ms.date: 12/2/2020
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
- _o__mbsnbcat_s
- _o__mbsnbcat_s_l
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
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: c7198d806d8ebe077b423ff2135b5bdcf66ffac6
ms.sourcegitcommit: 9c45483572db4470fe5db5a7b596d5770303098c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96523116"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>`_mbsnbcat_s`, `_mbsnbcat_s_l`

다른 멀티 바이트 문자열의 처음 **n** 바이트에 해당 하는 멀티 바이트 문자열에 추가 합니다. 이러한 버전은 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명 된 대로 향상 된 보안 기능을 포함 하는 [버전입니다. `_mbsnbcat` `_mbsnbcat_l` ](mbsnbcat-mbsnbcat-l.md)

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*`dest`*\
null로 끝나는 멀티바이트 문자 대상 문자열입니다.

*`sizeInBytes`*\
버퍼의 크기 *`dest`* (바이트)입니다.

*`src`*\
null로 끝나는 멀티바이트 문자 소스 문자열입니다.

*`count`*\
에 추가할의 바이트 수 *`src`* *`dest`* 입니다.

*`locale`*\
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

성공하면 0이고, 그렇지 않으면 오류 코드입니다.

### <a name="error-conditions"></a>오류 조건

|**`dest`**|*`sizeInBytes`*|*`src`*|반환 값|
|------------|-------------------|-----------|------------------|
|**`NULL`**|any|any|**`EINVAL`**|
|모두|<= 0|any|**`EINVAL`**|
|모두|any|**`NULL`**|**`EINVAL`**|

오류 조건이 발생하는 경우 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 오류를 생성합니다. 오류가 처리 되 면 함수는를 반환 하 **`EINVAL`** 고 **errno** 를로 설정 **`EINVAL`** 합니다.

## <a name="remarks"></a>설명

**`_mbsnbcat_s`** 함수는 *`dest`* 의 처음 바이트에를 추가 *`count`* *`src`* 합니다. 에서 null 문자 바로 앞에 오는 바이트가 *`dest`* 선행 바이트인 경우의 초기 바이트에 의해 덮어쓰여집니다 *`src`* . 그렇지 않으면의 초기 바이트가의 *`src`* 종료 null 문자를 덮어씁니다 *`dest`* . 바이트가 추가 되기 전에에 null 바이트가 표시 되 면에서 *`src`* *`count`* **`_mbsnbcat_s`** 모든 바이트를 *`src`* null 문자까지 추가 합니다. *`count`* 가의 길이 보다 크면의 *`src`* 길이가 대신 *`src`* 사용 됩니다 *`count`* . 결과 문자열은 null 문자로 끝납니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

출력 값은 로캘의 범주 설정에 영향을 받습니다 **`LC_CTYPE`** . 자세한 내용은 [setlocale, _wsetlocale를](setlocale-wsetlocale.md) 참조 하세요. 접미사가 없는 함수는 **`_l`** 현재 로캘을 사용 하 고 접미사가 있는 함수는 **`_l`** 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고 이러한 함수의 버전은 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

C + +에서는 템플릿 오버 로드로 인해 이러한 함수를 사용 하는 것이 간단 합니다. 오버 로드는 버퍼 길이를 자동으로 유추할 수 있으므로 크기 인수를 지정할 필요가 없으며, 보다 최신의 보안 기능을 자동으로 사용 하 여 안전 하지 않은 이전 함수를 대체할 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

이러한 함수의 디버그 라이브러리 버전은 먼저 0xFE를 사용 하 여 버퍼를 채웁니다. 이 동작을 사용 하지 않도록 설정 하려면를 사용 [`_CrtSetDebugFillThreshold`](crtsetdebugfillthreshold.md) 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|`Tchar.h` 일반|`_UNICODE``_MBCS`정의 되지 않음|`_MBCS` 지정|`_UNICODE` 지정|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**`_tcsncat_s`**|[strncat_s](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|**`_mbsnbcat_s`**|[wcsncat_s](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|
|**`_tcsncat_s_l`**|**`_strncat_s_l`**|**`_mbsnbcat_s_l`**|**`_wcsncat_s_l`**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`_mbsnbcat_s`**|\<mbstring.h>|
|**`_mbsnbcat_s_l`**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)\
[`_mbsnbcmp`, `_mbsnbcmp_l`](mbsnbcmp-mbsnbcmp-l.md)\
[`_strncnt`, `_wcsncnt`, `_mbsnbcnt`, `_mbsnbcnt_l`, `_mbsnccnt`, `_mbsnccnt_l`](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)\
[`_mbsnbcpy`, `_mbsnbcpy_l`](mbsnbcpy-mbsnbcpy-l.md)\
[`_mbsnbcpy_s`, `_mbsnbcpy_s_l`](mbsnbcpy-s-mbsnbcpy-s-l.md)\
[`_mbsnbset`, `_mbsnbset_l`](mbsnbset-mbsnbset-l.md)\
[`strncat`, `_strncat_l`, `wcsncat`, `_wcsncat_l`, `_mbsncat`, `_mbsncat_l`](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)\
[`strncat_s`, `_strncat_s_l`, `wcsncat_s`, `_wcsncat_s_l`, `_mbsncat_s`, `_mbsncat_s_l`](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)
