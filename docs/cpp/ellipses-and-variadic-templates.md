---
description: '자세한 정보: 줄임표 및 Variadic 템플릿'
title: 줄임표 및 Variadic 템플릿
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 37cb2e02f818cc5d4db8954a348fc749a477b7d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195466"
---
# <a name="ellipsis-and-variadic-templates"></a>줄임표 및 Variadic 템플릿

이 문서에서는 `...` c + + variadic 템플릿과 함께 줄임표 ()를 사용 하는 방법을 보여 줍니다. 줄임표는 C 및 c + +에서 많은 용도로 사용 됩니다. 여기에는 함수에 대 한 가변 인수 목록이 포함 됩니다. `printf()`C 런타임 라이브러리의 함수는 가장 잘 알려진 예제 중 하나입니다.

*Variadic 템플릿* 은 임의 개수의 인수를 지 원하는 클래스 또는 함수 템플릿입니다. 이 메커니즘은 클래스 템플릿과 함수 템플릿에 모두 적용할 수 있으므로 다양 한 형식의 안전 하 고 특수 기능 및 유연성을 제공 하므로 c + + 라이브러리 개발자에 게 특히 유용 합니다.

## <a name="syntax"></a>Syntax

Variadic 템플릿을 사용 하 여 두 가지 방법으로 줄임표를 사용 합니다. 매개 변수 이름의 왼쪽은 매개 변수 *팩* 을 나타내고 매개 변수 이름 오른쪽은 매개 변수 팩을 별도의 이름으로 확장 합니다.

*Variadic 템플릿 클래스* 정의 구문의 기본 예는 다음과 같습니다.

```cpp
template<typename... Arguments> class classname;
```

팩 및 확장 매개 변수의 경우 다음 예에서 같이 기본 설정에 따라 줄임표 주위에 공백을 추가할 수 있습니다.

```cpp
template<typename ...Arguments> class classname;
```

또는 다음을 사용하세요.

```cpp
template<typename ... Arguments> class classname;
```

이 문서에서는 첫 번째 예제에 표시 된 규칙을 사용 합니다 (줄임표는에 연결 됨 **`typename`** ).

앞의 예제에서 *인수* 는 매개 변수 팩입니다. 클래스는 `classname` 다음 예제와 같이 다양 한 수의 인수를 사용할 수 있습니다.

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

Variadic 템플릿 클래스 정의를 사용 하 여 매개 변수를 하나 이상 요구할 수도 있습니다.

```cpp
template <typename First, typename... Rest> class classname;
```

*Variadic 템플릿 함수* 구문의 기본 예는 다음과 같습니다.

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

다음 섹션인 **variadic 템플릿 이해** 에 나와 있는 것 처럼 *Arguments* 매개 변수 팩은 사용 하도록 확장 됩니다.

이러한 예제를 비롯 하 여 다른 형태의 variadic 템플릿 함수 구문을 사용할 수 있습니다.

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

같은 지정자 **`const`** 도 사용할 수 있습니다.

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Variadic 템플릿 클래스 정의와 마찬가지로 하나 이상의 매개 변수를 요구 하는 함수를 만들 수 있습니다.

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Variadic 템플릿은 `sizeof...()` 연산자 (이전 연산자와 무관 함)를 사용 합니다 `sizeof()` .

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>줄임표 배치에 대한 자세한 내용

이 문서의 앞 부분에서 "매개 변수 이름의 왼쪽은 매개 변수 팩을 나타내고 매개 변수 이름 오른쪽은 매개 변수 팩을 별도의 이름으로 확장"한다고 매개 변수 팩과 확장을 정의하는 줄임표 배치에 대해 설명했습니다. 이는 기술적으로는 맞지만 코드로 변환할 때 혼동될 수 있습니다. 고려할 사항은 다음과 같습니다.

- 템플릿 매개 변수 목록 ( `template <parameter-list>` )에서 `typename...` 템플릿 매개 변수 팩을 소개 합니다.

- 매개 변수-선언-절 ( `func(parameter-list)` )에서 "최상위" 줄임표는 함수 매개 변수 팩을 도입 하 고 줄임표 위치 지정이 중요 합니다.

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- 매개 변수 이름 바로 뒤에 줄임표가 표시된 경우 매개 변수 팩 확장이 있는 것입니다.

## <a name="example"></a>예제

Variadic 템플릿 함수 메커니즘을 설명 하는 좋은 방법은의 기능 중 일부를 다시 작성 하는 데 사용 하는 것입니다 `printf` .

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>출력

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
> Variadic 템플릿 함수를 통합 하는 대부분의 구현은 일부 형식의 재귀를 사용 하지만 기존 재귀와는 약간 다릅니다.  기존 재귀는 동일한 서명을 사용 하 여 자신을 호출 하는 함수를 포함 합니다. (오버 로드 되거나 템플릿 템플릿을 사용할 수 있지만 매번 동일한 서명이 선택 됩니다.) Variadic 재귀에는 서로 다른 (거의 항상 감소) 개수의 인수를 사용 하 여 Variadic 함수 템플릿을 호출 하는 작업이 포함 되므로 매번 다른 서명을 기록 합니다. "기본 사례"는 여전히 필요 하지만 재귀의 특성은 서로 다릅니다.
