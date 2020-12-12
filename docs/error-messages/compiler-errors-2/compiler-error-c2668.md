---
description: '자세한 정보: 컴파일러 오류 C2668'
title: 컴파일러 오류 C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: 87ae1cfa3588b8b524d73d717365206c9b7213ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210688"
---
# <a name="compiler-error-c2668"></a>컴파일러 오류 C2668

' function ': 오버 로드 된 함수에 대 한 호출이 모호 합니다.

지정 된 오버 로드 된 함수 호출을 확인할 수 없습니다. 하나 이상의 실제 매개 변수를 명시적으로 캐스팅 해야 할 수 있습니다.

템플릿 사용을 통해이 오류를 가져올 수도 있습니다. 동일한 클래스에서 같은 서명을 사용 하는 일반 멤버 함수 및 템플릿 멤버 함수가 있는 경우 템플릿 기반 함수를 먼저 가져와야 합니다. 이는 Visual C++의 현재 구현에 대 한 제한 사항입니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2668를 생성 합니다.

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

[Using 선언을 사용](../../cpp/using-declaration.md)하 여이 오류를 해결할 수도 있습니다.

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

이 오류는 Visual Studio .NET 2003에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다. 즉, 상수 0 캐스트가 모호 하 게 변환 됩니다.

Int는 long과 void *를 모두 변환 해야 하므로 상수 0을 사용 하는 캐스트의 변환은 모호 합니다. 이 오류를 해결 하려면 0을 사용 하는 함수 매개 변수의 정확한 형식으로 캐스팅 해야 합니다 .이 코드는 Visual Studio .NET 2003 및 Visual Studio .NET 버전의 Visual C++에서 유효 합니다.

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

이 오류는 이제 CRT에 모든 수학 함수의 float 및 double 형식이 있기 때문에 발생할 수 있습니다.

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

Pow (int, int)가 CRT의 math에서 제거 되었기 때문에이 오류가 발생할 수 있습니다.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

이 코드는 Visual Studio 2015에서 성공 하지만 Visual Studio 2017 이상 C2668에서 실패 합니다. Visual Studio 2015에서 컴파일러는 일반 copy-initialization과 같은 방식으로 copy-list-initialization을 잘못 처리했고 오버로드 확인을 위해 생성자 변환만 고려했습니다.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```
