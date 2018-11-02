---
title: 컴파일러 오류 C3002
ms.date: 11/04/2016
f1_keywords:
- C3002
helpviewer_keywords:
- C3002
ms.assetid: 2d4241a7-c8eb-4d43-a128-dca255d137bc
ms.openlocfilehash: 9f48021f5a32006c6a78a69500b0701cb7612d96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451131"
---
# <a name="compiler-error-c3002"></a>컴파일러 오류 C3002

'name1 name2': OpenMP 지시문 이름이 여러 개 있습니다.

여러 지시문 이름은 허용되지 않습니다.

다음 샘플에서는 C3002를 생성합니다.

```
// C3002.c
// compile with: /openmp
int main()
{
   #pragma omp parallel single   // C3002
}
```