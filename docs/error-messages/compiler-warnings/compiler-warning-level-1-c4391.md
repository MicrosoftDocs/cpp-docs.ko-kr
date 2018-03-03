---
title: "컴파일러 경고 (수준 1) C4391 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4391
dev_langs:
- C++
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e41234f179a977643f8f44ad1e5fad05e1a2361f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4391"></a>컴파일러 경고(수준 1) C4391
'서명': 내장 함수에 대 한 잘못 된 반환 형식이 'type' 필요 합니다.  
  
 함수 선언에는 컴파일러 내장 함수에 잘못 된 반환 형식이 있습니다. 결과 이미지가 올바르게 실행 되지 않을 수 있습니다.  
  
 이 경고를 해결 하려면 수정 선언 하거나 선언을 삭제 하 고 간단 #include 적절 한 헤더 파일입니다.  
  
 다음 샘플에서는 C4391 오류가 생성 됩니다.  
  
```  
// C4391.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_load_ss(float *p);   // C4391  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```