---
description: '자세히 알아보기: 범위 (c + +)'
title: 범위 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
ms.openlocfilehash: 62f4e948f956565ef25bf612332a59823be6df23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319367"
---
# <a name="scope-c"></a>범위 (C++)

클래스, 함수 또는 변수와 같은 프로그램 요소를 선언 하는 경우 해당 이름을 "표시" 하 고 프로그램의 특정 부분 에서만 사용할 수 있습니다. 이름을 표시 하는 컨텍스트를 해당 *범위* 라고 합니다. 예를 들어 함수 내에서 변수를 선언 하는 경우는 `x` `x` 해당 함수 본문 내 에서만 볼 수 있습니다. *로컬 범위* 를 포함 합니다. 프로그램에 동일한 이름의 다른 변수가 있을 수 있습니다. 서로 다른 범위에 있으면 하나의 정의 규칙을 위반 하지 않으며 오류가 발생 하지 않습니다.

자동 비정적 변수의 경우 범위는 프로그램 메모리에서 만들어지고 삭제 되는 시기를 결정 하기도 합니다.

범위에는 다음 6 가지 종류가 있습니다.

- **전역 범위** 전역 이름은 클래스, 함수 또는 네임 스페이스 외부에서 선언 된 이름입니다. 그러나 c + +에서는 이러한 이름이 암시적 전역 네임 스페이스와 함께 존재 하기도 합니다. 전역 이름의 범위는 선언 지점부터 선언 되는 파일의 끝까지 확장 됩니다. 전역 이름의 경우에는 이름이 프로그램의 다른 파일에 표시 되는지 여부를 결정 하는 [링크](program-and-linkage-cpp.md) 규칙에 따라 표시 여부가 결정 됩니다.

- **네임 스페이스 범위** 클래스 또는 열거형 정의 나 함수 블록 외부에서 [네임 스페이스](namespaces-cpp.md)내에 선언 된 이름은 선언 지점에서 네임 스페이스의 끝까지 표시 됩니다. 네임 스페이스는 여러 파일에 걸쳐 여러 블록에 정의 될 수 있습니다.

- **로컬 범위** 매개 변수 이름을 포함 하 여 함수 또는 람다 내에 선언 된 이름에는 로컬 범위가 있습니다. 흔히 "지역" 이라고 합니다. 선언 지점에서 함수 또는 람다 본문의 끝까지 볼 수 있습니다. 로컬 범위는이 문서의 뒷부분에서 설명 하는 블록 범위의 일종입니다.

- **클래스 범위** 클래스 멤버의 이름에는 선언 지점에 관계 없이 클래스 정의 전체에서 확장 되는 클래스 범위가 있습니다. 클래스 멤버 액세스 가능성은 **`public`** , 및 키워드를 통해 추가로 제어 됩니다 **`private`** **`protected`** . Public 또는 protected 멤버는 멤버 선택 연산자 (를 사용 해야만 액세스할 수 있습니다 **.** or **->** ) 또는 멤버 포인터 연산자 (**.** <strong>\*</strong> 또는)를 가리킵니다 **->** <strong>\*</strong> .

- **문 범위** ,, 또는 문에 선언 된 이름은 **`for`** **`if`** **`while`** **`switch`** 문 블록이 끝날 때까지 표시 됩니다.

- **함수 범위** [레이블에](labeled-statements.md) 는 함수 범위가 있으므로 선언 지점 앞에도 함수 본문 전체에 표시 됩니다. 함수 범위를 사용 하면 `goto cleanup` 레이블이 선언 되기 전에와 같은 문을 작성할 수 있습니다 `cleanup` .

## <a name="hiding-names"></a>이름 숨기기

이름을 포함된 블록에서 선언하여 숨길 수 있습니다. 다음 그림에서는 `i`가 내부 블록 안에서 다시 선언되므로 바깥쪽 블록 범위에서 `i`와 연결된 변수가 숨겨집니다.

![블록&#45;범위 이름 숨기기](../cpp/media/vc38sf1.png "블록&#45;범위 이름 숨기기") <br/>
블록 범위 및 이름 숨기기

그림에 표시된 프로그램의 출력은 다음과 같습니다.

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> `szWhat` 인수는 함수 범위에 있는 것으로 간주되므로 함수의 가장 바깥쪽 블록에서 선언된 것처럼 취급됩니다.

## <a name="hiding-class-names"></a>클래스 이름 숨기기

함수, 개체, 변수 또는 열거자를 동일한 코드에서 선언하여 클래스 이름을 숨길 수 있습니다. 그러나 키워드 앞에 키워드를 추가 하는 경우에도 클래스 이름에 액세스할 수 있습니다 **`class`** .

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as
                                       //  class name

    cout << "Opening account with a balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with a balance of: 15.37
```

> [!NOTE]
> 클래스 이름 ( `Account` )이 호출 되는 모든 장소에서 키워드 클래스를 사용 하 여 전역 범위 변수 계정과 구분 해야 합니다. 이 규칙은 범위 결정 연산자(::)의 왼쪽에 클래스 이름이 나타나는 경우에는 적용되지 않습니다. 범위 결정 연산자의 왼쪽에 있는 이름은 항상 클래스 이름으로 간주됩니다.

다음 예제에서는 `Account` 키워드를 사용 하 여 형식의 개체에 대 한 포인터를 선언 하는 방법을 보여 줍니다 **`class`** .

```cpp
class Account *Checking = new class Account( Account );
```

`Account`앞의 문에서 이니셜라이저의 (괄호 안에 있음)에는 전역 범위가 있습니다. 즉, 형식입니다 **`double`** .

> [!NOTE]
> 이 예제와 같이 식별자 이름을 다시 사용하는 것은 좋지 않은 프로그래밍 스타일로 간주됩니다.

클래스 개체의 선언 및 초기화에 대 한 자세한 내용은 [클래스, 구조체 및 공용 구조체](../cpp/classes-and-structs-cpp.md)를 참조 하세요. 및 무료 저장소 연산자를 사용 하는 방법에 대 한 자세한 내용은 **`new`** **`delete`** [new 및 delete 연산자](new-and-delete-operators.md)를 참조 하세요.

## <a name="hiding-names-with-global-scope"></a>전역 범위를 사용 하 여 이름 숨기기

블록 범위에서 동일한 이름을 명시적으로 선언 하 여 전역 범위를 가진 이름을 숨길 수 있습니다. 그러나 범위 결정 연산자 ()를 사용 하 여 전역 범위 이름을 액세스할 수 있습니다 `::` .

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>참고 항목

[기본 개념](../cpp/basic-concepts-cpp.md)
