---
description: '다음에 대 한 자세한 정보: __readcr4'
title: __readcr4
ms.date: 09/02/2019
f1_keywords:
- __readcr4
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
ms.openlocfilehash: 3e1d3999f488d4b7c155fd2c475a2070f29f6cda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341037"
---
# <a name="__readcr4"></a>__readcr4

**Microsoft 전용**

CR4 레지스터를 읽고 해당 값을 반환 합니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>반환 값

CR4 레지스터의 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__readcr4`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

내장 함수는 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
