---
description: '다음에 대 한 자세한 정보: __nop'
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 55759e8324511b6ddaa2774bdfdc3554c0032c2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118929"
---
# <a name="__nop"></a>__nop

**Microsoft 전용**

작업을 수행 하지 않는 플랫폼별 기계어 코드를 생성 합니다.

## <a name="syntax"></a>Syntax

```C
void __nop();
```

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="remarks"></a>설명

`__nop` 함수는 `NOP` 컴퓨터 명령에 해당합니다. X86 및 x 64에 대 한 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "Intel 아키텍처 소프트웨어 개발자 설명서, 볼륨 2: 명령 집합 참조" 문서를 검색 하십시오.

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
