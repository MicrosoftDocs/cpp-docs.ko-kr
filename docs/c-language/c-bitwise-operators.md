---
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
ms.openlocfilehash: 50be8ae38f21d0a9f46c180abf179e1358b707cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168775"
---
# <a name="c-bitwise-operators"></a>C 비트 연산자

비트 연산자는 비트 AND( **&** ), 배타적 비트 OR( **^** ) 및 포괄적 비트 OR( **&#124;** ) 연산을 수행합니다.

## <a name="syntax"></a>구문

*AND-expression*: &nbsp;&nbsp;*같음* 식 &nbsp;&nbsp;*및-식* **&** *같음 식*

*배타적 or 식*: &nbsp;&nbsp;*및-expression* &nbsp;&nbsp;*배타적 or 식* **^** *및-식*

*포함*또는 식: &nbsp;&nbsp;*배타적* or 식 &nbsp;&nbsp;*포함* &#124; 식 또는 식 *배타적 or 식*

비트 연산자의 피연산자는 정수 형식을 가져야 하지만 해당 형식은 다를 수 있습니다. 이러한 연산자는 일반적인 산술 변환을 수행하며, 결과의 형식은 변환 후 피연산자의 형식입니다.

C 비트 연산자는 아래에 설명되어 있습니다.

|연산자|Description|
|--------------|-----------------|
|**&**|비트 AND 연산자는 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다. 두 비트가 모두 1이면 해당 결과 비트가 1로 설정되고, 그렇지 않으면 해당 결과 비트가 0으로 설정됩니다.|
|**^**|포괄적 비트 OR 연산자는 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다. 두 비트 중 하나가 0이고 다른 비트가 1이면 해당 결과 비트는 1로 설정됩니다. 그렇지 않으면 해당 결과 비트가 0으로 설정됩니다.|
|**&#124;**|배타적 비트 OR 연산자는 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다. 두 비트 중 하나가 1이면 해당 결과 비트가 1로 설정되고, 그렇지 않으면 해당 결과 비트가 0으로 설정됩니다.|

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

## <a name="see-also"></a>참고 항목

[비트 AND 연산자: &](../cpp/bitwise-and-operator-amp.md)<br/>
[배타적 비트 OR 연산자: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[포괄적 비트 OR 연산자: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
