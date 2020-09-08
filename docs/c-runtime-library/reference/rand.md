---
title: rand
description: 잘 알려져 있고 완전히 재현할 수 있는 알고리즘을 사용 하 여 의사 난수를 생성 하는 rand에 대 한 API 참조입니다.
ms.date: 4/2/2020
api_name:
- rand
- _o_rand
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 50c4f921c81ecad00abb19e6ce50158d450b170e
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555334"
---
# <a name="rand"></a>rand

잘 알려져 있고 완전히 재현 가능한 알고리즘을 사용 하 여 의사 난수를 생성 합니다. 이 함수의 프로그래밍 방식으로 안전한 버전을 사용할 수 있습니다. [rand_s](rand-s.md)를 참조 하세요. **Rand** 로 생성 된 숫자는 암호화 보안이 유지 되지 않습니다. 보다 안전한 보안 난수 생성을 위해 [rand_s](rand-s.md) 또는의 c + + 표준 라이브러리에 선언 된 함수를 사용 [\<random>](../../standard-library/random.md) 합니다.

## <a name="syntax"></a>구문

```C
int rand( void );
```

## <a name="return-value"></a>Return Value

**rand** 는 위에서 설명한 대로 의사 난수를 반환 합니다. 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

**Rand** 함수는 0에서 **RAND_MAX** (32767) 범위의 의사 난수 정수를 반환 합니다. **Rand**를 호출 하기 전에 [srand](srand.md) 함수를 사용 하 여 의사 (pseudo) 번호 생성기를 초기값으로 사용 합니다.

**Rand** 함수는 잘 알려진 시퀀스를 생성 하며 암호화 함수로 사용 하기에 적합 하지 않습니다. 보다 안전한 보안 난수 생성을 위해 [rand_s](rand-s.md) 또는의 c + + 표준 라이브러리에 선언 된 함수를 사용 [\<random>](../../standard-library/random.md) 합니다. **Rand** 의 문제 및 이러한 단점을 해결 하는 방법에 대 한 자세한 내용은 \<random> 이 비디오에서 잘못 된 [것으로 간주](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful)되는이 비디오를 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
