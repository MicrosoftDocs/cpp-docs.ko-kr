---
description: Back_insert_iterator 클래스에 대해 자세히 알아보세요.
title: back_insert_iterator 클래스
ms.date: 11/04/2016
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
ms.openlocfilehash: e8c188da7201ccb78866981ffb64e168d1a8fc32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132772"
---
# <a name="back_insert_iterator-class"></a>back_insert_iterator 클래스

출력 반복기의 요구 사항을 충족하는 반복기 어댑터에 대해 설명합니다. 반복기 어댑터는 요소를 덮어쓰는 것이 아니라, 시퀀스 끝 부분에 요소를 삽입하므로 C++ 시퀀스 컨테이너의 반복기가 제공한 덮어쓰기 의미 체계와 다른 의미 체계를 제공합니다. `back_insert_iterator` 클래스는 컨테이너 형식에 대해 템플릿화됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>매개 변수

*컨테이너*\
`back_insert_iterator`가 뒤에 요소를 삽입할 컨테이너의 형식입니다.

## <a name="remarks"></a>설명

컨테이너는 가능할 경우 시퀀스 끝에 분할된 시간으로 요소를 삽입하는 후면 삽입 시퀀스에 대한 요구 사항을 충족해야 합니다. [deque 클래스](../standard-library/deque-class.md), [list 클래스](../standard-library/list-class.md) 및 [vector 클래스](../standard-library/vector-class.md)에서 정의한 C++ 표준 라이브러리 시퀀스 컨테이너는 필요한 `push_back` 멤버 함수를 제공하며 이러한 요구 사항을 충족합니다. 이러한 세 컨테이너와 문자열은 각각 `back_insert_iterator`와 함께 사용하도록 조정할 수 있습니다. `back_insert_iterator`는 항상 컨테이너를 사용하여 초기화해야 합니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|컨테이너의 마지막 요소 다음에 요소를 삽입하는 `back_insert_iterator`를 만듭니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[container_type](#container_type)|`back_insert_iterator`에 대한 컨테이너를 제공하는 형식입니다.|
|[reference](#reference)|`back_insert_iterator`에 대한 참조를 제공하는 형식입니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자](#op_star)|뒤로 삽입을 위해 출력 반복기 식을 구현 하는 데 사용 되는 역참조 연산자 \* `i`  =  `x` 입니다.|
|[operator + +](#op_add_add)|값을 저장할 다음 위치에 `back_insert_iterator`를 증가시킵니다.|
|[연산자 =](#op_eq)|뒤로 삽입을 위해 출력 반복기 식을 구현 하는 데 사용 되는 할당 연산자 \* `i`  =  `x` 입니다.|

## <a name="requirements"></a>요구 사항

**헤더**: \<iterator>

**네임스페이스:** std

## <a name="back_insert_iteratorback_insert_iterator"></a><a name="back_insert_iterator"></a> back_insert_iterator:: back_insert_iterator

컨테이너의 마지막 요소 다음에 요소를 삽입하는 `back_insert_iterator`를 만듭니다.

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>매개 변수

*_Cont*\
`back_insert_iterator`가 요소를 삽입할 컨테이너입니다.

### <a name="return-value"></a>반환 값

매개 변수 컨테이너에 대한 `back_insert_iterator`입니다.

### <a name="example"></a>예제

```cpp
// back_insert_iterator_back_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions with member function
   back_inserter ( vec ) = 40;
   back_inserter ( vec ) = 50;

   // Alternatively, insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 600;
   backiter++;
*backiter = 700;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 1 2 3 ).
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).
```

## <a name="back_insert_iteratorcontainer_type"></a><a name="container_type"></a> back_insert_iterator:: container_type

`back_insert_iterator`에 대한 컨테이너를 제공하는 형식입니다.

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 **Container** 의 동의어입니다.

### <a name="example"></a>예제

```cpp
// back_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The original vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::container_type vec1 = vec;
   back_inserter ( vec1 ) = 40;

   cout << "After the insertion, the vector is: ( ";
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector vec is: ( 1 2 3 ).
After the insertion, the vector is: ( 1 2 3 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_star"></a> back_insert_iterator:: operator\*

출력 반복기 식 i x를 구현 하는 데 사용 되는 역참조 연산자 \*   =  입니다.

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>반환 값

컨테이너의 뒤쪽에 삽입된 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

출력 반복기 식 **\* Iter** value를 구현 하는 데 사용  =  됩니다. **Iter** 이 시퀀스에서 요소의 주소를 지정하는 반복기인 경우 **\*Iter** = **value** 는 해당 요소를 값과 바꾸며 시퀀스에서 총 요소 수를 변경하지 않습니다.

### <a name="example"></a>예제

```cpp
// back_insert_iterator_back_insert.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_add_add"></a> back_insert_iterator:: operator + +

값을 저장할 다음 위치에 `back_insert_iterator`를 증가시킵니다.

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>반환 값

값을 저장할 수 있는 다음 위치의 주소를 지정하는 `back_insert_iterator`입니다.

### <a name="remarks"></a>설명

preincrementation과 postincrementation 연산자는 둘 다 동일한 결과를 반환합니다.

### <a name="example"></a>예제

```cpp
// back_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 3 ; ++i )
   {
      vec.push_back ( 10 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;      // Increment to the next element
*backiter = 40;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 10 20 ).
After the insertions, the vector vec becomes: ( 10 20 30 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_eq"></a> back_insert_iterator:: operator =

컨테이너의 백 엔드에 값을 추가하거나 푸시합니다.

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
컨테이너에 삽입할 값입니다.

### <a name="return-value"></a>반환 값

컨테이너의 뒤쪽에 삽입된 마지막 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 연산자는 `Container.push_back( val)`을 계산한 다음

그런 다음 **`*this`** 를 반환 합니다. 두 번째 멤버 연산자는 다음을 계산합니다.

`container->push_back((typename Container::value_type&&)val)`,

그런 다음 **`*this`** 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// back_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

## <a name="back_insert_iteratorreference"></a><a name="reference"></a> back_insert_iterator:: reference

`back_insert_iterator`에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>설명

이 형식은 연관 컨테이너에서 제어하는 시퀀스의 요소에 대한 참조를 제공합니다.

### <a name="example"></a>예제

```cpp
// back_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::reference
        RefLast = *(vec.end ( ) - 1 );
   cout << "The last element in the vector vec is: "
        << RefLast << "." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
The last element in the vector vec is: 3.
```

## <a name="see-also"></a>참고 항목

[\<iterator>](../standard-library/iterator.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
