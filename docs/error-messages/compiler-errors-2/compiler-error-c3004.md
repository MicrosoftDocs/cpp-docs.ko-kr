---
description: '자세한 정보: 컴파일러 오류 C3004'
title: 컴파일러 오류 C3004
ms.date: 11/04/2016
f1_keywords:
- C3004
helpviewer_keywords:
- C3004
ms.assetid: 819c2b57-8366-4ca7-9135-1f0c5e5b6bb6
ms.openlocfilehash: 30737aca11b52fb8eaecc376c38211772442abf5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326030"
---
# <a name="compiler-error-c3004"></a>컴파일러 오류 C3004

'clause': OpenMP 'directive' 지시문의 절이 잘못되었습니다.

OpenMP 절이 활성화되지 않은 지시문에서 사용되었습니다.

다음 샘플에서는 C3004를 생성합니다.

```c
// C3004.c
// compile with: /openmp
int main()
{
   int x, y, z;

   // Shared clause not allowed for 'single' directive.
   #pragma omp single shared(x, y)   // C3004

   x = y;
}
```
