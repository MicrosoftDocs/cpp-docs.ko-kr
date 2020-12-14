---
description: '자세한 정보: 쉼표 연산자:,'
title: '쉼표 연산자: ,'
ms.date: 11/04/2016
f1_keywords:
- '%2C'
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
ms.openlocfilehash: 1429e2ce444e0f253bffca795f36f4e6194e0395
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274777"
---
# <a name="comma-operator-"></a>쉼표 연산자: ,

하나의 문이 예상되는 곳에서 두 문을 그룹화할 수 있도록 합니다.

## <a name="syntax"></a>구문

```
expression , expression
```

## <a name="remarks"></a>설명

쉼표 연산자는 왼쪽에서 오른쪽으로 결합됩니다. 두 식은 쉼표로 구분되며 왼쪽에서 오른쪽으로 계산됩니다. 오른쪽 피연산자는 항상 왼쪽 피연산자가 실행되고, 모든 파생 작용이 완료된 후에 실행됩니다.

쉼표는 함수 인수 목록과 같은 일부 컨텍스트에서 구분 기호로 사용될 수 있습니다. 쉼표를 구분 기호로 사용하는 경우와 연산자로 사용하는 경우는 완전히 다르기 때문에 둘을 혼동하지 않도록 주의해야 합니다.

`e1, e2` 식을 참조하십시오. 식의 유형 및 값은 *e2* 의 유형 및 값입니다. *e1* 평가 결과가 삭제 됩니다. 결과는 오른쪽 피연산자가 l-value인 경우 l-value입니다.

쉼표가 일반적으로 구분 기호로 사용되는 경우(예: 함수에 대한 실제 인수 또는 집합체 이니셜라이저), 쉼표 연산자와 피연산자는 괄호로 묶어야 합니다. 예를 들어:

```cpp
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

위 `func_one`에 대한 함수 호출에서 쉼표로 구분된 세 인수, `x`, `y + 2`, `z`가 전달됩니다. `func_two`에 대한 함수 호출에서 괄호는 컴파일러가 첫 번째 쉼표를 순차적 계산 연산자로 해석하도록 합니다. 이 함수 호출은 두 인수를 `func_two`에 전달합니다. 첫 번째 인수는 `(x--, y + 2)` 식의 값과 형식을 가진 순차적 계산 연산 `y + 2`의 결과이며, 두 번째 인수는 `z`입니다.

## <a name="example"></a>예제

```cpp
// cpp_comma_operator.cpp
#include <stdio.h>
int main () {
   int i = 10, b = 20, c= 30;
   i = b, c;
   printf("%i\n", i);

   i = (b, c);
   printf("%i\n", i);
}
```

```Output
20
30
```

## <a name="see-also"></a>참고 항목

[이항 연산자가 있는 식](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[순차적 계산 연산자](../c-language/sequential-evaluation-operator.md)
