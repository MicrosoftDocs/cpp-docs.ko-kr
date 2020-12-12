---
description: Strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l에 대해 자세히 알아보세요.
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 4/2/2020
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
- _o__strxfrm_l
- _o__wcsxfrm_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: ce49d725673e909cd2befb322bbd90450bfba2e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326267"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

로캘별 정보를 기반으로 문자열을 변형합니다.

## <a name="syntax"></a>구문

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*strDest*<br/>
대상 문자열입니다.

*strSource*<br/>
원본 문자열입니다.

*count*<br/>
*Strdest* 에 저장할 최대 문자 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

종료 null 문자를 세지 않고 변형된 문자열의 길이를 반환합니다. 반환 값이 *count* 보다 크거나 같으면 *strdest* 의 콘텐츠를 예측할 수 없습니다. 오류가 발생 하면 각 함수는 **errno** 를 설정 하 고 **INT_MAX** 을 반환 합니다. 잘못 된 문자의 경우 **errno** 는 **eilseq** 로 설정 됩니다.

## <a name="remarks"></a>설명

**Strxfrm** 함수는 *strsource* 에 의해 가리키는 문자열을 *strsource* 에 저장 된 새로운 정렬 된 형식으로 변환 합니다. Null 문자를 포함 하 여 *count* 개 이하의 문자가 변환 되어 결과 문자열에 배치 됩니다. 변환은 로캘의 **LC_COLLATE** 범주 설정을 사용 하 여 수행 됩니다. **LC_COLLATE** 에 대 한 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조 하세요. **strxfrm** 는 로캘 종속 동작에 현재 로캘을 사용 합니다. **_strxfrm_l** 은 현재 로캘 대신 전달 된 로캘을 사용 한다는 점을 제외 하 고 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

변환 후 변환 된 두 문자열을 사용 하 여 **strcmp** 를 호출 하면 원래 두 문자열에 적용 된 **strcoll** 에 대 한 호출과 동일한 결과가 발생 합니다. **Strcoll** 및 **stricoll** 와 마찬가지로 **strxfrm** 는 자동으로 멀티 바이트 문자열을 적절 하 게 처리 합니다.

**wcsxfrm** 는 **strxfrm** 의 와이드 문자 버전입니다. **wcsxfrm** 의 문자열 인수는 와이드 문자 포인터입니다. **Wcsxfrm** 의 경우 문자열 변환 후 변환 된 문자열이 두 개인 **wcscmp** 에 대 한 호출은 원래 두 문자열에 적용 된 **wcscoll** 에 대 한 호출의 결과와 동일한 결과를 생성 합니다. **wcsxfrm** 및 **strxfrm** 는 동일 하 게 동작 합니다. **wcsxfrm** 는 로캘 종속 동작에 현재 로캘을 사용 합니다. **_wcsxfrm_l** 은 현재 로캘 대신 전달 된 로캘을 사용 합니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *Strsource* 가 null 포인터 이거나 *strsource* 가 **null** 포인터 (count가 0이 아닌 경우) 이거나 *Count* 가 **INT_MAX** 보다 큰 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **INT_MAX** 을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

"C" 로캘에서 문자 집합(ASCII 문자 집합)의 순서는 사전적 문자 순서와 같습니다. 그러나 다른 로캘에서 문자 집합의 문자 순서는 사전적 문자 순서와 다를 수 있습니다. 예를 들어 특정 유럽 로캘의 문자 집합에서 문자 'a'(값 0x61)는 문자 '&\#x00E4;'(값 0xE4) 앞에 오지만 사전적으로는 문자 'ä'가 'a' 앞에 옵니다.

문자 집합과 사전적 문자 순서가 다른 로캘에서는 원래 문자열에서 **strxfrm** 를 사용한 다음 결과 문자열에 대해 **strcmp** 를 사용 하 여 현재 로캘의 **LC_COLLATE** 범주 설정에 따라 사전적 문자열 비교를 생성 합니다. 따라서 위의 로캘에서 사전순으로 두 문자열을 비교 하려면 원래 문자열에서 **strxfrm** 를 사용한 다음 결과 문자열에 **strcmp** 합니다. 또는 원래 문자열에 **strcmp** 대신 **strcoll** 를 사용할 수 있습니다.

**strxfrm** 는 기본적으로 **LCMAP_SORTKEY** 와 [활성화 되었으며 lcmapstring](/windows/win32/api/winnls/nf-winnls-lcmapstringw) 에 대 한 래퍼입니다.

다음 식의 값은 원본 문자열의 **strxfrm** 변환을 유지 하는 데 필요한 배열의 크기입니다.

`1 + strxfrm( NULL, string, 0 )`

"C" 로캘에서만 **strxfrm** 는 다음과 같습니다.

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> 또는 \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
