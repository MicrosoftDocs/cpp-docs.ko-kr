---
title: __readdr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readdr
dev_langs:
- C++
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dffb51782e87903feaeb733765fcf9f4763a64f6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385146"
---
# <a name="readdr"></a>__readdr

지정 된 디버그 레지스터의 값을 읽습니다.

## <a name="syntax"></a>구문

```
unsigned         __readdr(unsigned int DebugRegister);
unsigned __int64 __readdr(unsigned int DebugRegister);
```

#### <a name="parameters"></a>매개 변수

*DebugRegister*<br/>
[in] 디버그를 식별 하는 0 ~ 7에서에서 상수를 등록 합니다.

## <a name="return-value"></a>반환 값

지정 된 디버그 레지스터의 값입니다.

## <a name="remarks"></a>설명

이러한 내장 함수는 커널 모드 에서만 사용할 수 있습니다 및 루틴은 내장 함수로 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`__readdr`|x86, x64|

**헤더 파일** \<intrin.h >

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)