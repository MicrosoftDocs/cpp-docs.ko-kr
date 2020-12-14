---
description: '자세한 정보: 전위 증가 및 감소 연산자: + + 및--'
title: '접두사 증가 및 감소 연산자: ++ 및 --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
ms.openlocfilehash: e484dde59a2bb58e7c408ad28242fc0ab4290051
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198644"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>접두사 증가 및 감소 연산자: ++ 및 --

## <a name="syntax"></a>구문

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>설명

전위 증가 연산자 ( **++** )는 피연산자에 하나를 더 합니다 .이 증가 된 값은 식의 결과입니다. 피연산자는 형식이 아닌 l-value 여야 합니다 **`const`** . 결과는 피연산자와 동일한 형식의 l-value입니다.

전위 감소 연산자 ( **--** )는 피연산자가 1 씩 감소 하 고 결과가 감소 하는 값을 제외 하 고 전위 증가 연산자와 유사 합니다.

**Visual Studio 2017 버전 15.3 이상** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능): 증가 또는 감소 연산자의 피연산자가 형식이 아닐 수 있습니다 **`bool`** .

전위 및 후위 증가 및 감소 연산자는 피연산자에 영향을 줍니다. 두 처리자의 주요 차이점은 식의 계산에서 증가 또는 감소가 수행되는 순서입니다. 자세한 내용은 [후 위 증가 및 감소 연산자](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)를 참조 하십시오. 접두사 형식에서 증가 또는 감소는 값이 식 계산에 사용 되기 전에 발생 하므로 식의 값이 피연산자의 값과 다릅니다. 후위 형식에서는 식 계산에서 값이 사용된 후에 증가 또는 감소가 발생하므로 식 값은 피연산자 값과 동일합니다. 예를 들어 다음 프로그램은 "`++i = 6`"을 인쇄합니다.

```cpp
// expre_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   int i = 5;
   cout << "++i = " << ++i << endl;
}
```

정수 계열 또는 부동 형식의 피연산자는 정수 값 1만큼 증가하거나 감소합니다. 결과 형식은 피연산자 형식과 동일합니다. 포인터 형식의 피연산자는 자신이 처리하는 개체의 크기만큼 증가하거나 감소합니다. 증가한 포인터는 다음 개체를 가리키고, 감소한 포인터는 이전 개체를 가리킵니다.

증가 및 감소 연산자에 부작용이 있으므로 [전처리기 매크로](../preprocessor/macros-c-cpp.md) 에서 증가 또는 감소 연산자가 있는 식을 사용 하면 바람직하지 않은 결과가 발생할 수 있습니다. 다음 예제를 고려해 보세요.

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

매크로는 다음과 같이 확장됩니다.

```cpp
k = ((++i)<(j))?(j):(++i);
```

`i`가 `j`보다 크거나 같거나 `j`보다 1만큼 작은 경우 두 번 증가합니다.

> [!NOTE]
> 이곳에서 설명한 것과 같은 부작용을 제거하고 언어를 사용하여 보다 완벽한 형식 검사를 수행할 수 있기 때문에 대부분 매크로보다는 C++ 인라인 함수를 사용하는 것이 좋습니다.

## <a name="see-also"></a>참조

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[전위 증가 및 감소 연산자](../c-language/prefix-increment-and-decrement-operators.md)
