---
description: '다음에 대 한 자세한 정보: __writecr4'
title: __writecr4
ms.date: 09/02/2019
f1_keywords:
- _writecr4
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
ms.openlocfilehash: 711a6dff42f3805886865d09b4638479173bc64e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313088"
---
# <a name="__writecr4"></a>__writecr4

**Microsoft 전용**

`Data`CR4 레지스터에 값을 씁니다.

## <a name="syntax"></a>구문

```C
void writecr4(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>매개 변수

*데이터*\
진행 CR4 레지스터에 쓸 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writecr4`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 내장 함수는 커널 모드에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
