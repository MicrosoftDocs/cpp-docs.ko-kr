---
description: Strtof, _strtof_l, wcstof, _wcstof_l에 대해 자세히 알아보세요.
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: 7a73df80fefb8d86431027650be2ecd236135dfd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322422"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof, _strtof_l, wcstof, _wcstof_l

문자열을 단정밀도 부동 소수점 값으로 변환합니다.

## <a name="syntax"></a>구문

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>매개 변수

*strSource*<br/>
변환할 Null 종료 문자열입니다.

*endptr*<br/>
검색을 중지하는 문자에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**strtof** 는 부동 소수점 숫자의 값을 반환 합니다. 단,이로 인해 오버플로가 발생 하는 경우를 제외 하 고 함수는 +/-**HUGE_VALF** 을 반환 합니다. **HUGE_VALF** 부호는 표현할 수 없는 값의 부호와 일치 합니다. **strtof** 는 변환을 수행할 수 없거나 언더플로가 발생 하는 경우 0을 반환 합니다.

**wcstof** 는와 유사 값을 **strtof** 로 반환 합니다. 두 함수 모두 오버플로 또는 언더플로가 발생 하면 **errno** 가 **ERANGE** 로 설정 되 고 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다.

반환 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

각 함수는 입력 문자열 *Strsource* 를로 변환 **`float`** 합니다. **Strtof** 함수는 *strsource* 를 단 정밀도 값으로 변환 합니다. **strtof** 는 숫자의 일부분으로 인식할 수 없는 첫 번째 문자에서 문자열 *strsource* 읽기를 중지 합니다. 이 문자는 종료 null 문자일 수 있습니다. **wcstof** 는 **strtof** 의 와이드 문자 버전입니다. *Strsource* 인수는 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 동작합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

현재 로캘의 **LC_NUMERIC** 범주 설정은 *strsource* 의 기 하 문자 인식 여부를 결정 합니다. 자세한 내용은 [setlocale, _wsetlocale](setlocale-wsetlocale.md)를 참조 하세요. **_L** 접미사가 없는 함수는 현재 로캘을 사용 합니다. 접미사가 있는 항목은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

*Endptr* 이 **NULL** 이 아닌 경우 검색을 중지 한 문자에 대 한 포인터는 *endptr* 에서 가리키는 위치에 저장 됩니다. 올바른 숫자를 찾을 수 없거나 잘못 된 밑수를 지정 하 여 변환을 수행할 수 없는 경우 *Strsource* 의 값은 *endptr* 에서 가리키는 위치에 저장 됩니다.

**strtof** 는 다음과 같은 형식의 문자열을 가리키는 *strsource* 가 필요 합니다.

[*공백*] [*sign*] [*숫자*] [__.__ *숫자*] [{**e** &#124; **e**} [*sign*] *숫자*]

공백은 무시 되는 공백 및 탭 문자로 구성 *될 수 있습니다* . *sign* 은 더하기 ( **+** ) 또는 빼기 ( **-** )이 고 *숫자* 는 하나 이상의 10 진수입니다. 기수 문자 앞에 숫자가 없는 경우 기수 문자 뒤에는 숫자가 하나 이상 있어야 합니다. 10 진수 뒤에는 기본 문자 (**e** 또는 **e**)와 선택적으로 부호 있는 정수로 구성 된 지수가 올 수 있습니다. 지수 부분과 기수 문자가 모두 없으면 기수 문자는 문자열의 마지막 숫자를 따르는 것으로 간주합니다. 이 형식에 맞지 않는 첫 번째 문자가 발견되면 검색이 중지됩니다.

이러한 함수의 버전 간 RT 버전은 포트란 스타일 (**d** 또는 **d**) 지 수 문자의 변환을 지원 하지 않습니다. 이러한 비표준 확장은 CRT의 이전 버전에서 지원되었으므로 코드에 대한 중요한 변경 사항일 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<stdlib.h> c + +: &lt; b> 또는 \<stdlib.h>|
|**wcstof**, **_wcstof_l**|C: \<stdlib.h> 또는 \<wchar.h> c + +: &lt; b> \<stdlib.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[문자열-숫자 값 함수](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
