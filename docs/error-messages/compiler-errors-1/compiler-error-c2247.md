---
description: '자세한 정보: 컴파일러 오류 C2247'
title: 컴파일러 오류 C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: 480d3862a1f96517ecce11be5c695e106eb58d7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177941"
---
# <a name="compiler-error-c2247"></a>컴파일러 오류 C2247

' t r u e '에서 ' class '로 상속 하기 위해 ' 지정자 '를 사용 하므로 ' identifier '에 액세스할 수 없습니다.

`identifier` 는 개인 또는 보호 된 액세스를 사용 하 여 선언 된 클래스에서 상속 됩니다.

다음 샘플에서는 C2247를 생성 합니다.

```cpp
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

이 오류는 Visual Studio .NET 2003에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다. 보호 된 멤버를 사용 하 여 액세스를 제어 합니다. 보호 된 멤버 (n)는 클래스 (n)가 멤버인 클래스 (B)의 멤버 함수를 통해서만 액세스할 수 있습니다.

Visual Studio .NET 2003 및 Visual Studio .NET 버전 Visual C++ 모두에서 유효한 코드의 경우 멤버를 형식의 friend로 선언 합니다. 공용 상속도 사용할 수 있습니다.

```cpp
// C2247b.cpp
// compile with: /c
// C2247 expected
class A {
public:
   void f();
   int n;
};

class B: protected A {
   // Uncomment the following line to resolve.
   // friend void A::f();
};

void A::f() {
   B b;
   b.n;
}
```

C2247는 Visual Studio .NET 2003에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다. 이제 전용 기본 클래스에 액세스할 수 없습니다. 형식에 대 한 개인 기본 클래스인 클래스 (B)는 B를 기본 클래스로 사용 하는 형식 (C)에 액세스할 수 없습니다.

Visual Studio .NET 2003 및 Visual Studio .NET 버전 Visual C++ 모두에서 유효한 코드의 경우 범위 연산자를 사용 합니다.

```cpp
// C2247c.cpp
// compile with: /c
struct A {};

struct B: private A {};

struct C : B {
   void f() {
      A *p1 = (A*) this;   // C2247
      // try the following line instead
      // ::A *p2 = (::A*) this;
   }
};
```
