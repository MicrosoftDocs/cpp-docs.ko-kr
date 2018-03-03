---
title: "가상 (c + +) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 041939197f18861d27d1f99708e27415de2b7787
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="virtual-c"></a>virtual (C++)
`virtual` 키워드는 가상 함수 또는 가상 기본 클래스를 선언합니다.  
  
## <a name="syntax"></a>구문  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>매개 변수  
 `type-specifiers`  
 가상 멤버 함수의 반환 형식을 지정합니다.  
  
 `member-function-declarator`  
 멤버 함수를 선언합니다.  
  
 `access-specifier`  
 기본 클래스 `public`, `protected` 또는 `private`에 대한 액세스 수준을 정의합니다. `virtual` 키워드 앞이나 뒤에 나타날 수 있습니다.  
  
 `base-class-name`  
 이전에 선언된 클래스 형식을 식별합니다.  
  
## <a name="remarks"></a>설명  
 참조 [가상 함수](../cpp/virtual-functions.md) 자세한 정보에 대 한 합니다.  
  
 또한 다음 키워드를 참조 하십시오: [클래스](../cpp/class-cpp.md), [개인](../cpp/private-cpp.md), [공용](../cpp/public-cpp.md), 및 [보호](../cpp/protected-cpp.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [키워드](../cpp/keywords-cpp.md)