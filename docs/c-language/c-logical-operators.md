---
description: '자세한 정보: C 논리 연산자'
title: C 논리 연산자
ms.date: 06/14/2018
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
ms.openlocfilehash: 58527e4702abce6d05f7f8e6d5aed2d7c17eca94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300309"
---
# <a name="c-logical-operators"></a>C 논리 연산자

논리 연산자는 논리 AND( **&&** ) 및 논리 OR( **||** ) 연산자를 수행합니다.

## <a name="syntax"></a>구문

*logical-AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*  **&&**  *inclusive-OR-expression*

*logical-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*

## <a name="remarks"></a>설명

논리 연산자는 일반적인 산술 변환을 수행하지 않습니다. 대신 각 피연산자가 0과 같은지를 평가합니다. 논리 연산의 결과는 0 또는 1입니다. 결과 형식은 **`int`** 입니다.

C 논리 연산자는 아래에 설명되어 있습니다.

|연산자|설명|
|--------------|-----------------|
|**&&**|논리 AND 연산자는 두 피연산자 모두 0이 아니면 값 1을 생성합니다. 피연산자 중 하나가 0이면 결과는 0입니다. 논리 AND 연산의 첫 번째 피연산자가 0이면 두 번째 피연산자는 평가되지 않습니다.|
|**&#124;&#124;**|논리 OR 연산자는 피연산자에 대해 포함적 OR 연산을 수행합니다. 두 피연산자 모두 값이 0이면 결과는 0입니다. 피연산자 중 하나가 0이 아니면 결과는 1입니다. 논리 OR 연산의 첫 번째 피연산자 값이 0이 아니면 두 번째 피연산자는 평가되지 않습니다.|

논리 AND 및 논리 OR 식의 피연산자는 왼쪽에서 오른쪽으로 계산됩니다. 첫 번째 피연산자의 값이 작업의 결과를 결정하는 데 충분한 경우 두 번째 피연산자는 평가되지 않습니다. 이것을 "단락(short-circuit) 계산"이라고 합니다. 첫 번째 피연산자 다음에 시퀀스 위치가 있습니다. 자세한 내용은 [시퀀스 위치](../c-language/c-sequence-points.md)를 참조하세요.

## <a name="examples"></a>예

다음 예제에서는 논리 연산자를 보여 줍니다.

```C
int w, x, y, z;

if ( x < y && y < z )
    printf( "x is less than z\n" );
```

이 예제에서는 **printf** 함수는 `x`가 `y`보다 작고 `y`가 `z`보다 작은 경우 메시지를 출력하도록 호출됩니다. `x`가 `y`보다 크면 두 번째 피연산자(`y < z`)는 평가되지 않고 아무 것도 출력되지 않습니다. 두 번째 피연산자에서 다른 이유로 요구되는 파생 작업이 발생하는 경우 이로 인해 문제가 발생할 수 있습니다.

```C
printf( "%d" , (x == w || x == y || x == z) );
```

이 예제에서 `x`가 `w`, `y` 또는 `z`와 같을 경우 **printf** 함수에 대한 두 번째 인수는 true로 계산되고 값 1이 출력됩니다. 그렇지 않으면 false로 계산되고 값 0이 출력됩니다. 조건 중 하나가 true로 확인되면 계산이 중지됩니다.

## <a name="see-also"></a>참조

- [논리적 AND 연산자: &&](../cpp/logical-and-operator-amp-amp.md)
- [논리 OR 연산자: &#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)
