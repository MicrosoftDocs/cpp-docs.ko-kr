---
title: 컴파일러 오류 C2646 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2646
dev_langs:
- C++
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6d4fdd5141c8fafb350110bee838a13b2cd3b1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2646"></a>컴파일러 오류 C2646
전역 또는 네임스페이스 범위의 익명 구조체 또는 공용 구조체는 static으로 선언해야 합니다.  
  
 익명 구조체 또는 공용 구조체가 전역 또는 네임스페이스 범위를 가지지만 `static`으로 선언되지 않았습니다.  
  
 다음 샘플에서는 C2646 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.  
  
```  
// C2646.cpp  
// compile with: /c  
union { int i; };   // C2646 not static  
  
// OK  
static union { int j; };  
union U { int i; };  
```