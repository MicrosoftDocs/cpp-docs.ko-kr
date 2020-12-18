---
description: '자세한 정보: 배열 선언'
title: 배열 선언
ms.date: 11/04/2016
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
ms.openlocfilehash: 2ab44c1121fde7371591967a9f5860442674abda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280003"
---
# <a name="array-declarations"></a>배열 선언

"배열 선언"은 배열의 이름을 지정하고 배열 요소의 형식을 지정합니다. 배열 선언은 배열의 요소 수를 정의할 수도 있습니다. 배열 형식이 있는 변수는 배열 요소의 형식에 대한 포인터로 간주됩니다.

## <a name="syntax"></a>구문

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *init-declarator-list*<sub>opt</sub> **;**

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* 함수 선언자 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**

*constant-expression* 은 선택 사항이기 때문에 구문에는 두 가지 형태가 있습니다.

- 첫 번째 형태는 배열 변수를 정의합니다. 대괄호 안의 *constant-expression* 인수는 배열의 요소 수를 지정합니다. *constant-expression*(있는 경우)에는 정수 계열 형식과 0보다 큰 값이 있어야 합니다. 각 요소에는 *type-specifier* 로 지정된 형식이 있으며, 형식은 **`void`** 를 제외한 모든 형식이 될 수 있습니다. 배열 요소는 함수 형식일 수 없습니다.

- 두 번째 형태는 다른 곳에 정의된 변수를 선언합니다. 이 형태에서는 대괄호로 묶은 *constant-expression* 인수가 생략되지만 대괄호는 생략되지 않습니다. 배열을 이전에 초기화했거나, 배열을 매개 변수로 선언했거나, 프로그램의 다른 곳에서 명시적으로 정의된 배열에 대한 참조로 배열을 선언한 경우에만 이 형태를 사용할 수 있습니다.

두 형태 모두에서 *direct-declarator* 는 변수의 이름을 지정하고 변수의 형식을 수정할 수 있습니다. *direct-declarator* 뒤에 오는 대괄호( **[ ]** )는 선언자를 배열 형식으로 수정합니다.

형식 한정자는 배열 형식의 개체에 대한 선언에 나타날 수 있지만 한정자는 배열 자체가 아니라 요소에 적용됩니다.

이 형태에서는 배열 선언자 뒤에 대괄호로 묶은 상수 식 목록을 추가하여 배열의 배열("다차원" 배열)을 선언할 수 있습니다.

> *type-specifier* *declarator* **[** *constant-expression* **]** **[** *constant-expression* **]** ...

대괄호로 묶은 각 *constant-expression* 은 지정된 차원의 요소 수를 정의합니다. 2차원 배열에는 대괄호로 묶은 식이 2개 있고 3차원 배열에는 3개가 있는 식입니다. 배열을 초기화했거나, 배열을 매개 변수로 선언했거나, 프로그램의 다른 곳에서 명시적으로 정의된 배열에 대한 참조로 배열을 선언한 경우 첫 번째 상수 식을 생략할 수 있습니다.

[더 복잡한 선언자 해석](../c-language/interpreting-more-complex-declarators.md)에 설명된 것처럼 복잡한 선언자를 사용하여 포인터 배열을 다양한 개체 형식으로 정의할 수 있습니다.

배열은 행별로 저장됩니다. 예를 들어, 다음 배열은 각각 두 행과 세 열로 구성됩니다.

```C
char A[2][3];
```

첫 번째 행의 세 열이 먼저 저장된 다음 두 번째 행의 세 열이 저장됩니다. 이에 따라 마지막 첨자가 가장 빠르게 변화합니다.

배열의 개별 요소를 참조하려면 [후위 연산자](../c-language/postfix-operators.md)에 설명된 것처럼 첨자 식을 사용하세요.

## <a name="examples"></a>예

다음 예제에서는 배열 선언을 보여 줍니다.

```C
float matrix[10][15];
```

`matrix`라고 하는 2차원 배열에는 150개의 요소가 있으며, 각각의 요소는 **`float`** 형식입니다.

```C
struct {
    float x, y;
} complex[100];
```

이것은 구조체 배열의 선언입니다. 이 배열에는 요소가 100개 있습니다. 각 요소는 두 멤버가 포함된 구조체입니다.

```C
extern char *name[];
```

이 문은 **`char`** 에 대한 포인터 배열의 형식과 이름을 선언합니다. `name`의 실제 정의는 다른 곳에서 발생합니다.

**Microsoft 전용**

배열의 최대 크기를 보유하는 데 필요한 정수의 형식은 **size_t** 의 크기입니다. 헤더 파일 STDDEF.H에 정의된 **size_t** 는 0x00000000~0x7CFFFFFF 범위의 **`unsigned int`** 입니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[선언자 및 변수 선언](../c-language/declarators-and-variable-declarations.md)
