---
title: "컴파일러 오류 C2910 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2910
dev_langs:
- C++
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 202593b506fc957fb98cc390c1874312509ea481
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2910"></a>컴파일러 오류 C2910
'function': 명시적으로 특수화할 수 없습니다.  
  
 컴파일러는 함수를 두 번 명시적으로 특수화 하려고를 했습니다.  
  
 다음 샘플에서는 C2910 오류가 생성 됩니다.  
  
```  
// C2910.cpp  
// compile with: /c  
template <class T>  
struct S;  
  
template <> struct S<int> { void f() {} };  
template <> void S<int>::f() {}   // C2910 delete this specialization  
```  
  
 템플릿이 아닌 멤버를 명시적으로 특수화 하려고 하면 C2910 생성할 수도 있습니다. 즉, 함수 템플릿을 명시적으로 특수화할 수 있습니다.  
  
 다음 샘플에서는 C2910 오류가 생성 됩니다.  
  
```  
// C2910b.cpp  
// compile with: /c  
template <class T> struct A {  
   A(T* p);  
};  
  
template <> struct A<void> {  
   A(void* p);  
};  
  
template <class T>  
inline A<T>::A(T* p) {}  
  
template <> A<void>::A(void* p){}   // C2910  
// try the following line instead  
// A<void>::A(void* p){}  
```  
  
 이 오류는 Visual Studio.NET 2003 컴파일러 규칙 작업의 결과로 생성 됩니다: 합니다.  
  
 코드를 Visual c + +의 Visual Studio.NET 2003 및 Visual Studio.NET 버전에서 사용할 수에 대 한 제거 `template <>`합니다.  
  
 다음 샘플에서는 C2910 오류가 생성 됩니다.  
  
```  
// C2910c.cpp  
// compile with: /c  
template <class T> class A {  
   void f();  
};  
  
template <> class A<int> {  
   void f();  
};  
  
template <> void A<int>::f() {}   // C2910  
// try the following line instead  
// void A<int>::f(){}   // OK  
```