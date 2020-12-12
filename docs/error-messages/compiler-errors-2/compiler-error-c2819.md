---
description: '자세한 정보: 컴파일러 오류 C2819'
title: 컴파일러 오류 C2819
ms.date: 11/04/2016
f1_keywords:
- C2819
helpviewer_keywords:
- C2819
ms.assetid: fcc7762d-cb82-4bb1-a715-0d82da832edf
ms.openlocfilehash: fa30432399913c6bdd00bb2728931d213c14064c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194750"
---
# <a name="compiler-error-c2819"></a>컴파일러 오류 C2819

' type ' 형식에 오버 로드 된 멤버 ' operator-> '이 (가) 없습니다.

`operator->()`이 포인터 작업을 사용 하려면를 정의 해야 합니다.

다음 샘플에서는 C2819를 생성 합니다.

```cpp
// C2819.cpp
// compile with: /c
class A {
   public:
      int i;
};

class B {};

void C(B j) {
   j->i;   // C2819
}

class D {
   A* pA;

   public:
      A* operator->() {
         return pA;
      }
};

void F(D j) {
   j->i;
}
```

C2819는 [참조 형식에 c + + 스택 의미 체계를](../../dotnet/cpp-stack-semantics-for-reference-types.md)사용 하는 경우에도 발생할 수 있습니다. 다음 샘플에서는 C2819를 생성 합니다.

```cpp
// C2819_b.cpp
// compile with: /clr
ref struct R {
   void Test() {}
};

int main() {
   R r;
   r->Test();   // C2819
   r.Test();   // OK
}
```
