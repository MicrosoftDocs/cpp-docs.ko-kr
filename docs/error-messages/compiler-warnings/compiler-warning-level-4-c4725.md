---
title: 컴파일러 경고(수준 4) C4725
ms.date: 11/04/2016
f1_keywords:
- C4725
helpviewer_keywords:
- C4725
ms.assetid: effa0335-71c3-4b3b-8618-da4b9b46a95d
ms.openlocfilehash: 9da830133bbca2abcd5fa77339e698b35dae32f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455642"
---
# <a name="compiler-warning-level-4-c4725"></a>컴파일러 경고(수준 4) C4725

명령이 일부 Pentium에서 정확하지 않을 수 있습니다.

코드에 일부 Pentium 마이크로프로세서에서 정확한 결과를 생성하지 않을 수 있는 인라인 어셈블리 명령이 포함되어 있습니다.

다음 샘플에서는 C4725를 생성합니다.

```
// C4725.cpp
// compile with: /W4
// processor: x86
double m32fp = 2.0003e-17;

void f() {
   __asm
   {
      FDIV m32fp   // C4725
   }
}

int main() {
}
```