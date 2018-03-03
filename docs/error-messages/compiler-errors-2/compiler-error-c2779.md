---
title: "컴파일러 오류 C2779 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2779
dev_langs:
- C++
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afae21cdd5f22d30da9702438e910cd1a8f0db2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2779"></a>컴파일러 오류 C2779
'declaration': 속성 메서드만 비정적 데이터 멤버와 연결할 수  
  
 `property` 확장된 특성 정적 데이터 멤버에 올바르게 적용 됩니다.  
  
 다음 샘플에서는 C2779 오류가 생성 됩니다.  
  
```  
// C2779.cpp  
struct A {  
   static __declspec(property(put=PutProp))  
   // try the following line instead  
   __declspec(property(put=PutProp))  
      int prop;   // C2779  
   int PutProp(void);  
};  
```