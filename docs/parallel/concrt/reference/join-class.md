---
description: '자세히 알아보기: 조인 클래스'
title: join 클래스
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: 0a160e0a8e12dc9d58c6a9c46dcb99be2ad1999b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132798"
---
# <a name="join-class"></a>join 클래스

`join` 메시징 블록은 각 소스에서 `T` 형식의 메시지를 결합하는 순서가 지정된 단일 대상 다중 소스 `propagator_block`입니다.

## <a name="syntax"></a>구문

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
블록에서 조인 및 전파 되는 메시지의 페이로드 유형입니다.

*_Jtype*<br/>
블록의 종류는 `join` , 또는입니다. `greedy``non_greedy`

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[조인](#ctor)|오버로드됨. `join` 메시징 블록을 생성합니다.|
|[~ join 소멸자](#dtor)|블록을 소멸 시킵니다 `join` .|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[accept_message](#accept_message)|`join`호출자에 게 소유권을 전송 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.|
|[consume_message](#consume_message)|메시징 블록에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `join` 호출자에 게 소유권을 전송 합니다.|
|[link_target_notification](#link_target_notification)|새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `join` .|
|[propagate_message](#propagate_message)|`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `join` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[propagate_to_any_targets](#propagate_to_any_targets)|모든 메시지가 메시지를 전파 했을 때 각 소스에서 입력 메시지를 포함 하는 출력 메시지를 생성 합니다. 이 출력 메시지를 각 대상으로 보냅니다.|
|[release_message](#release_message)|이전 메시지 예약을 해제 합니다. [Source_block:: release_message](source-block-class.md#release_message)를 재정의 합니다.|
|[reserve_message](#reserve_message)|이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `join` 합니다. [Source_block:: reserve_message](source-block-class.md#reserve_message)를 재정의 합니다.|
|[resume_propagation](#resume_propagation)|예약이 해제 된 후 전파를 다시 시작 합니다. [Source_block:: resume_propagation](source-block-class.md#resume_propagation)를 재정의 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

`join`호출자에 게 소유권을 전송 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

메시징 블록에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `join` 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 사용 되는 개체의입니다.

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

와 비슷하지만 `accept` 항상를 호출 `reserve` 합니다.

## <a name="join"></a><a name="ctor"></a> 조인

`join` 메시징 블록을 생성합니다.

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>매개 변수

*_NumInputs*<br/>
이 블록이 허용 되는 입력 수입니다 `join` .

*_Filter*<br/>
제공 된 메시지를 수락 해야 하는지 여부를 결정 하는 필터 함수입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `join` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `join` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

형식은 `filter_method` `bool (T const &)` 제공 된 메시지를 `join` 수락 해야 하는지 여부를 확인 하기 위해이 메시징 블록에 의해 호출 되는 시그니처가 포함 된 함수입니다.

## <a name="join"></a><a name="dtor"></a> ~ 조인

블록을 소멸 시킵니다 `join` .

```cpp
~join();
```

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `join` .

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `join` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

```cpp
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md) 입니다.

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a> propagate_to_any_targets

모든 메시지가 메시지를 전파 했을 때 각 소스에서 입력 메시지를 포함 하는 출력 메시지를 생성 합니다. 이 출력 메시지를 각 대상으로 보냅니다.

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
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

이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `join` 합니다.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

### <a name="return-value"></a>반환 값

**`true`** 메시지가 성공적으로 예약 되었으면이 고, **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

가 호출 된 후를 `reserve` 반환 하면 **`true`** 또는을 `consume` `release` 호출 하 여 메시지의 소유권을 가져오거나 해제 해야 합니다.

## <a name="resume_propagation"></a><a name="resume_propagation"></a> resume_propagation

예약이 해제 된 후 전파를 다시 시작 합니다.

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[choice 클래스](choice-class.md)<br/>
[multitype_join 클래스](multitype-join-class.md)
