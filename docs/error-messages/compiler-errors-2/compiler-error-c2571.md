---
title: "컴파일러 오류 C2571 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e760c9e9445339b47dc8f27e2ea5f2561b54af5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2571"></a>컴파일러 오류 C2571
'function': 가상 함수에 ' union' 될 수 없습니다  
  
 공용 구조체는 가상 함수 선언 됩니다. 클래스 또는 구조체에만 가상 함수를 선언할 수 있습니다.  가능한 해결 방법:  
  
1.  클래스 또는 구조체를 공용 구조체를 변경 합니다.  
  
2.  비가상 함수를 확인 합니다.  
  
 다음 샘플에서는 C2571 오류가 생성 됩니다.  
  
```  
// C2571.cpp  
// compile with: /c  
union A {  
   virtual void func1();   // C2571  
   void func2();   // OK  
};  
```