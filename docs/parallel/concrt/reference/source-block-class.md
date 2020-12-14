---
description: Source_block 클래스에 대해 자세히 알아보세요.
title: source_block 클래스
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: dface4f898bad1abf1ba51732f8059e87975fae7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188614"
---
# <a name="source_block-class"></a>source_block 클래스

`source_block` 클래스는 소스 전용 블록에 대한 추상 기본 클래스입니다. 이 클래스는 기본 링크 관리 기능 및 일반적인 오류 검사를 제공합니다.

## <a name="syntax"></a>구문

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>매개 변수

*_TargetLinkRegistry*<br/>
대상 링크를 보유 하는 데 사용할 링크 레지스트리

*_MessageProcessorType*<br/>
메시지 처리를 위한 프로세서 유형입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`target_iterator`|연결 된 대상을 탐색 하는 반복기입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[source_block](#ctor)|`source_block` 개체를 생성합니다.|
|[~ source_block 소멸자](#dtor)|개체를 소멸 시킵니다 `source_block` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[수락할](#accept)|이 개체가 제공한 메시지를 수락 하 여 `source_block` 호출자에 게 소유권을 전송 합니다.|
|[acquire_ref](#acquire_ref)|삭제를 방지 하기 위해이 개체의 참조 횟수를 가져옵니다 `source_block` .|
|[활용](#consume)|이 개체에서 이전에 제공한 메시지를 사용 하 `source_block` 고 대상에 의해 성공적으로 예약 되어 호출자에 게 소유권을 양도 합니다.|
|[link_target](#link_target)|대상 블록을이 개체에 연결 `source_block` 합니다.|
|[릴리스](#release)|이전의 성공적인 메시지 예약을 해제 합니다.|
|[release_ref](#release_ref)|이 개체에 대 한 참조 횟수를 해제 `source_block` 합니다.|
|[두기](#reserve)|이 개체에서 이전에 제공한 메시지를 예약 `source_block` 합니다.|
|[unlink_target](#unlink_target)|이 개체에서 대상 블록을 해제 `source_block` 합니다.|
|[unlink_targets](#unlink_targets)|이 개체에서 모든 대상 블록을 해제 `source_block` 합니다. ( [ISource:: unlink_targets](isource-class.md#unlink_targets)을 재정의 합니다.)|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[accept_message](#accept_message)|파생 클래스에서 재정의 되는 경우 소스에서 제공 된 메시지를 수락 합니다. 메시지 블록은의 유효성을 검사 하 `_MsgId` 고 메시지를 반환 하려면이 메서드를 재정의 해야 합니다.|
|[async_send](#async_send)|비동기 방식으로 메시지를 큐에 대기 시키고 아직 수행 되지 않은 경우 전파 작업을 시작 합니다.|
|[consume_message](#consume_message)|파생 클래스에서 재정의 되는 경우 이전에 예약 된 메시지를 사용 합니다.|
|[enable_batched_processing](#enable_batched_processing)|이 블록에 대한 일괄 처리를 할 수 있도록 합니다.|
|[initialize_source](#initialize_source)|`message_propagator`이 내에서를 초기화 합니다 `source_block` .|
|[link_target_notification](#link_target_notification)|새 대상이이 개체에 연결 되었음을 알리는 콜백입니다 `source_block` .|
|[process_input_messages](#process_input_messages)|입력된 메시지를 처리합니다. source_block에서 파생되는 전파자 블록에만 유용합니다.|
|[propagate_output_messages](#propagate_output_messages)|메시지를 대상으로 전파합니다.|
|[propagate_to_any_targets](#propagate_to_any_targets)|파생 클래스에서 재정의 되는 경우 지정 된 메시지를 연결 된 대상 중 하나 또는 모두에 전파 합니다. 메시지 블록에 대 한 주요 전파 루틴입니다.|
|[release_message](#release_message)|파생 클래스에서 재정의 되는 경우 이전 메시지 예약을 해제 합니다.|
|[remove_targets](#remove_targets)|이 소스 블록의 모든 대상 링크를 제거 합니다. 이를 소멸자에서 호출 해야 합니다.|
|[reserve_message](#reserve_message)|파생 클래스에서 재정의 되는 경우이 개체에서 이전에 제공 된 메시지를 예약 `source_block` 합니다.|
|[resume_propagation](#resume_propagation)|파생 클래스에서 재정의 된 경우 예약이 해제 된 후 전파를 다시 시작 합니다.|
|[sync_send](#sync_send)|아직 수행 하지 않은 경우 메시지를 동기적으로 큐에 대기 시키고 전파 작업을 시작 합니다.|
|[unlink_target_notification](#unlink_target_notification)|대상의 연결이이 개체에서 해제 되었음을 알리는 콜백입니다 `source_block` .|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|모든 비동기 전파 완료 될 때까지 기다립니다. 이 전파자 특정 spin wait는 메시지 블록의 소멸자에 사용 되어 모든 비동기 전파가 블록을 제거 하기 전에 완료할 시간이 있는지 확인 합니다.|

## <a name="remarks"></a>설명

메시지 블록은이 클래스에서 제공 하는 링크 관리 및 동기화를 활용 하기 위해이 블록에서 파생 되어야 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept"></a><a name="accept"></a> 수락할

이 개체가 제공한 메시지를 수락 하 여 `source_block` 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `accept` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

매개 변수가 인 경우 메서드는 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다 `_PTarget` `NULL` .

`accept`이 블록에서 메시지를 제공 하는 동안 대상에서 메서드를 호출 합니다 `ISource` . `propagate` `ITarget` 이 소스가 메시지의 복사본을 만들도록 결정 한 경우 반환 되는 메시지 포인터는 블록의 메서드에 전달 된 것과 다를 수 있습니다.

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

파생 클래스에서 재정의 되는 경우 소스에서 제공 된 메시지를 수락 합니다. 메시지 블록은의 유효성을 검사 하 `_MsgId` 고 메시지를 반환 하려면이 메서드를 재정의 해야 합니다.

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
개체의 런타임 개체 id `message` 입니다.

### <a name="return-value"></a>반환 값

호출자에 게 소유권이 있는 메시지에 대 한 포인터입니다.

### <a name="remarks"></a>설명

소유권을 이전 하려면 원래 메시지 포인터가 반환 되어야 합니다. 소유권을 유지 하려면 메시지 페이로드의 복사본을 만들고 반환 해야 합니다.

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

삭제를 방지 하기 위해이 개체의 참조 횟수를 가져옵니다 `source_block` .

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>설명

이 메서드는 메서드를 실행 하는 `ITarget` 동안이 소스에 연결 되는 개체에 의해 호출 됩니다 `link_target` .

## <a name="async_send"></a><a name="async_send"></a> async_send

비동기 방식으로 메시지를 큐에 대기 시키고 아직 수행 되지 않은 경우 전파 작업을 시작 합니다.

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>매개 변수

*_Msg*<br/>
`message`비동기적으로 보낼 개체에 대 한 포인터입니다.

## <a name="consume"></a><a name="consume"></a> 활용

이 개체에서 이전에 제공한 메시지를 사용 하 `source_block` 고 대상에 의해 성공적으로 예약 되어 호출자에 게 소유권을 양도 합니다.

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`예약 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `consume` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

매개 변수가 인 경우 메서드는 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다 `_PTarget` `NULL` .

매개 변수가 [](bad-target-class.md) `_PTarget` 호출 된 대상을 나타내지 않는 경우 메서드는 bad_target 예외를 throw 합니다 `reserve` .

`consume`메서드는와 유사 `accept` 하지만 항상 `reserve` 반환 되는를 호출 해야 합니다 **`true`** .

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

파생 클래스에서 재정의 되는 경우 이전에 예약 된 메시지를 사용 합니다.

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 사용 되는 개체의입니다.

### <a name="return-value"></a>반환 값

호출자에 게 소유권이 있는 메시지에 대 한 포인터입니다.

### <a name="remarks"></a>설명

와 비슷하지만 `accept` 항상를 호출 `reserve` 합니다.

## <a name="enable_batched_processing"></a><a name="enable_batched_processing"></a> enable_batched_processing

이 블록에 대한 일괄 처리를 할 수 있도록 합니다.

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a><a name="initialize_source"></a> initialize_source

`message_propagator`이 내에서를 초기화 합니다 `source_block` .

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>매개 변수

*_PScheduler*<br/>
작업을 예약 하는 데 사용할 스케줄러입니다.

*_PScheduleGroup*<br/>
작업을 예약 하는 데 사용할 일정 그룹입니다.

## <a name="link_target"></a><a name="link_target"></a> link_target

대상 블록을이 개체에 연결 `source_block` 합니다.

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
`ITarget`이 개체에 연결할 블록에 대 한 포인터 `source_block` 입니다.

### <a name="remarks"></a>설명

매개 변수가 인 경우 메서드는 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다 `_PTarget` `NULL` .

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

새 대상이이 개체에 연결 되었음을 알리는 콜백입니다 `source_block` .

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a><a name="process_input_messages"></a> process_input_messages

입력된 메시지를 처리합니다. source_block에서 파생되는 전파자 블록에만 유용합니다.

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
처리할 메시지에 대 한 포인터입니다.

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a> propagate_output_messages

메시지를 대상으로 전파합니다.

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a> propagate_to_any_targets

파생 클래스에서 재정의 되는 경우 지정 된 메시지를 연결 된 대상 중 하나 또는 모두에 전파 합니다. 메시지 블록에 대 한 주요 전파 루틴입니다.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
전파할 메시지에 대 한 포인터입니다.

## <a name="release"></a><a name="release"></a> 릴리스

이전의 성공적인 메시지 예약을 해제 합니다.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`예약 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `release` .

### <a name="remarks"></a>설명

매개 변수가 인 경우 메서드는 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다 `_PTarget` `NULL` .

매개 변수가 [](bad-target-class.md) `_PTarget` 호출 된 대상을 나타내지 않는 경우 메서드는 bad_target 예외를 throw 합니다 `reserve` .

## <a name="release_message"></a><a name="release_message"></a> release_message

파생 클래스에서 재정의 되는 경우 이전 메시지 예약을 해제 합니다.

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 해제 되는 개체의입니다.

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

이 개체에 대 한 참조 횟수를 해제 `source_block` 합니다.

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 메서드를 호출 하는 대상 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는이 소스에서 연결을 해제 하는 개체에 의해 호출 됩니다 `ITarget` . 소스 블록은 대상 블록에 예약 된 모든 리소스를 해제할 수 있습니다.

## <a name="remove_targets"></a><a name="remove_targets"></a> remove_targets

이 소스 블록의 모든 대상 링크를 제거 합니다. 이를 소멸자에서 호출 해야 합니다.

```cpp
void remove_targets();
```

## <a name="reserve"></a><a name="reserve"></a> 두기

이 개체에서 이전에 제공한 메시지를 예약 `source_block` 합니다.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `reserve` .

### <a name="return-value"></a>반환 값

**`true`** 메시지가 성공적으로 예약 되었으면이 고, **`false`** 그렇지 않으면입니다. 예약은 메시지를 이미 다른 대상이 예약했거나 수락한 경우, 소스에서 예약을 거부한 경우 등과 같은 다양한 이유로 실패할 수 있습니다.

### <a name="remarks"></a>설명

매개 변수가 인 경우 메서드는 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다 `_PTarget` `NULL` .

를 호출한 후에 `reserve` 성공 하면 또는을 호출 `consume` 하 여 `release` 메시지를 각각 소유 하거나 제공 해야 합니다.

## <a name="reserve_message"></a><a name="reserve_message"></a> reserve_message

파생 클래스에서 재정의 되는 경우이 개체에서 이전에 제공 된 메시지를 예약 `source_block` 합니다.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 예약 되는 개체의입니다.

### <a name="return-value"></a>반환 값

**`true`** 메시지가 성공적으로 예약 되었으면이 고, **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

가 호출 된 후를 `reserve` 반환 하면 **`true`** 또는을 `consume` `release` 호출 하 여 메시지의 소유권을 가져오거나 해제 해야 합니다.

## <a name="resume_propagation"></a><a name="resume_propagation"></a> resume_propagation

파생 클래스에서 재정의 된 경우 예약이 해제 된 후 전파를 다시 시작 합니다.

```cpp
virtual void resume_propagation() = 0;
```

## <a name="source_block"></a><a name="ctor"></a> source_block

`source_block` 개체를 생성합니다.

```cpp
source_block();
```

## <a name="source_block"></a><a name="dtor"></a> ~ source_block

개체를 소멸 시킵니다 `source_block` .

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a><a name="sync_send"></a> sync_send

아직 수행 하지 않은 경우 메시지를 동기적으로 큐에 대기 시키고 전파 작업을 시작 합니다.

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>매개 변수

*_Msg*<br/>
`message`동기적으로 보낼 개체에 대 한 포인터입니다.

## <a name="unlink_target"></a><a name="unlink_target"></a> unlink_target

이 개체에서 대상 블록을 해제 `source_block` 합니다.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
`ITarget`이 개체에서 연결을 해제할 블록에 대 한 포인터 `source_block` 입니다.

### <a name="remarks"></a>설명

매개 변수가 인 경우 메서드는 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다 `_PTarget` `NULL` .

## <a name="unlink_target_notification"></a><a name="unlink_target_notification"></a> unlink_target_notification

대상의 연결이이 개체에서 해제 되었음을 알리는 콜백입니다 `source_block` .

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
연결이 해제 된 `ITarget` 블록입니다.

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

이 개체에서 모든 대상 블록을 해제 `source_block` 합니다.

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a><a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends

모든 비동기 전파 완료 될 때까지 기다립니다. 이 전파자 특정 spin wait는 메시지 블록의 소멸자에 사용 되어 모든 비동기 전파가 블록을 제거 하기 전에 완료할 시간이 있는지 확인 합니다.

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[ISource 클래스](isource-class.md)
