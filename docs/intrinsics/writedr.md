---
description: '다음에 대 한 자세한 정보: __writedr'
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 3a52b8985a28268c430cbb1bfb7b2494e9004820
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331879"
---
# <a name="__writedr"></a>__writedr

**Microsoft 전용**

지정 된 값을 지정 된 디버그 레지스터에 씁니다.

## <a name="syntax"></a>구문

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>매개 변수

*DebugRegister*\
진행 디버그 레지스터를 식별 하는 0부터 7 까지의 숫자입니다.

*DebugValue*\
진행 디버그 레지스터에 쓸 값입니다.

## <a name="remarks"></a>설명

이러한 내장 함수는 커널 모드 에서만 사용할 수 있으며 루틴은 내장 함수 에서만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writedr`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
