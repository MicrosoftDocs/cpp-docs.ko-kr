---
description: _InterlockedCompareExchange128 내장 함수에 대해 자세히 알아보세요.
title: _InterlockedCompareExchange128 내장 함수
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: ee04a71dafe37d6075a054946cd947f6f3829092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168139"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>_InterlockedCompareExchange128 내장 함수

**Microsoft 전용**

128 비트 연동 비교 및 교환을 수행 합니다.

## <a name="syntax"></a>구문

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
[in, out] 128 비트 필드로 간주 되는 2 64 비트 정수의 배열인 대상에 대 한 포인터입니다. 일반 보호 오류를 방지 하려면 대상 데이터가 16 바이트 맞춤 이어야 합니다.

*ExchangeHigh*\
진행 대상의 상위 부분과 교환할 수 있는 64 비트 정수입니다.

*ExchangeLow*\
진행 대상의 하위 부분과 교환할 수 있는 64 비트 정수입니다.

*ComparandResult*\
[in, out] 대상과 비교할 2 64 비트 정수 (128 비트 필드로 간주 됨)의 배열에 대 한 포인터입니다.  출력에서이 배열을 대상의 원래 값으로 덮어씁니다.

## <a name="return-value"></a>반환 값

128 비트 비교 피연산자이 대상의 원래 값과 같으면 1입니다. `ExchangeHigh``ExchangeLow`128 비트 대상을 덮어씁니다.

비교 피연산자가 대상의 원래 값과 같지 않은 경우 0입니다. 대상의 값은 변경 되지 않으며 비교 피연산자의 값은 대상의 값으로 덮어쓰여집니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`_InterlockedCompareExchange128`내장 함수는 `cmpxchg16b` 접두사를 사용 하 여 `lock` 128 비트의 잠금 비교 및 교환을 수행 하는 명령을 생성 합니다. 이전 버전의 AMD 64 비트 하드웨어는이 명령을 지원 하지 않습니다. 명령에 대 한 하드웨어 지원을 확인 하려면를 사용 하 여 `cmpxchg16b` `__cpuid` 내장 함수를 호출 `InfoType=0x00000001 (standard function 1)` 합니다. 명령이 지원 되는 경우의 비트 13 `CPUInfo[2]` (ECX)은 1입니다.

> [!NOTE]
> 의 값은 `ComparandResult` 항상 덮어쓰여집니다. 명령 후 `lock` 이 내장 함수는의 초기 값을에 즉시 `Destination` 복사 `ComparandResult` 합니다. 따라서 `ComparandResult` 및는 `Destination` 예기치 않은 동작을 방지 하기 위해 별도의 메모리 위치를 가리켜야 합니다.

`_InterlockedCompareExchange128`낮은 수준의 스레드 동기화에를 사용할 수 있지만, 더 작은 동기화 기능 (예: 다른 내장 함수)을 사용할 수 있는 경우 128 비트를 동기화 할 필요가 없습니다 `_InterlockedCompareExchange` . `_InterlockedCompareExchange128`메모리에서 128 비트 값에 대 한 원자성 액세스를 원하는 경우를 사용 합니다.

명령을 지원 하지 않는 하드웨어에서 내장 함수를 사용 하는 코드를 실행 하는 경우 `cmpxchg16b` 결과를 예측할 수 없습니다.

ARM 플랫폼에서는 임계 영역의 시작 및 끝과 같은 위치에서 의미 체계를 획득하고 해제하려면 `_acq` 및 `_rel` 접미사가 포함된 내장 함수를 사용합니다. `_nf`("No fence") 접미사가 포함 된 ARM 내장 함수는 메모리 장벽으로 작동 하지 않습니다.

`_np`("no prefetch"의 약어) 접미사가 포함된 내장 함수는 컴파일러가 가능한 프리페치 연산을 삽입하지 못하도록 차단합니다.

이 루틴은 내장 함수로만 사용할 수 있습니다.

## <a name="example"></a>예제

이 예제에서는 `_InterlockedCompareExchange128` 를 사용 하 여 2 64 비트 정수의 배열에 대 한 상위 단어를 높은 단어와 낮은 단어의 합계로 바꾸고 하위 단어를 늘립니다. 배열에 대 한 액세스는 `BigInt.Int` 원자성 이지만,이 예제에서는 단일 스레드를 사용 하 고 편의상 잠금을 무시 합니다.

```cpp
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[_InterlockedCompareExchange 내장 함수](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[X86 컴파일러와 충돌](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
