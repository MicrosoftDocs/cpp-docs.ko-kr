---
description: '자세한 정보: 컴파일러 오류 C3058'
title: 컴파일러 오류 C3058
ms.date: 11/04/2016
f1_keywords:
- C3058
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
ms.openlocfilehash: 9a7c4c3fa4fd8186055985ff66caa3ffd0c4f081
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269460"
---
# <a name="compiler-error-c3058"></a>컴파일러 오류 C3058

'symbol': 기호를 'copyin' 절에 사용하기 전에 'threadprivate'로 선언하지 않았습니다.

기호를 먼저 [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 로 선언해야 [copyin](../../parallel/openmp/reference/openmp-clauses.md#copyin) 절에 사용할 수 있습니다.

다음 샘플에서는 C3058을 생성합니다.

```cpp
// C3058.cpp
// compile with: /openmp
int x, y, z;
#pragma omp threadprivate(x, z)

void test() {
   #pragma omp parallel copyin(x, y)   // C3058
   {
   }
}
```

해결 방법:

```cpp
// C3058b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
   }
}
```
