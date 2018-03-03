---
title: "컴파일러 오류 C2033 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2033
dev_langs:
- C++
helpviewer_keywords:
- C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5695cb76ef3b5c65bb3b0ad8572d335e2aa5a77
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2033"></a>컴파일러 오류 C2033
'identifier': 비트 필드에 간접 참조를 사용할 수 없습니다.  
  
 비트 필드가 허용되지 않는 포인터로 선언되었습니다.  
  
 다음 샘플에서는 C2033을 생성합니다.  
  
```  
// C2033.cpp  
struct S {  
   int *b : 1;  // C2033  
};  
```  
  
 해결 방법:  
  
```  
// C2033b.cpp  
// compile with: /c  
struct S {  
   int b : 1;  
};  
```