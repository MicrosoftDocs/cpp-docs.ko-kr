---
title: "컴파일러 오류 C3874 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3874
dev_langs:
- C++
helpviewer_keywords:
- C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f14dd566c7246b2de5e718bab6a05d1b3ebc852f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3874"></a>컴파일러 오류 C3874
'function'의 반환 형식은 'int' 대신 'type' 해야 합니다.  
  
 함수에는 컴파일러에서 예상 된 반환 형식이 없습니다.  
  
 다음 샘플에서는 C3874 오류가 생성 됩니다.  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```