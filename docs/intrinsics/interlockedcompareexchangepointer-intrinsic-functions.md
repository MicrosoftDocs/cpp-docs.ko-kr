---
description: _InterlockedCompareExchangePointer 내장 함수에 대해 자세히 알아보세요.
title: _InterlockedCompareExchangePointer 내장 함수
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
ms.openlocfilehash: cd8d42c6a7036a6c779af6fc32a7176b7e48a73c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168061"
---
# <a name="_interlockedcompareexchangepointer-intrinsic-functions"></a>_InterlockedCompareExchangePointer 내장 함수

**Microsoft 전용**

`Exchange` 및 `Destination` 주소가 같으면 `Comparand` 주소에 `Destination` 주소를 저장하는 원자성 작업을 수행합니다.

## <a name="syntax"></a>구문

```C
void * _InterlockedCompareExchangePointer (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_acq (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLEAcquire (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLERelease (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_nf (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_np (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
long _InterlockedCompareExchangePointer_rel (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
[in, out] 대상 값에 대 한 포인터에 대 한 포인터입니다. 부호는 무시됩니다.

*Exchange*\
진행 교환 포인터입니다. 부호는 무시됩니다.

*비교 피연산자*\
진행 대상과 비교할 포인터입니다. 부호는 무시됩니다.

## <a name="return-value"></a>반환 값

반환 값은 대상의 초기 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|헤더|
|---------------|------------------|------------|
|`_InterlockedCompareExchangePointer`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM, ARM64|\<iiintrin.h>|
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, x64|\<immintrin.h>|

## <a name="remarks"></a>설명

`_InterlockedCompareExchangePointer`는 `Destination` 주소와 `Comparand` 주소의 원자성 비교를 수행합니다. `Destination` 주소가 `Comparand` 주소와 같으면 `Exchange`으로 지정된 주소에 `Destination` 주소가 저장됩니다. 그렇지 않으면 작업이 수행 되지 않습니다.

`_InterlockedCompareExchangePointer` Win32 Windows SDK [InterlockedCompareExchangePointer](/windows-hardware/drivers/ddi/content/wdm/nf-wdm-interlockedcompareexchangepointer) 함수에 대 한 컴파일러 내장 함수 지원을 제공 합니다.

를 사용 하는 방법에 대 한 예제는 `_InterlockedCompareExchangePointer` [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)을 참조 하세요.

ARM 플랫폼에서는 임계 영역의 시작 및 끝과 같은 위치에서 의미 체계를 획득하고 해제하려면 `_acq` 및 `_rel` 접미사가 포함된 내장 함수를 사용합니다. `_nf`("No fence") 접미사가 포함 된 ARM 내장 함수는 메모리 장벽으로 작동 하지 않습니다.

`_np`("no prefetch"의 약어) 접미사가 포함된 내장 함수는 컴파일러가 가능한 프리페치 연산을 삽입하지 못하도록 차단합니다.

HLE(Hardware Lock Elision) 명령을 지원하는 Intel 플랫폼에서 `_HLEAcquire` 및 `_HLERelease` 접미사가 포함된 내장 함수는 하드웨어에서 잠금 쓰기 단계를 제거하여 성능을 향상시킬 수 있는 힌트를 프로세서에 포함합니다. HLE을 지원 하지 않는 플랫폼에서 이러한 내장 함수를 호출 하면 힌트가 무시 됩니다.

이러한 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[키워드](../cpp/keywords-cpp.md)
