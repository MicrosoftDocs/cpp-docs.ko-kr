---
title: div, ldiv, lldiv
description: Microsoft C 런타임 라이브러리 div, ldiv 및 lldiv 함수는 두 정수 값의 몫과 나머지를 계산 합니다.
ms.date: 11/21/2020
api_name:
- div
- ldiv
- lldiv
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
- ldiv
- lldiv
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.openlocfilehash: d87b2e3a84e389be8b14970a3aa611bb288cbec8
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440282"
---
# <a name="div-ldiv-lldiv"></a>`div`, `ldiv`, `lldiv`

두 정수 값의 몫과 나머지를 계산합니다.

## <a name="syntax"></a>구문

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>매개 변수

*`numer`*\
분자입니다.

*`denom`*\
분모입니다.

## <a name="return-value"></a>반환 값

**`div`** 형식의 인수를 사용 하 여 호출 된는 **`int`** 몫과 나머지를 포함 하는 형식의 구조체를 반환 합니다 `div_t` . 형식의 인수를 포함 하는 반환 값은 이며 **`long`** `ldiv_t` , 형식의 인수를 포함 하는 반환 값은 **`long long`** `lldiv_t` 입니다. `div_t`, `ldiv_t` 및 `lldiv_t` 형식은에 정의 되어 \<stdlib.h> 있습니다.

## <a name="remarks"></a>설명

**`div`** 함수는를 *`numer`* 로 나누고 *`denom`* 몫과 나머지를 계산 합니다. 구조체에는 [`div_t`](../../c-runtime-library/standard-types.md) 몫, `quot` 및 나머지가 포함 `rem` 됩니다. 몫의 부호는 수학적 몫의 부호와 같습니다. 절대 값은 수학적 몫의 절대 값 보다 작은 가장 큰 정수입니다. 분모가 0이면 프로그램이 종료되고 오류 메시지가 표시됩니다.

**`div`** 또는 형식의 인수를 사용 하는의 오버 로드는 **`long`** **`long long`** c + + 코드 에서만 사용할 수 있습니다. 반환 형식 및에는 [`ldiv_t`](../../c-runtime-library/standard-types.md) [`lldiv_t`](../../c-runtime-library/standard-types.md) `quot` `rem` 의 멤버와 동일한 의미를 갖는 및 멤버가 포함 되어 있습니다 `div_t` .

## <a name="requirements"></a>요구 사항

| 루틴에서 반환된 값 | 필수 헤더 |
|--|--|
| **`div`**, **`ldiv`**, **`lldiv`** | \<stdlib.h> |

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)\
[`imaxdiv`](imaxdiv.md)
