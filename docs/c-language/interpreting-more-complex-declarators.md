---
description: '자세한 정보: 더 복잡한 선언자 해석'
title: 더 복잡한 선언자 해석
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 82fc9b3cbd1bbf36191b5bfae7d5c3695f84f964
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137516"
---
# <a name="interpreting-more-complex-declarators"></a>더 복잡한 선언자 해석

선언자를 괄호로 묶어 "복합 선언자"의 특정 해석을 지정할 수 있습니다. 복합 선언자는 둘 이상의 배열, 포인터 또는 함수 한정자로 한정된 식별자입니다. 배열, 포인터 및 함수 한정자의 다양한 조합을 단일 식별자에 적용할 수 있습니다. 일반적으로 **`typedef`** 를 사용하여 선언을 단순화할 수 있습니다. [Typedef 선언](../c-language/typedef-declarations.md)을 참조하세요.

복합 선언자를 해석할 때 대괄호와 괄호(즉, 식별자 오른쪽의 한정자)는 별표(즉, 식별자 왼쪽의 한정자)보다 우선합니다. 대괄호와 괄호는 우선 순위가 동일하고 왼쪽에서 오른쪽으로 연결됩니다. 선언자가 완전히 해석된 후 형식 지정자가 마지막 단계로 적용됩니다. 괄호를 사용하여 기본 연결 순서를 재정의하고 특정 해석을 적용할 수 있습니다. 그러나 식별자 이름 자체는 괄호로 묶지 마십시오. 괄호로 묶으면 매개 변수 목록으로 잘못 해석될 수 있습니다.

복합 선언자를 해석하는 간단한 방법은 다음 4단계를 사용하여 "내부에서 외부로" 읽는 것입니다.

1. 식별자에서 시작하고 대괄호 또는 괄호(있는 경우)의 오른쪽을 바로 확인합니다.

1. 이러한 대괄호 또는 괄호를 해석한 다음 별표의 왼쪽을 확인합니다.

1. 어떤 단계에서든 오른쪽 괄호를 발견하면 뒤로 돌아가서 괄호 안의 모든 항목에 규칙 1 및 2를 적용합니다.

1. 형식 지정자를 적용합니다.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

이 예제에서 단계는 순서대로 번호가 매겨지고 다음과 같이 해석될 수 있습니다.

1. `var` 식별자는 다음으로 선언됩니다.

1. 다음에 대한 포인터

1. 다음을 반환하는 함수

1. 다음에 대한 포인터

1. 다음과 같은 10개 요소의 배열

1. 다음에 대한 포인터

1. **`char`** 값.

## <a name="examples"></a>예

다음 예제에서는 다른 복합 선언을 보여 주고 괄호가 선언의 의미에 미치는 영향을 나타냅니다.

```
int *var[5]; /* Array of pointers to int values */
```

배열 한정자는 포인터 한정자보다 우선 순위가 높으므로 `var`은 배열로 선언됩니다. 포인터 한정자는 배열 요소의 형식에 적용되므로 배열 요소는 **`int`** 값에 대한 포인터입니다.

```
int (*var)[5]; /* Pointer to array of int values */
```

`var`에 대한 이 선언에서 괄호는 배열 한정자보다 포인터 한정자에 보다 높은 우선 순위를 부여하고, `var`은 **`int`** 값이 5개인 배열에 대한 포인터로 선언됩니다.

```
long *var( long, long ); /* Function returning pointer to long */
```

함수 한정자도 포인터 한정자보다 우선 순위가 높기 때문에 `var`에 대한 이 선언은 `var`을 **`long`** 값에 대한 포인터를 반환하는 함수로 선언합니다. 함수는 두 개의 **`long`** 값을 인수로 사용하도록 선언됩니다.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

이 예제는 앞의 예제와 유사합니다. 괄호는 포인터 한정자에 함수 한정자보다 높은 우선 순위를 부여하고, `var`은 **`long`** 값을 반환하는 함수에 대한 포인터로 선언됩니다. 여기에서도 함수는 두 가지 **`long`** 인수를 사용합니다.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

배열의 요소가 함수일 수는 없지만 이 선언은 함수에 대한 포인터 배열을 선언하는 방법을 대신 보여 줍니다. 이 예제에서 `var`은 두 멤버가 포함된 구조체를 반환하는 함수에 대한 포인터 5개의 배열로 선언됩니다. 함수에 대한 인수는 동일한 구조체 형식 `both`를 사용하는 두 구조체로 선언됩니다. `*var[5]` 주위에는 괄호가 필요합니다. 괄호 없이 아래와 같이 함수 배열을 선언하는 것은 잘못된 시도입니다.

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

다음 문은 포인터의 배열을 선언합니다.

```
unsigned int *(* const *name[5][10] ) ( void );
```

`name` 배열에는 다차원 배열로 구성된 50개의 요소가 있습니다. 요소는 상수인 포인터에 대한 포인터입니다. 이 상수 포인터는 매개 변수가 없고 부호 없는 형식에 대한 포인터를 반환하는 함수를 가리킵니다.

다음 예제는 **`double`** 값이 세 개인 배열에 대한 포인터를 반환하는 함수입니다.

```
double ( *var( double (*)[3] ) )[3];
```

이 선언에서 배열을 반환하는 함수가 잘못되었으므로 함수는 배열에 대한 포인터를 반환합니다. 여기서 `var`은 **`double`** 값이 세 개인 배열에 대한 포인터를 반환하는 함수로 선언됩니다. `var` 함수는 인수를 하나 사용합니다. 인수는 반환 값과 마찬가지로 **`double`** 값이 세 개인 배열에 대한 포인터입니다. 인수 형식은 복합 *추상 선언자* 에서 제공됩니다. 인수 형식에서 별표 주위에 괄호가 필요합니다. 괄호가 없으면 인수 형식이 **`double`** 값에 대한 세 포인터의 배열이 됩니다. 추상 선언자에 대한 설명과 예제는 [추상 선언자](../c-language/c-abstract-declarators.md)를 참조하세요.

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

위의 예제와 같이 포인터는 다른 포인터를 가리킬 수 있으며 배열에는 배열이 요소로 포함될 수 있습니다. 여기서 `var`은 요소가 5개인 배열입니다. 각 요소는 멤버가 두 개인 공용 구조체에 대한 포인터에 대한 포인터의 배열(요소가 5개임)입니다.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

이 예제에서는 괄호의 위치에 따라 선언의 의미가 어떻게 바뀌는지를 보여 줍니다. 이 예제에서 `var`은 공용 구조체에 대한 포인터의 배열(요소가 5개임)에 대한 포인터의 배열(요소가 5개임)입니다. **`typedef`** 를 사용하여 복합 선언을 방지하는 방법에 대한 예제를 보려면 [Typedef 선언](../c-language/typedef-declarations.md)을 참조하세요.

## <a name="see-also"></a>참조

[선언 및 형식](../c-language/declarations-and-types.md)
