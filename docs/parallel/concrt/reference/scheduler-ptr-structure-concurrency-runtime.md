---
title: scheduler_ptr 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 672e4a0dd5f66ab613dde8877915c799d6c4b2f4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686986"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr 구조체
스케줄러에 대한 포인터를 나타냅니다. 이 클래스는 shared_ptr을 사용하는 공유 수명 또는 원시 포인터를 사용하는 일반 참조의 사양을 허용하기 위해 존재합니다.  
  
## <a name="syntax"></a>구문  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[scheduler_ptr::scheduler_ptr](#ctor)|오버로드됨. shared_ptr에서 스케줄러에 대한 스케줄러 포인터를 만듭니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[scheduler_ptr::get](#get)|스케줄러에 대한 원시 포인터를 반환합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[scheduler_ptr::operator bool](#operator_bool)|스케줄러 포인터가 null이 아닌지 여부를 테스트합니다.|  
|[scheduler_ptr::operator-&gt;](#operator_ptr)|포인터처럼 작동합니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `scheduler_ptr`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** pplinterface.h  
  
 **네임스페이스:** 동시성  
  
##  <a name="get"></a>  scheduler_ptr:: get 메서드  
 스케줄러에 대한 원시 포인터를 반환합니다.  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>반환 값  
  
##  <a name="operator_bool"></a>  scheduler_ptr::operator bool   
 스케줄러 포인터가 null이 아닌지 여부를 테스트합니다.  
  
' ' const; 연산자 bool()
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface 연산자 () const;->
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
명시적 scheduler_ptr (std:: shared_ptr < scheduler_interface > 스케줄러);

명시적 scheduler_ptr (_In_opt_ scheduler_interface pScheduler);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)
