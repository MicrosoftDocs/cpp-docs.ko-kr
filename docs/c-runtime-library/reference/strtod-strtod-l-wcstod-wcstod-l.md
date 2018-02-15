---
title: _strtod_l, strtod, wcstod, _wcstod_l | Microsoft Docs
ms.custom: 
ms.date: 10/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
apilocation:
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
apitype: DLLExport
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
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe18737b52ba2b04e3ee09813c6b48b6ebdf0363
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod, _strtod_l, wcstod, _wcstod_l

문자열을 배정밀도 값으로 변환합니다.

## <a name="syntax"></a>구문

```C
double strtod(
   const char *nptr,
   char **endptr
);
double _strtod_l(
   const char *nptr,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *nptr,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *nptr,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*nptr*  
변환할 Null 종료 문자열입니다.

*endptr*  
검색을 중지하는 문자에 대한 포인터입니다.

*locale*  
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

`strtod` 부동 소수점 숫자 표현을 + /-경우 함수를 반환 하는 오버플로 인해 경우를 제외 하 고 값을 반환`HUGE_VAL`합니다. `HUGE_VAL`의 부호는 표현할 수 없는 값의 부호와 일치합니다. 변환을 수행할 수 없거나 언더플로가 발생하면 `strtod`는 0을 반환합니다.

`wcstod`는 `strtod`와 동일한 값을 반환합니다. 오버플로나 언더플로가 발생하면 두 함수에 대해 `errno`가 `ERANGE`로 설정되며 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

각 함수는 입력된 문자열을 변환 *nptr* 에 `double`합니다. `strtod` 변환 함수 *nptr* 배정도 값으로. `strtod` 읽기를 중단 *nptr* 숫자의 일환으로 인식할 수 없는 첫 번째 문자에서 합니다. 이 문자는 종료 null 문자일 수 있습니다. `wcstod` 와이드 문자 버전이 `strtod`; 해당 *nptr* 인수는 와이드 문자 문자열입니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcstod`|`strtod`|`strtod`|`wcstod`|
|`_tcstod_l`|`_strtod_l`|`_strtod_l`|`_wcstod_l`|

`LC_NUMERIC` 현재 로캘 범주 설정에는 내의 지점 기 수 문자 인식 여부 결정 *nptr*합니다. 자세한 내용은 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. 없는 함수는 `_l` 접미사 사용은 현재 로캘; `_strtod_l` 동일 `_strtod_l` 를 사용 하는 점을 제외 하 고는 *로캘* 대신에 전달 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

경우 *endptr* 않습니다 `NULL`, 검색을 중지 하는 문자에 대 한 포인터에서 가리키는 위치에 저장 된 *endptr*합니다. 변환 작업 없이 수행할 수 있으면 (유효 자릿수 없이 발견 된 또는 지정 된 잘못 된 base)의 값 *nptr* 가 가리키는 위치에 저장 된 *endptr*합니다.

`strtod` 에서는 *nptr* 문자열을 다음 형식 중 하나를 가리키도록 합니다.

[*whitespace*] [*sign*] {*digits* [*radix* *digits*] &#124; *radix* *digits*} [{**e** &#124; **E**} [*sign*] *digits*]  
[*whitespace*] [*sign*] {**0x** &#124; **0X**} {*hexdigits* [*radix* *hexdigits*] &#124; *radix* *hexdigits*} [{**p** &#124; **P**} [*sign*] *hexdigits*]  
[*whitespace*] [*sign*] {**INF** &#124; **INFINITY**}  
[*whitespace*] [*sign*] **NAN** [*sequence*]

선택적 앞에 오는 *공백* ; 무시 되는 공백 및 탭 문자가 포함 될 수 *기호* 는 더하기 (+) 또는 빼기 (-); *자릿수* 하나 이상의 10 진수 숫자가; *hexdigits* 는 하나 이상의 16 진수; *기 수* 기 수 지점 문자 하거나 마침표 (.)를 기본 "C" 로캘에서 되었거나 로캘 관련 값은 현재 로캘 차이가 있는 경우 *로캘* 지정 되어 있으면는 *시퀀스* 는 일련의 영숫자 문자를 밑줄 또는 합니다. 10 진수 및 16 진수 숫자 형식의 기 수 지점 문자 앞에 자릿수 없이 표시 하는 경우 하나 이상 나타나야 지점 기 수 문자 뒤 합니다. 10 진수 형식에 10 진수의 기본 문자 구성 된 지 수가 올 수 있습니다 (**e** 또는 **E**) 및 선택적으로 부호 있는 정수입니다. 16 진수 형식 자리 16 진수의 기본 문자 구성 된 지 수가 올 수 있습니다 (**p** 또는 **P**)을 나타내는 부호가 붙은 16 진수 정수는 2의 거듭제곱으로 지 수입니다. 둘 중 하나의 형태로 지 수 부분을 차지 아니고 지점 기 수 문자 표시 되 면 지점 기 수 문자는 문자열에서 마지막 자릿수가 양수인 따르도록 간주 됩니다. 둘 다에서 대/소문자는 무시 됩니다는 **INF** 및 **NAN** 폼입니다. 이러한 폼 중 하나가 적합 하지 않은 첫 번째 문자는 검사를 중지 합니다.

이러한 함수의 UCRT 버전 포트란 스타일의 변환을 지원 하지 않습니다 (**d** 또는 **D**) 지 수의 문자입니다. 이러한 비표준 확장은 CRT의 이전 버전에서 지원되었으므로 코드에 대한 중요한 변경 사항일 수 있습니다. UCRT 버전에서는 16 진수 문자열 및 이전 버전에서 지원 되지 않은 INF 및 NAN 값의 라운드트립을 지원 합니다. 코드의 주요 변경 사항이 발생할 수 있습니다. "0x1a" 문자열을 해석할 수는 예를 들어 `strtod` 26.0 UCRT 버전에서 이전 버전에서는 0.0 아니라 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`strtod`, `_strtod_l`|C: &lt;stdlib.h> C++: &lt;cstdlib> 또는 &lt;stdlib.h> |
|`wcstod`, `_wcstod_l`|C: &lt;stdlib.h> 또는 &lt;wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> 또는 &lt;wchar.h> |

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예

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

[데이터 변환](../../c-runtime-library/data-conversion.md)   
[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)   
[멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
[로캘](../../c-runtime-library/locale.md)   
[문자열을 숫자 값으로 변환하는 함수](../../c-runtime-library/string-to-numeric-value-functions.md)   
[strtol, wcstol, _strtol_l, _wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
[atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
[localeconv](../../c-runtime-library/reference/localeconv.md)   
[_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
[_free_locale](../../c-runtime-library/reference/free-locale.md)