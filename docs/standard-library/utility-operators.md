---
title: '&lt;utility&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: ec6c996487dc2e6c5ce628fe5e080b4f601479d9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854870"
---
# <a name="ltutilitygt-operators"></a>&lt;utility&gt; 연산자

> [!NOTE]
> `Type&`를 사용 하는 연산자는 `namespace rel_ops`에 포함 됩니다.

## <a name="op_neq"></a> operator!=

연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체와 같지 않은지 테스트합니다.

```cpp
template <class Type>
    constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>매개 변수

*왼쪽*\
`pair` 형식의 개체입니다.

*오른쪽*\
`pair` 형식의 개체입니다.

### <a name="return-value"></a>Return Value

pair가 같지 않으면 **true**이고 pair가 같으면 **false**입니다.

### <a name="remarks"></a>설명

해당 요소가 각각 같으면 한 쌍과 다른 쌍이 같습니다. 한 쌍의 첫 번째 또는 두 번째 요소가 다른 쌍의 해당 요소와 같지 않으면 두 쌍은 같지 않습니다.

### <a name="example"></a>예제

```cpp
// utility_op_ne.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 != p2 )
      cout << "The pairs p1 and p2 are not equal." << endl;
   else
      cout << "The pairs p1 and p2 are equal." << endl;

   if ( p1 != p3 )
      cout << "The pairs p1 and p3 are not equal." << endl;
   else
      cout << "The pairs p1 and p3 are equal." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.111 ).
The pair p2 is: ( 1000, 0.00111 ).
The pair p3 is: ( 10, 0.111 ).

The pairs p1 and p2 are not equal.
The pairs p1 and p3 are equal.
```

## <a name="op_eq_eq"></a>연산자 = =

연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체와 같은지 테스트합니다.

```cpp
template <class T, class U>
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>매개 변수

*왼쪽*\
`pair` 형식의 개체입니다.

*오른쪽*\
`pair` 형식의 개체입니다.

### <a name="return-value"></a>Return Value

pair가 같으면 **true**이고 **가 같지 않으면** false`pair`입니다.

### <a name="remarks"></a>설명

해당 요소가 각각 같으면 한 쌍과 다른 쌍이 같습니다. 함수에서 `left`을 반환합니다. **first** == `right`. **first** && `left`. **second** == `right`. **second**와 같습니다. 한 쌍의 첫 번째 또는 두 번째 요소가 다른 쌍의 해당 요소와 같지 않으면 두 쌍은 같지 않습니다.

### <a name="example"></a>예제

```cpp
// utility_op_eq.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 == p2 )
      cout << "The pairs p1 and p2 are equal." << endl;
   else
      cout << "The pairs p1 and p2 are not equal." << endl;

   if ( p1 == p3 )
      cout << "The pairs p1 and p3 are equal." << endl;
   else
      cout << "The pairs p1 and p3 are not equal." << endl;
}
```

## <a name="op_lt"></a> 연산자&lt;

연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 작은지 테스트합니다.

```cpp
template <class T, class U>
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>매개 변수

*왼쪽*\
연산자의 좌변에 있는 `pair` 형식의 개체입니다.

*오른쪽*\
연산자의 우변에 있는 `pair` 형식의 개체입니다.

### <a name="return-value"></a>Return Value

연산자 좌변의 **가 연산자 우변의** 보다 엄격하게 작으면 `pair`true`pair`이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

*왼쪽* 이 *오른쪽*보다 작고 `left` `pair` 개체는 `right` `pair` 개체 보다 엄격 하 게 작아야 합니다.

쌍의 비교에서 두 쌍에서 값의 첫 번째 요소가 가장 높은 우선 순위를 갖습니다. 서로 다르면 해당 비교 결과가 쌍의 비교 결과로 사용됩니다. 첫 번째 요소 값이 다르지 않으면 두 번째 요소 값이 비교되고 해당 비교 결과가 쌍의 비교 결과로 사용됩니다.

### <a name="example"></a>예제

```cpp
// utility_op_lt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 < p2 )
      cout << "The pair p1 is less than the pair p2." << endl;
   else
      cout << "The pair p1 is not less than the pair p2." << endl;

   if ( p1 < p3 )
      cout << "The pair p1 is less than the pair p3." << endl;
   else
      cout << "The pair p1 is not less than the pair p3." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).

The pair p1 is less than the pair p2.
The pair p1 is not less than the pair p3.
```

## <a name="op_lt_eq"></a>연산자&lt;=

연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 작은지 테스트합니다.

```cpp
template <class Type>
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>매개 변수

*왼쪽*\
연산자의 좌변에 있는 `pair` 형식의 개체입니다.

*오른쪽*\
연산자의 우변에 있는 `pair` 형식의 개체입니다.

### <a name="return-value"></a>Return Value

연산자 좌변의 **가 연산자 우변의** 보다 작거나 같으면 `pair`true`pair`이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

쌍의 비교에서 두 쌍에서 값의 첫 번째 요소가 가장 높은 우선 순위를 갖습니다. 서로 다르면 해당 비교 결과가 쌍의 비교 결과로 사용됩니다. 첫 번째 요소 값이 다르지 않으면 두 번째 요소 값이 비교되고 해당 비교 결과가 쌍의 비교 결과로 사용됩니다.

### <a name="example"></a>예제

```cpp
// utility_op_le.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 <= p2 )
      cout << "The pair p1 is less than or equal to the pair p2." << endl;
   else
      cout << "The pair p1 is greater than the pair p2." << endl;

   if ( p1 <= p3 )
      cout << "The pair p1 is less than or equal to the pair p3." << endl;
   else
      cout << "The pair p1 is greater than the pair p3." << endl;

   if ( p1 <= p4 )
      cout << "The pair p1 is less than or equal to the pair p4." << endl;
   else
      cout << "The pair p1 is greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than or equal to the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is less than or equal to the pair p4.
```

## <a name="op_gt"></a> 연산자&gt;

연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 큰지 테스트합니다.

```cpp
template <class Type>
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>매개 변수

*왼쪽*\
연산자의 좌변에 있는 `pair` 형식의 개체입니다.

*오른쪽*\
연산자의 우변에 있는 `pair` 형식의 개체입니다.

### <a name="return-value"></a>Return Value

연산자 좌변의 **가 연산자 우변의** 보다 엄격하게 크면 `pair`true`pair`이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

*왼쪽* 이 *오른쪽*보다 크거나 같으면 `left` `pair` 개체는 `right` `pair` 개체 보다 엄격 하 게 커야 합니다.

쌍의 비교에서 두 쌍에서 값의 첫 번째 요소가 가장 높은 우선 순위를 갖습니다. 서로 다르면 해당 비교 결과가 쌍의 비교 결과로 사용됩니다. 첫 번째 요소 값이 다르지 않으면 두 번째 요소 값이 비교되고 해당 비교 결과가 쌍의 비교 결과로 사용됩니다.

### <a name="example"></a>예제

```cpp
// utility_op_gt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 > p2 )
      cout << "The pair p1 is greater than the pair p2." << endl;
   else
      cout << "The pair p1 is not greater than the pair p2." << endl;

   if ( p1 > p3 )
      cout << "The pair p1 is greater than the pair p3." << endl;
   else
      cout << "The pair p1 is not greater than the pair p3." << endl;

   if ( p1 > p4 )
      cout << "The pair p1 is greater than the pair p4." << endl;
   else
      cout << "The pair p1 is not greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is not greater than the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is not greater than the pair p4.
```

## <a name="op_gt_eq"></a>연산자&gt;=

연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 크거나 같은지 테스트합니다.

```cpp
template <class Type>
    constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>매개 변수

*왼쪽*\
연산자의 좌변에 있는 `pair` 형식의 개체입니다.

*오른쪽*\
연산자의 우변에 있는 `pair` 형식의 개체입니다.

### <a name="return-value"></a>Return Value

연산자 좌변의 **가 연산자 우변의** 보다 크거나 같으면 `pair`true`pair`이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

쌍의 비교에서 두 쌍에서 값의 첫 번째 요소가 가장 높은 우선 순위를 갖습니다. 서로 다르면 해당 비교 결과가 쌍의 비교 결과로 사용됩니다. 첫 번째 요소 값이 다르지 않으면 두 번째 요소 값이 비교되고 해당 비교 결과가 쌍의 비교 결과로 사용됩니다.

### <a name="example"></a>예제

```cpp
// utility_op_ge.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 >= p2 )
      cout << "Pair p1 is greater than or equal to pair p2." << endl;
   else
      cout << "The pair p1 is less than the pair p2." << endl;

   if ( p1 >= p3 )
      cout << "Pair p1 is greater than or equal to pair p3." << endl;
   else
      cout << "The pair p1 is less than the pair p3." << endl;

   if ( p1 >= p4 )
      cout << "Pair p1 is greater than or equal to pair p4." << endl;
   else
      cout << "The pair p1 is less than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than the pair p2.
Pair p1 is greater than or equal to pair p3.
Pair p1 is greater than or equal to pair p4.
```
