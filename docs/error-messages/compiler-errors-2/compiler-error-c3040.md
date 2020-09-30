---
title: 컴파일러 오류 C3040
ms.date: 11/04/2016
f1_keywords:
- C3040
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
ms.openlocfilehash: 943c4b3da1a90c8636246032a3d8faf41ad4552a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508359"
---
# <a name="compiler-error-c3040"></a>컴파일러 오류 C3040

'var': 'reduction' 절의 변수 형식이 환산 연산자 'operator'와 호환되지 않습니다.

[reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) 절의 변수를 reduction 연산자와 함께 사용할 수 없습니다.

다음 샘플에서는 C3040을 생성합니다.

```cpp
// C3040.cpp
// compile with: /openmp /c
#include "omp.h"
double d;

int main() {
   #pragma omp parallel reduction(&:d)   // C3040
      ;

   #pragma omp parallel reduction(-:d)  // OK
      ;
}
```
