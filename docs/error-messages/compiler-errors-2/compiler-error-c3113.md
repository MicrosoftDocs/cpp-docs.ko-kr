---
title: 컴파일러 오류 C3113 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3113
dev_langs:
- C++
helpviewer_keywords:
- C3113
ms.assetid: 3afdc668-b29e-474e-9ea3-aa027d42db7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 220f400bd1ce80be039dcd8d572d20fad5da09f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245721"
---
# <a name="compiler-error-c3113"></a>컴파일러 오류 C3113
'structure' 템플릿/제네릭 일 수 없습니다.  
  
 클래스 템플릿 또는 클래스 제네릭을 인터페이스 또는 열거형 확인 하려고 했습니다.  
  
 다음 샘플에서는 C3113 오류가 생성 됩니다.  
  
```  
// C3113.cpp  
// compile with: /c  
template <class T>   
enum E {};   // C3113  
// try the following line instead  
// class MyClass{};  
```