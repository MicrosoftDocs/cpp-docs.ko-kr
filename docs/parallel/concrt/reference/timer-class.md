---
description: '자세히 알아보기: timer 클래스'
title: timer 클래스
ms.date: 11/04/2016
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: 460185f61be0dd33fe11dfa0f94e2147893089d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188172"
---
# <a name="timer-class"></a>timer 클래스

`timer` 메시징 블록은 지정된 기간이 경과한 후 또는 특정 간격마다 대상에 메시지를 보낼 수 있는 단일 대상 `source_block`입니다.

## <a name="syntax"></a>구문

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
이 블록에 대 한 출력 메시지의 페이로드 유형입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[시간이](#ctor)|오버로드됨. 지정 된 `timer` 간격 후 지정 된 메시지를 발생 시킬 메시징 블록을 생성 합니다.|
|[~ timer 소멸자](#dtor)|메시징 블록을 소멸 시킵니다 `timer` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[pause](#pause)|`timer`메시징 블록을 중지 합니다. 반복 되는 `timer` 메시징 블록인 경우 후속 호출을 사용 하 여 다시 시작할 수 있습니다 `start()` . 반복 되지 않는 타이머의 경우 호출 하는 것과 동일한 효과가 있습니다 `stop` .|
|[start](#start)|`timer`메시징 블록을 시작 합니다. 이이 호출 된 후 지정 된 시간 (밀리초)이 호출 되 면 지정 된 값이 다운스트림에로 전파 됩니다 `message` .|
|[stop](#stop)|`timer`메시징 블록을 중지 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[accept_message](#accept_message)|`timer`호출자에 게 소유권을 전송 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.|
|[consume_message](#consume_message)|에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `timer` 호출자에 게 소유권을 전송 합니다.|
|[link_target_notification](#link_target_notification)|새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `timer` .|
|[propagate_to_any_targets](#propagate_to_any_targets)|블록에서 생성 한 메시지를 `timer` 모든 연결 된 대상에 제공 하려고 시도 합니다.|
|[release_message](#release_message)|이전 메시지 예약을 해제 합니다. [Source_block:: release_message](source-block-class.md#release_message)를 재정의 합니다.|
|[reserve_message](#reserve_message)|이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `timer` 합니다. [Source_block:: reserve_message](source-block-class.md#reserve_message)를 재정의 합니다.|
|[resume_propagation](#resume_propagation)|예약이 해제 된 후 전파를 다시 시작 합니다. [Source_block:: resume_propagation](source-block-class.md#resume_propagation)를 재정의 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

`timer`호출자에 게 소유권을 전송 하는이 메시징 블록에서 제공 된 메시지를 수락 합니다.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 `timer` 호출자에 게 소유권을 전송 합니다.

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

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

새 대상이이 메시징 블록에 연결 되었음을 알리는 콜백입니다 `timer` .

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
새로 연결 된 대상에 대 한 포인터입니다.

## <a name="pause"></a><a name="pause"></a> 동안

`timer`메시징 블록을 중지 합니다. 반복 되는 `timer` 메시징 블록인 경우 후속 호출을 사용 하 여 다시 시작할 수 있습니다 `start()` . 반복 되지 않는 타이머의 경우 호출 하는 것과 동일한 효과가 있습니다 `stop` .

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a> propagate_to_any_targets

블록에서 생성 한 메시지를 `timer` 모든 연결 된 대상에 제공 하려고 시도 합니다.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `timer` 합니다.

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

## <a name="start"></a><a name="start"></a> 시작

`timer`메시징 블록을 시작 합니다. 이이 호출 된 후 지정 된 시간 (밀리초)이 호출 되 면 지정 된 값이 다운스트림에로 전파 됩니다 `message` .

```cpp
void start();
```

## <a name="stop"></a><a name="stop"></a> 막을

`timer`메시징 블록을 중지 합니다.

```cpp
void stop();
```

## <a name="timer"></a><a name="ctor"></a> 시간이

지정 된 `timer` 간격 후 지정 된 메시지를 발생 시킬 메시징 블록을 생성 합니다.

```cpp
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```

### <a name="parameters"></a>매개 변수

*_Ms*<br/>
지정 된 메시지의 다운스트림 전파를 시작 하기 위해 호출 후 경과 해야 하는 시간 (밀리초)입니다.

*value*<br/>
타이머가 경과할 때 다운스트림에 전파 되는 값입니다.

*_PTarget*<br/>
타이머가 메시지를 전파 하는 대상입니다.

*_Repeating*<br/>
True 이면 타이머가 정기적으로 밀리초 마다 발생 합니다 `_Ms` .

*_Scheduler*<br/>
`Scheduler`메시징 블록의 전파 태스크가 예약 된 개체가 `timer` 예약 됩니다.

*_ScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `timer` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

### <a name="remarks"></a>설명

런타임은 `_Scheduler` 또는 `_ScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

## <a name="timer"></a><a name="dtor"></a> ~ 타이머

메시징 블록을 소멸 시킵니다 `timer` .

```cpp
~timer();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
