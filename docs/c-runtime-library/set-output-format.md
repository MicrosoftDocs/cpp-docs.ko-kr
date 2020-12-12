---
description: '다음에 대 한 자세한 정보: _set_output_format'
title: _set_output_format
ms.date: 11/04/2016
api_name:
- _set_output_format
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_output_format
- _set_output_format
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
ms.openlocfilehash: d0e45f4f7ce2a6837bce1e583ec3afd5a70f108a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277182"
---
# <a name="_set_output_format"></a>_set_output_format

형식이 지정된 I/O 함수에서 사용되는 출력 형식을 사용자 지정합니다.

> [!IMPORTANT]
> 이 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>매개 변수

*format*<br/>
[in] 사용할 형식을 나타내는 값입니다.

## <a name="return-value"></a>반환 값

이전 출력 형식입니다.

## <a name="remarks"></a>설명

`_set_output_format`은 [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)와 같은 형식이 지정된 I/O 함수의 출력을 구성하는 데 사용됩니다. 현재, 이 함수에 의해 변경될 수 있는 형식 규칙은 부동 소수점 숫자의 출력에서 지수에 표시되는 자릿수뿐입니다.

기본적으로 `printf_s`, `wprintf_s`및 Visual C++ 표준 C 라이브러리의 관련 함수와 같은 함수에 의한 부동 소수점 숫자의 출력은 지수의 값을 나타내는 데 세 자리 숫자가 필요하지 않은 경우에도 지수에 대해 세 자리 숫자를 출력합니다. 0을 사용하여 값을 3자리까지 채웁니다. `_set_output_format` 을 사용하면 지수의 크기에 따라 세 번째 숫자가 필요한 경우가 아닌 한 지수에 두 자리 숫자만 인쇄되도록 이 동작을 변경할 수 있습니다.

두 자리 지수를 사용하도록 설정하려면 예제와 같이 `_TWO_DIGIT_EXPONENT`매개 변수를 사용하여 이 함수를 호출합니다. 두 자리 지수를 사용하지 않도록 설정하려면 인수 0을 사용하여 이 함수를 호출합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

호환성에 대한 자세한 내용은 소개 단원의 [호환성](../c-runtime-library/compatibility.md) 부분을 참조하세요.

## <a name="example"></a>예제

```C
// crt_set_output_format.c
#include <stdio.h>

void printvalues(double x, double y)
{
   printf_s("%11.4e %11.4e\n", x, y);
   printf_s("%11.4E %11.4E\n", x, y);
   printf_s("%11.4g %11.4g\n", x, y);
   printf_s("%11.4G %11.4G\n", x, y);
}

int main()
{
   double x = 1.211E-5;
   double y = 2.3056E-112;
   unsigned int old_exponent_format;

   // Use the default format
   printvalues(x, y);

   // Enable two-digit exponent format
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);

   printvalues(x, y);

   // Disable two-digit exponent format
   _set_output_format( old_exponent_format );

   printvalues(x, y);
}
```

```Output
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
1.2110e-05 2.3056e-112
1.2110E-05 2.3056E-112
  1.211e-05  2.306e-112
  1.211E-05  2.306E-112
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
```

## <a name="see-also"></a>참고 항목

[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
