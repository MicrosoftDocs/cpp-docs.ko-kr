---
title: 컴파일러 오류 C2499 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2499
dev_langs:
- C++
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6933d27a1f396dc08275c3f5149212be7abeaaf1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2499"></a>컴파일러 오류 C2499
'class': 클래스는 자체 기본 클래스일 수 없습니다  
  
 기본 클래스를 정의 하는 클래스를 지정 하려고 했습니다.  
  
 다음 샘플에서는 C2499 오류가 생성 됩니다.  
  
```  
// C2499.cpp  
// compile with: /c  
class CMyClass : public CMyClass {};   // C2499  
class CMyClass{};   // OK  
```