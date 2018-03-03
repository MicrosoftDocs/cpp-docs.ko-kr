---
title: "컴파일러 오류 C2053 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2053
dev_langs:
- C++
helpviewer_keywords:
- C2053
ms.assetid: 13324c85-13a8-4996-bd42-a31bfe7ff80f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 491d457447cc9ae6e5f0b66fa915e0aad45b85b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2053"></a>컴파일러 오류 C2053
'identifier': 와이드 문자열이 일치 하지 않습니다.  
  
 와이드 문자열은 호환 되지 않는 형식에 할당 됩니다.  
  
 다음 샘플에서는 C2053 오류가 생성 됩니다.  
  
```  
// C2053.c  
int main() {  
   char array[] = L"Rika";   // C2053  
}  
```