---
description: '다음에 대 한 자세한 정보: strcat, wcscat, _mbscat'
title: strcat, wcscat, _mbscat
ms.date: 11/04/2016
api_name:
- _mbscat
- wcscat
- strcat
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscat
- _ftcscat
- _tcscat
- strcat
- wcscat
helpviewer_keywords:
- concatenating strings
- mbscat function
- _ftcscat function
- _tcscat function
- ftcscat function
- strcat function
- strings [C++], appending
- _mbscat function
- tcscat function
- strings [C++], concatenating
- appending strings
- wcscat function
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
ms.openlocfilehash: 12ec6f6e0e9f940ef72d0aec742137843238c534
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292158"
---
# <a name="strcat-wcscat-_mbscat"></a>strcat, wcscat, _mbscat

문자열을 추가합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [strcat_s, wcscat_s, _mbscat_s](strcat-s-wcscat-s-mbscat-s.md)를 참조하세요.

> [!IMPORTANT]
> **_mbscat_s** 은 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *strcat(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscat(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscat(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcat(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscat(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscat(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>매개 변수

*strDestination*<br/>
Null 종료 대상 문자열입니다.

*strSource*<br/>
Null 종료 소스 문자열입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 대상 문자열 (*strdestination*)을 반환 합니다. 반환 값 없음은 오류를 나타내는 데 예약되어 있습니다.

## <a name="remarks"></a>설명

**Strcat** 함수는 *Strcat* 를 *strcat* 에 추가 하 고 결과 문자열을 null 문자를 사용 하 여 종료 합니다. *Strsource* 의 초기 문자는 *strsource* 의 종료 null 문자를 덮어씁니다. 원본 및 대상 문자열이 겹치면 **strcat** 의 동작이 정의 되지 않습니다.

> [!IMPORTANT]
> **Strcat** 은 *strcat* 를 추가 하기 전에 *strcat* 의 공간이 충분 한지 확인 하지 않으므로 버퍼 오버런이 발생할 수 있습니다. 대신 [strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)를 사용하는 것이 좋습니다.

**wcscat** 및 **_mbscat** 는 **strcat** 의 와이드 문자 및 멀티 바이트 문자 버전입니다. **Wcscat** 의 인수와 반환 값은 와이드 문자 문자열입니다. **_mbscat** 의 이러한 문자열은 멀티 바이트 문자열입니다. 그렇지 않으면 이들 세 함수는 동일하게 작동합니다.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat**|**strcat**|**_mbscat**|**wcscat**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strcat**|\<string.h>|
|**wcscat**|\<string.h> 또는 \<wchar.h>|
|**_mbscat**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[strcpy](strcpy-wcscpy-mbscpy.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
