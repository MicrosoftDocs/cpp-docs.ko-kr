---
description: '자세한 정보: break 문(C)'
title: break 문 (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: 54f20de08661073a65ee0b8c50cf877e719aadcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211650"
---
# <a name="break-statement-c"></a>break 문 (C)

**`break`** 문은 해당 문이 배치된 지점에서 가장 가까이에 있는 **`do`** , **`for`** , **`switch`** 또는 **`while`** 문의 실행을 종료합니다. 제어는 종료된 문 뒤의 문으로 전달됩니다.

## <a name="syntax"></a>구문

*점프 문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**

**`break`** 문은 **`switch`** 문 내의 특정 경우의 처리를 종료하는 데 자주 사용됩니다. 닫힌 반복문 또는 **`switch`** 문이 없으면 오류가 발생합니다.

중첩된 문 내의 **`break`** 문은 해당 문을 둘러싼 **`do`** , **`for`** , **`switch`** 또는 **`while`** 문만을 종료합니다. **`return`** 또는 **`goto`** 문을 사용하여 제어를 중첩된 구조 외부의 다른 지점으로 전달할 수도 있습니다.

이 예제에서는 **`break`** 문에 대해 설명합니다.

```C
#include <stdio.h>
int main() {
   char c;
   for(;;) {
      printf_s( "\nPress any key, Q to quit: " );

      // Convert to character value
      scanf_s("%c", &c);
      if (c == 'Q')
          break;
   }
} // Loop exits only when 'Q' is pressed
```

## <a name="see-also"></a>참조

[break 문](../cpp/break-statement-cpp.md)
