---
description: '자세히 알아보기: 로컬로 선언 된 이름에 대 한 이름 확인'
title: 로컬로 선언된 이름에 대한 이름 확인
ms.date: 11/04/2016
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
ms.openlocfilehash: 14530aae65940830db15f7e6fc0ec2c33935afe3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313777"
---
# <a name="name-resolution-for-locally-declared-names"></a>로컬로 선언된 이름에 대한 이름 확인

템플릿 인수를 사용하거나 사용하지 않고 템플릿 이름 자체를 참조할 수 있습니다. 클래스 템플릿의 범위에서 이름 자체는 템플릿을 나타냅니다. 템플릿 특수화 또는 부분 특수화의 범위에서 이름만 특수화 또는 부분 특수화를 참조합니다. 템플릿의 다른 특수화나 부분 특수화도 해당 템플릿 인수와 함께 참조될 수 있습니다.

## <a name="example-specialization-versus-partial-specialization"></a>예: 특수화 및 부분 특수화

다음 코드는 클래스 템플릿의 이름 A가 특수화 또는 부분 특수화의 범위에서 다르게 해석된다는 것을 보여 줍니다.

```cpp
// template_name_resolution3.cpp
// compile with: /c
template <class T> class A {
   A* a1;   // A refers to A<T>
   A<int>* a2;  // A<int> refers to a specialization of A.
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.
};

template <class T> class A<T*> {
   A* a4; // A refers to A<T*>.
};

template<> class A<int> {
   A* a5; // A refers to A<int>.
};
```

## <a name="example-name-conflict-between-template-parameter-and-object"></a>예: 템플릿 매개 변수와 개체 간 이름 충돌

템플릿 매개 변수와 다른 개체 사이에 이름이 충돌할 경우 템플릿 매개 변수를 숨길 수도 있고 숨기지 않을 수도 있습니다. 다음 규칙은 우선 순위를 결정하는 데 도움이 됩니다.

템플릿 매개 변수의 범위는 매개 변수가 처음 나타난 지점부터 클래스 또는 함수 템플릿의 끝까지입니다. 이름이 템플릿 인수 목록 또는 기본 클래스 목록에 다시 나타나는 경우 동일한 형식을 참조합니다. 표준 C++에서는 이 이외에 템플릿 매개 변수와 동일한 이름을 같은 범위에서 선언할 수 없습니다. Microsoft 확장은 템플릿 매개 변수가 템플릿 범위에서 다시 정의될 수 있도록 합니다. 다음 예제는 클래스 템플릿의 기본 지정에서의 템플릿 매개 변수 사용을 보여 줍니다.

```cpp
// template_name_resolution4.cpp
// compile with: /EHsc
template <class T>
class Base1 {};

template <class T>
class Derived1 : Base1<T> {};

int main() {
   // Derived1<int> d;
}
```

## <a name="example-define-member-function-outside-class-template"></a>예제: 클래스 템플릿 외부에서 멤버 함수 정의

템플릿의 멤버 함수를 클래스 템플릿 외부에서 정의할 때 다른 템플릿 매개 변수 이름을 사용할 수 있습니다. 템플릿 멤버 함수 정의가 선언이 템플릿 매개 변수에 대해 사용하는 이름과 다른 이름을 사용하고 정의에 사용된 이름이 선언의 다른 멤버와 충돌하는 경우 템플릿 선언의 멤버가 우선합니다.

```cpp
// template_name_resolution5.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T> class C {
public:
   struct Z {
      Z() { cout << "Z::Z()" << endl; }
   };
   void f();
};

template <class Z>
void C<Z>::f() {
   // Z refers to the struct Z, not to the template arg;
   // Therefore, the constructor for struct Z will be called.
   Z z;
}

int main() {
   C<int> c;
   c.f();
}
```

```Output
Z::Z()
```

## <a name="example-define-template-or-member-function-outside-namespace"></a>예: 네임 스페이스 외부에서 템플릿 또는 멤버 함수 정의

템플릿 함수 또는 멤버 함수를 템플릿을 선언한 네임스페이스 외부에서 정의할 때 템플릿 인수는 네임스페이스의 다른 멤버 이름보다 우선합니다.

```cpp
// template_name_resolution6.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

namespace NS {
   void g() { cout << "NS::g" << endl; }

   template <class T> struct C {
      void f();
      void g() { cout << "C<T>::g" << endl; }
   };
};

template <class T>
void NS::C<T>::f() {
   g(); // C<T>::g, not NS::g
};

int main() {
   NS::C<int> c;
   c.f();
}
```

```Output
C<T>::g
```

## <a name="example-base-class-or-member-name-hides-template-argument"></a>예: 기본 클래스 또는 멤버 이름이 템플릿 인수를 숨깁니다.

템플릿 클래스 선언 외부 정의에서 템플릿 클래스에 템플릿 인수에 종속되지 않는 기본 클래스가 있고 기본 클래스 또는 해당 멤버 중 하나가 템플릿 인수와 같은 이름을 가진 경우 기본 클래스 또는 멤버 이름은 템플릿 인수를 숨깁니다.

```cpp
// template_name_resolution7.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct B {
   int i;
   void print() { cout << "Base" << endl; }
};

template <class T, int i> struct C : public B {
   void f();
};

template <class B, int i>
void C<B, i>::f() {
   B b;   // Base class b, not template argument.
   b.print();
   i = 1; // Set base class's i to 1.
}

int main() {
   C<int, 1> c;
   c.f();
   cout << c.i << endl;
}
```

```Output
Base
1
```

## <a name="see-also"></a>참고 항목

[이름 확인](../cpp/templates-and-name-resolution.md)
