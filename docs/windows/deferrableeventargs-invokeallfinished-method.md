---
title: 'Deferrableeventargs:: Invokeallfinished 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1aaaf8c6849b30e26463810ff353234319960048
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished 메서드
지연된 이벤트를 처리하는 모든 처리가 완료되었음을 나타내기 위해 호출됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>설명  
 이벤트 소스 호출한 후이 메서드를 호출 해야 [InvokeAll](../windows/eventsource-invokeall-method.md)합니다. 이 메서드를 호출하면 추가 지연이 수행되지 않고, 수행된 지연이 없을 경우 완료 처리기가 강제로 실행됩니다.  
  
 코드 예제를 참조 하십시오. [DeferrableEventArgs 클래스](../windows/deferrableeventargs-class.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** event.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [DeferrableEventArgs 클래스](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll 메서드](../windows/eventsource-invokeall-method.md)