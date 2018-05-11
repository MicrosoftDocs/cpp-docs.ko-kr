---
title: 컴파일러 경고 C4484 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75531c207f0136f16109b4d69d689b883998aae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4484"></a>컴파일러 경고 C4484
'override_function': 기본 ref 클래스 메서드 'base_class_function'와 일치 하지만 'virtual', 'new' 또는 'override';로 표시 되지 않습니다 'new' (및 'virtual' 아님) 가정  
  
 로 컴파일할 때 **/clr**, 컴파일러는 기본 클래스 함수, 함수는 vtable의 new 슬롯을 암시적으로 재정의 하지 것입니다. 를 해결 하려면 명시적으로 재정의 하는 함수 인지 지정 합니다.  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [new (의 new 슬롯 vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 C4484은 항상 오류로 실행 됩니다. 사용 하 여는 [경고](../../preprocessor/warning.md) pragma C4484 표시를 합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4484 경고가 발생 합니다.  
  
```  
// C4484.cpp  
// compile with: /clr  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : A {  
   void Test() {}   // C4484  
};  
  
// OK  
ref struct C {  
   virtual void Test() {}  
   virtual void Test2() {}  
};  
  
ref struct D : C {  
   virtual void Test() new {}  
   virtual void Test2() override {}  
};  
```