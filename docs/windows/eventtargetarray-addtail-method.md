---
title: "Eventtargetarray:: Addtail 메서드 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ff008a60831ccce9a93bc3b4c4df8643db9c541
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail 메서드
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```  
void AddTail(  
   _In_ IUnknown* element  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `element`  
 추가할 이벤트 처리기에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  
 이벤트 처리기의 내부 배열의 끝에 지정된 된 이벤트 처리기를 추가합니다.  
  
 AddTail()는 EventSource 클래스에 의해 내부적으로 사용 되어야 하는 데 사용 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>참고 항목  
 [EventTargetArray 클래스](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)