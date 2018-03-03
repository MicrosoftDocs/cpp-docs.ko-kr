---
title: "컴파일러 오류 C2800 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2800
dev_langs:
- C++
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f23c6a4d0a38b800db09125af2401237458a4fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2800"></a>컴파일러 오류 C2800
'operator 연산자'를 오버 로드할 수 없습니다.  
  
 다음과 같은 연산자를 오버 로드할 수 없습니다: 클래스 멤버 액세스 (`.`), 멤버 포인터 (`.*`), 범위 결정 (`::`), 조건식 (`? :`), 및 `sizeof`합니다.  
  
 다음 샘플에서는 C2800 오류가 생성 됩니다.  
  
```  
// C2800.cpp  
// compile with: /c  
class C {  
   operator:: ();   // C2800  
};  
```