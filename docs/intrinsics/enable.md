---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 1d129db17b489972555efb0b5df2de52e01fa649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631244"
---
# <a name="enable"></a>_enable

**Microsoft 전용**

인터럽트를 사용하도록 설정합니다.

## <a name="syntax"></a>구문

```
void _enable(void);
```

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`_enable`|x86, ARM, x64|

**헤더 파일** \<intrin.h >

## <a name="remarks"></a>설명

`_enable`은 인터럽트 플래그를 설정하도록 프로세서에 명령합니다. x86 시스템에서 이 함수는 인터럽트 플래그 설정(`sti`) 명령을 생성합니다.

이 함수는 커널 모드에서만 사용할 수 있습니다. 사용자 모드에서 이 함수를 사용하면 권한 있는 명령 예외가 throw됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)