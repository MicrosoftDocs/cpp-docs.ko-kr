---
title: "컴파일러 오류 C2957 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2957
dev_langs:
- C++
helpviewer_keywords:
- C2957
ms.assetid: 9cb4526f-4af8-47e9-b786-56192627ca72
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53a9532904165446f726bd32df6ddab4d3975aed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2957"></a>컴파일러 오류 C2957
'delim': 왼쪽 구분 기호가 잘못되었습니다. '<'가 필요합니다.  
  
 제네릭 클래스의 형식이 잘못되었습니다.  
  
 다음 샘플에서는 C2957을 생성합니다.  
  
```  
// C2957.cpp  
// compile with: /clr /LD  
generic << class T>   // C2957  
// try the following line instead  
// generic < class T>  
gc class C {};  
```