---
description: '자세한 정보: 멤버 Access Control (c + +)'
title: 멤버 액세스 제어(C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: 2cce7cb98e76098f3c20a6c2404f91ccf40db1cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206879"
---
# <a name="member-access-control-c"></a>멤버 액세스 제어(C++)

액세스 제어를 사용 하 여 클래스의 [공용](../cpp/public-cpp.md) 인터페이스를 [개인](../cpp/private-cpp.md) 구현 세부 정보 및 파생 클래스 에서만 사용 되는 [보호](../cpp/protected-cpp.md) 된 멤버와 분리할 수 있습니다. 액세스 지정자는 다음 액세스 지정자가 나타날 때까지 해당 액세스 지정자 뒤에 선언된 모든 멤버에 적용됩니다.

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

기본 액세스는 **`private`** 클래스, **`public`** 구조체 또는 공용 구조체에 있습니다. 클래스의 액세스 지정자는 순서에 관계없이 여러 번 사용할 수 있습니다. 클래스 형식 개체의 스토리지 할당은 구현에 따라 다르지만 액세스 지정자 사이의 더 높은 메모리 주소가 연속적으로 멤버에 할당됩니다.

## <a name="member-access-control"></a>멤버 Access Control

|액세스 형식|의미|
|--------------------|-------------|
|[private](../cpp/private-cpp.md)|로 선언 된 클래스 멤버 **`private`** 는 클래스의 멤버 함수 및 friend (클래스 또는 함수) 에서만 사용할 수 있습니다.|
|[protected](../cpp/protected-cpp.md)|로 선언 된 클래스 멤버 **`protected`** 는 클래스의 멤버 함수 및 friend (클래스 또는 함수)에서 사용할 수 있습니다. 또한 클래스에서 파생 클래스에서 사용할 수 있습니다.|
|[public](../cpp/public-cpp.md)|로 선언 된 클래스 멤버 **`public`** 는 모든 함수에서 사용할 수 있습니다.|

액세스 제어는 의도하지 않은 방식으로 개체를 사용하는 것을 방지하는 데 도움이 됩니다. 이러한 보호는 명시적 형식 변환(캐스트)을 수행할 때 손실됩니다.

> [!NOTE]
> 액세스 제어는 모든 이름(멤버 함수, 멤버 데이터, 중첩 클래스 및 열거자)에 동일하게 적용 가능합니다.

## <a name="access-control-in-derived-classes"></a>파생 클래스의 Access Control

파생 클래스에서 액세스할 수 있는 기본 클래스의 멤버는 두 가지 요인으로 인해 결정됩니다. 이와 동일한 요인이 파생 클래스의 상속된 멤버에 대한 액세스도 결정합니다.

- 파생 클래스가 액세스 지정자를 사용 하 여 기본 클래스를 선언 하는지 여부 **`public`** 입니다.

- 기본 클래스의 멤버 액세스

다음 표에서는 이러한 요인과 기본 클래스 멤버 액세스를 확인하는 방법 간의 상호 작용을 보여 줍니다.

### <a name="member-access-in-base-class"></a>기본 클래스의 멤버 액세스

|private|protected|공용|
|-------------|---------------|------------|
|파생 액세스에 관계없이 항상 액세스할 수 없음|전용 파생을 사용하는 경우 파생 클래스에서 전용|전용 파생을 사용하는 경우 파생 클래스에서 전용|
||보호된 파생을 사용하는 경우 파생 클래스에서 보호됨|보호된 파생을 사용하는 경우 파생 클래스에서 보호됨|
||공용 파생을 사용하는 경우 파생 클래스에서 보호됨|공용 파생을 사용하는 경우 파생 클래스에서 공용|

다음 예제에서는 이에 대해 설명합니다.

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

`DerivedClass1`에서는 `PublicFunc`가 공용 기본 클래스이므로 멤버 함수 `ProtectedFunc`가 공용 멤버이고 `BaseClass`가 보호된 멤버입니다. `PrivateFunc`는 `BaseClass` 전용이며 모든 파생 클래스에서 액세스할 수 없습니다.

`DerivedClass2`에서는 `PublicFunc`가 전용 기본 클래스이므로 `ProtectedFunc` 및 `BaseClass` 함수가 전용 멤버로 간주됩니다. 여기서도 `PrivateFunc`는 `BaseClass` 전용이며 모든 파생 클래스에서 액세스할 수 없습니다.

파생 클래스는 기본 클래스 액세스 지정자 없이 선언할 수 있습니다. 이 경우 파생 클래스 선언에서 키워드를 사용 하는 경우 파생은 개인으로 간주 됩니다 **`class`** . 파생 클래스 선언에서 키워드를 사용 하는 경우 파생은 공용으로 간주 됩니다 **`struct`** . 예를 들어, 다음 코드는

```cpp
class Derived : Base
...
```

이는 다음과 동등합니다.

```cpp
class Derived : private Base
...
```

마찬가지로, 다음 코드는

```cpp
struct Derived : Base
...
```

이는 다음과 동등합니다.

```cpp
struct Derived : public Base
...
```

전용 액세스 권한으로 선언 된 멤버는 **`friend`** 기본 클래스의 선언을 사용 하 여 해당 함수나 클래스를 선언 하지 않는 한 함수 또는 파생 클래스에서 액세스할 수 없습니다.

형식에는 **`union`** 기본 클래스를 사용할 수 없습니다.

> [!NOTE]
> Private 기본 클래스를 지정 하는 경우 **`private`** 파생 클래스의 사용자가 멤버 액세스를 이해 하도록 키워드를 명시적으로 사용 하는 것이 좋습니다.

## <a name="access-control-and-static-members"></a>액세스 제어 및 정적 멤버

기본 클래스를로 지정 하면 **`private`** 비정적 멤버에만 영향을 줍니다. 파생 클래스에서 계속 공용 정적 멤버에 액세스할 수 있습니다. 그러나 포인터, 참조 또는 개체를 사용하여 기본 클래스의 멤버에 액세스하는 경우 액세스 제어가 다시 적용되는 시간에 변환이 필요할 수 있습니다. 다음 예제를 참조하세요.

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

위 코드에서는 액세스 제어가 `Derived2`에 대한 포인터를 `Base`에 대한 포인터로 변환하지 못하도록 합니다. **`this`** 포인터는 암시적으로 형식입니다 `Derived2 *` . 함수를 선택 하려면 `CountOf` 를 **`this`** 형식으로 변환 해야 합니다 `Base *` . `Base`가 `Derived2`에 대한 전용 간접 기본 클래스이므로 이러한 변환이 허용되지 않습니다. 직접 파생 클래스에 대한 포인터에 대해서만 전용 기본 클래스 형식으로 변환할 수 있습니다. 따라서 `Derived1 *`형식의 포인터를 `Base *` 형식으로 변환할 수 있습니다.

선택하기 위한 포인터, 참조 또는 개체를 사용하지 않고 `CountOf` 함수를 명시적으로 호출하면 변환이 수행되지 않습니다. 따라서 호출이 허용됩니다.

파생 클래스인 `T`의 멤버 및 friend는 `T`에 대한 포인터를 `T`의 전용 직접 기본 클래스에 대한 포인터로 변환할 수 있습니다.

## <a name="access-to-virtual-functions"></a>가상 함수에 대한 액세스

[가상](../cpp/virtual-cpp.md) 함수에 적용 되는 액세스 제어는 함수 호출을 수행 하는 데 사용 되는 형식에 따라 결정 됩니다. 함수의 선언 재정의는 지정된 형식에 대한 액세스 제어에 영향을 주지 않습니다. 예를 들어:

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

앞의 예제에서 `GetState` 형식에 대한 포인터를 사용하여 `VFuncBase` 가상 함수를 호출하면 `VFuncDerived::GetState`가 호출되며, `GetState`는 public으로 취급됩니다. 그러나 `GetState`가 `VFuncDerived` 클래스에서 private로 선언되기 때문에 `GetState` 형식에 대한 포인터를 사용하여 `VFuncDerived`를 호출하는 것은 액세스 제어 위반이 됩니다.

> [!CAUTION]
> 가상 함수 `GetState`는 기본 클래스 `VFuncBase`에 대한 포인터를 사용하여 호출할 수 있습니다. 이는 호출된 함수가 해당 함수의 기본 클래스 버전임을 의미하지는 않습니다.

## <a name="access-control-with-multiple-inheritance"></a>다중 상속으로 액세스 제어

가상 기본 클래스를 사용하는 다중 상속 격자의 경우 지정된 이름은 둘 이상의 경로를 통해 도달할 수 있습니다. 이렇게 다양한 경로에는 다양한 액세스 제어가 적용될 수 있기 때문에 컴파일러는 최적의 액세스를 제공하는 경로를 선택합니다. 다음 그림을 참조하세요.

![상속 그래프의 경로를 따라 액세스](../cpp/media/vc38v91.gif "상속 그래프의 경로를 따라 액세스") <br/>
상속 그래프의 경로를 따라 액세스

그림에서 클래스 `VBase`에 선언된 이름은 언제나 클래스 `RightPath`를 통해 도달됩니다. `RightPath`는 `VBase`를 공용 기본 클래스로 선언하지만, `LeftPath`는 `VBase`를 비공개로 선언합니다. 따라서, 오른쪽 경로를 보다 쉽게 액세스할 수 있습니다.

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)
