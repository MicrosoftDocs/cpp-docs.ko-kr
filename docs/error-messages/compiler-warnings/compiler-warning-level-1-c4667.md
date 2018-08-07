---
title: 컴파일러 경고 (수준 1) C4667 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4667
dev_langs:
- C++
helpviewer_keywords:
- C4667
ms.assetid: 5d2b7fe0-4f0e-4cd6-b432-ca02c3d194ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af88dc89fce0d95ec252a9cbca4c7a37955244dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280766"
---
# <a name="compiler-warning-level-1-c4667"></a>컴파일러 경고(수준 1) C4667
'function': 강제 인스턴스화와 일치 하는 정의 된 함수 템플릿이 없습니다  
  
 선언 되지 않은 함수 템플릿을 인스턴스화할 수 없습니다.  
  
 다음 샘플에서는 c4667:  
  
```  
// C4667a.cpp  
// compile with: /LD /W1  
template  
void max(const int &, const int &); // C4667 expected  
```  
  
 이 경고를 방지 하려면 먼저 함수 템플릿을 선언 하십시오.  
  
```  
// C4667b.cpp  
// compile with: /LD  
// Declare the function template  
template<typename T>  
const T &max(const T &a, const T &b) {  
   return (a > b) ? a : b;  
}  
// Then forcibly instantiate it with a desired type ... i.e. 'int'  
//  
template  
const int &max(const int &, const int &);  
```