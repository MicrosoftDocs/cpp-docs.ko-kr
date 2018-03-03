---
title: "절은 개인의 A.24 예 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e0abd7aa296a16e54e2ec5e5ce7b2c49a93c45e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="a24---example-of-the-private-clause"></a>A.24   private 절 예제
`private` 절 ([섹션 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) 페이지 25)의 병렬 영역에만 동적 지역 범위 아닌는 영역의 어휘 범위에 적용 됩니다.  다음에 나오는 예제, 변수의 사용이 모두에 따라서 *는* 내는 `for` 루틴에 루프 *f* 의 전용 복사본을 가리킵니다 *는*에서 사용 하는 동안 루틴 *g* 전역를 참조 *는*합니다.  
  
```  
int a;  
  
void f(int n)   
{  
    a = 0;  
  
    #pragma omp parallel for private(a)  
    for (int i=1; i<n; i++)   
    {  
        a = i;  
        g(i, n);  
        d(a);     // Private copy of "a"  
        ...  
    }  
    ...  
  
void g(int k, int n)   
{  
    h(k,a); // The global "a", not the private "a" in f  
}  
```