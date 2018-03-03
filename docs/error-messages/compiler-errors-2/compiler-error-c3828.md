---
title: "컴파일러 오류 C3828 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3828
dev_langs:
- C++
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5925962e6e4f3792e431f0e86494a8402e30456b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3828"></a>컴파일러 오류 C3828
'object type': WinRTclasses 또는 배치 인수를 관리 하는 인스턴스를 만드는 동안 사용할 수 없습니다  
  
 연산자의 배치 형태를 사용할 수 없습니다 관리 되는 형식 또는 Windows 런타임 형식의 개체를 만들 때 [ref new, gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md) 또는 [새](../../cpp/new-operator-cpp.md)합니다.  
  
 다음 샘플에서는 C3828 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```