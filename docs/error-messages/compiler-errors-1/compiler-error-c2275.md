---
description: '자세한 정보: 컴파일러 오류 C2275'
title: 컴파일러 오류 C2275
ms.date: 11/04/2016
f1_keywords:
- C2275
helpviewer_keywords:
- C2275
ms.assetid: c1eafa71-48de-46e0-82f3-b575538ef205
ms.openlocfilehash: c6bc03c630a859c2f0913fd482f463071a21758c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134552"
---
# <a name="compiler-error-c2275"></a>컴파일러 오류 C2275

' identifier ':이 형식을 식으로 잘못 사용 했습니다.

식에서 `->` 식별자와 함께 연산자를 사용 **`typedef`** 합니다.

다음 샘플에서는 C2275를 생성 합니다.

```cpp
// C2275.cpp
typedef struct S {
    int mem;
} *S_t;
void func1( int *parm );
void func2() {
    func1( &S_t->mem );   // C2275, S_t is a typedef
}
```
