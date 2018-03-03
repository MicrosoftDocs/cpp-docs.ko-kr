---
title: "컴파일러 오류 C2208 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2208
dev_langs:
- C++
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73c535ad2aa24064afaf8fe631755bd33252f899
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2208"></a>컴파일러 오류 C2208
'type':이 형식을 사용 하 여 정의 된 멤버  
  
 형식 이름으로 확인 되는 식별자는 집계 선언에 있지만 컴파일러는 멤버를 선언할 수 없습니다.  
  
 다음 샘플에서는 C2208 오류가 생성 됩니다.  
  
```  
// C2208.cpp  
class C {  
   C;   // C2208  
   C(){}   // OK  
};  
```