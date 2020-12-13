---
description: '자세히 알아보기: ISchedulerProxy Structure'
title: ISchedulerProxy 구조체
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: 4c3c488136c2b41a76b3080b2162fbf95dcb5ea8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334445"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 구조체

스케줄러가 리소스 할당을 협상하기 위해 동시성 런타임의 리소스 관리자와 통신하는 데 사용되는 인터페이스입니다.

## <a name="syntax"></a>구문

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[ISchedulerProxy:: BindContext](#bindcontext)|실행 컨텍스트가 이미 연결 되어 있지 않은 경우 스레드 프록시를 연결 합니다.|
|[ISchedulerProxy:: Create과잉 구독자](#createoversubscriber)|기존 실행 리소스와 연결 된 하드웨어 스레드에 새 가상 프로세서 루트를 만듭니다.|
|[ISchedulerProxy:: RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|가상 프로세서 루트의 초기 할당을 요청 합니다. 모든 가상 프로세서 루트는 스케줄러에 대해 작업을 수행할 수 있는 하나의 스레드를 실행 하는 기능을 나타냅니다.|
|[ISchedulerProxy:: Shutdown](#shutdown)|스케줄러를 종료 하는 리소스 관리자에 게 알립니다. 이렇게 하면 리소스 관리자 스케줄러에 부여 된 모든 리소스를 즉시 회수할 수 있습니다.|
|[ISchedulerProxy:: SubscribeCurrentThread](#subscribecurrentthread)|현재 스레드를이 스케줄러와 연결 하 여 리소스 관리자에 등록 합니다.|
|[ISchedulerProxy:: UnbindContext](#unbindcontext)|매개 변수로 지정 된 실행 컨텍스트에서 스레드 프록시를 분리 `pContext` 하 여 스레드 프록시 팩터리의 사용 가능한 풀로 반환 합니다. 이 메서드는 [ISchedulerProxy:: bindcontext](#bindcontext) 메서드를 통해 바인딩되고 아직 `pContext` [Ithreadproxy:: SwitchTo](ithreadproxy-structure.md#switchto) 메서드 호출의 매개 변수를 통해 시작 되지 않은 실행 컨텍스트에서만 호출 될 수 있습니다.|

## <a name="remarks"></a>설명

리소스 관리자는 `ISchedulerProxy` [iresourcemanager:: registerscheduler](iresourcemanager-structure.md#registerscheduler) 메서드를 사용 하 여이에 등록 하는 모든 스케줄러에 인터페이스를 전달 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ISchedulerProxy`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a> ISchedulerProxy:: BindContext 메서드

실행 컨텍스트가 이미 연결 되어 있지 않은 경우 스레드 프록시를 연결 합니다.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>매개 변수

*pContext*<br/>
스레드 프록시와 연결할 실행 컨텍스트에 대 한 인터페이스입니다.

### <a name="remarks"></a>설명

일반적으로 [Ithreadproxy:: SwitchTo](ithreadproxy-structure.md#switchto) 메서드는 요청 시 스레드 프록시를 실행 컨텍스트에 바인딩합니다. 그러나 `SwitchTo` 메서드가 이미 바인딩된 컨텍스트로 전환 되도록 미리 컨텍스트를 미리 바인딩해야 하는 경우도 있습니다. 이는 메모리를 할당 하는 메서드를 호출할 수 없고, 스레드 프록시를 바인딩하는 스레드를 스레드 프록시 팩터리의 사용 가능한 풀에서 사용할 수 없는 경우에 메모리 할당이 필요할 수 있기 때문에이 경우에 해당 합니다.

`invalid_argument` 매개 변수의 값이 이면이 throw 됩니다 `pContext` `NULL` .

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a> ISchedulerProxy:: Create과잉 구독자 메서드

기존 실행 리소스와 연결 된 하드웨어 스레드에 새 가상 프로세서 루트를 만듭니다.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>매개 변수

*pExecutionResource*<br/>
`IExecutionResource`Oversubscribe 하드웨어 스레드를 나타내는 인터페이스입니다.

### <a name="return-value"></a>반환 값

`IVirtualProcessorRoot` 인터페이스입니다.

### <a name="remarks"></a>설명

스케줄러가 제한 된 시간 동안 특정 하드웨어 스레드를 oversubscribe 하려는 경우이 방법을 사용 합니다. 가상 프로세서 루트를 완료 한 후에는 인터페이스에서 [Remove](iexecutionresource-structure.md#remove) 메서드를 호출 하 여 리소스 관리자에 반환 해야 합니다 `IVirtualProcessorRoot` .

`IVirtualProcessorRoot` 인터페이스가 `IExecutionResource` 인터페이스에서 상속하기 때문에 기존 가상 프로세서 루트를 초과 구독할 수도 있습니다.

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a> ISchedulerProxy:: RequestInitialVirtualProcessors 메서드

가상 프로세서 루트의 초기 할당을 요청 합니다. 모든 가상 프로세서 루트는 스케줄러에 대해 작업을 수행할 수 있는 하나의 스레드를 실행 하는 기능을 나타냅니다.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>매개 변수

*doSubscribeCurrentThread*<br/>
리소스 할당 중에 현재 스레드와 계정을 구독할 지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

`IExecutionResource`매개 변수의 값이 인 경우 현재 스레드에 대 한 인터페이스 `doSubscribeCurrentThread` **`true`** 입니다. 값이 이면 **`false`** 메서드에서 NULL을 반환 합니다.

### <a name="remarks"></a>설명

스케줄러는 작업을 실행 하기 전에이 메서드를 사용 하 여 리소스 관리자에서 가상 프로세서 루트를 요청 해야 합니다. 리소스 관리자는 [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) 를 사용 하 여 스케줄러 정책에 액세스 하 고, 정책 키에 대 한 값을 사용 하 `MinConcurrency` `MaxConcurrency` 고, 처음에 `TargetOversubscriptionFactor` 스케줄러에 할당할 하드웨어 스레드 수와 각 하드웨어 스레드에 대해 만들 가상 프로세서 루트 수를 결정 합니다. 스케줄러 정책을 사용 하 여 scheduler의 초기 할당을 확인 하는 방법에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md)를 참조 하세요.

리소스 관리자은 가상 프로세서 루트의 목록을 사용 하 여 [IScheduler:: AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) 메서드를 호출 하 여 스케줄러에 리소스를 부여 합니다. 메서드는이 메서드가 반환 되기 전에 스케줄러에 대 한 콜백으로 호출 됩니다.

스케줄러에서 매개 변수를로 설정 하 여 현재 스레드의 구독을 요청한 경우이 `doSubscribeCurrentThread` **`true`** 메서드는 인터페이스를 반환 합니다 `IExecutionResource` . 나중에 [Iexecutionresource:: Remove](iexecutionresource-structure.md#remove) 메서드를 사용 하 여 구독을 종료 해야 합니다.

선택 된 하드웨어 스레드를 결정할 때 리소스 관리자 프로세서 노드 선호도에 대해 최적화를 시도 합니다. 현재 스레드에 대해 구독이 요청 되 면 현재 스레드가이 스케줄러에 할당 된 작업에 참여 하 고 있음을 나타냅니다. 이 경우 할당 된 가상 프로세서 루트는 현재 스레드가 실행 중인 프로세서 노드에 있습니다 (가능한 경우).

스레드를 구독 하는 동작은 기본 하드웨어 스레드의 구독 수준을 하나씩 늘립니다. 구독이 종료 되 면 구독 수준이 1 수준으로 줄어듭니다. 구독 수준에 대 한 자세한 내용은 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)을 참조 하세요.

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a> ISchedulerProxy:: Shutdown 메서드

스케줄러를 종료 하는 리소스 관리자에 게 알립니다. 이렇게 하면 리소스 관리자 스케줄러에 부여 된 모든 리소스를 즉시 회수할 수 있습니다.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>설명

모든 `IExecutionContext` 인터페이스는 메서드를 사용 하 여 외부 스레드를 등록 한 결과로 수신 된 스케줄러는 `ISchedulerProxy::RequestInitialVirtualProcessors` `ISchedulerProxy::SubscribeCurrentThread` 스케줄러가 종료 되기 전에를 사용 하 여 리소스 관리자로 반환 되어야 합니다 `IExecutionResource::Remove` .

스케줄러가 비활성화 된 가상 프로세서 루트를 사용 하는 경우 [IVirtualProcessorRoot:: activate](ivirtualprocessorroot-structure.md#activate)를 사용 하 여 활성화 해야 하며, 스레드 프록시가 실행 되는 스레드는 `Dispatch` `Shutdown` 스케줄러 프록시에서를 호출 하기 전에 디스패치 되는 실행 컨텍스트의 메서드를 그대로 두어야 합니다.

모든 가상 프로세서 루트는 종료 시 리소스 관리자로 반환되기 때문에 리소스 관리자가 `Remove` 메서드 호출을 통해 부여한 모든 가상 프로세서 루트를 스케줄러가 개별적으로 반환할 필요는 없습니다.

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a> ISchedulerProxy:: SubscribeCurrentThread 메서드

현재 스레드를이 스케줄러와 연결 하 여 리소스 관리자에 등록 합니다.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>반환 값

`IExecutionResource`런타임에 현재 스레드를 나타내는 인터페이스입니다.

### <a name="remarks"></a>설명

스케줄러 및 기타 스케줄러에 리소스를 할당 하는 동안 리소스 관리자 현재 스레드를 고려 하도록 하려면이 메서드를 사용 합니다. 이는 스케줄러가 리소스 관리자에서 받는 가상 프로세서 루트와 함께 스케줄러에 대기 중인 작업에 참여할 계획인 경우에 특히 유용 합니다. 리소스 관리자는 정보를 사용 하 여 시스템에서 하드웨어 스레드의 불필요 한 초과 구독을 방지 합니다.

이 메서드를 통해 받은 실행 리소스는 [Iexecutionresource:: Remove](iexecutionresource-structure.md#remove) 메서드를 사용 하 여 리소스 관리자로 반환 되어야 합니다. 메서드를 호출 하는 스레드는 `Remove` 이전에 메서드를 호출한 스레드와 동일 해야 합니다 `SubscribeCurrentThread` .

스레드를 구독 하는 동작은 기본 하드웨어 스레드의 구독 수준을 하나씩 늘립니다. 구독이 종료 되 면 구독 수준이 1 수준으로 줄어듭니다. 구독 수준에 대 한 자세한 내용은 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)을 참조 하세요.

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a> ISchedulerProxy:: UnbindContext 메서드

매개 변수로 지정 된 실행 컨텍스트에서 스레드 프록시를 분리 `pContext` 하 여 스레드 프록시 팩터리의 사용 가능한 풀로 반환 합니다. 이 메서드는 [ISchedulerProxy:: bindcontext](#bindcontext) 메서드를 통해 바인딩되고 아직 `pContext` [Ithreadproxy:: SwitchTo](ithreadproxy-structure.md#switchto) 메서드 호출의 매개 변수를 통해 시작 되지 않은 실행 컨텍스트에서만 호출 될 수 있습니다.

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>매개 변수

*pContext*<br/>
스레드 프록시와의 연관을 해제할 실행 컨텍스트입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[IScheduler 구조체](ischeduler-structure.md)<br/>
[IThreadProxy 구조체](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 구조체](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 구조체](iresourcemanager-structure.md)
