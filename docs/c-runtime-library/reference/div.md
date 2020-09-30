---
title: div, ldiv, lldiv
ms.date: 04/05/2018
api_name:
- div
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
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: e0c87ad44986363e871d68bccde757214f5e2c45
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509892"
---
# <a name="div-ldiv-lldiv"></a>div, ldiv, lldiv

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

*숫자로*<br/>
분자입니다.

*denom*<br/>
분모입니다.

## <a name="return-value"></a>반환 값

형식의 인수를 사용 하 여 호출 된 **div** 는 **`int`** 몫과 나머지를 구성 하는 **div_t**형식의 구조체를 반환 합니다. 형식의 인수를 포함 하는 반환 값 **`long`** 이 **ldiv_t**되 고 형식의 인수를 포함 하는 반환 값이 **`long long`** **lldiv_t**됩니다. **div_t**, **ldiv_t**및 **lldiv_t** 는에 정의 되어 \<stdlib.h> 있습니다.

## <a name="remarks"></a>설명

**Div** 함수는 *숫자로* 을 *denom* 로 나눈 다음 몫과 나머지를 계산 합니다. [Div_t](../../c-runtime-library/standard-types.md) 구조체에는 몫, **q**및 나머지가 포함 **됩니다.** 몫의 부호는 수학적 몫의 부호와 동일 합니다. 몫의 절대 값은 수학적 몫의 절대 값보다 작은 가장 큰 정수입니다. 분모가 0이면 프로그램이 종료되고 오류 메시지가 표시됩니다.

또는 형식의 인수를 사용 하는 **div** 의 오버 로드는 **`long`** **`long long`** c + + 코드 에서만 사용할 수 있습니다. 반환 형식 [ldiv_t](../../c-runtime-library/standard-types.md) 및 [lldiv_t](../../c-runtime-library/standard-types.md) 에는 **div_t**멤버와 동일한 의미를 갖는 **q** 및 **rem**멤버가 포함 되어 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**div**, **ldiv**, **lldiv**|\<stdlib.h>|

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

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv]()<br/>
[imaxdiv](imaxdiv.md)<br/>
