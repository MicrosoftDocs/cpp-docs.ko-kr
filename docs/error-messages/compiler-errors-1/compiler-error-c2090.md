---
title: "컴파일러 오류 C2090 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2090
dev_langs:
- C++
helpviewer_keywords:
- C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e929f415c294a9e14dadd1ac8ecd1b0915de592
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2090"></a>컴파일러 오류 C2090
함수 배열을 반환합니다  
  
 함수 배열을 반환할 수 없습니다. 대신 배열에 대 한 포인터를 반환 합니다.  
  
 다음 샘플에서는 C2090 오류가 생성 됩니다.  
  
```  
// C2090.cpp  
int func1(void)[] {}   // C2090  
```  
  
 해결 방법:  
  
```  
// C2090b.cpp  
// compile with: /c  
int* func2(int * i) {  
   return i;  
}  
```