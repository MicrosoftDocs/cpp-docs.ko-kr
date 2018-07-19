---
title: nested_scheduler_missing_detach 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
dev_langs:
- C++
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26027693209bc5b4687686efeae5d190ed374607
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687363"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach 클래스
이 클래스는 동시성 런타임에서 `Scheduler` 개체의 `Attach` 메서드를 사용하여 두 번째 스케줄러에 연결된 컨텍스트에 대해 `CurrentScheduler::Detach` 메서드를 호출하지 않은 것을 감지하는 경우 발생하는 예외를 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[nested_scheduler_missing_detach](#ctor)|오버로드됨. `nested_scheduler_missing_detach` 개체를 생성합니다.|  
  
## <a name="remarks"></a>설명  
 이 예외는 다른 스케줄러에서 이미 소유하고 있거나 다른 스케줄러에 연결된 컨텍스트에서 `Attach` 개체의 `Scheduler` 메서드를 호출함으로써 다른 컨텍스트 내에 한 스케줄러를 중첩할 때만 throw됩니다. 동시성 런타임 문제에 도움이 되는 시나리오를 검색할 수 있는 경우 선택적이 예외를 throw 합니다. 호출을 무시 하는 모든 인스턴스가 `CurrentScheduler::Detach` 메서드는 항상이 예외를 throw 합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** concrt.h  
  
 **네임스페이스:** 동시성  
  
##  <a name="ctor"></a> nested_scheduler_missing_detach 

 `nested_scheduler_missing_detach` 개체를 생성합니다.  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `_Message`  
 오류 설명 메시지입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Namespace 동시성](concurrency-namespace.md)   
 [Scheduler 클래스](scheduler-class.md)
