---
title: "컴파일러 오류 C2979 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2979
dev_langs:
- C++
helpviewer_keywords:
- C2979
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de9cff3ec44bc0a44055264f6aab0b54ca5f543e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2979"></a>컴파일러 오류 C2979
제네릭에서는 명시적 특수화가 지원되지 않습니다.  
  
 제네릭 클래스가 잘못 선언되었습니다.  참조 [제네릭](../../windows/generics-cpp-component-extensions.md) 자세한 정보에 대 한 합니다.  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2979를 생성합니다.  
  
```  
// C2979.cpp  
// compile with: /clr /c  
generic <>   
ref class Utils {};   // C2979 error  
  
generic <class T>  
ref class Utils2 {};   // OK  
```