---
title: 컴파일러 오류 C3001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3001
dev_langs:
- C++
helpviewer_keywords:
- C3001
ms.assetid: d0e03478-1b44-47e5-8f5b-70415fa1f8bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4c8275b1fc511ebf4e09b625f64cffae74a3ca6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263087"
---
# <a name="compiler-error-c3001"></a>컴파일러 오류 C3001
'error_text': OpenMP 지시문 이름이 필요합니다.  
  
 `omp` pragma 뒤에 지시문이 와야 합니다.  
  
 다음 샘플에서는 C3001을 생성합니다.  
  
```  
// C3001.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp   // C3001 missing token  
}  
```