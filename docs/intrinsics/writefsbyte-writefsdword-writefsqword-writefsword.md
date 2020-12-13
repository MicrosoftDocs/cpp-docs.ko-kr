---
description: '자세한 정보: __writefsbyte, __writefsdword, __writefsqword, __writefsword'
title: __writefsbyte, __writefsdword, __writefsqword, __writefsword
ms.date: 09/02/2019
f1_keywords:
- __writefsword
- __writefsbyte
- __writefsqword
- __writefsdword
helpviewer_keywords:
- writefsbyte intrinsic
- __writefsword intrinsic
- writefsqword intrinsic
- writefsdword intrinsic
- __writefsdword intrinsic
- __writefsqword intrinsic
- __writefsbyte intrinsic
- writefsword intrinsic
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
ms.openlocfilehash: cde85cd7fea5b65ced127da96033ecc5b1f4f058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136060"
---
# <a name="__writefsbyte-__writefsdword-__writefsqword-__writefsword"></a>__writefsbyte, __writefsdword, __writefsqword, __writefsword

**Microsoft 전용**

FS 세그먼트의 시작을 기준으로 하는 오프셋으로 지정 된 위치에 메모리를 씁니다.

## <a name="syntax"></a>구문

```C
void __writefsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writefsword(
   unsigned long Offset,
   unsigned short Data
);
void __writefsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writefsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>매개 변수

*이동*\
진행 쓸 FS의 시작 부분에서의 오프셋입니다.

*데이터*\
진행 쓸 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 루틴은 내장 함수 에서만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__readfsbyte, \_ _readfsdword, \_ _readfsqword, \_ _readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
