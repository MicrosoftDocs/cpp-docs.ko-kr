---
title: if...else 문 (c + +)
description: Else를 사용 하는 경우 이니셜라이저를 사용 하 고 if-constexpr 문은 조건부 분기를 제어 합니다.
ms.date: 10/02/2020
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 20d828bf00a79687fe0a9fffbeb1a9cc56fae08c
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765298"
---
# <a name="if-else-statement-c"></a>if...else 문 (c + +)

If else 문은 조건부 분기를 제어 합니다. 의 문은가 *`if-branch`* *`condition`* 0이 아닌 값 (또는)으로 계산 되는 경우에만 실행 됩니다 **`true`** . 의 값 *`condition`* 이 0이 아닌 경우 다음 문이 실행 되 고, 선택적 뒤에 오는 문이 **`else`** 생략 됩니다. 그렇지 않으면 다음 문이 생략 되 고가 있는 경우 뒤에 오는 **`else`** 문이 **`else`** 실행 됩니다.

*`condition`* 0이 아닌 값으로 계산 되는 식은 다음과 같습니다.

- **`true`**
- null이 아닌 포인터
- 0이 아닌 산술 값 또는
- 산술, 부울 또는 포인터 형식으로의 명확한 변환을 정의 하는 클래스 형식입니다. 변환에 대 한 자세한 내용은 [표준 변환](../cpp/standard-conversions.md)을 참조 하세요.

## <a name="syntax"></a>구문

*`init-statement`*:\
&emsp; *`expression-statement`*\
&emsp; *`simple-declaration`*

*`condition`*:\
&emsp; *`expression`*\
&emsp;*`attribute-specifier-seq`* <sub>*opt*</sub> *`decl-specifier-seq`* opt *`declarator`**`brace-or-equal-initializer`*

*`statement`*:\
&emsp; *`expression-statement`*\
&emsp; *`compound-statement`*

*`expression-statement`*:\
&emsp;*`expression`* <sub>*opt*</sub>**`;`**

*`compound-statement`*:\
&emsp;**`{`** *`statement-seq`* <sub>*opt*</sub>**`}`**

*`statement-seq`*:\
&emsp; *`statement`*\
&emsp; *`statement-seq`* *`statement`*

*`if-branch`*:\
&emsp; *`statement`*

*`else-branch`*:\
&emsp; *`statement`*

*`selection-statement`*:\
&emsp;**`if`** **`constexpr`** <sub>*opt*</sub><sup>17</sup> **`(`** *`init-statement`* <sub>*opt*</sub><sup>17</sup> 17 *`condition`* **`)`***`if-branch`*\
&emsp;**`if`** **`constexpr`** <sub>*opt*</sub><sup>17</sup> **`(`** *`init-statement`* <sub>*opt*</sub><sup>17</sup> 17 *`condition`* **`)`** *`if-branch`* **`else`***`else-branch`*

<sup>17</sup> 이 선택적 요소는 c + + 17부터 사용할 수 있습니다.

## <a name="if-else-statements"></a>if else 문

**`if`** 구조체를 제외한 모든 값을 가질 수 있는 모든 형식의 문에 *`condition`* 는 모든 부작용을 포함 하 여가 계산 됩니다. **`if`** 을 실행 하거나, 또는를 포함 하지 않는 경우 문에서 프로그램의 다음 문으로 제어가 전달 *`if-branch`* *`else-branch`* [`break`](../cpp/break-statement-cpp.md) [`continue`](../cpp/continue-statement-cpp.md) [`goto`](../cpp/goto-statement-cpp.md) 됩니다.

**`else`** 문의 절은 `if...else` **`if`** 해당 문이 없는 동일한 범위에서 가장 가까운 이전 문과 연결 되어 **`else`** 있습니다.

### <a name="example"></a>예제: 

이 샘플 코드에서는를 **`if`** 사용 하거나 사용 하지 않고 사용 중인 몇 가지 문을 보여 줍니다 **`else`** .

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

    // no else statement
    if (x == 10)
    {
        x = 0;
    }

    C* c;
    init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```

## <a name="if-statement-with-an-initializer"></a><a name="if_with_init"></a> 이니셜라이저가 포함 된 if 문

C + + 17부터 **`if`** 문에는 *`init-statement`* 명명 된 변수를 선언 하 고 초기화 하는 식이 포함 될 수도 있습니다. If 문의 범위 내 에서만 변수가 필요한 경우에는이 형식의 if 문을 사용 합니다. **Microsoft 전용**:이 양식은 Visual Studio 2017 버전 15.3부터 사용할 수 있으며 최소한 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션이 필요 합니다.

### <a name="example"></a>예제: 

```cpp
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>

using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }

    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }
}
```

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr"> constexpr 문

C + + 17부터 **`if constexpr`** 함수 템플릿의 문을 사용 하 여 여러 함수 오버 로드를 사용 하지 않고도 컴파일 시간 분기 결정을 내릴 수 있습니다. **Microsoft 전용**:이 양식은 Visual Studio 2017 버전 15.3부터 사용할 수 있으며 최소한 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션이 필요 합니다.

### <a name="example"></a>예제: 

이 예제에서는 매개 변수 압축 풀기를 처리 하는 단일 함수를 작성 하는 방법을 보여 줍니다. 매개 변수가 없는 오버 로드는 필요 하지 않습니다.

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
    {
        f(r...);
    }
    else
    {
        g(r...);
    }
}
```

## <a name="see-also"></a>참조

[선택 문](../cpp/selection-statements-cpp.md)\
[어](../cpp/keywords-cpp.md)\
[`switch` Statement (C++)](../cpp/switch-statement-cpp.md)
