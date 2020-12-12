---
description: '다음에 대 한 자세한 정보: pop_macro pragma'
title: pop_macro pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
helpviewer_keywords:
- pop_macro pragma
- pragmas, pop_macro
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
ms.openlocfilehash: 395e107586b9534b2e9db616f30ddd88b15b93ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325708"
---
# <a name="pop_macro-pragma"></a>pop_macro pragma

*매크로 이름* 매크로의 값을이 매크로의 스택 맨 위에 있는 값으로 설정 합니다.

## <a name="syntax"></a>Syntax

> **#pragma pop_macro (** "*매크로-이름*" **)**

## <a name="remarks"></a>설명

**Pop_macro** 를 수행 하려면 먼저 *매크로 이름* 에 대 한 [push_macro](../preprocessor/push-macro.md) 를 실행 해야 합니다.

## <a name="example"></a>예제

```cpp
// pragma_directives_pop_macro.cpp
// compile with: /W1
#include <stdio.h>
#define X 1
#define Y 2

int main() {
   printf("%d",X);
   printf("\n%d",Y);
   #define Y 3   // C4005
   #pragma push_macro("Y")
   #pragma push_macro("X")
   printf("\n%d",X);
   #define X 2   // C4005
   printf("\n%d",X);
   #pragma pop_macro("X")
   printf("\n%d",X);
   #pragma pop_macro("Y")
   printf("\n%d",Y);
}
```

```Output
1
2
1
2
1
3
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
