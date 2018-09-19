---
title: Null 문 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27180a8252344f7b3185ec83b48ebef42f832907
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077362"
---
# <a name="null-statement"></a>Null 문

"Null 문"은 사용 하는 식 문은 합니다 *식* 없습니다. 언어의 구문에 문이 필요하지만 식 계산은 필요하지 않은 경우에 이 문이 유용합니다. 이 문은 세미콜론으로 구성됩니다.

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

## <a name="see-also"></a>참고자료

[식 문](../cpp/expression-statement.md)