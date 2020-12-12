---
description: _InterlockedExchangePointer 내장 함수에 대해 자세히 알아보세요.
title: _InterlockedExchangePointer 내장 함수
ms.date: 09/02/2019
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
helpviewer_keywords:
- _InterlockedExchangePointer_rel intrinsic
- _InterlockedExchangePointer_HLERelease intrinsic
- _InterlockedExchangePointer intrinsic
- _InterlockedExchangePointer_nf intrinsic
- _InterlockedExchangePointer_acq intrinsic
- _InterlockedExchangePointer_HLEAcquire intrinsic
- InterlockedExchangePointer_acq intrinsic
- InterlockedExchangePointer intrinsic
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
ms.openlocfilehash: 0bb6080b9bca38c67b12b28976b49eb84f74e6c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167996"
---
# <a name="_interlockedexchangepointer-intrinsic-functions"></a>_InterlockedExchangePointer 내장 함수

**Microsoft 전용**

첫 번째 인수에 두 번째 인수로 전달 된 주소를 복사 하 고 첫 번째 인수에 원래 주소를 반환 하는 원자성 교환 작업을 수행 합니다.

## <a name="syntax"></a>구문

```C
void * _InterlockedExchangePointer(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_acq(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_rel(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_nf(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLEAcquire(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLERelease(
   void * volatile * Target,
   void * Value
);
```

### <a name="parameters"></a>매개 변수

*대상을*\
[in, out] 교환할 값에 대 한 포인터의 포인터입니다. 함수는 값을 *값* 으로 설정 하 고 이전 값을 반환 합니다.

*Value*\
진행 *대상이* 가리키는 값과 교환할 값입니다.

## <a name="return-value"></a>반환 값

함수는 *대상이* 가리키는 초기 값을 반환 합니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|헤더|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|X64|\<immintrin.h>|

x86 아키텍처에서 `_InterlockedExchangePointer`는 `_InterlockedExchange`를 호출하는 매크로입니다.

## <a name="remarks"></a>설명

64 비트 시스템에서 매개 변수는 64 비트 이며 64 비트 경계에 정렬 되어야 합니다. 그렇지 않으면 함수가 실패 합니다. 32비트 시스템에서 매개 변수는 32비트이며 32 비트 경계에 정렬해야 합니다. 자세한 내용은 [align](../cpp/align-cpp.md)을 참조 하십시오.

ARM 플랫폼에서는 임계 영역의 시작 및 끝과 같은 위치에서 의미 체계를 획득하고 해제하려면 `_acq` 및 `_rel` 접미사가 포함된 내장 함수를 사용합니다. `_nf`("No fence") 접미사가 포함 된 내장 함수는 메모리 장벽으로 작동 하지 않습니다.

HLE(Hardware Lock Elision) 명령을 지원하는 Intel 플랫폼에서 `_HLEAcquire` 및 `_HLERelease` 접미사가 포함된 내장 함수는 하드웨어에서 잠금 쓰기 단계를 제거하여 성능을 향상시킬 수 있는 힌트를 프로세서에 포함합니다. HLE을 지원 하지 않는 플랫폼에서 이러한 내장 함수를 호출 하면 힌트가 무시 됩니다.

이러한 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[X86 컴파일러와 충돌](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
