---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4146'
title: 컴파일러 경고 (수준 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: 85aebd34ed83ef14e306f7512689ccdfba713eec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326506"
---
# <a name="compiler-warning-level-2-c4146"></a>컴파일러 경고 (수준 2) C4146

부호 없는 형식에 단항 빼기 연산자가 적용 되었습니다. 결과는 계속 서명 되지 않습니다.

부호 없는 형식에는 음수가 아닌 값만 포함 될 수 있으므로 단항 빼기 (부정)는 부호 없는 형식에 적용 될 때 일반적으로 의미가 없습니다. 피연산자와 결과가 모두 음수가 아닙니다.

실질적으로 프로그래머는 최소 정수 값 (-2147483648)을 표현 하려고 할 때 발생 합니다. 식이 다음 두 단계로 처리 되기 때문에이 값을-2147483648로 쓸 수 없습니다.

1. 숫자 2147483648가 계산 됩니다. 2147483647의 최대 정수 값 보다 크므로 2147483648의 형식은 [int](../../c-language/integer-types.md)가 아닙니다 **`unsigned int`** .

1. 단항 마이너스는 값에 적용 되며, 부호 없는 결과는 2147483648이 되기도 합니다.

결과의 부호 없는 형식으로 인해 예기치 않은 동작이 발생할 수 있습니다. 비교에 결과를 사용 하는 경우 예를 들어 다른 피연산자가 인 경우 부호 없는 비교가 사용 될 수 있습니다 **`int`** . 이는 아래 예제 프로그램이 한 줄만 인쇄 하는 이유를 설명 합니다.

가 false 이기 때문에 예상 되는 두 번째 줄은 `1 is greater than the most negative int` 인쇄 되지 않습니다 `((unsigned int)1) > 2147483648` .

형식이 인 C4146의 INT_MIN를 사용 하 여이를 방지할 수 **`signed int`** 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4146를 생성 합니다.

```cpp
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```
