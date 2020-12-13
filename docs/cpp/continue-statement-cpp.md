---
description: '자세히 알아보기: continue 문 (c + +)'
title: continue 문 (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6899e5cd249ab5a7a3b786e4b82c9890c08a7183
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344642"
---
# <a name="continue-statement-c"></a>continue 문 (C++)

가장 작은 바깥쪽 [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)또는 [while](../cpp/while-statement-cpp.md) 루프의 제어 식으로 제어를 강제로 전송 합니다.

## <a name="syntax"></a>구문

```
continue;
```

## <a name="remarks"></a>설명

현재 반복에서 나머지 모든 문은 실행되지 않습니다. 루프의 다음 반복은 다음과 같이 결정됩니다.

- 또는 **`do`** 루프에서 **`while`** 또는 문의 제어 식을 다시 계산 하 여 다음 반복이 시작 됩니다 **`do`** **`while`** .

- **`for`** 구문을 사용 하 여 루프에서 `for( <init-expr> ; <cond-expr> ; <loop-expr> )` `<loop-expr>` 절이 실행 됩니다. 그런 다음 `<cond-expr>` 절이 다시 계산되고 해당 결과에 따라 루프가 종료되거나 다른 반복이 발생합니다.

다음 예제에서는 **`continue`** 문을 사용 하 여 코드 섹션을 건너뛰고 루프의 다음 반복을 시작할 수 있는 방법을 보여 줍니다.

## <a name="example"></a>예제

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>참고 항목

[점프 문](../cpp/jump-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
