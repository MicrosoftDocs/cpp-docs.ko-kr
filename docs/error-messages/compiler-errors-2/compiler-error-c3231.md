---
title: 컴파일러 오류 C3231 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3231
dev_langs:
- C++
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4925055caac0f3d26922eebf6a043ad51c83efa2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3231"></a>컴파일러 오류 C3231
'arg': 템플릿 형식 인수는 제네릭 형식 매개 변수를 사용할 수 없습니다  
  
 템플릿은 컴파일 시간에 인스턴스화되는데 제네릭은 런타임에 인스턴스화됩니다. 따라서 제네릭 형식이 마지막으로 알려졌을 때 템플릿을 런타임에 인스턴스화할 수 없으므로 템플릿을 호출할 수 있는 제네릭 코드를 생성할 수 없습니다.  
  
 다음 샘플에서는 C3231 오류가 생성 됩니다.  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```