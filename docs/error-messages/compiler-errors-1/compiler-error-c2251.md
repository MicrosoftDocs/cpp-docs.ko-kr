---
description: '자세한 정보: 컴파일러 오류 C2251'
title: 컴파일러 오류 C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: 029d6fc807757da14cf004b4bf1d8ae253f17ec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134812"
---
# <a name="compiler-error-c2251"></a>컴파일러 오류 C2251

네임스페이스 'namespace'에 멤버 'member'가 없습니다. 'member'를 사용하시겠습니까?

컴파일러에서 지정된 네임스페이스의 식별자를 찾을 수 없습니다.

다음 샘플에서는 C2251을 생성합니다.

```cpp
// C2251.cpp
// compile with: /c
namespace A {
   namespace B {
      void f1();
   }

   using namespace B;
}

void A::f1() {}   // C2251
void A::B::f1() {}   // OK
```
