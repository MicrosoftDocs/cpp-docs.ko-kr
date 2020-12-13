---
description: '다음에 대 한 자세한 정보: imaxdiv'
title: imaxdiv
ms.date: 04/05/2018
api_name:
- imaxdiv
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
- imaxdiv
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
ms.openlocfilehash: 3e1f417c1fb45b452b3cd07560bfec68d21fd1a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332776"
---
# <a name="imaxdiv"></a>imaxdiv

크기와 관계없이 한 번의 연산으로 두 정수 값의 몫과 나머지를 계산합니다.

## <a name="syntax"></a>구문

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>매개 변수

*숫자로*<br/>
분자입니다.

*denom*<br/>
분모입니다.

## <a name="return-value"></a>반환 값

[intmax_t](../../c-runtime-library/standard-types.md) 형식의 인수를 사용 하 여 호출 된 **imaxdiv** 는 몫과 나머지를 구성 하는 [imaxdiv_t](../../c-runtime-library/standard-types.md) 형식의 구조체를 반환 합니다.

## <a name="remarks"></a>설명

**Imaxdiv** 함수는 *숫자로* 을 *denom* 로 나눈 다음 몫과 나머지를 계산 합니다. **Imaxdiv_t** 구조체에는 몫, **intmax_t** **q** 및 나머지 **intmax_t** **rem** 이 포함 됩니다. 몫의 부호는 수학적 몫의 부호와 동일 합니다. 몫의 절대 값은 수학적 몫의 절대 값보다 작은 가장 큰 정수입니다. 분모가 0이면 프로그램이 종료되고 오류 메시지가 표시됩니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

`9460730470000000 8766`의 명령줄 매개 변수를 사용하여 빌드된 다음 호출되면 코드는 다음 출력을 생성합니다.

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](./div.md)<br/>
