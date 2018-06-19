---
title: front_insert_iterator 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aacb6fda870f698bef23184912fc3becfd6c7e2d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847158"
---
# <a name="frontinsertiterator-class"></a>front_insert_iterator 클래스

출력 반복기의 요구 사항을 충족하는 반복기 어댑터에 대해 설명합니다. 요소를 덮어쓰는 것이 아니라, 시퀀스 앞 부분에 요소를 삽입하므로 C++ 시퀀스 컨테이너의 반복기가 제공한 덮어쓰기 의미 체계와 다른 의미 체계를 제공합니다. `front_insert_iterator` 클래스는 컨테이너 형식에 대해 템플릿화됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>매개 변수

`Container` 의해 삽입 될 요소는 앞에는 컨테이너 유형에 `front_insert_iterator`합니다.

## <a name="remarks"></a>설명

컨테이너는 가능할 경우 시퀀스 처음에 분할된 시간으로 요소를 삽입하는 전면 삽입 시퀀스에 대한 요구 사항을 충족해야 합니다. [deque 클래스](../standard-library/deque-class.md) 및 [list](../standard-library/list-class.md) 클래스에서 정의한 C++ 표준 라이브러리 시퀀스 컨테이너는 필요한 `push_front` 멤버 함수를 제공하며 이러한 요구 사항을 충족합니다. 반면 [vector 클래스](../standard-library/vector-class.md)에서 정의한 시퀀스 컨테이너는 이러한 요구 사항을 충족하지 않으며 `front_insert_iterator`에서 사용할 수 있도록 적용할 수 없습니다. `front_insert_iterator`는 항상 컨테이너를 사용하여 초기화해야 합니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|지정된 컨테이너 개체 앞에 요소를 삽입할 수 있는 반복기를 만듭니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[container_type](#container_type)|전면 삽입 대상인 컨테이너를 나타내는 형식입니다.|
|[reference](#reference)|연관 컨테이너에서 제어하는 시퀀스의 요소에 대한 참조를 제공하는 형식입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[operator*](#op_star)|전면 삽입을 위해 출력 반복기 식을 구현하는 데 사용된 역참조 연산자 * `i` = `x`|
|[operator++](#op_add_add)|값을 저장할 다음 위치에 `front_insert_iterator`를 증가시킵니다.|
|[operator=](#op_eq)|전면 삽입을 위해 출력 반복기 식을 구현하는 데 사용된 할당 연산자 * `i` = `x`|

## <a name="requirements"></a>요구 사항

**헤더**: \<iterator>

**네임스페이스:** std

## <a name="container_type"></a>  front_insert_iterator::container_type

전면 삽입 대상인 컨테이너를 나타내는 형식입니다.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 **Container**의 동의어입니다.

### <a name="example"></a>예제

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
\* Output:
The list L2 is: ( 40 10 20 ).
*\
```

## <a name="front_insert_iterator"></a>  front_insert_iterator::front_insert_iterator

지정된 컨테이너 개체 앞에 요소를 삽입할 수 있는 반복기를 만듭니다.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>매개 변수

`_Cont` 컨테이너 개체는 `front_insert_iterator` 요소를 삽입 하는 것입니다.

### <a name="return-value"></a>반환 값

매개 변수 컨테이너 개체에 대한 `front_insert_iterator`입니다.

### <a name="example"></a>예제

```cpp
// front_insert_iterator_front_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
 *Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
\* Output:
The list L is:
 ( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*\
```

## <a name="op_star"></a>  front_insert_iterator::operator*

주소가 지정된 요소를 반환하는 삽입 반복기를 역참조합니다.

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>반환 값

멤버 함수는 주소가 지정된 요소의 값을 반환합니다.

### <a name="remarks"></a>설명

출력 반복기 식 **\*Iter** = **value**를 구현하는 데 사용됩니다. **Iter**이 시퀀스에서 요소의 주소를 지정하는 반복기인 경우 **\*Iter** = **value**는 해당 요소를 값과 바꾸며 시퀀스에서 총 요소 수를 변경하지 않습니다.

### <a name="example"></a>예제

```cpp
// front_insert_iterator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
 *Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
\* Output:
The list L is:
 ( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*\
```

## <a name="op_add_add"></a>  front_insert_iterator::operator++

값을 저장할 다음 위치에 `back_insert_iterator`를 증가시킵니다.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>반환 값

값을 저장할 수 있는 다음 위치의 주소를 지정하는 `front_insert_iterator`입니다.

### <a name="remarks"></a>설명

preincrementation과 postincrementation 연산자는 둘 다 동일한 결과를 반환합니다.

### <a name="example"></a>예제

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
 *iter = 10;
   iter++;
 *iter = 20;
   iter++;
 *iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
\* Output:
The list L1 is: ( 30 20 10 ).
*\
```

## <a name="op_eq"></a>  front_insert_iterator::operator=

컨테이너의 앞에 값을 추가(푸시)합니다.

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>매개 변수

`val` 컨테이너에 할당할 값입니다.

### <a name="return-value"></a>반환 값

컨테이너의 앞에 삽입된 마지막 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 연산자는 `container.push_front( val)`을 계산하고 나서 `*this`를 반환합니다.

두 번째 멤버 연산자는 다음을 계산합니다.

`container->push_front((typename Container::value_type&&) val)`,

그런 다음 `*this`를 반환합니다.

### <a name="example"></a>예제

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
 *iter = 10;
   iter++;
 *iter = 20;
   iter++;
 *iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
\* Output:
The list L1 is: ( 30 20 10 ).
*\
```

## <a name="reference"></a>  front_insert_iterator::reference

연관 컨테이너에서 제어하는 시퀀스의 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>예제

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
 *fiivIter = 10;
 *fiivIter = 20;
 *fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
\* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*\
```

## <a name="see-also"></a>참고자료

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
