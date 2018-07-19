---
title: 컴파일러 경고 (수준 4) C4740 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4740
dev_langs:
- C++
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6260a923da9f48b869707480d64f9be13ef7e9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293311"
---
# <a name="compiler-warning-level-4-c4740"></a>컴파일러 경고(수준 4) C4740
내부 / 외부로 인라인 asm 코드 흐름을 선택 하면 전역 최적화  
  
 또는의 점프 경우는 `asm` 블록, 해당 함수에 대 한 전역 최적화가 해제 됩니다.  
  
 다음 샘플에서는 C4740 오류가 생성 됩니다.  
  
```  
// C4740.cpp  
// compile with: /O2 /W4  
// processor: x86  
int main() {  
   __asm jmp tester  
   tester:;  
}  
```