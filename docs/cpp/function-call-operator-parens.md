---
description: '자세한 정보: 함수 호출 연산자: ()'
title: '함수 호출 연산자: ()'
ms.date: 06/11/2020
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
no-loc:
- opt
ms.openlocfilehash: 351674f345c7213a3c164ff88e9a165775088c68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344564"
---
# <a name="function-call-operator-"></a>함수 호출 연산자: ()

함수 호출은 *`postfix-expression`* 함수 또는 호출 가능 개체로 계산 되 고 함수 호출 연산자가 있는 식으로 구성 된의 일종입니다 **`()`** . 개체는 `operator ()` 개체에 대 한 함수 호출 의미 체계를 제공 하는 함수를 선언할 수 있습니다.

## <a name="syntax"></a>구문

> *`postfix-expression`*:\
> &emsp;*`postfix-expression`* **`(`** *`argument-expression-list`* <sub>opt</sub> **`)`**

## <a name="remarks"></a>설명

함수 호출 연산자에 대 한 인수는 *`argument-expression-list`* 쉼표로 구분 된 식 목록에서 제공 됩니다. 이러한 식의 값은 인수로 함수에 전달 됩니다. *인수 식 목록은* 비워 둘 수 있습니다. C + + 17 이전에는 함수 식 및 인수 식의 계산 순서가 지정 되지 않으며 순서에 관계 없이 발생할 수 있습니다. C + + 17 이상에서 함수 식은 인수 식 또는 기본 인수 앞에서 계산 됩니다. 인수 식은 결정 되지 않은 시퀀스에서 계산 됩니다.

는 *`postfix-expression`* 호출할 함수로 평가 됩니다. 다음과 같은 여러 가지 형태를 사용할 수 있습니다.

- 현재 범위 또는 제공 된 함수 인수의 범위에서 표시 되는 함수 식별자입니다.
- 함수, 함수 포인터, 호출 가능 개체 또는 하나에 대 한 참조로 계산 되는 식입니다.
- 명시적 이거나 묵시적 인 멤버 함수 접근자
- 멤버 함수에 대 한 역참조 된 포인터입니다.

는 *`postfix-expression`* 오버 로드 된 함수 식별자 또는 오버 로드 된 멤버 함수 접근자 일 수 있습니다. 오버 로드 확인에 대 한 규칙은 호출할 실제 함수를 결정 합니다. 멤버 함수가 virtual 인 경우 호출할 함수는 런타임에 결정 됩니다.

몇 가지 예제 선언:

- `T` 형식을 반환하는 함수. 선언 예제:

    ```cpp
    T func( int i );
    ```

- `T` 형식을 반환하는 함수의 포인터. 선언 예제:

    ```cpp
    T (*func)( int i );
    ```

- `T` 형식을 반환하는 함수의 참조. 선언 예제:

    ```cpp
    T (&func)(int i);
    ```

- `T` 형식을 반환하는 멤버 포인터 함수 역참조. 함수 호출 예제:

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>예제

다음 예제에서는 3개의 인수로 표준 라이브러리 함수 `strcat_s`를 호출합니다.

```cpp
// expre_Function_Call_Operator.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library name space
using namespace std;

int main()
{
    enum
    {
        sizeOfBuffer = 20
    };

    char s1[ sizeOfBuffer ] = "Welcome to ";
    char s2[ ] = "C++";

    strcat_s( s1, sizeOfBuffer, s2 );

    cout << s1 << endl;
}
```

```Output
Welcome to C++
```

## <a name="function-call-results"></a>함수 호출 결과

함수가 참조 형식으로 선언 되지 않은 경우 함수 호출은 rvalue로 평가 됩니다. 참조 반환 형식이 있는 함수는 lvalues로 계산 됩니다. 이러한 함수는 다음에 표시 된 것 처럼 대입문의 왼쪽에서 사용할 수 있습니다.

```cpp
// expre_Function_Call_Results.cpp
// compile with: /EHsc
#include <iostream>
class Point
{
public:
    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
private:
    unsigned _x;
    unsigned _y;
};

using namespace std;
int main()
{
    Point ThePoint;

    ThePoint.x() = 7;           // Use x() as an l-value.
    unsigned y = ThePoint.y();  // Use y() as an r-value.

    // Use x() and y() as r-values.
    cout << "x = " << ThePoint.x() << "\n"
         << "y = " << ThePoint.y() << "\n";
}
```

위의 코드는 `Point` *x* 및 *y* 좌표를 나타내는 전용 데이터 개체를 포함 하는 라는 클래스를 정의 합니다. 이러한 데이터 개체를 수정하고 해당 값을 검색해야 합니다. 이 프로그램은 이러한 클래스를 위한 여러 디자인 중 하나이며, `GetX`와 `SetX` 또는 `GetY`와 `SetY` 함수는 사용할 수 있는 디자인입니다.

클래스 형식, 클래스 형식에 대한 포인터 또는 클래스 형식에 대한 참조를 반환하는 함수는 멤버 선택 연산자에 대한 왼쪽 피연산자로 사용할 수 있습니다. 다음 코드는 유효 합니다.

```cpp
// expre_Function_Results2.cpp
class A {
public:
   A() {}
   A(int i) {}
   int SetA( int i ) {
      return (I = i);
   }

   int GetA() {
      return I;
   }

private:
   int I;
};

A func1() {
   A a = 0;
   return a;
}

A* func2() {
   A *a = new A();
   return a;
}

A& func3() {
   A *a = new A();
   A &b = *a;
   return b;
}

int main() {
   int iResult = func1().GetA();
   func2()->SetA( 3 );
   func3().SetA( 7 );
}
```

함수를 재귀적으로 호출할 수 있습니다. 함수 선언에 대 한 자세한 내용은 [함수](functions-cpp.md)를 참조 하세요. 관련 자료는 [변환 단위와 링크](../cpp/program-and-linkage-cpp.md)에 있습니다.

## <a name="see-also"></a>참고 항목

[후위 식](../cpp/postfix-expressions.md)<br/>
[C + + 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[함수 호출](../c-language/function-call-c.md)
