---
title: 컴파일러 경고 (수준 1) C4052 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4052
dev_langs:
- C++
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5c937e602f14789419f6b124034503c127f6dc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271192"
---
# <a name="compiler-warning-level-1-c4052"></a>컴파일러 경고(수준 1) C4052
함수 선언이 다릅니다. 한쪽에 가변 인수가 들어 있습니다.  
  
 하나의 함수 선언에 변수 인수가 없습니다. 무시됩니다.  
  
 다음 샘플에서는 C4052를 생성합니다.  
  
```  
// C4052.c  
// compile with: /W4 /c  
int f();  
int f(int i, ...);   // C4052  
```