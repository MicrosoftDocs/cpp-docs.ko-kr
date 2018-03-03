---
title: "컴파일러 경고 (수준 4) C4343 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4343
dev_langs:
- C++
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf7ab18e58a7c77da42e6497c39e716b632d2f7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4343"></a>컴파일러 경고(수준 4) C4343
\#pragma optimize("g",off) /Og 옵션을 재정의합니다.  
  
 이 경고는 IPF(Itanium Processor Family) 컴파일러에서만 사용되며 pragma [optimize](../../preprocessor/optimize.md) 가 [/Og](../../build/reference/og-global-optimizations.md) 컴파일러 옵션을 재정의했음을 보고합니다.  
  
 다음 샘플에서는 C4343을 생성합니다.  
  
```  
// C4343.cpp  
// compile with: /Og /W4 /LD  
// processor: IPF  
#pragma optimize ("g", off)   // C4343  
```