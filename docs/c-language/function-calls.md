---
description: '자세한 정보: 함수 호출'
title: 함수 호출
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
ms.openlocfilehash: 3949ea88637d9476d6acb0fd4fc4cf43dcfb0fc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221932"
---
# <a name="function-calls"></a>함수 호출

*함수 호출* 은 컨트롤 및 인수(있는 경우)를 함수에 전달하는 다음 형식의 식입니다.

*expression* (*expression-list*<sub>opt</sub>)

여기서 *expression* 은 함수 이름이거나 함수 주소로 계산되며, *expression-list* 는 쉼표로 구분된 식 목록입니다. 두 번째 식의 값은 함수로 전달되는 인수입니다. 함수가 값을 반환하지 않는 경우에는 **`void`** 를 반환하는 함수로 선언합니다.

함수가 호출 전에 선언되었는데 매개 변수와 관련한 정보는 제공되지 않으면 선언되지 않은 인수에 대해서는 일반적인 산술 변환이 진행됩니다.

> [!NOTE]
> 함수 인수 목록의 식은 원하는 순서로 계산할 수 있으므로 다른 인수로부터의 의도하지 않은 결과로 인해 값이 변경될 수 있는 인수의 경우 정의되지 않은 값을 포함합니다. 함수 호출 연산자로 정의되는 시퀀스 위치를 통해 보장되는 사항은, 호출된 함수로 컨트롤이 전달되기 전에 인수 목록의 모든 의도하지 않은 결과가 평가된다는 것뿐입니다. 스택에서 인수가 푸시되는 순서는 별개의 사항입니다. 자세한 내용은 [시퀀스 위치](../c-language/c-sequence-points.md)를 참조하세요.

함수 호출의 요구 사항은 괄호 앞의 식이 함수 주소로 계산되어야 한다는 것뿐입니다. 즉, 함수 포인터 식을 통해 함수를 호출할 수 있습니다.

## <a name="example"></a>예제

이 예제에서는 **`switch`** 문에서 호출되는 함수 호출을 보여 줍니다.

```
int main()
{
    /* Function prototypes */

    long lift( int ), step( int ), drop( int );
    void work( int number, long (*function)(int i) );

    int select, count;
    .
    .
    .
    select = 1;
    switch( select )
    {
        case 1: work( count, lift );
                break;

        case 2: work( count, step );
                break;

        case 3: work( count, drop );
                /* Fall through to next case */
        default:
                break;
    }
}

/* Function definition */

void work( int number, long (*function)(int i) )
{
    int i;
    long j;

    for ( i = j = 0; i < number; i++ )
            j += ( *function )( i );
}
```

이 예제에서는 `main`의 다음 함수 호출이

```
work( count, lift );
```

정수 변수 `count` 및 `lift` 함수의 주소를 `work` 함수로 전달합니다. 함수 식별자가 포인터 식으로 계산되므로 함수 주소는 단순히 함수 식별자를 제공하는 방식으로 전달됩니다. 이러한 방식으로 함수 식별자를 사용하려면 식별자를 사용하기 전에 함수를 선언하거나 정의해야 합니다. 그지 않으면 식별자가 식별되지 않습니다. 이 경우에는 `work`에 대한 프로토타입이 `main` 함수 시작 부분에 제공됩니다.

`work`의 `function` 매개 변수는 **`int`** 인수 하나를 가져와 **`long`** 값을 반환하는 함수에 대한 포인터로 선언됩니다. 매개 변수 이름을 묶는 괄호는 필수 항목입니다. 괄호가 없으면 선언은 **`long`** 값으로 포인터를 반환하는 함수를 지정합니다.

`work` 함수는 다음 함수 호출을 사용하여 **`for`** 루프 내에서 선택한 함수를 호출합니다.

```
( *function )( i );
```

이 경우 단일 인수 `i`가 호출된 함수로 전달됩니다.

## <a name="see-also"></a>참조

[함수](../c-language/functions-c.md)
