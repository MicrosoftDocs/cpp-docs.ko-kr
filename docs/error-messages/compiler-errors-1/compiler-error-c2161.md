---
title: 컴파일러 오류 C2161 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2161
dev_langs:
- C++
helpviewer_keywords:
- C2161
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62ea3ec8d0d4ac4cb47f61d23473b1faabc3a894
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2161"></a>컴파일러 오류 C2161
매크로 정의 끝에 '##'이 올 수 없습니다.  
  
 매크로 정의가 토큰 붙여넣기 연산자(##)로 종료되었습니다.  
  
 다음 샘플에서는 C2161 오류가 발생하는 경우를 보여 줍니다.  
  
```  
// C2161.cpp  
// compile with: /c  
#define mac(a,b) a   // OK  
#define mac(a,b) a##   // C2161  
```