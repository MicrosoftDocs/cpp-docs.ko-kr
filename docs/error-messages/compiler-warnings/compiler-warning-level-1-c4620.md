---
title: "컴파일러 경고 (수준 1) C4620 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4620
dev_langs:
- C++
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f550a857f1799e32d599231348123e3f85a0dfd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4620"></a>컴파일러 경고(수준 1) C4620
'type' 형식에 대한 'operator ++' 후위 형식이 없으므로 전위 형식이 사용됩니다.  
  
 지정된 형식에 대해 정의된 후위 증가 연산자가 없습니다. 컴파일러가 오버로드된 전위 연산자를 사용했습니다.  
  
 이 경고는 후위 `++` 연산자를 정의하여 방지할 수 있습니다. 인수가 두 개인 버전의 `++` 연산자를 다음과 같이 만듭니다.  
  
```  
// C4620.cpp  
// compile with: /W1  
class A  
{  
public:  
   A(int nData) : m_nData(nData)  
   {  
   }  
  
   A operator++()  
   {  
      m_nData -= 1;  
      return *this;  
   }  
  
   // A operator++(int)  
   // {  
   //    A tmp = *this;  
   //    m_nData -= 1;  
   //    return tmp;  
   // }  
  
private:  
   int m_nData;  
};  
  
int main()  
{  
   A a(10);  
   ++a;  
   a++;   // C4620  
}  
```