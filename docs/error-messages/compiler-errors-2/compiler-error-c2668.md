---
title: 컴파일러 오류 C2668 | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3b318c663bb036629086d0bca9a67641e3c4c4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093755"
---
# <a name="compiler-error-c2668"></a>컴파일러 오류 C2668

'function': 오버 로드 된 함수에 대 한 모호한 호출

지정 된 오버 로드 된 함수 호출을 확인할 수 없습니다. 하나 이상의 실제 매개 변수를 명시적으로 캐스팅 하려고 합니다.

또한 템플릿 사용 하 여이 오류를 가져올 수 있습니다. 동일한 클래스에는 일반 멤버 함수와 동일한 서명 사용 하 여 템플릿 멤버 함수는 것이 있다면, 템플릿 기반 하나는 첫 번째 이어야 합니다. Visual c + +의 현재 구현 제한 됩니다.

함수 템플릿의 부분 순서 지정에 자세한 내용은 기술 자료 문서 Q240869를 참조 하세요.

지 원하는 COM 개체를 포함 하는 ATL 프로젝트를 빌드하는 경우 `ISupportErrorInfo`, q 243298 기술 자료 문서를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2668을 생성합니다.

```
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

## <a name="example"></a>예제

이 오류를 해결 하는 또 다른 방법은 사용 하 여 것을 [선언을 사용 하 여](../../cpp/using-declaration.md):

```
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

## <a name="example"></a>예제

이 오류는 Visual Studio.NET 2003에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다: 상수 0의 캐스트에 모호한 변환 합니다.

Int long 및 void *으로 변환을 모두 필요 하므로 상수 0을 사용 하 여 캐스트 변환이 모호 합니다. 이 오류를 해결 하려면 0을 변환 되지 않습니다 (이 코드는 Visual c + +의 Visual Studio.NET 2003 및 VISUAL Studio 버전에서 사용할 수는) 수행 되도록에 사용 되는 함수 매개 변수의 정확한 형식으로 캐스팅 합니다.

```
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

## <a name="example"></a>예제

CRT는 이제 float 및 double 형식의 모든 수학 함수에이 오류가 발생할 수 있습니다.

```
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

## <a name="example"></a>예제

Pow (int, int) math.h에서 CRT에서 제거 되었기 때문에이 오류가 발생할 수 있습니다.

```
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>예제

이 코드 Visual Studio 2015에서는 성공 하지만 C2668와 나중에 Visual Studio 2017에서 실패 합니다. Visual Studio 2015에서 컴파일러는 일반 copy-initialization과 같은 방식으로 copy-list-initialization을 잘못 처리했고 오버로드 확인을 위해 생성자 변환만 고려했습니다.

```
C++
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