---
description: '자세한 정보: 관계형 연산자: &lt; , &gt; , &lt; = 및 &gt;='
title: '관계형 연산자: &lt; , &gt; , &lt; = 및 &gt;='
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: dee784c5d93610b27a01ba4ecc36638b84a66885
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252417"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>관계형 연산자: &lt; , &gt; , &lt; = 및 &gt;=

## <a name="syntax"></a>구문

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>설명

이항 관계형 연산자는 다음과 같은 관계를 확인합니다.

- 보다 작음 ( **\<** )

- 보다 큼 ( **>** )

- 작거나 같음 ( **\<=** )

- 크거나 같음 ( **>=** )

관계형 연산자는 왼쪽에서 오른쪽으로 결합됩니다. 관계형 연산자의 두 피연산자는 산술 또는 포인터 형식이어야 하며, 형식의 값을 생성 **`bool`** 합니다. **`false`** 식의 관계가 false 이면 반환 되는 값은 (0)이 고, 그렇지 않으면 반환 되는 값은 **`true`** (1)입니다.

## <a name="example"></a>예제

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

스트림 삽입 연산자 ( **<<** )가 관계형 연산자 보다 우선 순위가 높기 때문에 앞의 예제에 있는 식은 괄호로 묶어야 합니다. 따라서 괄호가 없는 첫 번째 식은 다음과 같이 평가됩니다.

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

[표준 변환](standard-conversions.md) 에서 다루는 일반적인 산술 변환은 산술 형식의 피연산자에 적용 됩니다.

## <a name="comparing-pointers"></a>포인터 비교

형식이 같은 개체의 포인터 2개를 비교할 때 프로그램의 주소 공간에서 가리키는 개체 위치에 따라 결과가 결정됩니다. 또한 포인터는 0 또는 형식의 포인터로 계산 되는 상수 식과 비교할 수 있습니다 `void *` . 형식의 포인터에 대 한 포인터 비교가 수행 되 면 `void *` 다른 포인터는 암시적으로 형식으로 변환 됩니다 `void *` . 그런 다음 비교가 수행됩니다.

다음과 같은 경우에만 형식이 다른 두 포인터를 비교할 수 있습니다.

- 한 형식이 다른 형식에서 파생된 클래스 형식입니다.

- 하나 이상의 포인터가 형식으로 명시적으로 변환 (캐스트) 됩니다 `void *` . 다른 포인터는 `void *` 변환에 대 한 형식으로 암시적으로 변환 됩니다.

형식이 같은 두 포인터가 같은 개체를 가리킬 경우 동일하다고 간주합니다. 개체의 비정적 멤버에 대한 두 포인터를 비교할 경우 다음 규칙이 적용됩니다.

- 클래스 형식이이 아니고 **`union`** 두 멤버가, 또는와 같은 *액세스 지정자* 로 구분 되지 않는 경우 **`public`** 마지막으로 선언 된 **`protected`** **`private`** 멤버에 대 한 포인터는 이전에 선언 된 멤버에 대 한 포인터 보다 큰 비교를 합니다.

- 두 멤버가 *액세스 지정자* 로 분리 된 경우 결과가 정의 되지 않습니다.

- 클래스 형식이 이면 **`union`** 의 다른 데이터 멤버에 대 한 포인터와 **`union`** 비교 합니다.

포인터 2개가 배열이 같은 요소를 가리키거나 배열의 끝을 벗어난 요소를 가리킬 경우 첨자가 높은 개체의 포인터가 더 높다고 간주합니다. 포인터가 같은 배열의 개체를 참조하거나 배열의 끝을 벗어난 위치를 참조할 경우에만 포인터 비교가 유효합니다.

## <a name="see-also"></a>참고 항목

[이항 연산자가 있는 식](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 관계 및 같음 연산자](../c-language/c-relational-and-equality-operators.md)
