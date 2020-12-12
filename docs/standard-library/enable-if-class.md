---
description: Enable_if 클래스에 대해 자세히 알아보세요.
title: enable_if 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: 89bd78113a9f6ea9d94a69decccd58c7953e4a8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324464"
---
# <a name="enable_if-class"></a>enable_if 클래스

SFINAE 오버로드 확인을 위한 형식의 인스턴스를 조건부로 만듭니다. 중첩 된 typedef는 이며, `enable_if<Condition,Type>::type` 가 인 경우에 `Type` 만 인 경우와 동의어 `Condition` 입니다 **`true`** .

## <a name="syntax"></a>구문

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>매개 변수

*B*\
결과 형식의 존재를 확인하는 값입니다.

*트*\
*B* 가 true 인 경우 인스턴스화할 형식입니다.

## <a name="remarks"></a>설명

*B* 가 true 인 경우에는 `enable_if<B, T>` *T* 의 동의어 인 "type" 이라는 중첩 된 typedef가 있습니다.

*B* 가 false 이면에는 `enable_if<B, T>` 중첩 typedef "type"이 없습니다.

다음 별칭 템플릿이 제공됩니다.

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

C++에서 템플릿 매개 변수의 대체 실패는 그 자체만으로는 오류가 아닙니다. 이를 *SFINAE*(대체 실패는 오류가 아닙니다)라고도 합니다. 일반적으로 `enable_if`는 오버로드 확인에서 후보를 제거하는 데 사용됩니다. 즉, 오버로드 집합을 선별합니다. 따라서 다른 정의를 사용하기 위해 정의 하나가 거부될 수 있습니다. 이는 SFINAE 동작을 따릅니다. SFINAE에 대한 자세한 내용은 Wikipedia에서 [Substitution failure is not an error](https://go.microsoft.com/fwlink/p/?linkid=394798)(대체 실패는 오류가 아닙니다)를 참조하세요.

다음은 4가지 예제 시나리오입니다.

- 시나리오 1: 함수의 반환 형식 래핑:

```cpp
    template <your_stuff>
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
}
// The alias template makes it more concise:
    template <your_stuff>
enable_if_t<your_condition, your_return_type>
yourfunction(args) {// ...
}
```

- 시나리오 2: 기본 인수가 있는 함수 매개 변수 추가:

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- 시나리오 3: 기본 인수가 있는 템플릿 매개 변수 추가:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- 시나리오 4: 함수에 템플릿이 아닌 인수가 있는 경우 해당 인수의 형식을 래핑할 수 있음:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

생성자 및 변환 연산자에는 반환 형식이 없으므로 시나리오 1의 경우 생성자 및 변환 연산자를 사용하지 않습니다.

시나리오 2는 매개 변수를 명명하지 않은 채 그대로 둡니다. `::type Dummy = BAR`이라고 할 수 있지만 이름 `Dummy`는 상관이 없으므로 매개 변수에 이름을 지정하면 "참조되지 않은 매개 변수" 경고가 트리거될 수 있습니다. `FOO` 함수 매개 변수 형식과 `BAR` 기본 인수를 선택해야 합니다.  **`int`** 및를 사용할 수 `0` 있지만, 코드의 사용자가 실수로 함수를 함수에 전달 하 여 무시 되는 추가 정수를 제공할 수 있습니다. 대신, 또는 중 하나를 사용 하는 것 `void **` `0` 이 좋습니다 **`nullptr`** `void **` .

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

시나리오 2 역시 일반 생성자에 대해서 작동합니다.  그러나 변환 연산자는 추가 매개 변수를 사용할 수 없으므로 이 시나리오는 변환 연산자에 대해서는 작동하지 않습니다.  불필요한 매개 변수를 추가하면 함수 매개 변수 팩이 추론되지 않은 컨텍스트가 되어 `enable_if`의 목적에서 벗어나므로 시나리오 2는 [variadic](../cpp/ellipses-and-variadic-templates.md) 생성자에 대해서도 작동하지 않습니다.

시나리오 3은 이름 `Dummy`를 사용하지만 이는 선택 사항입니다. "`typename = typename`"만 작동합니다. 이상하다는 생각이 들면 "dummy" 이름을 사용할 수도 있지만 함수 정의에 사용되었을 수 있는 이름은 사용하지 마세요. `enable_if`에 형식을 지정하지 않으면 기본적으로 void 형식이 됩니다. 이는 `Dummy`가 무엇인지 신경을 쓰지 않으므로 완벽하게 합리적입니다. 이 시나리오는 변환 연산자와 [variadic](../cpp/ellipses-and-variadic-templates.md) 생성자를 비롯하여 모든 경우에 작동합니다.

시나리오 4는 반환 형식이 없는 생성자에서 작동하므로 시나리오 1의 래핑 제한 문제를 해결합니다.  그러나 시나리오 4는 템플릿이 아닌 함수 인수로 제한됩니다. 이러한 인수는 사용할 수 없는 경우도 있습니다.  템플릿 함수 인수에 시나리오 4를 사용하면 시나리오 4에 대해 템플릿 인수 추론이 수행되지 않습니다.

`enable_if`는 강력하지만 잘못 사용되면 위험하기도 합니다.  이 클래스의 용도는 오버로드 확인 전 후보를 없애는 것이므로 이 클래스를 잘못 사용하면 그 영향은 매우 혼란스러울 수 있습니다.  몇 가지 권장 사항입니다.

- 컴파일 시 구현 중에 `enable_if`를 사용하여 선택하지 마세요. `enable_if` 하나를 `CONDITION`에 대해 작성하고 다른 하나를 `!CONDITION`에 대해 작성하지 마세요.  대신 *태그 디스패치* 패턴을 사용합니다. 예를 들어 지정된 반복기의 강도에 따라 구현을 선택하는 알고리즘을 사용합니다.

- `enable_if`를 사용하여 요구 사항을 적용하지 마세요.  템플릿 매개 변수에 대한 유효성을 검사하려는 데 유효성 검사에 실패하여 오류가 발생하면 다른 구현을 선택하지 말고 [static_assert](../cpp/static-assert.md)를 사용합니다.

- 사용하지 않으면 좋은 코드를 모호하게 만드는 오버로드 집합이 있는 경우에는 `enable_if`를 사용합니다.  가장 일반적으로 이러한 경우는 생성자를 암시적으로 변환할 때 발생합니다.

## <a name="example"></a>예제

다음 예제는 C++ 표준 라이브러리 템플릿 함수 [std::make_pair()](../standard-library/utility-functions.md#make_pair)가 `enable_if`를 활용하는 방법을 보여 줍니다.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

이 예제에서 `make_pair("foo", "bar")`는 `pair<const char *, const char *>`을 반환합니다. 오버로드 확인은 사용자가 원하는 `func()`를 확인해야 합니다. `pair<A, B>`에는 `pair<X, Y>`에서 암시적으로 변환된 생성자가 있습니다.  이는 새로운 기능이 아니라 C++98에 있던 기능입니다. 그러나 C++98/03에서는 `pair<int, int>(const pair<const char *, const char *>&)`인 경우라도 암시적 변환 생성자의 서명이 항상 존재했습니다.  오버 로드 확인은로 암시적으로 변환할 수 없기 때문에 끔찍하게 전개 개의치 않고 생성자를 인스턴스화하 려는 것을 고려 하지 않습니다. `const char *` **`int`** 함수 정의가 인스턴스화되기 전에 서명만 확인 합니다.  따라서 서명은 `pair<const char *, const char *>`을 `pair<int, int>` 및 `pair<string, string>` 둘 다로 변환하기 위해 존재하므로 예제 코드가 모호합니다.

C++11에서는 `enable_if`를 사용하여 `const X&`가 `A`로 암시적으로 변환 가능하고 `const Y&`가 로 암시적으로 `B`로 변환 가능한 경우 **에만**`pair<A, B>(const pair<X, Y>&)`가 존재하도록 보장하여 이러한 모호성을 해결했습니다.  따라서 오버로드 확인을 통해 `pair<const char *, const char *>`을 `pair<int, int>`로 변환할 수 없는지 그리고 `pair<string, string>`을 사용하는 오버로드가 실행 가능한지 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
