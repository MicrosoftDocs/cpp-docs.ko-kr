---
title: '범위 확인 연산자: `::`'
description: 표준 c + +에서 범위 확인 연산자가 작동 하는 방식에 대해 알아봅니다 `::` .
ms.date: 12/06/2020
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.openlocfilehash: ff774d9fcca9f68cb2925af82c55ef438ab4d71a
ms.sourcegitcommit: 7b131db4ed39bddb4a456ebea402f47c5cbd69d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96776533"
---
# <a name="scope-resolution-operator-"></a>범위 확인 연산자: `::`

범위 확인 연산자는 **`::`** 서로 다른 범위에서 사용 되는 식별자를 식별 하 고 구분 하는 데 사용 됩니다. 범위에 대 한 자세한 내용은 [범위](../cpp/scope-visual-cpp.md)를 참조 하세요.

## <a name="syntax"></a>구문

> *`qualified-id`*:\
> &emsp; *`nested-name-specifier`* **`template`** <sub>opt</sub> *`unqualified-id`*

> *`nested-name-specifier`*:\
> &emsp;**`::`**\
> &emsp;*`type-name`* **`::`**\
> &emsp;*`namespace-name`* **`::`**\
> &emsp;*`decltype-specifier`* **`::`**\
> &emsp;*`nested-name-specifier`* *`identifier`* **`::`**\
> &emsp;*`nested-name-specifier`***`template`** <sub>opt</sub> opt *`simple-template-id`***`::`**

> *`unqualified-id`*:\
> &emsp;*`identifier`*\
> &emsp;*`operator-function-id`*\
> &emsp;*`conversion-function-id`*\
> &emsp;*`literal-operator-id`*\
> &emsp;**`~`** *`type-name`*\
> &emsp;**`~`** *`decltype-specifier`*\
> &emsp;*`template-id`*

## <a name="remarks"></a>설명

`identifier`에는 변수, 함수 또는 열거형 값이 해당됩니다.

## <a name="use--for-classes-and-namespaces"></a>`::`클래스 및 네임 스페이스에 사용

다음 예제에서는 범위 확인 연산자가 네임스페이스 및 클래스에 사용되는 방법을 보여줍니다.

```cpp
namespace NamespaceA{
    int x;
    class ClassA {
    public:
        int x;
    };
}

int main() {

    // A namespace name used to disambiguate
    NamespaceA::x = 1;

    // A class name used to disambiguate
    NamespaceA::ClassA a1;
    a1.x = 2;
}
```

범위 한정자가 없는 범위 확인 연산자는 전역 네임스페이스를 참조합니다.

```cpp
namespace NamespaceA{
    int x;
}

int x;

int main() {
    int x;

    // the x in main()
    x = 0;
    // The x in the global namespace
    ::x = 1;

    // The x in the A namespace
    NamespaceA::x = 2;
}
```

범위 확인 연산자를 사용 하 여의 멤버를 식별 **`namespace`** 하거나 지시문에서 멤버의 네임 스페이스를 지명 하는 네임 스페이스를 식별할 수 있습니다 **`using`** . 아래 예제에서는가 `NamespaceC` 지시문에 의해에서 표시 되었으므로를 사용 하 여 `ClassB` `ClassB` 네임 스페이스에서가 선언 된 경우에도를 한정할 `NamespaceB` `NamespaceB` 수 있습니다 `NamespaceC` **`using`** .

```cpp
namespace NamespaceB {
    class ClassB {
    public:
        int x;
    };
}

namespace NamespaceC{
    using namespace NamespaceB;
}

int main() {
    NamespaceB::ClassB b_b;
    NamespaceC::ClassB c_b;

    b_b.x = 3;
    c_b.x = 4;
}
```

범위 확인 연산자를 연쇄적으로 사용할 수 있습니다. 다음 예제에서 `NamespaceD::NamespaceD1`은 중첩된 네임스페이스 `NamespaceD1`을 식별하고 `NamespaceE::ClassE::ClassE1`은 중첩된 클래스 `ClassE1`을 식별합니다.

```cpp
namespace NamespaceD{
    namespace NamespaceD1{
        int x;
    }
}

namespace NamespaceE{
    class ClassE{
    public:
        class ClassE1{
        public:
            int x;
        };
    };
}

int main() {
    NamespaceD:: NamespaceD1::x = 6;
    NamespaceE::ClassE::ClassE1 e1;
    e1.x = 7  ;
}
```

## <a name="use--for-static-members"></a>`::`정적 멤버에 사용

클래스의 정적 멤버를 호출하려면 범위 확인 연산자를 사용해야 합니다.

```cpp
class ClassG {
public:
    static int get_x() { return x;}
    static int x;
};

int ClassG::x = 6;

int main() {

    int gx1 = ClassG::x;
    int gx2 = ClassG::get_x();
}
```

## <a name="use--for-scoped-enumerations"></a>범위가 지정 된 `::` 열거형에 사용

범위가 지정 된 확인 연산자는 다음 예제와 같이 범위가 지정 된 열거형 [열거형](../cpp/enumerations-cpp.md)의 값에도 사용 됩니다.

```cpp
enum class EnumA{
    First,
    Second,
    Third
};

int main() {
    EnumA enum_value = EnumA::First;
}
```

## <a name="see-also"></a>참고 항목

[C + + 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[네임스페이스](../cpp/namespaces-cpp.md)
