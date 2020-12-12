---
description: '자세한 정보: Null 문'
title: Null 문
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
ms.openlocfilehash: 1aa488da395cf84ae9ef6d78939f1f1e3019c572
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146174"
---
# <a name="null-statement"></a>Null 문

"Null 문"은 *식이* 누락 된 식 문입니다. 언어의 구문에 문이 필요하지만 식 계산은 필요하지 않은 경우에 이 문이 유용합니다. 이 문은 세미콜론으로 구성됩니다.

null 문은 일반적으로 반복 문에서 자리 표시자로 사용되거나 복합 문 또는 함수의 끝에 레이블을 배치할 문으로 사용됩니다.

다음 코드 조각에서는 한 문자열을 다른 문자열로 복사하여 null 문을 통합하는 방법을 보여 줍니다.

```cpp
// null_statement.cpp
char *myStrCpy( char *Dest, const char *Source )
{
    char *DestStart = Dest;

    // Assign value pointed to by Source to
    // Dest until the end-of-string 0 is
    // encountered.
    while( *Dest++ = *Source++ )
        ;   // Null statement.

    return DestStart;
}

int main()
{
}
```

## <a name="see-also"></a>참고 항목

[식 문](../cpp/expression-statement.md)
