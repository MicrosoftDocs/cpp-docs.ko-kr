---
title: 컴파일러 오류 C2636 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2636
dev_langs:
- C++
helpviewer_keywords:
- C2636
ms.assetid: 379873ec-8d05-49f8-adf1-b067bc07bdb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61422fcf03cabd6d7c2ed8bca23b9170df7e52bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2636"></a>컴파일러 오류 C2636
'identifier': 참조 멤버에 대 한 포인터가 잘못 되었습니다  
  
 참조 멤버에 대 한 포인터를 선언 했습니다.  
  
 다음 샘플에서는 C2636 오류가 생성 됩니다.  
  
```  
// C2636.cpp  
struct S {};  
int main() {  
   int &S::*prs;   // C2636  
   int S::*prs1;   // OK  
   int *S::*prs2;   // OK  
}  
```