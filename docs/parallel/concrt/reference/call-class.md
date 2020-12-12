---
description: '자세한 정보: call 클래스'
title: call 클래스
ms.date: 11/04/2016
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
ms.openlocfilehash: d1d489063d7eb301bbfdb923f6b2f3c351d01f5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172221"
---
# <a name="call-class"></a>call 클래스

`call` 메시징 블록은 메시지를 받을 때 지정된 함수를 호출하는 순서가 지정된 다중 소스 `target_block`입니다.

## <a name="syntax"></a>구문

```cpp
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
이 블록으로 전파 되는 메시지의 페이로드 유형입니다.

*_FunctorType*<br/>
이 블록에서 수락할 수 있는 함수의 서명입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[call](#ctor)|오버로드됨. `call` 메시징 블록을 생성합니다.|
|[~ call 소멸자](#dtor)|메시징 블록을 소멸 시킵니다 `call` .|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|입력 메시지에 대해 call 함수를 실행 합니다.|
|[process_message](#process_message)|이 메시징 블록에서 수락 된 메시지를 처리 `call` 합니다.|
|[propagate_message](#propagate_message)|`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `call` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[send_message](#send_message)|`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `call` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.|
|[supports_anonymous_source](#supports_anonymous_source)|`supports_anonymous_source` 메서드를 재정의하여 이 블록이 연결되지 않은 소스에서 제공하는 메시지를 수락할 수 있음을 나타냅니다. [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)을 재정의 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="call"></a><a name="ctor"></a> 전화할

`call` 메시징 블록을 생성합니다.

```cpp
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```

### <a name="parameters"></a>매개 변수

*_Func*<br/>
허용 되는 각 메시지에 대해 호출 되는 함수입니다.

*_Filter*<br/>
제공 된 메시지를 수락 해야 하는지 여부를 결정 하는 필터 함수입니다.

*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `call` 개체입니다.

*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `call` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.

### <a name="remarks"></a>설명

런타임은 `_PScheduler` 또는 `_PScheduleGroup` 매개 변수를 지정하지 않는 경우 기본 스케줄러를 사용합니다.

형식은 `_Call_method` `void (T const &)` 메시지를 `call` 처리 하기 위해이 메시징 블록에서 호출 하는 시그니처가 있는 함수입니다.

형식은 `filter_method` `bool (T const &)` 제공 된 메시지를 `call` 수락 해야 하는지 여부를 확인 하기 위해이 메시징 블록에 의해 호출 되는 시그니처가 포함 된 함수입니다.

## <a name="call"></a><a name="dtor"></a> ~ 호출

메시징 블록을 소멸 시킵니다 `call` .

```cpp
~call();
```

## <a name="process_input_messages"></a><a name="process_input_messages"></a> process_input_messages

입력 메시지에 대해 call 함수를 실행 합니다.

```cpp
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
처리할 메시지에 대 한 포인터입니다.

## <a name="process_message"></a><a name="process_message"></a> process_message

이 메시징 블록에서 수락 된 메시지를 처리 `call` 합니다.

```cpp
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>매개 변수

*_PMessage*<br/>
처리할 메시지에 대 한 포인터입니다.

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

`ISource`블록에서이 메시징 블록으로 메시지를 비동기적으로 전달 `call` 합니다. `propagate`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

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

## <a name="send_message"></a><a name="send_message"></a> send_message

`ISource`블록에서이 메시징 블록으로 메시지를 동기적으로 전달 `call` 합니다. `send`소스 블록에서 호출 하는 경우 메서드에 의해 호출 됩니다.

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

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[변환기 클래스](transformer-class.md)
