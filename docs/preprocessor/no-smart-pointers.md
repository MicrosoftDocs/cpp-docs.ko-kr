---
title: no_smart_pointers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 345da5de492c33107effffb9c97b2fe60906e899
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42545854"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**C + + 전용**  
  
형식 라이브러리의 모든 인터페이스에 대한 스마트 포인터를 만들지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```  
no_smart_pointers  
```  
  
## <a name="remarks"></a>설명  
 
`#import`를 사용하는 경우 기본적으로 형식 라이브러리에 있는 모든 인터페이스에 대한 스마트 포인터 선언을 가져옵니다. 이러한 스마트 포인터는 형식이 [_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)합니다.  
  
**C + + 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 
[#import 특성](../preprocessor/hash-import-attributes-cpp.md)   
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)