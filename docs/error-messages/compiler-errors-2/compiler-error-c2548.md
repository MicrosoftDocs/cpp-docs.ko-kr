---
title: 컴파일러 오류 C2548 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2548
dev_langs:
- C++
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf1edb19170cfe4bac49fbc5108d0d4a7e8be8a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2548"></a>컴파일러 오류 C2548
'class::member': 누락 된 매개 변수 매개 변수에 대 한 기본 매개 변수  
  
 기본 매개 변수 목록에 매개 변수가 없습니다. 매개 변수 목록에서 아무 곳 이나 기본 매개 변수를 제공 하는 경우에 모든 후속 매개 변수에 대 한 기본 매개 변수를 정의 해야 합니다.  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2548 오류가 생성 됩니다.  
  
```  
// C2548.cpp  
// compile with: /c  
void func( int = 1, int, int = 3);  // C2548  
  
// OK  
void func2( int, int, int = 3);  
void func3( int, int = 2, int = 3);  
```