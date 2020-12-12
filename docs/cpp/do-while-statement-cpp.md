---
description: '자세히 알아보기: do-while 문 (c + +)'
title: do-while 문(C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: fed7dc3300651dd35326c1eb28e3078538db1301
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195491"
---
# <a name="do-while-statement-c"></a>do-while 문(C++)

지정 된 종료 조건 ( *식*)이 0으로 평가 될 때까지 *문을* 반복 해 서 실행 합니다.

## <a name="syntax"></a>구문

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>설명

종료 상태의 테스트는 각 루프를 실행 한 후에 수행 됩니다. 따라서 **do while** 루프는 종료 식의 값에 따라 한 번 이상 실행 됩니다. **do-while** 문은 문 본문 내에서 [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) 또는 [return](../cpp/return-statement-cpp.md) 문이 실행되는 경우에도 종료될 수 있습니다.

*expression* 은 산술 형식이나 포인터 형식이어야 합니다. 다음과 같이 실행됩니다.

1. 문 본문이 실행됩니다.

1. 다음으로, *expression* 이 평가됩니다. *expression* 이 false인 경우 **do-while** 문이 종료되고 프로그램의 다음 문으로 제어가 전달됩니다. *expression* 이 true(0이 아님)인 경우에는 프로세스가 1단계부터 반복됩니다.

## <a name="example"></a>예제

다음 샘플에서는 **do while** 문을 보여 줍니다.

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>참고 항목

[반복 문](../cpp/iteration-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[while 문(C++)](../cpp/while-statement-cpp.md)<br/>
[for 문 (c + +)](../cpp/for-statement-cpp.md)<br/>
[범위 기반 for 문(C++)](../cpp/range-based-for-statement-cpp.md)
