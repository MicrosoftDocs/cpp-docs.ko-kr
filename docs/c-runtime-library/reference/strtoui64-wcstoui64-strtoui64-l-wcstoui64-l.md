---
description: '자세한 정보: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l'
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 4/2/2020
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
- _o__strtoui64
- _o__strtoui64_l
- _o__wcstoui64
- _o__wcstoui64_l
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: 8f8ab4663ab64b5b3f6787b5514cf1d0f779680f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124854"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

문자열을 값으로 변환 **`unsigned __int64`** 합니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
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

**_strtoui64** 는 표현이 오버플로를 발생 시키는 경우를 제외 하 고 **_UI64_MAX** 를 반환 하는 경우를 제외 하 고 문자열 *strsource* 에 표시 된 값을 반환 합니다. 변환을 수행할 수 없는 경우 **_strtoui64** 는 0을 반환 합니다.

**_UI64_MAX** 는 LIMITS에 정의 되어 있습니다.

*Strsource* 가 **NULL** 이거나 *기본* 가 0이 아니고 2 보다 작거나 36 보다 큰 경우 **errno** 은 **EINVAL** 로 설정 됩니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Strtoui64** 함수는 *strsource* 를로 변환 합니다 **`unsigned __int64`** . **_wcstoui64** 은 **_strtoui64** 의 와이드 문자 버전입니다. *Strsource* 인수는 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 동작합니다.

두 함수는 숫자의 일부분으로 인식할 수 없는 첫 번째 문자에서 문자열 *Strsource* 의 읽기를 중지 합니다. 이 문자는 종료 null 문자일 수도 있고 *base* 보다 크거나 같은 첫 번째 숫자 문자일 수도 있습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

현재 로캘의 **LC_NUMERIC** 범주 설정은 *strsource* 의 기 하 문자 인식 여부를 결정 합니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조 하세요. _L 접미사가 없는 함수는 현재 로캘을 사용 합니다. **_strtoui64_l** 및 **_wcstoui64_l** 은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고는 **_l** 접미사가 없는 해당 함수와 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

*Endptr* 이 **NULL** 이 아닌 경우 검색을 중지 한 문자에 대 한 포인터는 *endptr* 에서 가리키는 위치에 저장 됩니다. 올바른 숫자를 찾을 수 없거나 잘못 된 밑을 지정 하 여 변환을 수행할 수 없는 경우 *Strsource* 의 값은 *endptr* 에서 가리키는 위치에 저장 됩니다.

**_strtoui64** 는 다음과 같은 형식의 문자열을 가리키는 *strsource* 가 필요 합니다.

> [*공백*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*숫자*  &#124; *문자*]

공백은 무시 되는 공백과 탭 문자로 구성 *될 수 있습니다* . *숫자* 는 하나 이상의 10 진수입니다. *문자* 는 하나 이상의 문자 ' a ' ~ ' z ' (또는 ' a ' ~ ' z ')입니다. 이 형식에 맞지 않는 첫 번째 문자가 발견되면 검색이 중지됩니다. *Base* 가 2에서 36 사이인 경우 숫자의 밑으로 사용 됩니다. *Base* 가 0 인 경우 *strsource* 가 가리키는 문자열의 초기 문자를 사용 하 여 밑을 결정 합니다. 첫 번째 문자가 0이고 두 번째 문자가 'x' 또는 'X'가 아니면 문자열은 8진수 정수로 해석됩니다. 첫 번째 문자가 '0'이고 두 번째 문자가 'x' 또는 'X'이면 문자열은 16진수 정수로 해석됩니다. 첫 번째 문자가 '1'~'9' 이면 문자열은 10진수 정수로 해석됩니다. 문자 'a'~'z' 또는 'A'~'Z'에는 값 10~35가 할당됩니다. 할당된 값이 *밑* 보다 작은 문자만 사용할 수 있습니다. 밑의 범위를 벗어난 첫 번째 문자가 발견되면 검색이 중지됩니다. 예를 들어 *base* 가 0이 고 검색 된 첫 번째 문자가 ' 0 ' 이면 8 진수 정수로 간주 되며 ' 8 ' 또는 ' 9 ' 문자는 검색을 중지 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> 또는 \<wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[문자열-숫자 값 함수](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
