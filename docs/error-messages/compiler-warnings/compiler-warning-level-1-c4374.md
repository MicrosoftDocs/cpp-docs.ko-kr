---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4374'
title: 컴파일러 경고(수준 1) C4374
ms.date: 11/04/2016
f1_keywords:
- C4374
helpviewer_keywords:
- C4374
ms.assetid: 4ac9aaec-d815-4b6e-825f-fa872092dd3b
ms.openlocfilehash: 0b1d8eef5f168f12cc41f1108fcea24040f806ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311341"
---
# <a name="compiler-warning-level-1-c4374"></a>컴파일러 경고(수준 1) C4374

' function1 ': 인터페이스 메서드는 비가상 메서드 ' function2 '에 의해 구현 되지 않습니다.

컴파일러는 메서드 정의에서 [가상](../../cpp/virtual-specifier.md) 키워드를 찾아야 합니다.

다음 샘플에서는 C4374를 생성 합니다.

```cpp
// C4374.cpp
// compile with: /clr /W1 /c /WX
public interface class I {
   void f();
};

public ref struct B {
   void f() {
      System::Console::WriteLine("B::f()");
   }
};

public ref struct C {
   virtual void f() {
      System::Console::WriteLine("C::f()");
   }
};

public ref struct D : B, I {};   // C4374
public ref struct E : C, I {};   // OK
```
