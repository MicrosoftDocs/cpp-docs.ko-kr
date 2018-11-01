---
title: 컴파일러 오류 C2671
ms.date: 11/04/2016
f1_keywords:
- C2671
helpviewer_keywords:
- C2671
ms.assetid: fc0ee40f-c8f3-408f-b89d-745d149c4169
ms.openlocfilehash: 92ed646b0e4c5d2bbc6556c2a7b1ef66d8192ec1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496033"
---
# <a name="compiler-error-c2671"></a>컴파일러 오류 C2671

'function': 정적 멤버 함수에 'this' 포인터가 없습니다.

A `static` 멤버 함수에 액세스 하려고 `this`합니다.

다음 샘플에서는 C2671 오류가 생성 됩니다.

```
// C2671.cpp
struct S {
   static S* const func() { return this; }  // C2671
};
```