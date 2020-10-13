---
title: 선언 사용
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: 072ecd325a76e80dbd710c241e39fdf7b969e537
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008254"
---
# <a name="using-declaration"></a>선언 사용

선언에는 **`using`** using 선언이 표시 되는 선언적 영역에 대 한 이름이 도입 됩니다.

## <a name="syntax"></a>구문

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>매개 변수

*중첩 된 이름 지정자* 범위 확인 연산자에 의해 종료 되는 네임 스페이스, 클래스 또는 열거형 이름 및 범위 확인 연산자 (::)의 시퀀스입니다. 단일 범위 확인 연산자를 사용 하 여 전역 네임 스페이스의 이름을 도입할 수 있습니다. 키워드는 **`typename`** 선택 사항이 며 기본 클래스에서 클래스 템플릿에 도입 될 때 종속 이름을 확인 하는 데 사용할 수 있습니다.

*정규화* 되지 않은 id 식별자, 오버 로드 된 연산자 이름, 사용자 정의 리터럴 연산자 또는 변환 함수 이름, 클래스 소멸자 이름 또는 템플릿 이름과 인수 목록 일 수 있는 정규화 되지 않은 id 식입니다.

*선언 자 목록* 쉼표로 구분 된 [ **`typename`** ] *중첩 이름 지정자* 의 정규화 되지 않은 *id* 선언 자입니다 .이 목록에는 선택적으로 줄임표가 있습니다.

## <a name="remarks"></a>설명

Using 선언은 다른 곳에서 선언 된 엔터티의 동의어로 정규화 되지 않은 이름을 도입 합니다. 이를 통해 특정 네임 스페이스의 단일 이름이 표시 되는 선언 영역에서 명시적인 자격 없이 사용 될 수 있습니다. 이는 네임 스페이스의 *모든* 이름을 한정자 없이 사용할 수 있도록 [하는 using 지시문](../cpp/namespaces-cpp.md#using_directives)과는 대조적입니다. **`using`** 키워드는 [형식 별칭](../cpp/aliases-and-typedefs-cpp.md)에도 사용 됩니다.

## <a name="example-using-declaration-in-class-field"></a>예: `using` 클래스 필드의 선언

Using 선언은 클래스 정의에서 사용할 수 있습니다.

```cpp
// using_declaration1.cpp
#include <stdio.h>
class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class D : B {
public:
   using B::f;    // B::f(char) is now visible as D::f(char)
   using B::g;    // B::g(char) is now visible as D::g(char)
   void f(int) {
      printf_s("In D::f()\n");
      f('c');     // Invokes B::f(char) instead of recursing
   }

   void g(int) {
      printf_s("In D::g()\n");
      g('c');     // Invokes B::g(char) instead of recursing
   }
};

int main() {
   D myD;
   myD.f(1);
   myD.g('a');
}
```

```Output
In D::f()
In B::f()
In B::g()
```

## <a name="example-using-declaration-to-declare-a-member"></a>예: `using` 멤버를 선언 하는 선언

멤버를 선언 하는 데 사용 하는 경우 using 선언은 기본 클래스의 멤버를 참조 해야 합니다.

```cpp
// using_declaration2.cpp
#include <stdio.h>

class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class C {
public:
   int g();
};

class D2 : public B {
public:
   using B::f;   // ok: B is a base of D2
   // using C::g;   // error: C isn't a base of D2
};

int main() {
   D2 MyD2;
   MyD2.f('a');
}
```

```Output
In B::f()
```

## <a name="example-using-declaration-with-explicit-qualification"></a>예: `using` 명시적 한정자를 사용한 선언

Using 선언을 사용 하 여 선언 된 멤버는 명시적 한정자를 사용 하 여 참조할 수 있습니다. `::`접두사는 전역 네임 스페이스를 참조 합니다.

```cpp
// using_declaration3.cpp
#include <stdio.h>

void f() {
   printf_s("In f\n");
}

namespace A {
   void g() {
      printf_s("In A::g\n");
   }
}

namespace X {
   using ::f;   // global f is also visible as X::f
   using A::g;   // A's g is now visible as X::g
}

void h() {
   printf_s("In h\n");
   X::f();   // calls ::f
   X::g();   // calls A::g
}

int main() {
   h();
}
```

```Output
In h
In f
In A::g
```

## <a name="example-using-declaration-synonyms-and-aliases"></a>예: `using` 선언 동의어 및 별칭

Using 선언이 생성 되 면 선언에 의해 생성 된 동의어가 using 선언 지점에서 유효한 정의만 참조 합니다. Using 선언 후에 네임 스페이스에 추가 된 정의는 유효한 동의어가 아닙니다.

선언에 의해 정의 되는 이름은 **`using`** 원래 이름에 대 한 별칭입니다. 원래 선언의 형식, 링크 또는 다른 특성에는 영향을 주지 않습니다.

```cpp
// post_declaration_namespace_additions.cpp
// compile with: /c
namespace A {
   void f(int) {}
}

using A::f;   // f is a synonym for A::f(int) only

namespace A {
   void f(char) {}
}

void f() {
   f('a');   // refers to A::f(int), even though A::f(char) exists
}

void b() {
   using A::f;   // refers to A::f(int) AND A::f(char)
   f('a');   // calls A::f(char);
}
```

## <a name="example-local-declarations-and-using-declarations"></a>예: 로컬 선언 및 `using` 선언

네임 스페이스의 함수와 관련 하 여 단일 이름에 대 한 로컬 선언 집합 및 선언 사용이 선언적 영역에 제공 되는 경우 모두 동일한 엔터티를 참조 하거나 모두 함수를 참조 해야 합니다.

```cpp
// functions_in_namespaces1.cpp
// C2874 expected
namespace B {
    int i;
    void f(int);
    void f(double);
}

void g() {
    int i;
    using B::i;   // error: i declared twice
    void f(char);
    using B::f;   // ok: each f is a function
}
```

위의 예제에서 `using B::i` 문은 두 번째가 `int i` 함수에 선언 되도록 `g()` 합니다. `using B::f` `f(char)` 에서 제공 하는 함수 이름에 `B::f` 다른 매개 변수 형식이 있으므로 문이 함수와 충돌 하지 않습니다.

## <a name="example-local-function-declarations-and-using-declarations"></a>예: 로컬 함수 선언 및 `using` 선언

로컬 함수 선언은 선언을 사용 하 여 도입 된 함수와 동일한 이름과 형식을 가질 수 없습니다. 예를 들면 다음과 같습니다.

```cpp
// functions_in_namespaces2.cpp
// C2668 expected
namespace B {
    void f(int);
    void f(double);
}

namespace C {
    void f(int);
    void f(double);
    void f(char);
}

void h() {
    using B::f;          // introduces B::f(int) and B::f(double)
    using C::f;          // C::f(int), C::f(double), and C::f(char)
    f('h');              // calls C::f(char)
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)
}
```

## <a name="example-using-declaration-and-inheritance"></a>예: `using` 선언 및 상속

상속과 관련 하 여, using 선언으로 기본 클래스에서 파생 클래스 범위로 이름이 제공 되는 경우 파생 클래스의 멤버 함수는 기본 클래스에서 동일한 이름 및 인수 형식을 사용 하 여 가상 멤버 함수를 재정의 합니다.

```cpp
// using_declaration_inheritance1.cpp
#include <stdio.h>
struct B {
   virtual void f(int) {
      printf_s("In B::f(int)\n");
   }

   virtual void f(char) {
      printf_s("In B::f(char)\n");
   }

   void g(int) {
      printf_s("In B::g\n");
   }

   void h(int);
};

struct D : B {
   using B::f;
   void f(int) {   // ok: D::f(int) overrides B::f(int)
      printf_s("In D::f(int)\n");
   }

   using B::g;
   void g(char) {   // ok: there is no B::g(char)
      printf_s("In D::g(char)\n");
   }

   using B::h;
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)
};

void f(D* pd) {
   pd->f(1);     // calls D::f(int)
   pd->f('a');   // calls B::f(char)
   pd->g(1);     // calls B::g(int)
   pd->g('a');   // calls D::g(char)
}

int main() {
   D * myd = new D();
   f(myd);
}
```

```Output
In D::f(int)
In B::f(char)
In B::g
In D::g(char)
```

## <a name="example-using-declaration-accessibility"></a>예: `using` 선언 액세스 가능성

Using 선언에서 언급 한 이름의 모든 인스턴스에 액세스할 수 있어야 합니다. 특히 파생 클래스에서 using 선언을 사용 하 여 기본 클래스의 멤버에 액세스 하는 경우 멤버 이름에 액세스할 수 있어야 합니다. 오버 로드 된 멤버 함수의 이름이 면 명명 된 모든 함수에 액세스할 수 있어야 합니다.

멤버의 액세스 가능성에 대 한 자세한 내용은 [멤버 Access Control](../cpp/member-access-control-cpp.md)를 참조 하세요.

```cpp
// using_declaration_inheritance2.cpp
// C2876 expected
class A {
private:
   void f(char);
public:
   void f(int);
protected:
   void g();
};

class B : public A {
   using A::f;   // C2876: A::f(char) is inaccessible
public:
   using A::g;   // B::g is a public synonym for A::g
};
```

## <a name="see-also"></a>참조

[네임스페이스](../cpp/namespaces-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
