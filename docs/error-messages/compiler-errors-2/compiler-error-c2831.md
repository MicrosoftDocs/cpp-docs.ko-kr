---
title: "컴파일러 오류 C2831 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2831
dev_langs:
- C++
helpviewer_keywords:
- C2831
ms.assetid: c8c04288-0889-4265-a077-17f94cbcdcc9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 19aea7100d3e4916fcce63301bb4fe2192e7ce9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2831"></a>컴파일러 오류 C2831
'operator 연산자' 기본 매개 변수를 가질 수 없습니다.  
  
 세 명의 연산자는 기본 매개 변수를 가질 수 있습니다.  
  
-   [new](../../cpp/new-operator-cpp.md)  
  
-   할당 =  
  
-   왼쪽된 괄호 드 (  
  
 다음 샘플에서는 C2831 오류가 생성 됩니다.  
  
```  
// C2831.cpp  
// compile with: /c  
#define BINOP <=  
class A {  
public:  
   int i;  
   int operator BINOP(int x = 1) {   // C2831  
   // try the following line instead  
   // int operator BINOP(int x) {  
      return i+x;  
   }  
};  
```