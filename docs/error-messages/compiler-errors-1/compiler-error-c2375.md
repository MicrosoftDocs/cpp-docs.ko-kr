---
title: 컴파일러 오류 C2375 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2375
dev_langs:
- C++
helpviewer_keywords:
- C2375
ms.assetid: 193c5e8b-1b20-4928-8a02-8c1cddaf2a26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b0d6d3ecda2bd996e7ef53ff5fd0eed6290e2b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2375"></a>컴파일러 오류 C2375
'function': 재정의. 링크가 다릅니다.  
  
 함수가 다른 링크 지정자를 사용하여 이미 선언되었습니다.  
  
 다음 샘플에서는 C2375를 생성합니다.  
  
```  
// C2375.cpp  
// compile with: /Za /c  
extern void func( void );  
static void func( void );   // C2375  
static void func2( void );   // OK  
```