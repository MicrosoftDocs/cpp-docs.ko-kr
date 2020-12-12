---
description: Printf_p 위치 매개 변수에 대해 자세히 알아보세요.
title: printf_p 위치 매개 변수
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
ms.openlocfilehash: 2db76bc937e52b5945bf39cab1f47161fd3b162c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213431"
---
# <a name="printf_p-positional-parameters"></a>printf_p 위치 매개 변수

위치 매개 변수를 사용하면 형식 문자열의 필드로 대체되는 인수의 기준 숫자를 지정할 수 있습니다. 다음 위치 매개 변수 `printf` 함수를 사용할 수 있습니다.

| 비위치 printf 함수 | 해당하는 위치 매개 변수 |
|---|---|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|
|[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|
|[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|
|[vprintf, _vprintf_l, vwprintf, _vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|
|[vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, \_ _vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|

## <a name="how-to-specify-positional-parameters"></a>위치 매개 변수 지정 방법

### <a name="parameter-indexing"></a>매개 변수 인덱스

기본적으로 위치 형식이 없는 경우 위치 함수는 위치 매개 변수가 아닌 매개 변수와 동일하게 동작합니다. 형식 지정자의 시작 부분에 있는 `%n$`를 사용하여 형식을 지정할 위치 매개 변수를 지정합니다. 여기서 `n`은 매개 변수 목록에서 형식을 지정할 매개 변수의 위치입니다. 매개 변수 위치는 형식 문자열 뒤에 나오는 첫 번째 인수부터 1로 지정됩니다. 형식 지정자의 나머지 부분은 `printf` 형식 지정자와 동일한 규칙을 따릅니다. 형식 지정자에 대한 자세한 내용은 [형식 사양 구문: printf 및 wprintf 함수](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)를 참조하세요.

위치 형식 지정의 예는 다음과 같습니다.

```C
_printf_p("%1$s %2$s", "November", "10");
```

다음이 출력됩니다.

```
November 10
```

사용되는 숫자의 순서는 인수의 순서와 일치할 필요가 없습니다. 예를 들어 다음은 유효한 형식 문자열입니다.

```C
_printf_p("%2$s %1$s", "November", "10");
```

다음이 출력됩니다.

```
10 November
```

기존의 형식 문자열과 달리, 위치 매개 변수는 한 형식 문자열에 두 번 이상 사용될 수 있습니다. 예를 들면 다음과 같습니다.

```C
_printf_p("%1$d times %1$d is %2$d", 10, 100);
```

다음이 출력됩니다.

```
10 times 10 is 100
```

모든 인수를 형식 문자열에서 한 번 이상 사용해야 합니다. 형식 문자열에 허용되는 위치 매개 변수의 최대 수는 `_ARGMAX`로 지정합니다.

### <a name="width-and-precision"></a>너비 및 전체 자릿수

`*n$`를 사용하여 위치 매개 변수를 너비 또는 전체 자릿수로 지정할 수 있습니다. 여기서 `n`은 매개 변수 목록에서 너비 또는 전체 자릿수 매개 변수의 위치입니다. 너비 또는 전체 자릿수 값의 위치는 \* 기호 바로 다음에 나와야 합니다. 예를 들면 다음과 같습니다.

```C
_printf_p("%1$*2$s","Hello", 10);
```

또는

```C
_printf_p("%2$*1$s", 10, "Hello");
```

### <a name="mixing-positional-and-non-positional-arguments"></a>위치 인수 및 비위치 인수 혼합

위치 매개 변수는 동일한 형식 문자열에서 비 위치 매개 변수와 함께 혼합할 수 없습니다. 위치 형식이 사용되는 경우 모든 형식 지정자는 위치 서식을 사용해야 합니다. 그러나 `printf_p` 및 관련 함수는 비 위치 매개 변수를 포함하는 형식 문자열에서 계속해서 비 위치 매개 변수를 지합니다.

## <a name="example"></a>예제

```C
// positional_args.c
// Build by using: cl /W4 positional_args.c
// Positional arguments allow the specification of the order
// in which arguments are consumed in a formatting string.

#include <stdio.h>

int main()
{
    int     i = 1,
            j = 2,
            k = 3;
    double  x = 0.1,
            y = 2.22,
            z = 333.3333;
    char    *s1 = "abc",
            *s2 = "def",
            *s3 = "ghi";

    // If positional arguments are unspecified,
    // normal input order is used.
    _printf_p("%d %d %d\n", i, j, k);

    // Positional arguments are numbers followed by a $ character.
    _printf_p("%3$d %1$d %2$d\n", i, j, k);

    // The same positional argument may be reused.
    _printf_p("%1$d %2$d %1$d\n", i, j);

    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);

    // Precision and width specifiers must be int types.
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);
}
```

```Output
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```

## <a name="see-also"></a>참고 항목

[형식 사양 구문: printf 및 wprintf 함수](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)
