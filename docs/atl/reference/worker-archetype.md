---
description: '다음에 대 한 자세한 정보: Worker 원형'
title: 작업자 원형
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 8cb8c2b281bbdc074bb700b77a856f4d26c26cf6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157570"
---
# <a name="worker-archetype"></a>작업자 원형

*작업자* 원형를 준수 하는 클래스는 스레드 풀에서 큐에 대기 중인 작업 항목을 처리 하는 코드를 제공 합니다.

**구현**

이 원형을 준수 하는 클래스를 구현 하려면 클래스에서 다음 기능을 제공 해야 합니다.

|메서드|설명|
|------------|-----------------|
|[초기화](#initialize)|요청을 [실행](#execute)하기 위해 요청을 전달 하기 전에 worker 개체를 초기화 하기 위해 호출 됩니다.|
|[실행](#execute)|작업 항목을 처리 하기 위해 호출 됩니다.|
|[Terminate](#terminate)|모든 요청이 [실행](#execute)되도록 전달 된 후 작업자 개체의 초기화를 취소 하기 위해 호출 됩니다.|

|형식 정의|Description|
|-------------|-----------------|
|[RequestType](#requesttype)|Worker 클래스에서 처리할 수 있는 작업 항목의 형식에 대 한 typedef입니다.|

일반적인 *작업자* 클래스는 다음과 같습니다.

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**기존 구현**

이러한 클래스는 다음 원형을 따릅니다.

|클래스|설명|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|는 스레드 풀에서 요청을 수신 하 고 각 요청에 대해 만들어지고 소멸 된 작업자 개체에 전달 합니다.|

**사용**

이러한 템플릿 매개 변수는 클래스가이 원형을 준수 하는 것으로 간주 합니다.

|매개 변수 이름|사용 대상|
|--------------------|-------------|
|*작업자*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*작업자*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>요구 사항

**헤더:**

## <a name="workerarchetypeexecute"></a><a name="execute"></a> WorkerArchetype:: Execute

작업 항목을 처리 하기 위해 호출 됩니다.

```cpp
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>매개 변수

*요청*<br/>
처리할 작업 항목입니다. 작업 항목의 형식이와 동일 합니다 `RequestType` .

*pvWorkerParam*<br/>
Worker 클래스가 이해 하는 사용자 지정 매개 변수입니다. 및에도 `WorkerArchetype::Initialize` 전달 `Terminate` 됩니다.

*pOverlapped*<br/>
작업 항목이 큐에 대기 된 큐를 만드는 데 사용 되는 [겹쳐진](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) 구조체에 대 한 포인터입니다.

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a> WorkerArchetype:: Initialize

요청을에 전달 하기 전에 작업자 개체를 초기화 하기 위해 호출 됩니다 `WorkerArchetype::Execute` .

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>매개 변수

*pvParam*<br/>
Worker 클래스가 이해 하는 사용자 지정 매개 변수입니다. 및에도 `WorkerArchetype::Terminate` 전달 `WorkerArchetype::Execute` 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a> WorkerArchetype:: RequestType

Worker 클래스에서 처리할 수 있는 작업 항목의 형식에 대 한 typedef입니다.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>설명

이 형식은의 첫 번째 매개 변수로 사용 되어야 `WorkerArchetype::Execute` 하며 ULONG_PTR에서 캐스팅할 수 있어야 합니다.

## <a name="workerarchetypeterminate"></a><a name="terminate"></a> WorkerArchetype:: Terminate

모든 요청이에 전달 된 후 작업자 개체의 초기화를 취소 하기 위해 호출 `WorkerArchetype::Execute` 됩니다.

```cpp
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>매개 변수

*pvParam*<br/>
Worker 클래스가 이해 하는 사용자 지정 매개 변수입니다. 및에도 `WorkerArchetype::Initialize` 전달 `WorkerArchetype::Execute` 됩니다.

## <a name="see-also"></a>참고 항목

[개념](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 데스크톱 구성 요소](../../atl/atl-com-desktop-components.md)
