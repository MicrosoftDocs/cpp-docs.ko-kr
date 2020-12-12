---
description: '자세한 정보: 컴파일러 오류 C3055'
title: 컴파일러 오류 C3055
ms.date: 11/04/2016
f1_keywords:
- C3055
helpviewer_keywords:
- C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
ms.openlocfilehash: 6c75d476abf7535499c74705e4a0ec77d80dc772
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269577"
---
# <a name="compiler-error-c3055"></a>컴파일러 오류 C3055

'symbol': 'threadprivate' 지시문에 사용된 기호만 참조할 수 있습니다.

기호가 참조된 다음 [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 절에서 사용되며 이는 허용되지 않습니다.

다음 샘플에서는 C3055를 생성합니다.

```cpp
// C3055.cpp
// compile with: /openmp
int x, y;
int z = x;
#pragma omp threadprivate(x, y)   // C3055

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

해결 방법:

```cpp
// C3055b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
