---
description: __Incfsbyte, __incfsword, __incfsdword에 대해 자세히 알아보세요.
title: __incfsbyte, __incfsword, __incfsdword
ms.date: 09/02/2019
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: 29d86de51ad282789cb19b72ca953f65af2dc19d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336972"
---
# <a name="__incfsbyte-__incfsword-__incfsdword"></a>__incfsbyte, __incfsword, __incfsdword

**Microsoft 전용**

세그먼트의 시작을 기준으로 하는 오프셋으로 지정 된 메모리 위치에 있는 값에 하나를 추가 `FS` 합니다.

## <a name="syntax"></a>구문

```C
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

### <a name="parameters"></a>매개 변수

*이동*\
진행 의 시작 부분부터의 오프셋 `FS` 입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 내장 함수는 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수 에서만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[\__addfsbyte, \_ _addfsword, \_ _addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)\
[\__readfsbyte, \_ _readfsdword, \_ _readfsqword, \_ _readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[\__writefsbyte, \_ _writefsdword, \_ _writefsqword, \_ _writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
