---
description: '자세한 정보: 추상 클래스 (c + +)'
title: 추상 클래스 (c + +)
ms.date: 02/18/2021
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.openlocfilehash: 8a20e988cb0c0a134fd2ebb83382d81c838bcf23
ms.sourcegitcommit: 5efc34c2b98d4d0d3e41aec38b213f062c19d078
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844496"
---
# <a name="abstract-classes-c"></a>추상 클래스 (c + +)

추상 클래스는 보다 구체적인 클래스가 파생될 수 있는 일반 개념의 식 역할을 합니다. 추상 클래스 형식의 개체를 만들 수 없습니다. 그러나 추상 클래스 형식에 대 한 포인터 및 참조를 사용할 수 있습니다.

하나 이상의 순수 가상 멤버 함수를 선언 하 여 추상 클래스를 만듭니다. 순수 지정자 () 구문을 사용 하 여 선언 된 가상 함수입니다 `= 0` . 추상 클래스에서 파생된 클래스는 순수 가상 함수를 구현해야 합니다. 이렇게 하지 않으면 파생된 클래스도 추상 클래스가 됩니다.

[가상 함수](../cpp/virtual-functions.md)에 제공 된 예제를 참조 하세요. `Account` 클래스의 용도는 일반적인 기능을 제공하는 것이지만, `Account` 형식의 개체는 너무 일반적이어서 유용하게 사용하기가 어렵습니다. 즉, `Account` 다음은 추상 클래스에 적합 한 후보입니다.

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

이 선언과 이전 선언의 유일한 차이점은 `PrintBalance`가 순수 지정자(`= 0`)를 사용하여 선언되었다는 것입니다.

## <a name="restrictions-on-abstract-classes"></a>추상 클래스에 대한 제한

추상 클래스는 다음에 사용할 수 없습니다.

- 변수 또는 멤버 데이터

- 인수 형식

- 함수 반환 형식

- 명시적 변환 형식

추상 클래스에 대 한 생성자가 직접 또는 간접적으로 순수 가상 함수를 호출 하는 경우 결과가 정의 되지 않습니다. 하지만 추상 클래스의 생성자 및 소멸자는 다른 멤버 함수를 호출할 수 있습니다.

## <a name="defined-pure-virtual-functions"></a>정의 된 순수 가상 함수

추상 클래스의 순수 가상 함수를 *정의* 하거나 구현할 수 있습니다. 정규화 된 구문만 사용 하 여 이러한 함수를 호출할 수 있습니다.

*추상-클래스-이름*::*함수 이름*()

정의 된 순수 가상 함수는 순수 가상 소멸자를 포함 하는 기본 클래스의 클래스 계층 구조를 디자인 하는 경우에 유용 합니다. 이는 기본 클래스 소멸자가 항상 개체 소멸 중에 호출 되기 때문입니다. 다음 예제를 참조하세요.

```cpp
// deriv_RestrictionsOnUsingAbstractClasses.cpp
// Declare an abstract base class with a pure virtual destructor.
// It's the simplest possible abstract class.
class base
{
public:
    base() {}
    virtual ~base() = 0 {}; // pure virtual, and defined!
};

class derived : public base
{
public:
    derived() {}
    ~derived() {}
};

int main()
{
    derived aDerived; // destructor called when it goes out of scope
}
```

예제에서는 인라인의 정의를 보여 `~base()` 주지만를 사용 하 여 클래스 외부에서 정의할 수도 있습니다 `base::~base() {}` .

개체가 범위를 벗어나면 `aDerived` 클래스의 소멸자 `derived` 가 호출 됩니다. 컴파일러가 소멸자 이후에 클래스의 소멸자를 암시적으로 호출 하는 코드를 생성 합니다 `base` `derived` . 순수 가상 함수에 대 한 빈 구현은 `~base` 함수에 대해 최소한의 구현이 있는지 확인 합니다. 이 메서드를 사용 하지 않으면 링커가 암시적 호출에 대해 확인 되지 않은 외부 기호 오류를 생성 합니다.

> [!NOTE]
> 앞의 예제에서 순수 가상 함수인 `base::~base`는 `derived::~derived`에서 암시적으로 호출됩니다. 정규화 된 멤버 함수 이름을 사용 하 여 명시적으로 순수 가상 함수를 호출할 수도 있습니다. 이러한 함수에는 구현이 있어야 합니다. 그렇지 않으면 연결 시 오류가 발생 합니다.

## <a name="see-also"></a>추가 정보

[상속](../cpp/inheritance-cpp.md)
