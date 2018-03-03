---
title: "컴파일러 경고 (수준 1) C4630 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4630
dev_langs:
- C++
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7d045903874649b98eb4b79237445e167b3a5e2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4630"></a>컴파일러 경고(수준 1) C4630
'symbol': 멤버 정의에 잘못 된 'extern' 저장소 클래스 지정자  
  
 데이터 멤버 또는 멤버 함수를 이루어집니다 `extern`합니다. 멤버는 전체 개체 수는 있지만, 외부 수 없습니다. 컴파일러에서 무시 된 `extern` 키워드입니다. 다음 샘플에서는 C4630 오류가 생성 됩니다.  
  
```  
// C4630.cpp  
// compile with: /W1 /LD  
class A {  
   void func();  
};  
  
extern void A::func() {   // C4630, remove 'extern' to resolve  
}  
```