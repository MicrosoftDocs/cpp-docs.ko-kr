---
description: '자세한 정보: 컴파일러 오류 C2276'
title: 컴파일러 오류 C2276
ms.date: 11/04/2016
f1_keywords:
- C2276
helpviewer_keywords:
- C2276
ms.assetid: 62005ad9-6cb9-4b1f-965d-b875adaf695e
ms.openlocfilehash: dc6a407110ee121444b7e767f43d7d29ba42db72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134513"
---
# <a name="compiler-error-c2276"></a>컴파일러 오류 C2276

' operator ': 바인딩된 멤버 함수 식에 대 한 연산이 잘못 되었습니다.

컴파일러가 멤버 포인터를 만들기 위한 구문과 관련 된 문제를 발견 했습니다.

다음 샘플에서는 C2276를 생성 합니다.

```cpp
// C2276.cpp
class A {
public:
   int func(){return 0;}
} a;

int (*pf)() = &a.func;   // C2276
// try the following line instead
// int (A::*pf3)() = &A::func;

class B {
public:
   void mf() {
      &this -> mf;   // C2276
      // try the following line instead
      // &B::mf;
   }
};

int main() {
   A a;
   &a.func;   // C2276
   // try the following line instead
   // &A::func;
}
```
