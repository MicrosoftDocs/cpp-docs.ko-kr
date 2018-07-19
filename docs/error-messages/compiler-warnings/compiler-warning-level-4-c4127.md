---
title: 컴파일러 경고 (수준 4) C4127 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c98b2eb42cfc66c27faf74c3d6e46e981851a0a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293649"
---
# <a name="compiler-warning-level-4-c4127"></a>컴파일러 경고(수준 4) C4127
조건식이 상수입니다.  
  
 `if` 문 또는 `while` 루프의 제어 식이 상수로 계산됩니다. 일반적인 관용구 사용 trivial 상수 1 등으로 인해 또는 `true` 식에서 연산의 결과 있지 않은 경우 경고를 트리거하지 않습니다. 하는 경우의 제어 식이 `while` 중간에서 루프를 종료 하기 때문에 루프는 상수, 교체 하는 것이 좋습니다.는 `while` 루프는 `for` 루프입니다. 초기화, 종료 테스트를 생략 하 고 루프의 증가 `for` 인해 마찬가지로 무한 루프가 있는 루프 `while(1)`, 본문에서 루프를 종료할 수 있습니다는 `for` 문.  
  
 다음 샘플은 두 가지 방법으로 C4127 생성 되 고 사용 하는 방법을 보여 줍니다.는 for 루프는 경고를 방지 하려면:  
  
```  
// C4127.cpp  
// compile with: /W4  
#include <stdio.h>  
int main() {  
   if (1 == 1) {}   // C4127  
   while (42) { break; }   // C4127  
  
   // OK  
   for ( ; ; ) {  
      printf("test\n");  
      break;  
   }  
}  
```