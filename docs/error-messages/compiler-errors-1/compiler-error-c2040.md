---
title: "컴파일러 오류 C2040 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f102b1fea23c89debc86970d7548ba7da152cd37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2040"></a>컴파일러 오류 C2040
'operator' : 'identifier1'의 간접 참조 수준이 'identifier2'와 다릅니다.  
  
 지정 피연산자가 포함된 식에 호환되지 않는 피연산자 형식이나 암시적으로 변환된 피연산자 형식이 있습니다. 두 피연산자 모두가 산술이거나 모두가 비산술(예: 배열 또는 포인터)인 경우 변경 없이 사용됩니다. 한 피연산자는 산술이고 다른 피연산자는 아닌 경우 산술 피연산자가 비산술 피연산자의 형식으로 변환됩니다.  
  
 다음 샘플에서는 C2040 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.  
  
```  
// C2040.cpp  
// Compile by using: cl /c /W3 C2040.cpp  
bool test() {  
   char c = '3';  
   return c == "3"; // C2446, C2040  
   // return c == '3'; // OK  
}  
```