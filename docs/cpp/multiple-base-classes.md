---
description: '자세히 알아보기: 여러 기본 클래스'
title: 다중 기본 클래스
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: 6e9e839e5906fba4a45e4e2edd4965817816a298
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314102"
---
# <a name="multiple-base-classes"></a>다중 기본 클래스

클래스는 둘 이상의 기본 클래스에서 파생 될 수 있습니다. 클래스가 둘 이상의 기본 클래스에서 파생 되는 다중 상속 모델에서 기본 클래스는 *기본 목록* 문법 요소를 사용 하 여 지정 됩니다. 예를 들어 `CollectionOfBook` 및 `Collection`에서 파생된 `Book`에 대한 클래스 선언을 지정할 수 있습니다.

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

생성자와 소멸자가 호출되는 특정 경우를 제외하고 기본 클래스가 지정되는 순서는 중요하지 않습니다. 이러한 경우 기본 클래스가 지정되는 순서는 다음에 영향을 줍니다.

- 생성자에 의한 초기화가 진행되는 순서입니다. 코드가 `Book`의 `CollectionOfBook` 부분을 의존하여 `Collection` 파트 전에 초기화되는 경우 사양의 순서는 중요합니다. 초기화는 *기본 목록* 에 클래스를 지정 하는 순서 대로 발생 합니다.

- 정리하기 위해 소멸자를 호출하는 순서입니다. 다른 부품이 소멸될 때 클래스의 특정 "부품"이 있어야 하는 경우 순서가 중요합니다. 소멸자는 *기본 목록* 에 지정 된 클래스의 반대 순서로 호출 됩니다.

    > [!NOTE]
    >  기본 클래스의 사양 순서는 클래스의 메모리 레이아웃에 영향을 줍니다. 메모리에 있는 기본 멤버의 순서에 따라 모든 프로그래밍 의사를 결정하지 마십시오.

*기본 목록을* 지정할 때 동일한 클래스 이름을 두 번 이상 지정할 수 없습니다. 그러나 클래스는 간접 기본 클래스가 되거나 두 번 이상 파생 클래스가 될 수 있습니다.

## <a name="virtual-base-classes"></a>가상 기본 클래스

클래스는 한 번 이상 파생 클래스에 대한 간접 기본 클래스일 수 있으므로 C++는 이런 기본 클래스가 작동하는 방식을 최적화하는 방법을 제공합니다. 가상 기본 클래스는 다수의 형식 상속을 사용하는 클래스 계층에 모호성이 발생하지 않도록 공간을 절약하는 방법을 제공합니다.

각 비가상 개체에는 기본 클래스에 정의된 데이터 멤버의 복사본이 있습니다. 이 복제는 공간을 낭비하고 기본 클래스 멤버에 액세스할 때마다 기본 클래스 멤버의 어떤 사본을 원하는지 지정할 것을 요구합니다.

기본 클래스를 가상 기본으로 지정하면, 데이터 멤버가 중복되지 않으면서 한 번 이상 간접 기본으로 작동할 수 있습니다. 해당 데이터 멤버의 단일 복사본은 해당 복사본을 가상 기본 클래스로 사용하는 모든 기본 클래스에서 공유합니다.

가상 기본 클래스를 선언할 때 키워드는 **`virtual`** 파생 클래스의 기본 목록에 나타납니다.

다음 그림에서 시뮬레이션된 런치 라인을 설명하는 클래스 계층 구조를 살펴보십시오.

![시뮬레이션된 lunch line 그래프](../cpp/media/vc38xp1.gif "시뮬레이션된 lunch line 그래프") <br/>
시뮬레이션 된 점심 선 그래프

그림에서 `Queue`는 `CashierQueue` 및 `LunchQueue`에 대한 기본 클래스입니다. 하지만 두 클래스가 결합되어 `LunchCashierQueue`를 형성할 경우 새 클래스에 형식이 `Queue`인 두 하위 개체가 포함되는데 하나는 `CashierQueue`의 하위 개체이고 하나는 `LunchQueue`의 하위 개체인 문제가 발생할 수 있습니다. 다음 그림에서는 개념적 메모리 레이아웃을 보여 줍니다.(실제 메모리 레이아웃은 최적화될 수도 있습니다.)

![Line 개체&#45;시뮬레이션 된 점심 식사](../cpp/media/vc38xp2.gif "Line 개체&#45;시뮬레이션 된 점심 식사") <br/>
시뮬레이션된 Lunch-Line 개체

`Queue` 개체에 두 개의 `LunchCashierQueue` 하위 개체가 있습니다. 다음 코드에서는 `Queue`를 가상 기본 클래스로 선언합니다.

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

**`virtual`** 키워드를 사용 하면 하위 개체의 복사본 하나만 `Queue` 포함 됩니다 (다음 그림 참조).

![줄 개체, 가상 기본 클래스를&#45;시뮬레이션 된 점심](../cpp/media/vc38xp3.gif "줄 개체, 가상 기본 클래스를&#45;시뮬레이션 된 점심") <br/>
가상 기본 클래스를 사용 하는 시뮬레이션 된 점심 선 개체

클래스에는 주어진 형식의 가상 구성 요소와 비가상 구성 요소가 둘 다 있을 수 있습니다. 이는 다음 그림에서 설명하는 조건에서 발생합니다.

![클래스의 가상 및 비&#45;가상 구성 요소](../cpp/media/vc38xp4.gif "클래스의 가상 및 비&#45;가상 구성 요소") <br/>
동일한 클래스의 가상 및 비가상 구성 요소

그림에서 `CashierQueue` 및 `LunchQueue`는 `Queue`를 가상 기본 클래스로 사용합니다. 하지만 `TakeoutQueue`는 `Queue`를 가상 기본 클래스가 아니라 기본 클래스로 지정합니다. 따라서, `LunchTakeoutCashierQueue`는 형식이 `Queue`인 두 개의 하위 개체를 가지는데, 하나는 `LunchCashierQueue`를 포함하는 상속 경로의 하위 개체이고 하나는 `TakeoutQueue`를 포함하는 경로의 하위 개체입니다. 이는 다음 그림에 설명되어 있습니다.

![개체 레이아웃의 가상 &&#45;비가상 가상 상속](../cpp/media/vc38xp5.gif "개체 레이아웃의 가상 &&#45;비가상 가상 상속") <br/>
가상 상속과 비가상 상속을 사용 하는 개체 레이아웃

> [!NOTE]
> 가상 상속은 비가상 상속과 비교했을 때 상당한 크기의 혜택을 제공하지만, 추가 처리 오버헤드가 발생할 수 있습니다.

파생된 클래스가 가상 기본 클래스에서 상속된 가상 함수를 재정의하고 파생된 기본 클래스의 생성자 또는 소멸자가 가상 기본 클래스에 대한 포인터를 사용하여 해당 함수를 호출하는 경우, 컴파일러는 추가로 숨겨진 "vtordisp" 필드를 가상 기본 클래스에 사용할 수 있습니다. `/vd0`컴파일러 옵션은 숨겨진 vtordisp 생성자/소멸자 치환 멤버를 추가 하지 않도록 합니다. `/vd1`기본적으로 컴파일러 옵션을 사용 하면 필요에 따라이 옵션을 사용할 수 있습니다. 모든 클래스 생성자와 소멸자가 실제로 가상 함수를 호출한다고 확신하는 경우에만 vtordisps를 해제합니다.

`/vd`컴파일러 옵션은 전체 컴파일 모듈에 영향을 줍니다. Pragma를 사용 하 여 클래스 `vtordisp` 별로 필드를 표시 하지 않고 다시 활성화 합니다 `vtordisp` .

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>이름 모호성

다중 상속이 발생하면 2개 이상의 경로에서 이름이 상속될 가능성이 있습니다. 이 경로의 클래스 멤버 이름은 반드시 고유하지는 않습니다. 이러한 이름 충돌을 "모호성"이라고 합니다.

클래스 멤버를 참조하는 식은 모호하지 않은 참조를 만들어야 합니다. 다음 예제에서는 모호성이 전개되는 방법을 보여 줍니다.

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

위의 클래스 선언에서 `b`가 `b`를 `A`에서 참조하는지 또는 `B`에서 참조하는지 분명하지 않으므로 다음 코드가 모호합니다.

```cpp
C *pc = new C;

pc->b();
```

위의 예제를 살펴 보십시오. `a` 이름은 `A` 클래스와 `B` 클래스 모두의 멤버이므로 컴파일러는 호출할 함수를 지정하는 `a`를 확인할 수 없습니다. 함수, 개체, 형식 또는 열거자를 2개 이상 참조할 수 있는 경우 멤버에 대한 액세스가 모호합니다.

컴파일러는 다음 순서대로 테스트하여 모호성을 검색합니다.

1. 앞에서 설명한 대로 이름에 대한 액세스가 모호할 경우 오류 메시지가 생성됩니다.

1. 오버로드된 함수가 명확해지면 해결됩니다.

1. 이름에 대한 액세스가 멤버 액세스 권한을 위반하는 경우 오류 메시지가 생성됩니다. 자세한 내용은 [멤버 Access Control](../cpp/member-access-control-cpp.md)를 참조 하세요.

상속을 통해 식에 모호성이 생기면 클래스 이름으로 문제의 이름을 정규화하여 수동으로 해결할 수 있습니다. 모호성이 발생하지 않도록 앞의 예제를 적절하게 컴파일하려면 다음 코드를 사용하십시오.

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
> `C`가 선언되면 `B`가 `C`의 범위에서 참조될 경우 오류가 발생할 수 있습니다. 그러나 `B`의 범위에 실제로 `C`의 정규화되지 않은 참조가 생길 때까지는 오류가 발생하지 않습니다.

### <a name="dominance"></a>우위

둘 이상의 이름(함수, 개체 또는 열거자)을 상속 그래프를 통해 도달할 수 있습니다. 이러한 경우는 비가상 기본 클래스에서 모호한 것으로 간주됩니다. 이름 중 하나가 다른 이름보다 "우위를 차지하지" 않는 한 가상 기본 클래스에서도 모호합니다.

이름은 두 클래스에 정의되어 있고 한 클래스가 다른 클래스에서 파생된 경우 다른 이름보다 우위를 차지합니다. 우위를 차지하는 이름은 파생 클래스에 있는 이름입니다. 이 이름은 모호성이 다른 방식으로 발생하지 않은 경우 다음 예제와 같이 사용됩니다.

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>모호한 변환

포인터 또는 참조 형식에서 클래스 형식으로 명시적 및 암시적으로 변환하면 모호성이 발생할 수 있습니다. 아래에 나와 있는 포인터에서 기본 클래스로의 모호한 변환 그림에서는 다음을 보여 줍니다.

- `D` 형식 개체의 선언

- 해당 개체에 연산자 주소 ()를 적용 한 결과입니다 **&** . 주소 연산자는 항상 개체의 기준 주소를 제공합니다.

- 주소 연산자를 사용하여 얻은 포인터를 기본 클래스 형식 `A`로 명시적으로 변환하는 경우의 효과. 개체의 주소를 `A*` 형식으로 강제 변환하면 선택할 `A` 형식의 하위 개체에 대한 충분한 정보가 컴파일러에 제공되지 않는 경우도 있습니다. 이 경우에는 두 하위 개체가 존재합니다.

![포인터에서 기본 클래스로의 모호한 변환](../cpp/media/vc38xt1.gif "포인터에서 기본 클래스로의 모호한 변환") <br/>
포인터에서 기본 클래스로의 모호한 변환

`A*` 형식의 하위 개체 중 올바른 것을 구별할 수 없기 때문에 `A`(`A`에 대한 포인터) 형식으로의 변환은 모호합니다. 다음과 같이 사용하려는 하위 개체를 명시적으로 지정하여 모호성을 방지할 수 있습니다.

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>모호성 및 가상 기본 클래스

가상 기본 클래스를 사용하는 경우 다중 상속 경로를 통해 함수, 개체, 형식 및 열거자에 도달할 수 있습니다. 기본 클래스의 인스턴스는 하나 밖에 없기 때문에 이러한 이름에 액세스할 때 모호성이 없습니다.

다음 그림에서는 가상 및 비가상 상속을 사용하여 개체를 구성하는 방법을 보여 줍니다.

![가상 파생 및 비&#45;가상 파생](../cpp/media/vc38xr1.gif "가상 파생 및 비&#45;가상 파생") <br/>
가상 파생 및 비가상 파생

이 그림에서 비가상 기본 클래스를 통해 `A` 클래스의 임의 멤버에 액세스하면 모호성이 발생합니다. 컴파일러는 `B`에 연결된 하위 개체를 사용할지, 아니면 `C`에 연결된 하위 개체를 사용할지를 설명하는 정보를 가지고 있지 않습니다. 그러나 `A`를 가상 기본 클래스로 지정하면 어느 하위 개체에 액세스할지가 분명해집니다.

## <a name="see-also"></a>추가 정보

[상속](../cpp/inheritance-cpp.md)
