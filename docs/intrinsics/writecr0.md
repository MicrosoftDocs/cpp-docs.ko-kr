---
description: '다음에 대 한 자세한 정보: __writecr0'
title: __writecr0
ms.date: 09/02/2019
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: 9a4cf4f30b5663b875ca27416b698eb8477938d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313101"
---
# <a name="__writecr0"></a>__writecr0

**Microsoft 전용**

`Data`Cr0 레지스터 레지스터에 값을 씁니다.

## <a name="syntax"></a>구문

```C
void writecr0(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>매개 변수

*데이터*\
진행 CR0 레지스터 레지스터에 쓸 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writecr0`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 내장 함수는 커널 모드에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
