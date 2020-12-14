---
description: '다음에 대 한 자세한 정보: rand_s'
title: rand_s
ms.date: 4/2/2020
api_name:
- rand_s
- _o_rand_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 8894248bf924ef513dc916e10e47ce8ea7e95137
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274829"
---
# <a name="rand_s"></a>rand_s

의사 난수를 생성합니다. 이는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명 된 대로 향상 된 보안 기능을 제공 하는 함수 [rand](rand.md)의 더 안전한 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>매개 변수

*randomValue*<br/>
생성 된 값을 보유할 정수에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

정상적으로 실행되는 경우 0이고 그렇지 않으면 오류 코드입니다. 입력 포인터 _randomValue_ 가 null 포인터인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **EINVAL** 를 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다. 다른 이유로 인해 함수가 실패 하면 *_randomValue_ 는 0으로 설정 됩니다.

## <a name="remarks"></a>설명

**Rand_s** 함수는 입력 포인터에 **UINT_MAX** 범위 0의 의사 난수 정수를 씁니다. **Rand_s** 함수는 운영 체제를 사용 하 여 암호 보안 난수를 생성 합니다. [Srand](srand.md) 함수에 의해 생성 된 초기값은 사용 하지 않으며 [rand](rand.md)에서 사용 하는 난수 시퀀스에도 영향을 주지 않습니다.

**Rand_s** 함수를 사용 하려면 다음 예제와 같이 함수를 선언 하기 위한 포함 문 앞에 상수 **_CRT_RAND_S** 정의 해야 합니다.

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** 는 Windows XP 이상 에서만 사용할 수 있는 [Rtlgenrandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) API에 따라 달라 집니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>샘플 출력

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
