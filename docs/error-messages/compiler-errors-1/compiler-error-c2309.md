---
title: 컴파일러 오류 C2309 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2309
dev_langs:
- C++
helpviewer_keywords:
- C2309
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52be559b2e5991e647425b99a1795866046d9050
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2309"></a>컴파일러 오류 C2309
catch 처리기에 괄호로 묶은 예외 선언이 필요합니다.  
  
 Catch 처리기에 괄호로 묶인 형식이 없습니다.  
  
 다음 샘플에서는 C2309 오류가 생성 됩니다.  
  
```  
// C2309.cpp  
// compile with: /EHsc  
#include <eh.h>  
class C {};  
int main() {  
   try {  
      throw "ooops!";  
   }  
   catch C {}   // C2309  
   // try the following line instead  
   // catch( C ) {}  
}  
```