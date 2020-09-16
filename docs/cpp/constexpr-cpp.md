---
title: constexpr(C++)
description: C + + 언어 키워드에 대 한 지침 constexpr 입니다.
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 57ebf4bf69c768bfcd2e4d26a5c3334ca788b08f
ms.sourcegitcommit: a6b97f5d78299ad93675de2fe0f0561f528d26c7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90569564"
---
# <a name="no-locconstexpr-c"></a>constexpr(C++)

키워드는 c + + **`constexpr`** 11에서 도입 되었으며 c + + 14에서 향상 되었습니다. 이것은 * const ant 식*입니다. 마찬가지로 **`const`** 변수에 적용할 수 있습니다. 코드에서 값을 mod로 시도 하면 컴파일러 오류가 발생 if 합니다. 와 달리 **`const`** 는 **`constexpr`** 함수와 클래스 ructors에도 적용 될 수 있습니다 const . **`constexpr`** 값 또는 반환 값이 const ant 이며 가능 하면 컴파일 시간에 계산 됨을 나타냅니다.

**`constexpr`** 정수 값은 const 템플릿 인수 및 배열 선언과 같이 정수를 필요로 하는 모든 곳에서 사용할 수 있습니다. 런타임 대신 컴파일 시간에 값을 계산 하는 경우에는 프로그램을 더 빠르게 실행 하 고 메모리를 절약 하는 데 도움이 됩니다.

컴파일 시간 const ant 계산의 복잡성 및 컴파일 시간에 대 한 잠재적 영향을 제한 하려면 c + + 14 표준에서 ant 식의 형식이 const [리터럴 형식](trivial-standard-layout-and-pod-types.md#literal_types)이어야 합니다.

## <a name="syntax"></a>구문

> **`constexpr`***리터럴 형식의* *ident if * **=** * const 식 ant-식* **;**\
> **`constexpr`***리터럴 형식* *ident if * **{** * const ant-expression* **}** **;**\
> **`constexpr`***리터럴 형식* *ident if * **(** *params* **)** **;**\
> **`constexpr`***ctor* **(** *params* **)** **;**

## <a name="parameters"></a>매개 변수

*params*\
하나 이상의 매개 변수입니다. 각 매개 변수는 리터럴 형식 이어야 하며 그 자체가 ant 식일 수 있어야 합니다 const .

## <a name="return-value"></a>반환 값

**`constexpr`** 변수나 함수는 [리터럴 형식을](trivial-standard-layout-and-pod-types.md#literal_types)반환 해야 합니다.

## <a name="no-locconstexpr-variables"></a>constexpr 변수

if및 변수 간의 주 d f)은 런타임까지 **`const`** **`constexpr`** 변수 초기화가 **`const`** 지연 될 수 있다는 것입니다. **`constexpr`** 변수는 컴파일 타임에 초기화 되어야 합니다.  모든 **`constexpr`** 변수는 **`const`** 입니다.

- 변수는 **`constexpr`** 리터럴 형식이 있고 초기화 될 때를 사용 하 여 선언할 수 있습니다. 초기화가 ructor에 의해 med-v 당 인 경우 for const ructor를 const 로 선언 해야 합니다 **`constexpr`** .

- 참조는 두 조건이 모두 충족 되는 경우로 선언할 수 있습니다 **`constexpr`** . 참조 된 개체가 ant 식에 의해 초기화 되 const 고 초기화 중에 호출 되는 모든 암시적 변환도 const ant 식입니다.

- **`constexpr`** 변수 또는 함수의 모든 선언에는 spec이 있어야 **`constexpr`** 합니다 if .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="no-locconstexpr-functions"></a><a name="constexpr_functions"></a> constexpr 함수

**`constexpr`** 함수는 코드를 사용 하는 경우 컴파일 시간에 반환 값이 계산할 수 함수입니다. 코드를 사용 하려면 컴파일 시간에 변수를 초기화 하기 위한 반환 값 **`constexpr`** 이 필요 하거나 비 형식 템플릿 인수를 제공 해야 합니다. 인수가 **`constexpr`** 값인 경우 **`constexpr`** 함수는 컴파일 타임 ant를 생성 const 합니다. 인수가 아닌를 사용 하 여 호출 **`constexpr`** 하거나 컴파일 타임에 해당 값이 필요 하지 않은 경우 일반 함수 처럼 런타임에 값을 생성 합니다. 이 이중 동작을 통해 동일한 함수를 작성 하 **`constexpr`** 고 버전이 아닌 것을 방지할 수 있습니다 **`constexpr`** .

**`constexpr`** 함수나 const ructor는 암시적 **`inline`** 입니다.

함수에 적용 되는 규칙은 constexpr 다음과 같습니다.

- **`constexpr`** 함수는 [리터럴 형식만](trivial-standard-layout-and-pod-types.md#literal_types)수락 하 고 반환 해야 합니다.

- **`constexpr`** 함수는 재귀적 일 수 있습니다.

- [가상](../cpp/virtual-cpp.md)일 수 없습니다. constRuctor는 **`constexpr`** 바깥쪽 클래스에 가상 기본 클래스가 있는 경우로 정의할 수 없습니다.

- 본문은 `= default` 또는 `= delete`로 정의할 수 있습니다.

- 본문은 문이나 블록을 포함할 수 없습니다 **`goto`** **`try`** .

- 비템플릿의 명시적 특수화는 **`constexpr`** 다음과 같이 선언할 수 있습니다 **`constexpr`** .

- 또한 템플릿의 명시적 특수화는 **`constexpr`** 다음과 같을 필요가 없습니다 **`constexpr`** .

다음 규칙은 **`constexpr`** Visual Studio 2017 이상 버전의 함수에 적용 됩니다.

- **`if`** 및 **`switch`** 문과 **`for`** , 범위 기반 **`for`** , **`while`** 및 **do while **를 비롯 한 모든 루핑 문을 포함할 수 있습니다.

- 지역 변수 선언을 포함할 수 있지만 변수를 초기화 해야 합니다. 리터럴 형식 이어야 하며, 또는 스레드 로컬이 될 수 없습니다 **`static`** . 로컬로 선언 된 변수는 일 필요는 **`const`** 없으며 변경할 수도 있습니다.

- 비멤버 함수는 암시적이 지 않아도 **`constexpr`** **`static`** 됩니다 **`const`** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}
```

> [!TIP]
> Visual Studio 디버거에서는 최적화 되지 않은 디버그 빌드를 디버그할 때 **`constexpr`** 함수 안에 중단점을 배치 하 여 컴파일 시간에 함수가 계산 되는지 여부를 확인할 수 있습니다. 중단점을 적중할 경우 함수가 런타임에 호출되었습니다.  그렇지 않을 경우 함수가 컴파일 타임에 호출되었습니다.

## <a name="extern-no-locconstexpr"></a>시키거나 constexpr

[/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) 컴파일러 옵션을 사용 하면 컴파일러가 ** constexpr extern **을 사용 하 여 선언 된 변수에 [외부 링크](../c-language/external-linkage.md) 를 적용 합니다. 이전 버전의 Visual Studio에서는 기본적으로 또는 **/zc: externConstexpr-** 가 spec 인 경우 if 키워드가 사용 되는 경우에도 visual studio에서 변수에 내부 링크를 적용 **`constexpr`** **`extern`** 합니다. **/Zc: externConstexpr** 옵션은 Visual Studio 2017 업데이트 15.6부터 사용할 수 있으며 기본적으로 해제 되어 있습니다. [/Permissive-](../build/reference/permissive-standards-conformance.md) 옵션은 **/zc: externConstexpr**를 사용 하지 않습니다.

## <a name="example"></a>예제

다음 예에서는 **`constexpr`** 변수, 함수 및 사용자 정의 형식을 보여 줍니다. 의 마지막 문에서 `main()` **`constexpr`** 멤버 함수는 `GetValue()` 컴파일 시간에 값을 알 필요가 없기 때문에 런타임 호출입니다.

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
}

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>요구 사항

Visual Studio 2015 이상.

## <a name="see-also"></a>참조

[선언 및 정의](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
