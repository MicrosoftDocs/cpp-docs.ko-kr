---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4280'
title: 컴파일러 경고 (수준 3) C4280
ms.date: 11/04/2016
f1_keywords:
- C4280
helpviewer_keywords:
- C4280
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
ms.openlocfilehash: e2ef8d4961bf4046d2501d5724ff487bb1526ce2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344135"
---
# <a name="compiler-warning-level-3-c4280"></a>컴파일러 경고 (수준 3) C4280

' operator-> '는 ' type ' 형식을 통해 자체 재귀적입니다.

코드에서 >자신을 호출 하는 **연산자** 를 잘못 허용 합니다.

다음 샘플에서는 C4280를 생성 합니다.

```cpp
// C4280.cpp
// compile with: /W3 /WX
struct A
{
   int z;
   A& operator ->();
};

void f(A y)
{
   int i = y->z; // C4280
}
```
