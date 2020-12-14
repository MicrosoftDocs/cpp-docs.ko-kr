---
description: Multitype_join 클래스에 대해 자세히 알아보세요.
title: multitype_join 클래스
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: ee4e3a282bc9fa410140fefb79f31ac5ed9463ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202121"
---
# <a name="multitype_join-class"></a>multitype_join 클래스

`multitype_join` 메시징 블록은 각 소스에서 다양한 형식의 메시지를 결합하고 결합된 메시지의 튜플을 대상에 제공하는 다중 소스, 단일 대상 메시징 블록입니다.

## <a name="syntax"></a>구문

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
`tuple`블록에서 조인 및 전파 되는 메시지의 페이로드 유형입니다.

*_Jtype*<br/>
블록의 종류는 `join` , 또는입니다. `greedy``non_greedy`

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`type`|에 대 한 형식 별칭 `T` 입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[multitype_join](#ctor)|오버로드됨. `multitype_join` 메시징 블록을 생성합니다.|
|[~ multitype_join 소멸자](#dtor)|메시징 블록을 소멸 시킵니다 `multitype_join` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[수락할](#accept)|`multitype_join`호출자에 게 소유권을 전송 하는이 블록에서 제공 된 메시지를 수락 합니다.|
|[acquire_ref](#acquire_ref)|`multitype_join`삭제를 방지 하기 위해이 메시징 블록의 참조 횟수를 가져옵니다.|
|[활용](#consume)|메시징 블록에서 이전에 제공 `multitype_join` 하 고 대상에 의해 성공적으로 예약 된 메시지를 사용 하 여 호출자에 게 소유권을 전송 합니다.|
|[link_target](#link_target)|대상 블록을이 `multitype_join` 메시징 블록에 연결 합니다.|
|[릴리스](#release)|이전의 성공적인 메시지 예약을 해제 합니다.|
|[release_ref](#release_ref)|이 메시징 블록에서 참조 횟수를 해제 `multiple_join` 합니다.|
|[두기](#reserve)|이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `multitype_join` 합니다.|
|[unlink_target](#unlink_target)|이 메시징 블록에서 대상 블록을 해제 `multitype_join` 합니다.|
|[unlink_targets](#unlink_targets)|이 메시징 블록에서 모든 대상을 해제 `multitype_join` 합니다. ( [ISource:: unlink_targets](isource-class.md#unlink_targets)을 재정의 합니다.)|

## <a name="remarks"></a>설명

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept"></a><a name="accept"></a> 수락할

`multitype_join`호출자에 게 소유권을 전송 하는이 블록에서 제공 된 메시지를 수락 합니다.

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `accept` .

### <a name="return-value"></a>반환 값

호출자에 게 소유권이 있는 메시지에 대 한 포인터입니다.

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

`multitype_join`삭제를 방지 하기 위해이 메시징 블록의 참조 횟수를 가져옵니다.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 메서드를 호출 하는 대상 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 메서드를 실행 하는 `ITarget` 동안이 소스에 연결 되는 개체에 의해 호출 됩니다 `link_target` .

## <a name="consume"></a><a name="consume"></a> 활용

메시징 블록에서 이전에 제공 `multitype_join` 하 고 대상에 의해 성공적으로 예약 된 메시지를 사용 하 여 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
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

## <a name="link_target"></a><a name="link_target"></a> link_target

대상 블록을이 `multitype_join` 메시징 블록에 연결 합니다.

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
`ITarget`이 메시징 블록에 연결할 블록에 대 한 포인터 `multitype_join` 입니다.

## <a name="multitype_join"></a><a name="ctor"></a> multitype_join

`multitype_join` 메시징 블록을 생성합니다.

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>매개 변수

*_Tuple*<br/>
이 `tuple` 메시징 블록에 대한 소스의 `multitype_join` 입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `multitype_join` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `multitype_join` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

*_Join*<br/>
복사할 `multitype_join` 메시징 블록입니다. 원래 개체는 고아로 표시되어 생성자가 이동하도록 합니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

잠금이 있는 경우 이동 생성은 수행되지 않습니다. 즉, 이동하는 중에 간단한 작업이 실행되고 있지 않은지 확인할 책임은 사용자에게 있습니다. 그러지 않으면 수많은 레이스가 발생하여 예외가 발생하거나 일관성 없는 상태가 될 수 있습니다.

## <a name="multitype_join"></a><a name="dtor"></a> ~ multitype_join

메시징 블록을 소멸 시킵니다 `multitype_join` .

```cpp
~multitype_join();
```

## <a name="release"></a><a name="release"></a> 릴리스

이전의 성공적인 메시지 예약을 해제 합니다.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity` `message` 해제 되는 개체의입니다.

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `release` .

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

이 메시징 블록에서 참조 횟수를 해제 `multiple_join` 합니다.

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 메서드를 호출 하는 대상 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는이 소스에서 연결을 해제 하는 개체에 의해 호출 됩니다 `ITarget` . 소스 블록은 대상 블록에 예약 된 모든 리소스를 해제할 수 있습니다.

## <a name="reserve"></a><a name="reserve"></a> 두기

이 메시징 블록에 의해 이전에 제공 된 메시지를 예약 `multitype_join` 합니다.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
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

이 메시징 블록에서 대상 블록을 해제 `multitype_join` 합니다.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
`ITarget`이 메시징 블록에서 연결을 해제할 블록에 대 한 포인터 `multitype_join` 입니다.

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

이 메시징 블록에서 모든 대상을 해제 `multitype_join` 합니다.

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[choice 클래스](choice-class.md)<br/>
[join 클래스](join-class.md)
