---
title: 컴파일러 오류 C2805
ms.date: 11/04/2016
f1_keywords:
- C2805
helpviewer_keywords:
- C2805
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
ms.openlocfilehash: b0b3c0d4291787fb0b5664baa9159c84c8549dfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471736"
---
# <a name="compiler-error-c2805"></a>컴파일러 오류 C2805

이항 'operator o'에 매개 변수가 너무 적습니다.

이항 연산자 매개 변수가 없습니다.

다음 샘플에서는 C2805 오류가 생성 됩니다.

```
// C2805.cpp
// compile with: /c
class X {
public:
   X operator< ( void );   // C2805 must take one parameter
   X operator< ( X );   // OK
};
```