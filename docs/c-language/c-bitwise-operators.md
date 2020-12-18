---
description: '자세한 정보: C 비트 연산자'
title: C 비트 연산자
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 8cbdb5309d5351f77306007e8acd1675be5e2a35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211585"
---
# <a name="c-bitwise-operators"></a>C 비트 연산자

비트 연산자는 비트 AND( **&** ), 배타적 비트 OR( **^** ) 및 포괄적 비트 OR( **&#124;** ) 연산을 수행합니다.

## <a name="syntax"></a>구문

*AND-expression*: &nbsp;&nbsp;*equality-expression* &nbsp;&nbsp;*AND-expression* **&** *equality-expression*

*exclusive-OR-expression*: &nbsp;&nbsp;*AND-expression* &nbsp;&nbsp;*exclusive-OR-expression* **^** *AND-expression*

*inclusive-OR-expression*: &nbsp;&nbsp;*exclusive-OR-expression* &nbsp;&nbsp;*inclusive-OR-expression* &#124; *exclusive-OR-expression*

비트 연산자의 피연산자는 정수 형식을 가져야 하지만 해당 형식은 다를 수 있습니다. 이러한 연산자는 일반적인 산술 변환을 수행하며, 결과의 형식은 변환 후 피연산자의 형식입니다.

C 비트 연산자는 아래에 설명되어 있습니다.

|연산자|설명|
|--------------|-----------------|
|**&**|비트 AND 연산자는 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다. 양쪽 비트가 모두 1이면 해당 결과 비트는 1로 설정됩니다. 그렇지 않으면 해당 결과 비트는 0으로 설정됩니다.|
|**^**|포괄적 비트 OR 연산자는 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다. 한 비트가 0이고 다른 비트가 1인 경우 해당 결과 비트는 1로 설정됩니다. 그렇지 않으면 해당 결과 비트는 0으로 설정됩니다.|
|**&#124;**|배타적 비트 OR 연산자는 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다. 어느 한쪽 비트가 1이면 해당 결과 비트는 1로 설정됩니다. 그렇지 않으면 해당 결과 비트는 0으로 설정됩니다.|

## <a name="examples"></a>예

이러한 선언은 다음 3가지 예제에서 사용됩니다.

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

이 첫 번째 예제에서 `n`에 할당된 결과는 `i`(16진수 0xAB00)와 같습니다.

```C
n = i | j;

n = i ^ j;
```

두 번째 예제에서 포괄적 비트 OR의 결과 값은 0xABCD(16진수)이지만 세 번째 예제의 배타적 비트 OR은 0xCD(16진수)를 생성합니다.

**Microsoft 전용**

부호 있는 정수에 대한 비트 연산 결과는 ANSI C 표준에 따라 구현이 정의됩니다. Microsoft C 컴파일러의 경우 부호 있는 정수에 대한 비트 연산은 부호 없는 정수에 대한 비트 연산과 동일하게 작동합니다. 예를 들어, `-16 & 99`는 이진 형식으로 다음과 같이 표현될 수 있습니다.

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

비트 AND의 결과는 10진수 96입니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[비트 AND 연산자: &](../cpp/bitwise-and-operator-amp.md)<br/>
[배타적 비트 OR 연산자: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[포괄적 비트 OR 연산자: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
