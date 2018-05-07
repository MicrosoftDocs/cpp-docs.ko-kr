---
title: 컴파일러 경고 C4485 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4485
dev_langs:
- C++
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b84d2976e31d5cc3a9b6547d0c4b02a61327ce0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4485"></a>컴파일러 경고 C4485
'override_function': 기본 ref 클래스 메서드 'base_class_function'와 일치 하지 않으면이 '표시 된 new' 또는 'override'; 'new' (및 'virtual') 가정  
  
 재정의 하거나 사용 하지 않고는 `virtual` 키워드, 기본 클래스 접근자 함수를 되지만 `override` 또는 `new` 지정자 재정의 함수 서명의 일부가 아니었습니다. 추가 `new` 또는 `override` 이 경고를 해결 하려면 지정자입니다.  
  
 참조 [재정의](../../windows/override-cpp-component-extensions.md) 및 [new (의 new 슬롯 vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md) 자세한 정보에 대 한 합니다.  
  
 C4485은 항상 오류로 실행 됩니다. 사용 하 여는 [경고](../../preprocessor/warning.md) pragma C4485 표시를 합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```