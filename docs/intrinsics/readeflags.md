---
description: '다음에 대 한 자세한 정보: __readeflags'
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: e74864f522ba411f44b4a264e9c0e1fd16aa84ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340998"
---
# <a name="__readeflags"></a>__readeflags

**Microsoft 전용**

프로그램 상태 및 컨트롤 (EFLAGS) 레지스터를 읽습니다.

## <a name="syntax"></a>구문

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>반환 값

EFLAGS 레지스터의 값입니다. 반환 값은 32 비트 플랫폼의 32 비트 길이 이며 64 비트 플랫폼에서는 64 비트가 깁니다.

## <a name="remarks"></a>설명

이러한 루틴은 내장 함수 에서만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__readeflags`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
