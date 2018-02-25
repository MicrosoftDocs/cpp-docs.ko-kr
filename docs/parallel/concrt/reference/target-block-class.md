---
title: "target_block 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2827e7bbb9a2c23804d90ccb729e990b84f3a442
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="targetblock-class"></a>target_block 클래스
`target_block` 클래스는 대상 전용 블록에 대해 기본 링크 관리 기능 및 오류 검사를 제공하는 추상 기본 클래스입니다.  
  
## <a name="syntax"></a>구문  
  
```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>매개 변수  
 `_SourceLinkRegistry`  
 소스 링크를 저장에 사용할 링크 레지스트리에서 합니다.  
  
 `_MessageProcessorType`  
 메시지 처리에 대 한 프로세서 종류입니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-typedefs"></a>공용 Typedefs  
  
|이름|설명|  
|----------|-----------------|  
|`source_iterator`|에 대 한 반복기의 형식에서 `source_link_manager` 이 `target_block` 개체입니다.|  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[target_block](#ctor)|`target_block` 개체를 생성합니다.|  
|[~ target_block 소멸자](#dtor)|소멸 된 `target_block` 개체입니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[propagate](#propagate)|소스 블록에서이 대상 블록에 메시지를 비동기적으로 전달 합니다.|  
|[send](#send)|소스 블록에서이 대상 블록에 메시지를 동기적으로 전달 합니다.|  
  
### <a name="protected-methods"></a>보호된 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[async_send](#async_send)|비동기적으로 처리를 위한 메시지를 보냅니다.|  
|[decline_incoming_messages](#decline_incoming_messages)|새 메시지가 거부 되어야 하는 블록을 나타냅니다.|  
|[enable_batched_processing](#enable_batched_processing)|이 블록에 대한 일괄 처리를 할 수 있도록 합니다.|  
|[initialize_target](#initialize_target)|기준 개체를 초기화합니다. 특히,는 `message_processor` 개체를 초기화 해야 합니다.|  
|[link_source](#link_source)|이 지정 된 소스 블록에 연결 `target_block` 개체입니다.|  
|[process_input_messages](#process_input_messages)|입력으로 받은 메시지를 처리합니다.|  
|[process_message](#process_message)|파생 클래스에 재정의된 경우 이 `target_block` 개체가 수락했던 메시지를 처리합니다.|  
|[propagate_message](#propagate_message)|파생된 클래스에서 재정의 되 면이 메서드에서 메시지를 비동기적으로 전달 된 `ISource` 이 블록 `target_block` 개체입니다. 이 호출 하는 `propagate` 소스 블록에서 호출 될 경우이 메서드.|  
|[register_filter](#register_filter)|받은 모든 메시지에 대해 호출 되는 필터 메서드를 등록 합니다.|  
|[remove_sources](#remove_sources)|처리 중인 비동기 보내기 작업이 완료 될 때까지 기다린 후 모든 원본 연결을 끊습니다.|  
|[send_message](#send_message)|파생된 클래스에서 재정의 되 면이 메서드에서 메시지를 동기적으로 전달 된 `ISource` 이 블록 `target_block` 개체입니다. 이 호출 하는 `send` 소스 블록에서 호출 될 경우이 메서드.|  
|[sync_send](#sync_send)|동기적으로 처리를 위한 메시지를 보냅니다.|  
|[unlink_source](#unlink_source)|이 지정 된 소스 블록을 연결 해제 `target_block` 개체입니다.|  
|[unlink_sources](#unlink_sources)|모든 소스 블록에서이 연결을 해제 `target_block` 개체입니다. (재정의 [itarget:: Unlink_sources](itarget-class.md#unlink_sources).)|  
|[wait_for_async_sends](#wait_for_async_sends)|모든 비동기 전파가 완료 될 때까지 기다립니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [ITarget](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** agents.h  
  
 **네임스페이스:** 동시성  
  
##  <a name="async_send"></a> async_send 

 비동기적으로 처리를 위한 메시지를 보냅니다.  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PMessage`  
 보내는 메시지에 대 한 포인터입니다.  
  
##  <a name="decline_incoming_messages"></a> decline_incoming_messages 

 새 메시지가 거부 되어야 하는 블록을 나타냅니다.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>설명  
 이 메서드는 소멸 진행 중인 동안 새로운 메시지가 거부 되도록 소멸자에 의해 호출 됩니다.  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing 

 이 블록에 대한 일괄 처리를 할 수 있도록 합니다.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_target"></a> initialize_target 

 기준 개체를 초기화합니다. 특히,는 `message_processor` 개체를 초기화 해야 합니다.  
  
```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PScheduler`  
 작업을 예약 하는 데 사용할 스케줄러입니다.  
  
 `_PScheduleGroup`  
 작업을 예약 하는 데 사용할 수 있는 일정 그룹입니다.  
  
##  <a name="link_source"></a> link_source 

 이 지정 된 소스 블록에 연결 `target_block` 개체입니다.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PSource`  
 에 대 한 포인터는 `ISource` 블록 연결 되어야 하는 것입니다.  
  
### <a name="remarks"></a>설명  
 이 함수에서 직접 호출할 수 없습니다는 `target_block` 개체입니다. 블록을 사용 하 여 함께 연결할는 `link_target` 메서드를 `ISource` 호출 하는 블록의 `link_source` 해당 대상 메서드.  
  
##  <a name="process_input_messages"></a> process_input_messages 

 입력으로 받은 메시지를 처리합니다.  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PMessage`  
  
##  <a name="process_message"></a> process_message 

 파생 클래스에 재정의된 경우 이 `target_block` 개체가 수락했던 메시지를 처리합니다.  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="propagate"></a> 전파 

 소스 블록에서이 대상 블록에 메시지를 비동기적으로 전달 합니다.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PMessage`  
 `message` 개체에 대한 포인터입니다.  
  
 `_PSource`  
 메시지를 제공 하는 소스 블록에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 A [message_status](concurrency-namespace-enums.md) 메시지로 하기로 하는 대상의 표시 합니다.  
  
### <a name="remarks"></a>설명  
 메서드에서 throw 된 [invalid_argument](../../../standard-library/invalid-argument-class.md) 경우 예외는 `_PMessage` 또는 `_PSource` 매개 변수는 `NULL`합니다.  
  
##  <a name="propagate_message"></a> propagate_message 

 파생된 클래스에서 재정의 되 면이 메서드에서 메시지를 비동기적으로 전달 된 `ISource` 이 블록 `target_block` 개체입니다. 이 호출 하는 `propagate` 소스 블록에서 호출 될 경우이 메서드.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>매개 변수  
 `_PMessage`  
 `message` 개체에 대한 포인터입니다.  
  
 `_PSource`  
 메시지를 제공 하는 소스 블록에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 A [message_status](concurrency-namespace-enums.md) 메시지로 하기로 하는 대상의 표시 합니다.  
  
##  <a name="register_filter"></a> register_filter 

 받은 모든 메시지에 대해 호출 되는 필터 메서드를 등록 합니다.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>매개 변수  
 `_Filter`  
 필터 메서드입니다.  
  
##  <a name="remove_sources"></a> remove_sources 

 처리 중인 비동기 보내기 작업이 완료 될 때까지 기다린 후 모든 원본 연결을 끊습니다.  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>설명  
 모든 대상 블록 해당 소멸자에서 원본을 제거 하려면이 루틴을 호출 해야 합니다.  
  
##  <a name="send"></a> 보내기 

 소스 블록에서이 대상 블록에 메시지를 동기적으로 전달 합니다.  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PMessage`  
 `message` 개체에 대한 포인터입니다.  
  
 `_PSource`  
 메시지를 제공 하는 소스 블록에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 A [message_status](concurrency-namespace-enums.md) 메시지로 하기로 하는 대상의 표시 합니다.  
  
### <a name="remarks"></a>설명  
 메서드에서 throw 된 [invalid_argument](../../../standard-library/invalid-argument-class.md) 경우 예외는 `_PMessage` 또는 `_PSource` 매개 변수는 `NULL`합니다.  
  
 사용 하 여 `send` 메시지 시작 외부 및 네트워크 내에서 메시지를 전파 하는 것은 위험 메서드와 교착 상태가 발생할 수 있습니다.  
  
 때 `send` 반환 메시지에 이미 허용 되었으며 대상 블록으로 전송 또는 대상에 의해 거부 되었습니다.  
  
##  <a name="send_message"></a> send_message 

 파생된 클래스에서 재정의 되 면이 메서드에서 메시지를 동기적으로 전달 된 `ISource` 이 블록 `target_block` 개체입니다. 이 호출 하는 `send` 소스 블록에서 호출 될 경우이 메서드.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>반환 값  
 A [message_status](concurrency-namespace-enums.md) 메시지로 하기로 하는 대상의 표시 합니다.  
  
### <a name="remarks"></a>설명  
 기본적으로이 블록 반환 `declined` 파생된 클래스에서 재정의 되지 않는 경우.  
  
##  <a name="sync_send"></a> sync_send 

 동기적으로 처리를 위한 메시지를 보냅니다.  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PMessage`  
 보내는 메시지에 대 한 포인터입니다.  
  
##  <a name="ctor"></a> target_block 

 `target_block` 개체를 생성합니다.  
  
```
target_block();
```  
  
##  <a name="dtor"></a> ~target_block 

 소멸 된 `target_block` 개체입니다.  
  
```
virtual ~target_block();
```  
  
##  <a name="unlink_source"></a> unlink_source 

 이 지정 된 소스 블록을 연결 해제 `target_block` 개체입니다.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PSource`  
 에 대 한 포인터는 `ISource` 블록 연결을 끊을 하는 것입니다.  
  
##  <a name="unlink_sources"></a> unlink_sources 

 모든 소스 블록에서이 연결을 해제 `target_block` 개체입니다.  
  
```
virtual void unlink_sources();
```  
  
##  <a name="wait_for_async_sends"></a> wait_for_async_sends 

 모든 비동기 전파가 완료 될 때까지 기다립니다.  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>설명  
 이 메서드는 모든 비동기 작업이 시간 블록을 삭제 하기 전에 완료 했을 수 있도록 메시지 블록 소멸자가 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Namespace 동시성](concurrency-namespace.md)   
 [ITarget 클래스](itarget-class.md)
