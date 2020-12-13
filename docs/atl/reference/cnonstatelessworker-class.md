---
description: '자세한 정보: CNonStatelessWorker 클래스'
title: CNonStatelessWorker 클래스
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: 68457c9594bfaf4d8dd53acd80d7997355c3a3f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141429"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker 클래스

스레드 풀에서 요청을 수신 하 고 각 요청에서 만들어지고 소멸 된 작업자 개체에 전달 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>매개 변수

*작업자*<br/>
[작업자 원형](../../atl/reference/worker-archetype.md) 를 준수 하는 작업자 스레드 클래스는 [cthreadpool](../../atl/reference/cthreadpool-class.md)에서 큐에 대기 중인 요청을 처리 하는 데 적합 합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CNonStatelessWorker:: RequestType](#requesttype)|[WorkerArchetype:: RequestType](worker-archetype.md#requesttype)의 구현입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CNonStatelessWorker:: Execute](#execute)|[WorkerArchetype:: Execute](worker-archetype.md#execute)의 구현입니다.|
|[CNonStatelessWorker:: Initialize](#initialize)|[WorkerArchetype:: Initialize](worker-archetype.md#initialize)의 구현입니다.|
|[CNonStatelessWorker:: Terminate](#terminate)|[WorkerArchetype:: Terminate](worker-archetype.md#terminate)의 구현입니다.|

## <a name="remarks"></a>설명

이 클래스는 [Cthreadpool](../../atl/reference/cthreadpool-class.md)에서 사용할 수 있는 간단한 작업자 스레드입니다. 이 클래스는 자체의 요청 처리 기능을 제공 하지 않습니다. 대신 요청 당 *작업자* 의 한 인스턴스를 인스턴스화하고 해당 메서드의 구현을 해당 인스턴스에 위임 합니다.

이 클래스의 장점에는 기존 작업자 스레드 클래스에 대 한 상태 모델을 편리 하 게 변경할 수 있는 방법이 있습니다. `CThreadPool` 는 스레드 수명 동안 단일 작업자를 만들기 때문에 worker 클래스가 상태를 유지 하는 경우 여러 요청에서 보류 합니다. 에서 사용 하기 전에 해당 클래스를 `CNonStatelessWorker` 템플릿에서 래핑하여 `CThreadPool` , 작업자의 수명과 보유 한 상태는 단일 요청으로 제한 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a> CNonStatelessWorker:: Execute

[WorkerArchetype:: Execute](worker-archetype.md#execute)의 구현입니다.

```cpp
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>설명

이 메서드는 스택에 *Worker* 클래스의 인스턴스를 만들고 해당 개체에 대해 [Initialize](worker-archetype.md#initialize) 를 호출 합니다. 초기화에 성공 하면이 메서드는 동일한 개체에서 [Execute](worker-archetype.md#execute) 및 [Terminate](worker-archetype.md#terminate) 도 호출 합니다.

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a> CNonStatelessWorker:: Initialize

[WorkerArchetype:: Initialize](worker-archetype.md#initialize)의 구현입니다.

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>반환 값

항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

이 클래스는에서 초기화를 수행 하지 않습니다 `Initialize` .

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a> CNonStatelessWorker:: RequestType

[WorkerArchetype:: RequestType](worker-archetype.md#requesttype)의 구현입니다.

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>설명

이 클래스는 *작업자* 템플릿 매개 변수에 사용 되는 클래스와 동일한 형식의 작업 항목을 처리 합니다. 자세한 내용은 [Cnonstatelessworker 개요](../../atl/reference/cnonstatelessworker-class.md) 를 참조 하세요.

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a> CNonStatelessWorker:: Terminate

[WorkerArchetype:: Terminate](worker-archetype.md#terminate)의 구현입니다.

```cpp
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>설명

이 클래스는에서 정리 작업을 수행 하지 않습니다 `Terminate` .

## <a name="see-also"></a>참고 항목

[CThreadPool 클래스](../../atl/reference/cthreadpool-class.md)<br/>
[작업자 원형](../../atl/reference/worker-archetype.md)<br/>
[클래스](../../atl/reference/atl-classes.md)
