---
description: '자세한 정보: message 클래스'
title: message 클래스
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 0e15dafd9606e68f7a6ed1bed3795791c0f6870c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202316"
---
# <a name="message-class"></a>message 클래스

메시징 블록 간에 전달되는 데이터 페이로드를 포함하는 기본 메시지 봉투입니다.

## <a name="syntax"></a>구문

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
메시지 내 페이로드의 데이터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`type`|에 대 한 형식 별칭 `T` 입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[message](#ctor)|오버로드됨. `message` 개체를 생성합니다.|
|[~ 메시지 소멸자](#dtor)|개체를 소멸 시킵니다 `message` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[add_ref](#add_ref)|개체의 참조 횟수에를 추가 `message` 합니다. 메시지 수명을 확인 하기 위해 참조 계산이 필요한 메시지 블록에 사용 됩니다.|
|[msg_id](#msg_id)|개체의 ID를 반환 합니다 `message` .|
|[remove_ref](#remove_ref)|개체의 참조 횟수에서 뺍니다 `message` . 메시지 수명을 확인 하기 위해 참조 계산이 필요한 메시지 블록에 사용 됩니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[페이로드와](#payload)|개체의 페이로드 `message` 입니다.|

## <a name="remarks"></a>설명

자세한 내용은 [비동기 메시지 블록](../../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`message`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="add_ref"></a><a name="add_ref"></a> add_ref

개체의 참조 횟수에를 추가 `message` 합니다. 메시지 수명을 확인 하기 위해 참조 계산이 필요한 메시지 블록에 사용 됩니다.

```cpp
long add_ref();
```

### <a name="return-value"></a>반환 값

참조 횟수의 새 값입니다.

## <a name="message"></a><a name="ctor"></a> 메시지

`message` 개체를 생성합니다.

```cpp
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```

### <a name="parameters"></a>매개 변수

*_P*<br/>
이 메시지의 페이로드입니다.

*_Id*<br/>
이 메시지의 고유 ID입니다.

*_Msg*<br/>
개체에 대 한 참조 또는 포인터 `message` 입니다.

### <a name="remarks"></a>설명

매개 변수가 인 경우 개체에 대 한 포인터를 인수로 사용 하는 생성자는 `message` [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외를 throw 합니다 `_Msg` `NULL` .

## <a name="message"></a><a name="dtor"></a> ~ 메시지

개체를 소멸 시킵니다 `message` .

```cpp
virtual ~message();
```

## <a name="msg_id"></a><a name="msg_id"></a> msg_id

개체의 ID를 반환 합니다 `message` .

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>반환 값

`runtime_object_identity` 개체의 `message`입니다.

## <a name="payload"></a><a name="payload"></a> 페이로드와

개체의 페이로드 `message` 입니다.

```cpp
T const payload;
```

## <a name="remove_ref"></a><a name="remove_ref"></a> remove_ref

개체의 참조 횟수에서 뺍니다 `message` . 메시지 수명을 확인 하기 위해 참조 계산이 필요한 메시지 블록에 사용 됩니다.

```cpp
long remove_ref();
```

### <a name="return-value"></a>반환 값

참조 횟수의 새 값입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
