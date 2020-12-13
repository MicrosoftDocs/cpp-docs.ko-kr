---
description: '자세한 정보: IExecutionResource 구조체'
title: IExecutionResource 구조체
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 913155ac4ca19f116742134e9d39678ee92b44a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334652"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource 구조체

하드웨어 스레드에 대한 추상화입니다.

## <a name="syntax"></a>구문

```cpp
struct IExecutionResource;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IExecutionResource:: CurrentSubscriptionLevel](#currentsubscriptionlevel)|이 실행 리소스가 나타내는 기본 하드웨어 스레드와 현재 연결 된 활성 외부 스레드 및 활성화 된 가상 프로세서 루트의 수를 반환 합니다.|
|[IExecutionResource:: GetExecutionResourceId](#getexecutionresourceid)|이 실행 리소스가 나타내는 하드웨어 스레드의 고유 식별자를 반환 합니다.|
|[IExecutionResource:: GetNodeId](#getnodeid)|이 실행 리소스가 속한 프로세서 노드에 대 한 고유 식별자를 반환 합니다.|
|[IExecutionResource:: Remove](#remove)|이 실행 리소스를 리소스 관리자 반환 합니다.|

## <a name="remarks"></a>설명

실행 리소스는 독립 실행형 이거나 가상 프로세서 루트와 관련 될 수 있습니다. 응용 프로그램의 스레드가 스레드 구독을 만들 때 독립 실행형 실행 리소스가 생성 됩니다. 메서드 [ISchedulerProxy:: SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) 및 [ISchedulerProxy:: requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) 는 스레드 구독을 만들고 구독을 나타내는 인터페이스를 반환 합니다 `IExecutionResource` . 스레드 구독을 만드는 것은 지정 된 스레드가 스케줄러에 큐에 대기 중인 작업 (스케줄러에 할당 리소스 관리자 가상 프로세서 루트)과 함께 참여 하는 것을 리소스 관리자에 알리는 방법입니다. 리소스 관리자는이 정보를 사용 하 여 하드웨어 스레드를 과도 하 게 등록 하는 것을 방지 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IExecutionResource`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a> IExecutionResource:: CurrentSubscriptionLevel 메서드

이 실행 리소스가 나타내는 기본 하드웨어 스레드와 현재 연결 된 활성 외부 스레드 및 활성화 된 가상 프로세서 루트의 수를 반환 합니다.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>반환 값

현재 구독 수준입니다.

### <a name="remarks"></a>설명

구독 수준은 하드웨어 스레드와 연결 된 실행 중인 스레드 수를 알려 줍니다. 여기에는 구독 된 스레드 형식으로 리소스 관리자가 인식 하는 스레드 및 스레드 프록시를 적극적으로 실행 중인 가상 프로세서 루트가 포함 됩니다.

[ISchedulerProxy:: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)메서드를 호출 하거나 매개 변수를 값으로 설정 하 여 [ISchedulerProxy:: requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) 메서드를 호출 하면 `doSubscribeCurrentThread` **`true`** 하드웨어 스레드의 구독 수준이 1 씩 증가 합니다. 또한 `IExecutionResource` 구독을 나타내는 인터페이스를 반환 합니다. [Iexecutionresource:: Remove](#remove) 에 대해 해당 하는 호출은 하드웨어 스레드의 구독 수준을 1 씩 감소 시킵니다.

[IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate) 메서드를 사용 하 여 가상 프로세서 루트를 활성화 하는 동작은 하드웨어 스레드의 구독 수준을 하나씩 늘립니다. [IVirtualProcessorRoot::D eactivate](ivirtualprocessorroot-structure.md#deactivate)또는 [Iexecutionresource:: Remove](#remove) 메서드는 활성화 된 가상 프로세서 루트에서 호출 될 때 구독 수준을 하나씩 감소 시킵니다.

리소스 관리자은 스케줄러 간에 리소스를 이동할 시기를 결정 하는 방법 중 하나로 구독 수준 정보를 사용 합니다.

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a> IExecutionResource:: GetExecutionResourceId 메서드

이 실행 리소스가 나타내는 하드웨어 스레드의 고유 식별자를 반환 합니다.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>반환 값

이 실행 리소스의 기반이 되는 하드웨어 스레드의 고유 식별자입니다.

### <a name="remarks"></a>설명

각 하드웨어 스레드에는 동시성 런타임에서 고유 식별자가 할당 됩니다. 여러 실행 리소스가 관련 된 하드웨어 스레드인 경우 모두 동일한 실행 리소스 식별자가 있습니다.

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a> IExecutionResource:: GetNodeId 메서드

이 실행 리소스가 속한 프로세서 노드에 대 한 고유 식별자를 반환 합니다.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>반환 값

프로세서 노드에 대 한 고유 식별자입니다.

### <a name="remarks"></a>설명

동시성 런타임 프로세서 노드 그룹의 시스템에 있는 하드웨어 스레드를 나타냅니다. 노드는 일반적으로 시스템의 하드웨어 토폴로지에서 파생 됩니다. 예를 들어 특정 소켓 또는 특정 NUMA 노드의 모든 프로세서는 동일한 프로세서 노드에 속할 수 있습니다. 리소스 관리자은 (으)로 시작 하 여 이러한 노드에 고유 식별자를 할당 합니다 `0` `nodeCount - 1` . 여기서은 `nodeCount` 시스템의 총 프로세서 노드 수를 나타냅니다.

[GetProcessorNodeCount](concurrency-namespace-functions.md)함수에서 노드 수를 가져올 수 있습니다.

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a> IExecutionResource:: Remove 메서드

이 실행 리소스를 리소스 관리자 반환 합니다.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>매개 변수

*pScheduler*<br/>
이 실행 리소스를 제거 하는 요청을 수행 하는 스케줄러에 대 한 인터페이스입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 독립 실행형 실행 리소스 뿐만 아니라 가상 프로세서 루트와 연결 된 실행 리소스를 리소스 관리자으로 반환할 수 있습니다.

메서드를 호출 하 여 [ISchedulerProxy:: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) 또는 [ISchedulerProxy:: requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)중 하나에서 받은 독립 실행형 실행 리소스인 경우 메서드를 호출 하면 `Remove` 리소스가 생성 된 스레드 구독이 종료 됩니다. 스케줄러 프록시를 종료 하기 전에 모든 스레드 구독을 종료 해야 하며, 구독을 만든 스레드에서를 호출 해야 합니다 `Remove` .

인터페이스 `Remove`는 `IVirtualProcessorRoot` 인터페이스에서 상속되기 때문에 `IExecutionResource` 메서드를 호출하여 리소스 관리자에 가상 프로세서 루트도 반환할 수 있습니다. [IScheduler:: RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) 메서드에 대 한 호출에 대 한 응답으로 또는 [ISchedulerProxy:: createoversubscriber](ischedulerproxy-structure.md#createoversubscriber) 메서드에서 가져온 초과 구독 가상 프로세서 루트를 사용 하 여 작업을 수행 하는 경우 가상 프로세서 루트를 반환 해야 할 수 있습니다. 가상 프로세서 루트의 경우 어떤 스레드가 메서드를 호출할 수 있는지에 대 한 제한이 없습니다 `Remove` .

`invalid_argument` 매개 변수가로 설정 되 면이 throw 됩니다 `pScheduler` `NULL` .

`invalid_operation` 매개 변수가 `pScheduler` 이 실행 리소스를 만든 스케줄러와 다른 경우 또는 현재 스레드가 스레드 구독을 만든 스레드와 다른 경우 독립 실행형 실행 리소스를 사용 하 여이 throw 됩니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot 구조체](ivirtualprocessorroot-structure.md)
