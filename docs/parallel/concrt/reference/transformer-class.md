---
description: '자세한 정보: 변환기 클래스'
title: transformer 클래스
ms.date: 11/04/2016
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: 34d937d1be1c3907ea75d0345bb52bcf359d4f34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188133"
---
# <a name="transformer-class"></a>transformer 클래스

`transformer` 메시징 블록은 한 형식의 메시지를 수락하고 다른 형식의 메시지를 개수에 제한 없이 저장할 수 있는 순서가 지정된 단일 대상 다중 소스 `propagator_block`입니다.

## <a name="syntax"></a>구문

```cpp
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

### <a name="parameters"></a>매개 변수

*_Input*<br/>
버퍼에서 허용 하는 메시지의 페이로드 유형입니다.

*_Output*<br/>
버퍼에 의해 저장 및 전파 되는 메시지의 페이로드 유형입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[가](#ctor)|오버로드됨. `transformer` 메시징 블록을 생성합니다.|
|[~ 변환기 소멸자](#dtor)|메시징 블록을 소멸 시킵니다 `transformer` .|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[accept_message](#accept_message)|`transformer`호출자에 게 소유권을 전송 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.|
|[consume_message](#consume_message)|에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `transformer` 호출자에 게 소유권을 전송 합니다.|
|[link_target_notification](#link_target_notification)|새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `transformer` .|
|[propagate_message](#propagate_message)|`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `transformer` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[propagate_to_any_targets](#propagate_to_any_targets)|입력 메시지에 대해 변형기 함수를 실행합니다.|
|[release_message](#release_message)|이전 메시지 예약을 해제 합니다. [Source_block:: release_message](source-block-class.md#release_message)를 재정의 합니다.|
|[reserve_message](#reserve_message)|이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `transformer` 합니다. [Source_block:: reserve_message](source-block-class.md#reserve_message)를 재정의 합니다.|
|[resume_propagation](#resume_propagation)|예약이 해제 된 후 전파를 다시 시작 합니다. [Source_block:: resume_propagation](source-block-class.md#resume_propagation)를 재정의 합니다.|
|[send_message](#send_message)|`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `transformer` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[supports_anonymous_source](#supports_anonymous_source)|`supports_anonymous_source` 메서드를 재정의하여 이 블록이 연결되지 않은 소스에서 제공하는 메시지를 수락할 수 있음을 나타냅니다. [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)을 재정의 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

`transformer`호출자에 게 소유권을 전송 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `transformer` 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 사용 되는 개체의입니다.

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

와 비슷하지만 `accept` 항상를 호출 `reserve` 합니다.

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `transformer` .

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `transformer` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md) 입니다.

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a> propagate_to_any_targets

입력 메시지에 대해 변형기 함수를 실행합니다.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

## <a name="release_message"></a><a name="release_message"></a> release_message

이전 메시지 예약을 해제 합니다.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 해제 되는 개체의입니다.

## <a name="reserve_message"></a><a name="reserve_message"></a> reserve_message

이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `transformer` 합니다.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 예약 되는 개체의입니다.

### <a name="return-value"></a>반환 값

**`true`** 메시지가 성공적으로 예약 되었으면이 고, **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

가 호출 된 후를 `reserve` 반환 하면 **`true`** 또는을 `consume` `release` 호출 하 여 메시지의 소유권을 가져오거나 해제 해야 합니다.

## <a name="resume_propagation"></a><a name="resume_propagation"></a> resume_propagation

예약이 해제 된 후 전파를 다시 시작 합니다.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a><a name="send_message"></a> send_message

`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `transformer` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md) 입니다.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a> supports_anonymous_source

`supports_anonymous_source` 메서드를 재정의하여 이 블록이 연결되지 않은 소스에서 제공하는 메시지를 수락할 수 있음을 나타냅니다.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>반환 값

**`true`** 블록은 제공 된 메시지를 연기 하지 않기 때문입니다.

## <a name="transformer"></a><a name="ctor"></a> 가

`transformer` 메시징 블록을 생성합니다.

```cpp
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>매개 변수

*_Func*<br/>
허용 되는 각 메시지에 대해 호출 되는 함수입니다.

*_PTarget*<br/>
변환기와 연결할 대상 블록에 대 한 포인터입니다.

*_Filter*<br/>
제공 된 메시지를 수락 해야 하는지 여부를 결정 하는 필터 함수입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `transformer` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `transformer` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

형식은 `_Transform_method` `_Output (_Input const &)` 메시지를 `transformer` 처리 하기 위해이 메시징 블록에서 호출 하는 시그니처가 있는 함수입니다.

형식은 `filter_method` `bool (_Input const &)` 제공 된 메시지를 `transformer` 수락 해야 하는지 여부를 확인 하기 위해이 메시징 블록에 의해 호출 되는 시그니처가 포함 된 함수입니다.

## <a name="transformer"></a><a name="dtor"></a> ~ 변환기

메시징 블록을 소멸 시킵니다 `transformer` .

```cpp
~transformer();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[call 클래스](call-class.md)
