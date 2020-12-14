---
description: '자세한 정보: c + + 표준 라이브러리 컨테이너'
title: C++ 표준 라이브러리 컨테이너
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, class template containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 3f95654b5b6f06e62621a5a325e794cf2a764af3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222049"
---
# <a name="c-standard-library-containers"></a>C++ 표준 라이브러리 컨테이너

표준 라이브러리는 관련 개체 컬렉션을 저장할, 형식이 안전한 다양한 컨테이너를 제공합니다. 컨테이너는 클래스 템플릿입니다. 컨테이너 변수를 선언할 때 컨테이너에 포함할 요소의 형식을 지정 합니다. 컨테이너는 이니셜라이저 목록을 사용하여 생성할 수 있습니다. 요소를 추가 및 제거 하 고 다른 작업을 수행 하기 위한 멤버 함수가 있습니다.

[반복기](../standard-library/iterators.md)를 사용하여 컨테이너의 요소를 반복하고 개별 요소에 액세스합니다. 해당 멤버 함수 및 연산자와 전역 함수를 사용 하 여 반복기를 명시적으로 사용할 수 있습니다. 예를 들면 range-for 루프를 암시적으로 사용할 수도 있습니다. 모든 C++ 표준 라이브러리 컨테이너에 대한 반복기에 공통적인 인터페이스가 있지만 각 컨테이너에서 자체적으로 특수화된 반복기를 정의합니다.

컨테이너는 시퀀스 컨테이너, 연관 컨테이너 및 컨테이너 어댑터의 세 가지 범주로 나눌 수 있습니다.

## <a name="sequence-containers"></a><a name="sequence_containers"></a> 시퀀스 컨테이너

시퀀스 컨테이너는 지정된 요소가 삽입된 순서를 유지합니다.

`vector` 컨테이너는 배열처럼 동작하지만 필요에 따라 자동으로 증가할 수 있습니다. 임의로 액세스되고 지속적으로 저장되며 길이가 매우 유연하게 조정됩니다. 따라서 `vector`는 대부분의 애플리케이션에 대한 기본 시퀀스 컨테이너입니다. 사용할 시퀀스 컨테이너의 종류에 대해 확실히 모르는 경우 벡터를 사용하여 시작합니다. 자세한 내용은 [vector 클래스](../standard-library/vector-class.md)를 참조하세요.

`array`컨테이너는의 일부 장점을 `vector` 갖지만 길이는 유연성이 아닙니다. 자세한 내용은 [array 클래스](../standard-library/array-class-stl.md)를 참조하세요.

`deque`(양쪽구 큐) 컨테이너를 사용하면 컨테이너의 시작과 끝에 빠르게 삽입하고 삭제할 수 있습니다. 의 임의 액세스 및 유연한 길이 장점을 공유 `vector` 하지만 인접 하지는 않습니다. 자세한 내용은 [deque 클래스](../standard-library/deque-class.md)를 참조하세요.

`list`컨테이너는 컨테이너의 모든 위치에서 양방향 액세스, 빠른 삽입 및 빠른 삭제가 가능한 이중 연결 목록 이지만, 컨테이너의 요소에 임의로 액세스할 수는 없습니다. 자세한 내용은 [list 클래스](../standard-library/list-class.md)를 참조하세요.

`forward_list` 컨테이너는 `list`의 전방향 액세스 버전인 단일 연결 목록입니다. 자세한 내용은 [forward_list 클래스](../standard-library/forward-list-class.md)를 참조하세요.

## <a name="associative-containers"></a>연관 컨테이너

연관 컨테이너에서 요소는 미리 정의된 순서(예: 오름차순 정렬)로 삽입됩니다. 순서가 지정되지 않은 연관 컨테이너도 사용할 수 있습니다. 연관 컨테이너를 맵 및 집합의 두 하위 집합으로 그룹화할 수 있습니다.

`map`은 사전이라고도 하며 키/값 쌍으로 구성됩니다. 키는 시퀀스의 순서를 지정하는 데 사용되며, 값이 해당 키에 연결됩니다. 예를 들어, `map`은 텍스트로 된 모든 고유한 단어를 나타내는 키와 각 단어가 텍스트에 표시되는 횟수를 나타내는 해당 값을 포함할 수 있습니다. `map`의 순서가 지정되지 않은 버전은 `unordered_map`입니다. 자세한 내용은 [map 클래스](../standard-library/map-class.md) 및 [unordered_map 클래스](../standard-library/unordered-map-class.md)를 참조하세요.

`set`은 고유 요소의 오름차순 컨테이너이고, 값이 키입니다. `set`의 순서가 지정되지 않은 버전은 `unordered_set`입니다. 자세한 내용은 [set 클래스](../standard-library/set-class.md) 및 [unordered_set 클래스](../standard-library/unordered-set-class.md)를 참조하세요.

`map` 및 `set`를 사용하여 키 또는 요소의 인스턴스를 컨테이너에 하나만 삽입할 수 있습니다. 요소의 여러 인스턴스가 필요한 경우 `multimap` 또는 `multiset`를 사용하세요. 순서가 지정되지 않은 버전은 `unordered_multimap` 및 `unordered_multiset`입니다. 자세한 내용은 [multimap 클래스](../standard-library/multimap-class.md), [unordered_multimap 클래스](../standard-library/unordered-multimap-class.md), [multiset 클래스](../standard-library/multiset-class.md) 및 [unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)를 참조하세요.

순서가 지정된 맵 및 집합은 양방향 반복기를 지원하고 순서가 지정되지 않은 맵 및 집합은 정방향 반복기를 지원합니다. 자세한 내용은 [반복기](../standard-library/iterators.md)를 참조하세요.

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>연관 컨테이너의 유형이 다른 조회(C++14)

이제 정렬 된 연관 컨테이너 (map, multimap, set 및 multiset)가 유형이 다른 조회를 지원 합니다. 즉, 및와 같은 멤버 함수의 키 또는 요소와 정확히 같은 개체 형식을 전달할 필요가 없습니다 `find()` `lower_bound()` . 대신, 오버로드된 `operator<`가 정의되어 있으며 키 형식 비교가 가능하다면 어떠한 형식도 전달할 수 있습니다.

컨테이너 변수를 선언할 때 다음과 같이 `std::less<>` 또는 `std::greater<>` "다이아몬드 함수자" 비교 연산자를 지정하면 유형이 다른 조회가 옵트인 방식으로 사용하도록 설정됩니다.

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

기본 비교 연산자를 사용하는 경우 컨테이너는 C++11 이전의 경우와 똑같이 작동합니다.

다음 예제에서는 `operator<` 의 사용자가 `std::set` 각 개체의 멤버와 비교할 수 있는 작은 문자열을 전달 하 여 조회를 수행할 수 있도록를 오버 로드 하는 방법을 보여 줍니다 `BigObject::id` .

```cpp
#include <set>
#include <string>
#include <iostream>
#include <functional>

using namespace std;

class BigObject
{
public:
    string id;
    explicit BigObject(const string& s) : id(s) {}
    bool operator< (const BigObject& other) const
    {
        return this->id < other.id;
    }

    // Other members....
};

inline bool operator<(const string& otherId, const BigObject& obj)
{
    return otherId < obj.id;
}

inline bool operator<(const BigObject& obj, const string& otherId)
{
    return obj.id < otherId;
}

int main()
{
    // Use C++14 brace-init syntax to invoke BigObject(string).
    // The s suffix invokes string ctor. It is a C++14 user-defined
    // literal defined in <string>
    BigObject b1{ "42F"s };
    BigObject b2{ "52F"s };
    BigObject b3{ "62F"s };
    set<BigObject, less<>> myNewSet; // C++14
    myNewSet.insert(b1);
    myNewSet.insert(b2);
    myNewSet.insert(b3);
    auto it = myNewSet.find(string("62F"));
    if (it != myNewSet.end())
        cout << "myNewSet element = " << it->id << endl;
    else
        cout << "element not found " << endl;

    // Keep console open in debug mode:
    cout << endl << "Press Enter to exit.";
    string s;
    getline(cin, s);
    return 0;
}

//Output: myNewSet element = 62F
```

Map, multimap, set 및 multiset의 다음 멤버 함수는 유형이 다른 조회를 지원 하도록 오버 로드 되었습니다.

1. 찾기

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>컨테이너 어댑터

컨테이너 어댑터는 간단 명료하게 인터페이스를 제한하는 시퀀스 또는 연관 컨테이너의 변형입니다. 컨테이너 어댑터는 반복기를 지원 하지 않습니다.

`queue` 컨테이너는 FIFO(선입 선출) 의미 체계를 따릅니다. 큐에 *푸시*(삽입)되는 첫 번째 요소가 큐에서 처음으로 *팝*(제거)됩니다. 자세한 내용은 [queue 클래스](../standard-library/queue-class.md)를 참조하세요.

`priority_queue` 컨테이너는 값이 가장 큰 요소가 항상 큐에서 첫 번째에 위치하도록 구성됩니다. 자세한 내용은 [priority_queue 클래스](../standard-library/priority-queue-class.md)를 참조하세요.

`stack` 컨테이너는 LIFO(후입 선출) 의미 체계를 따릅니다. 스택에 푸시된 마지막 요소가 첫 번째 팝되는 요소입니다. 자세한 내용은 [stack 클래스](../standard-library/stack-class.md)를 참조하세요.

컨테이너 어댑터는 반복기를 지원 하지 않기 때문에 c + + 표준 라이브러리 알고리즘과 함께 사용할 수 없습니다. 자세한 내용은 [알고리즘](../standard-library/algorithms.md)을 참조하세요.

## <a name="requirements-for-container-elements"></a>컨테이너 요소에 대한 요구 사항

일반적으로 C++ 표준 라이브러리 컨테이너에 삽입되는 요소는 임의의 개체 형식에 대한 요소입니다(복사할 수 있는 경우). 이동 전용 요소(예: `vector<unique_ptr<T>>`을 사용하여 만든 `unique_ptr<>`)는 복사를 시도하는 멤버 함수를 호출하지 않는 한 작동합니다.

소멸자는 예외를 throw 할 수 없습니다.

이 문서의 앞부분에서 설명한 순서가 지정된 연관 컨테이너는 공용 비교 연산자를 정의해야 합니다. 기본적으로 연산자는 `operator<`이지만 `operator<`를 사용하지 않는 형식도 지원됩니다.

또한 컨테이너의 일부 작업은 공용 기본 생성자와 해당하는 공용연산자가 필요할 수 있습니다. 예를 들어, 순서가 지정되지 않은 연관 컨테이너는 같음 및 해시를 지원해야 합니다.

## <a name="accessing-container-elements"></a>컨테이너 요소 액세스

반복기를 사용하여 컨테이너 요소에 액세스합니다. 자세한 내용은 [반복기](../standard-library/iterators.md)를 참조하세요.

> [!NOTE]
> [range-based for 루프](../cpp/range-based-for-statement-cpp.md)를 사용하여 C++ 표준 라이브러리 컬렉션을 반복할 수도 있습니다.

## <a name="comparing-containers"></a>컨테이너 비교

모든 컨테이너는 같은 요소 형식을 가진 같은 형식의 두 컨테이너를 비교하기 위해 == 연산자를 오버로드합니다. = =를 사용 하 여 벡터를 \<string> 다른 벡터와 비교할 수 있지만 벡터를 \<string> 목록 또는 벡터와 비교 하는 데 사용할 수는 없습니다 \<string> \<string> \<string> \<char*> .  C + + 98/03에서는 [std:: equal](algorithm-functions.md#equal) 또는 [std:: 불일치](algorithm-functions.md#mismatch) 를 사용 하 여 다른 종류의 컨테이너 형식 및/또는 요소 형식을 비교할 수 있습니다. C + + 11에서는 [std:: is_permutation](algorithm-functions.md#is_permutation)를 사용할 수도 있습니다. 그러나 이러한 모든 경우에 함수는 컨테이너의 길이가 동일 하다 고 가정 합니다. 두 번째 범위가 첫 번째 범위보다 짧은 경우 정의되지 않은 동작이 나타납니다. 두 번째 범위가 더 긴 경우에도 첫 번째 범위의 끝 이후에는 비교가 계속되지 않기 때문에 잘못된 결과가 나옵니다.

### <a name="comparing-dissimilar-containers-c14"></a>다른 종류의 컨테이너 비교(C++14)

C + + 14 이상에서는 `std::equal` `std::mismatch` `std::is_permutation` 두 개의 전체 범위를 사용 하는, 또는 함수 오버 로드 중 하나를 사용 하 여 다른 종류의 컨테이너 및/또는 서로 다른 요소 형식을 비교할 수 있습니다. 이러한 오버로드를 사용하면 길이가 서로 다른 컨테이너를 비교할 수 있습니다. 이 오버로드는 사용자 오류 취약성이 훨씬 덜하며 길이가 서로 다른 컨테이너를 비교할 때 일정한 시간에 false를 반환하도록 최적화되어 있습니다. 따라서 이러한 오버 로드를 사용 하지 않는 것이 좋습니다. 그렇지 않은 경우에는 이러한 오버 로드를 사용 하는 것이 좋습니다 .이는 이중 범위 최적화의 이점을 활용 하지 않는 [std:: list](../standard-library/list-class.md) 컨테이너를 사용 하는 것입니다.

## <a name="see-also"></a>참고 항목

[병렬 컨테이너](../parallel/concrt/parallel-containers-and-objects.md)\
[\<sample container>](../standard-library/sample-container.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
