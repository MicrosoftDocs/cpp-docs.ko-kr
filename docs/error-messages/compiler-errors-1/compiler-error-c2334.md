---
title: 컴파일러 오류 C2334 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2334
dev_langs:
- C++
helpviewer_keywords:
- C2334
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff086a9074db3fca2c85427365b4b90d99b17d24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222217"
---
# <a name="compiler-error-c2334"></a>컴파일러 오류 C2334
앞에 예기치 않은 토큰이 있습니다 ': 또는 {'; 명백한 함수 본문을 건너뜁니다.  
  
 다음 샘플에서는 C2334 오류가 발생 합니다. 오류 C2059 이후이 오류가 발생합니다.  
  
```  
// C2334.cpp  
// compile with: /c  
// C2059 expected  
struct s1 {  
   s1   {}   // C2334  
   s1() {}   // OK  
};  
```