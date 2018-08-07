---
title: '&lt;algorithm&gt; 함수 | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
dev_langs:
- C++
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.workload:
- cplusplus
ms.openlocfilehash: d905c8208bef98d584d3052c242de1ac127a4830
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209302"
---
# <a name="ltalgorithmgt-functions"></a>&lt;algorithm&gt; 함수

||||
|-|-|-|
|[move](#alg_move)|[adjacent_find](#adjacent_find)|[all_of](#all_of)|
|[any_of](#any_of)|[binary_search](#binary_search)|[copy](#copy)|
|[copy_backward](#copy_backward)|[copy_if](#copy_if)|[copy_n](#copy_n)|
|[count](#count)|[count_if](#count_if)|[equal](#equal)|
|[equal_range](#equal_range)|[fill](#fill)|[fill_n](#fill_n)|
|[find](#find)|[find_end](#find_end)|[find_first_of](#find_first_of)|
|[find_if](#find_if)|[find_if_not](#find_if_not)|[for_each](#for_each)|
|[generate](#generate)|[generate_n](#generate_n)|[includes](#includes)|
|[inplace_merge](#inplace_merge)|[is_heap](#is_heap)|[is_heap_until](#is_heap_until)|
|[is_partitioned](#is_partitioned)|[is_permutation](#is_permutation)|[is_sorted](#is_sorted)|
|[is_sorted_until](#is_sorted_until)|[iter_swap](#iter_swap)|[lexicographical_compare](#lexicographical_compare)|
|[lower_bound](#lower_bound)|[make_heap](#make_heap)|[max](#max)|
|[max_element](#max_element)|[merge](#merge)|[분](#min)|
|[min_element](#min_element)|[minmax](#minmax)|[minmax_element](#minmax_element)|
|[mismatch](#mismatch)|[move_backward](#move_backward)|[next_permutation](#next_permutation)|
|[none_of](#none_of)|[nth_element](#nth_element)|[partial_sort](#partial_sort)|
|[partial_sort_copy](#partial_sort_copy)|[partition](#partition)|[partition_copy](#partition_copy)|
|[partition_point](#partition_point)|[pop_heap](#pop_heap)|[prev_permutation](#prev_permutation)|
|[push_heap](#push_heap)|[random_shuffle](#random_shuffle)|[remove](#remove)|
|[remove_copy](#remove_copy)|[remove_copy_if](#remove_copy_if)|[remove_if](#remove_if)|
|[replace](#replace)|[replace_copy](#replace_copy)|[replace_copy_if](#replace_copy_if)|
|[replace_if](#replace_if)|[reverse](#reverse)|[reverse_copy](#reverse_copy)|
|[rotate](#rotate)|[rotate_copy](#rotate_copy)|[search](#search)|
|[search_n](#search_n)|[set_difference](#set_difference)|[set_intersection](#set_intersection)|
|[set_symmetric_difference](#set_symmetric_difference)|[set_union](#set_union)|[sort](#sort)|
|[sort_heap](#sort_heap)|[stable_partition](#stable_partition)|[stable_sort](#stable_sort)|
|[shuffle](#shuffle)|[swap](#swap)|[swap_ranges](#swap_ranges)|
|[transform](#transform)|[unique](#unique)|[unique_copy](#unique_copy)|
|[upper_bound](#upper_bound)|

## <a name="adjacent_find"></a>  adjacent_find

같지 않거나 지정한 조건을 충족하는 인접 요소 두 개를 검색합니다.

```cpp
template<class ForwardIterator>
    ForwardIterator adjacent_find(
        ForwardIterator first,
        ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
    ForwardIterator adjacent_find(
        ForwardIterator first,
        ForwardIterator last,
        BinaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*comp* 검색 중인 범위에 있는 인접 요소의 값이 충족 되어야 하는 조건을 제공 하는 이진 조건자입니다.

### <a name="return-value"></a>반환 값

서로 같거나(첫 번째 버전) 이진 조건자가 지정한 조건을 충족하는(두 번째 버전) 인접 쌍의 첫 번째 요소에 대한 정방향 반복기입니다(해당 요소 쌍이 있는 경우). 그렇지 않으면를 가리키는 반복기 *마지막* 반환 됩니다.

### <a name="remarks"></a>설명

`adjacent_find` 알고리즘은 변경할 수 없는 시퀀스 알고리즘입니다. 검색할 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다. 알고리즘의 시간 복잡도는 범위에 포함된 요소 수에 비례합니다.

요소 간의 일치를 확인하는 데 사용되는 `operator==`는 피연산자 간에 동등 관계를 적용해야 합니다.

### <a name="example"></a>예

```cpp
// alg_adj_fnd.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

// Returns whether second element is twice the first
bool twice (int elem1, int elem2 )
{
   return elem1 * 2 == elem2;
}

int main()
{
   using namespace std;
   list <int> L;
   list <int>::iterator Iter;
   list <int>::iterator result1, result2;

   L.push_back( 50 );
   L.push_back( 40 );
   L.push_back( 10 );
   L.push_back( 20 );
   L.push_back( 20 );

   cout << "L = ( " ;
   for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )
      cout << *Iter << " ";
   cout << ")" << endl;

   result1 = adjacent_find( L.begin( ), L.end( ) );
   if ( result1 == L.end( ) )
      cout << "There are not two adjacent elements that are equal."
           << endl;
   else
      cout << "There are two adjacent elements that are equal."
           << "\n They have a value of "
           <<  *( result1 ) << "." << endl;

   result2 = adjacent_find( L.begin( ), L.end( ), twice );
   if ( result2 == L.end( ) )
      cout << "There are not two adjacent elements where the "
           << " second is twice the first." << endl;
   else
      cout << "There are two adjacent elements where "
           << "the second is twice the first."
           << "\n They have values of " << *(result2++);
      cout << " & " << *result2 << "." << endl;
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
 They have a value of 20.
There are two adjacent elements where the second is twice the first.
 They have values of 10 & 20.
```

## <a name="all_of"></a>  all_of

반환 **true** 조건이 지정된 된 범위에서 각 요소에 있는 경우.

```cpp
template<class InputIterator, class Predicate>
    bool all_of(
        InputIterator first,
        InputIterator last,
        BinaryPredicatecomp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 조건 검사의 시작 위치를 나타내는 입력된 반복기입니다. 반복기는 요소 범위의 시작 위치를 표시합니다.

*마지막* 조건을 검사할 요소 범위의 끝을 나타내는 입력된 반복기입니다.

*comp* 를 테스트할 조건입니다. 확인 중인 요소가 충족할 조건을 정의하는 사용자 정의 조건자 함수 개체입니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

반환 **true** 표시 된 범위에서 각 요소에는 조건이 발견 되 고 **false** 조건이 한 번 이상 검색 되지 않은 경우.

### <a name="remarks"></a>설명

템플릿 함수가 반환 하 **true** 각각에 대 한 경우에만 `N` 범위의 `[0,Last - first)`, 조건자 `comp(*(_First + N))` 됩니다 **true**합니다.

## <a name="any_of"></a>  any_of

반환 **true** 조건이 지정 된 범위의 요소에 한 번 이상 있는 경우.

```cpp
template<class InputIterator, class UnaryPredicate>
    bool any_of(
        InputIterator first,
        InputIterator last,
        UnaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소를 조건에 대해 범위 검사를 시작 하는 위치를 나타내는 입력된 반복기입니다.

*마지막* 조건을 검사할 요소 범위의 끝을 나타내는 입력된 반복기입니다.

*comp* 를 테스트할 조건입니다. 사용자 정의 조건자 함수 개체에 의해 제공됩니다. 조건자는 테스트 중인 요소가 충족해야 할 조건을 정의합니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

반환 **true** 표시 된 범위에서 조건이 한 번 이상 감지 되 면 **false** 조건이 전혀 검색 되지 경우.

### <a name="remarks"></a>설명

템플릿 함수 **true** 일부 경우에만 `N` 범위

`[0, last - first)`조건자 `comp(*(first + N))` 그렇습니다.

## <a name="binary_search"></a>  binary_search

정렬된 범위에 지정된 값과 같거나 이진 조건자가 지정한 의미에 따라 지정된 값과 같은 요소가 있는지 여부를 테스트합니다.

```cpp
template<class ForwardIterator, class Type>
    bool binary_search(
        ForwardIterator first,
        ForwardIterator last,
        const Type& value);

template<class ForwardIterator,  class Type,  class BinaryPredicate>
    bool binary_search(
        ForwardIterator first,
        ForwardIterator last,
        const Type& value,
        BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*값* 값 또는 요소 값을 기준으로 일치 하는 데 필요한 요소 값이 이진 조건자에 의해 지정 된 조건을 충족 해야 합니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

**true 이면** 요소가 같으면 또는 고, 그렇지 않으면 지정 된 값에 해당 하는 범위에 있으면 **false**합니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

정렬된 범위는 각각 `binary_search` 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다.

소스 범위는 `binary_search`에 의해 수정되지 않습니다.

정방향 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 등가이거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 비등가 요소 사이에 정렬이 수행됩니다.

알고리즘의 복잡성은 임의 액세스 반복기에 대 한 로그 및 선형 비례 하는 단계 수 이며 그렇지 않은 경우 (`last` - `first`).

### <a name="example"></a>예

```cpp
// alg_bin_srch.cpp
// compile with: /EHsc
#include <list>
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main( )
{
    using namespace std;

    list <int> List1;

    List1.push_back( 50 );
    List1.push_back( 10 );
    List1.push_back( 30 );
    List1.push_back( 20 );
    List1.push_back( 25 );
    List1.push_back( 5 );

    List1.sort();

    cout << "List1 = ( " ;
    for ( auto Iter : List1 )
        cout << Iter << " ";
    cout << ")" << endl;

    // default binary search for 10
    if( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

## <a name="copy"></a>  copy

소스 범위의 요소를 대상 범위에 할당하여 요소의 소스 시퀀스 전체에서 반복하고 정방향으로 새 위치를 할당합니다.

```cpp
template<class InputIterator, class OutputIterator>
    OutputIterator copy(
        InputIterator first,
        InputIterator last,
        OutputIterator destBeg);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 소스 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 입력된 반복기입니다.

*destBeg* 대상 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

### <a name="return-value"></a>반환 값

즉, 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 출력 반복기, 반복기 주소 `result` + (*마지막* - *첫 번째*).

### <a name="remarks"></a>설명

소스 범위는 유효해야 하며 대상에서 복사할 모든 요소를 보관할 충분한 공간이 있어야 합니다.

대상 범위가 소스 범위와 겹칠 수 있습니다부터 시작 하는 첫 번째 요소를 사용 하 여 소스 요소를 복사 하는 알고리즘을 하기 때문에 합니다 *마지막* 소스 범위의 위치 대상에 포함 되지 않습니다 범위입니다. `copy` 원본 및 대상 범위가 겹치지 않는 경우 오른쪽이 아니라 왼쪽으로 요소를 이동 하려면 사용할 수 있습니다. 여러 위치를 오른쪽으로 이동하려면 [copy_backward](../standard-library/algorithm-functions.md#copy_backward) 알고리즘을 사용합니다.

이 `copy` 알고리즘은 반복기가 가리키는 값만 수정하며 대상 범위에 있는 요소에 새로운 값을 할당합니다. 새 요소를 만드는 데 사용할 수 없고 빈 컨테이너에 요소를 직접 삽입할 수 없습니다.

### <a name="example"></a>예

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1.push_back( 10 * i );

   int ii;
   for ( ii = 0 ; ii <= 10 ; ii++ )
      v2.push_back( 3 * ii );

   cout << "v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To copy the first 3 elements of v1 into the middle of v2
   copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );

   cout << "v2 with v1 insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To shift the elements inserted into v2 two positions
   // to the left
   copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );

   cout << "v2 with shifted insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )
```

## <a name="copy_backward"></a>  copy_backward

소스 범위의 요소를 대상 범위에 할당하여 요소의 소스 시퀀스 전체에서 반복하고 역방향으로 새 위치를 할당합니다.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
    BidirectionalIterator2 copy_backward(
        BidirectionalIterator1 first,
        BidirectionalIterator1 last,
        BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 양방향 반복기입니다.

*마지막* 소스 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 양방향 반복기입니다.

*destEnd* 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 양방향 반복기입니다.

### <a name="return-value"></a>반환 값

즉, 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 출력 반복기, 반복기 주소 *destEnd* -(*마지막* - *첫번째*).

### <a name="remarks"></a>설명

소스 범위는 유효해야 하며 대상에서 복사할 모든 요소를 보관할 충분한 공간이 있어야 합니다.

이 `copy_backward` 알고리즘은 복사 알고리즘보다 요구 사항이 더 엄격합니다. 입력 및 출력 반복기가 모두 양방향입니다.

`copy_backward` 및 [move_backward](../standard-library/algorithm-functions.md#move_backward) 알고리즘은 대상 범위의 끝 부분을 가리키는 반복기를 사용하여 출력 범위를 지정하는 유일한 C++ 표준 라이브러리 알고리즘입니다.

대상 범위가 소스 범위와 겹칠 수 있습니다부터 시작 하는 마지막 요소를 사용 하 여 소스 요소를 복사 하는 알고리즘을 하기 때문에 합니다 *첫 번째* 소스 범위의 위치 대상에 포함 되지 않습니다 범위입니다. `copy_backward`는 소스와 대상 범위가 겹치지 않는 한 왼쪽이 아닌 오른쪽으로 요소를 이동하는 데 사용할 수 있습니다. 여러 위치를 왼쪽으로 이동하려면, [복사](../standard-library/algorithm-functions.md#copy) 알고리즘을 사용합니다.

이 `copy_backward` 알고리즘은 반복기가 가리키는 값만 수정하며 대상 범위에 있는 요소에 새로운 값을 할당합니다. 새 요소를 만드는 데 사용할 수 없고 빈 컨테이너에 요소를 직접 삽입할 수 없습니다.

### <a name="example"></a>예

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 5 ; ++i )
      v1.push_back( 10 * i );

   int ii;
   for ( ii = 0 ; ii <= 10 ; ++ii )
      v2.push_back( 3 * ii );

   cout << "v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To copy_backward the first 3 elements of v1 into the middle of v2
   copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );

   cout << "v2 with v1 insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To shift the elements inserted into v2 two positions
   // to the right
   copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );

   cout << "v2 with shifted insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;
}
```

## <a name="copy_if"></a>  copy_if

요소 범위에 있는 요소에 복사 **true** 지정된 된 조건에 대 한 합니다.

```cpp
template<class InputIterator, class OutputIterator, class BinaryPredicate>
    OutputIterator copy_if(
        InputIterator first,
        InputIterator last,
        OutputIterator dest,
        Predicate pred);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 조건을 검사할 범위의 시작을 나타내는 입력된 반복기입니다.

*마지막* 범위의 끝을 나타내는 입력된 반복기입니다.

*dest* 복사 된 요소에 대 한 대상을 나타내는 출력 반복기입니다.

*_Pred* 범위에 있는 모든 요소가 테스트 되는 조건입니다. 이 조건은 사용자 정의 조건자 함수 개체에 의해 제공됩니다. 조건자는 하나의 인수를 반환 **true** 하거나 **false**합니다.

### <a name="return-value"></a>반환 값

해당 하는 출력 반복기 *dest* 조건을 충족 하는 각 요소에 대해 한 번씩 증가 합니다. 즉, 반환 값에서 뺀 *dest* 복사 된 요소의 수와 같습니다.

### <a name="remarks"></a>설명

템플릿 함수는

`if (_Pred(*_First + N)) * dest++ = *(_First + N))`

`[0, last - first)` 범위의 각 `N`에 대해 위의 식을 한 번 평가하고, 가장 낮은 값부터 시작하여 `N`의 값을 최소값부터 엄격하게 증가시킵니다. 하는 경우 *dest* 하 고 *첫 번째* 저장소, 영역을 지정 *dest* 범위에 없어야 `[ first, last )`합니다.

## <a name="copy_n"></a>  copy_n

지정된 수의 요소를 복사합니다.

```cpp
template<class InputIterator, class Size, class OutputIterator>
    OutputIterator copy_n(
        InputIterator first,
        Size count,
        OutputIterator dest);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소를 복사할 원본 위치를 나타내는 입력된 반복기입니다.

*개수* 는 부호가 있거나 복사할 요소의 수를 지정 정수 형식입니다.

*dest* 요소를 복사할 위치를 나타내는 출력 반복기입니다.

### <a name="return-value"></a>반환 값

요소가 복사된 출력 반복기를 반환합니다. 세 번째 매개 변수, 반환된 된 값과 동일 *dest*합니다.

### <a name="remarks"></a>설명

템플릿 함수는 `*(dest + N) = *(first + N))` 마다 한 번씩 `N` 범위의 `[0, count)`, 엄격 하 게 값을 높이기 위한 `N` 가장 낮은 값을 사용 하 여 시작 합니다. 그런 다음 `dest + N`를 반환합니다. 하는 경우 *dest* 하 고 *첫 번째* 저장소, 영역을 지정 *dest* 범위에 없어야 `[first, last)`합니다.

## <a name="count"></a>  count

해당 값이 지정된 값과 일치하는 요소의 개수를 반환합니다.

```cpp
template<class InputIterator, class Type>
    typename iterator_traits<InputIterator>::difference_type count(
        InputIterator first,
        InputIterator last,
        const Type& val);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 트래버스할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 트래버스할 하나 다음 위치의 마지막 요소 범위에서를 지정 하는 입력된 반복기입니다.

*val* 계산할 요소의 값입니다.

### <a name="return-value"></a>반환 값

차이 유형 합니다 `InputIterator` 범위의 요소 수를 계산 하는 [ *첫 번째*, *마지막* ) 값을 갖는 *val*.

### <a name="remarks"></a>설명

요소와 지정된 값 간의 일치 여부를 확인하는 데 사용되는 `operator==`로서, 피연산자 간에 동등 관계를 적용해야 합니다.

이 알고리즘은 템플릿 함수 [count_if](../standard-library/algorithm-functions.md#count_if)가 포함된 모든 조건자를 충족하는 요소를 계산하기 위해 일반화됩니다.

### <a name="example"></a>예

```cpp
// alg_count.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result;
    result = count(v1.begin(), v1.end(), 10);
    cout << "The number of 10s in v2 is: " << result << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of 10s in v2 is: 3.
```

## <a name="count_if"></a>  count_if

범위 내에서 해당 값이 지정된 조건과 일치하는 요소의 개수를 반환합니다.

```cpp
template<class InputIterator, class Predicate>
    typename iterator_traits<InputIterator>::difference_type count_if(
        InputIterator first,
        InputIterator last,
        Predicate pred);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 검색할 하나 다음 위치의 마지막 요소 범위에서를 지정 하는 입력된 반복기입니다.

*_Pred* 개수를 셀 요소가 충족할 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

조건자로 지정된 조건과 일치하는 요소의 개수.

### <a name="remarks"></a>설명

이 템플릿 함수는 "지정한 값과 일치" 조건자를 다른 임의의 조건자로 교체하는 방식으로 [count](../standard-library/algorithm-functions.md#count) 알고리즘을 일반화한 것입니다.

### <a name="example"></a>예

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value >10;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greater10);
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of elements in v1 greater than 10 is: 2.
```

## <a name="equal"></a>  equal

두 범위를 요소별로 비교하여 같음 여부 또는 이진 조건자가 지정한 의미의 동등성을 확인합니다.

서로 다른 컨테이너 형식(예: `vector` 및 `list`)에서 요소를 비교하는 경우, 다른 요소 형식을 비교하는 경우 또는 컨테이너의 하위 범위를 비교해야 하는 경우 `std::equal`을 사용합니다. 그렇지 않고 같은 컨테이너 형식에서 같은 형식의 요소를 비교하는 경우에는 각 컨테이너에 제공되는 비 멤버 `operator==`를 사용합니다.

두 번째 범위에 단일 반복기만 사용하는 오버로드는 두 번째 범위가 첫 번째 범위보다 긴 경우 차이를 감지하지 못하고 두 번째 범위가 첫 번째 범위보다 짧은 경우 정의되지 않은 동작이 발생하므로 C++14 코드에서 이중 범위 오버로드를 사용합니다.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    BinaryPredicate Comp); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    InputIterator2  Last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    InputIterator2  Last2,
    BinaryPredicate Comp);
```

### <a name="parameters"></a>매개 변수

*First1* 테스트할 첫 번째 범위의 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*Last1* 테스트할 첫 번째 범위에서 마지막 요소의 하나의 위치를 지정 하는 입력된 반복기입니다.

*First2* 테스트할 두 번째 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*First2* 테스트할 두 번째 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 입력된 반복기입니다.

*Comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

요소별로 비교할 경우 범위가 이진 조건자에서 동일하거나 동등한 경우에만 **true**이고, 아닌 경우에는 **false**입니다.

### <a name="remarks"></a>설명

검색할 범위는 유효해야 하고 모든 반복기는 역참조 가능해야 하며 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

두 범위의 길이가 같은 경우 알고리즘의 시간 복잡도는 범위에 포함된 요소 수에 비례합니다. 그렇지 않은 경우 즉시 반환 **false**합니다.

피연산자 간에 대칭, 재귀 및 전이적인 동등 관계를 적용하려면 `operator==`나 사용자 정의 조건자 모두 필요하지 않습니다.

### <a name="example"></a>예

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };

    // Using range-and-a-half equal:
    bool b = equal(v1.begin(), v1.end(), v2.begin());
    cout << "v1 and v2 are equal: "
       << b << endl; // true, as expected

    b = equal(v1.begin(), v1.end(), v3.begin());
    cout << "v1 and v3 are equal: "
       << b << endl; // true, surprisingly

    // Using dual-range equal:
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());
    cout << "v1 and v3 are equal with dual-range overload: "
       << b << endl; // false

    return 0;
}

```

## <a name="equal_range"></a>  equal_range

정렬된 범위가 지정되면, 모든 요소가 지정된 값에 해당하는 하위 범위를 찾습니다.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val);

template<class ForwardIterator, class Type, class Predicate>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val,
    Predicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*val* 정렬된 된 범위에서 검색 되는 값입니다.

*comp* 는 하나의 요소가 다른 노드보다 작은지 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다.

### <a name="return-value"></a>반환 값

모든 요소에 해당 하는 앞으로 검색 된 범위 내에 포함 된 하위 범위를 지정 하는 반복기의 쌍 *val* 에서 사용 되는 이진 조건자에 의해 정의 된 의미 (하거나 *comp* 또는 기본값, less-보다).

범위의 요소가 해당 하는 경우 *val*, 정방향 반복기의 반환 된 쌍이 같은지 및 지점을 지정 위치 *val* 범위의 순서를 방해 하지 않고 삽입할 수 없습니다.

### <a name="remarks"></a>설명

알고리즘에 의해 반환된 쌍의 첫 번째 반복기는 [lower_bound](../standard-library/algorithm-functions.md#lower_bound), 두 번째 반복기는 [upper_bound](../standard-library/algorithm-functions.md#upper_bound)입니다.

`equal_range`에 제공된 조건자에 따라 범위를 정렬해야 합니다. 예를 들어, greater-than 조건자를 사용하려는 경우 범위를 내림차순으로 정렬해야 합니다.

반환 된 반복기의 쌍으로 정의 된 비어 있을 수 있는 하위 범위에 있는 요소 `equal_range` 에 해당 됩니다 *val* 에서 사용 되는 조건자에 정의 된 의미 합니다.

알고리즘의 복잡성은 임의 액세스 반복기에 대 한 로그 및 선형 비례 하는 단계 수 이며 그렇지 않은 경우 (*마지막* - *첫 번째*).

### <a name="example"></a>예

```cpp
// alg_equal_range.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>()
#include <iostream>
#include <string>
using namespace std;

template<class T> void dump_vector( const vector<T>& v, pair< typename vector<T>::iterator, typename vector<T>::iterator > range )
{
    // prints vector v with range delimited by [ and ]

    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if( i == range.first )
        {
            cout << "[ ";
        }
        if( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T val )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair< vector<T>::iterator, vector<T>::iterator > result
        = equal_range( v.begin(), v.end(), val );

    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T val, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair< typename vector<T>::iterator, typename vector<T>::iterator > result
        = equal_range( v.begin(), v.end(), val, pred );

    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

// Return whether absolute value of elem1 is less than absolute value of elem2
bool abs_lesser( int elem1, int elem2 )
{
    return abs(elem1) < abs(elem2);
}

// Return whether string l is shorter than string r
bool shorter_than(const string& l, const string& r)
{
    return l.size() < r.size();
}

int main()
{
    vector<int> v1;

    // Constructing vector v1 with default less than ordering
    for( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for( int i =-3; i <= 0; ++i )
    {
        v1.push_back( i );
    }

    equal_range_demo( v1, 3 );
    equal_range_demo( v1, 3, greater<int>(), "greater" );
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );

    vector<string> v2;

    v2.push_back("cute");
    v2.push_back("fluffy");
    v2.push_back("kittens");
    v2.push_back("fun");
    v2.push_back("meowmeowmeow");
    v2.push_back("blah");

    equal_range_demo<string>( v2, "fred" );
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );
}

```

## <a name="fill"></a>  fill

지정한 범위의 모든 요소에 동일한 새 값을 할당합니다.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 트래버스할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 트래버스할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*val* 범위의 요소에 할당할 값 [ *첫 번째*하십시오 *마지막*).

### <a name="remarks"></a>설명

대상 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다. 복잡성은 범위의 크기와 선형입니다.

### <a name="example"></a>예

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Fill the last 5 positions with a value of 2
   fill( v1.begin( ) + 5, v1.end( ), 2 );

   cout << "Modified v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )
```

## <a name="fill_n"></a>  fill_n

특정 요소로 시작하는 범위에서 지정된 개수의 요소에 새 값을 할당합니다.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator First,
    Size Count,
    const Type& Val);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기 값이 할당 됩니다 *Val*합니다.

*개수* 는 부호가 있거나 값을 할당할 요소의 수를 지정 정수 형식입니다.

*Val* 범위의 요소에 할당할 값 [ *첫 번째*하십시오 *First + Count*).

### <a name="return-value"></a>반환 값

마지막 요소 다음에 나오는 요소에 반복기 채워집니다 *개수* > 첫 번째 요소, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

대상 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다. 복잡성은 범위의 크기와 선형입니다.

### <a name="example"></a>예

```cpp
// alg_fill_n.cpp
// compile using /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector <int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << "  vector v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the first 3 positions with a value of 1, saving position.
    auto pos = fill_n( v.begin(), 3, 1 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the next 3 positions with a value of 2, using last position.
    fill_n( pos, 3, 2 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the last 3 positions with a value of 3, using relative math.
    fill_n( v.end()-3, 3, 3 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;
}

```

## <a name="find"></a>  find

범위에서 지정된 값을 가진 요소가 첫 번째로 나타나는 위치를 찾습니다.

```cpp
template<class InputIterator, class T>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const T& val);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 지정 된 값을 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 지정 된 값을 검색할 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 입력된 반복기입니다.

*val* 검색할 값입니다.

### <a name="return-value"></a>반환 값

검색 중인 범위 내에서 지정된 값이 처음 나타나는 위치의 주소를 지정하는 입력 반복기입니다. 해당 하는 값을 사용 하 여 요소가 없으면 반환 *마지막*합니다.

### <a name="remarks"></a>설명

요소와 지정된 값 간의 일치 여부를 확인하는 데 사용되는 `operator==`로서, 피연산자 간에 동등 관계를 적용해야 합니다.

`find()`를 사용하는 코드 예제를 보려면 [find_if](../standard-library/algorithm-functions.md#find_if)를 참조하세요.

## <a name="find_end"></a>  find_end

범위에서 지정된 시퀀스와 동일하거나 이진 조건자가 지정한 의미와 동일한 마지막 하위 시퀀스를 찾습니다.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2,
    Pred Comp);
```

### <a name="parameters"></a>매개 변수

*First1* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*Last1* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*First2* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*Last2* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*Comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

지정한 시퀀스 [First2, Last2)와 일치하는 [First1, Last1) 내의 마지막 하위 시퀀스의 첫 번째 요소 위치 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

요소와 지정된 값 간의 일치 여부를 확인하는 데 사용되는 `operator==`로서, 피연산자 간에 동등 관계를 적용해야 합니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

### <a name="example"></a>예

```cpp
// alg_find_end.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for a match to L1 under identity
   vector <int>::iterator result1;
   result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a match of L1 in v1 that begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent to those\n in v2 under the binary "
           << "predicate twice and that begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 5 10 15 20 )
Vector v2 = ( 20 30 40 )
There is a match of L1 in v1 that begins at position 7.
There is a sequence of elements in v1 that are equivalent to those
 in v2 under the binary predicate twice and that begins at position 8.
```

## <a name="find_first_of"></a>  find_first_of

대상 범위 내에서 여러 값이 첫 번째로 나타나는 경우 또는 이진 조건자가 지정한 의미에서 지정된 요소 집합과 동일한 여러 요소가 첫 번째로 나타나는 경우를 검색합니다.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1  first1,
    ForwardIterator1 Last1,
    ForwardIterator2  first2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1  first1,
    ForwardIterator1 Last1,
    ForwardIterator2  first2,
    ForwardIterator2 Last2,
    BinaryPredicate  comp);
```

### <a name="parameters"></a>매개 변수

*first1* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*last1* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*first2* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*last2* 일치 시킬 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

지정한 시퀀스와 일치하거나 이진 조건자가 지정한 사항에 따라 동일한 첫 번째 하위 시퀀스의 첫 번째 요소 위치 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

요소와 지정된 값 간의 일치 여부를 확인하는 데 사용되는 `operator==`로서, 피연산자 간에 동등 관계를 적용해야 합니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

### <a name="example"></a>예

```cpp
// alg_find_first_of.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 3 ; ii <= 4 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for first match to L1 under identity
   vector <int>::iterator result1;
   result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is at least one match of L1 in v1"
           << "\n and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent\n to those in v2 under the binary "
           << "predicate twice\n and the first one begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 15 20 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
 and the first one begins at position 3.
There is a sequence of elements in v1 that are equivalent
 to those in v2 under the binary predicate twice
 and the first one begins at position 2.
```

## <a name="find_if"></a>  find_if

범위에서 지정된 조건을 만족하는 요소가 첫 번째 나타나는 위치를 찾습니다.

```cpp
template<class InputIterator, class Predicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 검색할 하나 다음 위치의 마지막 요소 범위에서를 지정 하는 입력된 반복기입니다.

*pred* 사용자 정의 조건자 함수 개체 또는 [람다 식](../cpp/lambda-expressions-in-cpp.md) 검색 중인 요소가 충족할 조건을 정의 하는 합니다. 조건자는 단일 인수를 반환 **true** (충족) 또는 **false** (미 충족). 서명의 *pred* 여야 `bool pred(const T& arg);`여기서 `T` 형식에 `InputIterator` 역참조 시 암시적으로 변환 될 수 있습니다. 합니다 **const** 키워드는 함수 개체 또는 람다 인수를 수정 하지 않아야 함을 나타내기 위한 용도로 에게만 표시 됩니다.

### <a name="return-value"></a>반환 값

조건자에 지정 된 조건을 충족 하는 범위에서 첫 번째 요소를 가리키는 입력된 반복기 (조건자 **true**). 조건자를 충족 하기 위해 요소가 없으면 반환 *마지막*합니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 [find](../standard-library/algorithm-functions.md#find) 알고리즘을 일반화한 것으로, "equals a specific value" 조건자를 임의의 조건자로 바꿉니다. 이 조건자와 논리적으로 반대되는 항목(조건자를 충족하지 않는 첫 번째 요소를 찾음)은 [find_if_not](../standard-library/algorithm-functions.md#find_if_not)을 참조하세요.

### <a name="example"></a>예

```cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <vector>
#include <algorithm>
#include <iostream>
#include <string>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }
    cout << endl;
}

// Test std::find()
template <class InputIterator, class T>
void find_print_result(InputIterator first, InputIterator last, const T& value) {

    // call <algorithm> std::find()
    auto p = find(first, last, value);

    cout << "value " << value;
    if (p == last) {
        cout << " not found." << endl;
    } else {
        cout << " found." << endl;
    }
}

// Test std::find_if()
template <class InputIterator, class Predicate>
void find_if_print_result(InputIterator first, InputIterator last,
    Predicate Pred, const string& Str) {

    // call <algorithm> std::find_if()
    auto p = find_if(first, last, Pred);

    if (p == last) {
        cout << Str << " not found." << endl;
    } else {
        cout << "first " << Str << " found: " << *p << endl;
    }
}

// Function to use as the UnaryPredicate argument to find_if() in this example
bool is_odd_int(int i) {
    return ((i % 2) != 0);
}

int main()
{
    // Test using a plain old array.
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    cout << "array x[] contents: ";
    print(x);
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.
    cout << "Test std::find() with array..." << endl;
    find_print_result(begin(x), end(x), 10);
    find_print_result(begin(x), end(x), 42);
    cout << "Test std::find_if() with array..." << endl;
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name
    find_if_print_result(begin(x), end(x), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");

    // Test using a vector.
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back((i + 1) * 10);
    }
    cout << endl << "vector v contents: ";
    print(v);
    cout << "Test std::find() with vector..." << endl;
    find_print_result(v.begin(), v.end(), 20);
    find_print_result(v.begin(), v.end(), 12);
    cout << "Test std::find_if() with vector..." << endl;
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");
    find_if_print_result(v.begin(), v.end(), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");
}

```

## <a name="find_if_not"></a>  find_if_not

표시된 범위에서 조건을 충족하지 않는 첫 번째 요소를 반환합니다.

```cpp
template<class InputIterator, class Predicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 검색할 하나 다음 위치의 마지막 요소 범위에서를 지정 하는 입력된 반복기입니다.

*pred* 사용자 정의 조건자 함수 개체 또는 [람다 식](../cpp/lambda-expressions-in-cpp.md) 검색 중인 요소가 충족 하지 않는 조건을 정의 하는 합니다. 조건자는 단일 인수를 반환 **true** (충족) 또는 **false** (미 충족). 서명의 *pred* 여야 `bool pred(const T& arg);`여기서 `T` 형식에 `InputIterator` 역참조 시 암시적으로 변환 될 수 있습니다. 합니다 **const** 키워드는 함수 개체 또는 람다 인수를 수정 하지 않아야 함을 나타내기 위한 용도로 에게만 표시 됩니다.

### <a name="return-value"></a>반환 값

조건자에 지정 된 조건을 충족 하지 않는 범위에서 첫 번째 요소를 가리키는 입력된 반복기 (조건자 **false**). 모든 요소가 조건자를 만족 하는 경우 (조건자 **true** 모든 요소에 대해)을 반환 *마지막*합니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 [find](../standard-library/algorithm-functions.md#find) 알고리즘을 일반화한 것으로, "equals a specific value" 조건자를 임의의 조건자로 바꿉니다. 이 조건자와 논리적으로 반대되는 항목(조건자를 충족하는 첫 번째 요소를 찾음)은 [find_if](../standard-library/algorithm-functions.md#find_if)를 참조하세요.

`find_if_not()`에 맞게 즉시 조정 가능한 코드 예제는 [find_if](../standard-library/algorithm-functions.md#find_if)를 참조하세요.

## <a name="for_each"></a>  for_each

범위 내에서 정방향으로 각 요소에 지정된 함수 개체를 적용하고 함수 개체를 반환합니다.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function _Func);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 작업을 수행할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 하나 다음 위치의 마지막 요소 범위에서 지정 하는 입력된 반복기에 연산을 수행 합니다.

*_Func* 범위의 각 요소에 적용 되는 사용자 정의 함수 개체입니다.

### <a name="return-value"></a>반환 값

범위에서 모든 요소에 적용된 후 함수 개체의 복사본입니다.

### <a name="remarks"></a>설명

`for_each` 알고리즘은 매우 유연하여, 사용자가 지정한 서로 다른 방법으로 범위 내에서 각 요소를 수정할 수 있습니다. 서로 다른 매개 변수를 전달하여 템플릿화된 함수를 수정된 형식으로 다시 사용할 수 있습니다. 사용자 정의 함수는 범위의 모든 요소를 처리한 후 알고리즘이 반환할 수 있는 내부 상태 내에서 정보를 누적할 수 있습니다.

참조된 범위는 유효해야 하며, 모든 포인터는 역참조 가능해야 하고 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 선형 이며 최대 ( *마지막* -  *첫 번째*) 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_for_each.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
   Type Factor;   // The value to multiply by
public:
   // Constructor initializes the value to multiply by
   MultValue ( const Type& val ) : Factor ( val ) {
   }

   // The function call for the element to be multiplied
   void operator ( ) ( Type& elem ) const
   {
      elem *= Factor;
   }
};

// The function object to determine the average
class Average
{
private:
   long num;      // The number of elements
   long sum;      // The sum of the elements
public:
   // Constructor initializes the value to multiply by
   Average ( ) : num ( 0 ) , sum ( 0 )
   {
   }

   // The function call to process the next elment
   void operator ( ) ( int elem ) \
   {
      num++;      // Increment the element count
      sum += elem;   // Add the value to the partial sum
   }

   // return Average
   operator double ( )
   {
      return  static_cast <double> (sum) /
      static_cast <double> (num);
   }
};

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   // Constructing vector v1
   int i;
   for ( i = -4 ; i <= 2 ; i++ )
   {
      v1.push_back(  i );
   }

   cout << "Original vector  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Using for_each to multiply each element by a Factor
   for_each ( v1.begin ( ) , v1.end ( ) , MultValue<int> ( -2 ) );

   cout << "Multiplying the elements of the vector v1\n "
        <<  "by the factor -2 gives:\n v1mod1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // The function object is templatized and so can be
   // used again on the elements with a different Factor
   for_each (v1.begin ( ) , v1.end ( ) , MultValue<int> (5 ) );

   cout << "Multiplying the elements of the vector v1mod\n "
        <<  "by the factor 5 gives:\n v1mod2 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // The local state of a function object can accumulate
   // information about a sequence of actions that the
   // return value can make available, here the Average
   double avemod2 = for_each ( v1.begin ( ) , v1.end ( ) ,
      Average ( ) );
   cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
        << avemod2 << "." << endl;
}
```

```Output
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
 by the factor -2 gives:
 v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
 by the factor 5 gives:
 v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
 Average ( v1mod2 ) = 10.
```

## <a name="generate"></a>  generate

범위에 있는 각 요소에 함수 개체에 의해 생성된 값을 할당합니다.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator _Gen);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 할당 되는 값 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 할당 되는 값 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 정방향 반복기입니다.

*_Gen* 각 범위에 있는 요소에 할당할 값을 생성 하는 데 사용 되는 인수 없이 호출 되는 함수 개체입니다.

### <a name="remarks"></a>설명

이 함수 개체는 범위 내 각 요소에 대해 호출되고 호출될 때마다 동일한 값을 반환할 필요가 없습니다. 예를 들어 파일에서 읽거나 로컬 상태를 참조 및 수정할 수 있습니다. 생성기의 결과 형식은 범위의 정방향 반복기 값 형식으로 변환할 수 있어야 합니다.

참조된 범위는 유효해야 하며, 모든 포인터는 역참조 가능해야 하고 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 선형 이며 정확히 ( `last`  -   `first`)에 필요한 생성기에 대 한 호출 합니다.

### <a name="example"></a>예

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main( )
{
   using namespace std;

   // Assigning random values to vector integer elements
   vector <int> v1 ( 5 );
   vector <int>::iterator Iter1;
   deque <int> deq1 ( 5 );
   deque <int>::iterator d1_Iter;

   generate ( v1.begin ( ), v1.end ( ) , rand );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Assigning random values to deque integer elements
   generate ( deq1.begin ( ), deq1.end ( ) , rand );

   cout << "Deque deq1 is ( " ;
   for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )
      cout << *d1_Iter << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 41 18467 6334 26500 19169 ).
Deque deq1 is ( 15724 11478 29358 26962 24464 ).
```

## <a name="generate_n"></a>  generate_n

함수 개체에 의해 생성된 값을 범위 내 지정된 수의 요소에 할당하고 마지막에 할당된 값 하나 다음의 위치로 반환합니다.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator First,
    Diff Count,
    Generator Gen);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 할당 되는 값 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

*개수* 는 부호가 있거나 생성기 함수를 통해 값을 할당할 요소의 수를 지정 정수 형식입니다.

*범용* 각 범위에 있는 요소에 할당할 값을 생성 하는 데 사용 되는 인수 없이 호출 되는 함수 개체입니다.

### <a name="remarks"></a>설명

이 함수 개체는 범위 내 각 요소에 대해 호출되고 호출될 때마다 동일한 값을 반환할 필요가 없습니다. 예를 들어 파일에서 읽거나 로컬 상태를 참조 및 수정할 수 있습니다. 생성기의 결과 형식은 범위의 정방향 반복기 값 형식으로 변환할 수 있어야 합니다.

참조된 범위는 유효해야 하며, 모든 포인터는 역참조 가능해야 하고 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 필요한 생성기에 대해 정확하게 `Count`개 선형 호출입니다.

### <a name="example"></a>예

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <deque>
#include <iostream>
#include <string>
#include <algorithm>
#include <random>

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
    const int elemcount = 5;
    vector<int> v(elemcount);
    deque<int> dq(elemcount);

    // Set up random number distribution
    random_device rd;
    mt19937 engine(rd());
    uniform_int_distribution<int> dist(-9, 9);

    // Call generate_n, using a lambda for the third parameter
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });
    print("vector v is: ", v);

    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });
    print("deque dq is: ", dq);
}

```

## <a name="includes"></a>  includes

요소 간 순서 지정 또는 동등성 기준을 이진 조건자로 지정할 수 있을 경우 하나의 정렬된 범위가 두 번째 정렬된 범위에 포함된 모든 요소를 포함할 수 있는지 여부를 테스트합니다.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate comp );
```

### <a name="parameters"></a>매개 변수

*first1* 두 번째의 모든 요소가 첫 번째에 포함 되는지를 테스트할 두 개의 정렬 된 소스 범위 중 첫 번째 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 두 번째의 모든 요소가 첫 번째에 포함 되는지를 테스트할 하나 다음 위치의 마지막 요소가 첫 번째에서 두 개의 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*first2* 두 번째의 모든 요소가 첫 번째에 포함 되는지를 테스트할 첫 번째 정렬 된 요소에 두 개의 연속 중 두 번째 소스 범위의 위치를 지정 하는 입력된 반복기입니다.

*last2* 두 번째의 모든 요소가 첫 번째에 포함 되는지를 테스트할 하나 마지막 정렬 된 요소에 두 개의 연속 중 두 번째 소스 범위 다음의 위치를 지정 하는 입력된 반복기입니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

첫 번째 정렬된 범위가 두 번째 정렬된 범위의 모든 요소를 포함하는 경우 **true**, 아닌 경우 **false**입니다.

### <a name="remarks"></a>설명

이 테스트에서 고려해 볼 또 다른 방법은 두 번째 소스 범위가 첫 번째 소스 범위의 하위 집합인지를 확인하는 것입니다.

참조된 정렬된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

정렬된 소스 범위는 각각 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다.

소스 범위는 알고리즘에 의해 수정 되지 않습니다 `merge`합니다.

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 좀 더 정확하게, 알고리즘은 지정된 이진 조건자에 따라 첫 번째 정렬된 범위의 모든 요소가 두 번째 정렬된 범위의 모든 요소와 동일한 순서인지를 테스트합니다.

알고리즘의 복잡성은 선형 이며 최대 2 \* (( *last1-first1*)-(* last2-first2 *))-1 비어 있지 않은 소스 범위에 대해 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_includes.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1a, v1b;
   vector <int>::iterator Iter1a,  Iter1b;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -2 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-2 ; ii <= 3 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        << "binary predicate less than is v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is v1b = ( " ;
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b );
   vector <int>::iterator Iter2a,  Iter2b;
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );
   v2a.pop_back ( );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is v2a = ( " ;
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is v2b = ( " ;
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ;
   vector <int>::iterator Iter3a, Iter3b;
   reverse (v3a.begin( ), v3a.end( ) );
   v3a.pop_back ( );
   v3a.pop_back ( );
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3a = ( " ;
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3b = ( " ;
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To test for inclusion under an asscending order
   // with the default binary predicate less <int> ( )
   bool Result1;
   Result1 = includes ( v1a.begin ( ) , v1a.end ( ) ,
      v1b.begin ( ) , v1b.end ( ) );
   if ( Result1 )
      cout << "All the elements in vector v1b are "
           << "contained in vector v1a." << endl;
   else
      cout << "At least one of the elements in vector v1b "
           << "is not contained in vector v1a." << endl;

   // To test for inclusion under descending
   // order specify binary predicate greater<int>( )
   bool Result2;
   Result2 = includes ( v2a.begin ( ) , v2a.end ( ) ,
      v2b.begin ( ) , v2b.end ( ) , greater <int> ( ) );
   if ( Result2 )
      cout << "All the elements in vector v2b are "
           << "contained in vector v2a." << endl;
   else
      cout << "At least one of the elements in vector v2b "
           << "is not contained in vector v2a." << endl;

   // To test for inclusion under a user
   // defined binary predicate mod_lesser
   bool Result3;
   Result3 = includes ( v3a.begin ( ) , v3a.end ( ) ,
      v3b.begin ( ) , v3b.end ( ) , mod_lesser );
   if ( Result3 )
      cout << "All the elements in vector v3b are "
           << "contained under mod_lesser in vector v3a."
           << endl;
   else
      cout << "At least one of the elements in vector v3b is "
           << " not contained under mod_lesser in vector v3a."
           << endl;
}
```

```Output
Original vector v1a with range sorted by the
 binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).
Original vector v1b with range sorted by the
 binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).
Original vector v2a with range sorted by the
 binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).
Original vector v2b with range sorted by the
 binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).
Original vector v3a with range sorted by the
 binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).
Original vector v3b with range sorted by the
 binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).
All the elements in vector v1b are contained in vector v1a.
At least one of the elements in vector v2b is not contained in vector v2a.
At least one of the elements in vector v3b is  not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>  inplace_merge

두 연속 정렬 범위의 요소를 단일 정렬 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Predicate>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Predicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 결합 되어 단일 범위로 정렬 된 첫 번째 정렬 된 두 개의 연속 중 첫 번째에서 요소 범위의 주소를 지정 하는 양방향 반복기입니다.

*중간* 결합 되어 단일 범위로 정렬 첫 번째 정렬 된 요소에 두 개의 연속 중 두 번째 범위의 위치를 주소 지정 하는 양방향 반복기입니다.

*마지막* 하나 결합 되어 단일 범위로 정렬 마지막 두 개의 연속 중 두 번째 정렬 된 요소 범위 다음의 위치를 주소 지정 하는 양방향 반복기입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="remarks"></a>설명

참조된 정렬된 연속 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

정렬된 연속 범위는 각각 `inplace_merge` 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다. 각 범위 내 요소의 상대 순서가 유지되므로 작업이 안정적입니다. 두 소스 범위에 동일한 요소가 있는 경우, 결합된 범위에서 첫 번째 범위의 요소가 두 번째 소스 범위의 요소보다 앞에 옵니다.

알고리즘은 임시 버퍼에 메모리를 할당하므로 복잡성은 사용 가능한 메모리에 따라 달라집니다. 충분 한 메모리가 사용 가능한 경우 최상의 경우는 선형 이며 (*-먼저 마지막 *)-1 비교; 최악의 경우에는 보조 메모리가 없습니다. 사용 가능한 경우 *N* 로그 *(N)* 여기서  *N* = (* 성-*).

### <a name="example"></a>예

```cpp
// alg_inplace_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      //For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2, Iter3;

   // Constructing vector v1 with default less-than ordering
   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =-5 ; ii <= 0 ; ii++ )
   {
      v1.push_back(  ii  );
   }

   cout << "Original vector v1 with subranges sorted by the\n "
        <<  "binary predicate less than is  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Constructing vector v2 with ranges sorted by greater
   vector <int> v2 ( v1 );
   vector <int>::iterator break2;
   break2 = find ( v2.begin ( ) , v2.end ( ) , -5 );
   sort ( v2.begin ( ) , break2 , greater<int> ( ) );
   sort ( break2 , v2.end ( ) , greater<int> ( ) );
   cout << "Original vector v2 with subranges sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Constructing vector v3 with ranges sorted by mod_lesser
   vector <int> v3 ( v1 );
   vector <int>::iterator break3;
   break3 = find ( v3.begin ( ) , v3.end ( ) , -5 );
   sort ( v3.begin ( ) , break3 , mod_lesser );
   sort ( break3 , v3.end ( ) , mod_lesser );
   cout << "Original vector v3 with subranges sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;

   vector <int>::iterator break1;
   break1 = find (v1.begin ( ) , v1.end ( ) , -5 );
   inplace_merge ( v1.begin( ), break1, v1.end( ) );
   cout << "Merged inplace with default order,\n vector v1mod = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To merge inplace in descending order, specify binary
   // predicate greater<int>( )
   inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );
   cout << "Merged inplace with binary predicate greater specified,\n "
        << "vector v2mod = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Applying a user defined (UD) binary predicate mod_lesser
   inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "
        << "vector v3mod = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 with subranges sorted by the
 binary predicate less than is  v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
Original vector v2 with subranges sorted by the
 binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Original vector v3 with subranges sorted by the
 binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )
Merged inplace with default order,
 vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )
Merged inplace with binary predicate greater specified,
 vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Merged inplace with binary predicate mod_lesser specified,
 vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )
```

## <a name="is_heap"></a>  is_heap

반환 **true** 지정 된 범위의 요소가 힙을 구성 하는 경우.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 힙에 대해 확인할 범위의 시작을 나타내는 임의 액세스 반복기입니다.

*마지막* 범위의 끝을 나타내는 임의 액세스 반복기입니다.

*comp* 요소의 순서 지정에 테스트할 조건입니다. 이진 조건자는 단일 인수를 받아서 반환 **true** 하거나 **false**합니다.

### <a name="return-value"></a>반환 값

반환 **true** 지정 된 범위의 요소가 힙을 구성 하는, 하는 경우 **false** 아닌 경우.

### <a name="remarks"></a>설명

첫 번째 템플릿 함수는 [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(` `first ,` `last ) ==` `last`를 반환합니다.

두 번째 템플릿 함수는

`is_heap_until` `(`  `first` `,`  `last` `,`  `comp` `) ==`  `last`를 반환합니다.

## <a name="is_heap_until"></a>  is_heap_until

범위에서 첫 번째 요소에 배치 된 반복기를 반환 합니다. [ `begin`, `end`) 힙 정렬 조건을 충족 하지 않는 또는 *끝* 는 범위가 힙을 형성 하는 경우.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator begin,
    RandomAccessIterator end);

template<class RandomAccessIterator, class BinaryPredicate>
RandomAccessIterator is_heap_until(
    RandomAccessIterator begin,
    RandomAccessIterator end,
    BinaryPredicate compare);
```

### <a name="parameters"></a>매개 변수

*시작* 힙에 대해 확인할 범위의 첫 번째 요소를 지정 하는 임의 액세스 반복기입니다.

*최종* 힙에 대해 확인할 범위의 끝을 지정 하는 임의 액세스 반복기입니다.

*비교* 는 엄격한/약한 정렬 힙을 정의 하는 조건을 지정 하는 이진 조건자입니다. 경우의 기본 조건자 *비교* 지정 하지 않으면는 `std::less<>`합니다.

### <a name="return-value"></a>반환 값

반환 *최종* 지정한 범위가 힙을 형성 하 또는 하나 이하의 요소를 포함 하는 경우. 그렇지 않으면 첫 번째로 발견된 힙 조건을 충족하지 않는 요소에 대한 반복기를 반환합니다.

### <a name="remarks"></a>설명

마지막 반복기를 반환 하는 첫 번째 템플릿 함수 `next` 에 `[ begin , end ]` 여기서 `[ begin , next)` 힙 함수 개체로 정렬 `std::less<>`합니다. 경우 거리 `end - begin < 2`를 반환 *끝*합니다.

두 번째 템플릿도 첫 번째 템플릿과 동일하게 동작하지만 힙 정렬 조건으로 `compare`가 아닌 `std::less<>` 조건자를 사용합니다.

## <a name="is_partitioned"></a>  is_partitioned

반환 **true** 테스트는 지정된 된 범위에 있는 모든 요소 **true** 조건을 테스트 하는 요소 앞에 대 한 **false**합니다.

```cpp
template<class InputIterator, class BinaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 조건을 검사할 범위가 시작 되는 위치를 나타내는 입력된 반복기입니다.

*마지막* 범위의 끝을 나타내는 입력된 반복기입니다.

*comp* 조건에 대 한 테스트입니다. 검색 중인 요소가 충족할 조건을 정의하는 사용자 정의 조건자 함수 개체에 의해 제공됩니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

True를 반환 하는 경우 테스트는 지정된 된 범위에서 요소의 모든 **true** 조건을 테스트 하는 요소 앞에 대 한 **false**, 그렇지 않은 경우 반환 **false**.

### <a name="remarks"></a>설명

템플릿 함수 **true** 경우에만의 모든 요소 `[` `first ,` `last )` 에서 분할 됩니다 *comp*; 즉, 모든 요소 `X` 에서`[` `first ,` `last )` 는 `comp (X)` true 모든 요소 보다 먼저 발생 `Y` 입니다 `comp (Y)` 되 **false**합니다.

## <a name="is_permutation"></a>  is_permutation

요소의 순서가 동일한지 여부에 관계없이 두 범위에 동일한 요소가 포함되어 있으면 true를 반환합니다. 두 번째 범위에 단일 반복기만 사용하는 오버로드는 두 번째 범위가 첫 번째 범위보다 긴 경우 차이를 감지하지 못하고 두 번째 범위가 첫 번째 범위보다 짧은 경우 정의되지 않은 동작이 발생하므로 C++14 코드에서 이중 범위 오버로드를 사용합니다.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    Predicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2,
    Predicate Pred);
```

### <a name="parameters"></a>매개 변수

*First1* 범위의 첫 번째 요소를 가리키는 정방향 반복기입니다.

*Last1* 범위의 마지막 요소 하나 다음을 참조 하는 정방향 반복기입니다.

*First2* 비교에 사용 되는, 두 번째 범위의 첫 번째 요소를 가리키는 정방향 반복기입니다.

*Last2* 비교에 사용 되는, 두 번째 범위의 마지막 요소 하나 다음을 참조 하는 정방향 반복기입니다.

*Pred* 동등성을 테스트 하 고 반환 하는 조건자를 **bool**합니다.

### <a name="return-value"></a>반환 값

**true 이면** 범위 다시 정렬할 수이 고, 그렇지 않으면 비교 연산자 조건자에 따라 동일 하면 **false**합니다.

### <a name="remarks"></a>설명

최악의 경우 `is_permutation`은 정방형 복잡성을 갖습니다.

첫 번째 템플릿 함수에서 시작 하는 범위에서에서 만큼 많은 요소가 있다고 가정 *First2* 하 여 지정 된 범위에서는 [ `First1`, `Last1`). 두 번째 범위에 더 많은 요소가 있는 경우 무시되고, 더 적은 요소가 있는 경우 정의되지 않은 동작이 발생합니다. 세 째 템플릿 함수(C++14 이상)에서는 이러한 가정을 하지 않습니다.  둘 다 반환 **true** 로 지정 된 범위의 각 요소 X에 대 한 경우에만 [ `First1`합니다 `Last1`)는 X에 대 한 동일한 범위 만큼 많은 Y 요소가 가지에서 시작 하는 범위에에서는 = = Y *First2* 또는 [ `First2, Last2).` 이때 `operator==` 피연산자 간에 pairwise 비교를 수행 해야 합니다.

두 번째 및 네 번째 템플릿 함수는 `operator==(X, Y)`를 `Pred(X, Y)`로 대체한다는 점을 제외하고 동일하게 동작합니다. 올바르게 동작하려면 조건자가 대칭, 재귀 및 전이여야 합니다.

### <a name="example"></a>예

다음 예제에서는 `is_permutation`을 사용하는 방법을 보여 줍니다.

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
#include <string>

using namespace std;

int main()
{
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };

    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };

    cout << "(1) Compare using built-in == operator: ";
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // true

    cout << "(2) Compare after modifying vec_2: ";
    vec_2[0] = 6;
    cout << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // false

    // Define equivalence as "both are odd or both are even"
    cout << "(3) vec_3 is a permutation of vec_4: ";
    cout << is_permutation(vec_3.begin(), vec_3.end(),
        vec_4.begin(), vec_4.end(),
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true

    // Initialize a vector using the 's' string literal to specify a std::string
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };

    // Define equivalence as "first letters are equal":
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),
        [](const string& lhs, const string& rhs)
    {
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator
    });

    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true

    cout << "Press a letter" << endl;
    char c;
    cin >> c;

    return 0;
}

```

## <a name="is_sorted"></a>  is_sorted

반환 **true** 지정 된 범위의 요소가 정렬에서 하는 경우.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 검사할 범위의 시작 위치를 지정 하는 정방향 반복기입니다.

*마지막* 범위의 끝을 나타내는 정방향 반복기입니다.

*comp* 두 요소 사이의 순서를 결정 하려면 테스트할 조건입니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다. `operator<`와 동일한 작업을 수행합니다.

### <a name="remarks"></a>설명

첫 번째 템플릿 함수 [is_sorted_until](http://msdn.microsoft.com/bbad99d0-deaa-4fe6-ae58-eb5b3e4dded0)`( first, last ) == last`합니다. `operator<` 함수는 순서 비교를 수행 합니다.

두 번째 템플릿 함수의 반환 `is_sorted_until( first, last , comp ) == last`합니다. 합니다 *comp* 조건자 함수는 순서 비교를 수행 합니다.

## <a name="is_sorted_until"></a>  is_sorted_until

지정된 범위에서 정렬된 순서에 있는 마지막 요소로 설정된 `ForwardIterator`를 반환합니다.

두 번째 버전을 제공할 수는 `BinaryPredicate` 반환 하는 함수 **true** 지정 된 두 요소가 정렬 된 경우 및 **false** 그렇지 않은 경우.

```cpp
template<class ForwardIterator>
    ForwardIterator is_sorted_until(
        ForwardIterator first,
        ForwardIterator last
    );
template<class ForwardIterator, class BinaryPredicate>
    ForwardIterator is_sorted_until(
        ForwardIterator first,
        ForwardIterator last,
        BinaryPredicate comp
    );
```

### <a name="parameters"></a>매개 변수

*첫 번째* 정방향 반복기 검사할 범위의 시작 위치를 나타내는입니다.

*마지막* 범위의 끝을 나타내는 정방향 반복기입니다.

*comp* 두 요소 사이의 순서를 결정 하려면 테스트할 조건입니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

정렬된 순서에서 마지막 요소에 대해 설정된 `ForwardIterator`를 반환합니다. 정렬 된 시퀀스에서 시작 *첫 번째*입니다.

### <a name="remarks"></a>설명

`[` `first , next)`가 `operator<`에 의해 정렬된 시퀀스가 되도록 첫 번째 템플릿 함수는 `[` `first ,` `last ]`에서 마지막 반복기 `next`를 반환합니다. 하는 경우 `distance()` `< 2` 반환 *마지막*합니다.

`operator<(X, Y)`를 `comp (X, Y)`로 바꾸는 것을 제외하면 두 번째 템플릿 함수도 동일하게 동작합니다.

## <a name="iter_swap"></a>  iter_swap

지정된 반복기의 쌍이 참조하는 두 값을 교환합니다.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );

```

### <a name="parameters"></a>매개 변수

*왼쪽* 은 값을 교환할 정방향 반복기 중 하나입니다.

*오른쪽* 은 값을 교환할 정방향 반복기 중 두 번째 숫자입니다.

### <a name="remarks"></a>설명

이전 버전과의 호환성을 위해 C++ 표준에 포함된 **iter_swap**보다 `swap`을 먼저 사용해야 합니다. 하는 경우 `Fit1` 및 `Fit2` 있다면 정방향 반복기 `iter_swap` ( `Fit1`, `Fit2` ), 동일 `swap` ( \* `Fit1`를 \* `Fit2` ).

입력 정방향 반복기의 값 형식은 동일한 값을 가져야 합니다.

### <a name="example"></a>예

```cpp
// alg_iter_swap.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) { m_nVal =
   rhs.m_nVal; return *this; }
   bool operator<( const CInt& rhs ) const
      { return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt(" << rhs.m_nVal << ")";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main( )
{
   CInt c1 = 5, c2 = 1, c3 = 10;
   deque<CInt> deq1;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Exchanging first and last elements with iter_swap
   iter_swap ( deq1.begin ( ) , --deq1.end ( ) );

   cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Swapping back first and last elements with swap
   swap ( *deq1.begin ( ) , *(deq1.end ( ) -1 ) );

   cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Swapping a vector element with a deque element
   vector <int> v1;
   vector <int>::iterator Iter1;
   deque <int> deq2;
   deque <int>::iterator d2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 4 ; ii <= 5 ; ii++ )
   {
      deq2.push_back( ii );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Deque deq2 is ( " ;
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
      cout << *d2_Iter << " ";
   cout << ")." << endl;

   iter_swap ( v1.begin ( ) , deq2.begin ( ) );

   cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << " & deque deq2 is: deq2 = ( ";
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
      cout << *d2_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).
The deque of CInts with first & last elements swapped is:
 deq1 = ( CInt(10), CInt(1), CInt(5) ).
The deque of CInts with first & last elements swapped back is:
 deq1 = ( CInt(5), CInt(1), CInt(10) ).
Vector v1 is ( 0 1 2 3 ).
Deque deq2 is ( 4 5 ).
After exchanging first elements,
 vector v1 is: v1 = ( 4 1 2 3 ).
 & deque deq2 is: deq2 = ( 0 5 ).
```

## <a name="lexicographical_compare"></a>  lexicographical_compare

두 시퀀스를 요소별로 비교하여 둘 중 작은 것을 결정합니다.

```cpp
template<class InputIterator1, class InputIterator2>
 bool lexicographical_compare(
     InputIterator1  first1,
     InputIterator1 Last1,
     InputIterator2  first2,
     InputIterator2 Last2  );

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool lexicographical_compare(
     InputIterator1  first1,
     InputIterator1 Last1,
     InputIterator2  first2,
     InputIterator2 Last2,
     BinaryPredicate  comp  );

```

### <a name="parameters"></a>매개 변수

*first1* 비교할 첫 번째 범위의 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 비교할 첫 번째 범위의 마지막 요소 하나의 위치를 지정 하는 입력된 반복기입니다.

*first2* 비교할 두 번째 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last2* 비교할 두 번째 범위에서 마지막 요소 하나의 위치를 지정 하는 입력된 반복기입니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

첫 번째 범위가 두 번째 범위보다 사전 순으로 작은 경우 **true**, 아닌 경우 **false**입니다.

### <a name="remarks"></a>설명

시퀀스 간 사전순 비교는 다음 조건이 충족될 때까지 요소를 비교합니다.

- 두 개의 해당 요소가 같지 않음을 발견하고, 비교의 결과를 시퀀스 간 비교의 결과로서 가져올 때까지

- 부등식이 발견되지는 않지만 한 시퀀스가 다른 시퀀스보다 많은 요소를 가지고 있어, 더 짧은 시퀀스가 더 긴 시퀀스보다 작은 것으로 간주될 때까지

- 부등식이 발견되지 않고 시퀀스가 동일한 수의 요소를 가지고 있어서, 시퀀스가 같으며 비교 결과가 false가 될 때까지

### <a name="example"></a>예

```cpp
// alg_lex_comp.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 < elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   int ii;
   for ( ii = 0 ; ii <= 6 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Self lexicographical_comparison of v1 under identity
   bool result1;
   result1 = lexicographical_compare (v1.begin( ), v1.end( ),
                  v1.begin( ), v1.end( ) );
   if ( result1 )
      cout << "Vector v1 is lexicographically_less than v1." << endl;
   else
      cout << "Vector v1 is not lexicographically_less than v1." << endl;

   // lexicographical_comparison of v1 and L2 under identity
   bool result2;
   result2 = lexicographical_compare (v1.begin( ), v1.end( ),
                  L1.begin( ), L1.end( ) );
   if ( result2 )
      cout << "Vector v1 is lexicographically_less than L1." << endl;
   else
      cout << "Vector v1 is lexicographically_less than L1." << endl;

   bool result3;
   result3 = lexicographical_compare (v1.begin( ), v1.end( ),
                  v2.begin( ), v2.end( ), twice );
   if ( result3 )
      cout << "Vector v1 is lexicographically_less than v2 "
           << "under twice." << endl;
   else
      cout << "Vector v1 is not lexicographically_less than v2 "
           << "under twice." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 )
List L1 = ( 0 5 10 15 20 25 30 )
Vector v2 = ( 0 10 20 30 40 50 )
Vector v1 is not lexicographically_less than v1.
Vector v1 is lexicographically_less than L1.
Vector v1 is not lexicographically_less than v2 under twice.
```

## <a name="lower_bound"></a>  lower_bound

정렬된 범위에서 지정된 값보다 크거나 같은 값을 갖는 첫 번째 요소의 위치를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator lower_bound(
     ForwardIterator first,
     ForwardIterator last,
     const Type& value );

template<class ForwardIterator, class Type, class BinaryPredicate>
ForwardIterator lower_bound(
     ForwardIterator first,
     ForwardIterator last,
     const Type& value,
     BinaryPredicate comp );

```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*값* 인 첫 번째 위치 또는 가능한 첫 번째 위치는 검색 되는 값에 대 한 정렬된 된 범위에서.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

지정된 값보다 크거나 같은 값이 있는 정렬된 범위의 첫 번째 요소 위치에 있는 정방향 반복기입니다. 여기서 같음은 이진 조건자로 지정됩니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 반복기는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

정렬된 범위는 `lower_bound` 사용의 사전 조건이며 순서는 이진 조건자로 지정된 것과 같습니다.

범위는 `lower_bound` 알고리즘에 의해 수정되지 않습니다.

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 비등가 요소 사이에 정렬이 수행됩니다.

알고리즘의 복잡성은 임의 액세스 반복기에 대 한 로그 및 선형 비례 하는 단계 수 이며 그렇지 않은 경우 (`last - first`).

### <a name="example"></a>예

```cpp
// alg_lower_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main( )
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back(  i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back(  ii  );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate lower_bound

    vector<int>::iterator Result;

    // lower_bound of 3 in v1 with default binary predicate less<int>()
    Result = lower_bound(v1.begin(), v1.end(), 3);
    cout << "The lower_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The lower_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v3 with the binary predicate  mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3,  mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}

```

## <a name="make_heap"></a>  make_heap

지정한 범위의 요소를 첫 번째 요소가 가장 큰 힙으로 변환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class RandomAccessIterator>
void make_heap(
     RandomAccessIterator first,
     RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
     RandomAccessIterator first,
     RandomAccessIterator last,
     BinaryPredicate comp );

```

### <a name="parameters"></a>매개 변수

*첫 번째* 힙으로 변환할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*마지막* 힙으로 변환할 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="remarks"></a>설명

힙에는 두 가지 속성이 있습니다.

- 첫 번째 요소는 항상 가장 큽니다.

- 로그 시간에서 요소를 추가하거나 제거할 수 있습니다.

힙은 우선 순위 큐를 구현하는 이상적인 방법이며 C++ 표준 라이브러리 컨테이너 어댑터 [priority_queue 클래스](../standard-library/priority-queue-class.md)의 구현에 사용됩니다.

복잡성은 선형 이며 3 요구 \* (* 성-*) 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_make_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with default less than ordering
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with greater than ordering
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater-than heaped version of v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="max"></a>  max

두 개체를 비교하고 둘 중 큰 개체를 반환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class Type>
    const Type& max(
        const Type& left,
        const Type& right
    );
template<class Type, class Pr>
    const Type& max(
        const Type& left,
        const Type& right,
        BinaryPredicate comp
    );
template<class Type>
    Type& max (
        initializer_list<Type> _Ilist
    );
template<class Type, class Pr>
    Type& max(
        initializer_list<Type> _Ilist,
        BinaryPredicate comp
    );
```

### <a name="parameters"></a>매개 변수

*왼쪽* 비교 되는 두 개체 중 첫 번째 숫자입니다.

*오른쪽* 비교할 두 번째 개체입니다.

*comp* 두 개체를 비교 하는 데 사용 되는 이진 조건자입니다.

*_IList* 비교할 개체가 포함 된 이니셜라이저 목록입니다.

### <a name="return-value"></a>반환 값

둘 중 더 큰 개체입니다. 더 큰 개체가 없는 경우 두 개체 중 첫 번째 개체가 반환됩니다. initializer_list의 경우 목록의 개체 중 가장 큰 개체가 반환됩니다.

### <a name="remarks"></a>설명

`max` 알고리즘은 대체로 매개 변수로 전달된 개체를 사용하지 않습니다. 대부분의 C++ 표준 라이브러리 알고리즘은 매개 변수로 전달된 반복기가 위치를 지정하는 요소 범위에서 작동합니다. 요소 범위에서 작동하는 함수가 필요한 경우 [max_element](../standard-library/algorithm-functions.md#max_element)를 대신 사용합니다.

### <a name="example"></a>예

```cpp
// alg_max.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether absolute value of elem1 is greater than
// absolute value of elem2
bool abs_greater ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = -elem1;
   if ( elem2 < 0 )
      elem2 = -elem2;
   return elem1 < elem2;
};

int main( )
{
   int a = 6, b = -7;
   // Return the integer with the larger absolute value
   const int& result1 = max(a, b, abs_greater);
   // Return the larger integer
   const int& result2 = max(a, b);

   cout << "Using integers 6 and -7..." << endl;
   cout << "The integer with the greater absolute value is: "
        << result1 << "." << endl;
   cout << "The integer with the greater value is: "
        << result2 << "." << endl;
   cout << endl;

// Comparing the members of an initializer_list
const int& result3 = max({ a, b });
const int& result4 = max({ a, b }, abs_greater);

cout << "Comparing the members of an initializer_list..." << endl;
cout << "The member with the greater value is: " << result3 << endl;
cout << "The integer with the greater absolute value is: " << result4 << endl;

   // Comparing set containers with elements of type CInt
   // using the max algorithm
   CInt c1 = 1, c2 = 2, c3 = 3;
   set<CInt> s1, s2, s3;
   set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s2.insert ( c2 );
   s2.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   cout << "s2 = (";
   for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
      cout << " " << *s2_Iter << ",";
   s2_Iter = --s2.end( );
   cout << " " << *s2_Iter << " )." << endl;

   s3 = max ( s1, s2 );
   cout << "s3 = max ( s1, s2 ) = (";
   for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
      cout << " " << *s3_Iter << ",";
   s3_Iter = --s3.end( );
   cout << " " << *s3_Iter << " )." << endl << endl;

   // Comparing vectors with integer elements using the max algorithm
   vector <int> v1, v2, v3, v4, v5;
   vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

   int i;
   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 0 ; ii <= 2 ; ii++ )
   {
      v2.push_back( ii );
   }

   int iii;
   for ( iii = 0 ; iii <= 2 ; iii++ )
   {
      v3.push_back( 2 * iii );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   cout << "Vector v3 is ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;

   v4 = max ( v1, v2 );
   v5 = max ( v1, v3 );

   cout << "Vector v4 = max (v1,v2) is ( " ;
   for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
      cout << *Iter4 << " ";
   cout << ")." << endl;

   cout << "Vector v5 = max (v1,v3) is ( " ;
   for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
      cout << *Iter5 << " ";
   cout << ")." << endl;
}
```

```Output
Using integers 6 and -7...
The integer with the greater absolute value is: -7
The integer with the greater value is: 6.
Comparing the members of an initializer_list...The member with the greater value is: 6The integer wiht the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a>  max_element

지정된 범위에서 가장 큰 첫 번째 요소를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class ForwardIterator>
ForwardIterator max_element(ForwardIterator first, ForwardIterator last );

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator max_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp );

```

### <a name="parameters"></a>매개 변수

*첫 번째* 가장 큰 요소에 대 한 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 가장 큰 요소에 대 한 검색할 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 정방향 반복기입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

검색할 범위에서 최대 요소의 첫 번째 발생 위치의 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 선형: (`last` - `first`)-1 비교는 비어 있지 않은 범위에 대 한 필요 합니다.

### <a name="example"></a>예

```cpp
// alg_max_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt& operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<(ostream& osIn, const CInt& rhs)
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is greater than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main( )
{
   // Searching a set container with elements of type CInt
   // for the maximum element
   CInt c1 = 1, c2 = 2, c3 = -3;
   set<CInt> s1;
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s1.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   s1_R1_Iter = max_element ( s1.begin ( ) , s1.end ( ) );

   cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
   cout << endl;

   // Searching a vector with elements of type int for the maximum
   // element under default less than & mod_lesser binary predicates
   vector <int> v1;
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      v1.push_back( - 2 * ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << " ";
   cout << ")." << endl;

   v1_R1_Iter = max_element ( v1.begin ( ) , v1.end ( ) );
   v1_R2_Iter = max_element ( v1.begin ( ) , v1.end ( ), mod_lesser);

   cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
   cout << "The largest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a>  merge

정렬된 두 소스 범위의 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
 OutputIterator merge(
     InputIterator1 first1,
     InputIterator1 last1,
     InputIterator2 first2,
     InputIterator2 last2,
     OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator merge(
     InputIterator1 first1,
     InputIterator1 last1,
     InputIterator2 first2,
     InputIterator2 last2,
     OutputIterator result,
     BinaryPredicate comp );

```

### <a name="parameters"></a>매개 변수

*first1* 결합 하 고 정렬 된 단일 범위로 두 개의 정렬 된 소스 범위 중 첫 번째 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 하나 다음 위치의 마지막 요소가 첫 번째에서 결합 하 고 정렬 된 단일 범위로 두 개의 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*first2* 결합 되어 단일 범위로 정렬 된 첫 번째 정렬 된 요소에 두 개의 연속 중 두 번째 소스 범위의 위치를 지정 하는 입력된 반복기입니다.

*last2* 결합 되어 단일 범위로 정렬 마지막 정렬 된 요소에 두 개의 연속 중 두 번째 소스 범위 지난 한 위치를 지정 하는 입력된 반복기입니다.

*결과* 단일 정렬 범위로 결합 되는 대상 범위는 두 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

정렬된 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대상 범위는 소스 범위 중 하나와 겹쳐서는 안 되며, 대상 범위를 포함할 수 있을 정도로 커야 합니다.

정렬된 소스 범위는 각각 `merge` 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다.

각 범위 내 요소의 상대 순서가 대상 범위에서 유지되므로 작업이 안정적입니다. 소스 범위는 알고리즘에 의해 수정 되지 않습니다 `merge`합니다.

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 두 소스 범위에 동일한 요소가 있는 경우 대상 범위에서 첫 번째 범위의 요소가 두 번째 소스 범위의 요소보다 앞에 옵니다.

알고리즘의 복잡성은 선형 이며 최대 (* last1-first1 *)-(* last2-first2*)-1 비교 합니다.

[list class](../standard-library/list-class.md) 클래스는 두 목록의 요소를 병합하는 멤버 함수 "병합"을 제공합니다.

### <a name="example"></a>예

```cpp
// alg_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 ) {
   if (elem1 < 0)
      elem1 = - elem1;
   if (elem2 < 0)
      elem2 = - elem2;
   return elem1 < elem2;
}

int main() {
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1;

   // Constructing vector v1a and v1b with default less than ordering
   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1a.push_back(  i );

   int ii;
   for ( ii =-5 ; ii <= 0 ; ii++ )
      v1b.push_back(  ii  );

   cout << "Original vector v1a with range sorted by the\n "
        << "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        << "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vector v2 with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a,  Iter2b, Iter2;
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vector v3 with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3;
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        << "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        << "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To merge inplace in ascending order with default binary
   // predicate less <int> ( )
   merge ( v1a.begin ( ) , v1a.end ( ) , v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );
   cout << "Merged inplace with default order,\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To merge inplace in descending order, specify binary
   // predicate greater<int>( )
   merge ( v2a.begin ( ) , v2a.end ( ) , v2b.begin ( ) , v2b.end ( ) ,
       v2.begin ( ) ,  greater <int> ( ) );
   cout << "Merged inplace with binary predicate greater specified,\n "
        << "vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // Applying A user-defined (UD) binary predicate mod_lesser
   merge ( v3a.begin ( ) , v3a.end ( ) , v3b.begin ( ) , v3b.end ( ) ,
       v3.begin ( ) ,  mod_lesser );
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "
        << "vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="min"></a>  min

두 개체를 비교하고 둘 중 작은 개체를 반환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class Type>
    const Type& min(
        const Type& left,
        const Type& right
    );
template<class Type, class Pr>
    const Type& min(
        const Type& left,
        const Type& right,
        BinaryPredicate comp
    );
template<class Type>
    Type min ( initializer_list<Type> _Ilist
    );
template<class Type, class Pr>    Type min (
        initializer_list<Type> _Ilist,
        BinaryPredicate comp
    );

```

### <a name="parameters"></a>매개 변수

*왼쪽* 비교 되는 두 개체 중 첫 번째 숫자입니다.

*오른쪽* 비교할 두 번째 개체입니다.

*comp* 두 개체를 비교 하는 데 사용 되는 이진 조건자입니다.

*_IList* 비교할 멤버가 포함 된 initializer_list입니다.

### <a name="return-value"></a>반환 값

둘 중 더 작은 개체입니다. 더 작은 개체가 없는 경우 두 개체 중 첫 번째 개체가 반환됩니다. initializer_list의 경우 목록의 개체 중 가장 작은 개체가 반환됩니다.

### <a name="remarks"></a>설명

`min` 알고리즘은 대체로 매개 변수로 전달된 개체를 사용하지 않습니다. 대부분의 C++ 표준 라이브러리 알고리즘은 매개 변수로 전달된 반복기가 위치를 지정하는 요소 범위에서 작동합니다. 요소 범위를 사용하는 함수가 필요한 경우 [min_element](../standard-library/algorithm-functions.md#min_element)를 사용합니다.

### <a name="example"></a>예

```cpp
// alg_min.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
       return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main( )
{
    // Comparing integers directly using the min algorithm with
    // binary predicate mod_lesser & with default less than
    int a = 6, b = -7, c = 7 ;
    const int& result1 = min ( a, b, mod_lesser );
    const int& result2 = min ( b, c );

    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result1 << "." << endl;
     cout << "The lesser of the integers -7 & 7 is: "
        << result2 << "." << endl;
    cout << endl;

// Comparing the members of an initializer_list
    const int& result3 = min({ a, c });
    const int& result4 = min({ a, b }, mod_lesser);

    cout << "The lesser of the integers 6 & 7 is: "
        << result3 << "." << endl;
    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result4 << "." << endl;
    cout << endl;

    // Comparing set containers with elements of type CInt
       // using the min algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
        cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = min ( s1, s2 );
    cout << "s3 = min ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using min algorithm
    vector <int> v1, v2, v3, v4, v5;
    vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = min ( v1, v2 );
    v5 = min ( v1, v3 );

    cout << "Vector v4 = min ( v1,v2 ) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = min ( v1,v3 ) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
The mod_lesser of the integers 6 & -7 is: 6.
The lesser of the integers -7 & 7 is: -7.
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).
```

## <a name="min_element"></a>  min_element

지정된 범위에서 가장 작은 첫 번째 요소를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class ForwardIterator>
ForwardIterator min_element(ForwardIterator first, ForwardIterator last );

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator min_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 가장 작은 요소를 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 가장 작은 요소를 검색할 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 정방향 반복기입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

검색할 범위에서 최소 요소의 첫 번째 발생 위치의 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 선형: (`last` - `first`)-1 비교는 비어 있지 않은 범위에 대 한 필요 합니다.

### <a name="example"></a>예

```cpp
// alg_min_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt& operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   // Searching a set container with elements of type CInt
   // for the minimum element
   CInt c1 = 1, c2 = 2, c3 = -3;
   set<CInt> s1;
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s1.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   s1_R1_Iter = min_element ( s1.begin ( ) , s1.end ( ) );

   cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
   cout << endl;

   // Searching a vector with elements of type int for the maximum
   // element under default less than & mod_lesser binary predicates
   vector <int> v1;
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      v1.push_back( - 2 * ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << " ";
   cout << ")." << endl;

   v1_R1_Iter = min_element ( v1.begin ( ) , v1.end ( ) );
   v1_R2_Iter = min_element ( v1.begin ( ) , v1.end ( ), mod_lesser);

   cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;
   cout << "The smallest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

```Output
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).
The smallest element in s1 is: CInt( -3 )

Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).
The smallest element in v1 is: -8
The smallest element in v1 under the mod_lesser
 binary predicate is: 0
```

## <a name="minmax_element"></a>  minmax_element

한 번의 호출로 `min_element` 및 `max_element`에 의해 수행된 작업을 수행합니다.

```cpp
template<class ForwardIterator>
    pair< ForwardIterator, ForwardIterator >
        minmax_element(
            ForwardIterator  first,
            ForwardIterator Last
                 );
template<class ForwardIterator, class BinaryPredicate>
    pair< ForwardIterator, ForwardIterator >
        minmax_element(
            ForwardIterator  first,
            ForwardIterator Last,
            BinaryPredicate  comp
                );
```

### <a name="parameters"></a>매개 변수

*첫 번째* 범위의 시작을 나타내는 정방향 반복기입니다.

*마지막* 범위의 끝을 나타내는 정방향 반복기입니다.

*comp* 요소의 순서 지정에 사용 되는 선택적인 테스트입니다.

### <a name="return-value"></a>반환 값

반환 값

`pair<ForwardIterator, ForwardIterator>`

`(` [min_element](../standard-library/algorithm-functions.md#min_element)`(first, last), `[max_element](../standard-library/algorithm-functions.md#max_element)`(first, last))`합니다.

### <a name="remarks"></a>설명

첫 번째 템플릿 함수는 다음을 반환합니다.

`pair<ForwardIterator,ForwardIterator>`

`(min_element(_First,Last), max_element(_First,Last))`.

`operator<(X, Y)`를 `comp (X, Y)`로 바꾸는 것을 제외하면 두 번째 템플릿 함수도 동일하게 동작합니다.

시퀀스가 비어 있지 않은 경우 함수가 수행 최대 `3 * (last - first - 1) / 2` 비교 합니다.

## <a name="minmax"></a>  minmax

두 개의 입력된 매개 변수를 비교하여 작은 수에서 큰 수의 순서로 구성된 한 쌍을 반환합니다.

```cpp
template<class Type>
    pair<const Type&, const Type&>
        minmax(
            const Type& left,
            const Type& right
        );
template<class Type, class BinaryPredicate>
    pair<const Type&, const Type&>
        minmax(
            const Type& left,
            const Type& right,
            BinaryPredicate comp
        );
template<class Type>     pair<Type&, Type&>         minmax(
            initializer_list<Type> _Ilist
        );
template<class Type, class BinaryPredicate>
    pair<Type&, Type&>         minmax(
            initializer_list<Type> _Ilist,
            BinaryPredicate comp
        );

```

### <a name="parameters"></a>매개 변수

*왼쪽* 비교 되는 두 개체 중 첫 번째 숫자입니다.

*오른쪽* 비교할 두 번째 개체입니다.

*comp* 두 개체를 비교 하는 데 사용 되는 이진 조건자입니다.

*_IList* 비교할 멤버가 포함 된 initializer_list입니다.

### <a name="remarks"></a>설명

첫 번째 템플릿 함수 `pair<const Type&, const Type&>( right , left )` 하는 경우 *오른쪽* 는 미만 *왼쪽*합니다. 그 외의 경우 `pair<const Type&, const Type&>( left , right )`를 반환합니다.

여기서 첫 번째 요소가 더 작고 하 고 두 번째는 조건자에 비해 큰 쌍을 반환 하는 두 번째 멤버 함수 *comp*합니다.

나머지 템플릿 함수는 동일 하 게 동작을 제외 하 고 대체 합니다 *왼쪽* 하 고 *오른쪽* 매개 변수를 *_IList*합니다.

함수는 정확히 하나의 비교를 수행합니다.

## <a name="mismatch"></a>  mismatch

두 범위를 요소별로 비교하고 차이가 발생한 첫 번째 위치를 찾습니다.

두 번째 범위에 단일 반복기만 사용하는 오버로드는 두 번째 범위가 첫 번째 범위보다 긴 경우 차이를 감지하지 못하고 두 번째 범위가 첫 번째 범위보다 짧은 경우 정의되지 않은 동작이 발생하므로 C++14 코드에서 이중 범위 오버로드를 사용합니다.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
     InputIterator1 First1,
     InputIterator1 Last1,
     InputIterator2 First2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
     InputIterator1 First1,
     InputIterator1 Last1,
     InputIterator2 First2,
     BinaryPredicate Comp );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
     InputIterator1 Last1,
     InputIterator2 First2,
     InputIterator2 Last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
     InputIterator1 First1,
     InputIterator1 Last1,
     InputIterator2 First2,
     InputIterator2 Last2,
     BinaryPredicate Comp);
```

### <a name="parameters"></a>매개 변수

*First1* 테스트할 첫 번째 범위의 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*Last1* 테스트할 첫 번째 범위에서 마지막 요소의 하나의 위치를 지정 하는 입력된 반복기입니다.

*First2* 테스트할 두 번째 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*Last2* 테스트할 두 번째 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 입력된 반복기입니다.

*Comp* 각 범위에 있는 현재 요소를 비교 하 고 동일한 지 여부를 결정 하는 사용자 정의 조건자 함수 개체입니다. 조건이 충족되면 **true**를 반환하고, 충족되지 않으면 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

두 범위에서 불일치의 위치 주소를 지정하는 반복기 쌍입니다(첫 번째 범위의 위치에 대한 첫 번째 구성 요소 반복기 및 두 번째 범위의 위치에 대한 두 번째 구성 요소 반복기). 비교된 범위의 요소 간에 차이점이 있거나 두 범위의 모든 요소 쌍이 두 번째 버전의 이진 조건자를 충족하면 첫 번째 구성 요소 반복기는 첫 번째 범위에 있는 마지막 요소 하나 다음의 위치를 가리키고 두 번째 구성 요소 반복기는 두 번째 범위에서 테스트된 마지막 요소 하나 다음의 위치를 가리킵니다.

### <a name="remarks"></a>설명

첫 번째 템플릿 함수에서는 first2에서 시작하는 범위에 [first1, last1)로 지정된 범위만큼 많은 요소가 있다고 가정합니다. 두 번째 범위에 더 많은 요소가 있는 경우 무시되고, 더 적은 요소가 있는 경우 정의되지 않은 동작이 발생합니다.

검색할 범위는 유효해야 하고 모든 반복기는 역참조 가능해야 하며 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

알고리즘의 시간 복잡도는 더 짧은 범위에 포함된 요소 수에 비례합니다.

피연산자 간에 대칭, 재귀 및 전이적인 동등 관계를 적용하려면 사용자 정의 조건자가 필요하지 않습니다.

### <a name="example"></a>예

다음 예제에서는 불일치 사용 방법을 보여 줍니다. C++03 오버로드는 예기치 않은 결과를 생성하는 방법을 보여 주는 목적으로만 표시됩니다.

```cpp
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>
#include <string>
#include <utility>

using namespace std;

// Return whether first element is twice the second
// Note that this is not a symmetric, reflexive and transitive equivalence.
// mismatch and equal accept such predicates, but is_permutation does not.
bool twice(int elem1, int elem2)
{
    return elem1 == elem2 * 2;
}

void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,
    const vector<int>& left, const vector<int>& right)
{
    // If either iterator stops before reaching the end of its container,
    // it means a mismatch was detected.
    if (result.first != left.end() || result.second != right.end())
    {
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));
        cout << msg << "mismatch. Left iterator at " << leftpos
            << " right iterator at " << rightpos << endl;
    }
    else
    {
        cout << msg << " match." << endl;
    }
}

int main()
{

    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };

    // Testing different length vectors for mismatch (C++03)
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());
    bool is_mismatch = match_vecs.first != vec_1.end();
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;

    // Using dual-range overloads:

    // Testing different length vectors for mismatch (C++14)
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);

    // Identify point of mismatch between vec_1 and modified vec_2.
    vec_2[3] = 42;
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);

    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);

    vec_4[5] = 31;
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);

    // Compare a vector<int> to a list<int>
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;

    char c;
    cout << "Press a key" << endl;
    cin >> c;

}

/*
Output:
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred:  match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
*/

```

## <a name="alg_move"></a>  &lt;alg&gt; move

지정된 범위와 연결된 요소를 이동합니다.

```cpp
template<class InputIterator, class OutputIterator>
    OutputIterator move(
        InputIterator first,
        InputIterator last,
        OutputIterator dest
                  );
```

### <a name="parameters"></a>매개 변수

*첫 번째* 이동할 요소 범위의 시작 위치를 나타내는 입력된 반복기입니다.

*마지막* 이동할 요소 범위의 끝을 나타내는 입력된 반복기입니다.

*dest* 이동된 된 요소를 포함 하는 출력 반복기입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `*(dest + N) = move(*(first + N))` 마다 한 번씩 `N` 범위의 `[0, last - first)`, 엄격 하 게 값을 높이기 위한 `N` 가장 낮은 값을 사용 하 여 시작 합니다. 그런 다음 `dest + N`를 반환합니다. 하는 경우 `dest` 하 고 *첫 번째* 저장소, 영역을 지정 *dest* 범위에 없어야 `[first, last)`합니다.

## <a name="move_backward"></a>  move_backward

한 반복기의 요소를 다른 반복기로 이동합니다. 이동은 지정된 범위의 마지막 요소에서 시작하고 해당 범위의 첫 번째 요소에서 끝납니다.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
   BidirectionalIterator2 move_backward(
       BidirectionalIterator1 first,
       BidirectionalIterator1 last,
       BidirectionalIterator2 destEnd);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소를 이동할 범위의 시작을 나타내는 반복기입니다.

*마지막* 요소를 이동할 범위의 끝을 나타내는 반복기입니다. 이 요소를 이동하지 않습니다.

*destEnd* 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `*(destEnd - N - 1) = move(*(last - N - 1))` 마다 한 번씩 `N` 범위의 `[0, last - first)`, 엄격 하 게 값을 높이기 위한 `N` 가장 낮은 값을 사용 하 여 시작 합니다. 그런 다음 `destEnd - (last - first)`를 반환합니다. 하는 경우 *destEnd* 하 고 *첫 번째* 저장소, 영역을 지정 *destEnd* 범위에 없어야 `[first, last)`합니다.

`move` 및 `move_backward`는 이동 반복기와 함께 `copy` 및 `copy_backward`를 사용하는 것과 기능적으로 등가입니다.

## <a name="next_permutation"></a>  next_permutation

원래 순서 지정을 사전순에 따라 다음으로 큰 순열(있는 경우)로 대체할 수 있도록 범위의 요소 순서를 재정렬합니다. 여기서 다음의 의미는 이진 조건자로 지정할 수 있습니다.

```cpp
template<class BidirectionalIterator>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 순열 수 범위에서 첫 번째 요소의 위치를 가리키는 양방향 반복기입니다.

*마지막* 순열 수 하나 마지막 요소 범위에서 위치를 가리키는 양방향 반복기입니다.

*comp* 순서에 따라 연속적인 요소에 의해 충족 될 비교 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

사전식으로 다음 순열이 존재하여 범위의 원래 순서를 교체한 경우 **true**, 아닌 경우 **false**입니다. 이 경우 순서 지정은 사전식으로 가장 작은 순열로 변환됩니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

기본 이진 조건자는 less than이며, 범위의 요소는 다음 순열이 잘 정의되도록 less-than comparable이어야 합니다.

복잡성은 선형 이며 최대 (* 성-*) / 2 개의 교환이 지원 됩니다.

### <a name="example"></a>예

```cpp
// alg_next_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      { return ( m_nVal < rhs.m_nVal );}
   friend   ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main( )
{
   // Reordering the elements of type CInt in a deque
   // using the prev_permutation algorithm
   CInt c1 = 5, c2 = 1, c3 = 10;
   bool deq1Result;
   deque<CInt> deq1, deq2, deq3;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   deq1Result = next_permutation ( deq1.begin ( ) , deq1.end ( ) );

   if ( deq1Result )
      cout << "The lexicographically next permutation "
           << "exists and has\nreplaced the original "
           << "ordering of the sequence in deq1." << endl;
   else
      cout << "The lexicographically next permutation doesn't "
           << "exist\n and the lexicographically "
           << "smallest permutation\n has replaced the "
           << "original ordering of the sequence in deq1." << endl;

   cout << "After one application of next_permutation,\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl << endl;

   // Permuting vector elements with binary function mod_lesser
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = -3 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );

   cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= 5 ) {
      next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );
      cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
         cout << *Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).
The lexicographically next permutation exists and has
replaced the original ordering of the sequence in deq1.
After one application of next_permutation,
 deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first next_permutation, vector v1 is:
 v1 = ( -3 -2 -1 0 1 3 2 ).
After another next_permutation of vector v1,
 v1 =   ( -3 -2 -1 0 2 1 3 ).
After another next_permutation of vector v1,
 v1 =   ( -3 -2 -1 0 2 3 1 ).
After another next_permutation of vector v1,
 v1 =   ( -3 -2 -1 0 3 1 2 ).
After another next_permutation of vector v1,
 v1 =   ( -3 -2 -1 0 3 2 1 ).
After another next_permutation of vector v1,
 v1 =   ( -3 -2 -1 1 0 2 3 ).
```

## <a name="nth_element"></a>  nth_element

요소 범위를 분할하여 범위에서 시퀀스의 n번째 요소 앞의 모든 요소가 n번째 요소보다 작거나 같고 그 다음의 요소는 크거나 같도록 *n*번째 요소를 정확하게 찾습니다.

```cpp
template<class RandomAccessIterator>
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
 void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 파티셔닝할 범위에서 첫 번째 요소 위치의 주소를 지정 임의 액세스 반복기입니다.

*_Nth* 요소 위치의 주소를 지정 하는 임의 액세스 반복기 파티션 경계에 올바르게 정렬 됩니다.

*마지막* 파티셔닝할 범위에서 마지막 요소 하나의 위치를 주소 지정 임의 액세스 반복기입니다.

*comp* 순서에 따라 연속적인 요소에 의해 충족 될 비교 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

`nth_element` 알고리즘은 *n*번째 요소의 어느 한쪽 하위 범위에 있는 요소가 정렬되는 것을 보증하지 않습니다. 따라서 선택된 요소 아래의 범위에 있는 요소를 정렬하는 `partial_sort`보다 보증이 줄어들고, 더 낮은 범위의 순서가 필요하지 않은 경우 `partial_sort`에 대한 더 빠른 대안으로 사용될 수 있습니다.

둘 중 어느 요소도 다른 것보다 작지 않은 경우 두 요소는 등가이지만, 반드시 같은 것은 아닙니다.

정렬 복잡성의 평균은 선형 * 성-* 합니다.

### <a name="example"></a>예

```cpp
// alg_nth_elem.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 ) {
   return elem1 > elem2;
}

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1.push_back( 3 * i );

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
      v1.push_back( 3 * ii + 1 );

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
      v1.push_back( 3 * iii +2 );

   cout << "Original vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );
   cout << "Position 3 partitioned vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order, specify binary predicate
   nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),
          greater<int>( ) );
   cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   random_shuffle( v1.begin( ), v1.end( ) );
   cout << "Shuffled vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );
   cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

## <a name="none_of"></a>  none_of

반환 **true** 조건이 경우 지정된 된 범위에서 요소 간에 존재 하지 않습니다.

```cpp
template<class InputIterator, class BinaryPredicate>
bool none_of(InputIterator first, InputIterator last, BinaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소를 조건에 대해 범위 검사를 시작 하는 위치를 나타내는 입력된 반복기입니다.

*마지막* 요소 범위의 끝을 나타내는 입력된 반복기입니다.

*comp* 조건에 대 한 테스트입니다. 이 조건은 조건을 정의하는 사용자 정의 조건자 함수 개체에 의해 제공됩니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

반환 **true** 표시 된 범위에서 조건이 한 번 이상 검색 되지 않으면 및 **false** 조건이 검색 되는 경우.

### <a name="remarks"></a>설명

템플릿 함수 **true** 일부 경우에만 `N` 범위의 `[0, last - first)`, 조건자 `comp(*(first + N))` 항상 **false**.

## <a name="partial_sort"></a>  partial_sort

범위에 있는 지정된 수의 더 작은 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬합니다.

```cpp
template<class RandomAccessIterator>
   void partial_sort(
      RandomAccessIterator first,
      RandomAccessIterator sortEnd,
      RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
   void partial_sort(
      RandomAccessIterator first,
      RandomAccessIterator sortEnd,
      RandomAccessIterator last
      BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 정렬할 범위에서 첫 번째 요소 위치의 주소를 지정 된 임의 액세스 반복기입니다.

*sortEnd* 정렬할 하위 범위에서 마지막 요소 하나의 위치를 주소 지정을 임의 액세스 반복기입니다.

*마지막* 부분적으로 정렬할 하나 다음 위치의 마지막 요소 범위에서 주소 지정을 임의 액세스 반복기입니다.

*comp* 순서에 따라 연속적인 요소에 의해 충족 될 비교 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

둘 중 어느 요소도 다른 것보다 작지 않은 경우 두 요소는 등가이지만, 반드시 같은 것은 아닙니다. `sort` 알고리즘은 안정적이 지 및 됩니다 등가 요소의 상대적인 순서가 유지를 보장 하지 않습니다. `stable_sort` 알고리즘은 원래의 순서를 유지합니다.

평균 부분 정렬 복잡성은 *O*((`last`- `first`) 로그 (`sortEnd`- `first`)).

### <a name="example"></a>예

```cpp
// alg_partial_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
   {
      v1.push_back( 2 * ii +1 );
   }

   cout << "Original vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );
   cout << "Partially sorted vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To partially sort in descending order, specify binary predicate
   partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );
   cout << "Partially resorted (greater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ),
 UDgreater );
   cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector:
 v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Partially sorted vector:
 v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )
Partially resorted (greater) vector:
 v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )
Partially resorted (UDgreater) vector:
 v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )
```

## <a name="partial_sort_copy"></a>  partial_sort_copy

소스 범위의 요소를 대상 범위로 복사합니다. 여기서 소스 요소는 지정된 다른 이진 조건자보다 작거나 지정된 다른 이진 조건자로 정렬됩니다.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class BinaryPredicate>
RandomAccessIterator partial_sort_copy(
     InputIterator first1,
     InputIterator last1,
     RandomAccessIterator first2,
     RandomAccessIterator last2,
     BinaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*first1* 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 하나 다음 위치의 마지막 요소 소스 범위에서 지정 하는 입력된 반복기입니다.

*first2* 정렬된 된 대상 범위에서 첫 번째 요소 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*last2* 하나 다음 위치의 마지막 요소 정렬된 된 대상 범위에서 주소를 지정 하는 임의 액세스 반복기입니다.

*comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

소스 범위에서 삽입한 마지막 요소를 넘어 대상 범위에서 하나 다음 위치 요소의 주소를 지정하는 임의 액세스 반복기입니다.

### <a name="remarks"></a>설명

소스 및 대상 범위는 겹치지 않아야 하며 유효해야 합니다. 모든 포인터가 역참조 가능해야 하며, 각 시퀀스 내 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

등가가 아닌 요소는 정렬되고 등가인 요소는 정렬되지 않도록 엄밀히 약한 정렬을 제공해야 합니다. 둘 중 어느 요소도 다른 것보다 작지 않은 경우 두 요소는 보다 작음 조건에서 등가이지만, 반드시 같음은 아닙니다.

### <a name="example"></a>예

```cpp
// alg_partial_sort_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    list<int> list1;
    vector<int>::iterator iter1, iter2;
    list<int>::iterator list1_Iter, list1_inIter;

    int i;
    for (i = 0; i <= 9; i++)
        v1.push_back(i);

    random_shuffle(v1.begin(), v1.end());

    list1.push_back(60);
    list1.push_back(50);
    list1.push_back(20);
    list1.push_back(30);
    list1.push_back(40);
    list1.push_back(10);

    cout << "Vector v1 = ( " ;
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;

    cout << "List list1 = ( " ;
    for (list1_Iter = list1.begin();
         list1_Iter!= list1.end();
         list1_Iter++)
        cout << *list1_Iter << " ";
    cout << ")" << endl;

    // Copying a partially sorted copy of list1 into v1
    vector<int>::iterator result1;
    result1 = partial_sort_copy(list1.begin(), list1.end(),
             v1.begin(), v1.begin() + 3);

    cout << "List list1 Vector v1 = ( " ;
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;
    cout << "The first v1 element one position beyond"
         << "\n the last L 1 element inserted was " << *result1
         << "." << endl;

    // Copying a partially sorted copy of list1 into v2
    int ii;
    for (ii = 0; ii <= 9; ii++)
        v2.push_back(ii);

    random_shuffle(v2.begin(), v2.end());
    vector<int>::iterator result2;
    result2 = partial_sort_copy(list1.begin(), list1.end(),
             v2.begin(), v2.begin() + 6);

    cout << "List list1 into Vector v2 = ( " ;
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)
        cout << *iter2 << " ";
    cout << ")" << endl;
    cout << "The first v2 element one position beyond"
         << "\n the last L 1 element inserted was " << *result2
         << "." << endl;
}
```

## <a name="partition"></a>  partition

범위의 요소를 두 개의 연결되지 않은 집합으로 분류하고, 단항 조건자를 만족하는 요소는 만족하지 않는 요소보다 앞에 오도록 합니다.

```cpp
template<class BidirectionalIterator, class Predicate>
   BidirectionalIterator partition(
      BidirectionalIterator first,
      BidirectionalIterator last,
      Predicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 범위에서 첫 번째 요소 위치의 주소를 지정 하는 양방향 반복기 분할 되어야 합니다.

*마지막* 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 양방향 반복기 분할 되어야 합니다.

*comp* 인 경우 요소를 분류를 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

조건자 조건을 충족하지 못하는 범위에서 첫 번째 요소 위치의 주소를 지정하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

*Pr* ( *a*,  *b*)가 false이고 *Pr* ( *b*,  *a*)도 false인 경우 *a*와 *b* 요소는 등가이지만 반드시 같음은 아닙니다. 여기서 *Pr*은 매개 변수로 지정된 조건자입니다. `partition` 알고리즘은 안정적이 지 및 됩니다 등가 요소의 상대적인 순서가 유지를 보장 하지 않습니다. `stable_ partition` 알고리즘은 원래의 순서를 유지합니다.

복잡성은 선형: 가지 (`last` - `first`)의 응용 프로그램 *comp* 자에서 (`last` - `first`) / 2 개의 교환이 지원 됩니다.

### <a name="example"></a>예

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value ) {
   return value >5;
}

int main( ) {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 10 ; i++ )
   {
      v1.push_back( i );
   }
   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Partition the range with predicate greater10
   partition ( v1.begin( ), v1.end( ), greater5 );
   cout << "The partitioned set of elements in v1 is: ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="partition_copy"></a>  partition_copy

조건이 인 요소를 복사 **true** 하나의 대상 및 조건이 되 **false** 다른 합니다. 지정된 범위의 요소여야 합니다.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class Predicate>
    pair<OutputIterator1, OutputIterator2>
        partition_copy(
            InputIterator first,
            InputIterator last,
            OutputIterator1 dest1,
            OutputIterator2 dest2,
            Predicate pred
        );
```

### <a name="parameters"></a>매개 변수

*첫 번째* 조건을 검사할 범위의 시작을 나타내는 입력된 반복기입니다.

*마지막* 범위의 끝을 나타내는 입력된 반복기입니다.

*dest1* 사용 하 여 테스트 조건에 대해 true를 반환 하는 요소를 복사 하는 데 사용 하는 출력 반복기 *_Pred*합니다.

*dest2* 사용 하 여 테스트 조건에 대해 false를 반환 하는 요소를 복사 하는 데 사용 하는 출력 반복기 *_Pred*합니다.

*_Pred* 조건에 대 한 테스트입니다. 이 조건은 테스트할 조건을 정의하는 사용자 정의 조건자 함수 개체에 의해 제공됩니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="remarks"></a>설명

각 요소를 복사 하는 템플릿 함수 `X` 에서 `[first,last)` 하 `*dest1++` 하는 경우 `_Pred(X)` 가 true 이면 또는 `*dest2++` 그렇지 않은 경우. `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`를 반환합니다.

## <a name="partition_point"></a>  partition_point

지정된 범위에서 조건을 충족하지 않는 첫 번째 요소를 반환합니다. 조건을 충족하는 요소가 앞에, 그렇지 않는 요소는 뒤에 정렬됩니다.

```cpp
template<class ForwardIterator, class Predicate>
    ForwardIterator partition_point(
        ForwardIterator first,
        ForwardIterator last,
        Predicate comp
    );
```

### <a name="parameters"></a>매개 변수

*첫 번째* 는 `ForwardIterator` 조건을 검사할 범위의 시작을 나타내는입니다.

*마지막* 는 `ForwardIterator` 범위의 끝을 나타내는입니다.

*comp* 조건에 대 한 테스트입니다. 검색 중인 요소가 충족할 조건을 정의하는 사용자 정의 조건자 함수 개체에 의해 제공됩니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

반환을 `ForwardIterator` 참조 하 여 테스트 된 조건을 충족 하지 않는 첫 번째 요소는 *comp*를 반환 하거나 *마지막* 찾지 못한 경우.

### <a name="remarks"></a>설명

템플릿 함수는 첫 번째 반복기를 찾습니다 `it` 에 `[first, last)` 입니다 `comp(*it)` 됩니다 **false**합니다. 시퀀스에서 정렬 되어야 합니다 *comp*합니다.

## <a name="pop_heap"></a>  pop_heap

힙 맨 앞부터 범위의 끝에서 두 번째 위치 중에서 가장 큰 요소를 제거한 다음 나머지 요소로 새 힙을 구성합니다.

```cpp
template<class RandomAccessIterator>
void pop_heap( RandomAccessIterator first, RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 힙에서 첫 번째 요소 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*마지막* 하나 다음 위치의 마지막 요소 힙에서 주소를 지정 하는 임의 액세스 반복기입니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="remarks"></a>설명

`pop_heap` 알고리즘은 push_heap 알고리즘에 의해 수행되는 연산의 반대입니다. push_heap 알고리즘에서는 범위의 마지막 다음 위치에 있는 요소가 범위의 이전 요소로 구성된 힘에 추가되며, 이 경우 힙에 추가되는 요소는 이미 힙에 있는 다른 요소보다 더 큽니다.

힙에는 두 가지 속성이 있습니다.

- 첫 번째 요소는 항상 가장 큽니다.

- 로그 시간에서 요소를 추가하거나 제거할 수 있습니다.

힙은 우선 순위 큐를 구현하는 이상적인 방법이며 C++ 표준 라이브러리 컨테이너 어댑터 [priority_queue 클래스](../standard-library/priority-queue-class.md)의 구현에 사용됩니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

끝에서 새로 추가된 요소를 제외한 범위는 힙이어야 합니다.

복잡성은 로그 이며, 필요한 최대 로그 (* 성-*) 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )  {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 1 ; i <= 9 ; i++ )
      v1.push_back( i );

   // Make v1 a heap with default less than ordering
   random_shuffle( v1.begin( ), v1.end( ) );
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Add an element to the back of the heap
   v1.push_back( 10 );
   push_heap( v1.begin( ), v1.end( ) );
   cout << "The reheaped v1 with 10 added is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove the largest element from the heap
   pop_heap( v1.begin( ), v1.end( ) );
   cout << "The heap v1 with 10 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << endl;

   // Make v1 a heap with greater-than ordering with a 0 element
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   v1.push_back( 0 );
   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The 'greater than' reheaped v1 puts the smallest "
        << "element first:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Application of pop_heap to remove the smallest element
   pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The 'greater than' heaped v1 with the smallest element\n "
        << "removed from the heap is: ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="prev_permutation"></a>  prev_permutation

원래 순서 지정을 사전식으로 이전의 큰 순열(있는 경우)로 대체할 수 있도록 범위의 요소 순서를 재정렬합니다. 여기서 이전의 의미는 이진 조건자로 지정할 수 있습니다.

```cpp
template<class BidirectionalIterator>
   bool prev_permutation(
      BidirectionalIterator first,
      BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
   bool prev_permutation(
      BidirectionalIterator first,
      BidirectionalIterator last,
      BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 순열 수 범위에서 첫 번째 요소의 위치를 가리키는 양방향 반복기입니다.

*마지막* 순열 수 하나 마지막 요소 범위에서 위치를 가리키는 양방향 반복기입니다.

*comp* 순서에 따라 연속적인 요소에 의해 충족 될 비교 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

**true** 사전순으로 이전 순열이 존재를 여 범위의 원래 순서를 교체한 경우 그렇지 않으면 **false**를 사전순으로 가장 큰 값으로 순서 지정은 변환 하는 경우 순열입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

기본 이진 조건자는 더 작으며, 범위의 요소는 이전 순열이 잘 정의되도록 less-than comparable이어야 합니다.

복잡성은 선형 이며 최대 (`last` -  `first`) / 2 개의 교환이 지원 됩니다.

### <a name="example"></a>예

```cpp
// alg_prev_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt {
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main() {
   // Reordering the elements of type CInt in a deque
   // using the prev_permutation algorithm
   CInt c1 = 1, c2 = 5, c3 = 10;
   bool deq1Result;
   deque<CInt> deq1, deq2, deq3;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   deq1Result = prev_permutation ( deq1.begin ( ) , deq1.end ( ) );

   if ( deq1Result )
      cout << "The lexicographically previous permutation "
           << "exists and has \nreplaced the original "
           << "ordering of the sequence in deq1." << endl;
   else
      cout << "The lexicographically previous permutation doesn't "
           << "exist\n and the lexicographically "
           << "smallest permutation\n has replaced the "
           << "original ordering of the sequence in deq1." << endl;

   cout << "After one application of prev_permutation,\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl << endl;

   // Permutating vector elements with binary function mod_lesser
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = -3 ; i <= 3 ; i++ )
      v1.push_back( i );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );

   cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= 5 ) {
      prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );
      cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
         cout << *Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).
The lexicographically previous permutation doesn't exist
 and the lexicographically smallest permutation
 has replaced the original ordering of the sequence in deq1.
After one application of prev_permutation,
 deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first prev_permutation, vector v1 is:
 v1 = ( -3 -2 0 3 2 1 -1 ).
After another prev_permutation of vector v1,
 v1 =   ( -3 -2 0 3 -1 2 1 ).
After another prev_permutation of vector v1,
 v1 =   ( -3 -2 0 3 -1 1 2 ).
After another prev_permutation of vector v1,
 v1 =   ( -3 -2 0 2 3 1 -1 ).
After another prev_permutation of vector v1,
 v1 =   ( -3 -2 0 2 -1 3 1 ).
After another prev_permutation of vector v1,
 v1 =   ( -3 -2 0 2 -1 1 3 ).
```

## <a name="push_heap"></a>  push_heap

범위의 마지막에 있는 요소를 범위의 이전 요소로 구성된 기존 힙에 추가합니다.

```cpp
template<class RandomAccessIterator>
void push_heap( RandomAccessIterator first, RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap( RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 힙에서 첫 번째 요소 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*마지막* 힙으로 변환할 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="remarks"></a>설명

요소를 먼저 기존 힙의 끝으로 다시 푸시해야 하며, 그런 다음 이 요소를 기존 힙에 추가하는 데 알고리즘이 사용됩니다.

힙에는 두 가지 속성이 있습니다.

- 첫 번째 요소는 항상 가장 큽니다.

- 로그 시간에서 요소를 추가하거나 제거할 수 있습니다.

힙은 우선 순위 큐를 구현하는 이상적인 방법이며 C++ 표준 라이브러리 컨테이너 어댑터 [priority_queue 클래스](../standard-library/priority-queue-class.md)의 구현에 사용됩니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

끝에서 새로 추가된 요소를 제외한 범위는 힙이어야 합니다.

복잡성은 로그 이며, 로그 요구에 가장 ( *성-*) 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main( ) {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 1 ; i <= 9 ; i++ )
      v1.push_back( i );

   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with default less than ordering
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Add an element to the heap
   v1.push_back( 10 );
   cout << "The heap v1 with 10 pushed back is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   push_heap( v1.begin( ), v1.end( ) );
   cout << "The reheaped v1 with 10 added is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << endl;

   // Make v1 a heap with greater than ordering
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater-than heaped version of v1 is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   v1.push_back(0);
   cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater than reheaped v1 with 11 added is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="random_shuffle"></a>  random_shuffle

Std::random_shuffle() 함수 되지 바뀝니다 [std:: shuffle](../standard-library/algorithm-functions.md#shuffle)합니다. 코드 예제 및 자세한 내용은 참조 하세요 [ \<임의 >](../standard-library/random.md) 과 Stackoverflow 게시물 [이유는 std:: random_shuffle 메서드가 사용 되지 않는 C + + 14에서?](http://go.microsoft.com/fwlink/p/?linkid=397954)합니다.

## <a name="remove"></a>  remove

나머지 요소의 순서에 영향을 미치거나 지정된 값이 없는 새 범위의 끝을 반환하지 않고 지정된 범위에서 지정된 값을 제거합니다.

```cpp
template<class ForwardIterator, class Type>
 ForwardIterator remove(ForwardIterator first, ForwardIterator last, const Type& val);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 제거 되는 범위의 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 요소가 제거 되는 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 정방향 반복기입니다.

*val* 값 범위에서 제거 하는 것입니다.

### <a name="return-value"></a>반환 값

지정된 값이 없는 나머지 시퀀스의 마지막 요소를 벗어난, 수정된 범위의 새로운 끝 위치에 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

제거되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형; 있습니다 (`last` - `first`) 같은지 비교 합니다.

합니다 [list 클래스](../standard-library/list-class.md) 의 보다 효율적인 멤버 함수 버전이 `remove`은 포인터로 합니다.

### <a name="example"></a>예

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main( ) {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value of 7
   new_end = remove ( v1.begin( ), v1.end( ), 7 );

   cout << "Vector v1 with value 7 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To change the sequence size, use erase
   v1.erase (new_end, v1.end( ) );

   cout << "Vector v1 resized with value 7 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_copy"></a>  remove_copy

소스 범위의 요소를 대상 범위로 복사합니다. 단, 나머지 요소의 순서를 변경하거나 새 대상 범위의 끝을 반환하지 않고 지정된 값의 요소는 복사하지 않습니다.

```cpp
template<class InputIterator, class OutputIterator, class Type>
 OutputIterator remove_copy(InputIterator first, InputIterator last, OutputIterator result, const Type& val);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 제거 되는 범위의 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 요소가 제거 되는 범위에서 마지막 요소 하나의 위치를 지정 하는 입력된 반복기입니다.

*결과* 요소가 제거 되는 대상 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

*val* 값 범위에서 제거 하는 것입니다.

### <a name="return-value"></a>반환 값

지정된 값이 없는 나머지 시퀀스 복사본의 마지막 요소 하나 다음에 대상 범위의 새로운 끝 위치 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 소스 및 대상 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

지정된 값의 요소가 제거된 후 복사할 나머지 요소를 포함할 수 있는 충분한 공간이 대상 범위에 있어야 합니다.

제거되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형; 있습니다 (`last` - `first`) 개의 비교 및 최대 같은지 (`last` - `first`) 할당 합니다.

### <a name="example"></a>예

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2(10);
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle (v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:     ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value of 7
   new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );

   cout << "Vector v1 is left unchanged as ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_copy_if"></a>  remove_copy_if

소스 범위의 요소를 대상 범위로 복사합니다. 단, 나머지 요소의 순서를 변경하거나 새 대상 범위의 끝을 반환하지 않고 조건자를 만족하는 요소는 복사하지 않습니다.

```cpp
template<class InputIterator, class OutputIterator, class Predicate>
OutputIterator remove_copy_if(InputIterator first, InputIterator Last, OutputIterator result, Predicate pred);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 제거 되는 범위의 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*마지막* 요소가 제거 되는 범위에서 마지막 요소 하나의 위치를 지정 하는 입력된 반복기입니다.

*결과* 요소가 제거 되는 대상 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

*_Pred* 만족 해야 하는 단항 조건자는 대체할 요소의 값은입니다.

### <a name="return-value"></a>반환 값

조건자를 충족하는 요소가 없는 나머지 시퀀스의 마지막 요소 하나 다음에 대상 범위의 새로운 끝 위치 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

지정된 값의 요소가 제거된 후 복사할 나머지 요소를 포함할 수 있는 충분한 공간이 대상 범위에 있어야 합니다.

제거되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형: 가지 (`last` - `first`) 개의 비교 및 최대 같은지 (`last` - `first`) 할당 합니다.

이러한 함수의 동작 방식에 대한 자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value >6;
}

int main() {
   using namespace std;
   vector <int> v1, v2(10);
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:      ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value greater than 6
   new_end = remove_copy_if ( v1.begin( ), v1.end( ),
      v2.begin( ), greater6 );

   cout << "After the appliation of remove_copy_if to v1,\n "
        << "vector v1 is left unchanged as ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is a copy of v1 with values greater "
        << "than 6 removed:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_if"></a>  remove_if

나머지 요소의 순서에 영향을 미치거나 지정된 값이 없는 새 범위의 끝을 반환하지 않고 지정된 범위에서 조건자를 만족하는 요소를 제거합니다.

```cpp
template<class ForwardIterator, class Predicate>
 ForwardIterator remove_if(ForwardIterator first, ForwardIterator last, Predicate pred);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 제거 되는 범위의 첫 번째 요소의 위치를 가리키는 정방향 반복기입니다.

*마지막* 요소가 제거 되는 범위에서 마지막 요소 다음 위치를 가리키는 정방향 반복기입니다.

*_Pred* 만족 해야 하는 단항 조건자는 대체할 요소의 값은입니다.

### <a name="return-value"></a>반환 값

지정된 값이 없는 나머지 시퀀스의 마지막 요소를 벗어난, 수정된 범위의 새로운 끝 위치에 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

제거되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형: 가지 (`last` - `first`) 같은지 비교 합니다.

List에는 remove의 더욱 효율적인 멤버 함수 버전이 있습니다. 이 버전은 포인터를 다시 링크합니다.

### <a name="example"></a>예

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value >6;
}

int main( ) {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements satisfying predicate greater6
   new_end = remove_if (v1.begin( ), v1.end( ), greater6 );

   cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To change the sequence size, use erase
   v1.erase (new_end, v1.end( ) );

   cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace"></a>  replace

범위의 각 요소를 검사하고 요소가 지정된 값과 일치하면 대체합니다.

```cpp
template<class ForwardIterator, class Type>
void replace(ForwardIterator first, ForwardIterator last, const Type& _OldVal, const Type& _NewVal);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 대체 되는 범위의 첫 번째 요소의 위치를 가리키는 정방향 반복기입니다.

*마지막* 요소가 대체 되는 범위에서 마지막 요소 다음 위치를 가리키는 정방향 반복기입니다.

*_OldVal* 의 대체 되는 요소의 이전 값입니다.

*_NewVal* 이전 값을 가진 요소에 할당 되는 새 값입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대체되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형; 있습니다 (`last` - `first`) 개의 비교 및 최대 같은지 (`last` - `first`) 개의 새 값 할당이 있습니다.

### <a name="example"></a>예

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main( ) {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle (v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements with a value of 7 with a value of 700
   replace (v1.begin( ), v1.end( ), 7 , 700);

   cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_copy"></a>  replace_copy

소스 범위의 각 요소를 검사하고 요소가 지정된 값과 일치하면 대체하는 동시에 결과를 새 대상 범위로 복사합니다.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& _OldVal,
    const Type& _NewVal);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 대체 되는 범위의 첫 번째 요소의 위치를 가리키는 입력된 반복기입니다.

*마지막* 하나 다음 위치의 마지막 요소에서 요소가 대체 되는 범위를 가리키는 입력된 반복기입니다.

*결과* 변경된 요소 시퀀스를 복사할 대상 범위의 첫 번째 요소를 가리키는 출력 반복기입니다.

*_OldVal* 의 대체 되는 요소의 이전 값입니다.

*_NewVal* 이전 값을 가진 요소에 할당 되는 새 값입니다.

### <a name="return-value"></a>반환 값

변경된 요소 시퀀스를 복사할 대상 범위의 마지막 요소 하나 다음에 대한 위치를 가리키는 출력 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 겹치지 않아야 하고 둘 다 유효해야 합니다. 모든 포인터가 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대체되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형: 가지 (`last` - `first`) 개의 비교 및 최대 같은지 (`last` - `first`) 개의 새 값 할당이 있습니다.

### <a name="example"></a>예

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main( ) {
   using namespace std;
   vector <int> v1;
   list <int> L1 (15);
   vector <int>::iterator Iter1;
   list <int>::iterator L_Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );

   int iii;
   for ( iii = 0 ; iii <= 15 ; iii++ )
      v1.push_back( 1 );

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in one part of a vector with a value of 7
   // with a value of 70 and copy into another part of the vector
   replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);

   cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in a vector with a value of 70
   // with a value of 1 and copy into a list
   replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);

   cout << "The list copy L1 of v1 with the value 0 replacing "
        << "that of 7 is:\n ( " ;
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
      cout << *L_Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_copy_if"></a>  replace_copy_if

소스 범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체하는 동시에 결과를 새 대상 범위로 복사합니다.

```cpp
template<class InputIterator, class OutputIterator, class Predicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Predicate pred,
    const Type& val);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 대체 되는 범위의 첫 번째 요소의 위치를 가리키는 입력된 반복기입니다.

*마지막* 하나 다음 위치의 마지막 요소에서 요소가 대체 되는 범위를 가리키는 입력된 반복기입니다.

*결과* 요소가 복사 되는 대상 범위에서 첫 번째 요소의 위치를 가리키는 출력 반복기입니다.

*_Pred* 만족 해야 하는 단항 조건자는 대체할 요소의 값은입니다.

*val* 조건자를 충족 하는 이전 값을 갖는 요소에 할당 되는 새 값입니다.

### <a name="return-value"></a>반환 값

변경된 요소 시퀀스를 복사할 대상 범위의 마지막 요소 하나 다음에 대한 위치를 가리키는 출력 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 겹치지 않아야 하고 둘 다 유효해야 합니다. 모든 포인터가 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대체되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형; 있습니다 (`last` - `first`) 개의 비교 및 최대 같은지 (`last` - `first`) 개의 새 값 할당이 있습니다.

### <a name="example"></a>예

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value >6;
}

int main( ) {
   using namespace std;
   vector <int> v1;
   list <int> L1 (13);
   vector <int>::iterator Iter1;
   list <int>::iterator L_Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );

   int iii;
   for ( iii = 0 ; iii <= 13 ; iii++ )
      v1.push_back( 1 );

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements with a value of 7 in the 1st half of a vector
   // with a value of 70 and copy it into the 2nd half of the vector
   replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,
      greater6 , 70);

   cout << "The vector v1 with values of 70 replacing those greater"
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in a vector with a value of 70
   // with a value of 1 and copy into a list
   replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),
      greater6 , -1 );

   cout << "A list copy of vector v1 with the value -1\n replacing "
        << "those greater than 6 is:\n ( " ;
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
      cout << *L_Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_if"></a>  replace_if

범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체합니다.

```cpp
template<class ForwardIterator, class Predicate, class Type>
void replace_if(ForwardIterator first, ForwardIterator last, Predicate pred, const Type& val);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소가 대체 되는 범위의 첫 번째 요소의 위치를 가리키는 정방향 반복기입니다.

*마지막* 요소가 대체 되는 범위에서 마지막 요소 다음 위치를 가리키는 반복기입니다.

*_Pred* 만족 해야 하는 단항 조건자는 대체할 요소의 값은입니다.

*val* 조건자를 충족 하는 이전 값을 갖는 요소에 할당 되는 새 값입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대체되지 않은 요소의 순서는 변하지 않고 남아 있습니다.

알고리즘 `replace_if` 알고리즘의 일반화 `replace`, 조건자를 지정된 된 상수 값과 동일 하지 않고 지정할 수 있습니다.

요소 간의 같음을 확인하는 데 사용되는 `operator==` 는 피연산자 간에 동등 관계를 적용해야 합니다.

복잡성은 선형: 가지 (`last` - `first`) 개의 비교 및 최대 같은지 (`last` - `first`) 개의 새 값 할당이 있습니다.

### <a name="example"></a>예

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value >6;
}

int main( ) {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements satisfying the predicate greater6
   // with a value of 70
   replace_if ( v1.begin( ), v1.end( ), greater6 , 70);

   cout << "The vector v1 with a value 70 replacing those\n "
        << "elements satisfying the greater6 predicate is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reverse"></a>  reverse

범위 내에서 요소의 순서를 반대로 바꿉니다.

```cpp
template<class BidirectionalIterator>
 void reverse(BidirectionalIterator first, BidirectionalIterator last);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소는 순열는 범위의 첫 번째 요소의 위치를 가리키는 양방향 반복기입니다.

*마지막* 하나 다음 위치의 마지막 요소는 요소는 순열 있는 범위의 가리키는 양방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

### <a name="example"></a>예

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main( ) {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Reverse the elements in the vector
   reverse (v1.begin( ), v1.end( ) );

   cout << "The modified vector v1 with values reversed is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
 ( 0 1 2 3 4 5 6 7 8 9 ).
The modified vector v1 with values reversed is:
 ( 9 8 7 6 5 4 3 2 1 0 ).
```

## <a name="reverse_copy"></a>  reverse_copy

소스 범위 내의 요소의 순서를 바꾸는 동시에 요소를 대상 범위로 복사합니다.

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator  first,
    BidirectionalIterator Last,
    OutputIterator  result);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 요소는 순열는 소스 범위에 있는 첫 번째 요소의 위치를 가리키는 양방향 반복기입니다.

*마지막* 하나 다음 위치의 마지막 요소는 요소는 순열는 소스 범위에 있는 가리키는 양방향 반복기입니다.

*결과* 요소가 복사 되는 대상 범위에서 첫 번째 요소의 위치를 가리키는 출력 반복기입니다.

### <a name="return-value"></a>반환 값

변경된 요소 시퀀스를 복사할 대상 범위의 마지막 요소 하나 다음에 대한 위치를 가리키는 출력 반복기입니다.

### <a name="remarks"></a>설명

참조된 소스 및 대상 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

### <a name="example"></a>예

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main( ) {
   using namespace std;
   vector <int> v1, v2( 10 );
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Reverse the elements in the vector
   reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );

   cout << "The copy v2 of the reversed vector v1 is:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   cout << "The original vector v1 remains unmodified as:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="rotate"></a>  rotate

인접한 두 범위에 있는 요소를 교환합니다.

```cpp
template<class ForwardIterator>
 void rotate(ForwardIterator first, ForwardIterator middle, ForwardIterator last);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 회전할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*중간* 범위의 첫 번째 부분에 있는와 교환할 요소가 들어 있는 범위의 두 번째 부분에서 첫 번째 요소의 위치 하는 범위 내 경계를 정의 하는 정방향 반복기입니다.

*마지막* 회전할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 선형 이며 최대 (`last` - `first`) 개의 교환이 지원 됩니다.

### <a name="example"></a>예

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main( ) {
   using namespace std;
   vector <int> v1;
   deque <int> d1;
   vector <int>::iterator v1Iter1;
   deque<int>::iterator d1Iter1;

   int i;
   for ( i = -3 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =0 ; ii <= 5 ; ii++ )
   {
      d1.push_back( ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   rotate ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) );
   cout << "After rotating, vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   cout << "The original deque d1 is ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1  << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= d1.end ( ) - d1.begin ( ) ) {
      rotate ( d1.begin ( ) , d1.begin ( ) + 1 , d1.end ( ) );
      cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
      for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
         cout << *d1Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).
The original deque d1 is ( 0 1 2 3 4 5 ).
After the rotation of a single deque element to the back,
 d1 is   ( 1 2 3 4 5 0 ).
After the rotation of a single deque element to the back,
 d1 is   ( 2 3 4 5 0 1 ).
After the rotation of a single deque element to the back,
 d1 is   ( 3 4 5 0 1 2 ).
After the rotation of a single deque element to the back,
 d1 is   ( 4 5 0 1 2 3 ).
After the rotation of a single deque element to the back,
 d1 is   ( 5 0 1 2 3 4 ).
After the rotation of a single deque element to the back,
 d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="rotate_copy"></a>  rotate_copy

소스 범위 내의 인접한 두 범위의 요소를 교환하고 결과를 대상 범위로 복사합니다.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

```

### <a name="parameters"></a>매개 변수

*첫 번째* 회전할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*중간* 범위의 첫 번째 부분에 있는와 교환할 요소가 들어 있는 범위의 두 번째 부분에서 첫 번째 요소의 위치 하는 범위 내 경계를 정의 하는 정방향 반복기입니다.

_ *마지막* 회전할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*결과* 대상 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

### <a name="return-value"></a>반환 값

대상 범위에 있는 마지막 요소의 하나 다음 위치를 가리키는 출력 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 선형 이며 최대 (`last` - `first`) 개의 교환이 지원 됩니다.

### <a name="example"></a>예

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1 , v2 ( 9 );
   deque <int> d1 , d2 ( 6 );
   vector <int>::iterator v1Iter , v2Iter;
   deque<int>::iterator d1Iter , d2Iter;

   int i;
   for ( i = -3 ; i <= 5 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii =0 ; ii <= 5 ; ii++ )
      d1.push_back( ii );

   cout << "Vector v1 is ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
      cout << *v1Iter  << " ";
   cout << ")." << endl;

   rotate_copy ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) , v2.begin ( ) );
   cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
      cout << *v1Iter  << " ";
   cout << ")." << endl;

   cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
      cout << *v2Iter  << " ";
   cout << ")." << endl;

   cout << "The original deque d1 is ( " ;
   for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
      cout << *d1Iter  << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= d1.end ( ) - d1.begin ( ) )
   {
      rotate_copy ( d1.begin ( ) , d1.begin ( ) + iii , d1.end ( ) , d2.begin ( ) );
      cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
      for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
         cout << *d2Iter  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

## <a name="search"></a>  search

대상 범위 내에서 시퀀스의 요소가 지정된 요소 시퀀스와 동일하거나 이진 조건자가 지정한 의미에 따라 지정된 시퀀스의 요소와 동일한 첫 번째 시퀀스를 검색합니다.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
   ForwardIterator1 search(
      ForwardIterator1 first1,
      ForwardIterator1 last1,
      ForwardIterator2 first2,
      ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
   ForwardIterator1 search(
      ForwardIterator1 first1,
      ForwardIterator1 last1,
      ForwardIterator2 first2,
      ForwardIterator2 last2
      Predicate comp);

```

### <a name="parameters"></a>매개 변수

*first1* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*last1* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*first2* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*last2* 일치 시킬 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

지정한 시퀀스와 일치하거나 이진 조건자가 지정한 사항에 따라 동일한 첫 번째 하위 시퀀스의 첫 번째 요소 위치 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

요소와 지정된 값 간의 일치 여부를 확인하는 데 사용되는 `operator==`로서, 피연산자 간에 동등 관계를 적용해야 합니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

평균 복잡성은 검색 범위의 크기에 대해 선형이며, 가장 나쁜 경우의 복잡성도 검색 대상 시퀀스의 크기에 대해 선형입니다.

### <a name="example"></a>예

```cpp
// alg_search.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice (int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main( ) {
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 4 ; ii <= 5 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for first match to L1 under identity
   vector <int>::iterator result1;
   result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is at least one match of L1 in v1"
           << "\n and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = search  (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent\n to those in v2 under the binary "
           << "predicate twice\n and the first one begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 20 25 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
 and the first one begins at position 4.
There is a sequence of elements in v1 that are equivalent
 to those in v2 under the binary predicate twice
 and the first one begins at position 2.
```

## <a name="search_n"></a>  search_n

범위에서 특정 값의 요소가 지정된 수만큼 있거나 이진 조건자가 지정한 해당 값과 관련이 있는 첫 번째 하위 시퀀스를 검색합니다.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
   ForwardIterator1 search_n(
      ForwardIterator1 first1,
      ForwardIterator1 last1,
      Diff2 count,
      const Type& val);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
   ForwardIterator1 search_n(
      ForwardIterator1 first1,
      ForwardIterator1 last1,
      Diff2 count,
      const Type& val,
      BinaryPredicate comp);

```

### <a name="parameters"></a>매개 변수

*first1* 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*last1* 검색할 하나 다음 위치의 마지막 요소 범위에서 주소를 지정 하는 정방향 반복기입니다.

*개수* 검색 하는 하위 시퀀스의 크기입니다.

*val* 검색 대상 시퀀스의 요소 값입니다.

*comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

지정한 시퀀스와 일치하거나 이진 조건자가 지정한 사항에 따라 동일한 첫 번째 하위 시퀀스의 첫 번째 요소 위치 주소를 지정하는 정방향 반복기입니다.

### <a name="remarks"></a>설명

요소와 지정된 값 간의 일치 여부를 확인하는 데 사용되는 `operator==`로서, 피연산자 간에 동등 관계를 적용해야 합니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 검색 결과의 크기와 관련하여 선형입니다.

### <a name="example"></a>예

```cpp
// alg_search_n.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is 1/2 of the first
bool one_half ( int elem1, int elem2 )
{
   return elem1 == 2 * elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( 5  );
   }

   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( 10  );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Searching v1 for first match to (5 5 5) under identity
   vector <int>::iterator result1;
   result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

   if ( result1 == v1.end( ) )
      cout << "There is no match for a sequence ( 5 5 5 ) in v1."
           << endl;
   else
      cout << "There is at least one match of a sequence ( 5 5 5 )"
           << "\n in v1 and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for first match to (5 5 5) under one_half
   vector <int>::iterator result2;
   result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );

   if ( result2 == v1.end( ) )
      cout << "There is no match for a sequence ( 5 5 5 ) in v1"
           << " under the equivalence predicate one_half." << endl;
   else
      cout << "There is a match of a sequence ( 5 5 5 ) "
           << "under the equivalence\n predicate one_half "
           << "in v1 and the first one begins at "
           << "position "<< result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )
There is at least one match of a sequence ( 5 5 5 )
 in v1 and the first one begins at position 6.
There is a match of a sequence ( 5 5 5 ) under the equivalence
 predicate one_half in v1 and the first one begins at position 15.
```

## <a name="set_difference"></a>  set_difference

한 정렬된 소스 범위에 속하지만 두 번째 정렬된 소스 범위에 속하지 않는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
     InputIterator1  first1,
     InputIterator1  last1,
     InputIterator2  first2,
     InputIterator2  last2,
     OutputIterator  result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_difference(
    InputIterator1  first1,
    InputIterator1  last1,
    InputIterator2  first2,
    InputIterator2  last2,
    OutputIterator  result,
    BinaryPredicate  comp );
```

### <a name="parameters"></a>매개 변수

*first1* 통합 하 고 정렬 된 두 소스 범위의 차이 나타내는 단일 범위로 두 개의 정렬 된 소스 범위 중 첫 번째 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 통합 하 고 두 소스 범위의 차이 나타내는 단일 범위로 정렬 하나 다음 위치의 마지막 요소가 첫 번째에서 두 개의 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*first2* 통합 하 고 두 소스 범위의 차이 나타내는 단일 범위로 정렬 위치 첫 번째 요소에서 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*last2* 통합 하 고 두 소스 범위의 차이 나타내는 단일 범위로 정렬에서 하나 다음 위치의 마지막 요소 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*결과* 하며 대상 범위에 있는 두 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기는 두 소스 범위의 차이 나타내는 정렬 된 단일 범위로 통합 수입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

두 소스 범위의 차이를 나타내는 정렬된 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대상 범위는 소스 범위 중 하나와 겹쳐서는 안 되며, 첫 번째 소스 범위를 포함할 수 있을 정도로 커야 합니다.

정렬된 소스 범위는 각각 `set_difference` 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다.

각 범위 내 요소의 상대 순서가 대상 범위에서 유지되므로 작업이 안정적입니다. 소스 범위는 merge 알고리즘에 의해 수정되지 않습니다

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 두 소스 범위에 동일한 요소가 있는 경우 대상 범위에서 첫 번째 범위의 요소가 두 번째 소스 범위의 요소보다 앞에 옵니다. 소스 범위에 중복 요소가 포함되어 두 번째보다 첫 번째 소스 범위에 더 많은 요소가 있는 경우에는 첫 번째 소스 범위에서 해당 요소의 발생 빈도가 두 번째 소스 범위에서 해당 요소의 발생 빈도를 초과하는 횟수가 대상 범위에 포함됩니다.

알고리즘의 복잡성은 선형 이며 최대 2 \* (( *last1-first1*)-( *last2-first2*))-1 비어 있지 않은 소스 범위에 대해 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_set_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if (elem1 < 0)
      elem1 = - elem1;
   if (elem2 < 0)
      elem2 = - elem2;
   return elem1 < elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -1 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 0 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a difference in asscending
   // order with the default binary predicate less <int> ( )
   Result1 = set_difference ( v1a.begin ( ) , v1a.end ( ) ,
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );
   cout << "Set_difference of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a difference in descending
   // order specify binary predicate greater<int>( )
   Result2 = set_difference ( v2a.begin ( ) , v2a.end ( ) ,
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );
   cout << "Set_difference of source ranges with binary"
        << "predicate greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a difference applying a user
   // defined binary predicate mod_lesser
   Result3 = set_difference (  v3a.begin ( ) , v3a.end ( ) ,
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );
   cout << "Set_difference of source ranges with binary "
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_intersection"></a>  set_intersection

정렬된 두 소스 범위에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>매개 변수

*first1* 통합 하 고 정렬 된 두 소스 범위의 교집합을 나타내는 단일 범위로 두 개의 정렬 된 소스 범위 중 첫 번째 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 통합 하 고 두 소스 범위의 교집합을 나타내는 단일 범위로 정렬 하나 다음 위치의 마지막 요소가 첫 번째에서 두 개의 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*first2* 통합 하 고 두 소스 범위의 교집합을 나타내는 단일 범위로 정렬 위치 첫 번째 요소에서 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*last2* 통합 하 고 두 소스 범위의 교집합을 나타내는 단일 범위로 정렬에서 하나 다음 위치의 마지막 요소 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

**_** *결과* 하며 대상 범위에 있는 두 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기는 두 원본의 교집합을 나타내는 정렬 된 단일 범위로 통합 수 범위입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

두 소스 범위의 교집합을 나타내는 정렬된 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대상 범위는 소스 범위 중 하나와 겹쳐서는 안 되며, 대상 범위를 포함할 수 있을 정도로 커야 합니다.

정렬된 소스 범위는 각각 merge 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다.

각 범위 내 요소의 상대 순서가 대상 범위에서 유지되므로 작업이 안정적입니다. 소스 범위는 알고리즘에 의해 수정되지 않습니다

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 두 소스 범위에 동일한 요소가 있는 경우 대상 범위에서 첫 번째 범위의 요소가 두 번째 소스 범위의 요소보다 앞에 옵니다. 소스 범위에 중복 요소가 포함된 경우 두 소스 범위 모두에서 발생하는 중복 요소의 최대 개수가 대상 범위에 포함됩니다.

알고리즘의 복잡성은 선형 이며 최대 2 \* (( *last1-first1*) + ( *last2-first2*))-1 비어 있지 않은 소스 범위에 대해 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main() {
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less than ordering
   int i;
   for ( i = -1 ; i <= 3 ; i++ )
      v1a.push_back( i );

   int ii;
   for ( ii =-3 ; ii <= 1 ; ii++ )
      v1b.push_back( ii );

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );

   cout << "Original vector v2a with range sorted by the\n "
        << "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        << "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
           <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into an intersection in asscending order with the
   // default binary predicate less <int> ( )
   Result1 = set_intersection ( v1a.begin ( ) , v1a.end ( ) ,
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );
   cout << "Intersection of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into an intersection in descending order, specify
   // binary predicate greater<int>( )
   Result2 = set_intersection ( v2a.begin ( ) , v2a.end ( ) ,
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );
   cout << "Intersection of source ranges with binary predicate"
        << " greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into an intersection applying a user-defined
   // binary predicate mod_lesser
   Result3 = set_intersection ( v3a.begin ( ) , v3a.end ( ) ,
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );
   cout << "Intersection of source ranges with binary predicate "
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>  set_symmetric_difference

정렬된 두 소스 범위 중 하나에만 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
 OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );

```

### <a name="parameters"></a>매개 변수

*first1* 통합 하 고 정렬 된 두 소스 범위의 대칭 차를 나타내는 단일 범위로 두 개의 정렬 된 소스 범위 중 첫 번째 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 통합 하 고 두 소스 범위의 대칭 차를 나타내는 단일 범위로 정렬 하나 다음 위치의 마지막 요소가 첫 번째에서 두 개의 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*first2* 통합 하 고 두 소스 범위의 대칭 차를 나타내는 단일 범위로 정렬 위치 첫 번째 요소에서 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*last2* 통합 하 고 두 소스 범위의 대칭 차를 나타내는 단일 범위로 정렬에서 하나 다음 위치의 마지막 요소 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

**_** *결과* 하며 대상 범위에 있는 두 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기는 두 대칭 차를 나타내는 정렬 된 단일 범위로 통합 수 원본 범위입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

두 소스 범위의 대칭차를 나타내는 정렬된 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대상 범위는 소스 범위 중 하나와 겹쳐서는 안 되며, 대상 범위를 포함할 수 있을 정도로 커야 합니다.

정렬된 소스 범위는 각각 `merge*` 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다.

각 범위 내 요소의 상대 순서가 대상 범위에서 유지되므로 작업이 안정적입니다. 소스 범위는 merge 알고리즘에 의해 수정되지 않습니다

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 두 소스 범위에 동일한 요소가 있는 경우 대상 범위에서 첫 번째 범위의 요소가 두 번째 소스 범위의 요소보다 앞에 옵니다. 소스 범위에 중복 요소가 포함된 경우에는 소스 범위 중 하나에서 해당 요소의 발생 빈도가 두 번째 소스 범위에서 해당 요소의 발생 빈도를 초과하는 횟수의 절대값이 대상 범위에 포함됩니다.

알고리즘의 복잡성은 선형 이며 최대 2 \* ((*last1-first1*)-(*last2-first2*))-1 비어 있지 않은 소스 범위에 대해 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_set_sym_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -1 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 0 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference in ascending
   // order with the default binary predicate less <int> ( )
   Result1 = set_symmetric_difference ( v1a.begin ( ) , v1a.end ( ) ,
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );
   cout << "Set_symmetric_difference of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference in descending
   // order, specify binary predicate greater<int>( )
   Result2 = set_symmetric_difference ( v2a.begin ( ) , v2a.end ( ) ,
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );
   cout << "Set_symmetric_difference of source ranges with binary"
        << "predicate greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference applying a user
   // defined binary predicate mod_lesser
   Result3 = set_symmetric_difference ( v3a.begin ( ) , v3a.end ( ) ,
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );
   cout << "Set_symmetric_difference of source ranges with binary "
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_union"></a>  set_union

정렬된 두 소스 범위 중 하나 이상에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>매개 변수

*first1* 통합 하 고 정렬 된 두 소스 범위의 합집합을 나타내는 단일 범위로 두 개의 정렬 된 소스 범위 중 첫 번째 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 통합 하 고 두 소스 범위의 합집합을 나타내는 단일 범위로 정렬 하나 다음 위치의 마지막 요소가 첫 번째에서 두 개의 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*first2* 통합 하 고 두 소스 범위의 합집합을 나타내는 단일 범위로 정렬 위치 첫 번째 요소에서 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

*last2* 통합 하 고 두 소스 범위의 합집합을 나타내는 단일 범위로 정렬에서 하나 다음 위치의 마지막 요소 두 개의 연속 중 두 번째 정렬 된 소스 범위를 지정 하는 입력된 반복기입니다.

**_** *결과* 하며 대상 범위에 있는 두 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기는 두 소스 범위의 합집합을 나타내는 정렬 된 단일 범위로 통합 수입니다.

*comp* 하나의 요소가 다른 인스턴스보다 큰지를 의미를 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 가져와 첫 번째 요소가 두 번째 요소보다 작은 경우 **true** 를 반환하고, 그렇지 않은 경우 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

두 소스 범위의 합집합을 나타내는 정렬된 대상 범위에서 마지막 요소 하나 다음 위치의 주소를 지정하는 입력 반복기입니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

대상 범위는 소스 범위 중 하나와 겹쳐서는 안 되며, 대상 범위를 포함할 수 있을 정도로 커야 합니다.

정렬된 소스 범위는 각각 `merge` 알고리즘에서 결합된 범위를 정렬하는 데 사용하는 것과 동일한 순서에 따라 알고리즘을 적용하기 위한 사전 조건으로 배열되어야 합니다.

각 범위 내 요소의 상대 순서가 대상 범위에서 유지되므로 작업이 안정적입니다. 소스 범위는 알고리즘에 의해 수정 되지 않습니다 `merge`합니다.

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 정렬이 수행됩니다. 두 소스 범위에 동일한 요소가 있는 경우 대상 범위에서 첫 번째 범위의 요소가 두 번째 소스 범위의 요소보다 앞에 옵니다. 소스 범위에 중복 요소가 포함된 경우 두 소스 범위 모두에서 발생하는 중복 요소의 최대 개수가 대상 범위에 포함됩니다.

알고리즘의 복잡성은 선형 이며 최대 2 \* (( *last1-first1*)-( *last2-first2*))-1 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_set_union.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a, Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less than ordering
   int i;
   for ( i = -1 ; i <= 3 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 1 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
   vector <int>::iterator Iter2a,  Iter2b, Iter2, Result2;
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a union in ascending order with the default
    // binary predicate less <int> ( )
   Result1 = set_union ( v1a.begin ( ) , v1a.end ( ) ,
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );
   cout << "Union of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a union in descending order, specify binary
   // predicate greater<int>( )
   Result2 = set_union (  v2a.begin ( ) , v2a.end ( ) ,
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );
   cout << "Union of source ranges with binary predicate greater "
        << "specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a union applying a user-defined
   // binary predicate mod_lesser
   Result3 = set_union ( v3a.begin ( ) , v3a.end ( ) ,
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );
   cout << "Union of source ranges with binary predicate "
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="shuffle"></a>  std::shuffle

난수 생성기를 사용하여 지정된 범위 내 요소의 순서를 섞습니다(다시 정렬).

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 를 섞으 (포함) 범위의 첫 번째 요소에 대 한 반복기입니다. 
          `RandomAccessIterator` 및 `ValueSwappable`의 요구 사항을 충족해야 합니다.

*마지막* 섞으, 배타적 범위에서 마지막 요소에 대 한 반복기입니다. 
          `RandomAccessIterator` 및 `ValueSwappable`의 요구 사항을 충족해야 합니다.

*gen* 난수 생성기는는 `shuffle()` 함수 작업에 사용 됩니다. `UniformRandomNumberGenerator`의 요구 사항을 충족해야 합니다.

### <a name="remarks"></a>설명

자세한 내용과 `shuffle()`을 사용하는 코드 샘플은 [\<random>](../standard-library/random.md)을 참조하세요.

## <a name="sort"></a>  sort

지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬합니다.

```cpp
template<class RandomAccessIterator>
   void sort(
      RandomAccessIterator first,
      RandomAccessIterator last);

template<class RandomAccessIterator, class Predicate>
   void sort(
      RandomAccessIterator first,
      RandomAccessIterator last,
      Predicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 정렬할 범위에서 첫 번째 요소 위치의 주소를 지정 된 임의 액세스 반복기입니다.

*마지막* 정렬할 범위에서 마지막 요소 하나의 위치를 주소 지정을 임의 액세스 반복기입니다.

*comp* 순서에 따라 연속적인 요소에 의해 충족 될 비교 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 이 이진 조건자가 두 개의 인수를 받아서 반환 **true** 두 인수가 순서 대로 되어 있으면 및 **false** 그렇지 않은 경우. 이 비교 함수는 시퀀스의 요소 쌍에 대해 엄밀히 약한 순서를 적용해야 합니다. 자세한 내용은 [알고리즘](../standard-library/algorithms.md)을 참조하세요.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

둘 중 어느 요소도 다른 것보다 작지 않은 경우 두 요소는 등가이지만, 반드시 같은 것은 아닙니다. `sort` 알고리즘은 안정적이지 않으므로 등가 요소의 상대적인 순서가 유지될 것임을 보증하지 않습니다. `stable_sort` 알고리즘은 원래의 순서를 유지합니다.

정렬 복잡성의 평균은 *O*( *N* 로그 *N*), 여기서 *N* =  *마지막-첫 번째*.

### <a name="example"></a>예

```cpp
// alg_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
   {
      v1.push_back( 2 * ii + 1 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order. specify binary predicate
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted (greater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   sort( v1.begin( ), v1.end( ), UDgreater );
   cout << "Resorted (UDgreater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
```

## <a name="sort_heap"></a>  sort_heap

힙을 정렬된 범위로 변환합니다.

```cpp
template<class RandomAccessIterator>
   void sort_heap(
      RandomAccessIterator first,
      RandomAccessIterator last);

template<class RandomAccessIterator, class Predicate>
   void sort_heap(
      RandomAccessIterator first,
      RandomAccessIterator last,
      Predicate comp);
```

### <a name="parameters"></a>매개 변수

*첫 번째* 대상 힙에서 첫 번째 요소 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*마지막* 대상 힙의 마지막 요소 하나 위치의 주소를 지정 하는 임의 액세스 반복기입니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="remarks"></a>설명

힙에는 두 가지 속성이 있습니다.

- 첫 번째 요소는 항상 가장 큽니다.

- 로그 시간에서 요소를 추가하거나 제거할 수 있습니다.

이 알고리즘을 적용하고 나면 적용된 범위가 더 이상 힙이 아닙니다.

등가 요소의 상대적 순서가 반드시 유지되지는 않으므로 이것은 안정적인 정렬이 아닙니다.

힙은 우선 순위 큐를 구현하는 이상적인 방법이며 C++ 표준 라이브러리 컨테이너 어댑터 [priority_queue 클래스](../standard-library/priority-queue-class.md)의 구현에 사용됩니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 많아야 *N* 로그 *N*여기서 *N* = ( *성-*).

### <a name="example"></a>예

```cpp
// alg_sort_heap.cpp
// compile with: /EHsc
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>
#include <string>
#include <vector>
using namespace std;

void print(const string& s, const vector<int>& v) {
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i) {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main() {
    vector<int> v;
    for (int i = 1; i <= 9; ++i) {
        v.push_back(i);
    }
    print("Initially", v);

    random_shuffle(v.begin(), v.end());
    print("After random_shuffle", v);

    make_heap(v.begin(), v.end());
    print("     After make_heap", v);

    sort_heap(v.begin(), v.end());
    print("     After sort_heap", v);

    random_shuffle(v.begin(), v.end());
    print("             After random_shuffle", v);

    make_heap(v.begin(), v.end(), greater<int>());
    print("After make_heap with greater<int>", v);

    sort_heap(v.begin(), v.end(), greater<int>());
    print("After sort_heap with greater<int>", v);
}
```

## <a name="stable_partition"></a>  stable_partition

범위의 요소를 두 개의 연결되지 않은 집합으로 분류하고, 단항 조건자를 만족하는 요소는 만족하지 않는 요소보다 앞에 오도록 하여 동등한 요소의 상대적 관계를 유지합니다.

```cpp
template<class BidirectionalIterator, class Predicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Predicate pred );

```

### <a name="parameters"></a>매개 변수

*첫 번째* 범위에서 첫 번째 요소 위치의 주소를 지정 하는 양방향 반복기 분할 되어야 합니다.

*마지막* 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 양방향 반복기 분할 되어야 합니다.

*_Pred* 인 경우 요소를 분류를 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 조건자는 단일 인수를 받아서 **true** 또는 **false**를 반환합니다.

### <a name="return-value"></a>반환 값

조건자 조건을 충족하지 못하는 범위에서 첫 번째 요소 위치의 주소를 지정하는 양방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

*Pr* ( *a*,  *b*)가 false이고 *Pr* ( *b*,  *a*)도 false인 경우 *a*와 *b* 요소는 등가이지만 반드시 같음은 아닙니다. 여기서 *Pr*은 매개 변수로 지정된 조건자입니다. `stable_ partition` 알고리즘은 안정적 이며 등가 요소의 상대적인 순서가 유지 것임을 보증 됩니다. 알고리즘 `partition` 반드시 유지 이렇게 원래 순서를 지정 합니다.

### <a name="example"></a>예

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value ) {
   return value >5;
}

int main( ) {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, result;

   int i;
   for ( i = 0 ; i <= 10 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 4 ; ii++ )
      v1.push_back( 5 );

   random_shuffle(v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Partition the range with predicate greater10
   result = stable_partition (v1.begin( ), v1.end( ), greater5 );
   cout << "The partitioned set of elements in v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "The first element in v1 to fail to satisfy the"
        << "\n predicate greater5 is: " << *result << "." << endl;
}
```

## <a name="stable_sort"></a>  stable_sort

지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬하고 동등한 요소의 상대적 관계를 유지합니다.

```cpp
template<class BidirectionalIterator>
 void stable_sort( BidirectionalIterator first, BidirectionalIterator last );

template<class BidirectionalIterator, class BinaryPredicate>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate comp );

```

### <a name="parameters"></a>매개 변수

*첫 번째* 범위에서 첫 번째 요소 위치의 주소를 지정 하는 양방향 반복기 정렬 되어야 합니다.

*마지막* 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 양방향 반복기 정렬 되어야 합니다.

*comp* 순서에 따라 연속적인 요소에 의해 충족 될 비교 조건을 정의 하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

둘 중 어느 요소도 다른 것보다 작지 않은 경우 두 요소는 등가이지만, 반드시 같은 것은 아닙니다. `sort` 알고리즘은 안정적 이며 등가 요소의 상대적인 순서가 유지 것임을 보증 됩니다.

런타임 복잡성 `stable_sort` 사용 가능한 메모리의 양에 따라 달라 집니다 (메모리가 충분 한) 모범 사례 이지만 *O*( *N* log *N*) 및 최악의 경우 됩니다 *O*( *N* (log *N* ) 2) 여기서 *N* =  *성-이름입니다.* 일반적으로 `sort` 알고리즘은 보다 훨씬 빠릅니다 `stable_sort`합니다.

### <a name="example"></a>예

```cpp
// alg_stable_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater (int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i  );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   stable_sort(v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order, specify binary predicate
   stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted (greater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   stable_sort(v1.begin( ), v1.end( ), UDgreater );
   cout << "Resorted (UDgreater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
```

## <a name="swap"></a>  swap

첫 번째 재정의는 두 개체의 값을 교환합니다. 두 번째 재정의는 두 개체 배열 간에 값을 교환합니다.

```cpp
template<class Type>
   void swap(
      Type& left,
      Type& right);
template<class Type, size_t N>
   void swap(
      Type (& left)[N],
      Type (& right)[N]);\r

```

### <a name="parameters"></a>매개 변수

*왼쪽* 첫 번째 재정의에서는 교환 내용이 있는 첫 번째 개체입니다. 두 번째 재정의에서는 내용이 있는 첫 번째 개체 배열이 교환됩니다.

*오른쪽* 첫 번째 재정의에서는 교환 내용이 있는 두 번째 개체입니다. 두 번째 재정의에서는 내용이 있는 두 번째 개체 배열이 교환됩니다.

### <a name="remarks"></a>설명

첫 번째 오버로드는 개별 개체에서 작동하도록 설계되었습니다. 두 번째 오버로드는 두 배열 간에 개체의 내용을 교환합니다.

### <a name="example"></a>예

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, result;

   for ( int i = 0 ; i <= 10 ; i++ )
   {
      v1.push_back( i );
   }

   for ( int ii = 0 ; ii <= 4 ; ii++ )
   {
      v2.push_back( 5 );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   swap( v1, v2 );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
Vector v2 is ( 5 5 5 5 5 ).
Vector v1 is ( 5 5 5 5 5 ).
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
```

## <a name="swap_ranges"></a>  swap_ranges

한 범위의 요소를 크기가 동일한 다른 범위의 요소로 교환합니다.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

```

### <a name="parameters"></a>매개 변수

*first1* 범위의 첫 번째 요소를 교환할 첫 번째 위치를 가리키는 정방향 반복기입니다.

*last1* 지난 요소를 교환할 요소가 들어 있는 첫 번째 범위의 마지막 위치를 가리키는 정방향 반복기입니다.

*first2* 요소가를 교환할 두 번째 범위의 첫 번째 위치를 가리키는 정방향 반복기입니다.

### <a name="return-value"></a>반환 값

요소를 교환할 두 번째 범위의 마지막 위치 하나 다음을 가리키는 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다. 두 번째 범위는 첫 번째 범위 정도의 크기여야 합니다.

복잡성은 선형 이며 *last1* - *first1* 개의 교환이 수행 합니다. 멤버 함수는 일반적으로 일관된 복잡성을 가지고 있기 때문에, 동일한 유형의 컨테이너에서 요소를 교환하는 경우 해당 컨테이너의 `swap` 멤버 함수를 사용해야 합니다.

### <a name="example"></a>예

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   deque <int> d1;
   vector <int>::iterator v1Iter1;
   deque<int>::iterator d1Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =4 ; ii <= 9 ; ii++ )
   {
      d1.push_back( 6 );
   }

   cout << "Vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   cout << "Deque d1 is  ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1  << " ";
   cout << ")." << endl;

   swap_ranges ( v1.begin ( ) , v1.end ( ) , d1.begin ( ) );

   cout << "After the swap_range, vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1 << " ";
   cout << ")." << endl;

   cout << "After the swap_range deque d1 is   ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 ).
Deque d1 is  ( 6 6 6 6 6 6 ).
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="transform"></a>  transform

두 소스 범위에서 요소 쌍에 또는 소스 범위에 있는 각 요소에 지정된 함수 개체를 적용하고 대상 범위에 함수 개체의 반환 값을 복사합니다.

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction _Func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction _Func );
```

### <a name="parameters"></a>매개 변수

*first1* 작업을 수행할 첫 번째 소스 범위에 있는 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*last1* 첫 번째 소스 범위에서 마지막 요소 하나의 위치를 지정 하는 입력된 반복기에 연산을 수행 합니다.

*first2* 작업을 수행할 두 번째 소스 범위에 있는 첫 번째 요소 위치의 주소를 지정 하는 입력된 반복기입니다.

*결과* 대상 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

*_Func* 첫 번째 소스 범위 또는 적용 되는 알고리즘의 두 번째 버전에 사용 되는 사용자 정의 (UD) 이항 함수 개체의 각 요소에 적용 되는 알고리즘의 첫 번째 버전에서 사용 되는 사용자 정의 단항 함수 개체 쌍으로 정방향 순서로 두 소스 범위에 있습니다.

### <a name="return-value"></a>반환 값

함수 개체에 의해 변형된 출력 요소를 받는 대상 범위에서 최종 요소의 하나 다음 위치를 주소 지정하는 출력 반복기입니다.

### <a name="remarks"></a>설명

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 각 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다. 대상 범위는 변환된 소스 범위를 포함할 만큼 충분히 커야 합니다.

하는 경우 *결과* 으로 설정 되었습니다 *first1* 알고리즘의 첫 번째 버전에서는 다음 원본 및 대상 범위는 동일 하 고 현재 위치에서 시퀀스를 수정 합니다. 하지만 *결과* 범위 내에 위치를 다루지 않을 수 있습니다 [`first1` + 1 `last1`).

복잡성은 선형 이며 최대 (`last1` - `first1`) 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_transform.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
   private:
      Type Factor;   // The value to multiply by
   public:
      // Constructor initializes the value to multiply by
      MultValue ( const Type& val ) : Factor ( val ) {
      }

      // The function call for the element to be multiplied
      Type operator ( ) ( Type& elem ) const
      {
         return elem * Factor;
      }
};

int main( )
{
   using namespace std;
   vector <int> v1, v2 ( 7 ), v3 ( 7 );
   vector <int>::iterator Iter1, Iter2 , Iter3;

   // Constructing vector v1
   int i;
   for ( i = -4 ; i <= 2 ; i++ )
   {
      v1.push_back(  i );
   }

   cout << "Original vector  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Modifying the vector v1 in place
   transform (v1.begin ( ) , v1.end ( ) , v1.begin ( ) , MultValue<int> ( 2 ) );
   cout << "The elements of the vector v1 multiplied by 2 in place gives:"
        << "\n v1mod = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Using transform to multiply each element by a factor of 5
   transform ( v1.begin ( ) , v1.end ( ) , v2.begin ( ) , MultValue<int> ( 5 ) );

   cout << "Multiplying the elements of the vector v1mod\n "
        <<  "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // The second version of transform used to multiply the
   // elements of the vectors v1mod & v2 pairwise
   transform ( v1.begin ( ) , v1.end ( ) ,  v2.begin ( ) , v3.begin ( ) ,
      multiplies <int> ( ) );

   cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
        <<  "gives:\n v3 = ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

```Output
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
 v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
 by the factor 5 & copying to v2 gives:
 v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
 v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>  unique

지정된 범위에서 서로 인접한 중복 요소를 제거합니다.

```cpp
template<class ForwardIterator>
   ForwardIterator unique(
      ForwardIterator first,
      ForwardIterator last);

template<class ForwardIterator, class Predicate>
   ForwardIterator unique(
      ForwardIterator first,
      ForwardIterator last,
      Predicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 중복 제거를 위해 검색할 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 하나 다음 위치의 마지막 요소를 검색 하 여 중복 제거에 대 한 범위에서 주소를 지정 하는 정방향 반복기입니다.

*comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

연속 중복 항목을 포함하지 않는 수정된 시퀀스의 새로운 끝에 대한 정방향 반복기로, 제거되지 않은 마지막 요소 하나 다음 위치의 주소를 지정합니다.

### <a name="remarks"></a>설명

두 알고리즘 모두 동일한 요소의 연속된 쌍 중 두 번째 중복을 제거합니다.

알고리즘의 작업이 안정적이므로 삭제되지 않은 요소의 상대 순서가 변경되지 않습니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다. 시퀀스의 요소 수는 알고리즘에 의해 변경 되지 않습니다 `unique` 및 수정 된 시퀀스의 끝 너머에 있는 요소는 역참조가 가능 하지만 지정 되지 않았습니다.

복잡성은 선형 이며 요구 (`last` - `first`)-1 비교 합니다.

List는 성능이 더 뛰어나고 좀 더 효과적인 멤버 함수인 "unique"를 제공합니다.

이러한 알고리즘은 연관 컨테이너에서 사용할 수 없습니다.

### <a name="example"></a>예

```cpp
// alg_unique.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 == elem2;
};

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
         v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( 5 );
      v1.push_back( -5 );
   }

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
   {
      v1.push_back( 4 );
   }
   v1.push_back( 7 );

   cout << "Vector v1 is ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Remove consecutive duplicates
   v1_NewEnd1 = unique ( v1.begin ( ) , v1.end ( ) );

   cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Remove consecutive duplicates under the binary prediate mod_equals
   v1_NewEnd2 = unique ( v1.begin ( ) , v1_NewEnd1 , mod_equal );

   cout << "Removing adjacent duplicates from vector v1 under the\n "
        << " binary predicate mod_equal gives\n ( " ;
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
      cout << *v1_Iter2 << " ";
   cout << ")." << endl;

   // Remove elements if preceded by an element that was greater
   v1_NewEnd3 = unique ( v1.begin ( ) , v1_NewEnd2, greater<int>( ) );

   cout << "Removing adjacent elements satisfying the binary\n "
        << " predicate mod_equal from vector v1 gives ( " ;
   for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )
      cout << *v1_Iter3 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).
Removing adjacent duplicates from vector v1 gives
 ( 5 -5 5 -5 5 -5 5 -5 4 7 ).
Removing adjacent duplicates from vector v1 under the
  binary predicate mod_equal gives
 ( 5 4 7 ).
Removing adjacent elements satisfying the binary
  predicate mod_equal from vector v1 gives ( 5 7 ).
```

## <a name="unique_copy"></a>  unique_copy

서로 인접한 중복 요소를 제외하고 소스 범위의 요소를 대상 범위로 복사합니다.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy( InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy( InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>매개 변수

*첫 번째* 복사할 소스 범위에서 첫 번째 요소 위치의 주소를 지정 하는 정방향 반복기입니다.

*마지막* 복사할 소스 범위에서 마지막 요소 하나 위치의 주소를 지정 하는 정방향 반복기입니다.

*결과* 제거 연속 중복 된 복사본을 수신 하는 대상 범위에서 첫 번째 요소 위치의 주소를 지정 하는 출력 반복기입니다.

*comp* 두 요소에서 수행 하려는 경우 충족 해야 할 조건을 정의 하는 사용자 정의 조건자 함수 개체와 동일 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

연속 중복 항목이 제거된 복사본을 수신하는 대상 범위에서 마지막 요소 하나 다음 위치의 주소 지정하는 출력 반복기입니다.

### <a name="remarks"></a>설명

두 알고리즘 모두 동일한 요소의 연속된 쌍 중 두 번째 중복을 제거합니다.

알고리즘의 작업이 안정적이므로 삭제되지 않은 요소의 상대 순서가 변경되지 않습니다.

참조된 범위는 유효해야 하고 모든 포인터는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

복잡성은 선형 이며 요구 (`last` - `first`) 비교 합니다.

### <a name="example"></a>예

```cpp
// alg_unique_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 == elem2;
};

int main() {
   vector <int> v1;
   vector <int>::iterator v1_Iter1, v1_Iter2,
         v1_NewEnd1, v1_NewEnd2;

   int i;
   for ( i = 0 ; i <= 1 ; i++ ) {
      v1.push_back( 5 );
      v1.push_back( -5 );
   }

   int ii;
   for ( ii = 0 ; ii <= 2 ; ii++ )
      v1.push_back( 4 );
   v1.push_back( 7 );

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
      v1.push_back( 10 );

   cout << "Vector v1 is\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Copy first half to second, removing consecutive duplicates
   v1_NewEnd1 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 8, v1.begin ( ) + 8 );

   cout << "Copying the first half of the vector to the second half\n "
        << "while removing adjacent duplicates gives\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   int iv;
   for ( iv = 0 ; iv <= 7 ; iv++ )
      v1.push_back( 10 );

   // Remove consecutive duplicates under the binary prediate mod_equals
   v1_NewEnd2 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 14,
      v1.begin ( ) + 14 , mod_equal );

   cout << "Copying the first half of the vector to the second half\n "
        << " removing adjacent duplicates under mod_equals gives\n ( " ;
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
      cout << *v1_Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="upper_bound"></a>  upper_bound

지정된 값보다 큰 값을 갖는 정렬된 범위에 있는 첫 번째 요소의 위치를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

```cpp
template<class ForwardIterator, class Type>
   ForwardIterator upper_bound(
      ForwardIterator first,
      ForwardIterator last,
      const Type& value);

template<class ForwardIterator, class Type, class Predicate>
   ForwardIterator upper_bound(
      ForwardIterator first,
      ForwardIterator last,
      const Type& value,
      Predicate comp);

```

### <a name="parameters"></a>매개 변수

*첫 번째* 검색할 범위에서 첫 번째 요소의 위치입니다.

*마지막* 하나 다음 위치의 마지막 요소를 검색할 범위에서.

*값* 반복기가 주소를 지정 하는 요소 값을 기준으로 초과 해야 하는 정렬된 된 범위에서 값을 반환 합니다.

*comp* 정의 하는 사용자 정의 조건자 함수 개체는 하나의 요소에 다른 노드보다 작은지 감지 합니다. 이진 조건자는 두 개의 인수를 사용하며 조건이 충족되면 **true** 를 반환하고, 충족되지 않으면 **false** 를 반환합니다.

### <a name="return-value"></a>반환 값

지정된 값보다 큰 값을 가진 첫 번째 요소의 위치에 대한 정방향 반복기입니다.

### <a name="remarks"></a>설명

참조된 정렬된 소스 범위는 유효해야 하고 모든 반복기는 역참조 가능해야 하며 시퀀스 내에서 처음 위치에서 증분하여 마지막 위치까지 도달할 수 있어야 합니다.

정렬된 범위는 `upper_bound` 사용의 사전 조건이며 순서 기준은 이진 조건자로 지정된 것과 같습니다.

범위는 `upper_bound`에 의해 수정되지 않습니다.

입력 반복기의 값 형식은 보다 작음을 비교하여 순서를 지정할 수 있어야 합니다. 즉, 지정된 두 요소가 동일하거나(어느 것도 다른 것보다 작지 않다는 의미에서) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 비등가 요소 사이에 정렬이 수행됩니다.

알고리즘의 복잡성은 임의 액세스 반복기에 대 한 로그 및 선형 비례 하는 단계 수 이며 그렇지 않은 경우 (`last - first`).

### <a name="example"></a>예

```cpp
// alg_upper_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main( )
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back(  i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back(  ii  );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate upper_bound

    vector<int>::iterator Result;

    // upper_bound of 3 in v1 with default binary predicate less<int>()
    Result = upper_bound(v1.begin(), v1.end(), 3);
    cout << "The upper_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The upper_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v3 with the binary predicate  mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3,  mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}

```
## <a name="see-also"></a>참고자료

[\<algorithm>](../standard-library/algorithm.md)<br/>