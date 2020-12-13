---
description: '다음에 대 한 자세한 정보: __getcallerseflags'
title: __getcallerseflags
ms.date: 09/02/2019
f1_keywords:
- _getcallerseflags
- _getcallerseflags_cpp
helpviewer_keywords:
- _getcallerseflags intrinsic
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
ms.openlocfilehash: bc73ca965f61ee4b5291c48f9680d4aa2f1774a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337008"
---
# <a name="__getcallerseflags"></a>__getcallerseflags

**Microsoft 전용**

호출자의 컨텍스트에서 EFLAGS 값을 반환 합니다.

## <a name="syntax"></a>구문

```C
unsigned int __getcallerseflags(void);
```

## <a name="return-value"></a>반환 값

호출자 컨텍스트의 EFLAGS 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__getcallerseflags`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// getcallerseflags.cpp
// processor: x86, x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__getcallerseflags)

unsigned int g()
{
    unsigned int EFLAGS = __getcallerseflags();
    printf_s("EFLAGS 0x%x\n", EFLAGS);
    return EFLAGS;
}
unsigned int f()
{
    return g();
}

int main()
{
    unsigned int i;
    i = f();
    i = g();
    return 0;
}
```

```Output
EFLAGS 0x202
EFLAGS 0x206
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
