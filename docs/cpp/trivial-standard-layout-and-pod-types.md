---
description: 간단한 정보, 표준 레이아웃, POD 및 리터럴 형식에 대해 자세히 알아보세요.
title: Trivial, 표준 레이아웃, POD 및 리터럴 형식
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: cfd9a9406c62f8c338d2c54587b61ad0c7b87ecc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186470"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Trivial, 표준 레이아웃, POD 및 리터럴 형식

용어 *레이아웃* 은 클래스, 구조체 또는 공용 형식의 개체 멤버가 메모리에 정렬되는 방식을 가리킵니다. 경우에 따라 레이아웃은 언어 사양에 따라 잘 정의됩니다. 그러나 클래스 또는 구조체에 가상 기본 클래스, 가상 함수, 액세스 제어가 다른 멤버와 같은 특정 C++ 언어 기능이 포함되어 있는 경우, 컴파일러는 레이아웃을 자유롭게 선택할 수 있습니다. 해당 레이아웃은 수행되는 최적화에 따라 달라질 수 있으며, 대부분의 경우 개체가 인접한 메모리의 영역을 차지하지 못할 수도 있습니다. 예를 들어 클래스에 가상 함수가 있는 경우 해당 클래스의 모든 인스턴스는 단일 가상 함수 테이블을 공유할 수 있습니다. 이러한 형식은 매우 유용하지만 제한 사항도 있습니다. 레이아웃이 정의되지 않았기 때문에 C와 같은 다른 언어로 작성된 프로그램에 전달할 수 없으며, 인접하지 않을 수도 있기 때문에 `memcopy`와 같은 빠른 하위 수준 함수로 안정적으로 복사하거나 네트워크를 통해 직렬화할 수 없습니다.

C++ 프로그램 및 메타프로그램뿐만 아니라 컴파일러가 특정 메모리 레이아웃에 종속된 작업에 대해 지정된 유형의 적합성에 대한 추론을 위해 C++14는 간단한 클래스와 구조체인 *trivial*, *표준 레이아웃* 및 *POD* 또는 Plain Old Data의 세 가지 범주를 도입했습니다. 표준 라이브러리에는 지정된 유형이 지정된 범주에 속하는지 여부를 결정하는 함수 템플릿 `is_trivial<T>`, `is_standard_layout<T>` 및 `is_pod<T>`가 있습니다.

## <a name="trivial-types"></a>Trivial 형식

C++의 클래스 또는 구조체에 컴파일러 제공 또는 명시적으로 특수 멤버 함수를 기본값으로 지정하는 경우 이는 trivial 형식입니다. 인접한 메모리 영역을 차지합니다. 다른 액세스 지정자가 있는 멤버를 가질 수 있습니다. C++에서 컴파일러는 이 상황에서 멤버를 정렬하는 방법을 자유롭게 선택할 수 있습니다. 따라서 이러한 개체를 memcopy할 수는 있지만 C 프로그램에서 안정적으로 사용할 수 없습니다. trivial 형식 T는 char 또는 부호 없는 char 배열에 복사하고, 안전하게 T 변수로 다시 복사할 수 있습니다. 맞춤 요구 사항으로 인해 형식 멤버 간에 패딩 바이트가 있을 수 있습니다.

Trivial 형식에는 trivial 기본 생성자, trivial 복사 생성자, trivial 복사 할당 연산자 및 trivial 소멸자가 있습니다. 각각의 경우에 *trivial* 은 생성자/연산자/소멸자가 사용자 제공이 아니라 다음과 같은 클래스에 속한다는 것을 의미합니다.

- 가상 함수 또는 기본 클래스가 없음

- 해당 비 trivial 생성자/연산자/소멸자가 있는 기본 클래스가 없음

- 해당 비 trivial 생성자/연산자/소멸자가 있는 클래스 유형의 데이터 멤버 없음

다음 예제는 trivial 형식을 보여줍니다. Trivial2에서 `Trivial2(int a, int b)` 생성자가 있으면 기본 생성자를 제공해야 합니다. trivial로 형식을 한정하려면 해당 생성자를 명시적으로 기본 설정해야 합니다.

```cpp
struct Trivial
{
   int i;
private:
   int j;
};

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>표준 레이아웃 형식

클래스 또는 구조체에 C 언어에서 찾을 수 없는 가상 함수와 같은 특정 C++ 언어 기능이 없고 모든 멤버가 동일한 액세스 제어를 갖고 있으면 표준 레이아웃 형식입니다. 이는 memcopy가 가능하고 레이아웃이 충분히 정의되어 C 프로그램에서 사용할 수 있습니다. 표준 레이아웃 형식은 사용자 정의 특수 멤버 함수를 사용할 수도 있습니다. 또한 표준 레이아웃 형식에는 다음과 같은 특성이 있습니다.

- 가상 함수 또는 기본 클래스 없음

- 모든 비정적 데이터 멤버는 동일한 액세스 제어를 가지고 있습니다.

- 클래스 형식의 모든 비정적 멤버는 표준 레이아웃입니다.

- 모든 기본 클래스는 표준 레이아웃입니다.

- 첫 번째 비정적 데이터 멤버와 동일한 유형의 기본 클래스가 없습니다.

- 다음 조건 중 하나를 충족합니다.

  - 가장 많이 파생된 클래스에 비정적 데이터 멤버가 없고, 비정적 데이터 멤버가 있는 기본 클래스가 하나 이하인 경우, 또는

  - 비정적 데이터 멤버가 있는 기본 클래스가 없음

다음 코드는 표준 레이아웃 형식의 한 가지 예를 보여줍니다.

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

마지막 두 가지 요구 사항은 코드로 더 잘 설명될 수 있습니다. 다음 예제에서 기본 사항이 표준 레이아웃임에도 불구하고 `Derived`는 표준 레이아웃이 아닙니다. 가장 많이 파생된 클래스와 `Base`는 모두 비정적 데이터 멤버가 있기 때문입니다.

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

이 예제에서 `Base`에 비정적 데이터 멤버가 없기 때문에 `Derived`는 표준 레이아웃입니다.

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

`Base`에 데이터 멤버가 있고 `Derived`에 멤버 함수만 있는 경우에도 파생된 것이 표준 레이아웃이 될 수 있습니다.

## <a name="pod-types"></a>POD 형식

클래스 또는 구조체가 사소하고 표준 레이아웃인 경우 POD(Plain Old Data) 형식입니다. 따라서 POD 형식의 메모리 레이아웃은 연속적이며 각 멤버는 이전에 선언된 멤버보다 더 높은 주소를 가지므로 바이트 복사본 및 이진 I/O를 위한 바이트가 이러한 유형에 대해 수행될 수 있습니다.  int와 같은 스칼라 형식도 POD 형식입니다. 클래스인 POD 형식은 POD 형식만 비정적 데이터 멤버로 가질 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 trivial, 표준 레이아웃 및 POD 형식 간의 차이점을 보여줍니다.

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
   int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
{
   int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal-types"></a><a name="literal_types"></a> 리터럴 형식

리터럴 형식은 컴파일 타임에 해당 레이아웃이 결정될 수 있는 형식입니다. 다음은 리터럴 형식입니다.

- void
- 스칼라 형식
- references
- void, 스칼라 형식 또는 참조의 배열
- trivial 소멸자 및 이동 또는 복사 생성자가 아닌 constexpr 생성자를 하나 이상 포함하는 클래스입니다. 또한 해당 비정적 데이터 멤버 및 기본 클래스가 모두 리터럴 형식이고 volatile이 아니어야 합니다.

## <a name="see-also"></a>참고 항목

[기본 개념](../cpp/basic-concepts-cpp.md)
