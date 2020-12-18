---
description: '자세한 정보: 조건식 연산자'
title: 조건식 연산자
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: 4b11b0f3ed132459f4e1608922e111c3b5bf2a98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293315"
---
# <a name="conditional-expression-operator"></a>조건식 연산자

C에는 삼항 연산자인 조건식 연산자가 하나 있습니다( **? :** ).

## <a name="syntax"></a>구문

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR expression*  **?**  *expression*  **:**  *conditional-expression*

*logical-OR-expression* 은 정수 계열, 부동 소수점 또는 포인터 형식이어야 합니다. 식은 0과 같은지 여부의 측면에서 평가됩니다. 시퀀스 위치가 *logical-OR-expression* 뒤에 나옵니다. 피연산자에 대한 평가는 다음과 같이 진행됩니다.

- *logical-OR-expression* 이 0과 같지 않은 경우 *expression* 이 평가됩니다. 식의 평가 결과는 비터미널 *expression* 에서 제공됩니다. 즉, *logical-OR-expression* 이 true인 경우에만 *expression* 이 평가됩니다.

- *logical-OR-expression* 이 0과 같은 경우 *conditional-expression* 이 평가됩니다. 식의 결과는 *conditional-expression* 의 값입니다. 즉, *logical-OR-expression* 이 false인 경우에만 *conditional-expression* 이 평가됩니다.

*expression* 또는 *conditional-expression* 중에서 하나만 평가되고 둘 다 평가되지는 않습니다.

조건부 연산의 결과 형식은 다음과 같이 *expression* 또는 *conditional-expression* 피연산자의 형식에 따라 달라집니다.

- *expression* 또는 *conditional-expression* 이 정수 계열 또는 부동 소수점 형식인 경우(형식이 서로 다를 수 있음) 연산자는 일반적인 산술 변환을 수행합니다. 결과 형식은 변환 후의 피연산자 형식과 동일합니다.

- *expression* 및 *conditional-expression* 이 둘 다 동일한 구조체, 공용 구조체 또는 포인터 형식인 경우 결과의 형식은 동일한 구조체, 공용 구조체 또는 포인터 형식입니다.

- 피연산자가 둘 다 **`void`** 형식인 경우 결과의 형식은 **`void`** 입니다.

- 피연산자 중 하나가 임의의 형식의 개체에 대한 포인터이고 다른 피연산자가 **`void`** 에 대한 포인터인 경우, 개체에 대한 포인터가 **`void`** 에 대한 포인터로 변환되고 결과는 **`void`** 에 대한 포인터입니다.

- *expression* 또는 *conditional-expression* 이 포인터이고 다른 피연산자가 값이 0인 상수 식인 경우 결과의 형식은 포인터 형식입니다.

포인터에 대한 형식 비교에서 포인터가 가리키는 형식의 모든 형식 한정자( **`const`** 또는 **`volatile`** )는 중요하지 않지만 결과 형식은 조건의 두 구성 요소에서 한정자를 상속합니다.

## <a name="examples"></a>예

다음 예제에서는 조건 연산자를 사용하는 방법을 보여 줍니다.

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

이 예제에서는 `i`의 절대값을 `j`에 할당합니다. `i`가 0보다 작으면 `-i`가 `j`에 할당되고, `i`가 0보다 크거나 같으면 `i`가 `j`에 할당됩니다.

```cpp
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

이 예제에서는 `f1` 및 `f2` 함수와 `x` 및 `y` 변수가 선언되었습니다. 프로그램의 뒷부분에서 두 변수의 값이 같으면 `f1` 함수가 호출되고, 그렇지 않으면 `f2`가 호출됩니다.

## <a name="see-also"></a>참조

[조건 연산자: ? :](../cpp/conditional-operator-q.md)
