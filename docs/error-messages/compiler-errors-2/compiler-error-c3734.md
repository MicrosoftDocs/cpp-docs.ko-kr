---
title: 컴파일러 오류 C3734 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3734
dev_langs:
- C++
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af0b27f449e61d6b80ad2d19eb09a3a55c5f3ad1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264196"
---
# <a name="compiler-error-c3734"></a>컴파일러 오류 C3734
'class': 관리되는 클래스 또는 WinRT 클래스에는 coclass를 사용할 수 없습니다.  
  
 [coclass](../../windows/coclass.md) 특성은 함께 사용할 수 없습니다 관리 되는 또는 WinRT 클래스입니다.  
  
 다음 샘플에서는 C3734를 생성하고 해결 방법을 보여 줍니다.  
  
```  
// C3734.cpp  
// compile with: /clr /c  
[module(name="x")];  
  
[coclass]  
ref class CMyClass {   // C3734 remove the ref keyword to resolve  
};  
```  
