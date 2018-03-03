---
title: "컴파일러 경고 (수준 1) C4096 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3c8fd8e18743a4cf0c9004236ab60bb30219119e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4096"></a>컴파일러 경고 (수준 1) C4096
'a': 인터페이스는 COM 인터페이스; 아닙니다. IDL로 내보내지 않습니다.  
  
 COM 인터페이스 계획 했던 인터페이스 정의 COM 인터페이스로 정의 되지 않았습니다 고 따라서 내보내지지 않습니다 IDL 파일을 합니다.  
  
 참조 [인터페이스 특성](../../windows/interface-attributes.md) 인터페이스는 COM 인터페이스를 나타내는 특성을 목록에 대 한 합니다.  
  
 다음 샘플에서는 C4096 오류가 생성 됩니다.  
  
```  
// C4096.cpp  
// compile with: /W1 /LD  
#include "windows.h"  
[module(name="xx")];  
  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct b : a  
{  
};   // C4096, remove coclass or uncomment object  
```