---
title: goto 및 레이블 문 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf56a409f9a76cdf401323d1425ee28fc6cf286b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386416"
---
# <a name="goto-and-labeled-statements-c"></a>goto 및 레이블 문 (C)
`goto` 문은 레이블에 제어를 전송합니다. 지정된 레이블은 동일한 함수에 있어야 하며 동일한 함수에서 하나의 문 앞에만 나타날 수 있습니다.  
  
## <a name="syntax"></a>구문  
 *statement*:  
 *labeled-statement*  
  
 *jump-statement*  
  
 *점프 문*:  
 **goto**  *identifier*  **;**  
  
 *labeled-statement*:  
 *identifier*  **:**  *statement*  
  
 문 레이블은 `goto` 문에만 의미가 있으며 다른 모든 컨텍스트에서 레이블 문은 레이블에 관계없이 실행됩니다.  
  
 *jump-statement*는 동일한 함수에 있어야 하며 동일한 함수에서 하나의 문 앞에만 나타날 수 있습니다. `goto` 이후에 오는 *identifier* 이름 집합은 해당 이름이 다른 식별자를 방해하지 않도록 자체 네임스페이스를 가지고 있습니다. 레이블을 다시 선언할 수 없습니다. 자세한 내용은 [네임스페이스](../c-language/name-spaces.md)를 참조하세요.  
  
 가능하면 `goto`보다 **break**, **continue** 및 `return` 문을 사용하는 것이 더 좋은 프로그래밍 방식입니다. **break** 문은 한 수준의 루프에서만 종료되므로 깊이 중첩된 루프 내에서 루프를 종료하려면 `goto`가 필요할 수도 있습니다.  
  
 이 예제에서는 `goto` 문을 보여 줍니다.  
  
```  
// goto.c  
#include <stdio.h>  
  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 3; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 5 )  
                goto stop;  
        }  
    }  
  
    /* This message does not print: */  
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop: printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
 이 예제에서 `goto`가 5에 해당하는 경우 `stop` 문은 `i`이라는 레이블이 지정된 지점으로 제어를 전송합니다.  
  
## <a name="see-also"></a>참고 항목  
 [문](../c-language/statements-c.md)