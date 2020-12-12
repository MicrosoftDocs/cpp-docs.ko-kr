---
description: '자세한 정보: 단항 연산자가 있는 식'
title: 단항 연산자가 있는 식
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 6714727d0a4b2c386c37550151df21062534376e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186508"
---
# <a name="expressions-with-unary-operators"></a>단항 연산자가 있는 식

단항 연산자는 하나의 식에서 하나의 피연산자에 대해서만 작동합니다. 단항 연산자의 종류는 다음과 같습니다.

- [간접 참조 연산자 (*)](../cpp/indirection-operator-star.md)

- [주소 연산자 (&)](../cpp/address-of-operator-amp.md)

- [단항 더하기 연산자 (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [단항 부정 연산자 (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [논리 부정 연산자 (!)](../cpp/logical-negation-operator-exclpt.md)

- [1의 보수 연산자 (~)](../cpp/one-s-complement-operator-tilde.md)

- [후위 증가 연산자(++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [전위 감소 연산자 (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [캐스트 연산자 ()](../cpp/cast-operator-parens.md)

- [`sizeof` 연산자](../cpp/sizeof-operator.md)

- [`__uuidof` 연산자](../cpp/uuidof-operator.md)

- [`alignof` 연산자](../cpp/alignof-operator.md)

- [`new` 연산자](../cpp/new-operator-cpp.md)

- [`delete` 연산자](../cpp/delete-operator-cpp.md)

이러한 연산자는 오른쪽에서 왼쪽으로 결합됩니다. 단항 식은 일반적으로 후위 식 또는 주 식 앞에 오는 구문을 포함합니다.

다음은 단항 식의 가능한 형식입니다.

- *postfix-expression*

- `++` *unary-expression*

- `--` *unary-expression*

- *단항 연산자* *캐스트 식*

- **`sizeof`***단항 식*

- `sizeof(`*유형-이름*`)`

- `decltype(`*식*`)`

- *할당 식*

- *할당 취소 식*

*후 위 식은* *단항 식* 으로 간주 되며, 기본 식은 *후 위 식* 으로 간주 되기 때문에 모든 기본 식은 *단항 식* 으로 간주 됩니다. 자세한 내용은 [후 위 식](../cpp/postfix-expressions.md) 및 [기본 식](../cpp/primary-expressions.md)을 참조 하세요.

*단항 연산자* 는 다음 기호 중 하나 이상으로 구성 됩니다.`* & + - ! ~`

*캐스트 식은* 형식을 변경 하는 선택적 캐스트를 사용 하는 단항 식입니다. 자세한 내용은 [캐스트 연산자: ()](../cpp/cast-operator-parens.md)를 참조 하세요.

*식은* 어떤 식일 수도 있습니다. 자세한 내용은 [식](../cpp/expressions-cpp.md)을 참조 하세요.

*할당 식은* 연산자를 참조 합니다 **`new`** . *할당 취소 식은* 연산자를 참조 합니다 **`delete`** . 자세한 내용은 이 항목의 앞부분에 나오는 링크를 참조하십시오.

## <a name="see-also"></a>참고 항목

[식 형식](../cpp/types-of-expressions.md)
