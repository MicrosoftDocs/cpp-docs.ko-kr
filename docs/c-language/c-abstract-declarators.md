---
description: '자세한 정보: C 추상 선언자'
title: C 추상 선언자
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: 9af51d96ac50222b9148060147812aecdf114b7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211611"
---
# <a name="c-abstract-declarators"></a>C 추상 선언자

추상 선언자는 식별자 없이 하나 이상의 포인터, 배열 또는 함수 한정자로 구성되는 선언자입니다. 선언자에서 포인터 한정자(<strong>\*</strong>)는 항상 식별자 앞에 옵니다. 배열( **[ ]** ) 및 함수( **( )** ) 한정자는 식별자 뒤에 옵니다. 이 사실을 알고 있으면 추상 선언자에서 식별자가 나타날 위치를 확인하고 그에 따라 선언자를 해석할 수 있습니다. 복잡한 선언자에 대한 추가 정보 및 예제는 [더 복잡한 선언자 해석](../c-language/interpreting-more-complex-declarators.md)을 참조하세요. 일반적으로 **`typedef`** 는 선언자를 단순화하는 데 사용할 수 있습니다. [Typedef 선언](../c-language/typedef-declarations.md)을 참조하세요.

추상 선언자는 복잡할 수 있습니다. 복잡한 추상 선언자에 있는 괄호는 선언의 복잡한 선언자에 있는 괄호와 마찬가지로 특정 해석을 지정합니다.

다음 예제에서는 추상 선언자를 보여 줍니다.

```
int *         // The type name for a pointer to type int:

int *[3]      // An array of three pointers to int

int (*) [5]   // A pointer to an array of five int

int *()       // A function with no parameter specification
              // returning a pointer to int

// A pointer to a function taking no arguments and
// returning an int

int (*) ( void )

// An array of an unspecified number of constant pointers to
// functions each with one parameter that has type unsigned int
// and an unspecified number of other parameters returning an int

int (*const []) ( unsigned int, ... )
```

> [!NOTE]
> 빈 괄호 **( )** 집합으로 구성된 추상 선언자는 모호하기 때문에 허용되지 않습니다. 암시적 식별자가 괄호 안에 속하는지(수정되지 않은 형식), 아니면 괄호 앞에 속하는지(함수 형식)는 확인할 수 없습니다.

## <a name="see-also"></a>참조

[선언자 및 변수 선언](../c-language/declarators-and-variable-declarations.md)
