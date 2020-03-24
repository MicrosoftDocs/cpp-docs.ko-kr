---
title: 컴파일러 경고(수준 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: e0feb1cb7131b4388c87213a85ff1c921f636e1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162038"
---
# <a name="compiler-warning-level-2-c4250"></a>컴파일러 경고(수준 2) C4250

' class1 ': 우위를 통해 ' class2:: member '를 상속 합니다.

두 개 이상의 멤버가 동일한 이름을 갖습니다. `class2`의 하나는이 멤버를 포함 하는 다른 클래스의 기본 클래스 이므로 상속 됩니다.

C4250를 표시 하지 않으려면 [warning](../../preprocessor/warning.md) pragma를 사용 합니다.

가상 기본 클래스는 여러 파생 클래스 간에 공유 되므로 파생 클래스의 이름은 기본 클래스의 이름을 우위에 있습니다. 예를 들어, 다음과 같은 클래스 계층 구조에 있는 경우에는 다음 두 개의 func 정의가 해당 클래스를 통해 weak:: func () 인스턴스와 weak 클래스를 통한 기준:: func ()를 통해 다이아몬드 내에 상속 됩니다. 다이아몬드형 클래스 개체를 통해 func ()의 정규화 되지 않은 호출은 항상 우위:: func () 인스턴스를 호출 합니다.  Weak 클래스가 func ()의 인스턴스를 도입 하는 경우 두 정의 모두 우위를 가지 며 호출은 모호한 것으로 플래그가 지정 됩니다.

```cpp
// C4250.cpp
// compile with: /c /W2
#include <stdio.h>
struct vbc {
   virtual void func() { printf("vbc::func\n"); }
};

struct weak : public virtual vbc {};

struct dominant : public virtual vbc {
   void func() { printf("dominant::func\n"); }
};

struct diamond : public weak, public dominant {};

int main() {
   diamond d;
   d.func();   // C4250
}
```

## <a name="example"></a>예제

다음 샘플에서는 C4250를 생성 합니다.

```cpp
// C4250_b.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;
class A {
public:
   virtual operator int () {
      return 2;
   }
};

class B : virtual public A {
public:
   virtual operator int () {
      return 3;
   }
};

class C : virtual public A {};

class E : public B, public C {};   // C4250

int main() {
   E eObject;
   cout << eObject.operator int() << endl;
}
```

## <a name="example"></a>예제

이 샘플에서는 더 복잡 한 상황을 보여 줍니다. 다음 샘플에서는 C4250를 생성 합니다.

```cpp
// C4250_c.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;

class V {
public:
   virtual int f() {
      return 1024;
   }
};

class B : virtual public V {
public:
   int b() {
      return f(); // B::b() calls V::f()
   }
};

class M : virtual public V {
public:
   int f() {
      return 7;
   }
};

// because of dominance, f() is M::f() inside D,
// changing the meaning of B::b's f() call inside a D
class D : public B, public M {};   // C4250

int main() {
   D d;
   cout << "value is: " << d.b();   // invokes M::f()
}
```
