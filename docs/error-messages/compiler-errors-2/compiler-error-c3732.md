---
title: "컴파일러 오류 C3732 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3732
dev_langs:
- C++
helpviewer_keywords:
- C3732
ms.assetid: 2d55a7e1-9c39-4379-a093-2f7beb27e2ca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c6c0e4b2b5fc97bfabea0b059c89d2abff8b901
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3732"></a>컴파일러 오류 C3732
'interface': COM 이벤트를 발생 시키는 사용자 지정 인터페이스는 IDispatch에서 상속할 수 없습니다  
  
 지 원하는 COM 이벤트 인터페이스에서 상속할 수 없습니다 `IDispatch`합니다. 자세한 내용은 참조 [COM에서 이벤트 처리](../../cpp/event-handling-in-com.md)합니다.  
  
 다음 오류 C3732를 생성합니다.  
  
```  
// C3732.cpp  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="test")];  
  
// to resolve this C3732, use dual instead of object  
// or inherit from IUnknown  
[ object ]  
__interface I : IDispatch  
{  
};  
  
[ event_source(com), coclass ]  
struct A  
{  
   __event __interface I;   // C3732  
};  
  
int main()  
{  
}  
```