---
description: '자세한 정보: 컴파일러 오류 C2682'
title: 컴파일러 오류 C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 962debb0227347abe97e290db724fdb227212914
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177434"
---
# <a name="compiler-error-c2682"></a>컴파일러 오류 C2682

casting_operator를 사용 하 여 ' type1 '에서 ' type2 ' (으)로 변환할 수 없습니다.

캐스팅 연산자가 호환 되지 않는 형식 간에 변환 하려고 했습니다. 예를 들어 [dynamic_cast](../../cpp/dynamic-cast-operator.md) 연산자를 사용 하 여 포인터를 참조로 변환할 수 없습니다. **`dynamic_cast`** 연산자를 사용 하 여 한정자를 캐스트할 수 없습니다. 형식에 대 한 모든 한정자가 일치 해야 합니다.

연산자를 사용 **`const_cast`** 하 여, 또는와 같은 특성을 제거할 수 있습니다 **`const`** **`volatile`** **`__unaligned`** .

다음 샘플에서는 C2682를 생성 합니다.

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

다음 샘플에서는 C2682를 생성 합니다.

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
