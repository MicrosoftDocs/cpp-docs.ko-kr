---
description: '자세한 정보: 컴파일러 오류 C2680'
title: 컴파일러 오류 C2680
ms.date: 11/04/2016
f1_keywords:
- C2680
helpviewer_keywords:
- C2680
ms.assetid: d6f7129e-dd17-4661-b680-18d6b925b1cc
ms.openlocfilehash: 076a7409802a786f795ebac3cac83f8d5fdf968d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155685"
---
# <a name="compiler-error-c2680"></a>컴파일러 오류 C2680

' type ': 이름의 대상 형식이 잘못 되었습니다.

캐스팅 연산자가 포인터나 참조가 아닌 형식으로 변환 하려고 했습니다. [Dynamic_cast](../../cpp/dynamic-cast-operator.md) 연산자는 포인터나 참조에만 사용할 수 있습니다.

다음 샘플에서는 C2680를 생성 합니다.

```cpp
// C2680.cpp
// compile with: /c
class A { virtual void f(); };
class B : public A {};

void g(B b) {
   A a;
   a = dynamic_cast<A>(b);   // C2680  target not a reference type
   a = dynamic_cast<A&>(b);   // OK
}
```

C2680는 대상이 정의 되지 않은 경우에도 발생할 수 있습니다.

```cpp
// C2680b.cpp
// compile with: /clr /c
// C2680 expected
using namespace System::Collections;

// Delete the following line to resolve.
ref class A;   // not defined

// Uncomment the following line to resolve.
// ref class A{};

public ref class B : ArrayList {
   property A^ C[int] {
      A^ get(int index) {
         return dynamic_cast<A^>(this->default::get(index));
      }
      void set(int index, A^ value) {
         this->default::set(index, value);
      }
   }
};
```
