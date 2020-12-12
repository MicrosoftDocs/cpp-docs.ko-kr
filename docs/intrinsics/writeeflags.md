---
description: '다음에 대 한 자세한 정보: __writeeflags'
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 9c439194782f52b474ec6c6365705ebd8756c6b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331865"
---
# <a name="__writeeflags"></a>__writeeflags

**Microsoft 전용**

지정 된 값을 프로그램 상태 및 컨트롤 (EFLAGS) 레지스터에 씁니다.

## <a name="syntax"></a>구문

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>매개 변수

*Value*\
진행 EFLAGS 레지스터에 쓸 값입니다. `Value`매개 변수는 32 비트 플랫폼의 경우 32 비트이 고 64 비트 플랫폼의 경우 64 비트 길이입니다.

## <a name="remarks"></a>설명

이러한 루틴은 내장 함수 에서만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
