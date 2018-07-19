---
title: Nowait 절을 사용 하 여 A.4 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1de6b5e86d600ee1b3c2fa2c29fe014f9cb768
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689807"
---
# <a name="a4---using-the-nowait-clause"></a>A.4   nowait 절 사용
병렬 영역 내부에서는 여러 독립 루프에 있는 경우 사용할 수 있습니다는 `nowait` 절 ([섹션 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 페이지)의 끝에 암시적된 장벽을 방지 하기 위해는 `for` 다음과 같이 지시문:  
  
```  
#pragma omp parallel  
{  
    #pragma omp for nowait  
        for (i=1; i<n; i++)  
             b[i] = (a[i] + a[i-1]) / 2.0;  
    #pragma omp for nowait  
        for (i=0; i<m; i++)  
            y[i] = sqrt(z[i]);  
}  
```