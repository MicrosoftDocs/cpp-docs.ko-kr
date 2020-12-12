---
description: '자세한 정보: 단항 더하기 및 부정 연산자: + 및-'
title: '단항 더하기 및 부정 연산자: + 및 -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: 64478ccfa9191e5704c1e3c896b17bc0986dc0e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145771"
---
# <a name="unary-plus-and-negation-operators--and--"></a>단항 더하기 및 부정 연산자: + 및 -

## <a name="syntax"></a>Syntax

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ 연산자

단항 더하기 연산자 ()의 결과는 **+** 피연산자의 값입니다. 단항 더하기 연산자의 피연산자는 산술 형식이어야 합니다.

정수 계열 확장은 정수 계열 피연산자를 대상으로 수행됩니다. 결과 형식은 피연산자가 승격될 형식입니다. 따라서 식은 형식이 며,이 경우 `+ch` `ch` **`char`** **`int`** 값은 수정 되지 않습니다. 승격을 수행 하는 방법에 대 한 자세한 내용은 [표준 변환](standard-conversions.md) 을 참조 하세요.

## <a name="--operator"></a>- 연산자

단항 부정 연산자 ( **-** )는 해당 피연산자의 음수를 생성 합니다. 단항 부정 연산자의 피연산자는 산술 형식이어야 합니다.

정수 계열 확장은 정수 계열 피연산자에서 수행되며, 결과 형식은 피연산자가 확장되는 형식입니다. 승격을 수행 하는 방법에 대 한 자세한 내용은 [표준 변환](standard-conversions.md) 을 참조 하세요.

**Microsoft 전용**

부호 없는 수량의 단항 부정은 2^n에서 피연산자의 값을 빼서 수행됩니다. 여기서 n은 지정된 부호 없는 형식의 개체에 있는 비트 수입니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
