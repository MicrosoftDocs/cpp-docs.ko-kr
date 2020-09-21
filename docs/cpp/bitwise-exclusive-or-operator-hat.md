---
title: '배타적 비트 OR 연산자: ^'
description: C + + 표준 언어 배타적 OR 연산자 구문 및를 사용 합니다.
ms.date: 09/21/2020
f1_keywords:
- xor_cpp
- ^
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 4823c245ffca7032347e37c0c25c2963407733a7
ms.sourcegitcommit: f656092eebbcb148ca4d3b7a6a8508eff8f7e85f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90836630"
---
# <a name="bitwise-exclusive-or-operator-"></a>배타적 비트 OR 연산자: ^

## <a name="syntax"></a>구문

> *식* **`^`** *식*

## <a name="remarks"></a>설명

배타적 비트 OR 연산자 ( **`^`** )는 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교 합니다. 피연산자 중 하나의 비트가 0이 고 다른 피연산자의 비트가 1 이면 해당 결과 비트는 1로 설정 됩니다. 그렇지 않으면 해당 결과 비트는 0으로 설정됩니다.

연산자에 대 한 두 피연산자는 정수 계열 형식 이어야 합니다. [표준 변환](standard-conversions.md) 에서 다루는 일반적인 산술 변환은 피연산자에 적용 됩니다.

**`^`** C + +/cli 및 c + +/cx에서 문자의 대체 사용에 대 한 자세한 내용은 [개체 연산자에 대 한 핸들 (^) (c + +/Cli 및 c + +/cx)을](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)참조 하세요.

## <a name="operator-keyword-for-"></a>^의 Operator 키워드

C + +는 **`xor`** 의 대체 철자를 지정 합니다 **`^`** . C에서 대체 철자는 헤더에 매크로로 제공 됩니다 \<iso646.h> . C + +에서 대체 철자는 키워드입니다. \<iso646.h> 또는이에 해당 하는 c + +는 사용 \<ciso646> 되지 않습니다. Microsoft c + +에서 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 또는 [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 컴파일러 옵션은 대체 철자를 사용 하도록 설정 하는 데 필요 합니다.

## <a name="example"></a>예제

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>참고 항목

[C + + 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
