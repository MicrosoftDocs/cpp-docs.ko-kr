---
description: '자세한 정보: 매개 변수'
title: 매개 변수
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipsis (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: b68cd5934e597e486b00f2772e913f627e584ecb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256824"
---
# <a name="parameters"></a>매개 변수

인수는 함수 호출을 통해 함수에 전달되는 값의 이름입니다. 매개 변수는 함수가 수신할 수 있는 값입니다. 함수 프로토타입에서 함수 이름 뒤의 괄호에는 함수의 전체 매개 변수 및 해당 형식 목록이 포함됩니다. 매개 변수 선언은 형식, 크기 및 매개 변수에 저장된 값의 식별자를 지정합니다.

## <a name="syntax"></a>구문

*`function-definition`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declaration-specifiers`* <sub>opt</sub> *`attribute-seq`* <sub>opt</sub> *`declarator`* *`declaration-list`* <sub>opt</sub> *`compound-statement`*

/\* *`attribute-seq`* 는 Microsoft 전용 \*/

*`declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`pointer`* <sub>opt</sub> *`direct-declarator`*

*`direct-declarator`* : /\* 함수 선언자 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`direct-declarator`*  **`(`**  *`parameter-type-list`*  **`)`**  /\* 새 스타일 선언자 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`direct-declarator`*  **`(`**  *`identifier-list`* <sub>opt</sub> **`)`**  /\* 사용되지 않는 스타일 선언자 \*/

*`parameter-type-list`* : /\* 매개 변수 목록 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* **`, ...`**

*`parameter-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-declaration`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* **`,`**  *`parameter-declaration`*

*`parameter-declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`* *`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declaration-specifiers`* *`abstract-declarator`* <sub>opt</sub>

*`parameter-type-list`* 는 쉼표로 구분된 매개 변수 선언 시퀀스입니다. 매개 변수 목록에 있는 각 매개 변수 형식은 다음과 같습니다.

> **`register`** <sub>opt</sub> *`type-specifier`* *`declarator`* <sub>opt</sub>

**`auto`** 특성을 사용하여 선언된 함수 매개 변수는 오류를 생성합니다. 매개 변수 식별자는 함수 본문에 사용되어 함수에 전달된 값을 참조합니다. 프로토타입에서 매개 변수 이름을 지정할 수 있지만 선언 끝에서 이름이 범위를 벗어납니다. 이는 함수 정의에서 같거나 다른 방식으로 매개 변수 이름을 지정할 수 있음을 의미합니다. 함수 본문의 가장 바깥쪽 블록에서 이 식별자를 다시 정의할 수 있지만 매개 변수 목록이 바깥쪽 블록인 것처럼 내부의 중첩 블록에서 다시 정의할 수 있습니다.

이 예제에 표시된 대로 *`parameter-type-list`* 의 각 식별자는 적합한 형식 식별자 뒤에 와야 합니다.

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

매개 변수 목록에 매개 변수가 하나 이상 있을 경우 목록 끝에 쉼표 1개와 마침표 3개가 차례로 올 수 있습니다( **`, ...`** ). "줄임표 표기법"이라고 하는 이 생성은 가변적인 개수의 인수가 함수에 사용됨을 나타냅니다. (자세한 내용은 [가변적인 개수의 인수를 사용하여 호출](../c-language/calls-with-a-variable-number-of-arguments.md)을 참조하세요.) 그러나 함수 호출에는 마지막 쉼표 앞에 있는 매개 변수만큼 인수가 있어야 합니다.

함수에 인수가 전달되지 않을 경우 **`void`** 키워드에 의해 매개 변수 목록이 바뀝니다. 이때 **`void`** 사용은 형식 지정자로 사용하는 것과는 다릅니다.

줄임표 표기법 사용을 포함하여 매개 변수의 순서와 형식은 모든 함수 선언(있을 경우) 및 함수 정의에서 동일해야 합니다. 일반적인 산술 변환 후 인수 형식이 해당 매개 변수의 형식과 할당 호환이 되어야 합니다. 산술 변환에 대한 자세한 내용은 [일반적인 산술 변환](../c-language/usual-arithmetic-conversions.md)을 참조하세요. 줄임표 뒤의 인수는 확인되지 않습니다. 매개 변수는 기본, 구조체, 공용 구조체, 포인터 또는 배열 형식을 가질 수 있습니다.

필요할 경우 컴파일러가 매개 변수 및 인수마다 독립적으로 일반적인 산술 변환을 수행합니다. 변환 후 매개 변수는 **`int`** 보다 짧아지지 않으며 매개 변수 형식이 명시적으로 프로토타입에 **`float`** 로 지정되지 않을 경우 매개 변수가 **`float`** 형식을 가질 수 없습니다. 이는 예를 들어 매개 변수를 **`char`** 로 선언하면 **`int`** 로 선언하는 것과 같은 효과를 가진다는 의미입니다.

## <a name="see-also"></a>참조

[C 함수 정의](../c-language/c-function-definitions.md)
