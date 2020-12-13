---
description: '자세한 정보: _strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l'
title: _strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l
ms.date: 4/2/2020
api_name:
- _mbsnicoll_l
- _mbsnicoll
- _wcsnicoll_l
- _strnicoll
- _strnicoll_l
- _wcsnicoll
- _o__mbsnicoll
- _o__mbsnicoll_l
- _o__strnicoll
- _o__strnicoll_l
- _o__wcsnicoll
- _o__wcsnicoll_l
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
- wcshicoll_l
- _ftcsncicoll
- strnicoll_l
- _wcsnicoll
- mbsnicoll_l
- _strnicoll
- mbsnicoll
- _ftcsnicoll
- wcsnicoll
- _tcsnicoll
- _mbsnicoll
- strinicoll
- _tcsncicoll
helpviewer_keywords:
- code pages, using for string comparisons
- ftcsncicoll function
- mbsnicoll_l function
- _ftcsnicoll function
- mbsnicoll function
- _tcsnicoll function
- _wcsnicoll_l function
- _mbsnicoll function
- tcsncicoll function
- strnicoll function
- _ftcsncicoll function
- wcsnicoll_l function
- _mbsnicoll_l function
- _tcsncicoll function
- strnicoll_l function
- wcsnicoll function
- _strnicoll_l function
- _wcsnicoll function
- ftcsnicoll function
- strings [C++], comparing by code page
- tcsnicoll function
- _strnicoll function
ms.assetid: abf0c569-725b-428d-9ff2-924f430104b4
ms.openlocfilehash: 7fbbf44747bdcd0b95ccb603d735fc2ac0ecf6b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336470"
---
# <a name="_strnicoll-_wcsnicoll-_mbsnicoll-_strnicoll_l-_wcsnicoll_l-_mbsnicoll_l"></a>_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l

로캘별 정보를 사용하여 문자열을 비교합니다.

> [!IMPORTANT]
> **_mbsnicoll** 및 **_mbsnicoll_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _strnicoll(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicoll(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count
);
int _mbsnicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicoll_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicoll_l(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count,
   _locale_t locale
);
int _mbsnicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*string1*, *문자열 2*<br/>
비교할 Null 종료 문자열입니다.

*count*<br/>
비교할 문자 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 각 함수는 다음과 *같이 문자열 1과 문자열* *2* 의 부분 문자열의 관계를 나타내는 값을 반환 합니다.

|반환 값|문자열 1과 문자열 2의 관계|
|------------------|----------------------------------------|
|< 0|*문자열* *2* 보다 작음|
|0|*문자열* *2* 와 같음|
|> 0|*문자열* *2* 보다 큼|

이러한 각 함수는 **_NLSCMPERROR** 를 반환 합니다. **_NLSCMPERROR** 를 사용 하려면 문자열을 포함 합니다. H 또는 MBSTR.H. 문자열이 나 문자열이 정렬 시퀀스의 도메인 외부에 있는 와이드 문자 *코드를 포함* 하는 *경우에는* **_wcsnicoll** 실패할 수 있습니다. 오류가 발생 하면 **errno** 를 **EINVAL** 로 설정할 수 **_wcsnicoll** . **_Wcsnicoll** 에 대 한 호출에서 오류를 확인 하려면 **errno** 를 0으로 설정한 다음 **_wcsnicoll** 를 호출한 후 **errno** 를 확인 합니다.

## <a name="remarks"></a>설명

이러한 각 함수는 코드 페이지에 따라 *문자열* 1과 *문자열 2* 의 첫 번째 *count* 문자를 대/소문자를 구분 하지 않고 비교 합니다. 코드 페이지에서 문자 집합 순서와 사전적 문자 순서가 다르며 이러한 차이가 문자열 비교 시 중요한 경우에만 이러한 함수를 사용해야 합니다. **_L** 접미사가 없는 이러한 함수 버전은 현재 로캘 및 코드 페이지를 사용 합니다. **_L** 접미사가 있는 버전은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

이러한 모든 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *String1* 또는 *문자열* 개수가 null 포인터 이거나 count가 **INT_MAX** 보다 큰 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **_NLSCMPERROR** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicoll**|**_strnicoll**|**_mbsnbicoll**|**_wcsnicoll**|
|**_tcsnicoll**|**_strnicoll**|[_mbsnbicoll](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|**_wcsnicoll**|
|**_tcsnicoll_l**|**_strnicoll_l**|**_mbsnbicoll_l**|**_wcsnicoll_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_strnicoll**, **_strnicoll_l**|\<string.h>|
|**_wcsnicoll**, **_wcsnicoll_l**|\<wchar.h> 또는 \<string.h>|
|**_mbsnicoll**, **_mbsnicoll_l**|\<mbstring.h>|

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
