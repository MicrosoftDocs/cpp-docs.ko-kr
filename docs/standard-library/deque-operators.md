---
description: '다음에 대 한 자세한 정보: &lt; deque &gt; 연산자'
title: '&lt;deque&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: f162a234aec66982e274755e7898cbbc1c63ab22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324563"
---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; 연산자

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

연산자의 좌변에 있는 deque 개체가 우변에 있는 deque 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`deque` 형식의 개체입니다.

*오른쪽*\
`deque` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** deque 개체가 같지 않으면이 고, 그렇지 않으면입니다. **`false`** deque 개체가 같으면입니다.

### <a name="remarks"></a>설명

deque 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 deque 개체는 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
```

```Output
The deques are not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> 연산자&lt;

연산자의 좌변에 있는 deque 개체가 우변에 있는 deque 개체보다 작은지 테스트합니다.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`deque` 형식의 개체입니다.

*오른쪽*\
`deque` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 deque이 연산자 우변의 deque 보다 작거나 같지 않으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

deque 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 보다 작음 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
```

```Output
Deque c1 is less than deque c2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 연산자&lt;=

연산자의 좌변에 있는 deque 개체가 우변에 있는 deque 개체보다 작거나 같은지 테스트합니다.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`deque` 형식의 개체입니다.

*오른쪽*\
`deque` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 deque이 연산자 우변의 deque 보다 작거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

deque 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 작거나 같음 관계는 같지 않은 첫 번째 요소 쌍의 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
```

```Output
Deque c1 is less than or equal to deque c2.
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

연산자의 좌변에 있는 deque 개체가 우변에 있는 deque 개체와 같은지 테스트합니다.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`deque` 형식의 개체입니다.

*오른쪽*\
`deque` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 deque이 연산자 우변의 deque과 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

deque 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소의 값이 같으면 두 deque는 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
```

```Output
The deques are equal.
The deques are not equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a> 연산자&gt;

연산자의 좌변에 있는 deque 개체가 우변에 있는 deque 개체보다 큰지 테스트합니다.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`deque` 형식의 개체입니다.

*오른쪽*\
`deque` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 deque이 연산자 우변의 deque 보다 크면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

deque 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 보다 큼 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
```

```Output
Deque c1 is greater than deque c2.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 연산자&gt;=

연산자의 좌변에 있는 deque 개체가 우변에 있는 deque 개체보다 크거나 같은지 테스트합니다.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`deque` 형식의 개체입니다.

*오른쪽*\
`deque` 형식의 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 연산자 좌 변의 deque이 연산자 우변의 deque 보다 크거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

deque 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 개체 간의 크거나 같음 관계는 같지 않은 첫 번째 요소 쌍의 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
```

```Output
Deque c1 is greater than or equal to deque c2.
```
