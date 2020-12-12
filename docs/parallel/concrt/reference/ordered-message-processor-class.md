---
description: Ordered_message_processor 클래스에 대해 자세히 알아보세요.
title: ordered_message_processor 클래스
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: bea7f2ae70b6eb87fc30ece578f3bd8c3b35b5ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167541"
---
# <a name="ordered_message_processor-class"></a>ordered_message_processor 클래스

`ordered_message_processor`는 메시지 블록이 수신된 순서대로 메시지를 처리할 수 있도록 하는 `message_processor`입니다.

## <a name="syntax"></a>구문

```cpp
template<class T>
class ordered_message_processor : public message_processor<T>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
프로세서에서 처리 하는 메시지의 페이로드 유형입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`type`|에 대 한 형식 별칭 `T` 입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[ordered_message_processor](#ctor)|`ordered_message_processor` 개체를 생성합니다.|
|[~ ordered_message_processor 소멸자](#dtor)|개체를 소멸 시킵니다 `ordered_message_processor` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[async_send](#async_send)|아직 수행 하지 않은 경우 비동기적으로 메시지를 큐에 대기 시키고 처리 작업을 시작 합니다. [Message_processor:: async_send](message-processor-class.md#async_send)를 재정의 합니다.|
|[초기](#initialize)|`ordered_message_processor`적절 한 콜백 함수, 스케줄러 및 일정 그룹을 사용 하 여 개체를 초기화 합니다.|
|[initialize_batched_processing](#initialize_batched_processing)|일관 처리된 메시지 처리 초기화|
|[sync_send](#sync_send)|메시지를 동기적으로 큐에 대기 시키고 처리 태스크를 시작 합니다 (아직 수행 하지 않은 경우). [Message_processor:: sync_send](message-processor-class.md#sync_send)를 재정의 합니다.|
|[대기한](#wait)|블록을 제거 하기 전에 모든 비동기 처리 작업을 완료할 시간이 있는지 확인 하기 위해 메시지 블록의 소멸자에 사용 되는 프로세서 특정 spin wait입니다. [Message_processor:: wait](message-processor-class.md#wait)를 재정의 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|비동기식으로 호출 되는 처리 함수입니다. 메시지를 큐에서 제거 하 고 처리를 시작 합니다. [Message_processor::p rocess_incoming_message](message-processor-class.md#process_incoming_message)를 재정의 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="async_send"></a><a name="async_send"></a> async_send

아직 수행 하지 않은 경우 비동기적으로 메시지를 큐에 대기 시키고 처리 작업을 시작 합니다.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>매개 변수

*_Msg*<br/>
메시지에 대 한 포인터입니다.

## <a name="initialize"></a><a name="initialize"></a> 초기

`ordered_message_processor`적절 한 콜백 함수, 스케줄러 및 일정 그룹을 사용 하 여 개체를 초기화 합니다.

```cpp
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>매개 변수

*_PScheduler*<br/>
경량 작업을 예약 하는 데 사용할 스케줄러에 대 한 포인터입니다.

*_PScheduleGroup*<br/>
경량 작업을 예약 하는 데 사용할 일정 그룹에 대 한 포인터입니다.

*_Handler*<br/>
콜백 중에 호출 되는 처리기 함수입니다.

## <a name="initialize_batched_processing"></a><a name="initialize_batched_processing"></a> initialize_batched_processing

일관 처리된 메시지 처리 초기화

```cpp
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>매개 변수

*_Processor*<br/>
콜백 중에 호출 된 프로세서 함수입니다.

*_Propagator*<br/>
콜백 중에 호출 된 전파자 함수입니다.

## <a name="ordered_message_processor"></a><a name="ctor"></a> ordered_message_processor

`ordered_message_processor` 개체를 생성합니다.

```cpp
ordered_message_processor();
```

### <a name="remarks"></a>설명

이는 `ordered_message_processor` 함수가 호출 될 때까지 비동기 또는 동기 처리기를 예약 하지 않습니다 `initialize` .

## <a name="ordered_message_processor"></a><a name="dtor"></a> ~ ordered_message_processor

개체를 소멸 시킵니다 `ordered_message_processor` .

```cpp
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>설명

프로세서를 소멸 시키기 전에 처리 중인 모든 비동기 작업을 대기 합니다.

## <a name="process_incoming_message"></a><a name="process_incoming_message"></a> process_incoming_message

비동기식으로 호출 되는 처리 함수입니다. 메시지를 큐에서 제거 하 고 처리를 시작 합니다.

```cpp
virtual void process_incoming_message();
```

## <a name="sync_send"></a><a name="sync_send"></a> sync_send

메시지를 동기적으로 큐에 대기 시키고 처리 태스크를 시작 합니다 (아직 수행 하지 않은 경우).

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>매개 변수

*_Msg*<br/>
메시지에 대 한 포인터입니다.

## <a name="wait"></a><a name="wait"></a> 대기한

블록을 제거 하기 전에 모든 비동기 처리 작업을 완료할 시간이 있는지 확인 하기 위해 메시지 블록의 소멸자에 사용 되는 프로세서 특정 spin wait입니다.

```cpp
virtual void wait();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
