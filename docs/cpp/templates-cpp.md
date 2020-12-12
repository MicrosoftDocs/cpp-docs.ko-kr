---
description: '자세한 정보: 템플릿 (c + +)'
title: 템플릿 (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 14de4372502748c4d622e8739cad82b78a55daa9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164759"
---
# <a name="templates-c"></a>템플릿 (C++)

템플릿은 c + +의 제네릭 프로그래밍에 대 한 기본입니다. 강력한 형식의 언어인 c + +에서는 프로그래머가 명시적으로 선언 하거나 컴파일러에서 추론 한 특정 형식이 모든 변수에 포함 되어야 합니다. 그러나 많은 데이터 구조와 알고리즘은 작동 하는 형식에 관계 없이 동일 하 게 보입니다. 템플릿을 사용 하면 클래스 또는 함수의 작업을 정의 하 고 사용자가 작업을 수행 해야 하는 구체적인 형식을 지정할 수 있습니다.

## <a name="defining-and-using-templates"></a>템플릿 정의 및 사용

템플릿은 사용자가 템플릿 매개 변수에 대해 제공 하는 인수를 기반으로 컴파일 시간에 일반 형식 또는 함수를 생성 하는 구문입니다. 예를 들어 다음과 같이 함수 템플릿을 정의할 수 있습니다.

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

위의 코드에서는 반환 값과 호출 매개 변수 (lhs 및 rhs)가 모두이 형식인 단일 형식 매개 변수 *T* 를 사용 하는 제네릭 함수의 템플릿을 설명 합니다. 형식 매개 변수의 이름을 원하는 대로 지정할 수 있지만 기본적으로 단일 대문자를 사용 하는 것이 가장 일반적으로 사용 됩니다. *T* 는 템플릿 매개 변수입니다. **`typename`** 키워드는이 매개 변수가 형식에 대 한 자리 표시자 임을 의미 합니다. 함수가 호출 되 면 컴파일러는 모든 인스턴스를 `T` 사용자가 지정 하거나 컴파일러에서 추론 한 구체적인 형식 인수로 바꿉니다. 컴파일러가 템플릿에서 클래스 또는 함수를 생성 하는 프로세스를  *템플릿 인스턴스화* 라고 합니다. `minimum<int>` 는 템플릿을 인스턴스화한 것입니다 `minimum<T>` .

다른 곳에서 사용자는 int에 대해 특수화 된 템플릿의 인스턴스를 선언할 수 있습니다. Get_a () 및 get_b ()이 int를 반환 하는 함수인 것으로 가정 합니다.

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

그러나이는 함수 템플릿이 고 컴파일러가 `T` *a* 와 *b* 인수에서 형식을 추론할 수 있으므로 일반 함수와 마찬가지로 호출할 수 있습니다.

```cpp
int i = minimum(a, b);
```

컴파일러가 마지막 문을 발견 하면 템플릿에서 모든 *T* 의 항목이 다음과 같이 바뀔 때 새 함수를 생성 합니다 **`int`** .

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

컴파일러가 함수 템플릿에서 형식 추론을 수행 하는 방법에 대 한 규칙은 일반 함수에 대 한 규칙을 기반으로 합니다. 자세한 내용은 [함수 템플릿 호출의 오버 로드 확인](../cpp/overload-resolution-of-function-template-calls.md)을 참조 하세요.

## <a name="type-parameters"></a><a id="type_parameters"></a> 형식 매개 변수

`minimum`위의 템플릿에서 형식 매개 변수 *T* 는 const 및 참조 한정자가 추가 되는 함수 호출 매개 변수에 사용 될 때까지 정규화 되지 않습니다.

형식 매개 변수의 수에 대 한 실질적인 제한은 없습니다. 여러 매개 변수를 쉼표로 구분 합니다.

```cpp
template <typename T, typename U, typename V> class Foo{};
```

키워드는 **`class`** **`typename`** 이 컨텍스트에서와 동일 합니다. 이전 예제를 다음과 같이 표현할 수 있습니다.

```cpp
template <class T, class U, class V> class Foo{};
```

줄임표 연산자 (...)를 사용 하 여 임의의 수의 0 개 이상의 형식 매개 변수를 사용 하는 템플릿을 정의할 수 있습니다.

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

모든 기본 제공 또는 사용자 정의 형식을 형식 인수로 사용할 수 있습니다. 예를 들어 표준 라이브러리에서 [std:: vector](../standard-library/vector-class.md) 를 사용 하 여 **`int`** , **`double`** , [std:: string](../standard-library/basic-string-class.md), `MyClass` , **`const`** `MyClass` *, `MyClass&` 등 형식의 변수를 저장할 수 있습니다. 템플릿을 사용할 때의 주요 제한 사항은 형식 인수가 형식 매개 변수에 적용 되는 모든 작업을 지원 해야 한다는 것입니다. 예를 들어 `minimum` `MyClass` 다음 예제에서를 사용 하 여를 호출 하는 경우

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

`MyClass`에서 연산자에 대 한 오버 로드를 제공 하지 않으므로 컴파일러 오류가 생성 됩니다 **<** .

이러한 제한을 적용 하는 템플릿을 정의할 수는 있지만, 특정 템플릿에 대 한 형식 인수는 모두 동일한 개체 계층 구조에 속해야 한다는 요구 사항은 없습니다. 개체 지향 기술을 템플릿과 결합할 수 있습니다. 예를 들어, 벡터에 파생 된 *를 저장할 수 있습니다 \<Base\*> .    인수는 포인터 여야 합니다.

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

`std::vector`및 기타 표준 라이브러리 컨테이너가의 요소에 적용 하는 기본 요구 사항은 `T` `T` 복사 할당 및 복사 생성 가능입니다.

## <a name="non-type-parameters"></a>비 형식 매개 변수

C # 및 Java와 같은 다른 언어의 제네릭 형식과 달리, c + + 템플릿에서는 *비 형식 매개 변수*(값 매개 변수 라고도 함)를 지원 합니다. 예를 들어 표준 라이브러리의 [std:: array](../standard-library/array-class-stl.md) 클래스와 비슷한이 예제와 같이 상수 정수 계열 값을 제공 하 여 배열의 길이를 지정할 수 있습니다.

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

템플릿 선언의 구문을 확인 합니다. `size_t`값은 컴파일 시간에 템플릿 인수로 전달 되며 **`const`** 또는 식 이어야 합니다 **`constexpr`** . 다음과 같이 사용 합니다.

```cpp
MyArray<MyClass*, 10> arr;
```

포인터 및 참조를 비롯 한 다른 종류의 값은 비 형식 매개 변수로 전달 될 수 있습니다. 예를 들어 함수 또는 함수 개체에 대 한 포인터를 전달 하 여 템플릿 코드 내의 일부 작업을 사용자 지정할 수 있습니다.

### <a name="type-deduction-for-non-type-template-parameters"></a>형식이 아닌 템플릿 매개 변수에 대 한 형식 추론

Visual Studio 2017 이상에서는 **/std: c + + 17** 모드에서 컴파일러가 추론로 선언 된 형식이 아닌 템플릿 인수의 형식을 사용 합니다 **`auto`** .

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a> 템플릿 매개 변수로 서의 템플릿

템플릿은 템플릿 매개 변수가 될 수 있습니다. 이 예제에서 MyClass2에는 두 개의 템플릿 매개 변수, 즉 typename 매개 변수 *T* 와 템플릿 매개 변수 *Arr* 이 있습니다.

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

*Arr* 매개 변수 자체에는 본문이 없으므로 매개 변수 이름이 필요 하지 않습니다. 실제로는의 본문 내에서 *Arr* 의 typename 또는 클래스 매개 변수 이름을 참조 하는 것은 오류입니다 `MyClass2` . 따라서 다음 예제와 같이  *Arr* 의 형식 매개 변수 이름을 생략할 수 있습니다.

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>기본 템플릿 인수

클래스 및 함수 템플릿에서는 기본 인수를 사용할 수 있습니다. 템플릿에 기본 인수가 있는 경우 해당 인수를 사용 하는 경우 지정 되지 않은 상태로 둘 수 있습니다. 예를 들어 std:: vector 템플릿에는 할당자에 대 한 기본 인수가 있습니다.

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

대부분의 경우 기본 std:: 할당자 클래스를 사용할 수 있으므로 다음과 같이 벡터를 사용 합니다.

```cpp
vector<int> myInts;
```

그러나 필요한 경우 다음과 같이 사용자 지정 할당자를 지정할 수 있습니다.

```cpp
vector<int, MyAllocator> ints;
```

템플릿 인수가 여러 개인 경우 첫 번째 기본 인수 다음의 모든 인수에는 기본 인수가 있어야 합니다.

매개 변수를 모두 기본값으로 사용 하는 템플릿을 사용 하는 경우 빈 꺾쇠 괄호를 사용 합니다.

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>템플릿 특수화

경우에 따라 템플릿에서 모든 형식에 대해 정확 하 게 동일한 코드를 정의 하는 것이 불가능 하거나 바람직하지 않습니다. 예를 들어 형식 인수가 포인터 또는 std:: wstring 이거나 특정 기본 클래스에서 파생 된 형식인 경우에만 실행할 코드 경로를 정의할 수 있습니다.  이러한 경우 해당 특정 형식에 대 한 템플릿의 *특수화* 를 정의할 수 있습니다. 사용자가 해당 형식을 사용 하 여 템플릿을 인스턴스화하면 컴파일러가 특수화를 사용 하 여 클래스를 생성 하 고 다른 모든 형식의 경우 컴파일러는 더 일반적인 템플릿을 선택 합니다. 모든 매개 변수가 특수화 된 특수화는 *완전 한 특수화* 입니다. 일부 매개 변수만 특수화 된 경우 *부분 특수화* 라고 합니다.

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

각 특수화 된 형식 매개 변수가 고유한 경우 템플릿에는 특수화를 개수에 관계 없이 포함할 수 있습니다. 클래스 템플릿만 부분적으로 특수화할 수 있습니다. 템플릿의 모든 전체 및 부분 특수화는 원래 템플릿과 동일한 네임 스페이스에 선언 되어야 합니다.

자세한 내용은 [템플릿 특수화](../cpp/template-specialization-cpp.md)를 참조 하세요.
