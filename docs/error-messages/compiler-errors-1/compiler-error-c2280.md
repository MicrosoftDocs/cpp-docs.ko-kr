---
description: '자세한 정보: 컴파일러 오류 C2280'
title: 컴파일러 오류 C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: 74ed554006faa20046571971e080e0c0a2054b72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295057"
---
# <a name="compiler-error-c2280"></a>컴파일러 오류 C2280

'*선언*': 삭제 된 함수를 참조 하려고 합니다.

컴파일러가 함수를 참조 하려고 했습니다 `deleted` . 이 오류는 소스 코드에서로 명시적으로 표시 된 멤버 함수를 호출 하 여 발생할 수 있습니다 `= deleted` . 이 오류는 컴파일러에서 자동으로 선언 되 고 표시 되는 구조체 또는 클래스의 암시적 특수 멤버 함수를 호출 하는 경우에도 발생할 수 있습니다 `deleted` . 컴파일러가 또는 특수 멤버 함수를 자동으로 생성 하는 경우에 대 한 자세한 내용은 **`default`** `deleted` [특수 멤버 함수](../../cpp/special-member-functions.md)를 참조 하세요.

## <a name="example-explicitly-deleted-functions"></a>예: 명시적으로 삭제 된 함수

명시적 함수를 호출 하면 `deleted` 이 오류가 발생 합니다. 명시적 `deleted` 멤버 함수는 클래스 또는 구조체가 의도적으로 사용 되지 않도록 의도적으로 설계 되었음을 암시 하므로이 문제를 해결 하려면 코드를 변경 하 여이를 방지 해야 합니다.

```cpp
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```

## <a name="example-uninitialized-data-members"></a>예: 초기화 되지 않은 데이터 멤버

초기화 되지 않은 참조 형식 데이터 멤버 또는 **`const`** 데이터 멤버가 있으면 컴파일러가 기본 생성자를 암시적으로 선언 `deleted` 합니다. 이 문제를 해결 하려면 데이터 멤버가 선언 될 때 해당 멤버를 초기화 합니다.

```cpp
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```

## <a name="example-reference-and-const-data-members"></a>예: 참조 및 const 데이터 멤버

**`const`** 또는 참조 형식 데이터 멤버가 있으면 컴파일러가 `deleted` 복사 할당 연산자를 선언 합니다. 초기화 되 면 이러한 멤버를에 할당할 수 없으므로 단순 복사 또는 이동 작업을 수행할 수 없습니다. 이 문제를 해결 하려면 논리를 변경 하 여 오류를 발생 시키는 할당 작업을 제거 하는 것이 좋습니다.

```cpp
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```

## <a name="example-movable-deletes-implicit-copy"></a>예: 이동 가능한 삭제 암시적 복사

클래스가 이동 생성자 또는 이동 할당 연산자를 선언 하지만 복사 생성자를 명시적으로 선언 하지 않는 경우 컴파일러는 복사 생성자를 암시적으로 선언 하 고로 정의 `deleted` 합니다. 마찬가지로 클래스가 이동 생성자 또는 이동 할당 연산자를 선언 하지만 복사 할당 연산자를 명시적으로 선언 하지 않는 경우 컴파일러는 복사 할당 연산자를 암시적으로 선언 하 고로 정의 `deleted` 합니다. 이 문제를 해결 하려면 이러한 멤버를 명시적으로 선언 해야 합니다.

와의 연결에 C2280 오류가 표시 되 면 `unique_ptr` 해당 복사 생성자 (함수)를 호출 하려고 했기 때문입니다 `deleted` . 설계상은 복사할 수 `unique_ptr` 없습니다. 대신 이동 생성자를 사용 하 여 소유권을 양도 합니다.

```cpp
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base
{
public:
    base();
    ~base();
    base(base&&);
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};

void copy(base *p)
{
    base b{*p};  // C2280
}
```

## <a name="example-variant-and-volatile-members"></a>예: Variant 및 volatile 멤버

Visual Studio 2015 업데이트 2 이전의 컴파일러 버전은 익명 공용 구조체에 대 한 기본 생성자 및 소멸자를 준수 하지 않으며 생성 했습니다. 이제는로 암시적으로 선언 됩니다 `deleted` . 이러한 버전 **`default`** **`default`** 에는 멤버 변수가 있는 클래스와 구조체에서 복사 및 이동 생성자와 복사 및 이동 할당 연산자의 비호환 암시적 정의가 허용 됩니다 **`volatile`** . 이제 컴파일러는 이러한 생성자 및 대입 연산자를 포함 하지 않는 것으로 간주 하 고 구현을 생성 하지 않습니다 **`default`** . 이러한 클래스가 공용 구조체의 멤버 이거나 클래스 내의 익명 공용 구조체 인 경우에는 공용 구조체 또는 클래스의 복사 및 이동 생성자와 복사 및 이동 할당 연산자가 암시적으로로 정의 됩니다 `deleted` . 이 문제를 해결 하려면 필요한 특수 멤버 함수를 명시적으로 선언 해야 합니다.

```cpp
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {
    A() = default;
    A(const A&);
};

struct B {
    union {
        A a;
        int i;
    };
    // To fix this issue, declare the required
    // special member functions:
    // B();
    // B(const B& b);
};

int main() {
    B b1;
    B b2(b1);  // C2280
}
```

## <a name="example-indirect-base-members-deleted"></a>예: 간접 기본 멤버가 삭제 됨

Visual Studio 2015 업데이트 2 이전의 컴파일러 버전은 비준수 이며 파생 클래스에서 간접적으로 파생 된 기본 클래스의 특수 멤버 함수를 호출 하는 것을 허용 했습니다 `private virtual` . 이제 컴파일러는 이러한 호출이 수행 될 때 컴파일러 오류 C2280를 발생 시킵니다.

이 예제에서 클래스는 `top` 전용 가상에서 간접적으로 파생 `base` 됩니다. 준수 하는 코드에서이를 통해의 멤버를 `base` 에 액세스할 수 없게 됩니다. `top` 형식의 개체는 `top` 기본으로 생성 되거나 삭제 될 수 없습니다. 이전 컴파일러 동작에 의존 하는 코드에서이 문제를 해결 하려면 파생을 사용 하도록 중간 클래스를 변경 `protected virtual` 하거나 `top` 직접 파생을 사용 하도록 클래스를 변경 합니다.

```cpp
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base
{
protected:
    base();
    ~base();
};

class middle : private virtual base {};
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};

void destroy(top *p)
{
    delete p;  // C2280
}
```
