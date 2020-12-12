---
description: '자세한 정보: 심각한 오류 C1310'
title: 심각한 오류 C1310
ms.date: 11/04/2016
f1_keywords:
- C1310
helpviewer_keywords:
- C1310
ms.assetid: ac48aa51-8023-42fe-b844-3f8bf228fbef
ms.openlocfilehash: edd4cb75c77ec272ddd3f985b4bfefac93e04e83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177759"
---
# <a name="fatal-error-c1310"></a>심각한 오류 C1310

OpenMP에서는 프로필 기반 최적화를 사용할 수 없습니다.

[/GL](../../build/reference/ltcg-link-time-code-generation.md) 로 컴파일된 모든 모듈을 [/LTCG:PGI](../../build/reference/gl-whole-program-optimization.md)와 연결할 수 없습니다.

다음 샘플에서는 C1310을 생성합니다.

```cpp
// C1310.cpp
// compile with: /openmp /GL /link /LTCG:PGI
// C1310 expected
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 0; i++)
         --j;
   }
}
```
