---
title: 컴파일러 경고 (수준 3) C4823 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c29499a82601dcf653ff2f003441935f1d6841a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293233"
---
# <a name="compiler-warning-level-3-c4823"></a>컴파일러 경고(수준 3) C4823
'function': 사용 고정 포인터 하지만 해제 의미 체계를 사용할 수 없습니다. /EHa를 사용 하는 것이 좋습니다.  
  
블록 범위에서 선언 된 고정 포인터에 의해 관리 되는 힙에 있는 개체를 제거 하려면 컴파일러의 고정 포인터에 포인터를 무효화 하는 소멸자 "가장" 로컬 클래스의 소멸자는 동작이 시뮬레이션 합니다. 예외를 throw 한 후 소멸자에 대 한 호출을 사용 하려면 설정 해야 개체 해제를 사용 하 여 수행할 수 있는 [/EHsc](../../build/reference/eh-exception-handling-model.md)합니다.  
  
개체를 해제 하 고 경고를 무시 수동으로 있습니다.  
  
## <a name="example"></a>예제  
다음 샘플에서는 C4823 오류가 발생 합니다.  
  
```  
// C4823.cpp  
// compile with: /clr /W3 /EHa-  
using namespace System;  
  
ref struct G {  
   int m;  
};  
  
void f(G ^ pG) {  
   try {  
      pin_ptr<int> p = &pG->m;  
      // manually unpin, ignore warning  
      // p = nullptr;  
      throw gcnew Exception;  
   }  
   catch(Exception ^) {}  
}   // C4823 warning  
  
int main() {  
   f( gcnew G );  
}  
```  
