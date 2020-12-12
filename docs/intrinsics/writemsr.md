---
description: '다음에 대 한 자세한 정보: __writemsr'
title: __writemsr
ms.date: 09/02/2019
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: 0ab7392d9df07a9083ca095bc7002a6bf7d45628
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331855"
---
# <a name="__writemsr"></a>__writemsr

**Microsoft 전용**

모델 특정 레지스터에 쓰기 ( `wrmsr` ) 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

### <a name="parameters"></a>매개 변수

*레지스터*\
진행 모델 관련 레지스터입니다.

*Value*\
진행 쓸 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writemsr`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 함수는 커널 모드 에서만 사용할 수 있으며이 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
