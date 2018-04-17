---
title: 컴파일러 오류 C2942 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- C2942
dev_langs:
- C++
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3f5a5a8941a1f0cc42127f5bda7d9c97a52bc18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2942"></a>컴파일러 오류 C2942
'class': type-class-id가 함수의 정식 인수로 재정의되었습니다.  
  
 제네릭 또는 템플릿 클래스를 정식 인수로 사용할 수 없습니다. 제네릭 또는 템플릿 클래스의 생성자에 직접 인수를 전달할 수 없습니다.  
  
 다음 샘플에서는 C2942를 생성합니다.  
  
```  
  
// C2942.cpp  
// compile with: /c  
template<class T>  
struct TC {};   
void f(int TC<int>) {}   // C2942  
  
// OK  
struct TC2 {};  
void f(TC2 i) {}  
```  
  
 C2942는 제네릭을 사용하는 경우에도 발생할 수 있습니다.  
  
```  
// C2942b.cpp  
// compile with: /clr /c  
generic<class T>  
ref struct GC {};  
void f(int GC<int>) {}   // C2942  
ref struct GC2 { };  
void f(int GC2) {}  
```