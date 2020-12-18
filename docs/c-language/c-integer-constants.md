---
description: '자세한 정보: C 정수 상수'
title: C 정수 상수
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 1dbc22a2d4351dbd6d09f555a95380a1fd94619b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182192"
---
# <a name="c-integer-constants"></a>C 정수 상수

‘정수 상수’는 정수 계열 값을 나타내는 10진수(기수 10), 8진수(기수 8) 또는 16진수(기수 16)입니다.  정수 상수는 변경할 수 없는 정수 값을 나타낼 때 사용합니다.

## <a name="syntax"></a>구문

*integer-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*

*octal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*

*hexadecimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*

*hexadecimal-prefix*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**

*nonzero-digit*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*octal-digit*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*hexadecimal-digit*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-long-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*

*unsigned-suffix*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*long-suffix*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*long-long-suffix*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ll LL**

*64-bit-integer-suffix*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**i64 I64**

**i64** 및 **I64** 는 Microsoft 고유의 접미사입니다.

정수 상수는 빼기 기호( **-** )가 앞에 없는 경우 양수입니다. 빼기 기호는 단항 산술 부정 연산자로 해석됩니다. 이 연산자에 대한 자세한 내용은 [단항 산술 연산자](../c-language/unary-arithmetic-operators.md)를 참조하세요.

정수 상수가 **0x** 또는 **0X** 로 시작되는 경우 16진수이고, 숫자 **0** 으로 시작되는 경우에는 8진수입니다. 두 경우에 해당하지 않으면 10진수로 간주됩니다.

다음 정수 상수는 같습니다.

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

공백 문자는 정수 상수의 숫자를 구분할 수 없습니다. 다음 예제에서는 몇 가지 유효한 10진수, 8진수 및 16진수 상수를 보여줍니다.

```C
    /* Decimal Constants */
    int                 dec_int    = 28;
    unsigned            dec_uint   = 4000000024u;
    long                dec_long   = 2000000022l;
    unsigned long       dec_ulong  = 4000000000ul;
    long long           dec_llong  = 9000000000LL;
    unsigned long long  dec_ullong = 900000000001ull;
    __int64             dec_i64    = 9000000000002I64;
    unsigned __int64    dec_ui64   = 90000000000004ui64;

    /* Octal Constants */
    int                 oct_int    = 024;
    unsigned            oct_uint   = 04000000024u;
    long                oct_long   = 02000000022l;
    unsigned long       oct_ulong  = 04000000000UL;
    long long           oct_llong  = 044000000000000ll;
    unsigned long long  oct_ullong = 044400000000000001Ull;
    __int64             oct_i64    = 04444000000000000002i64;
    unsigned __int64    oct_ui64   = 04444000000000000004uI64;

    /* Hexadecimal Constants */
    int                 hex_int    = 0x2a;
    unsigned            hex_uint   = 0XA0000024u;
    long                hex_long   = 0x20000022l;
    unsigned long       hex_ulong  = 0XA0000021uL;
    long long           hex_llong  = 0x8a000000000000ll;
    unsigned long long  hex_ullong = 0x8A40000000000010uLL;
    __int64             hex_i64    = 0x4a44000000000020I64;
    unsigned __int64    hex_ui64   = 0x8a44000000000040Ui64;
```

## <a name="see-also"></a>참조

[C 상수](../c-language/c-constants.md)<br/>
