---
description: '자세한 정보: C 관계 및 같음 연산자'
title: C 관계 및 같음 연산자
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 6ed6b4de51fdc9eda929cdaf4cf87d238bf7dcc6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214258"
---
# <a name="c-relational-and-equality-operators"></a>C 관계 및 같음 연산자

이진 관계형 연산자와 같음 연산자는 첫 번째 피연산자와 두 번째 피연산자를 비교하여 지정된 관계의 유효성을 테스트합니다. 테스트된 관계가 true이면 관계식 결과는 1이고, 테스트된 관계가 false이면 결과는 0입니다. 결과의 형식은 **`int`** 입니다.

**구문**

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;=** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>=** *shift-expression*

*equality-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **==** *relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **!=** *relational-expression*

관계형 연산자와 같음 연산자는 다음 관계를 테스트합니다.

|연산자|테스트되는 관계|
|--------------|-------------------------|
|**&lt;**|첫 번째 피연산자가 두 번째 피연산자보다 작음|
|**>**|첫 번째 피연산자가 두 번째 피연산자보다 큼|
|**&lt;=**|첫 번째 피연산자가 두 번째 피연산자보다 작거나 같음|
|**>=**|첫 번째 피연산자가 두 번째 피연산자보다 크거나 같음|
|**==**|첫 번째 피연산자가 두 번째 피연산자와 같음|
|**!=**|첫 번째 피연산자가 두 번째 피연산자와 같지 않음|

위 목록에 있는 처음 네 연산자의 우선 순위가 같음 연산자(`==` 및 `!=`)보다 높습니다. [C++ 연산자의 우선 순위와 결합성](../c-language/precedence-and-order-of-evaluation.md) 표에서 우선 순위 정보를 참조하세요.

피연산자는 정수 계열, 부동 또는 포인터 형식일 수 있습니다. 피연산자의 형식은 서로 다를 수 있습니다. 관계형 연산자는 정수 계열 및 부동 형식 피연산자에 대한 일반적인 산술 변환을 수행합니다. 또한 관계형 연산자와 같음 연산자에서 다음과 같은 피연산자 형식의 조합을 사용할 수 있습니다.

- 모든 관계형 연산자나 같음 연산자의 피연산자는 둘 다 동일한 형식에 대한 포인터일 수 있습니다. 같음(`==`) 및 같지 않음(`!=`) 연산자의 경우 비교의 결과는 두 개의 포인터가 동일한 메모리 위치를 가리키는지 여부를 나타냅니다. 다른 관계형 연산자( **\<**, **>** , **\<**=, and **>** =)의 경우 비교의 결과는 가리킨 개체에 대한 두 메모리 주소의 상대적 위치를 나타냅니다. 관계형 연산자는 오프셋만 비교합니다.

   포인터 비교는 같은 개체의 부분에 대해서만 정의됩니다. 포인터가 배열의 멤버를 참조하는 경우 비교는 해당 아래 첨자의 비교와 동일합니다. 첫 번째 배열 요소의 주소는 마지막 요소의 주소보다 "작습니다." 구조체의 경우 나중에 선언된 구조체 멤버에 대한 포인터는 구조체에서 이전에 선언된 멤버에 대한 포인터보다 "큽니다." 같은 공용 구조체의 멤버에 대한 포인터는 동일합니다.

- 포인터 값을 상수 값 0과 비교하여 같은지(`==`) 또는 같지 않은지(`!=`)를 확인할 수 있습니다. 값이 0인 포인터를 "null" 포인터라고 합니다. 즉, 이러한 포인터는 유효한 메모리 위치를 가리키지 않습니다.

- 같음 연산자는 관계형 연산자와 동일한 규칙을 따르지만 추가 가능성을 허용합니다. 포인터를 값이 0인 상수 정수 식과 비교하거나 **`void`** 에 대한 포인터와 비교할 수 있습니다. 두 포인터가 모두 null 포인터인 경우는 동일한 것으로 비교됩니다. 같음 연산자는 세그먼트와 오프셋을 모두 비교합니다.

## <a name="examples"></a>예

아래 예제에서는 관계형 연산자와 같음 연산자를 보여 줍니다.

```C
int x = 0, y = 0;
if ( x < y )
```

`x` 및 `y`가 같기 때문에 이 예제의 식은 0 값을 생성합니다.

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

이 예제에서는 `array`의 각 요소를 null 문자 상수로 설정합니다.

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

이러한 문은 `col` 태그를 사용하여 `color`이라는 열거형 변수를 선언합니다. 언제든지 변수는 정수 값 0, 1 또는 2를 포함할 수 있으며, 이러한 값은 열거형 집합 `color`의 요소 중 하나인 빨간색, 흰색 또는 녹색을 각각 나타냅니다. **`if`** 문이 실행될 때 `col`에 0이 포함되어 있는 경우 **`if`** 에 종속된 모든 문이 실행됩니다.

## <a name="see-also"></a>참조

[관계 연산자: \<, >, \<=, and >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[같음 연산자: == 및 !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
