---
description: '자세한 정보: 컨텍스트 클래스'
title: Context 클래스
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 4360b01f2261bd75a7db5bd7fab1bbce56a268ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189004"
---
# <a name="context-class"></a>Context 클래스

실행 컨텍스트에 대한 추상화를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class Context;
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[~ 컨텍스트 소멸자](#dtor)||

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[차단](#block)|현재 컨텍스트를 차단 합니다.|
|[CurrentContext](#currentcontext)|현재 컨텍스트에 대 한 포인터를 반환 합니다.|
|[GetId](#getid)|컨텍스트가 속한 스케줄러 내에서 고유한 컨텍스트의 식별자를 반환 합니다.|
|[GetScheduleGroupId](#getschedulegroupid)|컨텍스트가 현재 작업 중인 일정 그룹에 대 한 식별자를 반환 합니다.|
|[GetVirtualProcessorId](#getvirtualprocessorid)|컨텍스트가 현재 실행 되 고 있는 가상 프로세서에 대 한 식별자를 반환 합니다.|
|[ID](#id)|현재 컨텍스트가 속한 스케줄러 내에서 고유한 현재 컨텍스트에 대 한 식별자를 반환 합니다.|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|현재 컨텍스트에서 현재 인라인으로 실행 중인 작업 컬렉션이 활성 취소를 기반으로 하 고 있는지 여부를 나타내는 표시를 반환 합니다.|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|컨텍스트가 동기적으로 차단 되는지 여부를 결정 합니다. 컨텍스트는 차단을 초래한 작업을 명시적으로 수행 하는 경우 동기적으로 차단 된 것으로 간주 됩니다.|
|[Oversubscribe](#oversubscribe)|해당 스케줄러의 가상 프로세서 중 하나에서 실행 되는 컨텍스트에서 호출 될 때 코드 블록의 기간 동안 추가 가상 프로세서를 스케줄러에 삽입 합니다.|
|[ScheduleGroupId](#schedulegroupid)|현재 컨텍스트가 작업 중인 일정 그룹에 대 한 식별자를 반환 합니다.|
|[차단 해제](#unblock)|컨텍스트를 차단 해제 하 여 실행 가능 상태가 되도록 합니다.|
|[VirtualProcessorId](#virtualprocessorid)|현재 컨텍스트가 실행 되 고 있는 가상 프로세서에 대 한 식별자를 반환 합니다.|
|[Yield](#yield)|다른 컨텍스트에서 실행할 수 있도록 실행을 양도합니다. 양도할 수 있는 다른 컨텍스트가 없는 경우 스케줄러에서 다른 운영 체제 스레드에 양도할 수 있습니다.|

## <a name="remarks"></a>설명

동시성 런타임 scheduler ( [스케줄러](scheduler-class.md)참조)는 실행 컨텍스트를 사용 하 여 응용 프로그램에 의해 큐에 대기 중인 작업을 실행 합니다. Win32 스레드는 Windows 운영 체제의 실행 컨텍스트에 대 한 예입니다.

언제 든 지 스케줄러의 동시성 수준은 리소스 관리자에 의해 부여 된 가상 프로세서의 수와 동일 합니다. 가상 프로세서는 처리 리소스에 대 한 추상화 이며 기본 시스템의 하드웨어 스레드에 매핑됩니다. 단일 스케줄러 컨텍스트는 지정 된 시간에 가상 프로세서에서 실행할 수 있습니다.

스케줄러는 본질적으로 협조적 이며 실행 컨텍스트는 대기 상태를 입력 하려는 경우 언제 든 지 가상 프로세서를 다른 컨텍스트로 생성할 수 있습니다. 대기 하는 동안에는 스케줄러에서 사용 가능한 가상 프로세서가 실행을 시작할 때까지 다시 시작할 수 없습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Context`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="block"></a><a name="block"></a> 거부

현재 컨텍스트를 차단 합니다.

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다.

호출 컨텍스트가 가상 프로세서에서 실행 되는 경우 가상 프로세서는 실행 될 다른 실행 가능한 컨텍스트를 찾거나 새 컨텍스트를 만들 수 있습니다.

메서드를 `Block` 호출 하거나 호출한 후에는 해당 메서드를 다시 실행 하기 위해 다른 실행 컨텍스트에서 [차단 해제](#unblock) 메서드 호출과 연결 해야 합니다. 코드에서 메서드를 호출할 수 있는 다른 스레드에 대 한 컨텍스트를 게시 하는 지점과 `Unblock` 실제 메서드 호출이 수행 되는 지점 사이에는 중요 한 기간이 있습니다 `Block` . 이 기간 동안에는 잠금 가져오기 등과 같은 개별적인 이유로 차단하거나 차단 해제할 수 있는 메서드를 호출해서는 안 됩니다. 및 메서드를 호출 하면 `Block` `Unblock` 차단 및 차단 해제 이유가 추적 되지 않습니다. 한 개체에만 쌍의 소유권이 있어야 `Block` -  `Unblock` 합니다.

이 메서드는 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)을 포함 하 여 다양 한 예외를 throw 할 수 있습니다.

## <a name="context"></a><a name="dtor"></a> ~ 컨텍스트

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a><a name="currentcontext"></a> CurrentContext

현재 컨텍스트에 대 한 포인터를 반환 합니다.

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>반환 값

현재 컨텍스트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다.

## <a name="getid"></a><a name="getid"></a> GetId

컨텍스트가 속한 스케줄러 내에서 고유한 컨텍스트의 식별자를 반환 합니다.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>반환 값

컨텍스트가 속한 스케줄러 내에서 고유한 컨텍스트의 식별자입니다.

## <a name="getschedulegroupid"></a><a name="getschedulegroupid"></a> GetScheduleGroupId

컨텍스트가 현재 작업 중인 일정 그룹에 대 한 식별자를 반환 합니다.

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>반환 값

컨텍스트가 현재 작업 중인 일정 그룹의 식별자입니다.

### <a name="remarks"></a>설명

이 메서드의 반환 값은 컨텍스트가 실행 되는 일정 그룹의 즉각적인 샘플링입니다. 이 메서드가 현재 컨텍스트가 아닌 다른 컨텍스트에서 호출될 경우 값은 반환되는 순간에 부실 값이 되어 사용할 수 없습니다. 일반적으로이 메서드는 디버깅 또는 추적 목적 으로만 사용 됩니다.

## <a name="getvirtualprocessorid"></a><a name="getvirtualprocessorid"></a> GetVirtualProcessorId

컨텍스트가 현재 실행 되 고 있는 가상 프로세서에 대 한 식별자를 반환 합니다.

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>반환 값

현재 컨텍스트가 가상 프로세서에서 실행 되 고 있는 경우 컨텍스트가 현재 실행 중인 가상 프로세서의 식별자입니다. 그렇지 않으면 값 `-1` 입니다.

### <a name="remarks"></a>설명

이 메서드의 반환 값은 컨텍스트가 실행 되는 가상 프로세서의 즉각적인 샘플링입니다. 이 값은 반환되는 순간 부실할 수 있으며, 이 값에 의존할 수 없습니다. 일반적으로이 메서드는 디버깅 또는 추적 목적 으로만 사용 됩니다.

## <a name="id"></a><a name="id"></a> A-id

현재 컨텍스트가 속한 스케줄러 내에서 고유한 현재 컨텍스트에 대 한 식별자를 반환 합니다.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>반환 값

현재 컨텍스트가 스케줄러에 연결 된 경우 현재 컨텍스트가 속한 스케줄러 내에서 고유한 현재 컨텍스트의 식별자입니다. 그렇지 않으면 값 `-1` 입니다.

## <a name="iscurrenttaskcollectioncanceling"></a><a name="iscurrenttaskcollectioncanceling"></a> IsCurrentTaskCollectionCanceling

현재 컨텍스트에서 현재 인라인으로 실행 중인 작업 컬렉션이 활성 취소를 기반으로 하 고 있는지 여부를 나타내는 표시를 반환 합니다.

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>반환 값

스케줄러를 호출 컨텍스트에 연결 하 고 작업 그룹에서 해당 컨텍스트에서 작업을 인라인으로 실행 하는 경우 해당 작업 그룹이 활성 취소를 기반으로 하 고 있는지 여부를 나타냅니다. 그렇지 않으면 값 **`false`** 입니다.

## <a name="issynchronouslyblocked"></a><a name="issynchronouslyblocked"></a> IsSynchronouslyBlocked

컨텍스트가 동기적으로 차단 되는지 여부를 결정 합니다. 컨텍스트는 차단을 초래한 작업을 명시적으로 수행 하는 경우 동기적으로 차단 된 것으로 간주 됩니다.

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>반환 값

컨텍스트가 동기적으로 차단 되었는지 여부를 나타냅니다.

### <a name="remarks"></a>설명

컨텍스트는 차단을 초래한 작업을 명시적으로 수행 하는 경우 동기적으로 차단 된 것으로 간주 됩니다. 스레드 스케줄러에서 이는 `Context::Block` 메서드에 대한 직접 호출이나 `Context::Block` 메서드를 사용하여 작성된 동기화 개체를 나타냅니다.

이 메서드의 반환 값은 컨텍스트가 동기적으로 차단 되었는지 여부에 대 한 즉각적인 샘플입니다. 이 값은 반환 되는 순간에 유효 하지 않을 수 있으며 매우 특정 한 경우에만 사용할 수 있습니다.

## <a name="operator-delete"></a><a name="operator_delete"></a> operator delete

`Context`개체는 런타임에서 내부적으로 소멸 됩니다. 개체를 명시적으로 삭제할 수 없습니다.

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>매개 변수

*_PObject*<br/>
삭제할 개체에 대 한 포인터입니다.

## <a name="oversubscribe"></a><a name="oversubscribe"></a> Oversubscribe

해당 스케줄러의 가상 프로세서 중 하나에서 실행 되는 컨텍스트에서 호출 될 때 코드 블록의 기간 동안 추가 가상 프로세서를 스케줄러에 삽입 합니다.

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>매개 변수

*_BeginOversubscription*<br/>
인 경우 **`true`** 초과 구독 기간 동안 추가 가상 프로세서를 추가 해야 한다는 것을 나타냅니다. 인 경우 **`false`** 초과 구독을 종료 하 고 이전에 추가한 가상 프로세서를 제거 해야 함을 나타냅니다.

## <a name="schedulegroupid"></a><a name="schedulegroupid"></a> ScheduleGroupId

현재 컨텍스트가 작업 중인 일정 그룹에 대 한 식별자를 반환 합니다.

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>반환 값

현재 컨텍스트가 스케줄러에 연결 되어 있고 일정 그룹에서 작업 하는 경우 현재 컨텍스트가 작동 중인 스케줄러 그룹의 식별자입니다. 그렇지 않으면 값 `-1` 입니다.

## <a name="unblock"></a><a name="unblock"></a> 차단 해제

컨텍스트를 차단 해제 하 여 실행 가능 상태가 되도록 합니다.

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>설명

메서드를 호출 하는 것이 `Unblock` 해당 [블록](#block) 메서드에 대 한 해당 호출 앞에 나올 수 있습니다. 및 메서드에 대 한 호출이 적절 하 게 `Block` `Unblock` 쌍을 이루는 경우 런타임에서는 각 순서 지정의 자연 스러운 경합을 적절히 처리 합니다. 호출 `Unblock` 전에 오는 호출은 `Block` 단순히 호출의 효과를 부정 합니다 `Block` .

이 메서드에서 throw 할 수 있는 몇 가지 예외가 있습니다. 컨텍스트가 자체에서 메서드를 호출 하려고 하면 `Unblock` [context_self_unblock](context-self-unblock-class.md) 예외가 throw 됩니다. 및에 대 한 호출이 `Block` `Unblock` 제대로 쌍을 이루지 않는 경우 (예: `Unblock` 현재 실행 중인 컨텍스트에 대 한 두 번의 호출) [context_unblock_unbalanced](context-unblock-unbalanced-class.md) 예외가 throw 됩니다.

코드에서 메서드를 호출할 수 있는 다른 스레드에 대 한 컨텍스트를 게시 하는 지점과 `Unblock` 실제 메서드 호출이 수행 되는 지점 사이에는 중요 한 기간이 있습니다 `Block` . 이 기간 동안에는 잠금 가져오기 등과 같은 개별적인 이유로 차단하거나 차단 해제할 수 있는 메서드를 호출해서는 안 됩니다. 및 메서드를 호출 하면 `Block` `Unblock` 차단 및 차단 해제 이유가 추적 되지 않습니다. 한 개체에만 및 쌍의 소유권이 `Block` 있어야 `Unblock` 합니다.

## <a name="virtualprocessorid"></a><a name="virtualprocessorid"></a> VirtualProcessorId

현재 컨텍스트가 실행 되 고 있는 가상 프로세서에 대 한 식별자를 반환 합니다.

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>반환 값

현재 컨텍스트가 스케줄러에 연결 된 경우 현재 컨텍스트가 실행 되 고 있는 가상 프로세서의 식별자입니다. 그렇지 않으면 값 `-1` 입니다.

### <a name="remarks"></a>설명

이 메서드의 반환 값은 현재 컨텍스트가 실행 되는 가상 프로세서의 즉각적인 샘플링입니다. 이 값은 반환되는 순간 부실할 수 있으며, 이 값에 의존할 수 없습니다. 일반적으로이 메서드는 디버깅 또는 추적 목적 으로만 사용 됩니다.

## <a name="yield"></a><a name="yield"></a> Yield

다른 컨텍스트에서 실행할 수 있도록 실행을 양도합니다. 양도할 수 있는 다른 컨텍스트가 없는 경우 스케줄러에서 다른 운영 체제 스레드에 양도할 수 있습니다.

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다.

## <a name="yieldexecution"></a><a name="yieldexecution"></a> YieldExecution

다른 컨텍스트에서 실행할 수 있도록 실행을 양도합니다. 양도할 수 있는 다른 컨텍스트가 없는 경우 스케줄러에서 다른 운영 체제 스레드에 양도할 수 있습니다.

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다.

이 함수는 Visual Studio 2015의 새로운 기능이 며 [yield](#yield) 함수와 동일 하지만 Windows의 yield 매크로와 충돌 하지 않습니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[Scheduler 클래스](scheduler-class.md)<br/>
[작업 Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
