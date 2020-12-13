---
description: '자세한 정보: 심각한 오류 C1094'
title: 심각한 오류 C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: af83c6fa80a6e1b115146ad05513539fea7d348c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145095"
---
# <a name="fatal-error-c1094"></a>심각한 오류 C1094

'-Zmval1 ': 명령줄 옵션이 미리 컴파일된 헤더 ('-Zmval2 ')를 빌드하는 데 사용 된 값과 일치 하지 않습니다.

[/Yc](../../build/reference/yc-create-precompiled-header-file.md) 에 전달 되는 값은 [/yu](../../build/reference/yu-use-precompiled-header-file.md) 로 전달 되는 값과 동일 해야 합니다 (**/zm** 값은 동일한 미리 컴파일된 헤더 파일을 사용 하거나 만드는 모든 컴파일에서 동일 해야 함).

다음 샘플에서는 C1094를 생성 합니다.

```
// C1094.h
int func1();
```

그리고

```cpp
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

그리고

```cpp
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```
