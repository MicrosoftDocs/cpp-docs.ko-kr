---
description: '자세한 정보: IResourceManager 구조체'
title: IResourceManager 구조체
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 1577d20f7a54bbf2f5613cd47afa22ead36b3630
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334475"
---
# <a name="iresourcemanager-structure"></a>IResourceManager 구조체

동시성 런타임의 리소스 관리자에 대한 인터페이스입니다. 스케줄러가 리소스 관리자와 통신하는 데 사용되는 인터페이스입니다.

## <a name="syntax"></a>구문

```cpp
struct IResourceManager;
```

## <a name="members"></a>멤버

### <a name="public-enumerations"></a>public 열거형

|Name|설명|
|----------|-----------------|
|[IResourceManager:: OSVersion](#osversion)|운영 체제 버전을 나타내는 열거 형식입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IResourceManager:: CreateNodeTopology](#createnodetopology)|런타임의 디버그 빌드에서만 제공 되는이 메서드는 구성과 일치 하는 실제 하드웨어를 요구 하지 않고 다양 한 하드웨어 토폴로지에서 리소스 관리자 테스트를 용이 하 게 하기 위해 설계 된 테스트 후크입니다. 런타임의 정품 빌드를 사용 하 여이 메서드는 아무 작업도 수행 하지 않고 반환 합니다.|
|[IResourceManager:: GetAvailableNodeCount](#getavailablenodecount)|리소스 관리자에서 사용할 수 있는 노드의 수를 반환합니다.|
|[IResourceManager:: GetFirstNode](#getfirstnode)|리소스 관리자를 통해 정의된 열거 순서에서 첫 번째 노드를 반환합니다.|
|[IResourceManager:: Reference](#reference)|리소스 관리자 인스턴스의 참조 횟수를 늘립니다.|
|[IResourceManager:: RegisterScheduler](#registerscheduler)|리소스 관리자를 사용 하 여 스케줄러를 등록 합니다. 스케줄러가 등록 되 면 반환 된 인터페이스를 사용 하 여 리소스 관리자와 통신 해야 합니다 `ISchedulerProxy` .|
|[IResourceManager:: Release](#release)|리소스 관리자 인스턴스의 참조 횟수를 감소 시킵니다. 참조 횟수가로 이동 하면 리소스 관리자 제거 됩니다 `0` .|

## <a name="remarks"></a>설명

[CreateResourceManager](concurrency-namespace-functions.md) 함수를 사용 하 여 singleton 리소스 관리자 인스턴스에 대 한 인터페이스를 가져옵니다. 메서드는 리소스 관리자에 대 한 참조 횟수를 증가 시키고, 리소스 관리자 작업을 마치면 [Iresourcemanager:: Release](#release) 메서드를 호출 하 여 참조를 해제 해야 합니다. 일반적으로 만드는 각 스케줄러는 생성 중에이 메서드를 호출 하 고 종료 된 후 리소스 관리자에 대 한 참조를 해제 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IResourceManager`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a> IResourceManager:: CreateNodeTopology 메서드

런타임의 디버그 빌드에서만 제공 되는이 메서드는 구성과 일치 하는 실제 하드웨어를 요구 하지 않고 다양 한 하드웨어 토폴로지에서 리소스 관리자 테스트를 용이 하 게 하기 위해 설계 된 테스트 후크입니다. 런타임의 정품 빌드를 사용 하 여이 메서드는 아무 작업도 수행 하지 않고 반환 합니다.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>매개 변수

*nodeCount*<br/>
시뮬레이션 되는 프로세서 노드 수입니다.

*pCoreCount*<br/>
각 노드의 코어 수를 지정 하는 배열입니다.

*pNodeDistance*<br/>
두 노드 간의 노드 거리를 지정 하는 행렬입니다. 이 매개 변수는 값을 가질 수 있습니다 `NULL` .

*pProcessorGroups*<br/>
각 노드가 속한 프로세서 그룹을 지정 하는 배열입니다.

### <a name="remarks"></a>설명

[](../../../standard-library/invalid-argument-class.md) 매개 변수가 `nodeCount` 값을 `0` 전달 하거나 매개 변수에 `pCoreCount` 값이 있으면 invalid_argument이 throw 됩니다 `NULL` .

프로세스에 다른 스케줄러가 있는 동안이 메서드가 호출 되는 경우 [invalid_operation](invalid-operation-class.md) throw 됩니다.

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a> IResourceManager:: GetAvailableNodeCount 메서드

리소스 관리자에서 사용할 수 있는 노드의 수를 반환합니다.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>반환 값

리소스 관리자 사용할 수 있는 노드 수입니다.

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a> IResourceManager:: GetFirstNode 메서드

리소스 관리자를 통해 정의된 열거 순서에서 첫 번째 노드를 반환합니다.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>반환 값

리소스 관리자에서 정의한 열거형 순서에서 첫 번째 노드입니다.

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a> IResourceManager:: OSVersion 열거형

운영 체제 버전을 나타내는 열거 형식입니다.

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a> IResourceManager:: Reference 메서드

리소스 관리자 인스턴스의 참조 횟수를 늘립니다.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>반환 값

결과 참조 횟수입니다.

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a> IResourceManager:: RegisterScheduler 메서드

리소스 관리자를 사용 하 여 스케줄러를 등록 합니다. 스케줄러가 등록 되 면 반환 된 인터페이스를 사용 하 여 리소스 관리자와 통신 해야 합니다 `ISchedulerProxy` .

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>매개 변수

*pScheduler*<br/>
`IScheduler`등록할 scheduler에 대 한 인터페이스입니다.

*version*<br/>
스케줄러에서 리소스 관리자와 통신 하는 데 사용 하는 통신 인터페이스의 버전입니다. 버전을 사용 하면 스케줄러에서 이전 기능에 액세스할 수 있도록 하는 동시에 리소스 관리자 통신 인터페이스를 개선할 수 있습니다. Visual Studio 2010에 있는 리소스 관리자 기능을 사용 하려는 스케줄러는 버전을 사용 해야 합니다 `CONCRT_RM_VERSION_1` .

### <a name="return-value"></a>반환 값

`ISchedulerProxy`리소스 관리자 스케줄러와 연결 된 인터페이스입니다. 스케줄러는이 인터페이스를 사용 하 여이 지점에서 리소스 관리자와 통신 해야 합니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 리소스 관리자와의 통신을 시작 합니다. 메서드는 `IScheduler` 스케줄러에 대 한 인터페이스를 인터페이스에 연결 `ISchedulerProxy` 하 고 다시 사용자에 게 전달 합니다. 반환 된 인터페이스를 사용 하 여 스케줄러에서 사용할 실행 리소스를 요청 하거나 리소스 관리자를 사용 하 여 스레드를 구독할 수 있습니다. 리소스 관리자는 [IScheduler:: getpolicy](ischeduler-structure.md#getpolicy) 메서드에서 반환 된 스케줄러 정책의 정책 요소를 사용 하 여 스케줄러가 작업을 실행 하는 데 필요한 스레드 유형을 결정 합니다. `SchedulerKind`정책 키의 값이이 `UmsThreadDefault` 고 값이 정책에서 값으로 다시 전송 되는 경우 `UmsThreadDefault` 메서드에 전달 되는 `IScheduler` 인터페이스는 인터페이스 여야 합니다 `IUMSScheduler` .

`invalid_argument`매개 변수가 `pScheduler` 값을 포함 `NULL` 하거나 매개 변수가 `version` 통신 인터페이스에 대 한 유효한 버전이 아닌 경우 메서드는 예외를 throw 합니다.

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a> IResourceManager:: Release 메서드

리소스 관리자 인스턴스의 참조 횟수를 감소 시킵니다. 참조 횟수가로 이동 하면 리소스 관리자 제거 됩니다 `0` .

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>반환 값

결과 참조 횟수입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[ISchedulerProxy 구조체](ischedulerproxy-structure.md)<br/>
[IScheduler 구조체](ischeduler-structure.md)
