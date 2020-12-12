---
description: Propagator_block 클래스에 대해 자세히 알아보세요.
title: propagator_block 클래스
ms.date: 11/04/2016
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
ms.openlocfilehash: 4dd006829e01f663be20be76a2cc2e0364ef7b38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115263"
---
# <a name="propagator_block-class"></a>propagator_block 클래스

`propagator_block` 클래스는 소스인 동시에 대상인 메시지 블록에 대한 추상 기본 클래스입니다. `source_block` 및 `target_block` 클래스의 기능을 결합합니다.

## <a name="syntax"></a>구문

```cpp
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>매개 변수

*_TargetLinkRegistry*<br/>
대상 링크를 보유 하는 데 사용할 링크 레지스트리입니다.

*_SourceLinkRegistry*<br/>
소스 링크를 포함 하는 데 사용할 링크 레지스트리입니다.

*_MessageProcessorType*<br/>
메시지 처리를 위한 프로세서 유형입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`source_iterator`|이에 대 한 반복기의 형식입니다 `source_link_manager` `propagator_block` .|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[propagator_block](#ctor)|`propagator_block` 개체를 생성합니다.|
|[~ propagator_block 소멸자](#dtor)|`propagator_block` 개체를 제거합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[배포할](#propagate)|소스 블록에서이 대상 블록으로 메시지를 비동기적으로 전달 합니다.|
|[send](#send)|이 블록에 대 한 메시지를 동기적으로 시작 합니다. 블록에서 호출 `ISource` 됩니다. 이 함수가 완료 되 면 메시지는 이미 블록으로 전파 됩니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|새 메시지를 거부 해야 함을 블록에 나타냅니다.|
|[initialize_source_and_target](#initialize_source_and_target)|기본 개체를 초기화 합니다. 특히 개체를 `message_processor` 초기화 해야 합니다.|
|[link_source](#link_source)|지정 된 소스 블록을이 개체에 연결 `propagator_block` 합니다.|
|[process_input_messages](#process_input_messages)|입력된 메시지를 처리합니다. 이는 source_block에서 파생 되는 전파자 블록에만 유용 합니다 ( [source_block::p Rocess_input_messages](source-block-class.md#process_input_messages)재정의).|
|[propagate_message](#propagate_message)|파생 클래스에서 재정의 되는 경우이 메서드는 블록의 메시지를 `ISource` 이 개체에 비동기적으로 전달 `propagator_block` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[register_filter](#register_filter)|수신 되는 모든 메시지에 대해 호출할 필터 메서드를 등록 합니다.|
|[remove_network_links](#remove_network_links)|이 개체에서 모든 원본 및 대상 네트워크 링크를 제거 합니다 `propagator_block` .|
|[send_message](#send_message)|파생 클래스에서 재정의 되는 경우이 메서드는 블록에서이 개체로 동기적으로 메시지를 전달 `ISource` `propagator_block` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[unlink_source](#unlink_source)|이 개체에서 지정 된 소스 블록을 해제 `propagator_block` 합니다.|
|[unlink_sources](#unlink_sources)|이 개체에서 모든 소스 블록을 해제 `propagator_block` 합니다. [ITarget:: unlink_sources](itarget-class.md#unlink_sources)을 재정의 합니다.|

## <a name="remarks"></a>설명

여러 상속을 방지 하기 위해 클래스는 `propagator_block` `source_block` 클래스 및 `ITarget` 추상 클래스에서 상속 됩니다. 클래스의 기능 대부분 `target_block` 은 여기에 복제 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="decline_incoming_messages"></a><a name="decline_incoming_messages"></a> decline_incoming_messages

새 메시지를 거부 해야 함을 블록에 나타냅니다.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>설명

이 메서드는 소멸이 진행 되는 동안 새 메시지가 거부 되도록 소멸자에서 호출 됩니다.

## <a name="initialize_source_and_target"></a><a name="initialize_source_and_target"></a> initialize_source_and_target

기본 개체를 초기화 합니다. 특히 개체를 `message_processor` 초기화 해야 합니다.

```cpp
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>매개 변수

*_PScheduler*<br/>
작업을 예약 하는 데 사용할 스케줄러입니다.

*_PScheduleGroup*<br/>
작업을 예약 하는 데 사용할 일정 그룹입니다.

## <a name="link_source"></a><a name="link_source"></a> link_source

지정 된 소스 블록을이 개체에 연결 `propagator_block` 합니다.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>매개 변수

*_PSource*<br/>
연결 될 블록에 대 한 포인터입니다 `ISource` .

## <a name="process_input_messages"></a><a name="process_input_messages"></a> process_input_messages

입력된 메시지를 처리합니다. source_block에서 파생되는 전파자 블록에만 유용합니다.

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
처리할 메시지에 대 한 포인터입니다.

## <a name="propagate"></a><a name="propagate"></a> 배포할

소스 블록에서이 대상 블록으로 메시지를 비동기적으로 전달 합니다.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md) 입니다.

### <a name="remarks"></a>설명

`propagate`메서드는 연결 된 소스 블록에 의해 대상 블록에서 호출 됩니다. 아직 큐에 대기 중이거나 실행 중이 아닌 경우 메시지를 처리 하는 비동기 작업을 큐에 대기 시킵니다.

메서드는 [](../../../standard-library/invalid-argument-class.md) `_PMessage` 또는 `_PSource` 매개 변수가 인 경우 invalid_argument 예외를 throw 합니다 `NULL` .

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

파생 클래스에서 재정의 되는 경우이 메서드는 블록의 메시지를 `ISource` 이 개체에 비동기적으로 전달 `propagator_block` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md) 입니다.

## <a name="propagator_block"></a><a name="ctor"></a> propagator_block

`propagator_block` 개체를 생성합니다.

```cpp
propagator_block();
```

## <a name="propagator_block"></a><a name="dtor"></a> ~ propagator_block

`propagator_block` 개체를 제거합니다.

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a><a name="register_filter"></a> register_filter

수신 되는 모든 메시지에 대해 호출할 필터 메서드를 등록 합니다.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>매개 변수

*_Filter*<br/>
필터 메서드입니다.

## <a name="remove_network_links"></a><a name="remove_network_links"></a> remove_network_links

이 개체에서 모든 원본 및 대상 네트워크 링크를 제거 합니다 `propagator_block` .

```cpp
void remove_network_links();
```

## <a name="send"></a><a name="send"></a> 보내기

이 블록에 대 한 메시지를 동기적으로 시작 합니다. 블록에서 호출 `ISource` 됩니다. 이 함수가 완료 되 면 메시지는 이미 블록으로 전파 됩니다.

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md) 입니다.

### <a name="remarks"></a>설명

또는 매개 변수가 인 경우이 메서드는 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw `_PMessage` `_PSource` `NULL` 합니다.

## <a name="send_message"></a><a name="send_message"></a> send_message

파생 클래스에서 재정의 되는 경우이 메서드는 블록에서이 개체로 동기적으로 메시지를 전달 `ISource` `propagator_block` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>반환 값

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md) 입니다.

### <a name="remarks"></a>설명

기본적으로이 블록 `declined` 은 파생 클래스에 의해 재정의 되지 않는 한을 반환 합니다.

## <a name="unlink_source"></a><a name="unlink_source"></a> unlink_source

이 개체에서 지정 된 소스 블록을 해제 `propagator_block` 합니다.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>매개 변수

*_PSource*<br/>
연결을 끊을 블록에 대 한 포인터입니다 `ISource` .

## <a name="unlink_sources"></a><a name="unlink_sources"></a> unlink_sources

이 개체에서 모든 소스 블록을 해제 `propagator_block` 합니다.

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[source_block 클래스](source-block-class.md)<br/>
[ITarget 클래스](itarget-class.md)
