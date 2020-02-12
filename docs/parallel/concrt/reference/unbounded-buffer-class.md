---
title: unbounded_buffer 클래스
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: d0f2f81957ee88d4263c6acd879bd286c95631eb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142329"
---
# <a name="unbounded_buffer-class"></a>unbounded_buffer 클래스

`unbounded_buffer` 메시징 블록은 메시지를 개수에 제한 없이 저장할 수 있는, 순서가 지정된 다중 대상 다중 소스 `propagator_block`입니다.

## <a name="syntax"></a>구문

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>매개 변수

*_Type*<br/>
버퍼에 의해 저장 및 전파 되는 메시지의 페이로드 유형입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|name|설명|
|----------|-----------------|
|[unbounded_buffer](#ctor)|오버로드됨. `unbounded_buffer` 메시징 블록을 생성 합니다.|
|[~ unbounded_buffer 소멸자](#dtor)|`unbounded_buffer` 메시징 블록을 소멸 시킵니다.|

### <a name="public-methods"></a>Public 메서드

|name|설명|
|----------|-----------------|
|[나오는](#dequeue)|`unbounded_buffer` 메시징 블록에서 항목을 제거 합니다.|
|[스케줄러](#enqueue)|`unbounded_buffer` 메시징 블록에 항목을 추가 합니다.|

### <a name="protected-methods"></a>보호된 메서드

|name|설명|
|----------|-----------------|
|[accept_message](#accept_message)|는이 `unbounded_buffer` 메시징 블록이 제공한 메시지를 수락 하 여 호출자에 게 소유권을 전송 합니다.|
|[consume_message](#consume_message)|`unbounded_buffer` 메시징 블록에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 호출자에 게 소유권을 전송 합니다.|
|[link_target_notification](#link_target_notification)|새 대상이이 `unbounded_buffer` 메시징 블록에 연결 되었음을 알리는 콜백입니다.|
|[process_input_messages](#process_input_messages)|이 `unbounded_buffer` 메시징 블록에 `message` `_PMessage`를 배치 하 고 연결 된 모든 대상에 게 제공 하려고 합니다.|
|[propagate_message](#propagate_message)|`ISource` 블록에서이 `unbounded_buffer` 메시징 블록으로 메시지를 비동기적으로 전달 합니다. 소스 블록에서 호출 되는 경우 `propagate` 메서드에서 호출 됩니다.|
|[propagate_output_messages](#propagate_output_messages)|이 `unbounded_buffer` 메시징 블록에 `message` `_PMessage`를 배치 하 고 연결 된 모든 대상에 게 제공 하려고 합니다. [Source_block::p ropagate_output_messages](source-block-class.md#propagate_output_messages)를 재정의 합니다.|
|[release_message](#release_message)|이전 메시지 예약을 해제 합니다. [Source_block:: release_message](source-block-class.md#release_message)를 재정의 합니다.|
|[reserve_message](#reserve_message)|이 `unbounded_buffer` 메시징 블록에서 이전에 제공 된 메시지를 예약 합니다. [Source_block:: reserve_message](source-block-class.md#reserve_message)를 재정의 합니다.|
|[resume_propagation](#resume_propagation)|예약이 해제 된 후 전파를 다시 시작 합니다. [Source_block:: resume_propagation](source-block-class.md#resume_propagation)를 재정의 합니다.|
|[send_message](#send_message)|`ISource` 블록에서이 `unbounded_buffer` 메시징 블록으로 메시지를 동기적으로 전달 합니다. 소스 블록에서 호출 되는 경우 `send` 메서드에서 호출 됩니다.|
|[supports_anonymous_source](#supports_anonymous_source)|`supports_anonymous_source` 메서드를 재정의하여 이 블록이 연결되지 않은 소스에서 제공하는 메시지를 수락할 수 있음을 나타냅니다. [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)을 재정의 합니다.|

자세한 내용은 [비동기 메시지 블록](../asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임스페이스:** 동시성

## <a name="accept_message"></a>accept_message

는이 `unbounded_buffer` 메시징 블록이 제공한 메시지를 수락 하 여 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
제공 된 `message` 개체의 `runtime_object_identity`입니다.

### <a name="return-value"></a>Return Value

호출자에 게 소유권이 있는 `message` 개체에 대 한 포인터입니다.

## <a name="consume_message"></a>consume_message

`unbounded_buffer` 메시징 블록에서 이전에 제공 하 고 대상에 의해 예약 된 메시지를 사용 하 여 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
사용 중인 `message` 개체의 `runtime_object_identity`입니다.

### <a name="return-value"></a>Return Value

호출자에 게 소유권이 있는 `message` 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`accept`와 비슷하지만 항상 `reserve`에 대 한 호출 뒤에 나옵니다.

## <a name="dequeue"></a>나오는

`unbounded_buffer` 메시징 블록에서 항목을 제거 합니다.

```cpp
_Type dequeue();
```

### <a name="return-value"></a>Return Value

`unbounded_buffer`에서 제거 되는 메시지의 페이로드입니다.

## <a name="enqueue"></a>스케줄러

`unbounded_buffer` 메시징 블록에 항목을 추가 합니다.

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>매개 변수

*_Item*<br/>
추가할 항목입니다.

### <a name="return-value"></a>Return Value

항목이 수락 되었으면 **true** 이 고, 그렇지 않으면 **false** 입니다.

## <a name="link_target_notification"></a>link_target_notification

새 대상이이 `unbounded_buffer` 메시징 블록에 연결 되었음을 알리는 콜백입니다.

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
새로 연결 된 대상에 대 한 포인터입니다.

## <a name="propagate_message"></a>propagate_message

`ISource` 블록에서이 `unbounded_buffer` 메시징 블록으로 메시지를 비동기적으로 전달 합니다. 소스 블록에서 호출 되는 경우 `propagate` 메서드에서 호출 됩니다.

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>Return Value

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md#message_status) 입니다.

## <a name="propagate_output_messages"></a>propagate_output_messages

이 `unbounded_buffer` 메시징 블록에 `message` `_PMessage`를 배치 하 고 연결 된 모든 대상에 게 제공 하려고 합니다.

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>설명

이미 `unbounded_buffer`에 있는 다른 메시지의 경우 이전 메시지를 수락 하거나 사용 하기 전에는 연결 된 대상으로의 전파가 발생 하지 않습니다. 메시지를 성공적으로 `accept` 하거나 `consume` 하기 위해 연결 된 첫 번째 대상이 소유권을 가지 며 다른 대상이 메시지를 가져올 수 없습니다.

## <a name="process_input_messages"></a>process_input_messages

이 `unbounded_buffer` 메시징 블록에 `message` `_PMessage`를 배치 하 고 연결 된 모든 대상에 게 제공 하려고 합니다.

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
처리할 메시지에 대 한 포인터입니다.

## <a name="release_message"></a>release_message

이전 메시지 예약을 해제 합니다.

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
해제 되는 `message` 개체의 `runtime_object_identity`입니다.

## <a name="reserve_message"></a>reserve_message

이 `unbounded_buffer` 메시징 블록에서 이전에 제공 된 메시지를 예약 합니다.

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
예약 되는 `message` 개체의 `runtime_object_identity`입니다.

### <a name="return-value"></a>Return Value

메시지가 성공적으로 예약 되었으면 **true** 이 고, 그렇지 않으면 **false** 입니다.

### <a name="remarks"></a>설명

`reserve`가 호출 되 면 **true**를 반환 하는 경우 `consume` 또는 `release`를 호출 하 여 메시지 소유권을 가져오거나 해제 해야 합니다.

## <a name="resume_propagation"></a>resume_propagation

예약이 해제 된 후 전파를 다시 시작 합니다.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a>send_message

`ISource` 블록에서이 `unbounded_buffer` 메시징 블록으로 메시지를 동기적으로 전달 합니다. 소스 블록에서 호출 되는 경우 `send` 메서드에서 호출 됩니다.

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
`message` 개체에 대한 포인터입니다.

*_PSource*<br/>
메시지를 제공 하는 소스 블록에 대 한 포인터입니다.

### <a name="return-value"></a>Return Value

대상에서 메시지를 사용 하 여 수행 하기로 결정 한 내용을 나타내는 [message_status](concurrency-namespace-enums.md#message_status) 입니다.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

`supports_anonymous_source` 메서드를 재정의하여 이 블록이 연결되지 않은 소스에서 제공하는 메시지를 수락할 수 있음을 나타냅니다.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Return Value

블록에서 제공 된 메시지를 연기 하지 않으므로 **true** 입니다.

## <a name="ctor"></a>unbounded_buffer

`unbounded_buffer` 메시징 블록을 생성 합니다.

```cpp
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>매개 변수

*_Filter*<br/>
제공 된 메시지를 수락 해야 하는지 여부를 결정 하는 필터 함수입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `unbounded_buffer` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `unbounded_buffer` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

`filter_method` 형식은 제공 된 메시지를 수락 해야 하는지 여부를 확인 하기 위해이 `unbounded_buffer` 메시징 블록에서 호출 하는 시그니처 `bool (_Type const &)`를 사용 하는 함수입니다.

## <a name="dtor"></a>~ unbounded_buffer

`unbounded_buffer` 메시징 블록을 소멸 시킵니다.

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임스페이스](concurrency-namespace.md)<br/>
[overwrite_buffer 클래스](overwrite-buffer-class.md)<br/>
[single_assignment 클래스](single-assignment-class.md)
