---
title: 컴파일러 오류 C2071 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faee56023d14e9b010d1c691af654ffcbc31dc78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169207"
---
# <a name="compiler-error-c2071"></a>컴파일러 오류 C2071
'identifier': 저장소 클래스가 잘못되었습니다  
  
 `identifier` 잘못 된 선언 되었으면 [저장소 클래스](../../c-language/c-storage-classes.md)합니다. 식별자에 대해 둘 이상의 저장소 클래스를 지정하거나 정의가 저장소 클래스 선언과 호환되지 않는 경우 이 오류가 발생할 수 있습니다.  
  
 이 문제를 해결 하려면 식별자의 의도 한 저장소 클래스를 이해-예를 들어 `static` 또는 `extern`-선언에 맞게 수정 합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C2071 오류가 발생하는 경우를 보여 줍니다.  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C2071 오류가 발생하는 경우를 보여 줍니다.  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```