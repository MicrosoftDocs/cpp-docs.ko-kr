---
title: "컴파일러 경고 (수준 1) C4440 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4440
dev_langs:
- C++
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 418c49aa988c5cbf37b2307ca7f488dd9c4243d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4440"></a>컴파일러 경고(수준 1) C4440
재정의 된 호출 규칙이 'calling_convention1'에서 'calling_convention2' 무시 하려면  
  
 호출 규칙을 변경 하려고가.  
  
 다음 샘플에서는 C4440 오류가 생성 됩니다.  
  
```  
// C4440.cpp  
// compile with: /W1 /LD /clr  
typedef void __clrcall F();  
typedef F __cdecl *PFV;   // C4440  
```