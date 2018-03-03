---
title: "컴파일러 오류 C3854 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3854
dev_langs:
- C++
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed910ecf91642a6a1a1c5777be09b0251ddeda2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3854"></a>컴파일러 오류 C3854
함수에 '='의 왼쪽으로 식을 평가합니다. (한 함수는 l 값이 아님) 함수에 할당할 수 없습니다.  
  
 대 한 참조를 다시 초기화할 수 없습니다. 함수에 대 한 참조를 역참조 하 고 할당할 수 없습니다, rvalue가 함수를 생성 합니다. 따라서 함수에 대 한 참조를 통해 할당할 수 없습니다.  
  
 다음 샘플에서는 C3854 오류가 생성 됩니다.  
  
```  
// C3854.cpp  
int afunc(int i)  
{  
   return i;  
}  
  
typedef int (& rFunc_t)(int);  
typedef int (* pFunc_t)(int);  
  
int main()  
{  
   rFunc_t rf = afunc;   // OK binding a reference to function  
   pFunc_t pf = &afunc;   // OK initializing a pointer to function  
  
   *pf = &afunc;   // C3854  
   // try the following line instead  
   // pf = &afunc;  
   *rf = &afunc;   // C3854  
}  
```