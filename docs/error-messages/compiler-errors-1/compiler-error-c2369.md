---
description: '자세한 정보: 컴파일러 오류 C2369'
title: 컴파일러 오류 C2369
ms.date: 11/04/2016
f1_keywords:
- C2369
helpviewer_keywords:
- C2369
ms.assetid: 2a3933f6-2313-40ff-800f-921b296fdbbf
ms.openlocfilehash: 42ae61307793383954c473eee948ee511815ab95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326087"
---
# <a name="compiler-error-c2369"></a>컴파일러 오류 C2369

'array': 재정의. 첨자가 다릅니다.

배열이 다른 아래 첨자로 이미 선언되었습니다.

다음 샘플에서는 C2369를 생성합니다.

```cpp
// C2369.cpp
// compile with: /c
int a[10];
int a[20];   // C2369
int b[20];   // OK
```
