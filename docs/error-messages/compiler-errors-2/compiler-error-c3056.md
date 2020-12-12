---
description: '자세한 정보: 컴파일러 오류 C3056'
title: 컴파일러 오류 C3056
ms.date: 11/04/2016
f1_keywords:
- C3056
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
ms.openlocfilehash: d934221c4501256eb4bfd604bcc04534268de3fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269538"
---
# <a name="compiler-error-c3056"></a>컴파일러 오류 C3056

'symbol': 기호가 'threadprivate' 지시문과 같은 범위에 속하지 않습니다.

[threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 절에서 사용되는 기호는 `threadprivate` 절과 동일한 범위에 있어야 합니다.

다음 샘플에서는 C3056을 생성합니다.

```cpp
// C3056.cpp
// compile with: /openmp
int x, y;
void test() {
   #pragma omp threadprivate(x, y)   // C3056
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

해결 방법:

```cpp
// C3056b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)
void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
