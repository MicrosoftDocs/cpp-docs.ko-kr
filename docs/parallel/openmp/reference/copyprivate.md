---
title: copyprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyprivate
dev_langs:
- C++
helpviewer_keywords:
- copyprivate OpenMP clause
ms.assetid: 02c0209d-abe8-4797-8365-a82b53c3f15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96b1516970afb8729dc4e35c2226eb6ff00f5c2e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692940"
---
# <a name="copyprivate"></a>copyprivate
하나 이상의 변수 모든 스레드 간에 공유 되지 않아야 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
copyprivate(var)  
```  
  
## <a name="remarks"></a>설명  
 다음은 각 문자에 대한 설명입니다.  
  
 `var`  
 하나 이상의 변수를 공유 합니다. 둘 이상의 변수를 지정 하는 경우 변수 이름을 쉼표로 구분 합니다.  
  
## <a name="remarks"></a>설명  
 `copyprivate` 에 적용 된 [단일](../../../parallel/openmp/reference/single.md) 지시문입니다.  
  
 자세한 내용은 참조 [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md)합니다.  
  
## <a name="example"></a>예제  
  
```  
// omp_copyprivate.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
float x, y, fGlobal = 1.0;  
#pragma omp threadprivate(x, y)  
  
float get_float() {  
   fGlobal += 0.001;  
   return fGlobal;  
}  
  
void use_float(float f, int t) {  
   printf_s("Value = %f, thread = %d\n", f, t);  
}  
  
void CopyPrivate(float a, float b) {  
   #pragma omp single copyprivate(a, b, x, y)   
   {  
      a = get_float();  
      b = get_float();  
      x = get_float();  
      y = get_float();  
    }  
  
   use_float(a, omp_get_thread_num());     
   use_float(b, omp_get_thread_num());     
   use_float(x, omp_get_thread_num());  
   use_float(y, omp_get_thread_num());  
}  
  
int main() {  
   float a = 9.99, b = 123.456;  
  
   printf_s("call CopyPrivate from a single thread\n");  
   CopyPrivate(9.99, 123.456);  
  
   printf_s("call CopyPrivate from a parallel region\n");  
   #pragma omp parallel       
   {  
      CopyPrivate(a, b);  
   }  
}  
```  
  
```Output  
call CopyPrivate from a single thread  
Value = 1.001000, thread = 0  
Value = 1.002000, thread = 0  
Value = 1.003000, thread = 0  
Value = 1.004000, thread = 0  
call CopyPrivate from a parallel region  
Value = 1.005000, thread = 0  
Value = 1.005000, thread = 1  
Value = 1.006000, thread = 0  
Value = 1.006000, thread = 1  
Value = 1.007000, thread = 0  
Value = 1.007000, thread = 1  
Value = 1.008000, thread = 0  
Value = 1.008000, thread = 1  
```  
  
## <a name="see-also"></a>참고 항목  
 [절](../../../parallel/openmp/reference/openmp-clauses.md)