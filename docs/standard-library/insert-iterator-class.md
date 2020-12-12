---
description: Insert_iterator 클래스에 대해 자세히 알아보세요.
title: insert_iterator 클래스
ms.date: 11/04/2016
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
ms.openlocfilehash: d9089e0ab592ed6c8289570cc422aa6183444d55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231578"
---
# <a name="insert_iterator-class"></a>insert_iterator 클래스

출력 반복기의 요구 사항을 충족하는 반복기 어댑터에 대해 설명합니다. 반복기 어댑터는 요소를 덮어쓰는 것이 아니라, 시퀀스에 요소를 삽입하므로 C++ 시퀀스 및 연관 컨테이너의 반복기가 제공한 덮어쓰기 의미 체계와 다른 의미 체계를 제공합니다. `insert_iterator` 클래스는 조정하는 컨테이너 형식에 대해 템플릿화됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>매개 변수

*컨테이너*\
`insert_iterator`가 요소를 삽입할 컨테이너의 형식입니다.

## <a name="remarks"></a>설명

형식의 컨테이너는 `Container` 가변 크기의 컨테이너에 대 한 요구 사항을 충족 해야 하며, 매개 변수가 형식이 `Container::iterator` 고가 `Container::value_type` 형식을 반환 하는 두 개의 인수 삽입 멤버 함수가 있어야 합니다 `Container::iterator` . C++ 표준 라이브러리 시퀀스 및 정렬된 연관 컨테이너는 이러한 요구 사항을 준수하며 `insert_iterator`를 사용할 수 있도록 조정되었습니다. 연관 컨테이너의 경우 위치 인수는 힌트로 처리되며, 힌트가 얼마나 양호한가에 따라 성능이 향상되거나 저하될 수 있습니다. `insert_iterator`는 항상 컨테이너를 사용하여 초기화해야 합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[insert_iterator](#insert_iterator)|컨테이너의 지정된 위치에 요소를 삽입하는 `insert_iterator`를 만듭니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[container_type](#container_type)|일반 삽입 대상인 컨테이너를 나타내는 형식입니다.|
|[reference](#reference)|연관 컨테이너에서 제어하는 시퀀스의 요소에 대한 참조를 제공하는 형식입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자](#op_star)|일반 삽입을 위해 출력 반복기 식 * `i` = `x`를 구현하는 데 사용된 역참조 연산자입니다.|
|[operator + +](#op_add_add)|값을 저장할 다음 위치에 `insert_iterator`를 증가시킵니다.|
|[연산자 =](#op_eq)|일반 삽입을 위해 출력 반복기 식 * `i` = `x`를 구현하는 데 사용된 대입 연산자입니다.|

## <a name="requirements"></a>요구 사항

**헤더**: \<iterator>

**네임스페이스:** std

## <a name="insert_iteratorcontainer_type"></a><a name="container_type"></a> insert_iterator:: container_type

일반 삽입 대상인 컨테이너를 나타내는 형식입니다.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 *Container* 의 동의어입니다.

### <a name="example"></a>예제

```cpp
// insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   insert_iterator<list<int> >::container_type L2 = L1;
   inserter ( L2, L2.end ( ) ) = 20;
   inserter ( L2, L2.end ( ) ) = 10;
   inserter ( L2, L2.begin ( ) ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 20 10 ).
*/
```

## <a name="insert_iteratorinsert_iterator"></a><a name="insert_iterator"></a> insert_iterator:: insert_iterator

컨테이너의 지정된 위치에 요소를 삽입하는 `insert_iterator`를 만듭니다.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>매개 변수

*_Cont*\
`insert_iterator`에서 요소를 삽입할 대상 컨테이너입니다.

*_It*\
삽입할 위치입니다.

### <a name="remarks"></a>설명

모든 컨테이너에는 `insert_iterator`에서 호출하는 삽입 멤버 함수가 있습니다. 연관 컨테이너의 경우 위치 매개 변수는 단순히 제안입니다. inserter 함수는 값에 삽입하는 편리한 방법을 제공합니다.

### <a name="example"></a>예제

```cpp
// insert_iterator_insert_iterator.cpp
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
   for (i = 1 ; i < 4 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   inserter ( L, L.begin ( ) ) = 2;

   // Alternatively, you may use the template version
   insert_iterator< list < int> > Iter(L, L.end ( ) );
*Iter = 300;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( 10 20 30 ).
After the insertions, the list L is:
( 2 10 20 30 300 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_star"></a> insert_iterator:: operator *

주소가 지정된 요소를 반환하는 삽입 반복기를 역참조합니다.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>반환 값

멤버 함수는 주소가 지정된 요소의 값을 반환합니다.

### <a name="remarks"></a>설명

출력 반복기 식 **\* Iter** value를 구현 하는 데 사용  =  됩니다. `Iter`가 시퀀스의 요소에 주소를 지정한 반복기 인 경우 **\* Iter**  =  **value** 는 해당 요소를 value로 바꾸고 시퀀스의 총 요소 수를 변경 하지 않습니다.

### <a name="example"></a>예제

```cpp
// insert_iterator_op_deref.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_add_add"></a> insert_iterator:: operator + +

값을 저장할 다음 위치에 `insert_iterator`를 증가시킵니다.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>매개 변수

값을 저장할 수 있는 다음 위치의 주소를 지정하는 `insert_iterator`입니다.

### <a name="remarks"></a>설명

preincrementation과 postincrementation 연산자는 둘 다 동일한 결과를 반환합니다.

### <a name="example"></a>예제

```cpp
// insert_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 5 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );
*ii = 30;
   ii++;
*ii = 40;
   ii++;
*ii = 50;

   cout << "After the insertions, the vector vec becomes:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The vector vec is:
( 1 2 3 4 ).
After the insertions, the vector vec becomes:
( 30 40 50 1 2 3 4 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_eq"></a> insert_iterator:: operator =

컨테이너에 값을 삽입하고 새 요소를 가리키도록 업데이트된 반복기를 반환합니다.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
컨테이너에 할당할 값입니다.

### <a name="return-value"></a>반환 값

컨테이너에 삽입된 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 연산자는 다음을 계산합니다.

`Iter = container->insert(Iter, val)`;

`++Iter;`

그런 다음 **`*this`** 를 반환 합니다.

두 번째 멤버 연산자는 다음을 계산합니다.

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

그런 다음 **`*this`** 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// insert_iterator_op_assign.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratorreference"></a><a name="reference"></a> insert_iterator:: reference

연관 컨테이너에서 제어하는 시퀀스의 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>설명

이 형식은 연관 컨테이너에서 제어하는 시퀀스의 요소에 대한 참조를 제공합니다.

### <a name="example"></a>예제

```cpp
// insert_iterator_container_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );
*iivIter = 10;
*iivIter = 20;
*iivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )
      cout << *LIter << " ";
   cout << ")." << endl;

   insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*/
```

## <a name="see-also"></a>참고 항목

[\<iterator>](../standard-library/iterator.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
