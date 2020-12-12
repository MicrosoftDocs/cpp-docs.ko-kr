---
description: '다음에 대 한 자세한 정보: __writecr3'
title: __writecr3
ms.date: 09/02/2019
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: fa4555b2fe4a67dcb3669f8ae20ea0e2d76c8984
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313114"
---
# <a name="__writecr3"></a>__writecr3

**Microsoft 전용**

`Data`CR3 레지스터에 값을 씁니다.

## <a name="syntax"></a>구문

```C
void writecr3(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>매개 변수

*데이터*\
진행 CR3 레지스터에 쓸 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writecr3`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 내장 함수는 커널 모드에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
