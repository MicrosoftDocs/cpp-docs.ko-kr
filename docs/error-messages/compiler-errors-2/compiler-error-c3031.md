---
description: '자세한 정보: 컴파일러 오류 C3031'
title: 컴파일러 오류 C3031
ms.date: 11/04/2016
f1_keywords:
- C3031
helpviewer_keywords:
- C3031
ms.assetid: 7e621e7e-eda7-45b5-8836-29599cd05255
ms.openlocfilehash: 3da80fbf39c62f3e8918f58430a6932abd93f1a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328428"
---
# <a name="compiler-error-c3031"></a>컴파일러 오류 C3031

'var': 'reduction' 절의 변수는 스칼라 산술 형식이어야 합니다.

잘못된 형식의 변수가 reduction 절에 전달되었습니다.

다음 샘플에서는 C3031을 생성합니다.

```cpp
// C3031.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

typedef struct {
   int n;
} Incomplete;

extern Incomplete inc;
int i = 9;

int main() {
   #pragma omp parallel reduction(+: inc)   // C3031
      ;

   #pragma omp parallel reduction(+: i)     // OK
      ;
}
```
