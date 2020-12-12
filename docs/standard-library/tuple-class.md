---
description: '자세한 정보: 튜플 클래스'
title: 튜플 클래스
ms.date: 11/04/2016
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
ms.openlocfilehash: 9beb3f263fa516d7d4096c404c135deffde6fc31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169024"
---
# <a name="tuple-class"></a>튜플 클래스

고정 길이의 요소 시퀀스를 래핑합니다.

## <a name="syntax"></a>구문

```cpp
class tuple {
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple(const pair<U1, U2>&); // N == 2

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple& operator=(const pair<U1, U2>&); // N == 2
};
```

### <a name="parameters"></a>매개 변수

*TN*\
N번째 튜플 요소의 형식입니다.

## <a name="remarks"></a>설명

클래스 템플릿은,, ... `T1` `T2` ,, `TN` 각각의 N 개 개체를 저장 하는 개체를 설명 `0 <= N <= Nmax` 합니다. 튜플 인스턴스의 범위는 `tuple<T1, T2, ..., TN>` `N` 해당 템플릿 인수의 개수입니다. 템플릿 인수 및 해당 형식의 저장 된 값의 인덱스는 `Ti` `i - 1` 입니다. 따라서이 설명서에서 1에서 N 사이의 형식으로 숫자를 표시 하는 동안 해당 인덱스 값의 범위는 0에서 N-1 사이입니다.

## <a name="example"></a>예제

```cpp
// tuple.cpp
// compile with: /EHsc

#include <vector>
#include <iomanip>
#include <iostream>
#include <tuple>
#include <string>

using namespace std;

typedef tuple <int, double, string> ids;

void print_ids(const ids& i)
{
   cout << "( "
        << get<0>(i) << ", "
        << get<1>(i) << ", "
        << get<2>(i) << " )." << endl;
}

int main( )
{
   // Using the constructor to declare and initialize a tuple
   ids p1(10, 1.1e-2, "one");

   // Compare using the helper function to declare and initialize a tuple
   ids p2;
   p2 = make_tuple(10, 2.22e-1, "two");

   // Making a copy of a tuple
   ids p3(p1);

   cout.precision(3);
   cout << "The tuple p1 is: ( ";
   print_ids(p1);
   cout << "The tuple p2 is: ( ";
   print_ids(p2);
   cout << "The tuple p3 is: ( ";
   print_ids(p3);

   vector<ids> v;

   v.push_back(p1);
   v.push_back(p2);
   v.push_back(make_tuple(3, 3.3e-2, "three"));

   cout << "The tuples in the vector are" << endl;
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)
   {
      print_ids(*i);
   }
}
```

```Output
The tuple p1 is: ( 10, 0.011, one ).
The tuple p2 is: ( 10, 0.222, two ).
The tuple p3 is: ( 10, 0.011, one ).
The tuples in the vector are
( 10, 0.011, one ).
( 10, 0.222, two ).
( 3, 0.033, three ).
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

`tuple` 개체를 할당합니다.

```cpp
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>
   tuple& operator=(const pair<U1, U2>& right); // N == 2

tuple& operator=(tuple&& right);

template <class U1, class U2>
   tuple& operator=(pair<U1, U2>&& right);
```

### <a name="parameters"></a>매개 변수

*되지*\
N번째 복사된 튜플 요소의 형식입니다.

*오른쪽*\
복사할 튜플입니다.

### <a name="remarks"></a>설명

처음 두 멤버 연산자는의 요소를의 해당 *요소에 할당* 합니다 **`*this`** . 세 번째 멤버 연산자는 `right.first` 의 인덱스 0에 있는 요소 **`*this`** 와 인덱스 1의 요소에 할당 합니다 `right.second` . 세 개의 멤버 연산자는 모두 **`*this`** 를 반환 합니다.

나머지 구성원 연산자도 앞의 연산자와 동일하지만 [Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 사용합니다.

### <a name="example"></a>예제

```cpp
// std__tuple__tuple_operator_as.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
    {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c1);
    std::cout << " " << std::get<1>(c1);
    std::cout << " " << std::get<2>(c1);
    std::cout << " " << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2;
    c2 = std::make_pair('x', 4);

// display contents " x 4"
    std::cout << " " << std::get<0>(c2);
    std::cout << " " << std::get<1>(c2);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
```

## <a name="swap"></a><a name="tuple_swap"></a> 스왑을

두 튜플의 요소를 교환합니다.

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>매개 변수

*비어*\
튜플 *오른쪽* 의 요소와 교환할 요소를 포함 하는 튜플입니다.

*오른쪽*\
요소를 *왼쪽* 튜플의 요소와 교환 해야 하는 튜플입니다.

### <a name="remarks"></a>설명

함수는 `left.swap(right)`을 실행합니다.

## <a name="tuple"></a><a name="tuple"></a> 튜플이

`tuple` 개체를 생성합니다.

```cpp
constexpr tuple();
explicit constexpr tuple(const Types&...);
template <class... UTypes>
   explicit constexpr tuple(UTypes&&...);

tuple(const tuple&) = default;
tuple(tuple&&) = default;

template <class... UTypes>
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>
   constexpr tuple(tuple<UTypes...>&&);

// only if sizeof...(Types) == 2
template <class U1, class U2>
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>
   constexpr tuple(pair<U1, U2>&&);
```

### <a name="parameters"></a>매개 변수

*되지*\
N번째 복사된 튜플 요소의 형식입니다.

*오른쪽*\
복사할 튜플입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 요소가 기본 생성되는 개체를 생성합니다.

두 번째 생성자는 요소가 각 `Pi`로 `i - 1` 인덱스의 요소를 초기화하여 `P1`, `P2`, ..., `PN` 인수에서 복사 생성되는 개체를 생성합니다.

세 번째 및 네 번째 생성자는 해당 요소가 *오른쪽* 의 해당 요소에서 복사 생성 되는 개체를 생성 합니다.

다섯 번째 생성자는 인덱스 0의 요소가 `right.first`에서 복사 생성되고 인덱스 1의 요소가 `right.second`에서 복사 생성되는 개체를 생성합니다.

나머지 생성자도 앞의 생성자와 동일하지만 [Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 사용합니다.

### <a name="example"></a>예제

```cpp
// std__tuple__tuple_tuple.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
{
    Mytuple c0(0, 1, 2, 3);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c1) << " ";
    std::cout << std::get<1>(c1) << " ";
    std::cout << std::get<2>(c1) << " ";
    std::cout << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2(std::make_pair('x', 4));

    // display contents "x 4"
    std::cout << std::get<0>(c2) << " ";
    std::cout << std::get<1>(c2);
    std::cout << std::endl;

    Mytuple c3(c0);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c3) << " ";
    std::cout << std::get<1>(c3) << " ";
    std::cout << std::get<2>(c3) << " ";
    std::cout << std::get<3>(c3);
    std::cout << std::endl;

    typedef std::tuple<int, float, int, float> Mytuple2;
    Mytuple c4(Mytuple2(4, 5, 6, 7));

    // display contents "4 5 6 7"
    std::cout << std::get<0>(c4) << " ";
    std::cout << std::get<1>(c4) << " ";
    std::cout << std::get<2>(c4) << " ";
    std::cout << std::get<3>(c4);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
0 1 2 3
4 5 6 7
```
