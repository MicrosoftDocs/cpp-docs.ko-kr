---
title: _WriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: a41f4c6c5cdd6b72e76a596622912e88fbd03f34
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219320"
---
# <a name="_writebarrier"></a>_WriteBarrier

**Microsoft 전용**

호출 시점 전체에서 메모리 액세스 작업을 다시 정렬할 수 있는 컴파일러 최적화를 제한합니다.

> [!CAUTION]
> `_ReadBarrier`, `_WriteBarrier` 및 `_ReadWriteBarrier` 컴파일러 내장 함수 및 `MemoryBarrier` 매크로는 모두 더 이상 사용되지 않으므로 사용하면 안 됩니다. 스레드 간 통신의 경우 [ C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)에 정의 된 [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) 및 [std:: atomic\<T >](../standard-library/atomic.md)와 같은 메커니즘을 사용 합니다. 하드웨어 액세스의 경우 [/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) 컴파일러 옵션을 [volatile](../cpp/volatile-cpp.md) 키워드와 함께 사용 합니다.

## <a name="syntax"></a>구문

```C
void _WriteBarrier(void);
```

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**헤더 파일** \<intrin.h >

## <a name="remarks"></a>설명

`_WriteBarrier` 내장 함수는 호출 시점 전체에서 메모리 액세스 작업을 제거 또는 다시 정렬할 수 있는 컴파일러 최적화를 제한합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[C++ 키워드](../cpp/keywords-cpp.md)
