---
description: '자세한 정보: choice 클래스'
title: choice 클래스
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: a7597a3bd530185e316cdc42ebbc4696162d498f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254471"
---
# <a name="choice-class"></a>choice 클래스

`choice` 메시징 블록은 소스 집합과의 제어 흐름 상호 작용을 나타내는 다중 소스 단일 대상 블록입니다. 선택한 블록은 여러 소스 중 하나가 메시지를 생성할 때까지 대기하고 메시지를 생성한 소스의 인덱스를 전파합니다.

## <a name="syntax"></a>구문

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
`tuple`입력 소스의 페이로드를 나타내는 기반 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`type`|에 대 한 형식 별칭 `T` 입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[choice](#ctor)|오버로드됨. `choice` 메시징 블록을 생성합니다.|
|[~ choice 소멸자](#dtor)|메시징 블록을 소멸 시킵니다 `choice` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[수락할](#accept)|`choice`호출자에 게 소유권을 전송 하는이 블록에서 제공 된 메시지를 수락 합니다.|
|[acquire_ref](#acquire_ref)|`choice`삭제를 방지 하기 위해이 메시징 블록의 참조 횟수를 가져옵니다.|
|[활용](#consume)|이 메시징 블록에서 이전에 제공 하 고 대상에 의해 성공적으로 예약 된 메시지를 사용 하 여 `choice` 호출자에 게 소유권을 전송 합니다.|
|[has_value](#has_value)|이 `choice` 메시징 블록이 아직 값을 사용 하 여 초기화 되었는지 여부를 확인 합니다.|
|[index](#index)|`tuple`메시징 블록에서 선택한 요소를 나타내는에 대 한 인덱스를 반환 합니다 `choice` .|
|[link_target](#link_target)|대상 블록을이 `choice` 메시징 블록에 연결 합니다.|
|[릴리스](#release)|이전의 성공적인 메시지 예약을 해제 합니다.|
|[release_ref](#release_ref)|이 메시징 블록에서 참조 횟수를 해제 `choice` 합니다.|
|[두기](#reserve)|이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `choice` 합니다.|
|[unlink_target](#unlink_target)|이 메시징 블록에서 대상 블록을 해제 `choice` 합니다.|
|[unlink_targets](#unlink_targets)|이 메시징 블록에서 모든 대상을 해제 `choice` 합니다. ( [ISource:: unlink_targets](isource-class.md#unlink_targets)을 재정의 합니다.)|
|[value](#value)|메시지 블록에서 해당 인덱스를 선택한 메시지를 가져옵니다 `choice` .|

## <a name="remarks"></a>설명

선택 블록을 사용 하면 들어오는 메시지 중 하나만 사용 됩니다.

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept"></a><a name="accept"></a> 수락할

`choice`호출자에 게 소유권을 전송 하는이 블록에서 제공 된 메시지를 수락 합니다.

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `accept` .

### <a name="return-value"></a>반환 값

호출자에 게 소유권이 있는 메시지에 대 한 포인터입니다.

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

`choice`삭제를 방지 하기 위해이 메시징 블록의 참조 횟수를 가져옵니다.

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 메서드를 호출 하는 대상 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 메서드를 실행 하는 `ITarget` 동안이 소스에 연결 되는 개체에 의해 호출 됩니다 `link_target` .

## <a name="choice"></a><a name="ctor"></a> 적절

`choice` 메시징 블록을 생성합니다.

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>매개 변수

*_Tuple*<br/>
선택을 위한 소스의 `tuple` 입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `choice` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `choice` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

*_Choice*<br/>
복사할 `choice` 메시징 블록입니다. 원래 개체는 고아로 표시되어 생성자가 이동하도록 합니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

잠금이 있는 경우 이동 생성은 수행되지 않습니다. 즉, 이동하는 중에 간단한 작업이 실행되고 있지 않은지 확인할 책임은 사용자에게 있습니다. 그러지 않으면 수많은 레이스가 발생하여 예외가 발생하거나 일관성 없는 상태가 될 수 있습니다.

## <a name="choice"></a><a name="dtor"></a> ~ choice

메시징 블록을 소멸 시킵니다 `choice` .

```cpp
~choice();
```

## <a name="consume"></a><a name="consume"></a> 활용

이 메시징 블록에서 이전에 제공 하 고 대상에 의해 성공적으로 예약 된 메시지를 사용 하 여 `choice` 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`예약 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `consume` .

### <a name="return-value"></a>반환 값

`message`호출자가 소유 하 고 있는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`consume`메서드는와 유사 `accept` 하지만 항상 `reserve` 반환 되는를 호출 해야 합니다 **`true`** .

## <a name="has_value"></a><a name="has_value"></a> has_value

이 `choice` 메시징 블록이 아직 값을 사용 하 여 초기화 되었는지 여부를 확인 합니다.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>반환 값

**`true`** 블록에서 값을 받았으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="index"></a><a name="index"></a> 인덱싱할

`tuple`메시징 블록에서 선택한 요소를 나타내는에 대 한 인덱스를 반환 합니다 `choice` .

```cpp
size_t index();
```

### <a name="return-value"></a>반환 값

메시지 인덱스입니다.

### <a name="remarks"></a>설명

메시지 페이로드는 메서드를 사용 하 여 추출할 수 있습니다 `get` .

## <a name="link_target"></a><a name="link_target"></a> link_target

대상 블록을이 `choice` 메시징 블록에 연결 합니다.

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
`ITarget`이 메시징 블록에 연결할 블록에 대 한 포인터 `choice` 입니다.

## <a name="release"></a><a name="release"></a> 릴리스

이전의 성공적인 메시지 예약을 해제 합니다.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 해제 되는 개체의입니다.

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `release` .

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

이 메시징 블록에서 참조 횟수를 해제 `choice` 합니다.

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 메서드를 호출 하는 대상 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는이 소스에서 연결을 해제 하는 개체에 의해 호출 됩니다 `ITarget` . 소스 블록은 대상 블록에 예약 된 모든 리소스를 해제할 수 있습니다.

## <a name="reserve"></a><a name="reserve"></a> 두기

이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `choice` 합니다.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 예약 되는 개체의입니다.

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `reserve` .

### <a name="return-value"></a>반환 값

**`true`** 메시지가 성공적으로 예약 되었으면이 고, **`false`** 그렇지 않으면입니다. 예약은 메시지를 이미 다른 대상이 예약했거나 수락한 경우, 소스에서 예약을 거부한 경우 등과 같은 다양한 이유로 실패할 수 있습니다.

### <a name="remarks"></a>설명

를 호출한 후에 `reserve` 성공 하면 또는을 호출 `consume` 하 여 `release` 메시지를 각각 소유 하거나 제공 해야 합니다.

## <a name="unlink_target"></a><a name="unlink_target"></a> unlink_target

이 메시징 블록에서 대상 블록을 해제 `choice` 합니다.

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
`ITarget`이 메시징 블록에서 연결을 해제할 블록에 대 한 포인터 `choice` 입니다.

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

이 메시징 블록에서 모든 대상을 해제 `choice` 합니다.

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>설명

내부 블록의 소멸자 `single_assignment` 가 제대로 연결 해제 되므로이 메서드를 소멸자에서 호출할 필요가 없습니다.

## <a name="value"></a><a name="value"></a> 값

메시지 블록에서 해당 인덱스를 선택한 메시지를 가져옵니다 `choice` .

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>매개 변수

*_Payload_type*<br/>
메시지 페이로드의 유형입니다.

### <a name="return-value"></a>반환 값

메시지의 페이로드입니다.

### <a name="remarks"></a>설명

`choice` 메시징 블록은 페이로드 형식이 서로 다른 입력을 사용할 수 있기 때문에 검색 시 페이로드의 형식을 지정해야 합니다. 메서드의 결과에 따라 형식을 결정할 수 있습니다 `index` .

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[join 클래스](join-class.md)<br/>
[single_assignment 클래스](single-assignment-class.md)
