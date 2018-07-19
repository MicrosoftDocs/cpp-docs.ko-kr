---
title: 컴파일러 오류 C2534 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2534
dev_langs:
- C++
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae52374e09852ffb68c5807353155d9928924eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228248"
---
# <a name="compiler-error-c2534"></a>컴파일러 오류 C2534
'identifier': 생성자는 값을 반환할 수 없습니다  
  
 생성자는 값을 반환 하거나 반환 형식을 가질 수 없습니다 (아니더라도 `void` 반환 형식).  
  
 제거 하 여이 오류를 해결할 수 있습니다는 `return` 생성자 정의에서 문입니다.  
  
 다음 샘플에서는 C2534 오류가 생성 됩니다.  
  
```  
// C2534.cpp  
class A {  
public:  
   int i;  
   A() { return i; }   // C2534  
};  
```