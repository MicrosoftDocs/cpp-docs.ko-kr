---
title: 컴파일러 경고 (수준 4) C4626 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4626
dev_langs:
- C++
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e43aa93a2f40d97ef3db5c2f556b04e84512724
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4626"></a>컴파일러 경고(수준 4) C4626
'derived class' : 기본 클래스의 할당 연산자에 액세스할 수 없거나 이러한 연산자가 삭제되었으므로 할당 연산자가 암시적으로 삭제된 것으로 정의됩니다.  
  
 할당 연산자가 삭제되었거나 기본 클래스에서 액세스할 수 없으므로 파생 클래스에 대해 생성되지 않았습니다. 이 형식의 개체를 할당하려고 하면 컴파일러 오류가 발생합니다.  
  
 기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.  
  
 다음 샘플에서는 C4626 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.  
  
```  
// C4626  
// compile with: /W4  
#pragma warning(default : 4626)  
class B  
{  
// public:  
   B& operator = (const B&)  
   {  
      return *this;  
   }  
};  
  
class D : public B  
{  
  
}; // C4626 - to fix, make B's copy constructor public  
  
int main()  
{  
   D m;  
   D n;  
   // m = n;   // this line will cause an error  
}  
```