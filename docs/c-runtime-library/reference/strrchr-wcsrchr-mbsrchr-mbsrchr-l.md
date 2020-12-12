---
description: '다음에 대 한 자세한 정보: strrchr, wcsrchr, _mbsrchr, _mbsrchr_l'
title: strrchr, wcsrchr, _mbsrchr, _mbsrchr_l
ms.date: 4/2/2020
api_name:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
- _o__mbsrchr
- _o__mbsrchr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
ms.openlocfilehash: 6931358132372a03ca56e1ce99b62a7a84807b59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296227"
---
# <a name="strrchr-wcsrchr-_mbsrchr-_mbsrchr_l"></a>strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

문자열에서 마지막으로 나오는 문자를 검색합니다.

> [!IMPORTANT]
> Windows 런타임에서 실행되는 애플리케이션에서는 `_mbsrchr` 및 `_mbsrchr_l`을 사용할 수는 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *strrchr(
   const char *str,
   int c
); // C only
char *strrchr(
   char *str,
   int c
); // C++ only
const char *strrchr(
   const char *str,
   int c
); // C++ only
wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcsrchr(
   wchar_t *str,
   wchar_t c
); // C++ only
const wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C++ only
unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbsrchr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbsrchr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>매개 변수

*str*<br/>
검색할 Null 종료 문자열입니다.

*c*<br/>
찾을 문자입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

*Str* 에서 *c* 의 마지막 항목에 대 한 포인터를 반환 하거나 *c* 를 찾을 수 없는 경우 NULL을 반환 합니다.

## <a name="remarks"></a>설명

`strrchr`함수는 str에서 *c* (로 변환 됨)의 마지막 항목을 찾습니다 **`char`** .  검색에는 종료형 null 문자를 포함합니다.

`wcsrchr` 및 `_mbsrchr` 는 `strrchr`의 와이드 문자 및 멀티바이트 문자 버전입니다. `wcsrchr`의 인수 및 반환 값은 와이드 문자열이며 `_mbsrchr`의 인수와 반환 값은 멀티바이트 문자열입니다.

C에서 이러한 함수는 **`const`** 첫 번째 인수에 대 한 포인터를 사용 합니다. C++에서는 두 오버로드를 모두 사용할 수 있습니다. 포인터를 사용 하는 오버 로드는에 대 한 포인터를 반환 합니다 .가 아닌에 대 한 포인터를 사용 하는 **`const`** **`const`** 버전은가 **`const`** 아닌에 대 한 포인터를 반환 합니다 **`const`** . **`const`** 이러한 함수의 및 비 버전을 모두 사용할 수 있는 경우 매크로 _CRT_CONST_CORRECT_OVERLOADS 정의 됩니다 **`const`** . **`const`** 두 c + + 오버 로드에 대 한 비 동작이 필요한 경우 기호 _CONST_RETURN 정의 합니다.

`_mbsrchr`는 매개 변수의 유효성을 검사합니다. *Str* 이 NULL 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 `errno` 는 EINVAL로 설정 되 고는 `_mbsrchr` 0을 반환 합니다. `strrchr` 및 `wcsrchr`는 매개 변수의 유효성을 검사하지 않습니다. 그렇지 않으면 이들 세 함수는 동일하게 작동합니다.

출력 값은 로캘의 LC_CTYPE 범주 설정에 따라 영향을 받습니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조 하세요. **_l** 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|
|**해당 없음**|**해당 없음**|`_mbsrchr_l`|**해당 없음**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`strrchr`|\<string.h>|
|`wcsrchr`|\<string.h> 또는 \<wchar.h>|
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

`strrchr` 사용 예제는 [strchr](strchr-wcschr-mbschr-mbschr-l.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
