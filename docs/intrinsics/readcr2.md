---
description: '다음에 대 한 자세한 정보: __readcr2'
title: __readcr2
ms.date: 09/02/2019
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: dd862f88716fd2d385622c5100f91fdf47061543
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257357"
---
# <a name="__readcr2"></a>__readcr2

**Microsoft 전용**

CR2 레지스터를 읽고 해당 값을 반환 합니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>반환 값

CR2 레지스터의 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__readcr2`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

내장 함수는 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
