---
title: "컴파일러 오류 C2128 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- c2128
dev_langs:
- C++
helpviewer_keywords:
- C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8d8c1b06f03b8e4f4e26f3bb2dc3818d4576463
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2128"></a>컴파일러 오류 C2128
'function': alloc_text/same_seg는 C 링크가 있는 함수에만 적용  
  
 `pragma``alloc_text` 는 C 링크를 사용 하도록 선언 된 함수 에서만 사용할 수 있습니다.  
  
 다음 샘플에서는 생성 C2128 됩니다.  
  
```  
// C2128.cpp  
// compile with: /c  
  
// Delete the following line to resolve.  
void func();  
// #pragma alloc_text("my segment", func)   // C2128  
  
extern "C" {  
void func();  
}  
  
#pragma alloc_text("my segment", func)  
void func() {}  
```