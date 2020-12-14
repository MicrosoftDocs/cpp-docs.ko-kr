---
description: '자세한 정보: 컴파일러 오류 C2293'
title: 컴파일러 오류 C2293
ms.date: 11/04/2016
f1_keywords:
- C2293
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
ms.openlocfilehash: 667ca42295092711f5812d2d7d0b10afb82e9959
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235257"
---
# <a name="compiler-error-c2293"></a>컴파일러 오류 C2293

'identifier': 멤버 변수를 __based 지정자로 사용할 수 없습니다.

한정자에 대 한 지정자는 **`__based`** 비멤버 포인터 여야 합니다.

다음 샘플에서는 C2293을 생성합니다.

```cpp
// C2293.cpp
// compile with: /c
class A {
   static int *i;
   void __based(i) *bp;   // C2293
   void *bp2;   // OK
};
```
