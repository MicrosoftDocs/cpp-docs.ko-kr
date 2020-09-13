---
title: 생성자 (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 3694dc72860892d778533de2e40898faf9cc287d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042162"
---
# <a name="constructors-c"></a>생성자 (C++)

클래스 멤버를 초기화 하는 방법을 사용자 지정 하거나 클래스의 개체를 만들 때 함수를 호출 하려면 *생성자*를 정의 합니다. 생성자는 클래스와 같은 이름을 사용하며 반환 값이 없습니다. 여러 가지 방법으로 초기화를 사용자 지정 하기 위해 필요한 만큼 오버 로드 된 생성자를 정의할 수 있습니다. 일반적으로 생성자는 클래스 정의 또는 상속 계층 구조 외부의 코드에서 클래스의 개체를 만들 수 있도록 공용 액세스 가능성을 갖습니다. 그러나 생성자를 또는로 선언할 수도 있습니다 **`protected`** **`private`** .

생성자는 필요에 따라 멤버 init 목록을 사용할 수 있습니다. 이는 생성자 본문에서 값을 할당 하는 것 보다 더 효율적으로 클래스 멤버를 초기화 하는 방법입니다. 다음 예제에서는 `Box` 세 개의 오버 로드 된 생성자가 있는 클래스를 보여 줍니다. 마지막 두 가지 사용 멤버 init 목록은 다음과 같습니다.

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

클래스의 인스턴스를 선언 하는 경우 컴파일러는 오버 로드 확인 규칙에 따라 호출할 생성자를 선택 합니다.

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- 생성자는 **`inline`** , [explicit](#explicit_constructors) **`friend`** 또는 [constexpr](#constexpr_constructors)로 선언할 수 있습니다.
- 생성자는, 또는로 선언 된 개체를 초기화할 수 **`const`** 있습니다 **`volatile`** **`const volatile`** . **`const`** 생성자가 완료 된 후 개체가 됩니다.
- 구현 파일에서 생성자를 정의 하려면 다른 멤버 함수와 마찬가지로 정규화 된 이름을 지정 `Box::Box(){...}` 합니다.

## <a name="member-initializer-lists"></a><a name="member_init_list"></a> 멤버 이니셜라이저 목록

생성자는 필요에 따라 생성자 본문을 실행 하기 전에 클래스 멤버를 초기화 하는 멤버 이니셜라이저 목록을 포함할 수 있습니다. 멤버 이니셜라이저 목록은 [std:: initializer_list \<T> ](../standard-library/initializer-list-class.md)형식의 *이니셜라이저 목록과* 동일 하지 않습니다.

멤버 이니셜라이저 목록 사용은 멤버를 직접 초기화 하기 때문에 생성자의 본문에 값을 할당 하는 것 보다 좋습니다. 다음 예제에서는 멤버 이니셜라이저 목록이 콜론 뒤의 모든 **식별자 (인수)** 식으로 구성 된 것을 보여 줍니다.

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

식별자는 클래스 멤버를 참조 해야 합니다. 인수의 값을 사용 하 여 초기화 됩니다. 인수는 생성자 매개 변수, 함수 호출 또는 [std:: initializer_list \<T> ](../standard-library/initializer-list-class.md)중 하나일 수 있습니다.

**`const`** 멤버 및 참조 형식의 멤버는 멤버 이니셜라이저 목록에서 초기화 해야 합니다.

파생 생성자를 실행 하기 전에 기본 클래스가 완전히 초기화 되도록 하려면 매개 변수가 있는 기본 클래스 생성자를 호출 해야 합니다.

## <a name="default-constructors"></a><a name="default_constructors"></a> 기본 생성자

*기본 생성자* 에는 일반적으로 매개 변수가 없지만 기본값을 포함 하는 매개 변수를 사용할 수 있습니다.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

기본 생성자는 [특수 멤버 함수](special-member-functions.md)중 하나입니다. 클래스에 선언 된 생성자가 없는 경우 컴파일러는 암시적 기본 생성자를 제공 합니다 **`inline`** .

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

암시적 기본 생성자를 사용 하는 경우 앞의 예제와 같이 클래스 정의의 멤버를 초기화 해야 합니다. 이러한 이니셜라이저가 없으면 멤버가 초기화 되지 않고 Volume () 호출에서 가비지 값이 생성 됩니다. 일반적으로 암시적 기본 생성자를 사용할 수 없는 경우에도 이러한 방식으로 멤버를 초기화 하는 것이 좋습니다.

컴파일러가 암시적 기본 생성자를 [삭제](#explicitly_defaulted_and_deleted_constructors)된 것으로 정의 하 여 생성 하지 못하게 할 수 있습니다.

```cpp
    // Default constructor
    Box() = delete;
```

컴파일러에서 생성 된 기본 생성자는 모든 클래스 멤버가 기본 생성 가능이 아닌 경우 삭제 된 것으로 정의 됩니다. 예를 들어, 클래스 형식의 모든 멤버와 해당 클래스 형식 멤버에는 액세스할 수 있는 기본 생성자와 소멸자가 있어야 합니다. 참조 형식의 모든 데이터 멤버 및 **`const`** 멤버에는 기본 멤버 이니셜라이저가 있어야 합니다.

컴파일러에서 생성 된 기본 생성자를 호출 하 고 괄호를 사용 하려고 하면 경고가 발생 합니다.

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

이는 가장 까다로운 구문 분석 문제의 한 예입니다. 예제 식을 함수 선언 또는 기본 생성자 호출로 해석할 수 있고 C++ 파서에서는 선언을 다른 항목보다 우선하므로 식이 함수 선언으로 처리됩니다. 자세한 내용은 [가장 Vexing 구문 분석](https://en.wikipedia.org/wiki/Most_vexing_parse)을 참조 하세요.

기본값이 아닌 생성자가 선언된 경우 컴파일러는 기본 생성자를 제공하지 않습니다.

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

클래스에 기본 생성자가 없는 경우 대괄호 구문만 사용하여 해당 클래스의 개체 배열을 생성할 수 없습니다. 예를 들어 이전 코드 블록에서 다음과 같이 상자 배열을 선언할 수 없습니다.

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

그러나 이니셜라이저 목록 집합을 사용 하 여 Box 개체의 배열을 초기화할 수 있습니다.

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

자세한 내용은 [이니셜라이저](initializers.md)를 참조 하십시오.

## <a name="copy-constructors"></a><a name="copy_and_move_constructors"></a> 복사 생성자

*복사 생성자* 는 동일한 형식의 개체에서 멤버 값을 복사 하 여 개체를 초기화 합니다. 클래스 멤버가 스칼라 값과 같은 모든 단순 형식인 경우에는 컴파일러에서 생성 된 복사 생성자로 충분 하며 사용자가 직접 정의 하지 않아도 됩니다. 클래스에 더 복잡 한 초기화가 필요한 경우 사용자 지정 복사 생성자를 구현 해야 합니다. 예를 들어 클래스 멤버가 포인터인 경우 새 메모리를 할당 하 고 다른의 가리킨 개체에서 값을 복사 하려면 복사 생성자를 정의 해야 합니다. 컴파일러에서 생성 된 복사 생성자는 새 포인터가 다른의 메모리 위치를 계속 가리키도록 포인터를 복사 하기만 합니다.

복사 생성자에는 다음 서명 중 하나가 있을 수 있습니다.

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

복사 생성자를 정의할 때 복사 할당 연산자 (=)도 정의 해야 합니다. 자세한 내용은 [할당](assignment.md) 및 [복사 생성자 및 복사 할당 연산자](copy-constructors-and-copy-assignment-operators-cpp.md)를 참조 하세요.

복사 생성자를 삭제 된 것으로 정의 하 여 개체가 복사 되는 것을 방지할 수 있습니다.

```cpp
    Box (const Box& other) = delete;
```

개체를 복사 하려고 하면 오류 *C2280: 삭제 된 함수를 참조*하려고 합니다.

## <a name="move-constructors"></a><a name="move_constructors"></a> 이동 생성자

*이동 생성자* 는 원래 데이터를 복사 하지 않고 기존 개체의 데이터 소유권을 새 변수로 이동 하는 특수 멤버 함수입니다. 첫 번째 매개 변수로 rvalue 참조를 사용 하 고 추가 매개 변수에는 기본값이 있어야 합니다. 이동 생성자는 큰 개체를 전달할 때 프로그램의 효율성을 크게 향상 시킬 수 있습니다.

```cpp
Box(Box&& other);
```

소멸 되려고 하는 동일한 형식의 다른 개체에서 개체를 초기화 하 고 더 이상 해당 리소스를 필요로 하지 않는 특정 상황에서 컴파일러는 이동 생성자를 선택 합니다. 다음 예제에서는 오버 로드 확인으로 이동 생성자를 선택 하는 경우 한 가지 사례를 보여 줍니다. 을 호출 하는 생성자에서 `get_Box()` 반환 된 값은 *xvalue 값* (만료 값)입니다. 이는 변수에 할당 되지 않으므로 범위를 벗어나는 것입니다. 이 예제에 대 한 동기를 제공 하기 위해 콘텐츠를 나타내는 문자열의 많은 벡터를 제공 해 보겠습니다. 벡터와 해당 문자열을 복사 하는 대신 이동 생성자가 만료 값 "box"에서이를 "도용" 하 여 이제 벡터가 새 개체에 속하도록 합니다. `std::move` `vector` 및 클래스는 모두 자체 이동 생성자를 구현 하기 때문에에 대 한 호출이 모두 필요 합니다 `string` .

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Print_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Print_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

클래스가 이동 생성자를 정의 하지 않는 경우 사용자가 선언 된 복사 생성자, 복사 할당 연산자, 이동 할당 연산자 또는 소멸자가 없으면 컴파일러가 암시적 항목을 생성 합니다. 명시적 또는 암시적 이동 생성자가 정의 되지 않은 경우 이동 생성자를 사용 하는 작업은 복사 생성자를 대신 사용 합니다. 클래스가 이동 생성자 또는 이동 할당 연산자를 선언 하는 경우 암시적으로 선언 된 복사 생성자가 삭제 된 것으로 정의 됩니다.

암시적으로 선언 된 이동 생성자는 클래스 형식인 멤버가 소멸자를 누락 하거나 컴파일러가 이동 작업에 사용할 생성자를 결정할 수 없는 경우 삭제 된 것으로 정의 됩니다.

Trivial 이동 생성자를 작성 하는 방법에 대 한 자세한 내용은 [이동 생성자 및 이동 할당 연산자 (c + +)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)를 참조 하세요.

## <a name="explicitly-defaulted-and-deleted-constructors"></a><a name="explicitly_defaulted_and_deleted_constructors"></a> 명시적으로 기본 설정 및 삭제 된 생성자

복사 생성자, 기본 생성자, 이동 생성자, 복사 할당 연산자, 이동 할당 연산자 및 소멸자를 명시적으로 *기본* 설정할 수 있습니다. 모든 특수 멤버 함수를 명시적으로 *삭제할* 수 있습니다.

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

자세한 내용은 [명시적으로 기본값으로 설정 및 삭제 된 함수](../cpp/explicitly-defaulted-and-deleted-functions.md)를 참조 하세요.

## <a name="constexpr-constructors"></a><a name="constexpr_constructors"></a> constexpr 생성자

생성자는 다음의 경우 [constexpr](constexpr-cpp.md) 로 선언할 수 있습니다.

- 이 클래스는 기본값으로 선언 되거나 일반적으로 [constexpr 함수의](constexpr-cpp.md#constexpr_functions) 모든 조건을 충족 합니다.
- 클래스에는 가상 기본 클래스가 없습니다.
- 각 매개 변수는 [리터럴 형식](trivial-standard-layout-and-pod-types.md#literal_types)입니다.
- 본문이 함수 try 블록이 아닙니다.
- 모든 비정적 데이터 멤버 및 기본 클래스 하위 개체가 초기화 됩니다.
- 클래스가 (a) 멤버를 포함 하는 공용 구조체 또는 (b)에 익명 공용 구조체가 있으면 union 멤버 중 하나만 초기화 됩니다.
- 클래스 형식의 모든 비정적 데이터 멤버와 모든 기본 클래스 하위 개체에는 constexpr 생성자가 있습니다.

## <a name="initializer-list-constructors"></a><a name="init_list_constructors"></a> 이니셜라이저 목록 생성자

생성자가 [std:: initializer_list \<T\> ](../standard-library/initializer-list-class.md) 를 매개 변수로 사용 하 고 다른 모든 매개 변수에 기본 인수가 있는 경우 직접 초기화를 통해 클래스를 인스턴스화할 때 오버 로드 확인에서 해당 생성자가 선택 됩니다. Initializer_list를 사용 하 여이를 수락할 수 있는 모든 멤버를 초기화할 수 있습니다. 예를 들어 Box 클래스 (이전에 표시 됨)에 멤버가 있다고 가정 합니다 `std::vector<string>` `m_contents` . 다음과 같이 생성자를 제공할 수 있습니다.

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

그런 다음 상자 개체를 다음과 같이 만듭니다.

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit-constructors"></a><a name="explicit_constructors"></a> 명시적 생성자

클래스에 단일 매개 변수를 사용하는 생성자가 있거나 하나를 제외한 모든 매개 변수에서 기본값을 사용하는 경우 이 매개 변수 형식은 클래스 형식으로 암시적으로 변환할 수 있습니다. 예를 들어 `Box` 클래스에 다음과 같은 생성자가 있는 경우입니다.

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

다음과 같이 Box를 초기화할 수 있습니다.

```cpp
Box b = 42;
```

또는 Box를 사용하는 함수에 int를 전달합니다.

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

경우에 따라 이러한 변환은 유용할 수 있지만 코드에서 미세하지만 심각한 오류를 발생시키는 경우가 더 자주 있습니다. 일반적으로 **`explicit`** 이러한 종류의 암시적 형식 변환을 방지 하려면 생성자 (및 사용자 정의 연산자)에서 키워드를 사용 해야 합니다.

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

생성자가 명시적인 경우 `ShippingOrder so(42, 10.8);` 줄에서 컴파일 오류가 발생합니다.  자세한 내용은 [사용자 정의 형식 변환](../cpp/user-defined-type-conversions-cpp.md)을 참조 하세요.

## <a name="order-of-construction"></a><a name="order_of_construction"></a> 생성 순서

생성자는 다음과 같은 순서로 작업을 수행합니다.

1. 생성자는 선언 순서대로 기본 클래스 및 멤버 생성자를 호출합니다.

1. 클래스가 가상 기본 클래스에서 파생된 경우 해당 클래스는 개체의 가상 기본 포인터를 초기화합니다.

1. 클래스가 가상 함수를 포함하거나 상속하는 경우 해당 클래스는 개체의 가상 함수 포인터를 초기화합니다. 가상 함수 포인터는 클래스의 가상 함수 테이블을 가리켜서 가상 함수 호출의 올바른 바인딩이 코딩되도록 합니다.

1. 이러한 포인터는 함수 본문의 모든 코드를 실행합니다.

다음 예제에서는 파생 클래스의 생성자에서 기본 클래스 및 멤버 생성자가 호출되는 순서를 보여 줍니다. 먼저 기본 생성자를 호출하고, 기본 클래스 멤버를 클래스 선언에 표시되는 순서대로 초기화한 다음 파생된 생성자를 호출합니다.

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

출력은 다음과 같습니다.

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

파생 클래스 생성자는 항상 기본 클래스 생성자를 호출하므로, 완전히 생성된 기본 클래스를 통해서만 다른 작업을 수행할 수 있습니다. 기본 클래스 생성자는 파생 순서에 의해 호출 됩니다. 예를 들어, `ClassA` 에서 파생 된가에서 파생 된 경우 `ClassB` `ClassC` `ClassC` 생성자가 먼저 호출 된 다음 생성자가 호출 됩니다 `ClassB` `ClassA` .

기본 클래스에 기본 생성자가 없는 경우 파생 클래스 생성자에 기본 클래스 생성자 매개 변수를 제공해야 합니다.

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

생성자가 예외를 throw하는 경우 소멸 순서는 생성의 역순입니다.

1. 생성자 함수 본문의 코드가 해제됩니다.

1. 기본 클래스 및 멤버 개체가 선언의 역순으로 제거됩니다.

1. 생성자가 비대리자인 경우 제대로 생성된 기본 클래스 개체 및 멤버가 모두 소멸됩니다. 하지만 개체가 완전히 생성되지 않으므로 소멸자는 실행되지 않습니다.

## <a name="derived-constructors-and-extended-aggregate-initialization"></a><a name="extended_aggregate"></a> 파생 된 생성자 및 확장 된 집계 초기화

기본 클래스의 생성자가 public이 아니지만 파생 된 클래스에서 액세스할 수 있는 경우 Visual Studio 2017 이상에서 **/hd: c + + 17** 모드 아래에 있는 빈 중괄호를 사용 하 여 파생 형식의 개체를 초기화할 수 없습니다.

다음 예제에서는 C++14 준수 동작을 보여 줍니다.

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

C++17에서 `Derived`는 이제 집계 형식으로 간주되므로 프라이빗 기본 생성자를 통한 `Base`의 초기화가 확장된 집계 초기화 규칙의 일부로 직접 발생합니다. 이전에는 `Base` 프라이빗 생성자가 `Derived` 생성자를 통해 호출되었으며, friend 선언 때문에 성공했습니다.

다음 예제에서는 **/std: c + + 17** 모드의 Visual Studio 2017 이상에서 c + + 17 동작을 보여 줍니다.

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>여러 상속이 있는 클래스의 생성자

클래스가 여러 기본 클래스에서 파생되는 경우 기본 클래스 생성자는 파생 클래스 선언에 나열된 순서대로 호출됩니다.

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

다음과 같이 출력됩니다.

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating-constructors"></a><a name="delegating_constructors"></a> 생성자 위임

*위임 생성자* 는 동일한 클래스의 다른 생성자를 호출 하 여 초기화 작업 중 일부를 수행 합니다. 이는 모두 유사한 작업을 수행 해야 하는 여러 생성자가 있는 경우에 유용 합니다. 한 생성자에서 기본 논리를 작성 하 고 다른 생성자에서 호출할 수 있습니다. 다음 trivial 예제에서 Box (int)는 해당 작업을 Box (int, int, int)로 위임 합니다.

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

생성자에 의해 만들어지는 개체는 생성자가 완료되는 즉시 완전하게 초기화됩니다. 자세한 내용은 [생성자 위임](../cpp/delegating-constructors.md)을 참조 하세요.

## <a name="inheriting-constructors-c11"></a><a name="inheriting_constructors"></a> 생성자 상속 (c + + 11)

파생 클래스는 다음 예제와 같이 선언을 사용 하 여 직접 기본 클래스에서 생성자를 상속할 수 있습니다 **`using`** .

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=vs-2017"

**Visual Studio 2017 이상**: **`using`** **/std: c + + 17** 모드의 문은 파생 클래스의 생성자와 동일한 시그니처가 있는 경우를 제외 하 고 기본 클래스의 모든 생성자 범위를 가져옵니다. 일반적으로 파생 클래스에서 새 데이터 멤버나 생성자를 선언하지 않는 경우 상속 생성자를 사용하는 것이 가장 좋습니다.

::: moniker-end

클래스 템플릿은 해당 형식이 기본 클래스를 지정하는 경우 형식 인수에서 모든 생성자를 상속할 수 있습니다.

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

파생 클래스는 다중 기본 클래스에 동일한 서명을 사용하는 생성자가 있는 경우 해당 다중 기본 클래스에서 상속할 수 없습니다.

## <a name="constructors-and-composite-classes"></a><a name="constructors_in_composite_classes"></a> 생성자 및 복합 클래스

클래스 형식 멤버를 포함 하는 클래스를 *복합 클래스*라고 합니다. 복합 클래스의 클래스 형식 멤버를 만들 때 생성자가 클래스의 자체 생성자보다 먼저 호출됩니다. 포함된 클래스에 기본 생성자가 없는 경우 복합 클래스의 생성자에서 초기화 목록을 사용해야 합니다. 이전 `StorageBox` 예제에서 `m_label` 멤버 변수의 형식을 새 `Label` 클래스로 변경할 경우 기본 클래스 생성자를 호출하고 `m_label` 생성자에서 `StorageBox` 변수를 초기화해야 합니다.

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>섹션 내용

- [복사 생성자 및 복사 할당 연산자](copy-constructors-and-copy-assignment-operators-cpp.md)
- [이동 생성자 및 이동 할당 연산자](move-constructors-and-move-assignment-operators-cpp.md)
- [위임 생성자](delegating-constructors.md)

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](classes-and-structs-cpp.md)
