---
title: 컴파일러 경고 (수준 1) C4273 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4273
dev_langs:
- C++
helpviewer_keywords:
- C4273
ms.assetid: cc18611d-9454-40a4-ad73-69823d5888fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f37a9a2337c9f6a96091f9972b0308965c2bdc3c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4273"></a>컴파일러 경고(수준 1) C4273
'function': DLL 링크가 일치 하지 않습니다  
  
 두 개의 정의 파일에 서로 다르게 사용의 [dllimport](../../cpp/dllexport-dllimport.md)합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4273 오류가 발생 합니다.  
  
```  
// C4273.cpp  
// compile with: /W1 /c  
char __declspec(dllimport) c;  
char c;   // C4273, delete this line or the line above to resolve  
```  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4273 오류가 발생 합니다.  
  
```  
// C4273_b.cpp  
// compile with: /W1 /clr /c  
#include <stdio.h>  
extern "C" int printf_s(const char *, ...);   // C4273  
```