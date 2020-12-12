---
description: Strtoull, _strtoull_l, wcstoull, _wcstoull_l에 대해 자세히 알아보세요.
title: strtoull, _strtoull_l, wcstoull, _wcstoull_l
ms.date: 4/2/2020
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
- _o__strtoull_l
- _o__wcstoull_l
- _o_strtoull
- _o_wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: 941a38f5c972b73924aabea826e5495929505fe5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117265"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l

문자열을 **`unsigned long long`** 정수 값으로 변환 합니다.

## <a name="syntax"></a>구문

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*strSource*<br/>
변환할 Null 종료 문자열입니다.

*endptr*<br/>
검색을 중지하는 문자에 대한 포인터입니다.

*base*<br/>
사용할 기수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**strtoull** 는 변환 된 값 (있는 경우)을 반환 하거나 오버플로가 발생할 경우 **ULLONG_MAX** 반환 합니다. 변환을 수행할 수 없는 경우 **strtoull** 는 0을 반환 합니다. **wcstoull** 는와 유사 값을 **strtoull** 로 반환 합니다. 두 함수 모두 오버플로 또는 언더플로가 발생 하는 경우 **errno** 는 **ERANGE** 로 설정 됩니다.

반환 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

이러한 각 함수는 입력 문자열 *Strsource* 를 정수 값으로 변환 합니다 **`unsigned long long`** .

**strtoull** 는 숫자의 일부분으로 인식할 수 없는 첫 번째 문자에서 문자열 *strsource* 읽기를 중지 합니다. 이 문자는 종료 null 문자일 수도 있고 *base* 보다 크거나 같은 첫 번째 숫자 문자일 수도 있습니다. 로캘의 **LC_NUMERIC** 범주 설정은 *strsource* 의 기 하 문자를 인식 하도록 결정 합니다. 자세한 내용은 [setlocale, _wsetlocale](setlocale-wsetlocale.md)를 참조 하세요. **strtoull** 및 **wcstoull** 는 현재 로캘을 사용 합니다. **_strtoull_l** 및 **_wcstoull_l** 은 전달 된 로캘을 대신 사용 하지만 그렇지 않은 경우 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

*Endptr* 이 **NULL** 이 아닌 경우 검색을 중지 한 문자에 대 한 포인터는 *endptr* 에서 가리키는 위치에 저장 됩니다. 올바른 숫자를 찾을 수 없거나 잘못 된 밑수를 지정 하 여 변환을 수행할 수 없는 경우 *Strsource* 의 값은 *endptr* 에서 가리키는 위치에 저장 됩니다.

**wcstoull** 는 **strtoull** 의 와이드 문자 버전 이며, *strsource* 인수는 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 동작합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull** 는 다음과 같은 형식의 문자열을 가리키는 *strsource* 가 필요 합니다.

> [*공백*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*숫자*  &#124; *문자*]

공백은 무시 되는 공백과 탭 문자로 구성 *될 수 있습니다* . *숫자* 는 하나 이상의 10 진수입니다. *문자* 는 하나 이상의 문자 ' a ' ~ ' z ' (또는 ' a ' ~ ' z ')입니다. 이 형식에 맞지 않는 첫 번째 문자가 발견되면 검색이 중지됩니다. *Base* 가 2에서 36 사이인 경우 숫자의 밑으로 사용 됩니다. *Base* 가 0 인 경우 *strsource* 가 가리키는 문자열의 초기 문자를 사용 하 여 밑을 결정 합니다. 첫 번째 문자가 '0'이고 두 번째 문자가 'x' 또는 'X'가 아니면 문자열은 8진수 정수로 해석됩니다. 첫 번째 문자가 '0'이고 두 번째 문자가 'x' 또는 'X'이면 문자열은 16진수 정수로 해석됩니다. 첫 번째 문자가 '1'~'9' 이면 문자열은 10진수 정수로 해석됩니다. 문자 'a'~'z' 또는 'A'~'Z'에는 값 10~35가 할당됩니다. 할당된 값이 *밑* 보다 작은 문자만 사용할 수 있습니다. 밑의 범위를 벗어난 첫 번째 문자가 발견되면 검색이 중지됩니다. 예를 들어 *base* 가 0이 고 검색 된 첫 번째 문자가 ' 0 ' 이면 8 진수 정수로 간주 되며 ' 8 ' 또는 ' 9 ' 문자는 검색을 중지 합니다. **strtoull** 에서는 더하기 기호 ( **+** ) 또는 빼기 기호 () 접두사를 사용할 수 있습니다. **-** 선행 빼기 기호는 반환 값이 부정 됨을 나타냅니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull**|\<stdlib.h> 또는 \<wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[strtod](strtod-strtod-l-wcstod-wcstod-l.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[문자열-숫자 값 함수](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
