---
description: '자세히 알아보기: EventSource 클래스'
title: EventSource 클래스
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: 2553d82a0fc16cd759f43ef2e4ae9527884cab10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272814"
---
# <a name="eventsource-class"></a>EventSource 클래스

Agile이 아닌 이벤트를 나타냅니다. `EventSource` 멤버 함수는 이벤트 처리기를 추가, 삭제 및 호출합니다. Agile 이벤트의 경우 [AgileEventSource](agileeventsource-class.md)를 사용 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>매개 변수

*TDelegateInterface*<br/>
이벤트 처리기를 나타내는 대리자에 대 한 인터페이스입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

| 이름                                     | 설명                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource:: EventSource](#eventsource) | `EventSource` 클래스의 새 인스턴스를 초기화합니다. |

### <a name="public-methods"></a>Public 메서드

| 이름                                 | 설명                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: Add](#add)             | 지정 된 대리자 인터페이스에서 나타내는 이벤트 처리기를 현재 개체에 대 한 이벤트 처리기 집합에 추가 합니다 `EventSource` .                     |
| [EventSource:: GetSize](#getsize)     | 현재 개체와 연결 된 이벤트 처리기의 수를 검색 합니다 `EventSource` .                                                                         |
| [EventSource:: InvokeAll](#invokeall) | `EventSource`지정 된 인수 형식 및 인수를 사용 하 여 현재 개체와 연결 된 각 이벤트 처리기를 호출 합니다.                                      |
| [EventSource:: Remove](#remove)       | 현재 개체와 연결 된 이벤트 처리기 집합에서 지정 된 이벤트 등록 토큰이 나타내는 이벤트 처리기를 삭제 합니다 `EventSource` . |

### <a name="protected-data-members"></a>보호된 데이터 멤버

| Name                                                    | 설명                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: addRemoveLock_](#addremovelock)           | 이벤트 처리기를 추가, 제거 또는 호출할 때 [targets_](#targets) 배열에 대 한 액세스를 동기화 합니다.                          |
| [EventSource:: targets_](#targets)                       | 하나 이상의 이벤트 처리기 배열입니다.                                                                                           |
| [EventSource:: targetsPointerLock_](#targetspointerlock) | 이 EventSource의 이벤트 처리기를 추가, 삭제 또는 호출하는 동안에도 내부 데이터 멤버에 대한 액세스를 동기화합니다. |

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`EventSource`

## <a name="requirements"></a>요구 사항

**헤더:** 이벤트. h

**네임스페이스:** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a> EventSource:: Add

지정 된 대리자 인터페이스에서 나타내는 이벤트 처리기를 현재 개체에 대 한 이벤트 처리기 집합에 추가 합니다 `EventSource` .

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>매개 변수

*delegateInterface*<br/>
이벤트 처리기를 나타내는 대리자 개체에 대 한 인터페이스입니다.

*토큰*<br/>
이 작업이 완료 되 면 이벤트를 나타내는 핸들입니다. 이 토큰을 [Remove ()](#remove) 메서드에 대 한 매개 변수로 사용 하 여 이벤트 처리기를 삭제 합니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a> EventSource:: addRemoveLock_

이벤트 처리기를 추가, 제거 또는 호출할 때 [targets_](#targets) 배열에 대 한 액세스를 동기화 합니다.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a> EventSource:: EventSource

`EventSource` 클래스의 새 인스턴스를 초기화합니다.

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a> EventSource:: GetSize

현재 개체와 연결 된 이벤트 처리기의 수를 검색 합니다 `EventSource` .

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>반환 값

[Targets_](#targets)이벤트 처리기 수입니다.

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a> EventSource:: InvokeAll

`EventSource`지정 된 인수 형식 및 인수를 사용 하 여 현재 개체와 연결 된 각 이벤트 처리기를 호출 합니다.

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>매개 변수

*T0*<br/>
0번째 이벤트 처리기 인수 형식입니다.

*T1*<br/>
첫 번째 이벤트 처리기 인수 형식입니다.

*T2*<br/>
두 번째 이벤트 처리기 인수 형식입니다.

*T3*<br/>
세 번째 이벤트 처리기 인수 형식입니다.

*T4*<br/>
네 번째 이벤트 처리기 인수 형식입니다.

*T5*<br/>
다섯 번째 이벤트 처리기 인수 형식입니다.

*T6*<br/>
여섯 번째 이벤트 처리기 인수 형식입니다.

*T7*<br/>
일곱 번째 이벤트 처리기 인수 형식입니다.

*T8*<br/>
여덟 번째 이벤트 처리기 인수의 형식입니다.

*T9*<br/>
아홉 번째 이벤트 처리기 인수 형식입니다.

*arg0*<br/>
0번째 이벤트 처리기 인수입니다.

*arg1*<br/>
첫 번째 이벤트 처리기 인수입니다.

*arg2*<br/>
두 번째 이벤트 처리기 인수입니다.

*arg3*<br/>
세 번째 이벤트 처리기 인수입니다.

*arg4*<br/>
네 번째 이벤트 처리기 인수입니다.

*arg5*<br/>
다섯 번째 이벤트 처리기 인수입니다.

*arg6*<br/>
여섯 번째 이벤트 처리기 인수입니다.

*arg7*<br/>
일곱 번째 이벤트 처리기 인수입니다.

*arg8*<br/>
여덟 번째 이벤트 처리기 인수입니다.

*arg9*<br/>
아홉 번째 이벤트 처리기 인수입니다.

## <a name="eventsourceremove"></a><a name="remove"></a> EventSource:: Remove

현재 개체와 연결 된 이벤트 처리기 집합에서 지정 된 이벤트 등록 토큰이 나타내는 이벤트 처리기를 삭제 합니다 `EventSource` .

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>매개 변수

*토큰*<br/>
이벤트 처리기를 나타내는 핸들입니다. 이 토큰은 [Add ()](#add) 메서드에서 이벤트 처리기를 등록할 때 반환 되었습니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

구조체에 대 한 자세한 내용은 `EventRegistrationToken` **Windows 런타임** 참조 설명서의 **Windows:: Foundation:: EventRegistrationToken structure** 항목을 참조 하세요.

## <a name="eventsourcetargets_"></a><a name="targets"></a> EventSource:: targets_

하나 이상의 이벤트 처리기 배열입니다.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>설명

현재 개체가 나타내는 이벤트가 `EventSource` 발생 하면 이벤트 처리기가 호출 됩니다.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a> EventSource:: targetsPointerLock_

이에 대 한 이벤트 처리기 `EventSource` 가 추가, 제거 또는 호출 되는 동안에도 내부 데이터 멤버에 대 한 액세스를 동기화 합니다.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
