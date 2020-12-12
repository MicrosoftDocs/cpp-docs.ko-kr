---
description: '다음에 대 한 자세한 정보: __shiftright128'
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: 71f8a0d9b740ebfef5e930715e07d1ec31950269
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306978"
---
# <a name="__shiftright128"></a>__shiftright128

**Microsoft 전용**

두 개의 64비트 수량 `LowPart` 및 `HighPart`로 표현되는 128비트 수량을 `Shift`로 지정된 비트 수만큼 오른쪽으로 이동하고 결과 중 하위 64비트를 반환합니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>매개 변수

*LowPart*\
진행 이동할 128 비트 수량의 하위 64 비트입니다.

*Largeint.highpart*\
진행 이동할 128 비트 수량의 상위 64 비트입니다.

*교대조*\
진행 이동할 비트 수입니다.

## <a name="return-value"></a>반환 값

결과의 하위 64비트입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__shiftright128`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`Shift` 값은 항상 64로 나눈 나머지이므로 예를 들어 `__shiftright128(0, 1, 64)`를 호출하면 함수는 상위 부분의 `0`비트를 오른쪽으로 이동하고 일반적인 경우에 반환되는 `0`이 아닌 하위 부분 `1`을 반환합니다.

## <a name="example"></a>예제

예제를 보려면 [__shiftleft128](../intrinsics/shiftleft128.md)를 참조 하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__shiftleft128](../intrinsics/shiftleft128.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
