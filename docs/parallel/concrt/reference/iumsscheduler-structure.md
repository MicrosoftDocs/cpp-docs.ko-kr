---
description: '자세한 정보: IUMSScheduler 구조체'
title: IUMSScheduler 구조체
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: e42a2e3d39e568ba12cd681053406ce88c7b5dba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334341"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 구조체

동시성 런타임의 리소스 관리자를 통해 UMS(사용자 모드 예약 가능) 스레드를 전달하려는 작업 스케줄러의 추상화에 대한 인터페이스입니다. 리소스 관리자는 이 인터페이스를 사용하여 UMS 스레드 스케줄러와 통신합니다. `IUMSScheduler` 인터페이스는 `IScheduler` 인터페이스에서 상속됩니다.

## <a name="syntax"></a>구문

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IUMSScheduler:: SetCompletionList](#setcompletionlist)|인터페이스를 `IUMSCompletionList` UMS 스레드 스케줄러에 할당 합니다.|

## <a name="remarks"></a>설명

리소스 관리자와 통신 하는 사용자 지정 스케줄러를 구현 하는 경우, 일반 Win32 스레드 대신에 UMS 스레드를 스케줄러에 전달 하려면 인터페이스의 구현을 제공 해야 합니다 `IUMSScheduler` . 또한 스케줄러 정책 키에 대 한 정책 값을로 설정 해야 합니다 `SchedulerKind` `UmsThreadDefault` . 정책에서 UMS 스레드를 지정 하는 경우 `IScheduler` [iresourcemanager:: registerscheduler](iresourcemanager-structure.md#registerscheduler) 메서드에 매개 변수로 전달 되는 인터페이스는 인터페이스 여야 합니다 `IUMSScheduler` .

리소스 관리자은 ums 기능이 있는 운영 체제에만 UMS 스레드를 전달할 수 있습니다. Windows 7 이상 버전의 64 비트 운영 체제는 UMS 스레드를 지원 합니다. 키가 값으로 설정 된 스케줄러 정책을 만들고 `SchedulerKind` `UmsThreadDefault` 기본 플랫폼이 UMS를 지원 하지 않는 경우 `SchedulerKind` 해당 정책의 키 값이 값으로 변경 됩니다 `ThreadScheduler` . UMS 스레드를 수신 하기 전에 항상이 정책 값을 읽어야 합니다.

`IUMSScheduler`인터페이스는 스케줄러와 리소스 관리자 간의 양방향 통신 채널의 한쪽 끝입니다. 다른 끝은 `IResourceManager` 리소스 관리자에서 구현 하는 및 인터페이스로 표시 됩니다 `ISchedulerProxy` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a> IUMSScheduler:: SetCompletionList 메서드

인터페이스를 `IUMSCompletionList` UMS 스레드 스케줄러에 할당 합니다.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>매개 변수

*pCompletionList 목록*<br/>
스케줄러에 대 한 완성 목록 인터페이스입니다. 스케줄러 당 단일 목록이 있습니다.

### <a name="remarks"></a>설명

리소스 관리자는 스케줄러가 리소스의 초기 할당을 요청한 후에 UMS 스레드에 대해이 메서드를 호출 합니다. Scheduler는 인터페이스를 사용 `IUMSCompletionList` 하 여 UMS 스레드 프록시의 차단이 해제 된 시기를 확인할 수 있습니다. 이 인터페이스는 UMS 스케줄러에 할당 된 가상 프로세서 루트에서 실행 되는 스레드 프록시에서이 인터페이스에 액세스 하는 경우에만 유효 합니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler 구조체](ischeduler-structure.md)<br/>
[IUMSCompletionList 구조체](iumscompletionlist-structure.md)<br/>
[IResourceManager 구조체](iresourcemanager-structure.md)
