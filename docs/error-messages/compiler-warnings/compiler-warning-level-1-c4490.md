---
title: 컴파일러 경고 (수준 1) C4490 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4490
dev_langs:
- C++
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baf6c10d50b9b6dd7a41df195dd0b1e39683c98c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4490"></a>컴파일러 경고(수준 1) C4490
'override': 재정의 지정자;의 잘못 된 사용 'function' 기본 ref 클래스 메서드를 일치 하지 않습니다.  
  
 재정의 지정자를 잘못 사용 했습니다. 예를 들어 인터페이스 함수를 재정의 하지 않으면를 구현 해야 합니다.  
  
 자세한 내용은 참조 [재정의 지정자](../../windows/override-specifiers-cpp-component-extensions.md)합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4490 오류가 발생 합니다.  
  
```  
// C4490.cpp  
// compile with: /clr /c /W1  
  
interface struct IFace {  
   void Test();  
};  
  
ref struct Class1 : public IFace {  
   virtual void Test() override {}   // C4490  
   // try the following line instead  
   // virtual void Test() {}  
};  
```