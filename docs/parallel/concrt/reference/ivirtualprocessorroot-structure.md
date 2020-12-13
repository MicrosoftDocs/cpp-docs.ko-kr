---
description: '자세히 알아보기: IVirtualProcessorRoot Structure'
title: IVirtualProcessorRoot 구조체
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: b55aa72e9383447ea8d19e13e1e2aa9bd57d267d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334306"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 구조체

스레드 프록시가 실행될 수 있는 하드웨어 스레드의 추상화입니다.

## <a name="syntax"></a>구문

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IVirtualProcessorRoot:: Activate](#activate)|실행 컨텍스트 인터페이스와 연결 된 스레드 프록시가 `pContext` 이 가상 프로세서 루트에서 실행 되기 시작 합니다.|
|[IVirtualProcessorRoot::D eactivate](#deactivate)|이 가상 프로세서 루트에서 현재 실행 중인 스레드 프록시가 실행 컨텍스트 디스패치를 중지 하도록 합니다. 스레드 프록시는 메서드에 대 한 호출에서 실행을 다시 시작 합니다 `Activate` .|
|[IVirtualProcessorRoot:: EnsureAllTasksVisible](#ensurealltasksvisible)|개별 프로세서의 메모리 계층에 저장 된 데이터가 시스템의 모든 프로세서에 표시 됩니다. 메서드가 반환 되기 전에 모든 프로세서에서 전체 메모리 펜스가 실행 되었는지 확인 합니다.|
|[IVirtualProcessorRoot:: GetId](#getid)|가상 프로세서 루트에 대 한 고유 식별자를 반환 합니다.|

## <a name="remarks"></a>설명

모든 가상 프로세서 루트에는 연결 된 실행 리소스가 있습니다. `IVirtualProcessorRoot`인터페이스는 [Iexecutionresource](iexecutionresource-structure.md) 인터페이스에서 상속 됩니다. 여러 가상 프로세서 루트는 동일한 기본 하드웨어 스레드에 해당할 수 있습니다.

리소스 관리자는 리소스 요청에 대 한 응답으로 스케줄러에 가상 프로세서 루트를 부여 합니다. 스케줄러는 실행 컨텍스트로 활성화 하 여 작업을 수행 하는 데 가상 프로세서 루트를 사용할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a> IVirtualProcessorRoot:: Activate 메서드

실행 컨텍스트 인터페이스와 연결 된 스레드 프록시가 `pContext` 이 가상 프로세서 루트에서 실행 되기 시작 합니다.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>매개 변수

*pContext*<br/>
이 가상 프로세서 루트에서 디스패치되는 실행 컨텍스트에 대 한 인터페이스입니다.

### <a name="remarks"></a>설명

실행 컨텍스트 인터페이스와 연결 되지 않은 경우 리소스 관리자는 스레드 프록시를 제공 합니다. `pContext`

메서드를 사용 하 여 리소스 관리자에서 반환 하는 `Activate` 새 가상 프로세서 루트에서 작업 실행을 시작 하거나 비활성화 되었거나 비활성화 되는 가상 프로세서 루트에서 스레드 프록시를 다시 시작할 수 있습니다. 비활성화에 대 한 자세한 내용은 [IVirtualProcessorRoot::D eactivate](#deactivate) 를 참조 하세요. 비활성화 된 가상 프로세서 루트를 다시 시작 하는 경우 매개 변수는 `pContext` 가상 프로세서 루트를 비활성화 하는 데 사용 되는 매개 변수와 같아야 합니다.

가상 프로세서 루트를 처음 활성화 한 후에는 및에 대 한 후속 호출 쌍이 `Deactivate` `Activate` 서로 경합 할 수 있습니다. 즉,에 대 한 호출을 수신 하는 리소스 관리자에 대 한 호출을 수신 하는 데 사용할 수 `Activate` `Deactivate` 있습니다.

가상 프로세서 루트를 활성화 하는 경우이 가상 프로세서 루트가 현재 작업 중 이라는 리소스 관리자에 게 알립니다. 스케줄러가이 루트에서 실행할 작업을 찾을 수 없는 경우 `Deactivate` 가상 프로세서 루트가 유휴 상태임을 리소스 관리자 알리는 메서드를 호출 해야 합니다. 리소스 관리자는이 데이터를 사용 하 여 시스템의 부하를 분산 합니다.

`invalid_argument` 인수에 값이 있으면이 throw 됩니다 `pContext` `NULL` .

`invalid_operation` 인수가 `pContext` 이 가상 프로세서 루트에서 가장 최근에 디스패치 된 실행 컨텍스트를 나타내지 않으면이 throw 됩니다.

가상 프로세서 루트를 활성화 하는 작업은 기본 하드웨어 스레드의 구독 수준을 하나씩 늘립니다. 구독 수준에 대 한 자세한 내용은 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)을 참조 하세요.

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a> IVirtualProcessorRoot::D eactivate 메서드

이 가상 프로세서 루트에서 현재 실행 중인 스레드 프록시가 실행 컨텍스트 디스패치를 중지 하도록 합니다. 스레드 프록시는 메서드에 대 한 호출에서 실행을 다시 시작 합니다 `Activate` .

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>매개 변수

*pContext*<br/>
이 루트가 현재 디스패치 중인 컨텍스트입니다.

### <a name="return-value"></a>반환 값

부울 값입니다. 값은 **`true`** 스레드 프록시가 메서드 `Deactivate` 호출에 대 한 응답으로 메서드에서 반환 되었음을 나타냅니다 `Activate` . 값은 **`false`** 리소스 관리자의 알림 이벤트에 대 한 응답으로 메서드에서 스레드 프록시가 반환 되었음을 나타냅니다. UMS (사용자 모드 예약 가능) 스레드 스케줄러에서는 항목이 스케줄러의 완성 목록에 표시 되 고 스케줄러는이를 처리 하는 데 필요 합니다.

### <a name="remarks"></a>설명

스케줄러에서 작업을 찾을 수 없는 경우이 메서드를 사용 하 여 가상 프로세서 루트의 실행을 일시적으로 중지 합니다. `Deactivate`메서드 호출은 `Dispatch` 가상 프로세서 루트를 마지막으로 활성화 한 실행 컨텍스트의 메서드 내에서 시작 해야 합니다. 즉, 메서드를 호출 하는 스레드 프록시는 `Deactivate` 가상 프로세서 루트에서 현재 실행 되 고 있는 스레드 여야 합니다. 실행 되 고 있지 않은 가상 프로세서 루트에서 메서드를 호출 하면 정의 되지 않은 동작이 발생할 수 있습니다.

비활성화 된 가상 프로세서 루트는 메서드에 전달 된 것과 동일한 인수를 사용 하 여 메서드에 대 한 호출로 해제 될 수 있습니다 `Activate` `Deactivate` . 스케줄러는 및 메서드에 대 한 호출이 쌍을 이루어야 하는지 확인 하는 일을 담당 `Activate` `Deactivate` 하지만 특정 순서로 수신 하지 않아도 됩니다. 리소스 관리자는 `Activate` 메서드가 의도 한 메서드에 대 한 호출을 받기 전에 해당 메서드에 대 한 호출 수신을 처리할 수 있습니다 `Deactivate` .

가상 프로세서 루트 awakens 및 메서드의 반환 값 `Deactivate` 이 값 이면 **`false`** 스케줄러는 메서드를 통해 UMS 완성 목록을 쿼리하여 `IUMSCompletionList::GetUnblockNotifications` 해당 정보에 대해 작업을 수행한 다음 메서드를 다시 호출 해야 합니다 `Deactivate` . 메서드가 값을 반환할 때까지이를 반복 해야 합니다 `Deactivate` **`true`** .

`invalid_argument` 인수에 NULL 값이 있으면이 throw 됩니다 `pContext` .

`invalid_operation` 가상 프로세서 루트를 활성화 하지 않은 경우 또는 인수가 `pContext` 이 가상 프로세서 루트에서 가장 최근에 디스패치 된 실행 컨텍스트를 나타내지 않는 경우이 throw 됩니다.

가상 프로세서 루트를 비활성화 하면 기본 하드웨어 스레드의 구독 수준이 1 씩 줄어듭니다. 구독 수준에 대 한 자세한 내용은 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)을 참조 하세요.

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a> IVirtualProcessorRoot:: EnsureAllTasksVisible 메서드

개별 프로세서의 메모리 계층에 저장 된 데이터가 시스템의 모든 프로세서에 표시 됩니다. 메서드가 반환 되기 전에 모든 프로세서에서 전체 메모리 펜스가 실행 되었는지 확인 합니다.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>매개 변수

*pContext*<br/>
이 가상 프로세서 루트에서 현재 디스패치 중인 컨텍스트입니다.

### <a name="remarks"></a>설명

스케줄러에 새 작업을 추가 하 여 가상 프로세서 루트의 비활성화를 동기화 하려는 경우이 메서드를 사용 하는 것이 좋습니다. 성능상의 이유로 메모리 장벽을 실행 하지 않고 스케줄러에 작업 항목을 추가 하도록 결정할 수 있습니다. 즉, 한 프로세서에서 실행 되는 스레드에 의해 추가 된 작업 항목이 다른 모든 프로세서에 즉시 표시 되지 않습니다. 메서드와 함께이 메서드를 사용 하면 스케줄러 `Deactivate` 의 컬렉션에 작업 항목이 있는 동안 스케줄러에서 모든 가상 프로세서 루트를 비활성화 하지 않도록 보장할 수 있습니다.

`EnsureAllTasksVisibleThe`메서드 호출은 `Dispatch` 가상 프로세서 루트를 마지막으로 활성화 한 실행 컨텍스트의 메서드 내에서 시작 해야 합니다. 즉, 메서드를 호출 하는 스레드 프록시는 `EnsureAllTasksVisible` 가상 프로세서 루트에서 현재 실행 되 고 있는 스레드 여야 합니다. 실행 되 고 있지 않은 가상 프로세서 루트에서 메서드를 호출 하면 정의 되지 않은 동작이 발생할 수 있습니다.

`invalid_argument` 인수에 값이 있으면이 throw 됩니다 `pContext` `NULL` .

`invalid_operation` 가상 프로세서 루트를 활성화 하지 않은 경우 또는 인수가 `pContext` 이 가상 프로세서 루트에서 가장 최근에 디스패치 된 실행 컨텍스트를 나타내지 않는 경우이 throw 됩니다.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a> IVirtualProcessorRoot:: GetId 메서드

가상 프로세서 루트에 대 한 고유 식별자를 반환 합니다.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>반환 값

정수 식별자입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
