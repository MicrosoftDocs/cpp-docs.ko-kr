---
description: '자세한 정보: &lt; 반복기 &gt; 함수'
title: '&lt;iterator&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: 0db7e036cd89cf92449e539ac6a656658730425d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169257"
---
# <a name="ltiteratorgt-functions"></a>&lt;iterator&gt; 함수

## <a name="advance"></a><a name="advance"></a> 선

지정된 위치 수만큼 반복기를 증가시킵니다.

```cpp
template <class InputIterator, class Distance>
    void advance(InputIterator& InIt, Distance Off);
```

### <a name="parameters"></a>매개 변수

*Cloud-init*\
입력 반복기에 대해 증가하고 요구 사항을 충족해야 하는 반복기입니다.

*해제*\
반복기의 차이 형식으로 변환할 수 있고 반복기의 위치를 증가시킬 횟수를 지정하는 정수 계열 형식입니다.

### <a name="remarks"></a>설명

증가 범위는 특이하지 않아야 하며, 반복기는 역참조 가능하거나 끝을 지날 수 있어야 합니다.

가 `InputIterator` 양방향 반복기 형식에 대 한 요구 사항을 충족 하는 경우 *Off* 는 음수일 수 있습니다. `InputIterator`가 입력 또는 전방 반복기 형식이 면 *Off* 는 음수가 아니어야 합니다.

고급 함수는가 임의 액세스 반복기의 요구 사항을 충족 하는 경우 일관 된 복잡성을 갖습니다 `InputIterator` . 그렇지 않으면 선형 복잡성이 있으므로 잠재적으로 비용이 많이 듭니다.

### <a name="example"></a>예제

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a><a name="back_inserter"></a> back_inserter

지정된 컨테이너 뒤에 요소를 삽입할 수 있는 반복기를 만듭니다.

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>매개 변수

*_Cont*\
후면 삽입을 실행할 컨테이너입니다.

### <a name="return-value"></a>반환 값

`back_insert_iterator`컨테이너 개체와 연결 된 *_Cont* 입니다.

### <a name="remarks"></a>설명

C++ 표준 라이브러리 내에서 인수는 `push_back` 멤버 함수가 있는 세 가지 시퀀스 컨테이너 [deque 클래스](../standard-library/deque-class.md), [list 클래스](../standard-library/list-class.md) 또는 [vector 클래스](../standard-library/vector-class.md) 중 하나를 참조해야 합니다.

### <a name="example"></a>예제

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;
*backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a><a name="begin"></a> begin

지정된 컨테이너의 첫 번째 요소에 대한 반복기를 검색합니다.

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>매개 변수

*계속*\
컨테이너입니다.

*배열과*\
`Ty` 형식의 개체의 배열입니다.

### <a name="return-value"></a>반환 값

첫 번째 두 템플릿 함수에서 `cont.begin()`을 반환합니다. 첫 번째 함수는 비상수이고, 두 번째는 상수입니다.

세 번째 템플릿 함수는 *배열을* 반환 합니다.

### <a name="example"></a>예제

제네릭 동작이 더 필요할 경우 컨테이너 멤버 `begin()` 대신 이 템플릿 함수를 사용하는 것이 좋습니다.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

이 함수 `reverse_sort`는 비멤버 버전 `begin()`을 호출하므로 정기 배열 이외에 모든 종류의 컨테이너를 지원합니다. `reverse_sort`를 코딩하여 컨테이너 멤버 `begin()`을 사용할 경우

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

그런 다음 여기에 배열을 전송하면 이 컴파일러 오류가 발생합니다.

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

지정된 컨테이너의 첫 번째 요소에 대한 상수 반복기를 검색합니다.

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>매개 변수

*계속*\
컨테이너 또는 initializer_list입니다.

### <a name="return-value"></a>반환 값

상수 `cont.begin()`입니다.

### <a name="remarks"></a>설명

이 함수는 모든 C++ 표준 라이브러리 컨테이너와 [initializer_list](../standard-library/initializer-list-class.md)에서 작동합니다.

`begin()` 템플릿 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 를 수정 가능 (비 **`const`** ) 컨테이너 또는 `initializer_list` 및을 지 원하는 모든 종류의로 간주 `begin()` 합니다 `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

지정된 컨테이너에서 마지막 요소 다음에 있는 요소에 대한 상수 반복기를 검색합니다.

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>매개 변수

*계속*\
컨테이너 또는 initializer_list입니다.

### <a name="return-value"></a>반환 값

상수 `cont.end()`입니다.

### <a name="remarks"></a>설명

이 함수는 모든 C++ 표준 라이브러리 컨테이너와 [initializer_list](../standard-library/initializer-list-class.md)에서 작동합니다.

[end()](../standard-library/iterator-functions.md#end) 템플릿 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 를 수정 가능 (비 **`const`** ) 컨테이너 또는 `initializer_list` 및을 지 원하는 모든 종류의로 간주 `end()` 합니다 `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

```cpp
template <class C> constexpr auto crbegin(const C& c) -> decltype(std::rbegin(c));
```

## <a name="crend"></a><a name="crend"></a> crend

```cpp
template <class C> constexpr auto crend(const C& c) -> decltype(std::rend(c));
```

## <a name="data"></a><a name="data"></a> 데이터

```cpp
template <class C> constexpr auto data(C& c) -> decltype(c.data());
template <class C> constexpr auto data(const C& c) -> decltype(c.data());
template <class T, size_t N> constexpr T* data(T (&array)[N]) noexcept;
template <class E> constexpr const E* data(initializer_list<E> il) noexcept;
```

## <a name="distance"></a><a name="distance"></a> 거리

두 반복기에 의해 주소가 지정된 위치 사이의 간격의 수를 결정합니다.

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>매개 변수

*기본*\
두 번째로부터의 거리를 결정해야 하는 첫 번째 반복기입니다.

*최신*\
첫 번째로부터의 거리를 결정해야 하는 두 번째 반복기입니다.

### <a name="return-value"></a>반환 값

*마지막으로* 같을 때까지 *먼저* 증가 해야 하는 횟수입니다.

### <a name="remarks"></a>설명

Distance 함수는가 임의 액세스 반복기의 요구 사항을 충족 하는 경우 일관 된 복잡성을 갖습니다 `InputIterator` . 그렇지 않으면 선형 복잡성이 있으므로 잠재적으로 비용이 많이 듭니다.

### <a name="example"></a>예제

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="empty"></a><a name="empty"></a> 비우려면

```cpp
template <class C> constexpr auto empty(const C& c) -> decltype(c.empty());
template <class T, size_t N> constexpr bool empty(const T (&array)[N]) noexcept;
template <class E> constexpr bool empty(initializer_list<E> il) noexcept;
```

## <a name="end"></a><a name="end"></a> end

지정된 컨테이너에서 마지막 요소 다음의 요소에 대한 반복기를 검색합니다.

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>매개 변수

*계속*\
컨테이너입니다.

*배열과*\
`Ty` 형식의 개체의 배열입니다.

### <a name="return-value"></a>반환 값

첫 번째 두 템플릿 함수는 `cont.end()`를 반환합니다(첫 번째 함수는 비상수이며, 두 번째 함수는 상수임).

세 번째 템플릿 함수는 `array + Size`를 반환합니다.

### <a name="remarks"></a>설명

코드 예제는 [begin](../standard-library/iterator-functions.md#begin)을 참조하세요.

## <a name="front_inserter"></a><a name="front_inserter"></a> front_inserter

지정된 컨테이너 앞에 요소를 삽입할 수 있는 반복기를 만듭니다.

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>매개 변수

*_Cont*\
앞에 요소를 삽입할 컨테이너 개체입니다.

### <a name="return-value"></a>반환 값

`front_insert_iterator`컨테이너 개체와 연결 된 *_Cont* 입니다.

### <a name="remarks"></a>설명

front_insert_iterator 클래스의 멤버 함수 [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator)를 사용할 수도 있습니다.

C++ 표준 라이브러리 내에서 인수는 `push_back` 멤버 함수가 있는 두 가지 시퀀스 컨테이너 [deque 클래스](../standard-library/deque-class.md) 또는 "list 클래스" 중 하나를 참조해야 합니다.

### <a name="example"></a>예제

```cpp
// iterator_front_inserter.cpp
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
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
*Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a><a name="inserter"></a> 삽입기

대신를 사용할 수 있도록 하는 도우미 템플릿 함수입니다 `inserter(_Cont, _Where)` `insert_iterator<Container>(_Cont, _Where)` .

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>매개 변수

*_Cont*\
새 요소를 추가할 컨테이너입니다.

*_Where*\
삽입 지점을 찾고 있는 반복기입니다.

### <a name="remarks"></a>설명

템플릿 함수는 [insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator)를 반환 합니다 `<Container>(_Cont, _Where)` .

### <a name="example"></a>예제

```cpp
// iterator_inserter.cpp
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
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
*Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( 20 30 40 ).
After the insertions, the list L is:
( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a><a name="make_checked_array_iterator"></a> make_checked_array_iterator

다른 알고리즘에서 사용할 수 있는 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)를 만듭니다.

> [!NOTE]
> 이 함수는 C++ 표준 라이브러리의 Microsoft 확장입니다. 이 함수를 사용하여 구현한 코드는 이 Microsoft 확장을 지원하지 않는 C++ 표준 빌드 환경으로 이식할 수 없습니다.

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>매개 변수

*Ptr*\
대상 배열에 대한 포인터입니다.

*크기가*\
대상 배열의 크기입니다.

*인덱싱할*\
배열에 대한 선택적 크기입니다.

### <a name="return-value"></a>반환 값

`checked_array_iterator`의 인스턴스입니다.

### <a name="remarks"></a>설명

`make_checked_array_iterator` 함수는 `stdext` 네임스페이스에 정의되어 있습니다.

이 함수는 원시 포인터를 사용하며, 경계를 벗어나 확인하지 않는 [checked_array_iterator](../standard-library/checked-array-iterator-class.md) 클래스로 래핑되는 경우가 일반적입니다. 해당 클래스는 확인된 것으로 표시되기 때문에 C++ 표준 라이브러리에서 그에 대해 경고하지 않습니다. 자세한 내용과 코드 예제는 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

다음 예제에서는 [벡터](../standard-library/vector-class.md)를 만들고 10개 항목으로 채웁니다. 벡터 콘텐츠는 복사 알고리즘을 사용하여 배열로 복사된 다음, `make_checked_array_iterator`를 사용하여 대상을 지정합니다. 그러면 디버그 어설션 실패를 트리거할 수 있도록 고의적 경계 위반 확인을 수행합니다.

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}
```

## <a name="make_move_iterator"></a><a name="make_move_iterator"></a> make_move_iterator

제공된 반복기를 `stored` 반복기로 포함하는 `move iterator`를 만듭니다.

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>매개 변수

*_It*\
새 이동 반복기에 저장되는 반복기입니다.

### <a name="remarks"></a>설명

템플릿 함수가 `move_iterator` `<Iterator>(_It)`을 반환합니다.

## <a name="make_unchecked_array_iterator"></a><a name="make_unchecked_array_iterator"></a> make_unchecked_array_iterator

다른 알고리즘에서 사용할 수 있는 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)를 만듭니다.

> [!NOTE]
> 이 함수는 C++ 표준 라이브러리의 Microsoft 확장입니다. 이 함수를 사용하여 구현한 코드는 이 Microsoft 확장을 지원하지 않는 C++ 표준 빌드 환경으로 이식할 수 없습니다.

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>매개 변수

*Ptr*\
대상 배열에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

`unchecked_array_iterator`의 인스턴스입니다.

### <a name="remarks"></a>설명

`make_unchecked_array_iterator` 함수는 `stdext` 네임스페이스에 정의되어 있습니다.

이 함수는 원시 포인터를 사용하고 확인을 수행하지 않는 클래스에서 래핑되어 최적화 대상이 없지만, [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 등의 컴파일러 경고도 해제합니다. 따라서 이 방법은 경고를 전체적으로 해제하거나 확인 비용 없이 확인하지 않은 포인터 경고를 처리할 수 있는 계획적 방법입니다. 자세한 내용과 코드 예제는 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

다음 예제에서는 [벡터](../standard-library/vector-class.md)를 만들고 10개 항목으로 채웁니다. 벡터 콘텐츠는 복사 알고리즘을 사용하여 배열로 복사된 다음, `make_unchecked_array_iterator`를 사용하여 대상을 지정합니다.

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}
```

## <a name="next"></a><a name="next"></a> 그런

지정된 횟수만큼 반복하고 새 반복기 위치를 반환합니다.

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>매개 변수

*기본*\
현재 위치입니다.

*_Off*\
반복할 횟수입니다.

### <a name="return-value"></a>반환 값

*_Off* 시간을 반복한 후 새 반복기 위치를 반환 합니다.

### <a name="remarks"></a>설명

템플릿 함수는 `next` 증가 된 *_Off* 시간을 반환 합니다.

## <a name="prev"></a><a name="prev"></a> 이전

역순으로 지정된 횟수만큼 반복하고 새 반복기 위치를 반환합니다.

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>매개 변수

*기본*\
현재 위치입니다.

*_Off*\
반복할 횟수입니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 `off`번 감소된 `next`를 반환합니다.

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

```cpp
template <class C> constexpr auto rbegin(C& c) -> decltype(c.rbegin());
template <class C> constexpr auto rbegin(const C& c) -> decltype(c.rbegin());
```

## <a name="rend"></a><a name="rend"></a> rend

```cpp
template <class C> constexpr auto rend(C& c) -> decltype(c.rend());
template <class C> constexpr auto rend(const C& c) -> decltype(c.rend());
```

## <a name="size"></a><a name="size"></a> 크기가

```cpp
template <class C> constexpr auto size(const C& c) -> decltype(c.size());
template <class T, size_t N> constexpr size_t size(const T (&array)[N]) noexcept;
```
