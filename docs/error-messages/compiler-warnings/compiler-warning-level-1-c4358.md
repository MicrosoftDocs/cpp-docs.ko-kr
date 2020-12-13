---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4358'
title: 컴파일러 경고(수준 1) C4358
ms.date: 11/04/2016
f1_keywords:
- C4358
helpviewer_keywords:
- C4358
ms.assetid: a9848f84-14b3-405e-81bf-ee3e91a51511
ms.openlocfilehash: 2e3f548f5b464f712f6e5d0e20dc6da9edfdfd3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339984"
---
# <a name="compiler-warning-level-1-c4358"></a>컴파일러 경고(수준 1) C4358

' operator ': 결합 된 대리자의 반환 형식이 ' void '가 아닙니다. 반환 된 값이 정의 되지 않았습니다.

두 개의 대리자가 결합 되었으며 반환 값은 void가 아닙니다. Void가 아닌 반환 값을 포함 하는 두 개의 대리자가 결합 된 경우 대리자의 반환 값이 사용 되는 경우 컴파일러에서 적절 한 할당을 수행할 수 없습니다.

다음 샘플에서는 C4358를 생성 합니다.

```cpp
// C4358.cpp
// compile with: /clr /W1
delegate int D();
delegate void E();

ref class X {
   int i;
public:
   X(int ii) : i(ii) {}
   int f() {
      return i;
   }
};

ref class Y {
   int i;
public:
   Y() {}
   void g() {}
};

int main() {
   D^ d = gcnew D(gcnew X(1), &X::f);
   D^ d2 = gcnew D(gcnew X(2), &X::f);

   d += d2;   // C4358
   int j = d();   // return value indeterminate

   E^ e = gcnew E(gcnew Y, &Y::g);
   E^ e2 = gcnew E(gcnew Y, &Y::g);
   e += e2;   // OK
}
```
