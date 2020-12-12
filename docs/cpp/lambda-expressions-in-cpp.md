---
description: '자세한 정보: c + +의 람다 식'
title: C++의 람다 식
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: 5e65279fa8740876ad8824803ec459ced154f952
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321043"
---
# <a name="lambda-expressions-in-c"></a>C++의 람다 식

C + + 11 이상에서 람다 식 (종종 *람다*)은 호출 되거나 함수에 인수로 전달 되는 위치에서 무명 함수 개체 ( *클로저*)를 정의 하는 편리한 방법입니다. 일반적으로 람다는 알고리즘이나 비동기 메서드에 전달되는 몇 줄의 코드를 캡슐화하는 데 사용됩니다. 이 문서에서는 람다가 무엇인지 정의하고 다른 프로그래밍 기법과 비교하고 그 장점을 설명하며 기본 예제를 제공합니다.

## <a name="related-topics"></a>관련 항목

- [람다 식과 함수 개체 비교](lambda-expression-syntax.md)
- [람다 식 사용](examples-of-lambda-expressions.md)
- [constexpr 람다 식](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>람다 식의 부분

ISO C++ 표준에서는 `std::sort()` 함수에 세 번째 인수로 전달되는 간단한 람다를 보여 줍니다.

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

이 그림에서는 람다의 부분을 보여 줍니다.

![람다 식의 구조 요소](../cpp/media/lambdaexpsyntax.png "람다 식의 구조 요소")

1. *capture 절* (c + + 사양의 *lambda-introducer* 라고도 함)

1. *매개 변수 목록* 필드. ( *람다 선언 자* 라고도 함)

1. *변경 가능한 사양* 필드.

1. *예외 사양* 필드.

1. *후행 반환 형식* 필드.

1. *람다 본문*.

### <a name="capture-clause"></a>캡처 절

람다는 해당 본문에 새 변수를 도입할 수 있으며 ( **c + + 14**), 주변 범위에서 변수를 액세스 하거나 *캡처할* 수도 있습니다. 람다는 캡처 절 (표준 구문의 경우 *람다-lambda-introducer* )으로 시작 하 고 캡처할 변수를 지정 하며 캡처는 값 또는 참조로 지정 합니다. 앰퍼샌드(`&`) 접두사가 있는 변수는 참조로 액세스되며 이 접두사가 없는 변수는 값으로 액세스됩니다.

빈 캡처 절인 `[ ]`는 람다 식의 본문이 바깥쪽 범위의 변수에 액세스하지 않음을 나타냅니다.

기본 캡처 모드 (표준 구문에서 *캡처-기본값* )를 사용 하 여 람다에서 참조 되는 외부 변수를 캡처하는 방법을 나타낼 수 있습니다. `[&]` 즉, 참조 하는 모든 변수가 참조로 캡처되고 값을 사용 하 `[=]` 여 캡처되고 있음을 의미 합니다. 기본 캡처 모드를 사용하고 특정 변수에 대해서는 반대 모드를 지정할 수 있습니다. 예를 들어, 람다 본문이 외부 변수 `total`에 참조별로 액세스하고 외부 변수 `factor`에 값별로 액세스하는 경우 다음 캡처 절이 동일합니다.

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

캡처 기본값을 사용 하는 경우에는 람다에 언급 된 변수만 캡처됩니다.

캡처 절이 캡처 기본값을 포함 하는 경우 `&` `identifier` `capture` 해당 캡처 절의에는 형식이 있을 수 없습니다 `& identifier` . 마찬가지로 캡처 절에 캡처 기본값을 포함 하는 경우에 `=` `capture` 는 해당 캡처 절의 형식이가 될 수 없습니다 `= identifier` . 캡처링 절에는 식별자 또는가 **`this`** 두 번 이상 나타날 수 없습니다. 다음 코드 조각은 몇 가지 사례를 보여 줍니다.

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

다음 [variadic 템플릿](../cpp/ellipses-and-variadic-templates.md) 예제에 표시 된 것 처럼, 줄임표 앞에 오는 캡처는 팩 확장입니다.

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

클래스 메서드의 본문에서 람다 식을 사용 하려면 **`this`** 포인터를 캡처 절에 전달 하 여 바깥쪽 클래스의 메서드 및 데이터 멤버에 대 한 액세스를 제공 합니다.

**Visual Studio 2017 버전 15.3 이상** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능): **`this`** **`*this`** 캡처 절에를 지정 하 여 값에 의해 포인터를 캡처할 수 있습니다. 값으로 캡처는 람다 식을 사용 하는 익명 함수 개체인 전체 *클로저* 가 람다가 호출 되는 모든 호출 사이트에 복사 됨을 의미 합니다. 값으로 캡처는 람다가 병렬 또는 비동기 작업 (특히 NUMA와 같은 특정 하드웨어 아키텍처)에서 실행 되는 경우에 유용 합니다.

클래스 메서드를 사용 하 여 람다 식을 사용 하는 방법을 보여 주는 예제는 [람다 식의 예제](../cpp/examples-of-lambda-expressions.md)에서 "예제: 메서드에 람다 식 사용"을 참조 하세요.

캡처 절을 사용하는 경우 특히 람다를 다중 스레딩과 함께 사용할 때는 다음과 같은 사항에 유의해야 합니다.

- 참조 캡처는 외부 변수를 수정하는 데 사용할 수 있지만 값 캡처는 사용할 수 없습니다 ( **`mutable`** 복사본은 수정할 수 있지만 원본은 수정할 수 없습니다.)

- 참조 캡처는 외부 변수에 대한 업데이트를 반영하지만 값 캡처는 반영하지 않습니다.

- 참조 캡처는 수명 종속성을 발생시키지만 값 캡처에는 수명 종속성이 없습니다. 이는 람다가 비동기적으로 실행되는 경우에 특히 중요합니다. 비동기 람다에서 참조를 기준으로 로컬을 캡처하는 경우 이 로컬은 람다가 실행될 때는 사라졌을 가능성이 매우 높으며, 결과적으로 런타임에 액세스 위반이 발생할 수 있습니다.

### <a name="generalized-capture-c-14"></a>일반화된 캡처(C++ 14)

C++14에서는 해당 변수가 반드시 람다 함수의 바깥쪽 범위에 존재하지 않아도 캡처 절에 새 변수를 도입하고 초기화할 수 있습니다. 이러한 초기화는 임의의 식으로 표현할 수 있습니다. 새 변수의 형식은 식에서 생성되는 형식에서 추론됩니다. 이 기능의 이점 중 하나는, C++14에서 주변 범위에서 이동 전용 변수(예: std::unique_ptr)를 캡처하여 이를 람다에서 사용할 수 있다는 점입니다.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>매개 변수 목록

변수를 캡처하는 것 외에도, 람다는 입력 매개 변수를 사용할 수 있습니다. 매개 변수 목록 (표준 구문의 *람다 선언 자* )은 선택 사항이 며 대부분의 측면에서 함수에 대 한 매개 변수 목록과 유사 합니다.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

**C + + 14** 에서 매개 변수 형식이 제네릭인 경우 **`auto`** 키워드를 형식 지정자로 사용할 수 있습니다. 이렇게 하면 함수 호출 연산자를 템플릿으로 만들도록 컴파일러에 지시합니다. **`auto`** 매개 변수 목록에 있는 각 인스턴스는 고유한 형식 매개 변수와 같습니다.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

람다 식은 다른 람다 식을 인수로 사용할 수 있습니다. 자세한 내용은 [람다 식의 예제](../cpp/examples-of-lambda-expressions.md)항목에서 "고차 람다 식"을 참조 하세요.

매개 변수 목록은 선택 사항이 기 때문에 람다 식에 인수를 전달 하지 않고 람다 선언 자에 *예외 사양*, *후행 반환 형식* 또는가 포함 되지 않은 경우 빈 괄호를 생략할 수 있습니다 **`mutable`** .

### <a name="mutable-specification"></a>변경 가능한 사양

일반적으로 람다의 함수 호출 연산자는 값 단위로 const 이지만 키워드를 사용 하면 **`mutable`** 이를 취소할 수 없습니다. 변경할 수 있는 데이터 멤버는 생성 하지 않습니다. 변경 가능한 사양을 사용하면 람다 식의 본문이 값별로 캡처되는 변수를 수정할 수 있습니다. 이 문서의 뒷부분에 나오는 일부 예제에서는를 사용 하는 방법을 보여 줍니다 **`mutable`** .

### <a name="exception-specification"></a>예외 사양

예외 사양을 사용 하 여 **`noexcept`** 람다 식이 예외를 throw 하지 않음을 나타낼 수 있습니다. 일반적인 함수와 마찬가지로, 람다 식이 예외 사양을 선언 하 고 람다 본문에서 다음과 같이 예외를 throw 하는 경우 Microsoft c + + 컴파일러는 경고 [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) 를 생성 합니다 **`noexcept`** .

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

자세한 내용은 [예외 사양 (throw)](../cpp/exception-specifications-throw-cpp.md)을 참조 하세요.

### <a name="return-type"></a>반환 형식

람다 식의 반환 형식은 자동으로 추론됩니다. [`auto`](../cpp/auto-cpp.md) *후행 반환 형식을* 지정 하지 않으면 키워드를 사용할 필요가 없습니다. *후행 반환 형식은* 일반 메서드 또는 함수의 반환 형식 부분과 유사 합니다. 그러나 반환 형식은 매개 변수 목록 다음에와 야 합니다. 반환 형식 앞에 후행 반환 형식 키워드를 포함 해야 합니다 **`->`** .

람다 본문에 return 문이 하나만 포함되거나 식이 값을 반환하지 않으면 람다 식의 반환 형식 부분을 생략할 수 있습니다. 람다 본문에 단일 return 문이 포함되어 있으면 컴파일러는 반환 식의 형식에서 반환 형식을 추론합니다. 그렇지 않으면 컴파일러는 반환 형식을로 추론 합니다 **`void`** . 이 원칙을 설명하는 다음 예제 코드 조각을 참조하십시오.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

람다 식은 다른 람다 식을 반환 값으로 생성할 수 있습니다. 자세한 내용은 [람다 식의 예](../cpp/examples-of-lambda-expressions.md)에 있는 "고차 람다 식"을 참조 하세요.

### <a name="lambda-body"></a>람다 본문

람다 식의 람다 본문 (표준 구문의 *복합 문* )에는 일반 메서드 또는 함수 본문에 포함 될 수 있는 모든 항목이 포함 될 수 있습니다. 일반 함수와 람다 식 모두의 본문은 다음과 같은 종류의 변수에 액세스할 수 있습니다.

- 앞의 설명대로 바깥쪽 범위에서 캡처된 변수

- 매개 변수

- 로컬로 선언된 변수

- 클래스 데이터 멤버 (클래스 내부에서 선언 되 고 **`this`** 캡처되는 경우)

- 정적 스토리지 기간이 있는 모든 변수(예: 전역 변수)

다음 예제에는 `n` 변수를 값별로 명시적으로 캡처하고 `m` 변수를 참조별로 암시적으로 캡처하는 람다 식이 포함되어 있습니다.

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

`n` 변수는 값별로 캡처되므로 람다 식을 호출한 후 해당 값이 `0`으로 유지됩니다. **`mutable`** 사양은 `n` 람다 내에서 수정할 수 있습니다.

람다 식은 자동 스토리지 기간이 있는 변수만 캡처할 수 있지만 람다 식의 본문에서는 정적 스토리지 기간이 있는 변수를 사용할 수 있습니다. 다음 예제는 `generate` 함수 및 람다 식을 사용하여 `vector` 개체의 각 요소에 값을 할당합니다. 람다 식은 정적 변수를 수정하여 다음 요소의 값을 생성합니다.

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

자세한 내용은 [generate](../standard-library/algorithm-functions.md#generate)를 참조 하세요.

다음 코드 예제에서는 이전 예제의 함수를 사용 하 고 c + + 표준 라이브러리 알고리즘을 사용 하는 람다 식의 예제를 추가 합니다 `generate_n` . 이 람다 식은 `vector` 개체의 요소를 이전의 두 요소의 합에 할당합니다. **`mutable`** 람다 식의 본문이 외부 변수 `x` 및 `y` (람다 식이 값별로 캡처)의 복사본을 수정할 수 있도록 키워드가 사용 됩니다. 람다 식이 원래 변수 `x` 및 `y`를 값별로 캡처하기 때문에 람다가 실행된 후에도 값이 `1`로 유지됩니다.

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

자세한 내용은 [generate_n](../standard-library/algorithm-functions.md#generate_n)를 참조 하세요.

## <a name="constexpr-lambda-expressions"></a>`constexpr` 람다 식

**Visual Studio 2017 버전 15.3 이상** (에서 사용 가능 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ): 람다 식은 **`constexpr`** 상수 식 내에서 허용 되는 각 데이터 멤버의 초기화가 허용 되는 경우 상수 식에 사용 되거나 사용 될 수 있습니다.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

람다는 **`constexpr`** 결과가 함수의 요구 사항을 충족 하는 경우 암시적입니다 **`constexpr`** .

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

람다가 암시적 또는 명시적 이면 **`constexpr`** 함수 포인터로의 변환은 함수를 생성 합니다 **`constexpr`** .

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Microsoft 전용

람다는 **`ref class`** ,, **`ref struct`** **`value class`** 또는와 같은 CLR (공용 언어 런타임) 관리 되는 엔터티에서 지원 되지 **`value struct`** 않습니다.

등의 Microsoft 전용 한정자를 사용 하는 경우 [`__declspec`](../cpp/declspec.md) 바로 뒤에 람다 식에 삽입할 수 있습니다 `parameter-declaration-clause` . 예를 들면 다음과 같습니다.

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

한정자가 람다에서 지원 되는지 여부를 확인 하려면 설명서의 [Microsoft 전용 한정자](../cpp/microsoft-specific-modifiers.md) 섹션에서이에 대 한 문서를 참조 하세요.

Visual Studio는 c + + 11 표준 람다 기능 외에도 임의의 호출 규칙을 사용 하는 함수 포인터로 변환 가능한 상태 비저장 람다를 지원 합니다.

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C + + 표준 라이브러리의 함수 개체](../standard-library/function-objects-in-the-stl.md)<br/>
[함수 호출](../cpp/function-call-cpp.md)<br/>
[`for_each`](../standard-library/algorithm-functions.md#for_each)
