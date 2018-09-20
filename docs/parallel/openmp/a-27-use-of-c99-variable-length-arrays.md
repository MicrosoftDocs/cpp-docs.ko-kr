---
title: A.27 C99 가변 길이 배열 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51fda970f78592c8a4e10d17d370e9c78f0ea493
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405894"
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27   C99 가변 길이 배열 사용

다음 예제에서 C99 가변 길이 배열 (Vla)를 사용 하는 방법에 설명 된 `firstprivate` 지시문 ([2.7.2.2 섹션](../../parallel/openmp/2-7-2-2-firstprivate.md) 26 페이지).

> [!NOTE]
>  Visual c + +에서 가변 길이 배열은 현재 지원 되지 않습니다.

```
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```