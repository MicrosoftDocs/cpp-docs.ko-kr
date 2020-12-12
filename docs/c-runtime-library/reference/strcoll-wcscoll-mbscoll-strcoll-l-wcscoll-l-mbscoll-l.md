---
description: '자세히 알아보기: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l'
title: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
ms.date: 4/2/2020
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
- _o__mbscoll
- _o__mbscoll_l
- _o__strcoll_l
- _o__wcscoll_l
- _o_strcoll
- _o_wcscoll
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: f3d826a14bb1cc77f6265806cc24ef5e9cd92b6a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306146"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

현재 로캘 또는 지정된 LC_COLLAT 변환 상태 범주를 사용하여 문자열을 비교합니다.

> [!IMPORTANT]
> **_mbscoll** 및 **_mbscoll_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*string1*, *문자열 2*<br/>
비교할 Null 종료 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 다음과 같이 *문자열* 1과 *문자열 2* 의 관계를 나타내는 값을 반환 합니다.

|반환 값|문자열 1과 문자열 2의 관계|
|------------------|----------------------------------------|
|< 0|*문자열* *2* 보다 작음|
|0|*문자열* *2* 와 같음|
|> 0|*문자열* *2* 보다 큼|

이러한 각 함수는 오류에 **_NLSCMPERROR** 를 반환 합니다. **_NLSCMPERROR** 를 사용 하려면 문자열을 포함 합니다. H 또는 MBSTR.H. *string1 또는 string1* 이 **NULL** 이거나 정렬 시퀀스의 도메인 외부에 있는 와이드 문자 코드를 포함 하는 경우 *에는* **wcscoll** 가 실패할 수 있습니다. 오류가 발생 하면 **wcscoll** 가 **errno** 를 **EINVAL** 로 설정할 수 있습니다. **Wcscoll** 에 대 한 호출에서 오류를 확인 하려면 **errno** 를 0으로 설정 하 고 **wcscoll** 를 호출한 후 **errno** 를 확인 합니다.

## <a name="remarks"></a>설명

이러한 각 함수는 현재 사용 중인 코드 페이지에 따라 *문자열* 1과 *문자열* 1의 대/소문자를 구분 하는 비교를 수행 합니다. 현재 코드 페이지에서 문자 집합 순서와 사전적 문자 순서가 다르며 이러한 차이가 문자열 비교 시 중요한 경우에만 이러한 함수를 사용해야 합니다.

이러한 모든 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *String1* 또는 *문자열* 개수가 null 포인터 이거나 *count* 가 **INT_MAX** 보다 큰 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **_NLSCMPERROR** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

두 문자열의 비교는 로캘 종속 작업입니다. 각 로캘에서 문자의 순서를 지정하는 규칙은 서로 다르기 때문입니다. **_L** 접미사가 없는 이러한 함수 버전은이 로캘 종속 동작에 현재 스레드의 로캘을 사용 합니다. **_l** 접미사가 있는 버전은 현재 로캘 대신 매개 변수로 전달 된 로캘을 사용 한다는 점을 제외 하 고는 접미사가 없는 해당 함수와 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<wchar.h>, \<string.h>|
|**_mbscoll**, **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>, \<string.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[로캘](../../c-runtime-library/locale.md)<br/>
[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
