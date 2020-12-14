---
description: '다음에 대 한 자세한 정보: 후 위 증가 및 감소 연산자: + + 및--'
title: '후위 증가 및 감소 연산자: ++ 및 --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: 56f955fc4c8b5508c4b2c4e03c37e89f9d2d8bc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258514"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>후위 증가 및 감소 연산자: ++ 및 --

## <a name="syntax"></a>구문

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>설명

C++는 전위/후위 증가 및 감소 연산자를 제공합니다. 이 단원에서는 후위 증가 및 감소 연산자에 대해서만 설명합니다. 자세한 내용은 [전위 증가 및 감소 연산자](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)를 참조 하세요. 후 위 표기법의 차이는 후 위 표기법에서 연산자가 후 *위 식* 뒤에 표시 되는 반면 접두사 표기법에서는 연산자가 식 앞에 표시 된다는 것입니다 *.* 다음 예제에서는 후위 증가 연산자를 보여 줍니다.

```cpp
i++;
```

후 위 증가 연산자 ()를 적용 하면 **++** 피연산자의 값이 적절 한 형식의 단위 하나 만큼 증가 합니다. 마찬가지로 후 위 감소 연산자 ()를 적용 하면 **--** 피연산자의 값이 적절 한 형식의 단위 하나 만큼 감소 합니다.

후 위 증가 또는 감소 식은 각 연산자를 적용 하기 *전에* 식의 값으로 계산 된다는 점에 유의 해야 합니다. 증가 또는 감소 연산은 피연산자가 계산 된 *후* 에 발생 합니다. 이 문제는 후위 증가나 감소 연산이 더 큰 수식의 컨텍스트에서 진행할 경우에만 발생합니다.

후위 연산자가 함수 인수에 적용될 때 해당 인수의 값은 함수에 전달된 후에만 증가하거나 감소됩니다.  자세한 내용은 C++ 표준의 1.9.17 단원을 참조하십시오.

후 위 증가 연산자를 형식의 개체 배열에 대 한 포인터에 적용 하면 **`long`** 실제로 4 개가 포인터의 내부 표현에 추가 됩니다. 이 동작을 수행 하면 이전에 배열의 *n* 번째 요소를 참조 하는 포인터가 (*n*+ 1) 번째 요소를 참조 합니다.

후 위 증가 및 후 위 감소 연산자는 **`const`** 산술 또는 포인터 형식의 l-value를 수정할 수 있어야 합니다. 결과의 형식은 *후 위 식* 의 값과 동일 하지만 더 이상 l-value가 아닙니다.

**Visual Studio 2017 버전 15.3 이상** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능): 후 위 증가 또는 감소 연산자의 피연산자가 형식이 아닐 수 있습니다 **`bool`** .

다음 코드에서는 후위 증가 연산자에 대해 설명합니다.

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

후위 증가 및 감소 연산은 열거형 형식에서 지원되지 않습니다.

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>참고 항목

[후 위 식](../cpp/postfix-expressions.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 후 위 증가 및 감소 연산자](../c-language/c-postfix-increment-and-decrement-operators.md)
