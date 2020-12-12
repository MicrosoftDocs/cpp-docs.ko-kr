---
description: '다음에 대 한 자세한 정보: _ReadBarrier'
title: _ReadBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: 94ade7c8f602cf279ac75a5f0a56387c344d0fb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257496"
---
# <a name="_readbarrier"></a>_ReadBarrier

**Microsoft 전용**

호출 시점 전체에서 메모리 액세스 작업을 다시 정렬할 수 있는 컴파일러 최적화를 제한합니다.

> [!CAUTION]
> `_ReadBarrier`, `_WriteBarrier` 및 `_ReadWriteBarrier` 컴파일러 내장 함수 및 `MemoryBarrier` 매크로는 모두 더 이상 사용되지 않으므로 사용하면 안 됩니다. 스레드 간 통신의 경우 [c + + 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)에 정의 된 [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) 및 [std \<T> :: atomic](../standard-library/atomic.md) 와 같은 메커니즘을 사용 합니다. 하드웨어 액세스의 경우 [/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) 컴파일러 옵션을 [volatile](../cpp/volatile-cpp.md) 키워드와 함께 사용 합니다.

## <a name="syntax"></a>Syntax

```C
void _ReadBarrier(void);
```

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_ReadBarrier`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`_ReadBarrier` 내장 함수는 호출 시점 전체에서 메모리 액세스 작업을 제거 또는 다시 정렬할 수 있는 컴파일러 최적화를 제한합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[키워드](../cpp/keywords-cpp.md)
