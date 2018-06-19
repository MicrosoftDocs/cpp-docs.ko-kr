---
title: 컴파일러 오류 C2193 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2193
dev_langs:
- C++
helpviewer_keywords:
- C2193
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc5d6a5890a74fbb4f8a70ee86073c257cdf16ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169259"
---
# <a name="compiler-error-c2193"></a>컴파일러 오류 C2193
'identifier': 세그먼트에 이미  
  
 함수를 사용 하 여 두 개의 서로 다른 세그먼트에 배치 된 `alloc_text` 및 `code_seg` pragma입니다.  
  
 다음 샘플에서는 C2193 오류가 생성 됩니다.  
  
```  
// C2193.cpp  
// compile with: /c  
extern "C" void MYFUNCTION();  
#pragma alloc_text(MYCODE, MYFUNCTION)  
#pragma code_seg("MYCODE2")  
extern "C" void MYFUNCTION() {}   // C2193  
extern "C" void MYFUNCTION2() {}  
```