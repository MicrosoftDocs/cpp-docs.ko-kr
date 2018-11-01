---
title: 컴파일러 오류 C2881
ms.date: 11/04/2016
f1_keywords:
- C2881
helpviewer_keywords:
- C2881
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
ms.openlocfilehash: 82a4fbe94bc7250244d57f549e52037d6a54c784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610524"
---
# <a name="compiler-error-c2881"></a>컴파일러 오류 C2881

'namespace1': 이미 'namespace2'에 대 한 별칭으로 사용

두 개의 네임 스페이스에 대 한 별칭으로 동일한 이름을 사용할 수 없습니다.

다음 샘플에서는 C2881 오류가 생성 됩니다.

```
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