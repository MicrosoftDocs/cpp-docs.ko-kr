---
title: 컴파일러 오류 C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: c4f099ba241b56291074202e6c03ad98ee97f756
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743505"
---
# <a name="compiler-error-c2004"></a>컴파일러 오류 C2004

'defined(id)'가 필요합니다.

식별자는 전처리기 키워드 뒤의 괄호에 나타나야 합니다.

이 오류는 Visual Studio .NET 2003에 대해 수행한 컴파일러 규칙 작업의 결과로 생성될 수도 있습니다. 전처리기 지시문에 괄호가 없습니다. 전처리기 지시문에 닫는 괄호가 없는 경우 컴파일러에서 오류를 생성합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2004를 생성합니다.

```cpp
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

해결 방법:

```cpp
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```
