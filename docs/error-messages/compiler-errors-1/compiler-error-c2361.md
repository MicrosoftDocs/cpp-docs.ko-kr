---
title: "컴파일러 오류 C2361 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2361
dev_langs:
- C++
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afbc770118f42794639cbce92f8d360446b0ae9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2361"></a>컴파일러 오류 C2361
'i'의 초기화 'default' 레이블에 의해 생략 되었습니다.  
  
 초기화 `identifier` 건너 뛸 수 있습니다는 `switch` 문. 선언 블록 포함 하지 않는 한 이니셜라이저와 함께 선언 점프할 수 없습니다. (하지 않은 블록 내에 선언 된 변수는 범위 내에서 끝날 때까지 `switch` 문.)  
  
 다음 샘플에서는 C2361 오류가 생성 됩니다.  
  
```  
// C2361.cpp  
void func( void ) {  
   int x;  
   switch (x) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   default :   // C2361 error  
      int k = 1;  
   }  
}  
```  
  
 해결 방법:  
  
```  
// C2361b.cpp  
// compile with: /c  
void func( void ) {  
   int x = 0;  
   switch (x) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   default :  
      int k = 1;  
   }  
}  
```