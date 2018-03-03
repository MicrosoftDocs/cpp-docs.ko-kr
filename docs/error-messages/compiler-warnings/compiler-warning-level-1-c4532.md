---
title: "컴파일러 경고 (수준 1) C4532 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4532
dev_langs:
- C++
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44aae61190b20bf1ef93b586c02e88837d487324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4532"></a>컴파일러 경고(수준 1) C4532
'계속': 종료 처리 하는 동안 __finally/finally 블록 밖으로 점프 동작이 정의 되지 않았습니다  
  
 컴파일러는 다음 키워드 중 하나가 발생 했습니다.  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 점프를 일으키는 [__finally](../../cpp/try-finally-statement.md) 또는 [마지막](../../dotnet/finally.md) 비정상적으로 종료 하는 동안 차단 합니다.  
  
 예외가 발생 하 고 종료 처리기를 실행 하는 동안 스택이 되는 동안 (의 `__finally` 또는 finally 블록), 코드 외부로 점프 및는 `__finally` 되기까지 차단는 `__finally` 블록 끝 동작이 정의 되지 않습니다. 제어 되므로 예외가 제대로 처리 되지 해제 코드를 반환 하지 않을 수 있습니다.  
  
 외부로 이동할 해야 하는 경우는 **__finally** 차단, 비정상적인 종료를 먼저 확인 합니다.  
  
 다음 샘플에서는 C4532; 주석으로 처리 하는 경고를 해결 하려면 점프 문에 합니다.  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```