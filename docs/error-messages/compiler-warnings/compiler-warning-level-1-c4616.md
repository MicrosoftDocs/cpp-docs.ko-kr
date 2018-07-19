---
title: 컴파일러 경고 (수준 1) C4616 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4616
dev_langs:
- C++
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cf59fa32b45215cc29c1cc500cc0bef3378b51e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282706"
---
# <a name="compiler-warning-level-1-c4616"></a>컴파일러 경고(수준 1) C4616
\#pragma 경고: 경고 번호 '번호' 올바른 컴파일러 경고가 아닙니다  
  
 에 지정 된 경고 수는 [경고](../../preprocessor/warning.md) pragma를 할당할 수 없습니다. Pragma가 무시 되었습니다.  
  
 다음 샘플에서는 C4616 오류가 생성 됩니다.  
  
```  
// C4616.cpp  
// compile with: /W1 /c  
#pragma warning( disable : 0 )   // C4616  
#pragma warning( disable : 999 )   // OK  
#pragma warning( disable : 4998 )   // OK  
```