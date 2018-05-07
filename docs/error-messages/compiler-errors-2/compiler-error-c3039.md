---
title: 컴파일러 오류 C3039 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3039
dev_langs:
- C++
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bdcfa36d270dc842eec0508969c650e7b30bee4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3039"></a>컴파일러 오류 C3039
'var': OpenMP 'for' 문의 인덱스 변수는 환산(reduction) 변수가 될 수 없습니다.  
  
 인덱스 변수는 암시적으로 전용 변수이므로 [환산(reduction)](../../parallel/openmp/reference/reduction.md) 절의 바깥쪽 [병렬](../../parallel/openmp/reference/parallel.md) 지시문에 사용할 수 없습니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C3039를 생성합니다.  
  
```  
// C3039.cpp  
// compile with: /openmp /c  
int g_i;  
  
int main() {  
   int i;  
  
   #pragma omp parallel reduction(+: i)  
   {  
      #pragma omp for  
      for (i = 0; i < 10; ++i)   // C3039  
         g_i += i;  
   }  
}  
```