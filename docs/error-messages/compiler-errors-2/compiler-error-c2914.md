---
title: "컴파일러 오류 C2914 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2914
dev_langs:
- C++
helpviewer_keywords:
- C2914
ms.assetid: fc6a0592-f53e-4f5a-88cb-780bbed4acf2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fb24322ef9b5aed8c5e6b4079468645e19c2714
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2914"></a>컴파일러 오류 C2914
'identifier': 함수 인수가 모호 하기 때문에 따라 형식 인수를 추론할 수 없습니다  
  
 컴파일러는 제네릭 또는 템플릿 인수에 사용할 함수를 오버 로드 된 확인할 수 없습니다.  
  
 다음 샘플에서는 C2914 오류가 생성 됩니다.  
  
```  
// C2914.cpp  
// compile with: /c  
void f(int);  
void f(double);  
template<class T> void g(void (*) (T));  
void h() { g(f); }   // C2914  
// try the following line instead  
// void h() { g<int>(f); }  
```  
  
 C2914는 제네릭을 사용 하는 경우에 발생할 수 있습니다.  다음 샘플에서는 C2914 오류가 생성 됩니다.  
  
```  
// C2914b.cpp  
// compile with: /clr /c  
void f(int);  
void f(double);  
  
template<class T>   
void gf(void (*) (T));  
  
void h() { gf(f);}   // C2914  
// try the following line instead  
void h() { gf<int>(f); }  
```