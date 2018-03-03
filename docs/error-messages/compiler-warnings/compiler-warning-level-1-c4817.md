---
title: "컴파일러 경고 (수준 1) C4817 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4817
dev_langs:
- C++
helpviewer_keywords:
- C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f11e0c555bdf3a80dcc381ee642d6adb0ecc5c21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4817"></a>컴파일러 경고(수준 1) C4817
'member': 이 멤버에 액세스하기 위해 '.'를 사용할 수 없습니다. 컴파일러는 '->'로 바뀝니다.  
  
 잘못된 멤버 액세스 연산자가 사용되었습니다.  
  
## <a name="example"></a>예  
 다음 샘플에서는 C4817을 생성합니다.  
  
```  
// C4817.cpp  
// compile with: /clr /W1  
using namespace System;  
int main() {  
   array<Int32> ^ a = gcnew array<Int32>(100);  
   Console::WriteLine( a.Length );   // C4817  
   Console::WriteLine( a->Length );   // OK  
}  
```  
