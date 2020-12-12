---
description: '자세한 정보: 컴파일러 오류 C2881'
title: 컴파일러 오류 C2881
ms.date: 11/04/2016
f1_keywords:
- C2881
helpviewer_keywords:
- C2881
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
ms.openlocfilehash: a1bc3922ce315d29f84309849660b2574631b2fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194360"
---
# <a name="compiler-error-c2881"></a>컴파일러 오류 C2881

' 1 ': 이미 ' orders2 '의 별칭으로 사용 되 고 있습니다.

두 네임 스페이스의 별칭으로 동일한 이름을 사용할 수 없습니다.

다음 샘플에서는 C2881를 생성 합니다.

```cpp
// C2881.cpp
// compile with: /c
namespace A {
   int k;
}

namespace B {
   int i;
}

namespace C = A;
namespace C = B;   // C2881 C is already an alias for A
```
