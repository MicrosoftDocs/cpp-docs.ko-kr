---
title: '&lt;stack&gt; 연산자 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- stack/std::operator!=
- stack/std::operator&gt;
- stack/std::operator&gt;=
- stack/std::operator&lt;
- stack/std::operator&lt;=
- stack/std::operator==
dev_langs:
- C++
ms.assetid: 9c1fc282-2f61-4727-9e80-84ea5d4934a2
helpviewer_keywords:
- std::operator!= (stack)
- std::operator&gt; (stack)
- std::operator&gt;= (stack)
- std::operator&lt; (stack)
- std::operator&lt;= (stack)
- std::operator== (stack)
ms.openlocfilehash: 5d3bafd2d3112a2f4155f55a554b6c9c2e351b1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861648"
---
# <a name="ltstackgt-operators"></a>&lt;stack&gt; 연산자

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

연산자의 좌변에 있는 stack 개체가 우변에 있는 stack 개체와 같지 않은지 테스트합니다.

```cpp
bool operator!=(const stack <Type, Container>& left, const stack <Type, Container>& right,);
```

### <a name="parameters"></a>매개 변수

`left` 형식의 개체 **스택**합니다.

`right` 형식의 개체 **스택**합니다.

### <a name="return-value"></a>반환 값

스택이 같지 않으면 **true**이고 같으면 **false**입니다.

### <a name="remarks"></a>설명

stack 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소값이 같으면 두 스택은 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// stack_op_me.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> >  s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 != s2 )
      cout << "The stacks s1 and s2 are not equal." << endl;
   else
      cout << "The stacks s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The stacks s1 and s3 are not equal." << endl;
   else
      cout << "The stacks s1 and s3 are equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_lt"></a>  operator&lt;

연산자의 좌변에 있는 스택 개체가 우변에 있는 스택 개체보다 작은지 테스트합니다.

```cpp
bool operator<(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>매개 변수

`left` 형식의 개체 **스택**합니다.

`right` 형식의 개체 **스택**합니다.

### <a name="return-value"></a>반환 값

연산자 좌변의 stack이 연산자 우변의 stack보다 작으며 같지 않으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

stack 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 stack 개체 간의 보다 작음 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// stack_op_lt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 2 );
   s1.push( 4 );
   s1.push( 6 );
   s1.push( 8 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 2 );
   s3.push( 4 );
   s3.push( 6 );
   s3.push( 8 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;

   // to print out the stack s1 ( by unstacking the elements):
   stack <int>::size_type i_size_s1 = s1.size( );
   cout << "The stack s1 from the top down is: ( ";
   unsigned int i;
   for ( i = 1 ; i <= i_size_s1 ; i++ )
   {
      cout << s1.top( ) << " ";
      s1.pop( );
   }
   cout << ")." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
The stack s1 from the top down is: ( 8 6 4 2 ).
```

## <a name="op_lt_eq"></a>  operator&lt;=

연산자의 좌변에 있는 스택 개체가 우변에 있는 스택 개체보다 작거나 같은지 테스트합니다.

```cpp
bool operator<=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>매개 변수

`left` 형식의 개체 **스택**합니다.

`right` 형식의 개체 **스택**합니다.

### <a name="return-value"></a>반환 값

연산자 좌변의 stack이 연산자 우변의 stack보다 작거나 같으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

stack 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 stack 개체 간의 작거나 같음 관계는 같지 않은 첫 번째 요소 쌍의 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// stack_op_le.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with default deque base container
   stack <int> s1, s2, s3;

   s1.push( 5 );
   s1.push( 10 );
   s2.push( 1 );
   s2.push( 2 );
   s3.push( 5 );
   s3.push( 10 );

   if ( s1 <= s2 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;

   if ( s1 <= s3 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is greater than the stack s2.
The stack s1 is less than or equal to the stack s3.
```

## <a name="op_eq_eq"></a>  operator==

연산자의 좌변에 있는 stack 개체가 우변에 있는 stack 개체와 같은지 테스트합니다.

```cpp
bool operator==(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>매개 변수

`left` 형식의 개체 **스택**합니다.

`right` 형식의 개체 **스택**합니다.

### <a name="return-value"></a>반환 값

스택이 같으면 **true**이고 같지 않으면 **false**입니다.

### <a name="remarks"></a>설명

stack 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 포함된 요소 수가 같고 개별 요소값이 같으면 두 스택은 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

### <a name="example"></a>예제

```cpp
// stack_op_eq.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> > s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 == s2 )
      cout << "The stacks s1 and s2 are equal." << endl;
   else
      cout << "The stacks s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The stacks s1 and s3 are equal." << endl;
   else
      cout << "The stacks s1 and s3 are not equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_gt"></a>  operator&gt;

연산자의 좌변에 있는 스택 개체가 우변에 있는 스택 개체보다 큰지 테스트합니다.

```cpp
bool operator>(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>매개 변수

`left` 형식의 개체 **스택**합니다.

`right` 형식의 개체 **스택**합니다.

### <a name="return-value"></a>반환 값

연산자 좌변의 stack이 연산자 우변의 stack보다 크며 같지 않으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

stack 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 stack 개체 간의 보다 큼 관계는 같지 않은 요소의 첫 번째 쌍 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// stack_op_gt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s1.push( 3 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 > s2 )
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s2." << endl;

   if ( s1> s3 )
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is not greater than the stack s2.
The stack s1 is greater than the stack s3.
```

## <a name="op_gt_eq"></a>  operator&gt;=

연산자의 좌변에 있는 스택 개체가 우변에 있는 스택 개체보다 크거나 같은지 테스트합니다.

```cpp
bool operator>=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>매개 변수

`left` 형식의 개체 **스택**합니다.

`right` 형식의 개체 **스택**합니다.

### <a name="return-value"></a>반환 값

연산자 좌변의 stack이 연산자 우변의 stack보다 엄격하게 작으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

stack 개체 간의 비교는 해당 요소의 쌍 비교를 기반으로 합니다. 두 stack 개체 간의 크거나 같음 관계는 같지 않은 첫 번째 요소 쌍의 비교를 기반으로 합니다.

### <a name="example"></a>예제

```cpp
// stack_op_ge.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
```

## <a name="see-also"></a>참고자료

[\<stack>](../standard-library/stack.md)<br/>
