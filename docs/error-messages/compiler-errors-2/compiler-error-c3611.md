---
title: "컴파일러 오류 C3611 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3611
dev_langs:
- C++
helpviewer_keywords:
- C3611
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43e704ca395b3575139705f81d34ffa994479e63
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3611"></a>컴파일러 오류 C3611
'function': 봉인된 함수는 순수 지정자를 사용할 수 없습니다  
  
 봉인된 함수를 잘못 선언 되었습니다.  자세한 내용은 참조 [봉인](../../windows/sealed-cpp-component-extensions.md)합니다.  
  
## <a name="example"></a>예  
 다음 샘플에서는 C3611 오류가 발생 합니다.  
  
```  
// C3611.cpp  
// compile with: /clr /c  
  
ref struct V {  
   virtual void Test() sealed = 0;   // C3611  
   virtual void Test2() sealed;   // OK  
   virtual void Test3() = 0;   // OK  
};  
```