---
description: '자세한 정보: 인수'
title: 인수
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
ms.openlocfilehash: 02c8d7e9f6f4ef09bcfdce11c3bd0d88c21ab141
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280081"
---
# <a name="arguments"></a>인수

함수 호출의 인수는 다음과 같은 형식입니다.

> *expression* **(** *expression-list*<SUB>opt</SUB> **)**  /* 함수 호출 */

함수 호출에서 *식 목록* 은 쉼표로 구분된 식 목록입니다. 두 번째 식의 값은 함수로 전달되는 인수입니다. 함수에서 인수가 사용되지 않으면 *expression-list* 에는 **`void`** 키워드를 포함해야 합니다.

인수는 기본, 구조체, 공용 구조체 또는 포인터 형식의 모든 값일 수 있습니다. 모든 인수는 값으로 전달됩니다. 즉, 인수의 복사본이 해당 매개 변수에 할당됩니다. 함수는 전달된 인수의 실제 메모리 위치를 알 수 없습니다. 함수는 복사본이 원래 파생된 변수에 영향을 주지 않고 해당 복사본을 사용합니다.

배열이나 함수를 인수로 전달할 수는 없지만 포인터를 이러한 항목으로 전달할 수는 있습니다. 함수는 포인터를 통해 참조로 값에 액세스할 수 있습니다. 변수에 대한 포인터에는 변수의 주소가 포함되므로 함수는 이 주소를 사용해 변수의 값에 액세스할 수 있습니다. 배열 및 함수를 인수로 전달할 수는 없지만 포인터 인수를 사용하면 함수가 배열 및 함수에 액세스할 수 있습니다.

인수를 평가하는 순서는 컴파일러 및 최적화 수준에 따라 달라질 수 있습니다. 그러나 함수를 입력하기 전에 인수 및 해당 인수의 의도하지 않은 결과를 완전하게 평가합니다. 이와 같은 파생 작업에 대한 자세한 내용은 [파생 작업](../c-language/side-effects.md)을 참조하세요.

함수 호출의 *식 목록* 을 평가한 다음 해당 함수 호출의 각 인수에 대해 일반적인 산술 변환을 수행합니다. 프로토타입을 사용할 수 있으면 결과 인수 형식을 프로토타입의 해당 매개 변수와 비교합니다. 인수 형식과 매개 변수가 일치하지 않으면 변환이 수행되거나 진단 메시지가 표시됩니다. 매개 변수에 대해서도 일반적인 산술 변환이 진행됩니다.

함수의 프로토타입 또는 정의에 인수의 변수 수가 명시적으로 지정되는 경우가 아니면 *식 목록* 의 식 수는 매개 변수의 수와 일치해야 합니다. 변수의 수가 명시적으로 지정되는 경우에는 컴파일러가 매개 변수 목록에 있는 형식 이름의 수에 해당하는 인수를 확인한 다음 필요한 경우 위에서 설명한 것처럼 변환합니다. 자세한 내용은 [가변적인 개수의 인수를 사용하여 호출](../c-language/calls-with-a-variable-number-of-arguments.md)을 참조하세요.

프로토타입의 매개 변수 목록에 **`void`** 키워드만 포함되어 있으면 컴파일러는 함수 호출의 인수 수와 정의의 매개 변수 수를 0으로 가정합니다. 인수가 발견되면 진단 메시지가 표시됩니다.

## <a name="example"></a>예제

이 예제에서는 포인터를 인수로 사용합니다.

```C
int main()
{
    /* Function prototype */

    void swap( int *num1, int *num2 );
    int x, y;
    .
    .
    .
    swap( &x, &y );  /* Function call */
}

/* Function definition */

void swap( int *num1, int *num2 )
{
    int t;

    t = *num1;
    *num1 = *num2;
    *num2 = t;
}
```

이 예제에서는 `swap` 함수가 각각 `num1` 및 `num2` 식별자로 표시되는 인수 두 개를 포함하도록 `main`에서 선언됩니다. 이 두 식별자는 모두 **`int`** 값에 대한 포인터입니다. 프로토타입 스타일 정의의 `num1` 및 `num2` 매개 변수도 **`int`** 형식 값에 대한 포인터로 선언됩니다.

다음 함수 호출에서

```C
swap( &x, &y )
```

`x`의 주소는 `num1`에 저장되고 `y`의 주소는 `num2`에 저장됩니다. 즉, 같은 위치에 대해 두 개의 이름("별칭")이 있습니다. `*num1`의 `*num2` 및 `swap`에 대한 참조는 사실상 `x`의 `y` 및 `main`에 대한 참조입니다. `swap` 내의 할당은 실제로 `x` 및 `y`의 내용을 교환합니다. 따라서 **`return`** 문은 필요하지 않습니다.

`swap`의 프로토타입에 각 매개 변수에 대한 인수 형식이 포함되므로 컴파일러는 `swap`에 대한 인수에서 형식 검사를 수행합니다. 프로토타입과 정의의 괄호 안에 포함된 식별자는 같을 수도 있고 다를 수도 있습니다. 중요한 것은 인수의 형식이 프로토타입과 정의 둘 다의 매개 변수 목록에 포함된 형식과 일치한다는 점입니다.

## <a name="see-also"></a>참조

[함수 호출](../c-language/function-calls.md)
