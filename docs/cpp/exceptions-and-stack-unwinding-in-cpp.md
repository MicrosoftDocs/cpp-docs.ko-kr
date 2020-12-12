---
description: '자세한 정보: c + +에서 예외 및 스택 해제'
title: C++ 예외 및 스택 해제
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 4f9c5faff4dafcae41831eb4b24345134912b073
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164785"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++에서 예외 및 스택 해제

C++ 예외 메커니즘에서 컨트롤은 throw 문에서 throw된 형식을 처리할 수 있는 첫 번째 catch 문으로 이동합니다. Catch 문에 도달 하면 throw 및 catch 문 사이의 범위에 있는 모든 자동 변수는 *스택* 해제로 알려진 프로세스에서 제거 됩니다. 스택 해제에서 실행은 다음과 같이 진행됩니다.

1. 제어가 **`try`** 일반적인 순차적 실행에 의해 문에 도달 합니다. 블록의 보호 된 섹션이 **`try`** 실행 됩니다.

1. 보호 된 섹션을 실행 하는 동안 예외가 throw 되지 않으면 **`catch`** 블록 다음에 오는 절이 **`try`** 실행 되지 않습니다. 연결 된 블록 다음에 오는 마지막 절 다음의 문에서 실행이 계속 됩니다 **`catch`** **`try`** .

1. 보호 된 섹션을 실행 하는 동안 또는 보호 된 섹션에서 직접적으로 또는 간접적으로 호출 하는 루틴에서 예외가 throw 되 면 피연산자가 만든 개체에서 예외 개체가 만들어집니다 **`throw`** . 이는 복사 생성자가 포함 될 수도 있음을 의미 합니다. 이 시점에서 컴파일러는 **`catch`** throw 된 형식의 예외를 처리할 수 있는 더 높은 실행 컨텍스트 또는 **`catch`** 모든 형식의 예외를 처리할 수 있는 처리기에 대 한 절을 찾습니다. **`catch`** 처리기는 블록 뒤의 모양 순서 대로 검사 됩니다 **`try`** . 적절 한 처리기를 찾을 수 없는 경우 다음 동적 바깥쪽 **`try`** 블록을 검사 합니다. 이 프로세스는 가장 바깥쪽 블록이 검사 될 때까지 계속 됩니다 **`try`** .

1. 일치하는 처리기를 여전히 찾을 수 없거나 해제 프로세스 중 처리기가 컨트롤을 갖기 전에 예외가 발생하는 경우 미리 정의된 런타임 함수 `terminate`가 호출됩니다. 예외가 throw되었지만 해제 작업을 시작하기 전에 예외가 발생하는 경우 `terminate`가 호출됩니다.

1. 일치 하는 **`catch`** 처리기를 찾은 다음 값으로 catch 하는 경우 해당 형식 매개 변수는 예외 개체를 복사 하 여 초기화 됩니다. 참조로 catch하면 예외 개체를 참조하도록 매개 변수가 초기화됩니다. 정식 매개 변수가 초기화된 후 스택 해제 프로세스가 시작됩니다. 여기에는 처리기와 연결 된 블록의 시작과 **`try`** 예외의 throw 사이트 사이에서 완전히 구성 되었지만 아직 소멸 되지 않은 모든 자동 개체의 소멸이 포함 됩니다 **`catch`** . 소멸은 생성과 반대 순서로 발생합니다. **`catch`** 처리기가 실행 되 고 프로그램은 마지막 처리기 (즉, 처리기가 아닌 첫 번째 문 또는 구문) 이후에 실행을 다시 시작 합니다 **`catch`** . 컨트롤은 문에서 문이나 **`catch`** 레이블을 통해서가 아니라 throw 된 예외를 통해서만 처리기를 입력할 수 있습니다 **`goto`** **`case`** **`switch`** .

## <a name="stack-unwinding-example"></a>스택 해제 예

다음 예제에서는 예외가 throw되면 어떻게 스택이 해제되는지 보여 줍니다. 스레드에서의 실행은 방식에 따라 각 함수를 해제하면서 `C`의 throw 문에서 `main`의 catch 문으로 점프합니다. `Dummy` 개체가 만들어진 다음 범위에서 벗어날 때 제거되는 순서를 살펴보십시오. 또한 catch 문이 포함된 `main`을 제외하고는 어떤 함수도 완료할 수 없습니다. 함수 `A`는 `B()` 호출에서 반환되지 않으며 `B`도 `C()` 호출에서 반환되지 않습니다. `Dummy` 포인터의 정의 및 해당 delete 문에 대한 주석 처리를 제거한 다음 프로그램을 실행하면 포인터가 삭제되지 않습니다. 이는 함수가 예외 보장을 제공하지 않는 경우 발생할 수 있음을 보여 줍니다. 자세한 내용은 방법: 예외 디자인을 참조하십시오. catch 문을 주석으로 처리하는 경우 처리되지 않은 예외로 인해 프로그램을 종료할 때 나타나는 현상을 확인할 수 있습니다.

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName;
    int level;
};

void C(Dummy d, int i)
{
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);
    cout << "Exiting FunctionB" << endl;
}

void A(Dummy d, int i)
{
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd;
    cout << "Exiting FunctionA" << endl;
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```
