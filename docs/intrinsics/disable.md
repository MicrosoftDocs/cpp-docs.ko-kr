---
title: _disable
ms.date: 11/04/2016
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 64e7031ab578632322dfd5c73eb81e0750c1e0b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587813"
---
# <a name="disable"></a>_disable

**Microsoft 전용**

인터럽트를 사용하지 않도록 설정합니다.

## <a name="syntax"></a>구문

```
void _disable(void);
```

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`_disable`|x86, ARM, x64|

**헤더 파일** \<intrin.h >

## <a name="remarks"></a>설명

`_disable`는 인터럽트 플래그를 지우도록 프로세서에 명령합니다. x86 시스템에서 이 함수는 인터럽트 플래그 지우기(`cli`) 명령을 생성합니다.

이 함수는 커널 모드에서만 사용할 수 있습니다. 사용자 모드에서 이 함수를 사용하면 런타임에 권한 있는 명령 예외가 throw됩니다.

ARM 플랫폼에서 이 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)