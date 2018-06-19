---
title: 컴파일러 오류 C3865 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99a872d4cf7ed285a0798461c77adf904cfa3e71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275501"
---
# <a name="compiler-error-c3865"></a>컴파일러 오류 C3865
'calling_convention': 네이티브 멤버 함수에만 사용할 수  
  
 호출 규칙은 관리 되는 멤버 함수 또는 함수를 전역 함수에 사용 되었습니다. 호출 규칙 (관리 되지 않음) 네이티브 멤버 함수에만 사용할 수 있습니다.  
  
 자세한 내용은 참조 [호출 규칙](../../cpp/calling-conventions.md)합니다.  
  
 다음 샘플에서는 C3865 오류가 생성 됩니다.  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```