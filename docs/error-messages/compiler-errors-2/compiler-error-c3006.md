---
description: '자세한 정보: 컴파일러 오류 C3006'
title: 컴파일러 오류 C3006
ms.date: 11/04/2016
f1_keywords:
- C3006
helpviewer_keywords:
- C3006
ms.assetid: 449082ec-fd45-4c47-8ab3-ba6a719e4dc4
ms.openlocfilehash: e2c6372b86f7677f3beeaed5335798f10e01c82e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274556"
---
# <a name="compiler-error-c3006"></a>컴파일러 오류 C3006

'clause': OpenMP 'directive' 지시문의 절에 필요한 인수가 없습니다.

OpenMP 지시문에 필요한 인수가 없습니다.

다음 샘플에서는 C3006을 생성합니다.

```c
// C3006.c
// compile with: /openmp
int main()
{
   #pragma omp parallel shared   // C3006
   // Try the following line instead:
   // #pragma omp parallel shared(x) {}

}
```
