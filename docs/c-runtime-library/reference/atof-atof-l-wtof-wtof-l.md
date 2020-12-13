---
description: Atof, _atof_l, _wtof, _wtof_l에 대해 자세히 알아보세요.
title: atof, _atof_l, _wtof, _wtof_l
ms.date: 4/2/2020
api_name:
- _wtof_l
- atof
- _atof_l
- _wtof
- _o__atof_l
- _o__wtof
- _o__wtof_l
- _o_atof
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
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
ms.openlocfilehash: b583b4d443264d82fa83124f4dacd597fe8829b6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337781"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof, _atof_l, _wtof, _wtof_l

문자열을 double로 변환합니다.

## <a name="syntax"></a>구문

```C
double atof(
   const char *str
);
double _atof_l(
   const char *str,
   _locale_t locale
);
double _wtof(
   const wchar_t *str
);
double _wtof_l(
   const wchar_t *str,
   _locale_t locale
);
```

## <a name="parameters"></a>매개 변수

*str*<br/>
변환할 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

각 함수는 **`double`** 입력 문자를 숫자로 해석 하 여 생성 된 값을 반환 합니다. 입력이 이 형식의 값으로 변환될 수 없는 경우 반환 값은 0.0입니다.

범위를 벗어난 모든 경우에는 **errno** 가 **ERANGE** 로 설정 됩니다. 전달 된 매개 변수가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고 0을 반환 합니다.

## <a name="remarks"></a>설명

이러한 함수는 문자열을 배정밀도 부동 소수점 값으로 변환합니다.

입력 문자열은 지정된 형식의 숫자 값으로 해석될 수 있는 문자 시퀀스입니다. 함수는 숫자의 일부로 인식할 수 없는 첫 번째 문자에서 입력 문자열 읽기를 중지합니다. 이 문자는 문자열을 종결하는 null 문자('\0' 또는 L'\0')일 수 있습니다.

**Atof** 및 **_wtof** 에 대 한 *str* 인수 형식은 다음과 같습니다.

[*공백*] [*sign*] [*숫자*] [__.__ *숫자*] [{**e** &#124; **e** } [*sign*]*숫자*]

공백은 무시 되는 공백 또는 탭 *문자로 구성 됩니다* . *sign* 은 더하기 (+) 또는 빼기 (-) 중 하나입니다. 및 *숫자* 는 하나 이상의 10 진수입니다. 소수점 앞에 숫자가 없는 경우 소수점 뒤에는 하나 이상 있어야 합니다. 10 진수 뒤에는 기본 문자 (**e** 또는 **e**)와 선택적으로 부호 있는 10 진수 정수로 구성 된 지수가 올 수 있습니다.

이러한 함수의 버전 간 RT 버전은 포트란 스타일 (**d** 또는 **d**) 지 수 문자의 변환을 지원 하지 않습니다. 이러한 비표준 확장은 CRT의 이전 버전에서 지원되었으므로 코드에 대한 중요한 변경 사항일 수 있습니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 로캘 대신 전달 된 *로캘* 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|------------------|---------------------|
|**atof**, **_atof_l**|C: \<math.h> 또는 \<stdlib.h> c + +: \<cstdlib> , \<stdlib.h> \<cmath> 또는 \<math.h>|
|**_wtof**, **_wtof_l**|C: \<stdlib.h> 또는 \<wchar.h> c + +: \<cstdlib> , \<stdlib.h> 또는 \<wchar.h>|

## <a name="example"></a>예제

이 프로그램은 **atof** 및 **_atof_l** 함수를 사용 하 여 문자열로 저장 된 숫자를 숫자 값으로 변환할 수 있는 방법을 보여 줍니다.

```C
// crt_atof.c
//
// This program shows how numbers stored as
// strings can be converted to numeric
// values using the atof and _atof_l functions.

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function
    // using leading and training spaces.
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function
    // using the 'E' exponential formatting keyword.
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions
    // using the 'e' exponential formatting keyword
    // and showing different decimal point interpretations.
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}
```

```Output
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25
```

## <a name="see-also"></a>참고 항목

[데이터 변환](../../c-runtime-library/data-conversion.md)<br/>
[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
