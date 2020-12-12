---
description: '다음에 대 한 자세한 정보: iterator_traits 구조체'
title: iterator_traits 구조체
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator_traits
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
ms.openlocfilehash: ac97b84ff7bcedc00f2b069ce05f734ac65618ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289683"
---
# <a name="iterator_traits-struct"></a>iterator_traits 구조체

반복기에 포함되어야 하는 모든 중요한 형식 정의를 지정하는 데 사용되는 템플릿 도우미 구조체입니다.

## <a name="syntax"></a>구문

```cpp
struct iterator_traits {
   typedef typename Iterator::iterator_category iterator_category;
   typedef typename Iterator::value_type value_type;
   typedef typename Iterator::difference_type difference_type;
   typedef difference_type distance_type;
   typedef typename Iterator::pointer pointer;
   typedef typename Iterator::reference reference;
   };
```

## <a name="remarks"></a>설명

이 템플릿 구조체는 멤버 형식을 정의합니다.

- `iterator_category`:의 동의어 `Iterator::iterator_category` 입니다.

- `value_type`:의 동의어 `Iterator::value_type` 입니다.

- `difference_type`:의 동의어 `Iterator::difference_type` 입니다.

- `distance_type`:의 동의어 `Iterator::difference_type.`

- `pointer`:의 동의어 `Iterator::pointer` 입니다.

- `reference`:의 동의어 `Iterator::reference` 입니다.

부분 특수화 **는 형식** <strong>\*</strong> 또는 **const 형식의** 개체 포인터와 관련 된 중요 한 형식을 결정 합니다 <strong>\*</strong> .

이 구현에서는 부분 특수화를 사용하지 않는 여러 가지 템플릿 함수를 사용할 수도 있습니다.

```cpp
template <class Category, class Type, class Diff>
C _Iter_cat(const iterator<Category, Ty, Diff>&);

template <class Ty>
random_access_iterator_tag _Iter_cat(const Ty *);

template <class Category, class Ty, class Diff>
Ty *val_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
Ty *val_type(const Ty *);

template <class Category, class Ty, class Diff>
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
ptrdiff_t *_Dist_type(const Ty *);
```

이러한 함수는 여러 가지 동일한 형식을 보다 간접적으로 결정합니다. 함수 호출에서 인수로 이러한 함수를 사용합니다. 유일한 용도는 호출 된 함수에 유용한 클래스 템플릿 매개 변수를 제공 하는 것입니다.

## <a name="example"></a>예제

```cpp
// iterator_traits.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <vector>
#include <list>

using namespace std;

template< class it >
void
function( it i1, it i2 )
{
   iterator_traits<it>::iterator_category cat;
   cout << typeid( cat ).name( ) << endl;
   while ( i1 != i2 )
   {
      iterator_traits<it>::value_type x;
      x = *i1;
      cout << x << " ";
      i1++;
   };
   cout << endl;
};

int main( )
{
   vector<char> vc( 10,'a' );
   list<int> li( 10 );
   function( vc.begin( ), vc.end( ) );
   function( li.begin( ), li.end( ) );
}
/* Output:
struct std::random_access_iterator_tag
a a a a a a a a a a
struct std::bidirectional_iterator_tag
0 0 0 0 0 0 0 0 0 0
*/
```

## <a name="requirements"></a>요구 사항

**헤더:**\<iterator>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[\<iterator>](../standard-library/iterator.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
