---
description: '자세한 정보: __readfsbyte, __readfsdword, __readfsqword, __readfsword'
title: __readfsbyte, __readfsdword, __readfsqword, __readfsword
ms.date: 09/02/2019
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: 2b733ced12045253c78e823379c10a5e70f65143
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340985"
---
# <a name="__readfsbyte-__readfsdword-__readfsqword-__readfsword"></a>__readfsbyte, __readfsdword, __readfsqword, __readfsword

**Microsoft 전용**

FS 세그먼트의 시작을 기준으로 하는 오프셋으로 지정 된 위치에서 메모리를 읽습니다.

## <a name="syntax"></a>구문

```C
unsigned char __readfsbyte(
   unsigned long Offset
);
unsigned short __readfsword(
   unsigned long Offset
);
unsigned long __readfsdword(
   unsigned long Offset
);
unsigned __int64 __readfsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>매개 변수

*이동*\
진행 에서 읽을의 시작 부분부터의 오프셋 `FS` 입니다.

## <a name="return-value"></a>반환 값

위치에서 호출 되는 함수 이름으로 표시 되는 바이트, 단어, 더블 워드 또는 쿼드 워드의 메모리 내용입니다 `FS:[Offset]` .

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 루틴은 내장 함수 에서만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__writefsbyte, \_ _writefsdword, \_ _writefsqword, \_ _writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
