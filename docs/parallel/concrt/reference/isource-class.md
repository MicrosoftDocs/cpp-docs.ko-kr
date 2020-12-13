---
description: '자세히 알아보기: ISource 클래스'
title: ISource 클래스
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: 86a55c9ca056c0aebb98e00c12518293b316bcb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334438"
---
# <a name="isource-class"></a>ISource 클래스

`ISource` 클래스는 모든 소스 블록에 대한 인터페이스입니다. 소스 블록은 `ITarget` 블록에 메시지를 전파합니다.

## <a name="syntax"></a>구문

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
소스 블록에 의해 생성 되는 메시지 내 페이로드의 데이터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`source_type`|에 대 한 형식 별칭 `T` 입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[~ ISource 소멸자](#dtor)|개체를 소멸 시킵니다 `ISource` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[수락할](#accept)|파생 클래스에서 재정의 되는 경우이 블록이 제공한 메시지를 수락 하 여 `ISource` 소유권을 호출자에 게 전송 합니다.|
|[acquire_ref](#acquire_ref)|파생 클래스에서 재정의 되는 경우 `ISource` 삭제를 방지 하기 위해이 블록의 참조 횟수를 가져옵니다.|
|[활용](#consume)|파생 클래스에서 재정의 되는 경우이 블록에서 이전에 제공 `ISource` 하 고 대상에 의해 성공적으로 예약 된 메시지를 사용 하 여 호출자에 게 소유권을 전송 합니다.|
|[link_target](#link_target)|파생 클래스에서 재정의 되는 경우 대상 블록을이 블록에 연결 `ISource` 합니다.|
|[릴리스](#release)|파생 클래스에서 재정의 되는 경우 이전의 성공적인 메시지 예약을 해제 합니다.|
|[release_ref](#release_ref)|파생 클래스에서 재정의 되는 경우이 블록에서 참조 횟수를 해제 `ISource` 합니다.|
|[두기](#reserve)|파생 클래스에서 재정의 되는 경우이 블록에서 이전에 제공 된 메시지를 예약 `ISource` 합니다.|
|[unlink_target](#unlink_target)|파생 클래스에서 재정의 되는 경우이 블록에서 대상 블록의 `ISource` 연결을 끊습니다 (이전에 연결 된 경우).|
|[unlink_targets](#unlink_targets)|파생 클래스에서 재정의 되는 경우이 블록에서 모든 대상 블록을 해제 `ISource` 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ISource`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="accept"></a><a name="accept"></a> 수락할

파생 클래스에서 재정의 되는 경우이 블록이 제공한 메시지를 수락 하 여 `ISource` 소유권을 호출자에 게 전송 합니다.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `accept` .

### <a name="return-value"></a>반환 값

호출자에 게 소유권이 있는 메시지에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`accept`이 블록에서 메시지를 제공 하는 동안 대상에서 메서드를 호출 합니다 `ISource` . `propagate` `ITarget` 이 소스가 메시지의 복사본을 만들도록 결정 한 경우 반환 되는 메시지 포인터는 블록의 메서드에 전달 된 것과 다를 수 있습니다.

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

파생 클래스에서 재정의 되는 경우 `ISource` 삭제를 방지 하기 위해이 블록의 참조 횟수를 가져옵니다.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 메서드를 호출 하는 대상 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 메서드를 실행 하는 `ITarget` 동안이 소스에 연결 되는 개체에 의해 호출 됩니다 `link_target` .

## <a name="consume"></a><a name="consume"></a> 활용

파생 클래스에서 재정의 되는 경우이 블록에서 이전에 제공 `ISource` 하 고 대상에 의해 성공적으로 예약 된 메시지를 사용 하 여 호출자에 게 소유권을 전송 합니다.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="isource"></a><a name="dtor"></a> ~ ISource

개체를 소멸 시킵니다 `ISource` .

```cpp
virtual ~ISource();
```

## <a name="link_target"></a><a name="link_target"></a> link_target

파생 클래스에서 재정의 되는 경우 대상 블록을이 블록에 연결 `ISource` 합니다.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 블록에 연결 되는 대상 블록에 대 한 포인터 `ISource` 입니다.

## <a name="release"></a><a name="release"></a> 릴리스

파생 클래스에서 재정의 되는 경우 이전의 성공적인 메시지 예약을 해제 합니다.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`예약 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `release` .

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

파생 클래스에서 재정의 되는 경우이 블록에서 참조 횟수를 해제 `ISource` 합니다.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 메서드를 호출 하는 대상 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는이 소스에서 연결을 해제 하는 개체에 의해 호출 됩니다 `ITarget` . 소스 블록은 대상 블록에 예약 된 모든 리소스를 해제할 수 있습니다.

## <a name="reserve"></a><a name="reserve"></a> 두기

파생 클래스에서 재정의 되는 경우이 블록에서 이전에 제공 된 메시지를 예약 `ISource` 합니다.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*_MsgId*<br/>
`runtime_object_identity`제공 된 개체의입니다 `message` .

*_PTarget*<br/>
메서드를 호출 하는 대상 블록에 대 한 포인터입니다 `reserve` .

### <a name="return-value"></a>반환 값

**`true`** 메시지가 성공적으로 예약 되었으면이 고, **`false`** 그렇지 않으면입니다. 예약은 메시지를 이미 다른 대상이 예약했거나 수락한 경우, 소스에서 예약을 거부한 경우 등과 같은 다양한 이유로 실패할 수 있습니다.

### <a name="remarks"></a>설명

를 호출한 후에 `reserve` 성공 하면 또는을 호출 `consume` 하 여 `release` 메시지를 각각 소유 하거나 제공 해야 합니다.

## <a name="unlink_target"></a><a name="unlink_target"></a> unlink_target

파생 클래스에서 재정의 되는 경우이 블록에서 대상 블록의 `ISource` 연결을 끊습니다 (이전에 연결 된 경우).

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 블록에서 연결이 해제 되는 대상 블록에 대 한 포인터 `ISource` 입니다.

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

파생 클래스에서 재정의 되는 경우이 블록에서 모든 대상 블록을 해제 `ISource` 합니다.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[ITarget 클래스](itarget-class.md)
