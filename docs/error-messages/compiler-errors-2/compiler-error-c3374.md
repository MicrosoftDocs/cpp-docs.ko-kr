---
title: "컴파일러 오류 C3374 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3374
dev_langs:
- C++
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ecdacf3755560ef5f3dd7bfb8786945d457ee750
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3374"></a>컴파일러 오류 C3374
대리자 인스턴스를 만들지 않으면 'function'의 주소를 가져올 수 없습니다.  
  
 대리자 인스턴스를 만드는 컨텍스트가 아닌 다른 컨텍스트에서 함수의 주소를 가져왔습니다.  
  
 다음 샘플에서는 C3374 오류가 발생하는 경우를 보여 줍니다.  
  
```  
// C3374.cpp  
// compile with: /clr  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      System::Console::WriteLine("in func1 {0}", i);  
   }  
};  
  
int main() {  
   &A::func1;   // C3374  
  
   // OK  
   A ^ a = gcnew A;  
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [방법: 대리자 정의 및 사용(C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)