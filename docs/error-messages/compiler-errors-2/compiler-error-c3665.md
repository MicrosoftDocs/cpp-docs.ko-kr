---
title: 컴파일러 오류 C3665 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C3665
dev_langs:
- C++
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7a8b5a93c4ed3a003eb23824e9b7207c7e26f8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3665"></a>컴파일러 오류 C3665
'소멸자': 재정의 지정자는 'keyword' 소멸자/종료자에 사용할 수 없습니다  
  
 소멸자 또는 종료자에 허용 되지 않는 키워드를 사용 했습니다.  
  
 예를 들어, 소멸자 또는 종료자에는 새 슬롯을 요청할 수 없습니다.  자세한 내용은 참조 [명시적으로 재정의](../../windows/explicit-overrides-cpp-component-extensions.md) 및 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)합니다.  
  
 다음 샘플에서는 C3665 오류가 생성 됩니다.  
  
```  
// C3665.cpp  
// compile with: /clr  
public ref struct R {  
   virtual ~R() { }  
   virtual void a() { }  
};  
  
public ref struct S : R {  
   virtual ~S() new {}   // C3665  
   virtual void a() new {}   // OK  
};  
```