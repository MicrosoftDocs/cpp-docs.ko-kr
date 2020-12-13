---
description: '자세히 알아보기: ITopologyNode Structure'
title: ITopologyNode 구조체
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 1d603e35728791ff94e43b03d890061dec834660
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334360"
---
# <a name="itopologynode-structure"></a>ITopologyNode 구조체

리소스 관리자에 의해 정의된 토폴로지 노드에 대한 인터페이스입니다. 노드는 하나 이상의 실행 리소스를 포함합니다.

## <a name="syntax"></a>구문

```cpp
struct ITopologyNode;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[ITopologyNode:: GetExecutionResourceCount](#getexecutionresourcecount)|이 노드 아래에 함께 그룹화된 실행 리소스의 수를 반환합니다.|
|[ITopologyNode:: GetFirstExecutionResource](#getfirstexecutionresource)|열거 순서에서 이 노드 아래에 그룹화된 첫 번째 실행 리소스를 반환합니다.|
|[ITopologyNode:: GetId](#getid)|이 노드에 대 한 리소스 관리자의 고유 식별자를 반환 합니다.|
|[ITopologyNode:: GetNext](#getnext)|열거 순서에 따라 다음 토폴로지 노드로 인터페이스를 반환합니다.|
|[ITopologyNode:: GetNumaNode](#getnumanode)|이 리소스 Maanger 노드가 속한 Windows 할당 NUMA 노드 번호를 반환 합니다.|

## <a name="remarks"></a>설명

이 인터페이스는 일반적으로 리소스 관리자에서 관찰 되는 시스템의 토폴로지를 탐색 하는 데 사용 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ITopologyNode`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a> ITopologyNode:: GetExecutionResourceCount 메서드

이 노드 아래에 함께 그룹화된 실행 리소스의 수를 반환합니다.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>반환 값

이 노드 아래에 함께 그룹화된 실행 리소스의 수입니다.

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a> ITopologyNode:: GetFirstExecutionResource 메서드

열거 순서에서 이 노드 아래에 그룹화된 첫 번째 실행 리소스를 반환합니다.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>반환 값

열거 순서에서 이 노드 아래에 그룹화된 첫 번째 실행 리소스입니다.

## <a name="itopologynodegetid-method"></a><a name="getid"></a> ITopologyNode:: GetId 메서드

이 노드에 대 한 리소스 관리자의 고유 식별자를 반환 합니다.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>반환 값

이 노드에 대 한 리소스 관리자의 고유 식별자입니다.

### <a name="remarks"></a>설명

동시성 런타임 프로세서 노드 그룹의 시스템에 있는 하드웨어 스레드를 나타냅니다. 노드는 일반적으로 시스템의 하드웨어 토폴로지에서 파생 됩니다. 예를 들어 특정 소켓 또는 특정 NUMA 노드의 모든 프로세서는 동일한 프로세서 노드에 속할 수 있습니다. 리소스 관리자은 (으)로 시작 하 여 이러한 노드에 고유 식별자를 할당 합니다 `0` `nodeCount - 1` . 여기서은 `nodeCount` 시스템의 총 프로세서 노드 수를 나타냅니다.

[GetProcessorNodeCount](concurrency-namespace-functions.md)함수에서 노드 수를 가져올 수 있습니다.

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a> ITopologyNode:: GetNext 메서드

열거 순서에 따라 다음 토폴로지 노드로 인터페이스를 반환합니다.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>반환 값

열거 순서에서 다음 노드에 대한 인터페이스입니다. 시스템 토폴로지의 열거 순서에 노드가 더 이상 없을 경우 이 메서드는 `NULL` 값을 반환합니다.

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a> ITopologyNode:: GetNumaNode 메서드

이 리소스 Maanger 노드가 속한 Windows 할당 NUMA 노드 번호를 반환 합니다.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>반환 값

이 리소스 관리자 노드가 속한 Windows 할당 NUMA 노드 번호입니다.

### <a name="remarks"></a>설명

이 노드에 속한 가상 프로세서 루트에서 실행 되는 스레드 프록시는 최소한이 메서드에서 반환 된 NUMA 노드에 대 한 NUMA 노드 수준 이상의 선호도를 가집니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
