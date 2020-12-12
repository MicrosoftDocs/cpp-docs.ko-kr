---
description: '자세히 알아보기: 알고리즘 (STL/CLR)'
title: algorithm(STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
ms.openlocfilehash: 450a4afdf5c5d697d722e92132c5c59e74064f5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282837"
---
# <a name="algorithm-stlclr"></a>algorithm(STL/CLR)

알고리즘을 수행 하는 STL/CLR 컨테이너 템플릿 함수를 정의 합니다.

## <a name="syntax"></a>Syntax

```cpp
#include <cliext/algorithm>
```

## <a name="requirements"></a>요구 사항

**헤더:**\<cliext/algorithm>

**네임 스페이스:** cliext

## <a name="declarations"></a>선언

|함수|설명|
|--------------|-----------------|
|[adjacent_find(STL/CLR)](#adjacent_find)|동일한 두 개의 인접 요소를 검색 합니다.|
|[binary_search(STL/CLR)](#binary_search)|정렬 된 시퀀스에 지정 된 값이 포함 되어 있는지 여부를 테스트 합니다.|
|[copy(STL/CLR)](#copy)|원본 범위의 값을 대상 범위로 복사 하 여 정방향 방향으로 반복 합니다.|
|[copy_backward(STL/CLR)](#copy_backward)|원본 범위의 값을 대상 범위로 복사 하 여 역방향으로 반복 합니다.|
|[count(STL/CLR)](#count)|해당 값이 지정된 값과 일치하는 요소의 개수를 반환합니다.|
|[count_if(STL/CLR)](#count_if)|해당 값이 지정된 조건과 일치하는 요소의 개수를 반환합니다.|
|[equal(STL/CLR)](#equal)|요소 별로 두 범위를 비교 합니다.|
|[equal_range(STL/CLR)](#equal_range)|지정 된 요소와 동일한 값의 하위 시퀀스를 구분 하는 두 개의 위치를 반환 하는 값의 순서가 지정 된 시퀀스를 검색 합니다.|
|[fill(STL/CLR)](#fill)|지정한 범위의 모든 요소에 동일한 새 값을 할당합니다.|
|[fill_n(STL/CLR)](#fill_n)|특정 요소로 시작하는 범위에서 지정된 개수의 요소에 새 값을 할당합니다.|
|[find(STL/CLR)](#find)|지정 된 값이 처음 나타나는 위치를 반환 합니다.|
|[find_end(STL/CLR)](#find_end)|범위에서 지정 된 시퀀스와 동일한 마지막 하위 시퀀스를 반환 합니다.|
|[find_first_of(STL/CLR)](#find_first_of)|범위에서 지정 된 요소 범위 중 하나가 처음 나타나는 위치를 검색 합니다.|
|[find_if(STL/CLR)](#find_if)|요소가 지정 된 조건을 만족 하는 값 시퀀스에서 첫 번째 요소의 위치를 반환 합니다.|
|[for_each(STL/CLR)](#for_each)|값 시퀀스의 각 요소에 지정 된 함수 개체를 적용 하 고 함수 개체를 반환 합니다.|
|[generate(STL/CLR)](#generate)|값 시퀀스의 각 요소에 함수 개체에 의해 생성 된 값을 할당 합니다.|
|[generate_n(STL/CLR)](#generate_n)|함수 개체에 의해 생성 된 값을 지정 된 수의 요소에 할당 합니다.|
|[includes(STL/CLR)](#includes)|정렬 된 한 범위가 두 번째 정렬 된 범위에 있는 모든 요소를 포함 하는지 여부를 테스트 합니다.|
|[inplace_merge(STL/CLR)](#inplace_merge)|두 개의 연속 정렬 된 범위에 있는 요소를 정렬 된 단일 범위로 결합 합니다.|
|[iter_swap(STL/CLR)](#iter_swap)|지정된 반복기의 쌍이 참조하는 두 값을 교환합니다.|
|[lexicographical_compare(STL/CLR)](#lexicographical_compare)|두 시퀀스를 요소 별로 비교 하 여 둘 중 작은 시퀀스를 식별 합니다.|
|[lower_bound(STL/CLR)](#lower_bound)|지정 된 값 보다 크거나 같은 값을 포함 하는 순서가 지정 된 시퀀스에서 첫 번째 요소의 위치를 찾습니다.|
|[make_heap(STL/CLR)](#make_heap)|지정 된 범위의 요소를 힙의 첫 번째 요소가 가장 큰 힙으로 변환 합니다.|
|[max (STL/CLR)](#max))|두 개체를 비교 하 여 두 개체 중 더 큰 값을 반환 합니다.|
|[max_element(STL/CLR)](#max_element)|지정 된 값 시퀀스에서 가장 큰 요소를 찾습니다.|
|[merge (STL/CLR)](#merge)|정렬 된 두 소스 범위의 모든 요소를 정렬 된 단일 대상 범위로 결합 합니다.|
|[min(STL/CLR)](#min)|두 개체를 비교 하 여 두 개체 중 작은 값을 반환 합니다.|
|[min_element(STL/CLR)](#min_element)|지정 된 값 시퀀스에서 가장 작은 요소를 찾습니다.|
|[mismatch(STL/CLR)](#mismatch)|두 범위를 요소 별로 비교 하 고 차이가 발생 한 첫 번째 위치를 반환 합니다.|
|[next_permutation(STL/CLR)](#next_permutation)|원래 순서가 있는 경우 사전순으로 다음으로 더 큰 순열으로 바뀌는 범위에서 요소의 순서를 다시 지정 합니다.|
|[nth_element(STL/CLR)](#nth_element)|요소의 시퀀스를 분할 하 여 시퀀스의 th 요소를 정확 하 게 찾아 그 앞의 모든 요소가 해당 요소 보다 `n` 작거나 같고 그 다음에 나오는 모든 요소가 해당 요소 보다 크거나 같아야 합니다.|
|[partial_sort(STL/CLR)](#partial_sort)|범위에 있는 지정 된 수의 더 작은 요소를 비 내림차순으로 정렬 합니다.|
|[partial_sort_copy(STL/CLR)](#partial_sort_copy)|원본 범위의 요소가 정렬 되도록 소스 범위의 요소를 대상 범위로 복사 합니다.|
|[partition(STL/CLR)](#partition)|단항 조건자를 만족 하는 요소가이를 만족 하지 않는 요소 보다 앞에 오도록 범위에 있는 요소를 정렬 합니다.|
|[pop_heap(STL/CLR)](#pop_heap)|힙의 맨 앞에서 끝으로 가장 큰 요소를 이동한 다음 나머지 요소에서 새 힙을 형성 합니다.|
|[prev_permutation(STL/CLR)](#prev_permutation)|원래 순서를 사전순으로 이전 더 큰 순열 (있는 경우)으로 바꾸도록 요소 시퀀스의 순서를 다시 지정 합니다.|
|[push_heap(STL/CLR)](#push_heap)|범위의 마지막에 있는 요소를 범위의 이전 요소로 구성된 기존 힙에 추가합니다.|
|[random_shuffle(STL/CLR)](#random_shuffle)|`N`범위에 있는 요소의 시퀀스를 다음 중 하나로 다시 정렬 합니다 `N` . 가능 배열 중 하나로 재정렬합니다.|
|[remove(STL/CLR)](#remove)|나머지 요소의 순서를 방해 하지 않고 지정 된 범위에서 지정 된 값을 삭제 하 고 지정 된 값을 사용 하지 않는 새 범위의 끝을 반환 합니다.|
|[remove_copy(STL/CLR)](#remove_copy)|소스 범위의 요소를 대상 범위로 복사 합니다. 단, 나머지 요소의 순서를 방해 하지 않고 지정 된 값의 요소는 복사 되지 않습니다.|
|[remove_copy_if(STL/CLR)](#remove_copy_if)|나머지 요소의 순서를 방해 하지 않고 조건자를 만족 하는 요소를 제외 하 고 소스 범위의 요소를 대상 범위로 복사 합니다.|
|[remove_if(STL/CLR)](#remove_if)|나머지 요소의 순서를 방해 하지 않고 지정 된 범위에서 조건자를 만족 하는 요소를 삭제 합니다. .|
|[replace(STL/CLR)](#replace)|범위에서 지정 된 값과 일치 하는 요소를 새 값으로 바꿉니다.|
|[replace_copy(STL/CLR)](#replace_copy)|지정 된 값과 일치 하는 요소를 새 값으로 대체 하 여 소스 범위의 요소를 대상 범위로 복사 합니다.|
|[replace_copy_if(STL/CLR)](#replace_copy_if)|소스 범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체하는 동시에 결과를 새 대상 범위로 복사합니다.|
|[replace_if(STL/CLR)](#replace_if)|범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체합니다.|
|[reverse(STL/CLR)](#reverse)|범위 내에서 요소의 순서를 반대로 바꿉니다.|
|[reverse_copy(STL/CLR)](#reverse_copy)|소스 범위 내에서 요소의 순서를 반대로 하 여 대상 범위로 복사 합니다.|
|[rotate(STL/CLR)](#rotate)|인접한 두 범위에 있는 요소를 교환합니다.|
|[rotate_copy(STL/CLR)](#rotate_copy)|소스 범위 내의 인접한 두 범위의 요소를 교환하고 결과를 대상 범위로 복사합니다.|
|[search(STL/CLR)](#search_)|대상 범위 내에서 시퀀스의 요소가 지정된 요소 시퀀스와 동일하거나 이진 조건자가 지정한 의미에 따라 지정된 시퀀스의 요소와 동일한 첫 번째 시퀀스를 검색합니다.|
|[search_n(STL/CLR)](#search_n)|범위에서 특정 값의 요소가 지정된 수만큼 있거나 이진 조건자가 지정한 해당 값과 관련이 있는 첫 번째 하위 시퀀스를 검색합니다.|
|[set_difference(STL/CLR)](#set_difference)|한 정렬된 소스 범위에 속하지만 두 번째 정렬된 소스 범위에 속하지 않는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[set_intersection(STL/CLR)](#set_intersection)|정렬된 두 소스 범위에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[set_symmetric_difference(STL/CLR)](#set_symmetric_difference)|정렬된 두 소스 범위 중 하나에만 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[set_union (STL/CLR)](#set_union)|정렬된 두 소스 범위 중 하나 이상에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[sort(STL/CLR)](#sort)|지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬합니다.|
|[sort_heap(STL/CLR)](#sort_heap)|힙을 정렬된 범위로 변환합니다.|
|[stable_partition(STL/CLR)](#stable_partition)|범위의 요소를 두 개의 연결되지 않은 집합으로 분류하고, 단항 조건자를 만족하는 요소는 만족하지 않는 요소보다 앞에 오도록 하여 동등한 요소의 상대적 관계를 유지합니다.|
|[stable_sort(STL/CLR)](#stable_sort)|지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬하고 동등한 요소의 상대적 관계를 유지합니다.|
|[swap(STL/CLR)](#swap)|두 가지 형식의 개체 사이에서 요소 값을 교환하여 첫 번째 개체의 내용을 두 번째 개체에 할당하고 두 번째 개체의 내용을 첫 번째 개체에 할당합니다.|
|[swap_ranges(STL/CLR)](#swap_ranges)|한 범위의 요소를 크기가 동일한 다른 범위의 요소로 교환합니다.|
|[transform(STL/CLR)](#transform)|두 소스 범위에서 요소 쌍에 또는 소스 범위에 있는 각 요소에 지정된 함수 개체를 적용하고 대상 범위에 함수 개체의 반환 값을 복사합니다.|
|[unique(STL/CLR)](#unique)|지정된 범위에서 서로 인접한 중복 요소를 제거합니다.|
|[unique_copy(STL/CLR)](#unique_copy)|서로 인접한 중복 요소를 제외하고 소스 범위의 요소를 대상 범위로 복사합니다.|
|[upper_bound(STL/CLR)](#upper_bound)|지정된 값보다 큰 값을 갖는 정렬된 범위에 있는 첫 번째 요소의 위치를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|

## <a name="members"></a>멤버

## <a name="adjacent_find-stlclr"></a><a name="adjacent_find"></a> adjacent_find (STL/CLR)

같지 않거나 지정한 조건을 충족하는 인접 요소 두 개를 검색합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `adjacent_find` . 자세한 내용은 [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)를 참조 하세요.

## <a name="binary_search-stlclr"></a><a name="binary_search"></a> binary_search (STL/CLR)

정렬된 범위에 지정된 값과 같거나 이진 조건자가 지정한 의미에 따라 지정된 값과 같은 요소가 있는지 여부를 테스트합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Ty> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `binary_search` . 자세한 내용은 [binary_search](../standard-library/algorithm-functions.md#binary_search)를 참조 하세요.

## <a name="copy-stlclr"></a><a name="copy"></a> copy (STL/CLR)

소스 범위의 요소를 대상 범위에 할당하여 요소의 소스 시퀀스 전체에서 반복하고 정방향으로 새 위치를 할당합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `copy` . 자세한 내용은 [복사](../standard-library/algorithm-functions.md#copy)를 참조 하세요.

## <a name="copy_backward-stlclr"></a><a name="copy_backward"></a> copy_backward (STL/CLR)

소스 범위의 요소를 대상 범위에 할당하여 요소의 소스 시퀀스 전체에서 반복하고 역방향으로 새 위치를 할당합니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt1, class _BidIt2> inline
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,
        _BidIt2 _Dest);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `copy_backward` . 자세한 내용은 [copy_backward](../standard-library/algorithm-functions.md#copy_backward)를 참조 하세요.

## <a name="count-stlclr"></a><a name="count"></a> count (STL/CLR)

해당 값이 지정된 값과 일치하는 요소의 개수를 반환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _Ty> inline
    typename iterator_traits<_InIt>::difference_type
        count(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `count` . 자세한 내용은 [count](../standard-library/algorithm-functions.md#count)를 참조 하십시오.

## <a name="count_if-stlclr"></a><a name="count_if"></a> count_if (STL/CLR)

해당 값이 지정된 조건과 일치하는 요소의 개수를 반환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _Pr> inline
    typename iterator_traits<_InIt>::difference_type
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `count_if` . 자세한 내용은 [count_if](../standard-library/algorithm-functions.md#count_if)를 참조 하세요.

## <a name="equal-stlclr"></a><a name="equal"></a> equal (STL/CLR)

두 범위를 요소별로 비교하여 같음 여부 또는 이진 조건자가 지정한 의미의 동등성을 확인합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `equal` . 자세한 내용은 [같은](../standard-library/algorithm-functions.md#equal)항목을 참조 하세요.

## <a name="equal_range-stlclr"></a><a name="equal_range"></a> equal_range (STL/CLR)

정렬된 범위에서 위치의 쌍을 찾습니다. 첫 번째는 지정된 요소의 위치보다 작거나 같으며 두 번째는 요소의 위치보다 큽니다. 여기서 시퀀스의 위치를 정하는 데 사용된 동등성 또는 순서 지정의 의미는 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Ty> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `equal_range` . 자세한 내용은 [equal_range](../standard-library/algorithm-functions.md#equal_range)를 참조 하세요.

## <a name="fill-stlclr"></a><a name="fill"></a> fill (STL/CLR)

지정한 범위의 모든 요소에 동일한 새 값을 할당합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Ty> inline
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `fill` . 자세한 내용은 [채우기](../standard-library/algorithm-functions.md#fill)를 참조 하세요.

## <a name="fill_n-stlclr"></a><a name="fill_n"></a> fill_n (STL/CLR)

특정 요소로 시작하는 범위에서 지정된 개수의 요소에 새 값을 할당합니다.

### <a name="syntax"></a>구문

```cpp
template<class _OutIt, class _Diff, class _Ty> inline
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `fill_n` . 자세한 내용은 [fill_n](../standard-library/algorithm-functions.md#fill_n)를 참조 하세요.

## <a name="find-stlclr"></a><a name="find"></a> find (STL/CLR)

범위에서 지정된 값을 가진 요소가 첫 번째로 나타나는 위치를 찾습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _Ty> inline
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `find` . 자세한 내용은 [find](../standard-library/algorithm-functions.md#find)를 참조 하세요.

## <a name="find_end-stlclr"></a><a name="find_end"></a> find_end (STL/CLR)

범위에서 지정된 시퀀스와 동일하거나 이진 조건자가 지정한 의미와 동일한 마지막 하위 시퀀스를 찾습니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `find_end` . 자세한 내용은 [find_end](../standard-library/algorithm-functions.md#find_end)를 참조 하세요.

## <a name="find_first_of-stlclr"></a><a name="find_first_of"></a> find_first_of (STL/CLR)

대상 범위 내에서 여러 값이 첫 번째로 나타나는 경우 또는 이진 조건자가 지정한 의미에서 지정된 요소 집합과 동일한 여러 요소가 첫 번째로 나타나는 경우를 검색합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `find_first_of` . 자세한 내용은 [find_first_of](../standard-library/algorithm-functions.md#find_first_of)를 참조 하세요.

## <a name="find_if-stlclr"></a><a name="find_if"></a> find_if (STL/CLR)

범위에서 지정된 조건을 만족하는 요소가 첫 번째 나타나는 위치를 찾습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _Pr> inline
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `find_if` . 자세한 내용은 [find_if](../standard-library/algorithm-functions.md#find_if)를 참조 하세요.

## <a name="for_each-stlclr"></a><a name="for_each"></a> for_each (STL/CLR)

범위 내에서 정방향으로 각 요소에 지정된 함수 개체를 적용하고 함수 개체를 반환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _Fn1> inline
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `for_each` . 자세한 내용은 [for_each](../standard-library/algorithm-functions.md#for_each)를 참조 하세요.

## <a name="generate-stlclr"></a><a name="generate"></a> 생성 (STL/CLR)

범위에 있는 각 요소에 함수 개체에 의해 생성된 값을 할당합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Fn0> inline
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `generate` . 자세한 내용은 [generate](../standard-library/algorithm-functions.md#generate)를 참조 하세요.

## <a name="generate_n-stlclr"></a><a name="generate_n"></a> generate_n (STL/CLR)

함수 개체에 의해 생성된 값을 범위 내 지정된 수의 요소에 할당하고 마지막에 할당된 값 하나 다음의 위치로 반환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _OutIt, class _Diff, class _Fn0> inline
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `generate_n` . 자세한 내용은 [generate_n](../standard-library/algorithm-functions.md#generate_n)를 참조 하세요.

## <a name="includes-stlclr"></a><a name="includes"></a> 포함 (STL/CLR)

요소 간 순서 지정 또는 동등성 기준을 이진 조건자로 지정할 수 있을 경우 하나의 정렬된 범위가 두 번째 정렬된 범위에 포함된 모든 요소를 포함할 수 있는지 여부를 테스트합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `includes` . 자세한 내용은 [포함](../standard-library/algorithm-functions.md#includes)을 참조 하세요.

## <a name="inplace_merge-stlclr"></a><a name="inplace_merge"></a> inplace_merge (STL/CLR)

두 연속 정렬 범위의 요소를 단일 정렬 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `inplace_merge` . 자세한 내용은 [inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)를 참조 하세요.

## <a name="iter_swap-stlclr"></a><a name="iter_swap"></a> iter_swap (STL/CLR)

지정된 반복기의 쌍이 참조하는 두 값을 교환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `iter_swap` . 자세한 내용은 [iter_swap](../standard-library/algorithm-functions.md#iter_swap)를 참조 하세요.

## <a name="lexicographical_compare-stlclr"></a><a name="lexicographical_compare"></a> lexicographical_compare (STL/CLR)

두 시퀀스를 요소별로 비교하여 둘 중 작은 것을 결정합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `lexicographical_compare` . 자세한 내용은 [lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare)를 참조 하세요.

## <a name="lower_bound-stlclr"></a><a name="lower_bound"></a> lower_bound (STL/CLR)

지정 된 값 보다 작거나 같은 값을 갖는 정렬 된 범위에서 첫 번째 요소의 위치를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `lower_bound` . 자세한 내용은 [lower_bound](../standard-library/algorithm-functions.md#lower_bound)를 참조 하세요.

## <a name="make_heap-stlclr"></a><a name="make_heap"></a> make_heap (STL/CLR)

지정한 범위의 요소를 첫 번째 요소가 가장 큰 힙으로 변환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void make_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `make_heap` . 자세한 내용은 [make_heap](../standard-library/algorithm-functions.md#make_heap)를 참조 하세요.

## <a name="max-stlclr"></a><a name="max"></a> max (STL/CLR)

두 개체를 비교하고 둘 중 큰 개체를 반환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _Ty> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `max` . 자세한 내용은 [max](../standard-library/algorithm-functions.md#max)를 참조 하세요.

## <a name="max_element-stlclr"></a><a name="max_element"></a> max_element (STL/CLR)

지정된 범위에서 가장 큰 첫 번째 요소를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `max_element` . 자세한 내용은 [max_element](../standard-library/algorithm-functions.md#max_element)를 참조 하세요.

## <a name="merge-stlclr"></a><a name="merge"></a> merge (STL/CLR)

정렬된 두 소스 범위의 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `merge` . 자세한 내용은 [merge](../standard-library/algorithm-functions.md#merge)를 참조 하세요.

## <a name="min-stlclr"></a><a name="min"></a> min (STL/CLR)

두 개체를 비교하고 둘 중 작은 개체를 반환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _Ty> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `min` . 자세한 내용은 [min](../standard-library/algorithm-functions.md#min)을 참조 하십시오.

## <a name="min_element-stlclr"></a><a name="min_element"></a> min_element (STL/CLR)

지정된 범위에서 가장 작은 첫 번째 요소를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `min_element` . 자세한 내용은 [min_element](../standard-library/algorithm-functions.md#min_element)를 참조 하세요.

## <a name="mismatch-stlclr"></a><a name="mismatch"></a> 불일치 (STL/CLR)

두 범위를 요소별로 비교하여 같음 여부 또는 이진 조건자가 지정한 의미의 동등성을 확인하고 차이가 발생한 첫 번째 위치를 찾습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
            _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `mismatch` . 자세한 내용은 [불일치](../standard-library/algorithm-functions.md#mismatch)를 참조 하세요.

## <a name="next_permutation-stlclr"></a><a name="next_permutation"></a> next_permutation (STL/CLR)

원래 순서 지정을 사전순에 따라 다음으로 큰 순열(있는 경우)로 대체할 수 있도록 범위의 요소 순서를 재정렬합니다. 여기서 다음의 의미는 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt> inline
    bool next_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `next_permutation` . 자세한 내용은 [next_permutation](../standard-library/algorithm-functions.md#next_permutation)를 참조 하세요.

## <a name="nth_element-stlclr"></a><a name="nth_element"></a> nth_element (STL/CLR)

요소 범위를 분할 하 여 범위에서 시퀀스의 th 요소를 정확 하 게 배치 하 여 `n` 그 앞의 모든 요소가 값 보다 작거나 같고 시퀀스에서 뒤에 나오는 모든 요소가 해당 요소 보다 크거나 같은 경우

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `nth_element` . 자세한 내용은 [nth_element](../standard-library/algorithm-functions.md#nth_element)를 참조 하세요.

## <a name="partial_sort-stlclr"></a><a name="partial_sort"></a> partial_sort (STL/CLR)

범위에 있는 지정된 수의 더 작은 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬합니다.

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `partial_sort` . 자세한 내용은 [partial_sort](../standard-library/algorithm-functions.md#partial_sort)를 참조 하세요.

## <a name="partial_sort_copy-stlclr"></a><a name="partial_sort_copy"></a> partial_sort_copy (STL/CLR)

소스 범위의 요소를 대상 범위로 복사합니다. 여기서 소스 요소는 지정된 다른 이진 조건자보다 작거나 지정된 다른 이진 조건자로 정렬됩니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _RanIt> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2);
template<class _InIt, class _RanIt, class _Pr> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `partial_sort_copy` . 자세한 내용은 [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy)를 참조 하세요.

## <a name="partition-stlclr"></a><a name="partition"></a> partition (STL/CLR)

범위의 요소를 두 개의 연결되지 않은 집합으로 분류하고, 단항 조건자를 만족하는 요소는 만족하지 않는 요소보다 앞에 오도록 합니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `partition` . 자세한 내용은 [파티션](../standard-library/algorithm-functions.md#partition)을 참조 하세요.

## <a name="pop_heap-stlclr"></a><a name="pop_heap"></a> pop_heap (STL/CLR)

힙 맨 앞부터 범위의 끝에서 두 번째 위치 중에서 가장 큰 요소를 제거한 다음 나머지 요소로 새 힙을 구성합니다.

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void pop_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `pop_heap` . 자세한 내용은 [pop_heap](../standard-library/algorithm-functions.md#pop_heap)를 참조 하세요.

## <a name="prev_permutation-stlclr"></a><a name="prev_permutation"></a> prev_permutation (STL/CLR)

원래 순서 지정을 사전순에 따라 다음으로 큰 순열(있는 경우)로 대체할 수 있도록 범위의 요소 순서를 재정렬합니다. 여기서 다음의 의미는 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `prev_permutation` . 자세한 내용은 [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)를 참조 하세요.

## <a name="push_heap-stlclr"></a><a name="push_heap"></a> push_heap (STL/CLR)

범위의 마지막에 있는 요소를 범위의 이전 요소로 구성된 기존 힙에 추가합니다.

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void push_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `push_heap` . 자세한 내용은 [push_heap](../standard-library/algorithm-functions.md#push_heap)를 참조 하세요.

## <a name="random_shuffle-stlclr"></a><a name="random_shuffle"></a> random_shuffle (STL/CLR)

`N`범위에 있는 요소의 시퀀스를 다음 중 하나로 다시 정렬 합니다 `N` . 가능 배열 중 하나로 재정렬합니다.

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void random_shuffle(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Fn1> inline
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `random_shuffle` . 자세한 내용은 [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)를 참조 하세요.

## <a name="remove-stlclr"></a><a name="remove"></a> remove (STL/CLR)

나머지 요소의 순서에 영향을 미치거나 지정된 값이 없는 새 범위의 끝을 반환하지 않고 지정된 범위에서 지정된 값을 제거합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `remove` . 자세한 내용은 [remove](../standard-library/algorithm-functions.md#remove)를 참조 하십시오.

## <a name="remove_copy-stlclr"></a><a name="remove_copy"></a> remove_copy (STL/CLR)

소스 범위의 요소를 대상 범위로 복사합니다. 단, 나머지 요소의 순서를 변경하거나 새 대상 범위의 끝을 반환하지 않고 지정된 값의 요소는 복사하지 않습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt remove_copy(_InIt _First, _InIt _Last,
        _OutIt _Dest, const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `remove_copy` . 자세한 내용은 [remove_copy](../standard-library/algorithm-functions.md#remove_copy)를 참조 하세요.

## <a name="remove_copy_if-stlclr"></a><a name="remove_copy_if"></a> remove_copy_if (STL/CLR)

소스 범위의 요소를 대상 범위로 복사합니다. 단, 나머지 요소의 순서를 변경하거나 새 대상 범위의 끝을 반환하지 않고 조건자를 만족하는 요소는 복사하지 않습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `remove_copy_if` . 자세한 내용은 [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)를 참조 하세요.

## <a name="remove_if-stlclr"></a><a name="remove_if"></a> remove_if (STL/CLR)

나머지 요소의 순서에 영향을 미치거나 지정된 값이 없는 새 범위의 끝을 반환하지 않고 지정된 범위에서 조건자를 만족하는 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Pr> inline
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `remove_if` . 자세한 내용은 [remove_if](../standard-library/algorithm-functions.md#remove_if)를 참조 하세요.

## <a name="replace-stlclr"></a><a name="replace"></a> replace (STL/CLR)

범위의 각 요소를 검사하고 요소가 지정된 값과 일치하면 대체합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Ty> inline
    void replace(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `replace` . 자세한 내용은 [replace](../standard-library/algorithm-functions.md#replace)를 참조 하세요.

## <a name="replace_copy-stlclr"></a><a name="replace_copy"></a> replace_copy (STL/CLR)

소스 범위의 각 요소를 검사하고 요소가 지정된 값과 일치하면 대체하는 동시에 결과를 새 대상 범위로 복사합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `replace_copy` . 자세한 내용은 [replace_copy](../standard-library/algorithm-functions.md#replace_copy)를 참조 하세요.

## <a name="replace_copy_if-stlclr"></a><a name="replace_copy_if"></a> replace_copy_if (STL/CLR)

소스 범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체하는 동시에 결과를 새 대상 범위로 복사합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred, const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `replace_copy_if` . 자세한 내용은 [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)를 참조 하세요.

## <a name="replace_if-stlclr"></a><a name="replace_if"></a> replace_if (STL/CLR)

범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Pr, class _Ty> inline
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,
        const _Ty% _Val);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `replace_if` . 자세한 내용은 [replace_if](../standard-library/algorithm-functions.md#replace_if)를 참조 하세요.

## <a name="reverse-stlclr"></a><a name="reverse"></a> reverse (STL/CLR)

범위 내에서 요소의 순서를 반대로 바꿉니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt> inline
    void reverse(_BidIt _First, _BidIt _Last);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `reverse` . 자세한 내용은 [reverse](../standard-library/algorithm-functions.md#reverse)를 참조 하세요.

## <a name="reverse_copy-stlclr"></a><a name="reverse_copy"></a> reverse_copy (STL/CLR)

소스 범위 내에서 요소의 순서를 반대로 하 여 대상 범위로 복사 합니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt, class _OutIt> inline
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `reverse_copy` . 자세한 내용은 [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)를 참조 하세요.

## <a name="rotate-stlclr"></a><a name="rotate"></a> rotate (STL/CLR)

인접한 두 범위에 있는 요소를 교환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt> inline
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `rotate` . 자세한 내용은 [회전](../standard-library/algorithm-functions.md#rotate)을 참조 하십시오.

## <a name="rotate_copy-stlclr"></a><a name="rotate_copy"></a> rotate_copy (STL/CLR)

소스 범위 내의 인접한 두 범위의 요소를 교환하고 결과를 대상 범위로 복사합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _OutIt> inline
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,
        _OutIt _Dest);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `rotate_copy` . 자세한 내용은 [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)를 참조 하세요.

## <a name="search-stlclr"></a><a name="search_"></a> 검색 (STL/CLR)

대상 범위 내에서 시퀀스의 요소가 지정된 요소 시퀀스와 동일하거나 이진 조건자가 지정한 의미에 따라 지정된 시퀀스의 요소와 동일한 첫 번째 시퀀스를 검색합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `search` . 자세한 내용은 [검색](../standard-library/algorithm-functions.md#search)을 참조 하세요.

## <a name="search_n-stlclr"></a><a name="search_n"></a> search_n (STL/CLR)

범위에서 특정 값의 요소가 지정된 수만큼 있거나 이진 조건자가 지정한 해당 값과 관련이 있는 첫 번째 하위 시퀀스를 검색합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt1, class _Diff2, class _Ty> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val);
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `search_n` . 자세한 내용은 [search_n](../standard-library/algorithm-functions.md#search_n)를 참조 하세요.

## <a name="set_difference-stlclr"></a><a name="set_difference"></a> set_difference (STL/CLR)

한 정렬된 소스 범위에 속하지만 두 번째 정렬된 소스 범위에 속하지 않는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `set_difference` . 자세한 내용은 [set_difference](../standard-library/algorithm-functions.md#set_difference)를 참조 하세요.

## <a name="set_intersection-stlclr"></a><a name="set_intersection"></a> set_intersection (STL/CLR)

정렬된 두 소스 범위에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `set_intersection` . 자세한 내용은 [set_intersection](../standard-library/algorithm-functions.md#set_intersection)를 참조 하세요.

## <a name="set_symmetric_difference-stlclr"></a><a name="set_symmetric_difference"></a> set_symmetric_difference (STL/CLR)

정렬된 두 소스 범위 중 하나에만 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `set_symmetric_difference` . 자세한 내용은 [set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference)를 참조 하세요.

## <a name="set_union-stlclr"></a><a name="set_union"></a> set_union (STL/CLR)

정렬된 두 소스 범위 중 하나 이상에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `set_union` . 자세한 내용은 [set_union](../standard-library/algorithm-functions.md#set_union)를 참조 하세요.

## <a name="sort-stlclr"></a><a name="sort"></a> sort (STL/CLR)

지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬합니다.

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void sort(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `sort` . 자세한 내용은 [sort](../mfc/reference/cmfclistctrl-class.md#sort)를 참조 하세요.

## <a name="sort_heap-stlclr"></a><a name="sort_heap"></a> sort_heap (STL/CLR)

힙을 정렬된 범위로 변환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _RanIt> inline
    void sort_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `sort_heap` . 자세한 내용은 [sort_heap](../standard-library/algorithm-functions.md#sort_heap)를 참조 하세요.

## <a name="stable_partition-stlclr"></a><a name="stable_partition"></a> stable_partition (STL/CLR)

범위의 요소를 두 개의 연결되지 않은 집합으로 분류하고, 단항 조건자를 만족하는 요소는 만족하지 않는 요소보다 앞에 오도록 하여 동등한 요소의 상대적 관계를 유지합니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `stable_partition` . 자세한 내용은 [stable_partition](../standard-library/algorithm-functions.md#stable_partition)를 참조 하세요.

## <a name="stable_sort-stlclr"></a><a name="stable_sort"></a> stable_sort (STL/CLR)

지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬하고 동등한 요소의 상대적 관계를 유지합니다.

### <a name="syntax"></a>구문

```cpp
template<class _BidIt> inline
    void stable_sort(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `stable_sort` . 자세한 내용은 [stable_sort](../standard-library/algorithm-functions.md#stable_sort)를 참조 하세요.

## <a name="swap-stlclr"></a><a name="swap"></a> swap (STL/CLR)

두 가지 형식의 개체 사이에서 요소 값을 교환하여 첫 번째 개체의 내용을 두 번째 개체에 할당하고 두 번째 개체의 내용을 첫 번째 개체에 할당합니다.

### <a name="syntax"></a>구문

```cpp
<class _Ty> inline
    void swap(_Ty% _Left, _Ty% _Right);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `swap` . 자세한 내용은 [swap](../standard-library/algorithm-functions.md#swap)을 참조 하십시오.

## <a name="swap_ranges-stlclr"></a><a name="swap_ranges"></a> swap_ranges (STL/CLR)

한 범위의 요소를 크기가 동일한 다른 범위의 요소로 교환합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `swap_ranges` . 자세한 내용은 [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges)를 참조 하세요.

## <a name="transform-stlclr"></a><a name="transform"></a> transform (STL/CLR)

두 소스 범위에서 요소 쌍에 또는 소스 범위에 있는 각 요소에 지정된 함수 개체를 적용하고 대상 범위에 함수 개체의 반환 값을 복사합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _OutIt, class _Fn1> inline
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Fn1 _Func);
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `transform` . 자세한 내용은 [변환](../standard-library/algorithm-functions.md#transform)을 참조 하세요.

## <a name="unique-stlclr"></a><a name="unique"></a> unique (STL/CLR)

지정된 범위에서 서로 인접한 중복 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `unique` . 자세한 내용은 [unique](../standard-library/algorithm-functions.md#unique)를 참조 하세요.

## <a name="unique_copy-stlclr"></a><a name="unique_copy"></a> unique_copy (STL/CLR)

서로 인접한 중복 요소를 제외하고 소스 범위의 요소를 대상 범위로 복사합니다.

### <a name="syntax"></a>구문

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `unique_copy` . 자세한 내용은 [unique_copy](../standard-library/algorithm-functions.md#unique_copy)를 참조 하세요.

## <a name="upper_bound-stlclr"></a><a name="upper_bound"></a> upper_bound (STL/CLR)

지정된 값보다 큰 값을 갖는 정렬된 범위에 있는 첫 번째 요소의 위치를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>설명

이 함수는 c + + 표준 라이브러리 함수와 동일 하 게 작동 합니다 `upper_bound` . 자세한 내용은 [upper_bound](../standard-library/algorithm-functions.md#upper_bound)를 참조 하세요.
