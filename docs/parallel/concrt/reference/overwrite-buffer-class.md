---
description: Overwrite_buffer 클래스에 대해 자세히 알아보세요.
title: overwrite_buffer 클래스
ms.date: 11/04/2016
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
ms.openlocfilehash: 20acc133a988c145546e680acb394f0cb69307f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271397"
---
# <a name="overwrite_buffer-class"></a>overwrite_buffer 클래스

`overwrite_buffer` 메시징 블록은 한 번에 하나의 메시지를 저장할 수 있는, 순서가 지정된 다중 대상 다중 소스 `propagator_block`입니다. 새 메시지가 이전에 보유한 메시지를 덮어씁니다.

## <a name="syntax"></a>구문

```cpp
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
버퍼에 의해 저장 및 전파 되는 메시지의 페이로드 유형입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[overwrite_buffer](#ctor)|오버로드됨. `overwrite_buffer`메시징 블록을 생성 합니다.|
|[~ overwrite_buffer 소멸자](#dtor)|메시징 블록을 소멸 시킵니다 `overwrite_buffer` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[has_value](#has_value)|이 `overwrite_buffer` 메시징 블록에 아직 값이 있는지 여부를 확인 합니다.|
|[value](#value)|메시징 블록에 저장 되는 메시지의 현재 페이로드에 대 한 참조를 가져옵니다 `overwrite_buffer` .|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[accept_message](#accept_message)|`overwrite_buffer`메시지의 복사본을 호출자에 게 반환 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.|
|[consume_message](#consume_message)|메시징 블록에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `overwrite_buffer` 메시지의 복사본을 호출자에 게 반환 합니다.|
|[link_target_notification](#link_target_notification)|새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `overwrite_buffer` .|
|[propagate_message](#propagate_message)|`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `overwrite_buffer` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[propagate_to_any_targets](#propagate_to_any_targets)|을 `message _PMessage` 이 `overwrite_buffer` 메시징 블록에 배치 하 고 연결 된 모든 대상에 제공 합니다.|
|[release_message](#release_message)|이전 메시지 예약을 해제 합니다. [Source_block:: release_message](source-block-class.md#release_message)를 재정의 합니다.|
|[reserve_message](#reserve_message)|이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `overwrite_buffer` 합니다. [Source_block:: reserve_message](source-block-class.md#reserve_message)를 재정의 합니다.|
|[resume_propagation](#resume_propagation)|예약이 해제 된 후 전파를 다시 시작 합니다. [Source_block:: resume_propagation](source-block-class.md#resume_propagation)를 재정의 합니다.|
|[send_message](#send_message)|`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `overwrite_buffer` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[supports_anonymous_source](#supports_anonymous_source)|`supports_anonymous_source` 메서드를 재정의하여 이 블록이 연결되지 않은 소스에서 제공하는 메시지를 수락할 수 있음을 나타냅니다. [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)을 재정의 합니다.|

## <a name="remarks"></a>설명

`overwrite_buffer`메시징 블록은 저장 된 메시지의 복사본을 각 대상에 전파 합니다.

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

`overwrite_buffer`메시지의 복사본을 호출자에 게 반환 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`overwrite_buffer`메시징 블록은 현재 저장 된 메시지의 소유권을 전송 하는 대신 대상에 메시지의 복사본을 반환 합니다.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

메시징 블록에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `overwrite_buffer` 메시지의 복사본을 호출자에 게 반환 합니다.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 사용 되는 개체의입니다.

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

와 비슷하지만 `accept` 항상를 호출 `reserve` 합니다.

## <a name="has_value"></a><a name="has_value"></a> has_value

이 `overwrite_buffer` 메시징 블록에 아직 값이 있는지 여부를 확인 합니다.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>반환 값

**`true`** 블록에서 값을 받았으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `overwrite_buffer` .

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
새로 연결 된 대상에 대 한 포인터입니다.

## <a name="overwrite_buffer"></a><a name="dtor"></a> ~ overwrite_buffer

메시징 블록을 소멸 시킵니다 `overwrite_buffer` .

```cpp
~overwrite_buffer();
```

## <a name="overwrite_buffer"></a><a name="ctor"></a> overwrite_buffer

`overwrite_buffer`메시징 블록을 생성 합니다.

```cpp
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>매개 변수

*_Filter*<br/>
제공 된 메시지를 수락 해야 하는지 여부를 결정 하는 필터 함수입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `overwrite_buffer` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `overwrite_buffer` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

형식은 `filter_method` `bool (T const &)` 제공 된 메시지를 `overwrite_buffer` 수락 해야 하는지 여부를 확인 하기 위해이 메시징 블록에 의해 호출 되는 시그니처가 포함 된 함수입니다.

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `overwrite_buffer` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

```cpp
virtual message_status propagate_message(
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

을 `message _PMessage` 이 `overwrite_buffer` 메시징 블록에 배치 하 고 연결 된 모든 대상에 제공 합니다.

```cpp
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message`이에서 소유권을 가져온 개체에 대 한 포인터입니다 `overwrite_buffer` .

### <a name="remarks"></a>설명

이 메서드는의 현재 메시지를 `overwrite_buffer` 새로 허용 된 메시지로 덮어씁니다 `_PMessage` .

## <a name="send_message"></a><a name="send_message"></a> send_message

`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `overwrite_buffer` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

```cpp
virtual message_status send_message(
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

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a> supports_anonymous_source

`supports_anonymous_source` 메서드를 재정의하여 이 블록이 연결되지 않은 소스에서 제공하는 메시지를 수락할 수 있음을 나타냅니다.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>반환 값

**`true`** 블록은 제공 된 메시지를 연기 하지 않기 때문입니다.

## <a name="release_message"></a><a name="release_message"></a> release_message

이전 메시지 예약을 해제 합니다.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 해제 되는 개체의입니다.

## <a name="reserve_message"></a><a name="reserve_message"></a> reserve_message

이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `overwrite_buffer` 합니다.

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

## <a name="value"></a><a name="value"></a> 값

메시징 블록에 저장 되는 메시지의 현재 페이로드에 대 한 참조를 가져옵니다 `overwrite_buffer` .

```cpp
T value();
```

### <a name="return-value"></a>반환 값

현재 저장 된 메시지의 페이로드입니다.

### <a name="remarks"></a>설명

에 저장 된 값은 `overwrite_buffer` 이 메서드가 반환 된 후 즉시 변경 될 수 있습니다. 이 메서드는에 현재 저장 된 메시지가 없는 경우 메시지가 도착할 때까지 대기 `overwrite_buffer` 합니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[unbounded_buffer 클래스](unbounded-buffer-class.md)<br/>
[single_assignment 클래스](single-assignment-class.md)
