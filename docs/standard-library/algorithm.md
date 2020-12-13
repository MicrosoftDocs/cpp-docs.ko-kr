---
description: '자세히 알아보기: &lt; 알고리즘&gt;'
title: '&lt;알고리즘&gt;'
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: 42f03372d01ac2d3218ce5844b86e92526055bbf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163771"
---
# <a name="ltalgorithmgt"></a>&lt;알고리즘&gt;

알고리즘을 수행하는 C++ 표준 라이브러리 컨테이너 템플릿 함수를 정의합니다.

## <a name="syntax"></a>Syntax

```cpp
(see relevant links below for specific algorithm syntax)
```

> [!NOTE]
> \<algorithm>또한 라이브러리는 문을 사용 `#include <initializer_list>` 합니다.

## <a name="remarks"></a>설명

C++ 표준 라이브러리 알고리즘은 다양한 데이터 구조에서 작동하므로 제네릭입니다. 작동할 수 있는 데이터 구조에는 `vector`, `list` 등의 C++ 표준 라이브러리 컨테이너 클래스뿐만 아니라, 특정 알고리즘의 요구 사항을 충족하는 요소 배열 및 프로그램 정의 데이터 구조도 포함됩니다. C++ 표준 라이브러리 알고리즘은 반복기를 통해 간접적으로 컨테이너 요소를 액세스 및 이동하여 이러한 수준의 일반성을 달성합니다.

C++ 표준 라이브러리 알고리즘은 일반적으로 시작 또는 끝 위치로 지정하는 반복기 범위를 처리합니다. 참조 범위는 유효해야 합니다. 즉, 범위 내 모든 포인터를 역참조할 수 있어야 하며 각 범위의 시퀀스 내에서 마지막 위치를 처음부터 증분으로 접근할 수 있어야 합니다.

C++ 표준 라이브러리 알고리즘은 각 C++ 표준 라이브러리 컨테이너의 작업 및 멤버 함수로 지원되는 작업을 확장하며, 예를 들어 다른 형식의 컨테이너 개체를 동시에 사용할 수 있습니다. 알고리즘 목적에 대한 정보를 전달하기 위해 두 개의 접미사가 사용되었습니다.

- `_if`접미사는 알고리즘이 요소 자체가 아닌 요소 값에서 작동 하는 함수 개체에 사용 됨을 나타냅니다. `find_if` 알고리즘은 요소 값이 함수 개체에서 지정한 기준을 충족하는 요소를 찾고, `find` 알고리즘은 특정 값을 찾습니다.

- _copy 접미사는 알고리즘이 요소 값을 조작할 뿐만 아니라 수정된 값을 대상 범위로 복사함을 나타냅니다. `reverse` 알고리즘은 범위 내 요소의 순서를 반대로 바꾸며, `reverse_copy` 알고리즘은 또한 결과를 대상 범위로 복사합니다.

C++ 표준 라이브러리 알고리즘은 해당 목적 또는 요구 사항을 나타내는 그룹으로 분류되는 경우가 많습니다. 여기에는 요소 값을 변경하지 않는 비수정 알고리즘과 달리 요소 값을 변경하는 수정 알고리즘이 포함됩니다. 파생 알고리즘은 요소 값이 아닌 요소 순서를 변경합니다. 제거 알고리즘은 범위 또는 범위 복사본에서 요소를 제거할 수 있습니다. 정렬 알고리즘은 다양 한 방식으로 범위에 있는 요소의 순서를 변경 하 고 정렬 된 범위 알고리즘은 해당 요소가 특정 방식으로 정렬 된 범위 에서만 작동 합니다.

숫자 처리를 위해 제공 되는 c + + 표준 라이브러리 숫자 알고리즘에는 고유한 헤더 파일이 있으며 [\<numeric>](numeric.md) , 함수 개체와 어댑터는 [\<functional>](functional.md) 부울 값을 반환 하는 헤더 함수 개체에 정의 됩니다. 기본 이진 조건자는 비교 `operator<`입니다. 일반적으로, 순서를 정하는 요소는 크기를 비교할 수 있어야 합니다. 즉, 제공된 어떤 두 요소에서 두 요소가 동일하거나(어떤 것도 다른 것보다 작지 않음) 하나가 다른 것보다 작음을 정할 수 있어야 합니다. 그러면 동일하지 않은 요소 사이에 순서가 지정됩니다.

### <a name="function-templates"></a>함수 템플릿

|Name|설명|
|-|-|
|[adjacent_find](algorithm-functions.md#adjacent_find)|같지 않거나 지정한 조건을 충족하는 인접 요소 두 개를 검색합니다.|
|[all_of](algorithm-functions.md#all_of)|**`true`** 지정 된 범위의 각 요소에 조건이 있는 경우를 반환 합니다.|
|[any_of](algorithm-functions.md#any_of)|**`true`** 지정 된 요소 범위에서 조건이 한 번 이상 있는 경우를 반환 합니다.|
|[binary_search](algorithm-functions.md#binary_search)|정렬된 범위에 지정된 값과 같거나 이진 조건자가 지정한 의미에 따라 지정된 값과 같은 요소가 있는지 여부를 테스트합니다.|
|[클램프](algorithm-functions.md#clamp)||
|[copy](algorithm-functions.md#copy)|소스 범위의 요소를 대상 범위에 할당하여 요소의 소스 시퀀스 전체에서 반복하고 정방향으로 새 위치를 할당합니다.|
|[copy_backward](algorithm-functions.md#copy_backward)|소스 범위의 요소를 대상 범위에 할당하여 요소의 소스 시퀀스 전체에서 반복하고 역방향으로 새 위치를 할당합니다.|
|[copy_if](algorithm-functions.md#copy_if)|**`true`** 지정 된 조건에 대해 테스트 하는 지정 된 범위에 있는 모든 요소를 복사 합니다.|
|[copy_n](algorithm-functions.md#copy_n)|지정된 수의 요소를 복사합니다.|
|[count](algorithm-functions.md#count)|해당 값이 지정된 값과 일치하는 요소의 개수를 반환합니다.|
|[count_if](algorithm-functions.md#count_if)|해당 값이 지정된 조건과 일치하는 요소의 개수를 반환합니다.|
|[equal](algorithm-functions.md#equal)|두 범위를 요소별로 비교하여 같음 여부 또는 이진 조건자가 지정한 의미의 동등성을 확인합니다.|
|[equal_range](algorithm-functions.md#equal_range)|정렬된 범위에서 위치의 쌍을 찾습니다. 첫 번째는 지정된 요소의 위치보다 작거나 같으며 두 번째는 요소의 위치보다 큽니다. 여기서 시퀀스의 위치를 정하는 데 사용된 동등성 또는 순서 지정의 의미는 이진 조건자로 지정할 수 있습니다.|
|[칠할](algorithm-functions.md#fill)|지정한 범위의 모든 요소에 동일한 새 값을 할당합니다.|
|[fill_n](algorithm-functions.md#fill_n)|특정 요소로 시작하는 범위에서 지정된 개수의 요소에 새 값을 할당합니다.|
|[find](algorithm-functions.md#find)|범위에서 지정된 값을 가진 요소가 첫 번째로 나타나는 위치를 찾습니다.|
|[find_end](algorithm-functions.md#find_end)|범위에서 지정된 시퀀스와 동일하거나 이진 조건자가 지정한 의미와 동일한 마지막 하위 시퀀스를 찾습니다.|
|[find_first_of](algorithm-functions.md#find_first_of)|대상 범위 내에서 여러 값이 첫 번째로 나타나는 경우 또는 이진 조건자가 지정한 의미에서 지정된 요소 집합과 동일한 여러 요소가 첫 번째로 나타나는 경우를 검색합니다.|
|[find_if](algorithm-functions.md#find_if)|범위에서 지정된 조건을 만족하는 요소가 첫 번째 나타나는 위치를 찾습니다.|
|[find_if_not](algorithm-functions.md#find_if_not)|표시된 범위에서 조건을 충족하지 않는 첫 번째 요소를 반환합니다.|
|[for_each](algorithm-functions.md#for_each)|범위 내에서 정방향으로 각 요소에 지정된 함수 개체를 적용하고 함수 개체를 반환합니다.|
|[for_each_n](algorithm-functions.md#for_each_n)||
|[만드는](algorithm-functions.md#generate)|범위에 있는 각 요소에 함수 개체에 의해 생성된 값을 할당합니다.|
|[generate_n](algorithm-functions.md#generate_n)|함수 개체에 의해 생성된 값을 범위 내 지정된 수의 요소에 할당하고 마지막에 할당된 값 하나 다음의 위치로 반환합니다.|
|[내용이](algorithm-functions.md#includes)|요소 간 순서 지정 또는 동등성 기준을 이진 조건자로 지정할 수 있을 경우 하나의 정렬된 범위가 두 번째 정렬된 범위에 포함된 모든 요소를 포함할 수 있는지 여부를 테스트합니다.|
|[inplace_merge](algorithm-functions.md#inplace_merge)|두 연속 정렬 범위의 요소를 단일 정렬 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[is_heap](algorithm-functions.md#is_heap)|**`true`** 지정 된 범위의 요소가 힙을 형성 하는 경우를 반환 합니다.|
|[is_heap_until](algorithm-functions.md#is_heap_until)|**`true`** 지정 된 범위가 마지막 요소까지 힙을 형성 하는 경우를 반환 합니다.|
|[is_partitioned](algorithm-functions.md#is_partitioned)|**`true`** 지정 된 범위에서 조건에 대해 테스트 하는 모든 요소가를 **`true`** 테스트 하는 요소 앞에 있는 경우를 반환 **`false`** 합니다.|
|[is_permutation](algorithm-functions.md#is_permutation)|지정된 범위의 요소가 올바른 순열을 만드는지 여부를 결정합니다.|
|[is_sorted](algorithm-functions.md#is_sorted)|**`true`** 지정 된 범위의 요소가 정렬 된 순서 대로 되어 있으면를 반환 합니다.|
|[is_sorted_until](algorithm-functions.md#is_sorted_until)|**`true`** 지정 된 범위의 요소가 정렬 된 순서 대로 되어 있으면를 반환 합니다.|
|[iter_swap](algorithm-functions.md#iter_swap)|지정된 반복기의 쌍이 참조하는 두 값을 교환합니다.|
|[lexicographical_compare](algorithm-functions.md#lexicographical_compare)|두 시퀀스를 요소별로 비교하여 둘 중 작은 것을 결정합니다.|
|[lower_bound](algorithm-functions.md#lower_bound)|정렬된 범위에서 지정된 값보다 크거나 같은 값을 갖는 첫 번째 요소의 위치를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[make_heap](algorithm-functions.md#make_heap)|지정한 범위의 요소를 첫 번째 요소가 가장 큰 힙으로 변환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[max](algorithm-functions.md#max)|두 개체를 비교하고 둘 중 큰 개체를 반환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[max_element](algorithm-functions.md#max_element)|지정된 범위에서 가장 큰 첫 번째 요소를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[결합](algorithm-functions.md#merge)|정렬된 두 소스 범위의 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[min](algorithm-functions.md#min)|두 개체를 비교하고 둘 중 작은 개체를 반환합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[min_element](algorithm-functions.md#min_element)|지정된 범위에서 가장 작은 첫 번째 요소를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[minmax](algorithm-functions.md#minmax)|두 개의 입력된 매개 변수를 비교하여 작은 수와 큰 수의 순서로 구성된 한 쌍을 반환합니다.|
|[minmax_element](algorithm-functions.md#minmax_element)|한 번의 호출로 [min_element](algorithm-functions.md#min_element) 및 [max_element](algorithm-functions.md#max_element)에서 수행하는 작업을 수행합니다.|
|[않거나](algorithm-functions.md#mismatch)|두 범위를 요소별로 비교하여 같음 여부 또는 이진 조건자가 지정한 의미의 동등성을 확인하고 차이가 발생한 첫 번째 위치를 찾습니다.|
|[&lt;alg &gt; 이동](algorithm-functions.md#alg_move)|지정된 범위와 연결된 요소를 이동합니다.|
|[move_backward](algorithm-functions.md#move_backward)|한 반복기의 요소를 다른 반복기로 이동합니다. 이동은 지정된 범위의 마지막 요소에서 시작하고 해당 범위의 첫 번째 요소에서 끝납니다.|
|[next_permutation](algorithm-functions.md#next_permutation)|원래 순서 지정을 사전순에 따라 다음으로 큰 순열(있는 경우)로 대체할 수 있도록 범위의 요소 순서를 재정렬합니다. 여기서 다음의 의미는 이진 조건자로 지정할 수 있습니다.|
|[none_of](algorithm-functions.md#none_of)|**`true`** 지정 된 범위의 요소 사이에 조건이 없는 경우를 반환 합니다.|
|[nth_element](algorithm-functions.md#nth_element)|요소 범위를 분할 하 여 범위에서 시퀀스의 *n* 번째 요소를 정확 하 게 배치 하 여 그 앞의 모든 요소가 값 보다 작거나 같고 시퀀스에서 뒤에 나오는 모든 요소가 해당 요소 보다 크거나 같은 경우|
|[partial_sort](algorithm-functions.md#partial_sort)|범위에 있는 지정된 수의 더 작은 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬합니다.|
|[partial_sort_copy](algorithm-functions.md#partial_sort_copy)|소스 범위의 요소를 대상 범위로 복사합니다. 여기서 소스 요소는 지정된 다른 이진 조건자보다 작거나 지정된 다른 이진 조건자로 정렬됩니다.|
|[파티션마다](algorithm-functions.md#partition)|범위의 요소를 두 개의 연결되지 않은 집합으로 분류하고, 단항 조건자를 만족하는 요소는 만족하지 않는 요소보다 앞에 오도록 합니다.|
|[partition_copy](algorithm-functions.md#partition_copy)|조건이 다른 대상에 해당 하는 요소를 대상으로 하는 요소를 복사 **`true`** **`false`** 합니다. 지정된 범위의 요소여야 합니다.|
|[partition_point](algorithm-functions.md#partition_point)|지정된 범위에서 조건을 충족하지 않는 첫 번째 요소를 반환합니다. 조건을 충족하는 요소가 앞에, 그렇지 않는 요소는 뒤에 정렬됩니다.|
|[pop_heap](algorithm-functions.md#pop_heap)|힙 맨 앞부터 범위의 끝에서 두 번째 위치 중에서 가장 큰 요소를 제거한 다음 나머지 요소로 새 힙을 구성합니다.|
|[prev_permutation](algorithm-functions.md#prev_permutation)|원래 순서 지정을 사전순에 따라 다음으로 큰 순열(있는 경우)로 대체할 수 있도록 범위의 요소 순서를 재정렬합니다. 여기서 다음의 의미는 이진 조건자로 지정할 수 있습니다.|
|[push_heap](algorithm-functions.md#push_heap)|범위의 마지막에 있는 요소를 범위의 이전 요소로 구성된 기존 힙에 추가합니다.|
|[random_shuffle](algorithm-functions.md#random_shuffle)|범위의 *N* 개 요소의 시퀀스를 무작위로 선택한 *N*! 가능 배열 중 하나로 재정렬합니다.|
|[remove](algorithm-functions.md#remove)|나머지 요소의 순서에 영향을 미치거나 지정된 값이 없는 새 범위의 끝을 반환하지 않고 지정된 범위에서 지정된 값을 제거합니다.|
|[remove_copy](algorithm-functions.md#remove_copy)|소스 범위의 요소를 대상 범위로 복사합니다. 단, 나머지 요소의 순서를 변경하거나 새 대상 범위의 끝을 반환하지 않고 지정된 값의 요소는 복사하지 않습니다.|
|[remove_copy_if](algorithm-functions.md#remove_copy_if)|소스 범위의 요소를 대상 범위로 복사합니다. 단, 나머지 요소의 순서를 변경하거나 새 대상 범위의 끝을 반환하지 않고 조건자를 만족하는 요소는 복사하지 않습니다.|
|[remove_if](algorithm-functions.md#remove_if)|나머지 요소의 순서에 영향을 미치거나 지정된 값이 없는 새 범위의 끝을 반환하지 않고 지정된 범위에서 조건자를 만족하는 요소를 제거합니다.|
|[replace](algorithm-functions.md#replace)|범위의 각 요소를 검사하고 요소가 지정된 값과 일치하면 대체합니다.|
|[replace_copy](algorithm-functions.md#replace_copy)|소스 범위의 각 요소를 검사하고 요소가 지정된 값과 일치하면 대체하는 동시에 결과를 새 대상 범위로 복사합니다.|
|[replace_copy_if](algorithm-functions.md#replace_copy_if)|소스 범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체하는 동시에 결과를 새 대상 범위로 복사합니다.|
|[replace_if](algorithm-functions.md#replace_if)|범위의 각 요소를 검사하고 요소가 지정된 조건자를 충족하면 대체합니다.|
|[되돌립니다](algorithm-functions.md#reverse)|범위 내에서 요소의 순서를 반대로 바꿉니다.|
|[reverse_copy](algorithm-functions.md#reverse_copy)|소스 범위 내의 요소의 순서를 바꾸는 동시에 요소를 대상 범위로 복사합니다.|
|[시키거나](algorithm-functions.md#rotate)|인접한 두 범위에 있는 요소를 교환합니다.|
|[rotate_copy](algorithm-functions.md#rotate_copy)|소스 범위 내의 인접한 두 범위의 요소를 교환하고 결과를 대상 범위로 복사합니다.|
|[샘플이](algorithm-functions.md#sample)||
|[search](algorithm-functions.md#search)|대상 범위 내에서 시퀀스의 요소가 지정된 요소 시퀀스와 동일하거나 이진 조건자가 지정한 의미에 따라 지정된 시퀀스의 요소와 동일한 첫 번째 시퀀스를 검색합니다.|
|[search_n](algorithm-functions.md#search_n)|범위에서 특정 값의 요소가 지정된 수만큼 있거나 이진 조건자가 지정한 해당 값과 관련이 있는 첫 번째 하위 시퀀스를 검색합니다.|
|[set_difference](algorithm-functions.md#set_difference)|한 정렬된 소스 범위에 속하지만 두 번째 정렬된 소스 범위에 속하지 않는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[set_intersection](algorithm-functions.md#set_intersection)|정렬된 두 소스 범위에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[set_symmetric_difference](algorithm-functions.md#set_symmetric_difference)|정렬된 두 소스 범위 중 하나에만 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[set_union](algorithm-functions.md#set_union)|정렬된 두 소스 범위 중 하나 이상에 속하는 모든 요소를 정렬된 단일 대상 범위로 결합합니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|
|[sort](algorithm-functions.md#sort)|지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬합니다.|
|[순서 섞기](algorithm-functions.md#shuffle)|난수 생성기를 사용하여 지정된 범위 내 요소의 순서를 섞습니다(다시 정렬).|
|[sort_heap](algorithm-functions.md#sort_heap)|힙을 정렬된 범위로 변환합니다.|
|[stable_partition](algorithm-functions.md#stable_partition)|범위의 요소를 두 개의 연결되지 않은 집합으로 분류하고, 단항 조건자를 만족하는 요소는 만족하지 않는 요소보다 앞에 오도록 하여 동등한 요소의 상대적 관계를 유지합니다.|
|[stable_sort](algorithm-functions.md#stable_sort)|지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 정렬하고 동등한 요소의 상대적 관계를 유지합니다.|
|[스왑을](algorithm-functions.md#swap)|두 가지 형식의 개체 사이에서 요소 값을 교환하여 첫 번째 개체의 내용을 두 번째 개체에 할당하고 두 번째 개체의 내용을 첫 번째 개체에 할당합니다.|
|[swap_ranges](algorithm-functions.md#swap_ranges)|한 범위의 요소를 크기가 동일한 다른 범위의 요소로 교환합니다.|
|[transform](algorithm-functions.md#transform)|두 소스 범위에서 요소 쌍에 또는 소스 범위에 있는 각 요소에 지정된 함수 개체를 적용하고 대상 범위에 함수 개체의 반환 값을 복사합니다.|
|[unique](algorithm-functions.md#unique)|지정된 범위에서 서로 인접한 중복 요소를 제거합니다.|
|[unique_copy](algorithm-functions.md#unique_copy)|서로 인접한 중복 요소를 제외하고 소스 범위의 요소를 대상 범위로 복사합니다.|
|[upper_bound](algorithm-functions.md#upper_bound)|지정된 값보다 큰 값을 갖는 정렬된 범위에 있는 첫 번째 요소의 위치를 찾습니다. 정렬 기준은 이진 조건자로 지정할 수 있습니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](cpp-standard-library-reference.md)
