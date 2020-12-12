---
description: '다음에 대 한 자세한 정보: __readcr0'
title: __readcr0
ms.date: 09/02/2019
f1_keywords:
- __readcr0
helpviewer_keywords:
- __readcr0 intrinsic
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
ms.openlocfilehash: b8a7b98042e5e5dbff5236c27b97d8378d72ed6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257409"
---
# <a name="__readcr0"></a>__readcr0

**Microsoft 전용**

CR0 레지스터를 읽고 해당 값을 반환합니다.

## <a name="syntax"></a>구문

```C
unsigned long __readcr0(void);  /* X86 */
unsigned __int64 __readcr0(void);  /* X64 */
```

## <a name="return-value"></a>반환 값

CR0 레지스터의 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__readcr0`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

내장 함수는 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
