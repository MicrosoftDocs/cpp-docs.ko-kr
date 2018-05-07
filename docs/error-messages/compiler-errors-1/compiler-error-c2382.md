---
title: 컴파일러 오류 C2382 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2382
dev_langs:
- C++
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a17a1038e7e5923e0ee7570754d5c146b55a06f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2382"></a>컴파일러 오류 C2382
'function': 재정의. 예외 사양이 다릅니다.  
  
 [/Za](../../build/reference/za-ze-disable-language-extensions.md)아래에서 이 오류는 함수 오버로드가 [예외 사양](../../cpp/exception-specifications-throw-cpp.md)에서만 시도되었음을 나타냅니다.  
  
 다음 샘플에서는 C2382를 생성합니다.  
  
```  
// C2382.cpp  
// compile with: /Za /c  
void f1(void) throw(int) {}  
void f1(void) throw(char) {}   // C2382  
void f2(void) throw(char) {}   // OK  
```