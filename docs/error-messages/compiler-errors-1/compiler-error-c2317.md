---
title: "컴파일러 오류 C2317 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2317
dev_langs:
- C++
helpviewer_keywords:
- C2317
ms.assetid: e44d129b-8d3e-4ce9-9d79-6791ee77f25e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 110f5efb67c2962987514bf4e79391d484470779
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2317"></a>컴파일러 오류 C2317
줄 'number'에서 시작하는 'try' 블록에 catch 처리기가 없습니다.  
  
 `try` 블록에는 하나 이상의 catch 처리기가 있어야 합니다.  
  
 다음 샘플에서는 C2317을 생성합니다.  
  
```  
// C2317.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "throw an exception";  
   }  
   // C2317, no catch handler  
}  
```  
  
 해결 방법:  
  
```  
// C2317b.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "throw an exception";  
   }  
   catch(char*) {}  
}  
```