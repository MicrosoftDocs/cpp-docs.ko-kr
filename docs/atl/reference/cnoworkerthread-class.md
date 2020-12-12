---
description: '자세한 정보: Cno작업 스레드 클래스'
title: Cno, Thread 클래스
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: 5159c04a8390f8933291f697faccedb7353fb48e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141416"
---
# <a name="cnoworkerthread-class"></a>Cno, Thread 클래스

`MonitorClass`동적 캐시 유지 관리를 사용 하지 않도록 설정 하려는 경우 클래스를 캐시 하는 템플릿 매개 변수에 대 한 인수로이 클래스를 사용 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CNoWorkerThread
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cno작업 스레드:: AddHandle](#addhandle)|[C작업 스레드:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)의 기능에 해당 하지 않습니다.|
|[Cno작업 스레드:: AddTimer](#addtimer)|[C작업 스레드:: AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)와 동일한 기능을 수행 하지 않습니다.|
|[Cno작업 스레드:: GetThreadHandle](#getthreadhandle)|[C작업 스레드:: GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)과 동일한 기능을 수행 하지 않습니다.|
|[Cno작업 스레드:: GetThreadId](#getthreadid)|[C작업 스레드:: GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)의 기능에 해당 하지 않습니다.|
|[Cno작업 스레드:: Initialize](#initialize)|[C작업 스레드:: Initialize](../../atl/reference/cworkerthread-class.md#initialize)와 동일한 기능을 수행 하지 않습니다.|
|[Cno작업 스레드:: RemoveHandle](#removehandle)|[C작업 스레드:: RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)의 기능에 해당 하지 않습니다.|
|[Cno작업 스레드:: Shutdown](#shutdown)|[C작업 스레드:: Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)과 동일한 기능을 수행 하지 않습니다.|

## <a name="remarks"></a>설명

이 클래스는 [C이상 스레드와](../../atl/reference/cworkerthread-class.md)동일한 공용 인터페이스를 제공 합니다. 이 인터페이스는 템플릿 매개 변수를 통해 클래스를 캐시 하는 데 필요 합니다 `MonitorClass` .

이 클래스의 메서드는 아무 작업도 수행 하지 않도록 구현 됩니다. HRESULT를 반환 하는 메서드는 항상 S_OK을 반환 하 고 핸들 또는 스레드 ID를 반환 하는 메서드는 항상 0을 반환 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a> Cno작업 스레드:: AddHandle

[C작업 스레드:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)의 기능에 해당 하지 않습니다.

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>반환 값

S_OK 항상를 반환 합니다.

### <a name="remarks"></a>설명

이 클래스에서 제공 하는 구현은 아무 작업도 수행 하지 않습니다.

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a> Cno작업 스레드:: AddTimer

[C작업 스레드:: AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)와 동일한 기능을 수행 하지 않습니다.

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>반환 값

S_OK 항상를 반환 합니다.

### <a name="remarks"></a>설명

이 클래스에서 제공 하는 구현은 아무 작업도 수행 하지 않습니다.

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a> Cno작업 스레드:: GetThreadHandle

[C작업 스레드:: GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)과 동일한 기능을 수행 하지 않습니다.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>반환 값

항상 NULL을 반환합니다.

### <a name="remarks"></a>설명

이 클래스에서 제공 하는 구현은 아무 작업도 수행 하지 않습니다.

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a> Cno작업 스레드:: GetThreadId

[C작업 스레드:: GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)의 기능에 해당 하지 않습니다.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>반환 값

항상 0을 반환합니다.

### <a name="remarks"></a>설명

이 클래스에서 제공 하는 구현은 아무 작업도 수행 하지 않습니다.

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a> Cno작업 스레드:: Initialize

[C작업 스레드:: Initialize](../../atl/reference/cworkerthread-class.md#initialize)와 동일한 기능을 수행 하지 않습니다.

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>반환 값

S_OK 항상를 반환 합니다.

### <a name="remarks"></a>설명

이 클래스에서 제공 하는 구현은 아무 작업도 수행 하지 않습니다.

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a> Cno작업 스레드:: RemoveHandle

[C작업 스레드:: RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)의 기능에 해당 하지 않습니다.

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>반환 값

S_OK 항상를 반환 합니다.

### <a name="remarks"></a>설명

이 클래스에서 제공 하는 구현은 아무 작업도 수행 하지 않습니다.

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a> Cno작업 스레드:: Shutdown

[C작업 스레드:: Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)과 동일한 기능을 수행 하지 않습니다.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>반환 값

S_OK 항상를 반환 합니다.

### <a name="remarks"></a>설명

이 클래스에서 제공 하는 구현은 아무 작업도 수행 하지 않습니다.
