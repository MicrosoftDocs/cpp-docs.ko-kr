---
title: 컴파일러 경고 (수준 4) C4681 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4681
dev_langs:
- C++
helpviewer_keywords:
- C4681
ms.assetid: a4e6d85f-3e21-4b45-a551-c23d3c554d3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fea1628ec77294ff6698e123b2c199cad2a17596
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295365"
---
# <a name="compiler-warning-level-4-c4681"></a>컴파일러 경고(수준 4) C4681
'class': coclass가 이벤트 소스인 기본 인터페이스를 지정하지 않습니다.  
  
 클래스에 대한 [소스](../../windows/source-cpp.md) 인터페이스를 지정하지 않았습니다.  
  
 다음 샘플에서는 C4681을 생성합니다.  
  
```  
// C4681.cpp  
// compile with: /W4 /c  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[module(name="test")];  
  
[dual, uuid("00000000-0000-0000-0000-000000000000")]  
__interface IEvent { [id(3)] HRESULT myEvent(); };  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface ISource { HRESULT Fire(); };  
  
[ coclass,   
  source(IEvent),   
  default(ISource),  
  // Uncomment the following line to resolve.  
  // default(IEvent),   
  uuid("00000000-0000-0000-0000-000000000002")   
]  
struct CSource : ISource {   // C4681  
   HRESULT Fire() { return 0; }  
};  
```