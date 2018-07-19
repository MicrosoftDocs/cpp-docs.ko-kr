---
title: 컴파일러 오류 C3013 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3013
dev_langs:
- C++
helpviewer_keywords:
- C3013
ms.assetid: f896777d-27e6-4b6d-baab-1567317f3374
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 443a10936ebb08a5d9243b534bd93bb6a2753871
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33242094"
---
# <a name="compiler-error-c3013"></a>컴파일러 오류 C3013
'clause': OpenMP 'directive' 지시문에는 절이 한 번만 나와야 합니다.  
  
 동일한 지시문에 절이 두 번 표시되었습니다. 발생한 절 하나를 삭제합니다.  
  
 다음 샘플에서는 C3013을 생성합니다.  
  
```  
// C3013.cpp  
// compile with: /openmp  
int main() {  
   int a, b, c, x, y, z;  
  
   #pragma omp parallel shared(a,b,c) private(x)  
  
   #pragma omp for nowait private(x) nowait   // C3013  
   // The previous line generates C3013, with two nowait clauses  
   // try the following line instead:  
   // #pragma omp for nowait private(x)  
   for (a = 0 ; a < 10 ; ++a) {  
   }  
}  
```