---
title: 컴파일러 오류 C2451 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2451
dev_langs:
- C++
helpviewer_keywords:
- C2451
ms.assetid: a64c93a5-ab8d-4d39-ae57-9ee7ef803036
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2344ba4629a4f35556d8fc6c2e6760cadbc6392b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2451"></a>컴파일러 오류 C2451
'type' 형식의 조건식 올바르지 않습니다.  
  
 조건 식은 정수 형식으로 평가합니다.  
  
 다음 샘플에서는 C2451 오류가 생성 됩니다.  
  
```  
// C2451.cpp  
class B {};  
  
int main () {  
   B b1;  
   int i = 0;  
   if (b1)   // C2451  
   // try the following line instead  
   // if (i)  
      ;  
}  
```