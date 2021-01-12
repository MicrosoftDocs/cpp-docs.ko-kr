---
description: '자세히 알아보기: `auto` (c + +)'
title: auto(C++)
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 061ddac33af4b8e1587b2ab1035d9f96ba18b108
ms.sourcegitcommit: 14d6ae0d527d05d153e26463d4cd5ada0f43e864
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98104754"
---
# <a name="auto-c"></a>`auto`(C++)

초기화 식에서 선언된 변수의 형식을 추론합니다.

> [!NOTE]
> C + + 표준에서는이 키워드의 원래 의미와 수정 된 의미를 정의 합니다. Visual Studio 2010 이전에는 **`auto`** 키워드에서 *자동* 저장소 클래스의 변수, 즉 로컬 수명을 가진 변수를 선언 합니다. Visual Studio 2010부터 **`auto`** 키워드는 해당 형식이 선언의 초기화 식에서 추론 되는 변수를 선언 합니다. [ `/Zc:auto`&#91; &#93;](../build/reference/zc-auto-deduce-variable-type.md) 컴파일러 옵션은 키워드의 의미를 제어 합니다 **`auto`** .

## <a name="syntax"></a>구문

> **`auto`***선언 자* *이니셜라이저***`;`**

> **`[](auto`***param1* **`, auto`** *param2***`) {};`**

## <a name="remarks"></a>설명

**`auto`** 키워드는 선언 된 변수 또는 람다 식 매개 변수의 초기화 식을 사용 하 여 해당 형식을 추론 하도록 컴파일러에 지시 합니다.

대부분의 경우에는 다음과 **`auto`** 같은 이점을 제공 하므로 대부분의 경우 키워드를 사용 하는 것이 좋습니다.

- **견고성:** 식의 형식이 변경 된 경우 (함수 반환 형식이 변경 되는 경우 포함)에만 작동 합니다.

- **성능:** 변환이 발생 하지 않을 것으로 보장 됩니다.

- **유용성:** 형식 이름 철자 문제 및 오타가 걱정 하지 않아도 됩니다.

- **효율성:** 코딩을 보다 효율적으로 수행할 수 있습니다.

을 사용 하지 않을 수 있는 변환 사례는 **`auto`** 다음과 같습니다.

- 특정 형식을 원하는 경우 다른 항목은 사용할 수 없습니다.

- 식 템플릿 도우미 형식 (예:) `(valarray+valarray)`

키워드를 사용 하려면 **`auto`** 형식 대신이 키워드를 사용 하 여 변수를 선언 하 고 초기화 식을 지정 합니다. 또한, **`auto`** **`const`** **`volatile`** , 포인터 ( **`*`** ), 참조 ( **`&`** ) 및 rvalue 참조 ( **`&&`** )와 같은 지정자 및 선언 자를 사용 하 여 키워드를 수정할 수 있습니다. 컴파일러는 초기화 식을 계산하고 해당 정보를 사용하여 변수의 형식을 추론합니다.

**`auto`** 초기화 식은 다음과 같은 여러 가지 형식을 사용할 수 있습니다.

- 과 같은 범용 초기화 구문 `auto a { 42 };` 입니다.
- 와 같은 할당 구문 `auto b = 0;` 입니다.
- 위의 두 가지 형태 (예:)를 결합 하는 범용 할당 구문 `auto c = { 3.14156 };` 입니다.
- 직접 초기화 또는 생성자 스타일 구문 (예:) `auto d( 1.41421f );` .

자세한 내용은이 문서의 뒷부분에 나오는 [이니셜라이저](../cpp/initializers.md) 및 코드 예제를 참조 하세요.

**`auto`** 를 사용 하 여 범위 기반 문에 있는 루프 매개 변수를 선언 하는 경우 **`for`** 와 같이 다른 초기화 구문을 사용 `for (auto& i : iterable) do_action(i);` 합니다. 자세한 내용은 [범위 기반 `for` 문 (c + +)](../cpp/range-based-for-statement-cpp.md)을 참조 하세요.

**`auto`** 키워드는 형식에 대 한 자리 표시자 이지만 자체 형식이 아닙니다. 따라서 키워드는 **`auto`** [`sizeof`](../cpp/sizeof-operator.md) 및 (c + +/cli의 경우)와 같은 캐스트 또는 연산자에서 사용할 수 없습니다 [`typeid`](../extensions/typeid-cpp-component-extensions.md) .

## <a name="usefulness"></a>유용성

**`auto`** 키워드는 복잡 한 형식의 변수를 선언 하는 간단한 방법입니다. 예를 들어를 사용 **`auto`** 하 여 초기화 식에 템플릿, 함수에 대 한 포인터 또는 멤버에 대 한 포인터를 포함 하는 변수를 선언할 수 있습니다.

를 사용 하 여 **`auto`** 람다 식에 대 한 변수를 선언 하 고 초기화할 수도 있습니다. 람다 식의 형식은 컴파일러에만 알려져 있기 때문에 직접 변수 유형을 선언할 수 없습니다. 자세한 내용은 [람다 식의 예](../cpp/examples-of-lambda-expressions.md)를 참조 하세요.

## <a name="trailing-return-types"></a>후행 반환 형식

**`auto`** 형식 지정자와 함께를 사용 하 여 **`decltype`** 템플릿 라이브러리를 작성할 수 있습니다. **`auto`** 및 **`decltype`** 를 사용 하 여 반환 형식이 해당 템플릿 인수의 형식에 종속 되는 템플릿 함수를 선언 합니다. 또는 및를 **`auto`** 사용 **`decltype`** 하 여 다른 함수에 대 한 호출을 래핑하는 템플릿 함수를 선언한 다음 다른 함수의 반환 형식을 반환 합니다. 자세한 내용은 [`decltype`](../cpp/decltype-cpp.md)를 참조하세요.

## <a name="references-and-cv-qualifiers"></a>참조 및 cv 한정자

를 사용 하면 **`auto`** 참조, **`const`** 한정자 및 한정자가 삭제 **`volatile`** 됩니다. 다음 예제를 참조하세요.

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}
```

앞의 예제에서 myAuto는 **`int`** **`int`** 참조가 아니라 `11 11` `11 12` 입니다. 따라서 참조 한정자가에 의해 삭제 되지 않은 경우와는 다른 경우와 같이 출력 됩니다 **`auto`** .

## <a name="type-deduction-with-braced-initializers-c14"></a>중괄호로 묶인 이니셜라이저를 사용 하 여 형식 추론 (c + + 14)

다음 코드 예제에서는 **`auto`** 중괄호를 사용 하 여 변수를 초기화 하는 방법을 보여 줍니다. B와 C 간의 차이와 A와 E 사이의 차이를 확인 합니다.

```cpp
#include <initializer_list>

int main()
{
    // std::initializer_list<int>
    auto A = { 1, 2 };

    // std::initializer_list<int>
    auto B = { 3 };

    // int
    auto C{ 4 };

    // C3535: cannot deduce type for 'auto' from initializer list'
    auto D = { 5, 6.7 };

    // C3518 in a direct-list-initialization context the type for 'auto'
    // can only be deduced from a single initializer expression
    auto E{ 8, 9 };

    return 0;
}
```

## <a name="restrictions-and-error-messages"></a>제한 사항 및 오류 메시지

다음 표에서는 키워드 사용에 대 **`auto`** 한 제한 사항과 컴파일러가 내보내는 해당 진단 오류 메시지를 나열 합니다.

|오류 번호|Description|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**`auto`** 키워드는 다른 형식 지정자와 함께 사용할 수 없습니다.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|키워드를 사용 하 여 선언 된 기호에는 **`auto`** 이니셜라이저가 있어야 합니다.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|키워드를 잘못 사용 **`auto`** 하 여 형식을 선언 했습니다. 예를 들어 메서드 반환 형식 또는 배열을 선언했습니다.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|매개 변수 또는 템플릿 인수는 키워드를 사용 하 여 선언할 수 없습니다 **`auto`** .|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|메서드 또는 템플릿 매개 변수는 키워드를 사용 하 여 선언할 수 없습니다 **`auto`** .|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|초기화되기 전에 기호를 사용할 수 없습니다. 실제로, 이는 변수를 사용하여 자신을 초기화할 수 없음을 의미합니다.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|키워드를 사용 하 여 선언 된 형식으로 캐스팅할 수 없습니다 **`auto`** .|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|키워드를 사용 하 여 선언 된 선언 자 목록의 모든 기호는 **`auto`** 동일한 형식으로 확인 되어야 합니다. 자세한 내용은 [선언 및 정의](declarations-and-definitions-cpp.md)를 참조 하세요.|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md) 및 [typeid](../extensions/typeid-cpp-component-extensions.md) 연산자는 키워드를 사용 하 여 선언 된 기호에 적용할 수 없습니다 **`auto`** .|

## <a name="examples"></a>예

이러한 코드 조각은 키워드를 사용할 수 있는 몇 가지 방법을 보여 줍니다 **`auto`** .

다음 선언은 동일합니다. 첫 번째 문에서는 변수가 `j` 형식으로 선언 됩니다 **`int`** . 두 번째 문에서는 `k` **`int`** 초기화 식 (0)이 정수 이므로 변수가 형식으로 추론 됩니다.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

다음 선언은 동일하지만 두 번째 선언이 첫 번째 선언보다 간단합니다. 키워드를 사용 하는 가장 중요 한 이유 중 하나는 **`auto`** 단순성입니다.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

다음 코드 조각에서는 변수 형식과 `iter` `elem` **`for`** 및 범위 루프가 시작 될 때를 선언 합니다 **`for`** .

```cpp
// cl /EHsc /nologo /W4
#include <deque>
using namespace std;

int main()
{
    deque<double> dqDoubleData(10, 0.1);

    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)
    { /* ... */ }

    // prefer range-for loops with the following information in mind
    // (this applies to any range-for with auto, not just deque)

    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples
    { /* ... */ }

    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE
    { /* ... */ }

    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE
    { /* ... */ }
}
```

다음 코드 조각에서는 **`new`** 연산자 및 포인터 선언을 사용 하 여 포인터를 선언 합니다.

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

다음 코드 조각은 각 선언문에서 여러 기호를 선언합니다. 각 명령문의 모든 기호는 동일한 형식으로 확인됩니다.

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

다음 코드 조각은 조건부 연산자(`?:`)를 사용하여 변수 `x`를 정수 값을 200 값을 갖는 정수로 선언합니다.

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

다음 코드 조각에서는 변수를 형식으로 초기화 하 `x` **`int`** 고, 변수 `y` 를 형식에 대 한 참조로 초기화 하 **`const int`** 고, 변수를 `fp` 형식을 반환 하는 함수에 **`int`** 대 한 포인터로 초기화 합니다.

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>참조

[C++ 키워드](../cpp/keywords-cpp.md)<br/>
[`/Zc:auto` (변수 형식 추론)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[`sizeof` 연산자](../cpp/sizeof-operator.md)<br/>
[`typeid`](../extensions/typeid-cpp-component-extensions.md)<br/>
[`operator new`](new-operator-cpp.md)<br/>
[선언 및 정의](declarations-and-definitions-cpp.md)<br/>
[람다 식의 예](../cpp/examples-of-lambda-expressions.md)<br/>
[이니셜라이저](../cpp/initializers.md)<br/>
[`decltype`](../cpp/decltype-cpp.md)
