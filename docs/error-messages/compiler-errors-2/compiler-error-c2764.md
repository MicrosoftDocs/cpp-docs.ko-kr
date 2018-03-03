---
title: "컴파일러 오류 C2764 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2764
dev_langs:
- C++
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c623b48baf8a3ba41c7b14a4878e8473e0771cbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2764"></a>컴파일러 오류 C2764
'param': 템플릿 매개 변수 사용 하거나 부분 특수화 'specialization'에서 추론할 수 없습니다  
  
 부분 특수화에 템플릿 매개 변수가 사용 되지 않습니다. 이 부분 특수화를 사용할 수 없게 되므로 템플릿 매개 변수를 추론할 수 없습니다.  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2764 오류가 생성 됩니다.  
  
```  
// C2764.cpp  
#include <stdio.h>  
template <class T1, class T2>  
struct S  {  
   int m_i;  
};  
  
template <class T1, class T2>  
struct S<int, T2*> {   // C2764  
// try the following line instead  
// struct S<T1(*)(T2), T2*> {  
   char m_c;  
};  
  
int main() {  
   S<int, char> s1;  
   S<void (*)(short), short *> s2;  
   s2.m_c = 10;  
   s1.m_i = s2.m_c;  
   printf_s("%d\n", s1.m_i);  
}  
```