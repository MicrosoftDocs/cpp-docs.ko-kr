---
title: 컴파일러 오류 C2009
ms.date: 11/04/2016
f1_keywords:
- C2009
helpviewer_keywords:
- C2009
ms.assetid: fe9d94ed-20a5-4d83-b9c4-60ee69d2f30a
ms.openlocfilehash: 02780a88552231472c2e16299a6d5e5dfef1bdd2
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743115"
---
# <a name="compiler-error-c2009"></a>컴파일러 오류 C2009

매크로 형식 'identifier'를 다시 사용하세요.

매크로 정의의 정식 매개 변수 목록에서 식별자를 두 번 이상 사용 합니다. 매크로의 매개 변수 목록에 있는 식별자는 고유 해야 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2009를 생성 합니다.

```cpp
// C2009.cpp
#include <stdio.h>

#define macro1(a,a) (a*a)   // C2009

int main()
{
    printf_s("%d\n", macro1(2));
}
```

해결 방법:

```cpp
// C2009b.cpp
#include <stdio.h>

#define macro2(a)   (a*a)
#define macro3(a,b) (a*b)

int main()
{
    printf_s("%d\n", macro2(2));
    printf_s("%d\n", macro3(2,4));
}
```
