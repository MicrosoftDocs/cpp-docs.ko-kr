---
title: C++ 시작하기 - 최신 C++
description: 최신 C++의 새로운 프로그래밍 관용구와 그 근거를 설명합니다.
ms.date: 05/17/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: f2b9159e74ba7ce37c7eab1513826da939a3be49
ms.sourcegitcommit: f1752bf90b4f869633a859ace85439ca19e208b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2020
ms.locfileid: "87232198"
---
# <a name="welcome-back-to-c---modern-c"></a>C++ 시작하기 - 최신 C++

C++는 만들어진 이후 전 세계에서 가장 널리 사용되는 프로그래밍 언어 중 하나가 되었습니다. 잘 작성된 C++ 프로그램은 빠르고 효율적입니다. C++ 언어는 다른 언어보다 유연성이 높습니다. 가장 높은 추상화 수준은 물론 낮게는 회로 설계 시에도 사용할 수 있습니다. C++는 고도로 최적화된 표준 라이브러리를 제공합니다. 이를 통해 낮은 수준의 하드웨어 기능에 액세스하여 속도를 최대한으로 높이고 메모리 요구 사항을 최소화할 수 있습니다. C++를 사용하여 만들 수 있는 앱은 게임, 디바이스 드라이버, 고성능 과학 소프트웨어, 기본 포함 프로그램, Windows 클라이언트 앱 등 다양합니다. 심지어 다른 프로그래밍 언어를 위한 라이브러리와 컴파일러도 C++로 작성됩니다.

C++의 본래 요구 사항 중 하나는 C 언어와의 역 호환성이었습니다. 따라서 C++에서는 원시 포인터, 배열, null 종료 문자열, 기타 기능을 통해 항상 C 스타일 프로그래밍이 가능했습니다. 이로 인해 성능이 향상될 수 있는 반면 버그 및 복잡성이 생성될 수도 있습니다. C++가 진화하면서 C 스타일 관용구를 사용할 필요성을 크게 줄이는 기능이 강조되었습니다. 필요하다면 이전 C 프로그래밍 기능을 사용할 수도 있지만 최신 C++ 코드에서는 그 필요성이 점점 줄어듭니다. 최신 C++ 코드는 보다 간단하고 안전하고 명쾌하면서도 속도는 가장 빠릅니다.

다음 섹션에서는 최신 C++의 주요 기능에 대한 개요를 제공합니다. 별도로 언급하지 않는 한 여기에 나열된 기능은 C++11 이상에서 사용할 수 있습니다. Microsoft C++ 컴파일러에서는 [`/std`](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 설정하여 프로젝트에 사용할 표준 버전을 지정할 수 있습니다.

## <a name="resources-and-smart-pointers"></a>리소스 및 스마트 포인터

C 스타일 프로그래밍의 주요 버그 클래스 중 하나는 메모리 누수입니다. 메모리 누수의 흔한 원인은 **`new`** 를 사용하여 할당된 메모리의 **`delete`** 호출 오류입니다. 최신 C++는 *Resource Acquisition Is Initialization*(RAII) 원칙을 강조합니다. 개념은 간단합니다. 리소스(힙 메모리, 파일 핸들, 소켓 등)는 개체에 의해 소유되어야 합니다. 이 개체는 해당 생성자에서 새로 할당된 리소스를 만들거나 받아 해당 소멸자에서 삭제합니다. RAII 원칙은 소유하는 개체가 범위를 벗어나면 모든 리소스가 운영 체제에 제대로 반환되도록 보장합니다.

RAII 원칙을 쉽게 채택할 수 있도록 C++ 표준 라이브러리는 [`std::unique_ptr`](../standard-library/unique-ptr-class.md), [`std::shared_ptr`](../standard-library/shared-ptr-class.md), [`std::weak_ptr`](../standard-library/weak-ptr-class.md)의 세 가지 스마트 포인터 형식을 제공합니다. 스마트 포인터는 소유하고 있는 메모리의 할당 및 삭제를 처리합니다. 다음 예제는 `make_unique()`에 대한 호출에서 힙에 할당된 배열 멤버가 있는 클래스를 보여 줍니다. **`new`** 및 **`delete`** 에 대한 호출은 `unique_ptr` 클래스에 의해 캡슐화됩니다. `widget` 개체가 범위를 벗어나면 unique_ptr 소멸자가 호출되어 배열을 위해 할당된 메모리를 해제합니다.  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

힙 메모리를 할당할 때는 가능하면 항상 스마트 포인터를 사용하세요. new 및 delete 연산자를 명시적으로 사용해야 하는 경우 RAII 원칙을 따릅니다. 자세한 내용은 [개체 수명 및 리소스 관리(RAII)](object-lifetime-and-resource-management-modern-cpp.md)를 참조하세요.

## <a name="stdstring-and-stdstring_view"></a>`std::string` 및 `std::string_view`

C 스타일 문자열은 버그의 또 다른 주요 원인입니다. [`std::string` 및 `std::wstring`](../standard-library/basic-string-class.md)를 사용하면 C 스타일 문자열과 관련된 거의 모든 오류를 제거할 수 있습니다. 또한 검색, 추가, 앞에 추가 등에서 멤버 함수의 이점을 얻을 수 있습니다. 두 가지 모두 속도에 고도로 최적화되어 있습니다. 읽기 전용 액세스만 필요한 함수에 문자열을 전달하는 경우 C++17에서는 [`std::string_view`](../standard-library/basic-string-view-class.md)를 사용하여 훨씬 큰 성능상 이점을 얻을 수 있습니다.

## <a name="stdvector-and-other-standard-library-containers"></a>`std::vector` 및 기타 표준 라이브러리 컨테이너

표준 라이브러리 컨테이너는 모두 RAII 원칙을 따르며 요소의 안전한 탐색을 위한 반복기를 제공합니다. 또한 성능에 고도로 최적화되어 있으며, 정확성을 철저하게 테스트했습니다. 이 같은 컨테이너를 사용하면 사용자 지정 데이터 구조에 유입될 수 있는 버그 또는 비효율성의 가능성을 없앨 수 있습니다. C++에서 원시 배열 대신 [`vector`](../standard-library/vector-class.md)를 순차 컨테이너로 사용하세요.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

[`map`](../standard-library/map-class.md)(`unordered_map` 아님)을 기본 연관 컨테이너로 사용하세요. 중복 제거 및 다중 케이스에는 [`set`](../standard-library/set-class.md), [`multimap`](../standard-library/multimap-class.md), [`multiset`](../standard-library/multiset-class.md)를 사용하세요.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

성능 최적화가 필요한 경우 다음을 사용하는 것이 좋습니다.

- 예를 들어 클래스 멤버로서 포함이 중요한 경우 [`array`](../standard-library/array-class-stl.md) 형식.

- [`unordered_map`](../standard-library/unordered-map-class.md)과 같이 순서가 지정되지 않은 연관 컨테이너. 이 컨테이너에는 보다 낮은 요소당 오버헤드와 상수 시간 조회가 있지만 올바르고 효율적으로 사용하기는 더 어렵습니다.

- 정렬 `vector`. 자세한 내용은 [알고리즘](../cpp/algorithms-modern-cpp.md)을 참조하세요.

C 스타일 배열을 사용하지 마세요. 직접 데이터 액세스가 필요한 이전 API의 경우 `f(vec.data(), vec.size());`와 같은 접근자 메서드를 대신 사용합니다. 컨테이너에 대한 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

## <a name="standard-library-algorithms"></a>표준 라이브러리 알고리즘

프로그램을 위한 사용자 지정 알고리즘 작성이 필요하다고 가정하기 전에 먼저 C++ 표준 라이브러리 [알고리즘](../standard-library/algorithm.md)을 검토하세요. 표준 라이브러리에는 검색, 정렬, 필터링, 무작위화 등 여러 일반적 작업을 위해 계속 늘어나는 알고리즘 모음이 포함되어 있습니다. 수식 라이브러리는 광범위합니다. C++17부터 많은 알고리즘의 병렬 버전이 제공됩니다.

몇 가지 중요한 예는 다음과 같습니다.

- 기본 탐색 알고리즘인 `for_each`(범위 기반 `for` 루프와 함께 사용).

- 컨테이너 요소의 not-in-place 수정을 위한 `transform`.

- 기본 검색 알고리즘인 `find_if`.

- `sort`, `lower_bound`, 기타 기본 정렬 및 검색 알고리즘.

비교 연산자를 쓰려면 strict **`<`** 를 사용하고 가능한 경우 명명된 람다를 사용합니다.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>명시적 형식 이름 대신 `auto`

C++11에서는 변수, 함수, 템플릿 선언에 사용할 [`auto`](auto-cpp.md) 키워드가 도입되었습니다. **`auto`** 가 개체의 형식을 추론하도록 컴파일러에 지시하므로 명시적으로 입력할 필요가 없습니다. **`auto`** 는 추론된 형식이 중첩된 템플릿인 경우 특히 유용합니다.

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>범위 기반 `for` 루프

배열 및 컨테이너에 대한 C 스타일 반복은 인덱싱 오류가 발생하기 쉬우며 입력하기도 번거롭습니다. 이러한 오류를 제거하고 코드를 더 읽기 쉽게 만들려면 표준 라이브러리 컨테이너 및 원시 배열과 함께 범위 기반 **`for`** 루프를 사용하세요. 자세한 내용은 [범위 기반 `for` 문](../cpp/range-based-for-statement-cpp.md)을 참조하세요.

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>매크로 대신 `constexpr` 식

C와 C++의 매크로는 컴파일 전에 전처리기에 의해 처리되는 토큰입니다. 매크로 토큰의 각 인스턴스는 파일이 컴파일되기 전에 정의된 값 또는 식으로 교체됩니다. 매크로는 일반적으로 C 스타일 프로그래밍에서 컴파일 시간 상수 값을 정의하는 데 사용됩니다. 그러나 매크로는 오류가 발생하기 쉬우며 디버그하기 어렵습니다. 최신 C++에서는 컴파일 시간 상수에 [`constexpr`](constexpr-cpp.md) 변수를 사용하는 것이 좋습니다.

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>균일한 초기화

최신 C++에서는 모든 형식에 중괄호 초기화를 사용할 수 있습니다. 이러한 형태의 초기화는 배열, 벡터 또는 기타 컨테이너를 초기화할 때 특히 편리합니다. 다음 예제에서는 `S` 인스턴스 세 개를 사용하여 `v2`가 초기화됩니다. `v3`는 중괄호를 사용하여 초기화되는 `S` 인스턴스 세 개를 사용하여 초기화됩니다. 컴파일러는 `v3`의 선언된 형식을 기반으로 각 요소의 형식을 추론합니다.

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

자세한 내용은 [중괄호 초기화](initializing-classes-and-structs-without-constructors-cpp.md)를 참조하세요.

## <a name="move-semantics"></a>이동 의미 체계

최신 C++는 불필요한 메모리 복사본을 제거할 수 있도록 이동 의미 체계를 제공합니다. 이전 버전의 C++에서는 특정 상황에서 복사본이 불가피했습니다. 이동 작업은 복사를 수행하지 않고 한 개체에서 다음 개체로 리소스 소유권을 전송합니다. 일부 클래스는 힙 메모리, 파일 핸들 등의 리소스를 소유합니다. 리소스 소유 클래스를 구현할 때 이동 생성자와 해당 이동 대입 연산자를 정의할 수 있습니다. 컴파일러는 복사본이 필요하지 않은 상황에서 오버로드 확인 중에 이러한 특수 멤버를 선택합니다. 표준 라이브러리 컨테이너 형식은 개체에 대해 이동 생성자를 호출합니다(정의된 경우). 자세한 내용은 [이동 생성자 및 이동 대입 연산자(C++)](move-constructors-and-move-assignment-operators-cpp.md)를 참조하세요.

## <a name="lambda-expressions"></a>람다 식

C 스타일 프로그래밍에서는 함수 포인터를 사용하여 함수를 다른 함수에 전달할 수 있습니다. 함수 포인터는 유지 관리하고 이해하기에 불편합니다. 함수 포인터가 참조하는 함수는 호출되는 지점과 멀리 떨어진 소스 코드 다른 곳에서 정의될 수 있습니다. 또한 형식이 안전하지 않습니다. 최신 C++는 [`operator()`](function-call-operator-parens.md) 연산자를 재정의하는 클래스인 함수 개체를 제공하므로 함수 개체를 함수처럼 호출할 수 있습니다. 함수 개체를 만드는 가장 편리한 방법은 인라인 [람다 식](../cpp/lambda-expressions-in-cpp.md)을 사용하는 것입니다. 다음 예제는 람다 식을 사용하여 `for_each` 함수가 벡터의 각 요소에 대해 호출할 함수 개체를 전달하는 방법을 보여 줍니다.

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

람다 식 `[=](int i) { return i > x && i < y; }`는 " **`int`** 형식의 단일 인수를 취하며 이 인수가 `x`보다 크고 `y`보다 작은지 여부를 나타내는 부울을 반환하는 함수"로 해석할 수 있습니다. 주변 컨텍스트의 `x` 및 `y` 변수를 람다에서 사용할 수 있습니다. `[=]`는 이러한 변수가 값에 의해 캡처됨을 명시합니다. 즉, 람다 식에는 이러한 값의 고유한 복사본이 있습니다.

## <a name="exceptions"></a>예외

최신 C++에서는 오류 상태를 보고하고 처리하는 가장 좋은 방법으로 오류 코드가 아닌 예외를 강조합니다. 자세한 내용은 [최신 C++ 예외 및 오류 처리 모범 사례](errors-and-exception-handling-modern-cpp.md)를 참조하세요.

## `std::atomic`

스레드 간 통신 메커니즘에 C++ 표준 라이브러리 [`std::atomic`](../standard-library/atomic-structure.md) 구조체와 관련 형식을 사용하세요.

## <a name="stdvariant-c17"></a>`std::variant`(C++17)

C 스타일 프로그래밍에서는 일반적으로 공용 구조체를 사용하여 서로 다른 형식의 멤버가 동일한 메모리 위치를 점유할 수 있도록 함으로써 메모리를 보존합니다. 하지만 공용 구조체는 형식이 안전하지 않으며 프로그래밍 오류가 발생하기 쉽습니다. C++17에서는 공용 구조체보다 강력하고 안전한 대안으로 [`std::variant`](../standard-library/variant-class.md) 클래스가 도입되었습니다. [`std::visit`](../standard-library/variant-functions.md#visit) 함수를 사용하면 `variant` 형식의 멤버에 형식이 안전한 방식으로 액세스할 수 있습니다.

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)\
[람다 식](../cpp/lambda-expressions-in-cpp.md)\
[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)\
[Microsoft C++ 언어 규칙 테이블](../overview/visual-cpp-language-conformance.md)
