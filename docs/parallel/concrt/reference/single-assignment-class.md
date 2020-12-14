---
description: Single_assignment 클래스에 대해 자세히 알아보세요.
title: single_assignment 클래스
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: d01426843f2e9fe1106f7cb68c103c392cdf1ebd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188659"
---
# <a name="single_assignment-class"></a>single_assignment 클래스

`single_assignment` 메시징 블록은 하나의 한 번 쓰기 `message`를 저장할 수 있는, 순서가 지정된 다중 대상 다중 소스 `propagator_block`입니다.

## <a name="syntax"></a>구문

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
버퍼에 의해 저장 및 전파 되는 메시지의 페이로드 유형입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[single_assignment](#ctor)|오버로드됨. `single_assignment` 메시징 블록을 생성합니다.|
|[~ single_assignment 소멸자](#dtor)|메시징 블록을 소멸 시킵니다 `single_assignment` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[has_value](#has_value)|이 `single_assignment` 메시징 블록이 아직 값을 사용 하 여 초기화 되었는지 여부를 확인 합니다.|
|[value](#value)|메시징 블록에 저장 되는 메시지의 현재 페이로드에 대 한 참조를 가져옵니다 `single_assignment` .|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[accept_message](#accept_message)|`single_assignment`메시지의 복사본을 호출자에 게 반환 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.|
|[consume_message](#consume_message)|에서 이전에 제공 하 고 대상에서 예약한 메시지를 사용 하 여 `single_assignment` 메시지의 복사본을 호출자에 게 반환 합니다.|
|[link_target_notification](#link_target_notification)|새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `single_assignment` .|
|[propagate_message](#propagate_message)|`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `single_assignment` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[propagate_to_any_targets](#propagate_to_any_targets)|을 `message _PMessage` 이 `single_assignment` 메시징 블록에 배치 하 고 연결 된 모든 대상에 제공 합니다.|
|[release_message](#release_message)|이전 메시지 예약을 해제 합니다. [Source_block:: release_message](source-block-class.md#release_message)를 재정의 합니다.|
|[reserve_message](#reserve_message)|이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `single_assignment` 합니다. [Source_block:: reserve_message](source-block-class.md#reserve_message)를 재정의 합니다.|
|[resume_propagation](#resume_propagation)|예약이 해제 된 후 전파를 다시 시작 합니다. [Source_block:: resume_propagation](source-block-class.md#resume_propagation)를 재정의 합니다.|
|[send_message](#send_message)|`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `single_assignment` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|

## <a name="remarks"></a>설명

`single_assignment`메시징 블록은 메시지의 복사본을 각 대상으로 전파 합니다.

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

`single_assignment`메시지의 복사본을 호출자에 게 반환 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`single_assignment`메시징 블록은 현재 저장 된 메시지의 소유권을 전송 하는 대신 대상에 메시지의 복사본을 반환 합니다.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

에서 이전에 제공 하 고 대상에서 예약한 메시지를 사용 하 여 `single_assignment` 메시지의 복사본을 호출자에 게 반환 합니다.

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

이 `single_assignment` 메시징 블록이 아직 값을 사용 하 여 초기화 되었는지 여부를 확인 합니다.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>반환 값

**`true`** 블록에서 값을 받았으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `single_assignment` .

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
새로 연결 된 대상에 대 한 포인터입니다.

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `single_assignment` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

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

을 `message` `_PMessage` 이 `single_assignment` 메시징 블록에 배치 하 고 연결 된 모든 대상에 제공 합니다.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message`이 `single_assignment` 메시징 블록에서 소유권을 가져온에 대 한 포인터입니다.

## <a name="release_message"></a><a name="release_message"></a> release_message

이전 메시지 예약을 해제 합니다.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 해제 되는 개체의입니다.

## <a name="reserve_message"></a><a name="reserve_message"></a> reserve_message

이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `single_assignment` 합니다.

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

`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `single_assignment` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

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

## <a name="single_assignment"></a><a name="ctor"></a> single_assignment

`single_assignment` 메시징 블록을 생성합니다.

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>매개 변수

*_Filter*<br/>
제공 된 메시지를 수락 해야 하는지 여부를 결정 하는 필터 함수입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `single_assignment` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `single_assignment` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

형식은 `filter_method` `bool (T const &)` 제공 된 메시지를 `single_assignment` 수락 해야 하는지 여부를 확인 하기 위해이 메시징 블록에 의해 호출 되는 시그니처가 포함 된 함수입니다.

## <a name="single_assignment"></a><a name="dtor"></a> ~ single_assignment

메시징 블록을 소멸 시킵니다 `single_assignment` .

```cpp
~single_assignment();
```

## <a name="value"></a><a name="value"></a> 값

메시징 블록에 저장 되는 메시지의 현재 페이로드에 대 한 참조를 가져옵니다 `single_assignment` .

```cpp
T const& value();
```

### <a name="return-value"></a>반환 값

저장 된 메시지의 페이로드입니다.

### <a name="remarks"></a>설명

이 메서드는 현재 메시징 블록에 저장 된 메시지가 없는 경우 메시지가 도착할 때까지 기다립니다 `single_assignment` .

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[overwrite_buffer 클래스](overwrite-buffer-class.md)<br/>
[unbounded_buffer 클래스](unbounded-buffer-class.md)
