---
description: '자세한 정보: 컴파일러 오류 C3867'
title: 컴파일러 오류 C3867
ms.date: 11/04/2016
f1_keywords:
- C3867
helpviewer_keywords:
- C3867
ms.assetid: bc5de03f-e01a-4407-88c3-2c63f0016a1e
ms.openlocfilehash: 5d4340a3e9f2fc94ac9debeded601a37223904aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222842"
---
# <a name="compiler-error-c3867"></a>컴파일러 오류 C3867

' func ': 함수 호출에 인수 목록이 없습니다. ' &func '를 사용 하 여 멤버에 대 한 포인터 만들기

멤버 함수를 클래스 이름 및 address-of 연산자로 한정하지 않고 멤버 함수의 이름을 사용하려고 했습니다.

이 오류는 Visual Studio 2005에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다. 향상 된 멤버 포인터 규칙입니다. Visual Studio 2005 이전에 컴파일된 코드는 이제 C3867을 생성 합니다.

## <a name="examples"></a>예제

잘못 제안된 해결 방법을 통해 컴파일러에서 C3867 오류가 발생할 수 있습니다. 가능하면 항상 최다 파생 클래스를 사용하세요.

다음 샘플에서는 C3867 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3867_1.cpp
// compile with: /c
struct Base {
protected:
   void Test() {}
};

class Derived : public Base {
   virtual void Bar();
};

void Derived::Bar() {
   void (Base::*p1)() = Test;   // C3867
   &Derived::Test;   // OK
}
```

다음 샘플에서는 C3867 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3867_2.cpp
#include<stdio.h>

struct S {
   char *func() {
      return "message";
   }
};

class X {
public:
   void f() {}
};

int main() {
   X::f;   // C3867

   // OK
   X * myX = new X;
   myX->f();

   S s;
   printf_s("test %s", s.func);   // C3867
   printf_s("test %s", s.func());   // OK
}
```

다음 샘플에서는 C3867 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3867_3.cpp
class X {
public:
   void mf(){}
};

int main() {
   void (X::*pmf)() = X::mf;   // C3867

   // try the following line instead
   void (X::*pmf2)() = &X::mf;
}
```

다음 샘플에서는 C3867 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3867_4.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b1;
      b1.p = f;   // C3867
   }
};
```

다음 샘플에서는 C3867 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3867_5.cpp
// compile with: /EHsc
#include <iostream>

class Testpm {
public:
   void m_func1() {
      std::cout << m_num << "\tm_func1\n";
    }

   int m_num;
   typedef void (Testpm::*pmfn1)();
   void func(Testpm* p);
};

void Testpm::func(Testpm* p) {
   pmfn1 s = m_func1;   // C3867
   pmfn1 s2 = &Testpm::m_func1;   // OK
   (p->*s2)();
}

int main() {
   Testpm *pTestpm = new Testpm;
   pTestpm->m_num = 10;

   pTestpm->func(pTestpm);
}
```
