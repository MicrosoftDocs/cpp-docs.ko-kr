---
description: '자세한 정보: 구조체 및 공용 구조체 멤버'
title: 구조체 및 공용 구조체 멤버
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
ms.openlocfilehash: f20074157b28763d1db05487043ba0e1576e2d4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137204"
---
# <a name="structure-and-union-members"></a>구조체 및 공용 구조체 멤버

"멤버 선택 식"은 구조체와 공용 구조체의 멤버를 참조합니다. 이러한 식은 선택한 멤버의 값과 형식을 갖게 됩니다.

> *postfix-expression* **.** *identifier*\
> *postfix-expression* **->** *identifier*

다음 목록에서는 멤버 선택 식의 두 가지 형태에 대해 설명합니다.

1. 첫 번째 형태에서 *postfix-expression* 은 **`struct`** 또는 **`union`** 형식의 값을 나타내며, *identifier* 는 지정된 구조체 또는 공용 구조체의 멤버 이름을 지정합니다. 연산값은 *identifier* 의 값이며 *postfix-expression* 이 l-value인 경우 l-value입니다. 자세한 내용은 [L-Value 및 R-Value 식](../c-language/l-value-and-r-value-expressions.md)을 참조하세요.

1. 두 번째 형태에서 *postfix-expression* 은 구조체 또는 공용 구조체에 대한 포인터를 나타내며, *identifier* 는 지정된 구조체 또는 공용 구조체의 멤버 이름을 지정합니다. 값은 *identifier* 의 값이며 l-value입니다.

두 가지 형태의 멤버 선택 식은 비슷한 효과가 있습니다.

마침표( **.** ) 앞의 식이 포인터 값에 적용된 간접 참조 연산자(<strong>\*</strong>)로 구성된 경우 멤버 선택 연산자( **->** )를 포함하는 식은 마침표를 사용하는 식의 약식 버전입니다. 따라서

```cpp
expression->identifier
```

위의 식은 아래의 식과 동일합니다.

```cpp
(*expression).identifier
```

여기서 *expression* 은 포인터 값입니다.

## <a name="examples"></a>예

다음 예제에서는 이 구조체 선언을 참조합니다. 이러한 예제에서 사용하는 간접 참조 연산자(<strong>\*</strong>)에 대한 자세한 내용은 [간접 참조 및 주소 연산자](../c-language/indirection-and-address-of-operators.md)를 참조하세요.

```
struct pair
{
    int a;
    int b;
    struct pair *sp;
} item, list[10];
```

`item` 구조체에 대한 멤버 선택 식은 다음과 같습니다.

```
item.sp = &item;
```

위의 예제에서 `item` 구조체의 주소는 구조체의 `sp` 멤버에 할당됩니다. 이는 `item`이 자신에 대한 포인터를 포함하고 있음을 의미합니다.

```
(item.sp)->a = 24;
```

이 예제에서는 포인터 식 `item.sp`를 멤버 선택 연산자( **->** )와 함께 사용하여 `a` 멤버에 값을 할당합니다.

```
list[8].b = 12;
```

이 문은 구조체 배열에서 개별 구조체 멤버를 선택하는 방법을 보여 줍니다.

## <a name="see-also"></a>참조

[멤버 액세스 연산자: . 및 ->](../cpp/member-access-operators-dot-and.md)
