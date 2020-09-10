---
title: strtod, _strtod_l, wcstod, _wcstod_l
description: Strtod, _strtod_l, wcstod 및 _wcstod_l에 대 한 API 참조 문자열을 배정밀도 값으로 변환 하는입니다.
ms.date: 08/27/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
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
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: 1e75fe39c8ab7020a088307421926327d4043ba8
ms.sourcegitcommit: efed9ed109862c6c2a042f2663b680e8ca4e16a1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89933829"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod, _strtod_l, wcstod, _wcstod_l

문자열을 배정밀도 값으로 변환합니다.

## <a name="syntax"></a>구문

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*strSource*<br/>
변환할 Null 종료 문자열입니다.

*endptr*<br/>
검색을 중지하는 문자에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**strtod** 는 표현이 오버플로를 발생 시키는 경우를 제외 하 고 부동 소수점 숫자의 값을 반환 합니다 .이 경우 함수는 +/-**HUGE_VAL**을 반환 합니다. **HUGE_VAL** 부호는 표현할 수 없는 값의 부호와 일치 합니다. **strtod** `0` 변환을 수행할 수 없거나 언더플로가 발생 하는 경우 strtod는를 반환 합니다.

**wcstod** 는와 유사 값을 **strtod**로 반환 합니다.

- 두 함수 모두 오버플로 또는 언더플로가 발생 하는 경우 **errno** 는 **ERANGE** 로 설정 됩니다.
- 매개 변수가 잘못 된 경우 **errno** 가 **EINVAL** 로 설정 되 고 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다.

이 코드 및 기타 반환 코드에 대 한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요.

## <a name="remarks"></a>설명

각 함수는 입력 문자열 *Strsource* 를로 변환 **`double`** 합니다. **Strtod** 함수는 *strsource* 를 배정밀도 값으로 변환 합니다. **strtod** 는 숫자의 일부분으로 인식할 수 없는 첫 번째 문자에서 문자열 *strsource* 의 읽기를 중지 합니다. 이 문자는 null 종결 문자일 수 있습니다. **wcstod** 은 **strtod**;의 와이드 문자 버전입니다. *Strsource* 인수는 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

현재 로캘의 **LC_NUMERIC** 범주 설정은 *strsource*의 기 하 점 문자 인식 여부를 결정 합니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요. **_L** 접미사가 없는 함수는 현재 로캘을 사용 합니다. **_strtod_l** 은 이전에 전달 된 *로캘을* 대신 사용 한다는 점을 제외 하 고 **_strtod** 와 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

*Endptr* 이 **NULL**이 아닌 경우 검색을 중지 한 문자에 대 한 포인터는 *endptr*에서 가리키는 위치에 저장 됩니다. 올바른 숫자를 찾을 수 없거나 잘못 된 밑을 지정 하 여 변환을 수행할 수 없는 경우 *Strsource* 의 값은 *endptr*에서 가리키는 위치에 저장 됩니다.

**strtod** 는 다음 형식 중 하나의 문자열을 가리키는 *strsource* 가 필요 합니다.

[*공백*] [*sign*] {*숫자* [*기* 하 *자릿수*] &#124; *기* 하 *숫자*} [{**e** &#124; **e**} [*sign*] *자릿수*] [*공백*] [*sign*] {**0x** &#124; **0x**} {*hexdigits* [*기* *hexdigits*] &#124; *기* 수가 *hexdigits*} [**{p** &#124; **p**}*[sign*] *자릿수*] [*공백*] [*sign*] {**INF** &#124; **INFINITY**} [*공백*] [*sign*] **NAN** [*시퀀스*]

선행 *공백* (옵션)은 공백과 탭 문자로 구성 될 수 있으며이는 무시 됩니다.
*부호* 는 더하기 (+) 또는 빼기 (-)입니다.
*숫자가* 하나 이상의 10 진수입니다.
*hexdigits* 는 하나 이상의 16 진수입니다.
*기* 수는 기 수 점 문자 (기본 "C" 로캘의 마침표 (.), 현재 로캘이 다른 경우 또는 *로캘이* 지정 된 경우 로캘별 값)입니다.
 *시퀀스* 는 영숫자 또는 밑줄 문자의 시퀀스입니다.

10 진수 및 16 진수 형식 모두에서 기 수 지점 문자 앞에 숫자가 표시 되지 않으면 하나 이상이 기 수 점 문자 뒤에와 야 합니다. 

Decimal 형식에서 10 진수 뒤에는 기본 문자 (**e** 또는 **e**)와 선택적으로 부호 있는 정수로 구성 된 지수가 올 수 있습니다. 

16 진수 형식에서는 16 진수 뒤에 지수가 올 수 있습니다. 여기에는 소개 문자 (**p** 또는 **p**)와 지 수를 2의 거듭제곱으로 나타내는 선택적으로 부호 있는 10 진수 정수로 구성 됩니다.

두 형식 모두, 지 수 부분이 나 기 수 지점 문자가 없는 경우 문자열의 마지막 숫자를 따르는 기 수 지점 문자를 가정 합니다.

Case는 **INF** 및 **NAN** 형식 모두에서 무시 됩니다. 이러한 형식 중 하나에 맞지 않는 첫 번째 문자는 검색을 중지 합니다.

이러한 함수의 버전 간 RT 버전은 포트란 스타일 (**d** 또는 **d**) 지 수 문자의 변환을 지원 하지 않습니다. 이러한 비표준 확장은 CRT의 이전 버전에서 지원되었으므로 코드에 대한 중요한 변경 사항일 수 있습니다. 버전 간 RT 버전은 이전 버전에서 지원 되지 않는 16 진수 문자열 및 INF 및 NAN 값의 라운드트립을 지원 합니다. 이로 인해 코드의 주요 변경 사항이 발생할 수도 있습니다. 예를 들어 문자열 "0x1a"는 이전 버전에서 0.0으로 **strtod** 에 의해 해석 되지만, 이전 버전에서는 26.0로 해석 됩니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> 또는 &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C: &lt;stdlib.h> 또는 &lt;wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> 또는 &lt;wchar.h> |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[멀티 바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[문자열-숫자 값 함수](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
