---
title: 컴파일러 경고 (수준 1) C4813 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4813
dev_langs:
- C++
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 310c4c3a0d4be35e45c9593dc4f3cc1de00077d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283252"
---
# <a name="compiler-warning-level-1-c4813"></a>컴파일러 경고(수준 1) C4813
'function': 지역 클래스의 friend 함수를 미리 선언해야 합니다.  
  
 내부 클래스의 friend 함수가 외부 클래스에서 선언되지 않았습니다.  
  
 다음 샘플에서는 C4813을 생성합니다.  
  
```  
// C4813.cpp  
// compile with: /W1 /LD  
void MyClass()  
{  
   // void func();  
   class InnerClass  
   {  
      friend void func();   // C4813 uncomment declaration above  
   };  
}  
```