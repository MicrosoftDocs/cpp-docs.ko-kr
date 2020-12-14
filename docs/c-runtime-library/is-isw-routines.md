---
description: '자세히 알아보기: is, isw 루틴'
title: is, isw 루틴
ms.date: 11/04/2016
api_location:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isw
- is
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
ms.openlocfilehash: d9229d2437ea7a7e57178acc5fd40ba2afea043b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246719"
---
# <a name="is-isw-routines"></a>is, isw 루틴

:::row:::
   :::column span="":::
      [isalnum, iswalnum, _isalnum_l, _iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)\
      [isalpha, iswalpha, _isalpha_l, _iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)\
      [isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)\
      [isblank, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)\
      [iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)\
      [iscsym, iscsymf, __iscsym, \_ _iswcsym, \_ _iscsymf, \_ _iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)\
      [_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)\
      [isdigit, iswdigit, _isdigit_l, _iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)
   :::column-end:::
   :::column span="":::
      [isgraph, iswgraph, _isgraph_l, _iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)\
      [isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)\
      [islower, iswlower, _islower_l _iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)\
      [isprint 프린트, iswprint, _isprint_l, _iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)\
      [ispunct, iswpunct, _ispunct_l, _iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)\
      [isspace, iswspace, _isspace_l, _iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)\
      [isupper, _isupper_l, iswupper, _iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)\
      [isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)
   :::column-end:::
:::row-end:::

## <a name="remarks"></a>설명

이러한 루틴은 지정한 조건에 대해 문자를 테스트합니다.

**is** 루틴은 -1(`EOF`)에서 **UCHAR_MAX**(0xFF)(포함)까지 정수 인수에 대해 의미 있는 결과를 생성합니다. 필요한 인수 형식은 **`int`** 입니다.

> [!CAUTION]
> **Is** 루틴의 경우 형식의 인수를 전달 하면 **`char`** 예기치 않은 결과가 발생할 수 있습니다. 0x7F 보다 큰 형식의 SBCS 또는 MBCS 싱글바이트 문자는 **`char`** 음수입니다. **`char`** 이 전달 되 면 컴파일러에서 값을 또는로 변환할 수 있습니다 **`signed int`** **`signed long`** . 이 값은 컴파일러에서 부호 확장될 수 있으며 예기치 않은 결과가 발생할 수 있습니다.

**isw** 루틴은 - 1(**WEOF**)에서 0xFFFF(포함)까지 정수 값에 대해 의미 있는 결과를 생성합니다. **Wint_t** 데이터 형식은 WCHAR에 정의 되어 있습니다. H **`unsigned short`** , 와이드 문자 또는 와이드 문자 끝 (**weof**) 값을 포함할 수 있습니다.

출력 값은 로캘의 `LC_CTYPE` 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. **_l** 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다.

"C" 로캘에서 **is** 루틴에 대한 테스트 조건은 다음과 같습니다.

`isalnum`<br/>
영숫자(A-Z, a-z 또는 0-9)

`isalpha`<br/>
알파벳(A-Z 또는 a-z)

`__isascii`<br/>
ASCII 문자(0x00-0x7F)

`isblank`<br/>
가로 탭 또는 공백 문자(0x09 또는 0x20)

`iscntrl`<br/>
제어 문자(0x00 - 0x1F 또는 0x7F)

`__iscsym`<br/>
문자, 밑줄 또는 숫자

`__iscsymf`<br/>
문자 또는 밑줄

`isdigit`<br/>
10진수(0-9)

`isgraph`<br/>
공백을 제외한 인쇄 가능한 문자()

`islower`<br/>
소문자(a ~ z)

`isprint`<br/>
공백을 포함한 인쇄 가능한 문자(0x20-0x7E)

`ispunct`<br/>
문장 부호 문자

`isspace`<br/>
공백 문자(0x09-0x0D 또는 0x20)

`isupper`<br/>
대문자(A ~ Z)

`isxdigit`<br/>
16진수(A-F, a-f 또는 0-9)

**isw** 루틴의 경우 지정된 조건의 테스트 결과는 로캘과 무관합니다. **isw** 함수에 대한 테스트 조건은 다음과 같습니다.

`iswalnum`<br/>
`iswalpha` 또는 `iswdigit`

`iswalpha`<br/>
`iswcntrl`, `iswdigit`, `iswpunct`, `iswspace`가 모두 0인 구현 시 정의된 집합 중 하나인 와이드 문자. `iswalpha`는 `iswupper` 또는 `iswlower`가 0이 아닌 와이드 문자에 대해서는 0이 아닌 값을 반환합니다.

`iswascii`<br/>
ASCII 문자의 와이드 문자 표현(0x0000-0x007F)

`iswblank`<br/>
표준 공백 문자에 해당하거나 `iswalnum`이 false인 경우 구현 시 정의된 와이드 문자 집합 중 하나인 와이드 문자. 표준 공백 문자는 공백(L' ') 및 가로 탭(L'\t')입니다.

`iswcntrl`<br/>
제어 와이드 문자

`__iswcsym`<br/>
`isalnum`가 true인 경우 와이드 문자 또는 '_' 문자

`__iswcsymf`<br/>
`iswalpha`가 true인 경우 와이드 문자 또는 '_' 문자

`iswctype`<br/>
문자에 `desc` 인수에 의해 지정된 속성이 있습니다. 다음 표에 표시된 것처럼, `iswctype`의 `desc` 인수에 유효한 각 값에 대해 해당하는 와이드 문자 분류 루틴이 있습니다.

### <a name="equivalence-of-iswctypec-desc-to-other-isw-testing-routines"></a>기타 isw 테스트 루틴에 대한 iswctype(c, desc) 동등성

|*desc* 인수 값|해당 iswctype( *c, desc* )|
|------------------------------|----------------------------------------|
|**_ALPHA**|**iswalpha (** `c` **)**|
|**_ALPHA** &#124; **_DIGIT**|**iswalnum(** `c` **)**|
|**_BLANK**|**iswblank (** `c` **)**|
|**_CONTROL**|**iswcntrl(** `c` **)**|
|**_DIGIT**|**iswdigit(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph (** `c` **)**|
|**_LOWER**|**iswlower(** `c` **)**|
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint (** `c` **)**|
|**_PUNCT**|**iswpunct (** `c` **)**|
|**_BLANK**|**iswblank (** `c` **)**|
|**_SPACE**|**iswspace(** `c` **)**|
|**_UPPER**|**iswupper(** `c` **)**|
|**_HEX**|**iswxdigit (** `c` **)**|

`iswdigit`<br/>
10진수 문자에 해당하는 와이드 문자

`iswgraph`<br/>
공백 와이드 문자(L' ')를 제외한 인쇄 가능한 와이드 문자

`iswlower`<br/>
소문자이거나 `iswcntrl`, `iswdigit`, `iswpunct`, `iswspace`가 모두 0인 구현 시 정의된 와이드 문자 집합 중 하나. `iswlower`는 소문자에 해당하는 와이드 문자에 대해서만 0이 아닌 값을 반환합니다.

`iswprint`<br/>
공백 와이드 문자(L' ')를 포함한 인쇄 가능한 와이드 문자

`iswpunct`<br/>
`iswalnum`이 0이 아닌 와이드 문자도 공백 와이드 문자(L' ')도 아닌 인쇄 가능한 와이드 문자

`iswspace`<br/>
표준 공백 문자에 해당하거나 `iswalnum`이 false인 경우 구현 시 정의된 와이드 문자 집합 중 하나인 와이드 문자. 표준 공백 문자: 공백(L' '), 용지 공급(L'\f'), 줄 바꿈(L'\n'), 캐리지 리턴(L'\r'), 가로 탭(L'\t'), 세로 탭(L'\v')

`iswupper`<br/>
대문자이거나 `iswcntrl`, `iswdigit`, `iswpunct`, `iswspace`가 모두 0인 구현 시 정의된 와이드 문자 집합 중 하나인 와이드 문자. `iswupper`는 대문자에 해당하는 와이드 문자에 대해서만 0이 아닌 값을 반환합니다.

`iswxdigit`<br/>
16진수 문자에 해당하는 와이드 문자

## <a name="example"></a>예제

```C
// crt_isfam.c
/* This program tests all characters between 0x0
* and 0x7F, then displays each character with abbreviations
* for the character-type codes that apply.
*/

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   for( ch = 0; ch <= 0x7F; ch++ )
   {
      printf( "%.2x  ", ch );
      printf( " %c", isprint( ch )  ? ch   : ' ' );
      printf( "%4s", isalnum( ch )  ? "AN" : "" );
      printf( "%3s", isalpha( ch )  ? "A"  : "" );
      printf( "%3s", __isascii( ch )  ? "AS" : "" );
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );
      printf( "%3s", isdigit( ch )  ? "D"  : "" );
      printf( "%3s", isgraph( ch )  ? "G"  : "" );
      printf( "%3s", islower( ch )  ? "L"  : "" );
      printf( "%3s", ispunct( ch )  ? "PU" : "" );
      printf( "%3s", isspace( ch )  ? "S"  : "" );
      printf( "%3s", isprint( ch )  ? "PR" : "" );
      printf( "%3s", isupper( ch )  ? "U"  : "" );
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );
      printf( ".\n" );
   }
}
```

## <a name="output"></a>출력

```Output
00            AS  C                              .
01            AS  C                              .
02            AS  C                              .
03            AS  C                              .
04            AS  C                              .
05            AS  C                              .
06            AS  C                              .
07            AS  C                              .
08            AS  C                              .
09            AS  C                    S         .
0a            AS  C                    S         .
0b            AS  C                    S         .
0c            AS  C                    S         .
0d            AS  C                    S         .
0e            AS  C                              .
0f            AS  C                              .
10            AS  C                              .
11            AS  C                              .
12            AS  C                              .
13            AS  C                              .
14            AS  C                              .
15            AS  C                              .
16            AS  C                              .
17            AS  C                              .
18            AS  C                              .
19            AS  C                              .
1a            AS  C                              .
1b            AS  C                              .
1c            AS  C                              .
1d            AS  C                              .
1e            AS  C                              .
1f            AS  C                              .
20            AS                       S PR      .
21   !        AS              G    PU    PR      .
22   "        AS              G    PU    PR      .
23   #        AS              G    PU    PR      .
24   $        AS              G    PU    PR      .
25   %        AS              G    PU    PR      .
26   &        AS              G    PU    PR      .
27   '        AS              G    PU    PR      .
28   (        AS              G    PU    PR      .
29   )        AS              G    PU    PR      .
2a   *        AS              G    PU    PR      .
2b   +        AS              G    PU    PR      .
2c   ,        AS              G    PU    PR      .
2d   -        AS              G    PU    PR      .
2e   .        AS              G    PU    PR      .
2f   /        AS              G    PU    PR      .
30   0  AN    AS   CS      D  G          PR     X.
31   1  AN    AS   CS      D  G          PR     X.
32   2  AN    AS   CS      D  G          PR     X.
33   3  AN    AS   CS      D  G          PR     X.
34   4  AN    AS   CS      D  G          PR     X.
35   5  AN    AS   CS      D  G          PR     X.
36   6  AN    AS   CS      D  G          PR     X.
37   7  AN    AS   CS      D  G          PR     X.
38   8  AN    AS   CS      D  G          PR     X.
39   9  AN    AS   CS      D  G          PR     X.
3a   :        AS              G    PU    PR      .
3b   ;        AS              G    PU    PR      .
3c   <        AS              G    PU    PR      .
3d   =        AS              G    PU    PR      .
3e   >        AS              G    PU    PR      .
3f   ?        AS              G    PU    PR      .
40   @        AS              G    PU    PR      .
41   A  AN  A AS   CS CSF     G          PR  U  X.
42   B  AN  A AS   CS CSF     G          PR  U  X.
43   C  AN  A AS   CS CSF     G          PR  U  X.
44   D  AN  A AS   CS CSF     G          PR  U  X.
45   E  AN  A AS   CS CSF     G          PR  U  X.
46   F  AN  A AS   CS CSF     G          PR  U  X.
47   G  AN  A AS   CS CSF     G          PR  U   .
48   H  AN  A AS   CS CSF     G          PR  U   .
49   I  AN  A AS   CS CSF     G          PR  U   .
4a   J  AN  A AS   CS CSF     G          PR  U   .
4b   K  AN  A AS   CS CSF     G          PR  U   .
4c   L  AN  A AS   CS CSF     G          PR  U   .
4d   M  AN  A AS   CS CSF     G          PR  U   .
4e   N  AN  A AS   CS CSF     G          PR  U   .
4f   O  AN  A AS   CS CSF     G          PR  U   .
50   P  AN  A AS   CS CSF     G          PR  U   .
51   Q  AN  A AS   CS CSF     G          PR  U   .
52   R  AN  A AS   CS CSF     G          PR  U   .
53   S  AN  A AS   CS CSF     G          PR  U   .
54   T  AN  A AS   CS CSF     G          PR  U   .
55   U  AN  A AS   CS CSF     G          PR  U   .
56   V  AN  A AS   CS CSF     G          PR  U   .
57   W  AN  A AS   CS CSF     G          PR  U   .
58   X  AN  A AS   CS CSF     G          PR  U   .
59   Y  AN  A AS   CS CSF     G          PR  U   .
5a   Z  AN  A AS   CS CSF     G          PR  U   .
5b   [        AS              G    PU    PR      .
5c   \        AS              G    PU    PR      .
5d   ]        AS              G    PU    PR      .
5e   ^        AS              G    PU    PR      .
5f   _        AS   CS CSF     G    PU    PR      .
60   `        AS              G    PU    PR      .
61   a  AN  A AS   CS CSF     G  L       PR     X.
62   b  AN  A AS   CS CSF     G  L       PR     X.
63   c  AN  A AS   CS CSF     G  L       PR     X.
64   d  AN  A AS   CS CSF     G  L       PR     X.
65   e  AN  A AS   CS CSF     G  L       PR     X.
66   f  AN  A AS   CS CSF     G  L       PR     X.
67   g  AN  A AS   CS CSF     G  L       PR      .
68   h  AN  A AS   CS CSF     G  L       PR      .
69   i  AN  A AS   CS CSF     G  L       PR      .
6a   j  AN  A AS   CS CSF     G  L       PR      .
6b   k  AN  A AS   CS CSF     G  L       PR      .
6c   l  AN  A AS   CS CSF     G  L       PR      .
6d   m  AN  A AS   CS CSF     G  L       PR      .
6e   n  AN  A AS   CS CSF     G  L       PR      .
6f   o  AN  A AS   CS CSF     G  L       PR      .
70   p  AN  A AS   CS CSF     G  L       PR      .
71   q  AN  A AS   CS CSF     G  L       PR      .
72   r  AN  A AS   CS CSF     G  L       PR      .
73   s  AN  A AS   CS CSF     G  L       PR      .
74   t  AN  A AS   CS CSF     G  L       PR      .
75   u  AN  A AS   CS CSF     G  L       PR      .
76   v  AN  A AS   CS CSF     G  L       PR      .
77   w  AN  A AS   CS CSF     G  L       PR      .
78   x  AN  A AS   CS CSF     G  L       PR      .
79   y  AN  A AS   CS CSF     G  L       PR      .
7a   z  AN  A AS   CS CSF     G  L       PR      .
7b   {        AS              G    PU    PR      .
7c   |        AS              G    PU    PR      .
7d   }        AS              G    PU    PR      .
7e   ~        AS              G    PU    PR      .
7f            AS  C                              .
```

## <a name="see-also"></a>참조

[문자 분류](../c-runtime-library/character-classification.md)<br/>
[로캘](../c-runtime-library/locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[to 함수](../c-runtime-library/to-functions.md)
