---
description: '다음에 대 한 자세한 정보: __writecr8'
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: b9c642d92cd5d5cfb861dbff3d159b5c98a1aa5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331887"
---
# <a name="__writecr8"></a>__writecr8

**Microsoft 전용**

`Data`CR8 레지스터에 값을 씁니다.

## <a name="syntax"></a>구문

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>매개 변수

*데이터*\
진행 CR8 레지스터에 쓸 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writecr8`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`__writecr8`내장 함수는 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
