---
title: C++ 상수 식
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 97059066adadc3a7897cbd2c4c747e2a673e7201
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576425"
---
# <a name="c-constant-expressions"></a>C++ 상수 식

*상수* 값은 변경되지 않는 값입니다. C++에서는 개체를 수정할 수 없음을 나타내는 의도를 표현하고 해당 의도를 적용할 수 있는 두 가지 키워드를 제공합니다.

C++에서는 다음 선언에 대해 상수 식(상수로 계산되는 식)이 필요합니다.

- 배열 범위

- Case 문의 선택기

- 비트 필드 길이 사양

- 열거형 이니셜라이저

상수 식에는 다음 피연산자만 사용할 수 있습니다.

- 리터럴

- 열거형 상수

- 상수 식을 사용하여 초기화되며 const로 선언된 값

- **sizeof** 식

비정수 상수는 명시적이거나 암시적으로 상수 식에 사용할 수 있는 정수 계열 형식으로 변환해야 합니다. 따라서 다음 코드를 사용할 수 있습니다.

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

상수 식에서는 정수 계열 형식에 대한 명시적 변환이 적합합니다. **sizeof** 연산자의 피연산자로 사용되는 경우를 제외하고 다른 모든 형식과 파생 형식은 적합하지 않습니다.

쉼표 연산자와 할당 연산자를 상수 식에 사용할 수 없습니다.

## <a name="see-also"></a>참고 

[식의 형식](../cpp/types-of-expressions.md)
