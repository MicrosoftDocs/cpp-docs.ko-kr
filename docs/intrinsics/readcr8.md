---
title: __readcr8
ms.date: 11/04/2016
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: 041d1b1574ff3d6d3f8bf14575758d1b3ea62e15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602811"
---
# <a name="readcr8"></a>__readcr8

**Microsoft 전용**

CR8 레지스터를 읽고 해당 값을 반환 합니다.

## <a name="syntax"></a>구문

```
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>반환 값

CR8 레지스터 값입니다.

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`__readcr8`|X64|

**헤더 파일** \<intrin.h >

## <a name="remarks"></a>설명

이 내장 함수는 커널 모드에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)