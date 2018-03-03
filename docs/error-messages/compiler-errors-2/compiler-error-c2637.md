---
title: "컴파일러 오류 C2637 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2637
dev_langs:
- C++
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5891e09b979b96117772fee9c9fff1cb63c807b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2637"></a>컴파일러 오류 C2637
'identifier': 데이터 멤버에 대 한 포인터를 수정할 수 없습니다  
  
 데이터 멤버에 대 한 포인터는 호출 규칙을 사용할 수 없습니다. 를 해결 하려면 호출 규칙을 제거 하거나 멤버 함수에 대 한 포인터를 선언 합니다.  
  
 다음 샘플에서는 C2637 오류가 생성 됩니다.  
  
```  
// C2637.cpp  
// compile with: /c  
struct S {};  
int __stdcall S::*pms1;   // C2637  
  
// OK  
int S::*pms2;  
int (__stdcall S::*pms3)(...);  
```