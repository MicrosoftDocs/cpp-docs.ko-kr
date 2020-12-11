---
description: '자세한 정보: 가상 함수'
title: 가상 함수
ms.date: 09/10/2019
helpviewer_keywords:
- functions [C++], virtual functions
- derived classes [C++], virtual functions
- virtual functions
ms.assetid: b3e1ed88-2a90-4af8-960a-16f47deb3452
ms.openlocfilehash: a8e253f8debd594b1918fdcb2aed75b559b07ca8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161341"
---
# <a name="virtual-functions"></a>가상 함수

가상 함수는 파생 클래스에서 다시 정의할 멤버 함수입니다. 기본 클래스의 포인터나 참조를 사용하여 파생 클래스 개체를 참조할 때 해당 개체의 가상 함수를 호출하고 파생 클래스의 함수 버전을 실행할 수 있습니다.

가상 함수를 사용하면 함수 호출을 만드는 데 사용한 식과 관계없이 개체에 적합한 함수가 호출됩니다.

기본 클래스에 [가상](../cpp/virtual-cpp.md) 으로 선언 된 함수가 포함 되어 있고 파생 클래스가 동일한 함수를 정의 한다고 가정 합니다. 기본 클래스의 포인터나 참조를 사용하여 호출되더라도 파생 클래스의 개체에 대해 파생 클래스의 함수가 호출됩니다. 다음 예제에서는 `PrintBalance` 함수와 파생 클래스 2개의 구현을 제공하는 기본 클래스를 보여 줍니다.

```cpp
// deriv_VirtualFunctions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Account {
public:
   Account( double d ) { _balance = d; }
   virtual ~Account() {}
   virtual double GetBalance() { return _balance; }
   virtual void PrintBalance() { cerr << "Error. Balance not available for base type." << endl; }
private:
    double _balance;
};

class CheckingAccount : public Account {
public:
   CheckingAccount(double d) : Account(d) {}
   void PrintBalance() { cout << "Checking account balance: " << GetBalance() << endl; }
};

class SavingsAccount : public Account {
public:
   SavingsAccount(double d) : Account(d) {}
   void PrintBalance() { cout << "Savings account balance: " << GetBalance(); }
};

int main() {
   // Create objects of type CheckingAccount and SavingsAccount.
   CheckingAccount checking( 100.00 );
   SavingsAccount  savings( 1000.00 );

   // Call PrintBalance using a pointer to Account.
   Account *pAccount = &checking;
   pAccount->PrintBalance();

   // Call PrintBalance using a pointer to Account.
   pAccount = &savings;
   pAccount->PrintBalance();
}
```

위의 코드에서 `PrintBalance` 개체가 가리키는 경우를 제외하고 `pAccount`에 대한 호출이 동일합니다. `PrintBalance`가 virtual이므로 각 개체에 정의된 함수의 버전이 호출됩니다. 파생 클래스 `PrintBalance` 및 `CheckingAccount`의 `SavingsAccount` 함수가 기본 클래스 `Account`의 함수를 "재정의"합니다.

`PrintBalance` 함수의 재정의 구현을 제공하지 않는 클래스가 선언되면 기본 클래스 `Account`의 기본 구현이 사용됩니다.

형식이 같을 경우에만 파생 클래스의 함수가 기본 클래스에서 가상 함수를 재정의합니다. 파생 클래스의 함수는 기본 클래스의 가상 함수와 반환 형식만 같고 인수 목록은 달라야 합니다.

포인터나 참조를 사용하여 함수를 호출할 때 다음 규칙이 적용됩니다.

- 가상 함수 호출은 호출된 개체의 기본 형식에 따라 확인됩니다.

- 비가상 함수 호출은 포인터나 참조의 형식에 따라 확인됩니다.

다음 예제에서는 포인터를 통해 호출된 가상 함수와 비가상 함수의 동작을 보여 줍니다.

```cpp
// deriv_VirtualFunctions2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base {
public:
   virtual void NameOf();   // Virtual function.
   void InvokingClass();   // Nonvirtual function.
};

// Implement the two functions.
void Base::NameOf() {
   cout << "Base::NameOf\n";
}

void Base::InvokingClass() {
   cout << "Invoked by Base\n";
}

class Derived : public Base {
public:
   void NameOf();   // Virtual function.
   void InvokingClass();   // Nonvirtual function.
};

// Implement the two functions.
void Derived::NameOf() {
   cout << "Derived::NameOf\n";
}

void Derived::InvokingClass() {
   cout << "Invoked by Derived\n";
}

int main() {
   // Declare an object of type Derived.
   Derived aDerived;

   // Declare two pointers, one of type Derived * and the other
   //  of type Base *, and initialize them to point to aDerived.
   Derived *pDerived = &aDerived;
   Base    *pBase    = &aDerived;

   // Call the functions.
   pBase->NameOf();           // Call virtual function.
   pBase->InvokingClass();    // Call nonvirtual function.
   pDerived->NameOf();        // Call virtual function.
   pDerived->InvokingClass(); // Call nonvirtual function.
}
```

```Output
Derived::NameOf
Invoked by Base
Derived::NameOf
Invoked by Derived
```

`NameOf` 함수가 `Base`의 포인터를 통해 호출되건 `Derived`의 포인터를 통해 호출되건 관계없이 `Derived`에 대한 함수를 호출합니다. `Derived` 가 가상 함수이고 `NameOf` 및 `pBase`가 모두 `pDerived` 형식의 개체를 가리키므로 `Derived`에 대한 함수를 호출합니다.

가상 함수는 클래스 형식의 개체에 대해서만 호출 되므로 전역 함수 또는 정적 함수를로 선언할 수 없습니다 **`virtual`** .

**`virtual`** 키워드는 파생 클래스에서 재정의 함수를 선언 하는 경우에 사용할 수 있지만 필요 하지 않습니다. 가상 함수의 재정의는 항상 가상입니다.

기본 클래스의 가상 함수는 *순수 지정자* 를 사용 하 여 선언 된 경우를 제외 하 고 정의 해야 합니다. 순수 가상 함수에 대 한 자세한 내용은 [추상 클래스](../cpp/abstract-classes-cpp.md)를 참조 하세요.

범위 결정 연산자(`::`)를 사용하여 함수 이름을 명시적으로 정규화하여 가상 함수 호출 메커니즘을 억제할 수 있습니다. `Account` 클래스가 포함된 이전의 예제를 생각해 보십시오. 기본 클래스에서 `PrintBalance`를 호출하려면 다음과 같은 코드를 사용하세요.

```cpp
CheckingAccount *pChecking = new CheckingAccount( 100.00 );

pChecking->Account::PrintBalance();  //  Explicit qualification.

Account *pAccount = pChecking;  // Call Account::PrintBalance

pAccount->Account::PrintBalance();   //  Explicit qualification.
```

위의 예제에서 `PrintBalance`에 대한 두 호출 모두 가상 함수 호출 메커니즘을 억제합니다.
