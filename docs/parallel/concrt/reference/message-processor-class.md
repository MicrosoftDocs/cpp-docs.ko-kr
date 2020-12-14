---
description: Message_processor 클래스에 대해 자세히 알아보세요.
title: message_processor 클래스
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: f74314bde6e12ea8b00bfc7bfd2567ca15864f75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202199"
---
# <a name="message_processor-class"></a>message_processor 클래스

`message_processor` 클래스는 `message` 개체 처리를 위한 추상 기본 클래스입니다. 메시지 순서에 대한 보장은 없습니다.

## <a name="syntax"></a>구문

```cpp
template<class T>
class message_processor;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
이 개체에서 처리 하는 메시지 내 페이로드의 데이터 형식입니다 `message_processor` .

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`type`|에 대 한 형식 별칭 `T` 입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[async_send](#async_send)|파생 클래스에서 재정의 되는 경우 메시지를 블록에 비동기식으로 배치 합니다.|
|[sync_send](#sync_send)|파생 클래스에서 재정의 되는 경우 메시지를 블록에 동기적으로 배치 합니다.|
|[대기한](#wait)|파생 클래스에서 재정의 되는 경우 모든 비동기 작업이 완료 될 때까지 기다립니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|파생 클래스에서 재정의 되는 경우 메시지를 블록으로 전달 하는 작업을 수행 합니다. 새 메시지를 추가할 때마다 한 번 호출 되 고 큐는 비어 있는 것으로 확인 됩니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`message_processor`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="async_send"></a><a name="async_send"></a> async_send

파생 클래스에서 재정의 되는 경우 메시지를 블록에 비동기식으로 배치 합니다.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>매개 변수

*_Msg*<br/>
`message`비동기적으로 보낼 개체입니다.

### <a name="remarks"></a>설명

프로세서 구현에서이 메서드를 재정의 해야 합니다.

## <a name="process_incoming_message"></a><a name="process_incoming_message"></a> process_incoming_message

파생 클래스에서 재정의 되는 경우 메시지를 블록으로 전달 하는 작업을 수행 합니다. 새 메시지를 추가할 때마다 한 번 호출 되 고 큐는 비어 있는 것으로 확인 됩니다.

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>설명

메시지 블록 구현은이 메서드를 재정의 해야 합니다.

## <a name="sync_send"></a><a name="sync_send"></a> sync_send

파생 클래스에서 재정의 되는 경우 메시지를 블록에 동기적으로 배치 합니다.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>매개 변수

*_Msg*<br/>
`message`동기적으로 보낼 개체입니다.

### <a name="remarks"></a>설명

프로세서 구현에서이 메서드를 재정의 해야 합니다.

## <a name="wait"></a><a name="wait"></a> 대기한

파생 클래스에서 재정의 되는 경우 모든 비동기 작업이 완료 될 때까지 기다립니다.

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>설명

프로세서 구현에서이 메서드를 재정의 해야 합니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[ordered_message_processor 클래스](ordered-message-processor-class.md)
