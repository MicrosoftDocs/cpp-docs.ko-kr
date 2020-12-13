---
description: '다음에 대 한 자세한 정보: _InterlockedAddLargeStatistic'
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 52ca32d0f9b08d638a66923f8f0204eb515b447e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336870"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft 전용**

첫 번째 피연산자가 64 비트 값인 연동 추가를 수행 합니다.

## <a name="syntax"></a>구문

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>매개 변수

*가 수*\
[in, out] 추가 작업의 첫 번째 피연산자에 대 한 포인터입니다. 가리키는 값이 더하기의 결과로 대체 됩니다.

*Value*\
진행 두 번째 피연산자입니다. 첫 번째 피연산자에 더할 값입니다.

## <a name="return-value"></a>반환 값

두 번째 피연산자의 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`_InterlockedAddLargeStatistic`내장 함수는 두 개의 개별 잠긴 명령으로 구현 되기 때문에 원자성이 아닙니다. 내장 함수를 실행 하는 동안 다른 스레드에서 발생 한 원자성 64 비트 읽기가 일치 하지 않는 값을 읽을 수 있습니다.

`_InterlockedAddLargeStatistic` 읽기/쓰기 장벽으로 작동 합니다. 자세한 내용은 [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)를 참조 하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[X86 컴파일러와 충돌](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
