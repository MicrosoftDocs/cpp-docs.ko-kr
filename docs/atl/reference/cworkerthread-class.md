---
description: '자세한 정보: C작업 스레드 클래스'
title: CWorkerThread 클래스
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: 6ba4646f2e52d3a199ba42009f53d88717c8e2c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139999"
---
# <a name="cworkerthread-class"></a>CWorkerThread 클래스

이 클래스는 작업자 스레드를 만들거나 기존 작업자 스레드를 사용 하 고, 하나 이상의 커널 개체 핸들을 대기 하 고, 핸들 중 하나가 신호를 받으면 지정 된 클라이언트 함수를 실행 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>매개 변수

*ThreadTraits*<br/>
[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 또는 [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)와 같은 스레드 생성 함수를 제공 하는 클래스입니다.

## <a name="members"></a>멤버

### <a name="protected-structures"></a>Protected 구조체

|Name|설명|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[C작업 스레드:: C작업 스레드](#cworkerthread)|작업자 스레드의 생성자입니다.|
|[C작업 스레드:: ~ C작업 스레드](#dtor)|작업자 스레드의 소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[C작업 스레드:: AddHandle](#addhandle)|작업자 스레드에 의해 유지 관리 되는 목록에 대기 가능 개체의 핸들을 추가 하려면이 메서드를 호출 합니다.|
|[C작업 스레드:: AddTimer](#addtimer)|작업자 스레드에 의해 유지 관리 되는 목록에 주기적 대기 가능 타이머를 추가 하려면이 메서드를 호출 합니다.|
|[C작업 스레드:: GetThreadHandle](#getthreadhandle)|이 메서드를 호출 하 여 작업자 스레드의 스레드 핸들을 가져옵니다.|
|[C작업 스레드:: GetThreadId](#getthreadid)|작업자 스레드의 스레드 ID를 가져오려면이 메서드를 호출 합니다.|
|[C작업 스레드:: Initialize](#initialize)|작업자 스레드를 초기화 하려면이 메서드를 호출 합니다.|
|[C작업 스레드:: RemoveHandle](#removehandle)|대기 가능 개체 목록에서 핸들을 제거 하려면이 메서드를 호출 합니다.|
|[C작업 스레드:: Shutdown](#shutdown)|이 메서드를 호출 하 여 작업자 스레드를 종료 합니다.|

## <a name="remarks"></a>설명

### <a name="to-use-cworkerthread"></a>C이상 스레드를 사용 하려면

1. 이 클래스의 인스턴스를 만듭니다.

1. [C작업 스레드:: Initialize](#initialize)를 호출 합니다.

1. 커널 개체의 핸들과 [Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)의 구현에 대 한 포인터를 사용 하 여 [c작업 스레드:: addhandle](#addhandle) 을 호출 합니다.

   \- 또는 -

   [Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)의 구현에 대 한 포인터를 사용 하 여 [c작업 스레드:: addtimer](#addtimer) 를 호출 합니다.

1. 핸들이 나 타이머가 신호를 받을 때 일부 작업을 수행 하려면 [Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) 를 구현 합니다.

1. 대기 가능 개체 목록에서 개체를 제거 하려면 [c thread:: RemoveHandle](#removehandle)을 호출 합니다.

1. 스레드를 종료 하려면 [C작업 스레드:: Shutdown](#shutdown)을 호출 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a> C작업 스레드:: AddHandle

작업자 스레드에 의해 유지 관리 되는 목록에 대기 가능 개체의 핸들을 추가 하려면이 메서드를 호출 합니다.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
대기 가능 개체에 대 한 핸들입니다.

*pClient*<br/>
핸들이 신호를 받을 때 호출 되는 개체의 [Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md) 인터페이스에 대 한 포인터입니다.

*dwParam*<br/>
핸들이 신호를 받을 때 [Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) 에 전달할 매개 변수입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) 는 *hobject* 핸들이 신호를 받으면 *pclient* 를 통해 호출 됩니다.

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a> C작업 스레드:: AddTimer

작업자 스레드에 의해 유지 관리 되는 목록에 주기적 대기 가능 타이머를 추가 하려면이 메서드를 호출 합니다.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>매개 변수

*dwInterval*<br/>
타이머의 기간 (밀리초)을 지정 합니다.

*pClient*<br/>
핸들이 신호를 받을 때 호출 되는 개체의 [Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md) 인터페이스에 대 한 포인터입니다.

*dwParam*<br/>
핸들이 신호를 받을 때 [Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) 에 전달할 매개 변수입니다.

*phTimer*<br/>
제한이 성공 시 새로 만든 타이머에 대 한 핸들을 받는 핸들 변수의 주소입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

타이머가 신호를 받으면 [Pstthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) 는 *pclient* 를 통해 호출 됩니다.

*Phtimer* 에서 [c작업 스레드:: removehandle](#removehandle) 으로 타이머 핸들을 전달 하 여 타이머를 닫습니다.

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a> C작업 스레드:: C작업 스레드

생성자입니다.

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a> C작업 스레드:: ~ C작업 스레드

소멸자입니다.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>설명

[C작업 스레드:: Shutdown](#shutdown)을 호출 합니다.

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a> C작업 스레드:: GetThreadHandle

이 메서드를 호출 하 여 작업자 스레드의 스레드 핸들을 가져옵니다.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>반환 값

는 스레드 핸들을 반환 하 고, 작업자 스레드가 초기화 되지 않았으면 NULL을 반환 합니다.

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a> C작업 스레드:: GetThreadId

작업자 스레드의 스레드 ID를 가져오려면이 메서드를 호출 합니다.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>반환 값

스레드 ID를 반환 하거나, 작업자 스레드가 초기화 되지 않은 경우 NULL을 반환 합니다.

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a> C작업 스레드:: Initialize

작업자 스레드를 초기화 하려면이 메서드를 호출 합니다.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>매개 변수

*pThread*<br/>
기존 작업자 스레드

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 개체를 만든 후 또는 [C이상 스레드:: Shutdown](#shutdown)을 호출한 후에 초기화 해야 합니다.

둘 이상의 `CWorkerThread` 개체가 동일한 작업자 스레드를 사용 하도록 하려면 인수를 전달 하지 않고 개체 중 하나를 초기화 한 다음 해당 개체에 대 한 포인터를 `Initialize` 다른 개체의 메서드에 전달 합니다. 포인터를 사용 하 여 초기화 된 개체는 개체를 초기화 하는 데 사용 되기 전에 종료 되어야 합니다.

기존 개체에 대 한 포인터를 사용 하 여 초기화 될 때 해당 메서드의 동작을 변경 하는 방법에 대 한 자세한 내용은 [C작업 스레드:: 종료](#shutdown) 를 참조 하세요.

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a> C작업 스레드:: RemoveHandle

대기 가능 개체 목록에서 핸들을 제거 하려면이 메서드를 호출 합니다.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
제거할 핸들입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

핸들이 제거 될 때 [Addhandle](#addhandle)에 전달 된 연결 된 개체에 대해 [Iworkerthreadclient:: CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) 이 호출 됩니다. 이 호출이 실패 하면 `CWorkerThread` 는 핸들에 대해 Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) 함수를 호출 합니다.

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a> C작업 스레드:: Shutdown

이 메서드를 호출 하 여 작업자 스레드를 종료 합니다.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>매개 변수

*dwWait*<br/>
작업자 스레드가 종료 될 때까지 대기 하는 시간 (밀리초)입니다. ATL_WORKER_THREAD_WAIT 기본값은 10 초입니다. 필요한 경우에는이 기호에 대 한 고유한 값을 정의할 수 있습니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 반환 하거나, 제한 시간 값 *Dwwait* 를 초과 하는 경우와 같이 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

개체를 다시 사용 하려면이 메서드를 호출한 후 [C작업 thread:: Initialize](#initialize) 를 호출 합니다.

`Shutdown`다른 개체에 대 한 포인터를 사용 하 여 초기화 된 개체에 대 한 호출은 아무런 영향을 주지 않으며 `CWorkerThread` 항상 S_OK을 반환 합니다.

## <a name="see-also"></a>참고 항목

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[클래스](../../atl/reference/atl-classes.md)<br/>
[다중 스레딩: 작업자 스레드 만들기](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient 인터페이스](../../atl/reference/iworkerthreadclient-interface.md)
