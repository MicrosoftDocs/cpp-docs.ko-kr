---
title: "컴파일러 오류 C2842 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47130ec2bf73889130d64f3ca8411bbc38dabf93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2842"></a>컴파일러 오류 C2842
'class' : 관리되는 형식 또는 WinRT 형식은 고유한 'operator new' 또는 'operator delete'를 정의할 수 없습니다.  
  
 직접 정의할 수 있습니다 * * 연산자 new 또는 **delete 연산자** 네이티브 힙에 메모리 할당을 관리할 수 있습니다. 그러나 참조 클래스는 관리되는 힙에만 할당되기 때문에 이러한 연산자를 정의할 수 없습니다.  

  
 자세한 내용은 참조 [사용자 정의 연산자 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)합니다.  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2842 오류가 발생하는 경우를 보여 줍니다.  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  
