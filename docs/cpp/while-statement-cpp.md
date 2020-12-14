---
description: '자세히 알아보기: while 문 (c + +)'
title: while 문 (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 3001760372410222651366416ac74d0cba59f23b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302831"
---
# <a name="while-statement-c"></a>while 문 (C++)

*식이* 0으로 계산 될 때까지 *문을* 반복 해 서 실행 합니다.

## <a name="syntax"></a>구문

```
while ( expression )
   statement
```

## <a name="remarks"></a>설명

*식* 의 테스트는 루프를 실행할 때마다 발생 합니다. 따라서 루프는 **`while`** 0 번 이상 실행 됩니다. *식은* 정수 계열 형식, 포인터 형식 또는 정수 계열 또는 포인터 형식으로의 명확한 변환이 있는 클래스 형식 이어야 합니다.

**`while`** 문 본문 내에서 [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md)또는 [return](../cpp/return-statement-cpp.md) 이 실행 될 때 루프가 종료 될 수도 있습니다. [Continue](../cpp/continue-statement-cpp.md) 를 사용 하 여 루프를 종료 하지 않고 현재 반복을 종료 **`while`** 합니다. **`continue`** 루프의 다음 반복으로 제어를 전달 **`while`** 합니다.

다음 코드에서는 루프를 사용 하 여 **`while`** 문자열에서 후행 밑줄을 자릅니다.

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

종료 조건은 루프의 위쪽에서 계산 됩니다. 후행 밑줄이 없으면 루프가 실행 되지 않습니다.

## <a name="see-also"></a>참고 항목

[반복 문](../cpp/iteration-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[do-while 문(C++)](../cpp/do-while-statement-cpp.md)<br/>
[for 문 (c + +)](../cpp/for-statement-cpp.md)<br/>
[범위 기반 for 문(C++)](../cpp/range-based-for-statement-cpp.md)
