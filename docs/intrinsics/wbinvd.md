---
description: '다음에 대 한 자세한 정보: __wbinvd'
title: __wbinvd
ms.date: 09/02/2019
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: b40e1b618e49ab317a7b9cdeea647bcd58df7912
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257266"
---
# <a name="__wbinvd"></a>__wbinvd

**Microsoft 전용**

Write Back 및 무효화할 Cache ( `wbinvd` ) 명령을 생성 합니다.

## <a name="syntax"></a>Syntax

```C
void __wbinvd(void);
```

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__wbinvd`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 함수는 CPL (권한 수준)이 0 인 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
