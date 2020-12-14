---
description: '자세한 정보: CWinThread 클래스'
title: CWinThread 클래스
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: f9f89aa6397f44c95e8958d077fe18258e3c17f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342610"
---
# <a name="cwinthread-class"></a>CWinThread 클래스

애플리케이션 내의 실행 스레드를 나타냅니다.

## <a name="syntax"></a>구문

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CWinThread:: CWinThread](#cwinthread)|`CWinThread` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWinThread:: CreateThread](#createthread)|개체의 실행을 시작 `CWinThread` 합니다.|
|[CWinThread:: ExitInstance](#exitinstance)|스레드가 종료 될 때 정리 하도록 재정의 합니다.|
|[CWinThread:: GetMainWnd](#getmainwnd)|스레드의 주 창에 대 한 포인터를 검색 합니다.|
|[CWinThread:: GetThreadPriority](#getthreadpriority)|현재 스레드의 우선 순위를 가져옵니다.|
|[CWinThread:: InitInstance](#initinstance)|을 재정의 하 여 스레드 인스턴스 초기화를 수행 합니다.|
|[CWinThread:: IsIdleMessage](#isidlemessage)|특수 메시지를 확인 합니다.|
|[CWinThread:: OnIdle](#onidle)|스레드 별 유휴 시간 처리를 수행 하려면를 재정의 합니다.|
|[CWinThread::P ostThreadMessage](#postthreadmessage)|메시지를 다른 개체에 게시 `CWinThread` 합니다.|
|[CWinThread::P reTranslateMessage](#pretranslatemessage)|Windows 함수 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)에 디스패치 되기 전에 메시지를 필터링 합니다.|
|[CWinThread::P rocessMessageFilter](#processmessagefilter)|응용 프로그램에 도달 하기 전에 특정 메시지를 가로챕니다.|
|[CWinThread::P rocessWndProcException](#processwndprocexception)|스레드의 메시지 및 명령 처리기가 throw 한 처리 되지 않은 모든 예외를 가로챕니다.|
|[CWinThread::P umpMessage](#pumpmessage)|스레드의 메시지 루프를 포함 합니다.|
|[CWinThread:: ResumeThread](#resumethread)|스레드의 일시 중단 횟수를 감소 시킵니다.|
|[CWinThread:: Run](#run)|메시지 펌프를 사용 하는 스레드에 대 한 함수 제어 기본 메시지 루프를 사용자 지정 하려면를 재정의 합니다.|
|[CWinThread:: SetThreadPriority](#setthreadpriority)|현재 스레드의 우선 순위를 설정 합니다.|
|[CWinThread:: SuspendThread](#suspendthread)|스레드의 일시 중단 횟수를 늘립니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CWinThread:: operator 핸들](#operator_handle)|개체의 핸들을 검색 `CWinThread` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CWinThread:: m_bAutoDelete](#m_bautodelete)|스레드 종료 시 개체를 삭제할지 여부를 지정 합니다.|
|[CWinThread:: m_hThread](#m_hthread)|현재 스레드에 대 한 핸들입니다.|
|[CWinThread:: m_nThreadID](#m_nthreadid)|현재 스레드의 ID입니다.|
|[CWinThread:: m_pActiveWnd](#m_pactivewnd)|OLE 서버가 활성 상태인 경우 컨테이너 응용 프로그램의 주 창에 대 한 포인터입니다.|
|[CWinThread:: m_pMainWnd](#m_pmainwnd)|응용 프로그램의 주 창에 대 한 포인터를 보유 합니다.|

## <a name="remarks"></a>설명

실행의 주 스레드는 일반적으로에서 파생 된 개체에서 제공 `CWinApp` 됩니다 `CWinApp` .는에서 파생 됩니다 `CWinThread` . 추가 `CWinThread` 개체를 사용 하면 지정 된 응용 프로그램 내에서 여러 스레드를 사용할 수 있습니다.

에서 지 원하는 두 가지 일반적인 유형의 스레드는 `CWinThread` 작업자 스레드 및 사용자 인터페이스 스레드입니다. 작업자 스레드에는 메시지 펌프가 없습니다. 예를 들어 스프레드시트 응용 프로그램에서 백그라운드 계산을 수행 하는 스레드입니다. 사용자 인터페이스 스레드에는 메시지 펌프 및 시스템에서 받은 메시지 처리가 있습니다. [CWinApp](../../mfc/reference/cwinapp-class.md) 및 클래스에서 파생 된 클래스는 사용자 인터페이스 스레드의 예제입니다. 다른 사용자 인터페이스 스레드도에서 직접 파생 될 수도 있습니다 `CWinThread` .

클래스의 개체는 `CWinThread` 일반적으로 스레드 기간 동안 존재 합니다. 이 동작을 수정 하려는 경우 [m_bAutoDelete](#m_bautodelete) 을 FALSE로 설정 합니다.

`CWinThread`클래스는 코드와 MFC를 완전히 스레드로부터 안전 하 게 보호 하는 데 필요 합니다. 스레드 관련 정보를 유지 하기 위해 프레임 워크에서 사용 하는 스레드 로컬 데이터는 개체를 통해 관리 됩니다 `CWinThread` . 에서 스레드 로컬 데이터를 처리 하기 위해 이러한 종속성으로 인해 mfc를 `CWinThread` 사용 하는 모든 스레드는 mfc에서 만들어야 합니다. 예를 들어 런타임 함수를 사용 하 여 만든 스레드는 MFC Api를 사용할 수 [_beginthreadex _beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) .

스레드를 만들려면 [AfxBeginThread](application-information-and-management.md#afxbeginthread)를 호출 합니다. 작업자 또는 사용자 인터페이스 스레드를 원하는 지 여부에 따라 두 가지 형식이 있습니다. 사용자 인터페이스 스레드를 원하는 경우 `AfxBeginThread` 파생 클래스의에 대 한 포인터에를 전달 `CRuntimeClass` `CWinThread` 합니다. 작업자 스레드를 만들려는 경우 `AfxBeginThread` 제어 함수에 대 한 포인터와 매개 변수를 제어 함수로 전달 합니다. 작업자 스레드와 사용자 인터페이스 스레드 모두에 대해 우선 순위, 스택 크기, 생성 플래그 및 보안 특성을 수정 하는 선택적 매개 변수를 지정할 수 있습니다. `AfxBeginThread` 는 새 개체에 대 한 포인터를 반환 `CWinThread` 합니다.

를 호출 하 `AfxBeginThread` 는 대신 파생 개체를 생성 한 다음를 호출할 수 있습니다 `CWinThread` `CreateThread` . 이 2 단계 생성 방법은 `CWinThread` 스레드 실행의 연속 생성 및 종료 사이에 개체를 다시 사용 하려는 경우에 유용 합니다.

에 대 한 자세한 내용은 `CWinThread` [c + + 및 MFC를 사용](../../parallel/multithreading-with-cpp-and-mfc.md)하는 다중 스레딩 문서, [다중 스레딩: User-Interface 스레드 만들기](../../parallel/multithreading-creating-user-interface-threads.md), [다중 스레딩: 작업자 스레드 만들기](../../parallel/multithreading-creating-worker-threads.md)및 [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a> CWinThread:: CreateThread

호출 프로세스의 주소 공간 내에서 실행할 스레드를 만듭니다.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>매개 변수

*dwCreateFlags*<br/>
스레드의 생성을 제어 하는 추가 플래그를 지정 합니다. 이 플래그는 다음 두 값 중 하나를 포함할 수 있습니다.

- 일시 중단 횟수가 1 인 스레드를 시작 CREATE_SUSPENDED 합니다. `CWinThread`스레드의 실행을 시작 하기 전에 [m_bAutoDelete](#m_bautodelete) 또는 파생 클래스의 멤버와 같은 개체의 멤버 데이터를 초기화 하려면 CREATE_SUSPENDED를 사용 합니다. 초기화가 완료 되 면 [CWinThread:: ResumeThread](#resumethread) 를 사용 하 여 실행 스레드를 시작 합니다. 스레드는가 호출 될 때까지 실행 되지 않습니다 `CWinThread::ResumeThread` .

- **0** 생성 후 즉시 스레드를 시작 합니다.

*nStackSize*<br/>
새 스레드에 대 한 스택의 크기 (바이트)를 지정 합니다. **0** 인 경우 스택 크기는 기본적으로 프로세스의 주 스레드 크기와 동일 하 게 설정 됩니다.

*lpSecurityAttrs*<br/>
스레드에 대 한 보안 특성을 지정 하는 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

스레드가 성공적으로 생성 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`AfxBeginThread`를 사용 하 여 스레드 개체를 만들고 한 단계로 실행 합니다. 스레드 `CreateThread` 실행의 연속 생성 및 종료 사이에 스레드 개체를 다시 사용 하려면를 사용 합니다.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a> CWinThread:: CWinThread

`CWinThread` 개체를 생성합니다.

```
CWinThread();
```

### <a name="remarks"></a>설명

스레드의 실행을 시작 하려면 [CreateThread](#createthread) 멤버 함수를 호출 합니다. 일반적으로이 생성자 및를 호출 하는 [AfxBeginThread](application-information-and-management.md#afxbeginthread)를 호출 하 여 스레드를 만듭니다 `CreateThread` .

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a> CWinThread:: ExitInstance

거의 재정의 되지 않은 [실행](#run) 멤버 함수 내에서이 스레드의 인스턴스를 종료 하거나 [InitInstance](#initinstance) 에 대 한 호출이 실패할 경우 프레임 워크에서 호출 됩니다.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>반환 값

스레드의 종료 코드입니다. 0은 오류가 없음을 나타내고 0 보다 큰 값은 오류를 나타냅니다. [Getexitcodethread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)를 호출 하 여이 값을 검색할 수 있습니다.

### <a name="remarks"></a>설명

멤버 함수 내에서는 어디에서 나이 멤버 함수를 호출 하지 마세요 `Run` . 이 멤버 함수는 사용자 인터페이스 스레드에만 사용 됩니다.

이 함수의 기본 구현은 `CWinThread` [m_bAutoDelete](#m_bautodelete) TRUE 인 경우 개체를 삭제 합니다. 스레드가 종료 될 때 추가 정리를 수행 하려는 경우이 함수를 재정의 합니다. 구현에서 `ExitInstance` 코드를 실행 한 후 기본 클래스 버전을 호출 해야 합니다.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a> CWinThread:: GetMainWnd

응용 프로그램이 OLE 서버인 경우이 함수를 호출 하 여 응용 프로그램 개체의 멤버를 직접 참조 하는 대신 응용 프로그램의 활성 주 창에 대 한 포인터를 검색 `m_pMainWnd` 합니다.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>반환 값

이 함수는 두 가지 windows 형식 중 하나에 대 한 포인터를 반환 합니다. 스레드가 OLE 서버의 일부이 고 활성 컨테이너 내에서 내부 활성 상태인 개체를 포함 하는 경우이 함수는 개체의 [CWinApp:: m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) 데이터 멤버를 반환 합니다 `CWinThread` .

컨테이너 내에서 내부 활성 상태인 개체가 없거나 응용 프로그램이 OLE 서버가 아닌 경우이 함수는 스레드 개체의 [m_pMainWnd](#m_pmainwnd) 데이터 멤버를 반환 합니다.

### <a name="remarks"></a>설명

사용자 인터페이스 스레드의 경우이는 `m_pActiveWnd` 응용 프로그램 개체의 멤버를 직접 참조 하는 것과 같습니다.

애플리케이션이 OLE 서버가 아닌 경우 이 함수의 호출은 애플리케이션 개체의 `m_pMainWnd` 멤버를 직접 참조하는 것과 동일합니다.

기본 동작을 수정 하려면이 함수를 재정의 합니다.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a> CWinThread:: GetThreadPriority

이 스레드의 현재 스레드 우선 순위 수준을 가져옵니다.

```
int GetThreadPriority();
```

### <a name="return-value"></a>반환 값

우선 순위 클래스 내의 현재 스레드 우선 순위 수준입니다. 반환 되는 값은 다음 중 하나 이며, 가장 높은 우선 순위에서 가장 낮은 값으로 나열 됩니다.

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

이러한 우선 순위에 대 한 자세한 내용은 Windows SDK [Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 를 참조 하십시오.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a> CWinThread:: InitInstance

`InitInstance` 사용자 인터페이스 스레드의 새 인스턴스를 초기화 하려면를 재정의 해야 합니다.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

일반적으로를 재정의 하 여 `InitInstance` 스레드를 처음 만들 때 완료 해야 하는 작업을 수행 합니다.

이 멤버 함수는 사용자 인터페이스 스레드에만 사용 됩니다. [AfxBeginThread](application-information-and-management.md#afxbeginthread)에 전달 된 제어 함수에서 작업자 스레드를 초기화 합니다.

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a> CWinThread:: IsIdleMessage

`OnIdle`특정 메시지를 생성 한 후에 호출 되지 않도록이 함수를 재정의 합니다.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

*pMsg*<br/>
현재 처리 중인 메시지를 가리킵니다.

### <a name="return-value"></a>반환 값

`OnIdle`메시지 처리 후를 호출 해야 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`OnIdle`중복 된 마우스 메시지와 깜박이는 캐럿 메시지를 생성 한 후 기본 구현에서는를 호출 하지 않습니다.

응용 프로그램에서 짧은 타이머를 만든 경우가 `OnIdle` 자주 호출 되어 성능 문제가 발생 합니다. 이러한 응용 프로그램의 성능을 향상 시키려면 `IsIdleMessage` 응용 프로그램의 파생 클래스에서를 재정의 하 여 다음과 `CWinApp` 같이 WM_TIMER 메시지를 확인 합니다.

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

이러한 방식으로 WM_TIMER를 처리 하면 짧은 타이머를 사용 하는 응용 프로그램의 성능이 향상 됩니다.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a> CWinThread:: m_bAutoDelete

스레드 종료 시 `CWinThread` 개체를 자동으로 삭제할지 여부를 지정합니다.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>설명

`m_bAutoDelete`데이터 멤버는 BOOL 형식의 공용 변수입니다.

값은 `m_bAutoDelete` 기본 스레드 핸들을 닫는 방법에는 영향을 주지 않지만 핸들을 닫는 타이밍에는 영향을 주지 않습니다. 스레드 핸들은 항상 `CWinThread` 개체가 제거될 때 닫힙니다.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a> CWinThread:: m_hThread

이에 연결 된 스레드에 대 한 핸들 `CWinThread` 입니다.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>설명

`m_hThread`데이터 멤버는 핸들 형식의 공용 변수입니다. 기본 커널 스레드 개체가 현재 존재 하 고 핸들이 아직 닫히지 않은 경우에만 유효 합니다.

CWinThread 소멸자는에서 CloseHandle을 호출 `m_hThread` 합니다. 스레드가 종료 될 때 [M_BAUTODELETE](#m_bautodelete) TRUE 이면 cwinthread 개체가 제거 되어 cwinthread 개체 및 해당 멤버 변수에 대 한 모든 포인터를 무효화 합니다. `m_hThread`스레드 종료 값을 확인 하거나 신호를 대기 하려면 멤버가 필요할 수 있습니다. 스레드 실행 중에 CWinThread 개체와 해당 멤버를 유지 하 `m_hThread` 고 종료 된 후에는 `m_bAutoDelete` 스레드 실행을 계속 하기 전에 FALSE로 설정 합니다. 그렇지 않으면 스레드를 종료 하 고, CWinThread 개체를 삭제 하 고,이를 사용 하기 전에 핸들을 닫을 수 있습니다. 이 기법을 사용 하는 경우 CWinThread 개체를 삭제 해야 합니다.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a> CWinThread:: m_nThreadID

이에 연결 된 스레드의 ID `CWinThread` 입니다.

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>설명

`m_nThreadID`데이터 멤버는 DWORD 형식의 공용 변수입니다. 기본 커널 스레드 개체가 현재 존재 하는 경우에만 유효 합니다.
또한 [m_hThread](#m_hthread) 수명에 대 한 설명을 참조 하세요.

### <a name="example"></a>예제

  [AfxGetThread](application-information-and-management.md#afxgetthread)의 예제를 참조 하세요.

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a> CWinThread:: m_pActiveWnd

이 데이터 멤버를 사용 하 여 스레드의 활성 창 개체에 대 한 포인터를 저장 합니다.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>설명

에서 참조 하는 창이 닫히면 MFC 라이브러리이 자동으로 스레드를 종료 `m_pActiveWnd` 합니다. 이 스레드가 응용 프로그램의 주 스레드인 경우에도 응용 프로그램이 종료 됩니다. 이 데이터 멤버가 NULL 이면 응용 프로그램의 개체에 대 한 활성 창이 `CWinApp` 상속 됩니다. `m_pActiveWnd` 는 형식의 공용 변수입니다 `CWnd*` .

일반적으로를 재정의할 때이 멤버 변수를 설정 `InitInstance` 합니다. 작업자 스레드에서이 데이터 멤버의 값은 부모 스레드에서 상속 됩니다.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a> CWinThread:: m_pMainWnd

이 데이터 멤버를 사용 하 여 스레드의 주 창 개체에 대 한 포인터를 저장 합니다.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>설명

에서 참조 하는 창이 닫히면 MFC 라이브러리이 자동으로 스레드를 종료 `m_pMainWnd` 합니다. 이 스레드가 응용 프로그램의 주 스레드인 경우에도 응용 프로그램이 종료 됩니다. 이 데이터 멤버가 NULL 이면 응용 프로그램의 개체에 대 한 주 창이 `CWinApp` 스레드 종료 시기를 결정 하는 데 사용 됩니다. `m_pMainWnd` 는 형식의 공용 변수입니다 `CWnd*` .

일반적으로를 재정의할 때이 멤버 변수를 설정 `InitInstance` 합니다. 작업자 스레드에서이 데이터 멤버의 값은 부모 스레드에서 상속 됩니다.

## <a name="cwinthreadonidle"></a><a name="onidle"></a> CWinThread:: OnIdle

유휴 시간 처리를 수행 하려면이 멤버 함수를 재정의 합니다.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>매개 변수

*lCount*<br/>
`OnIdle`스레드의 메시지 큐가 비어 있을 때가 호출 될 때마다 증가 하는 카운터입니다. 이 개수는 새 메시지가 처리 될 때마다 0으로 다시 설정 됩니다. *Lcount* 매개 변수를 사용 하 여 메시지를 처리 하지 않고 스레드가 유휴 상태로 유지 된 시간의 상대 길이를 확인할 수 있습니다.

### <a name="return-value"></a>반환 값

0이 아니면 유휴 처리 시간을 더 받습니다. 유휴 처리 시간이 더 이상 필요 하지 않은 경우 0입니다.

### <a name="remarks"></a>설명

`OnIdle` 는 스레드의 메시지 큐가 비어 있을 때 기본 메시지 루프에서 호출 됩니다. 재정의를 사용 하 여 사용자 고유의 백그라운드 유휴 처리기 작업을 호출 합니다.

`OnIdle` 는 추가 유휴 처리 시간이 필요 하지 않음을 나타내려면 0을 반환 해야 합니다. *Lcount* 매개 변수는 `OnIdle` 메시지 큐가 비어 있을 때가 호출 될 때마다 증가 하며 새 메시지가 처리 될 때마다 0으로 다시 설정 됩니다. 이 수에 따라 다른 유휴 루틴을 호출할 수 있습니다.

이 멤버 함수의 기본 구현에서는 메모리에서 임시 개체 및 사용 되지 않는 동적 링크 라이브러리를 해제 합니다.

이 멤버 함수는 사용자 인터페이스 스레드에만 사용 됩니다.

응용 프로그램은가 반환 될 때까지 메시지를 처리할 수 없기 때문에 `OnIdle` 이 함수에서 긴 작업을 수행 하지 마십시오.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a> CWinThread:: operator 핸들

개체의 핸들을 검색 `CWinThread` 합니다.

```
operator HANDLE() const;
```

### <a name="return-value"></a>반환 값

성공 하면 스레드 개체의 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

핸들을 사용 하 여 Windows Api를 직접 호출 합니다.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a> CWinThread::P ostThreadMessage

사용자 정의 메시지를 다른 개체에 게시 하기 위해 호출 `CWinThread` 됩니다.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*message*<br/>
사용자 정의 메시지의 ID입니다.

*wParam*<br/>
첫 번째 메시지 매개 변수입니다.

*lParam*<br/>
두 번째 메시지 매개 변수입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

게시 된 메시지는 메시지 맵 매크로 ON_THREAD_MESSAGE에서 적절 한 메시지 처리기에 매핑됩니다.

> [!NOTE]
> [Postthreadmessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)를 호출 하면 메시지가 스레드의 메시지 큐에 배치 됩니다. 그러나 이러한 방식으로 게시 된 메시지는 창과 연결 되어 있지 않기 때문에 MFC는 메시지 또는 명령 처리기로 디스패치하지 않습니다. 이러한 메시지를 처리 하기 위해 `PreTranslateMessage()` CWinApp 파생 클래스의 함수를 재정의 하 고 메시지를 수동으로 처리 합니다.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a> CWinThread::P reTranslateMessage

Windows 함수 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)로 디스패치 되기 전에 창 메시지를 필터링 하려면이 함수를 재정의 합니다.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

*pMsg*<br/>
처리할 메시지를 포함 하는 [MSG 구조체](/windows/win32/api/winuser/ns-winuser-msg) 를 가리킵니다.

### <a name="return-value"></a>반환 값

에서 메시지를 완전히 처리 `PreTranslateMessage` 하 고 추가로 처리 하지 않아야 하는 경우 0이 아닙니다. 메시지를 일반적인 방식으로 처리 해야 하는 경우 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 사용자 인터페이스 스레드에만 사용 됩니다.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a> CWinThread::P rocessMessageFilter

프레임 워크의 후크 함수는이 멤버 함수를 호출 하 여 특정 Windows 메시지를 필터링 하 고 응답 합니다.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>매개 변수

*code*<br/>
후크 코드를 지정 합니다. 이 멤버 함수는 코드를 사용 하 여 Lpmsg를 처리 하는 방법을 결정 *합니다.*

*lpMsg*<br/>
Windows [MSG 구조체](/windows/win32/api/winuser/ns-winuser-msg)에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메시지가 처리 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

후크 함수는 응용 프로그램의 일반 메시지 처리에 전송 되기 전에 이벤트를 처리 합니다.

이 고급 기능을 재정의 하는 경우에는 기본 클래스 버전을 호출 하 여 프레임 워크의 후크 처리를 유지 해야 합니다.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a> CWinThread::P rocessWndProcException

처리기가 스레드의 메시지 또는 명령 처리기 중 하나에서 throw 된 예외를 catch 하지 않을 때마다 프레임 워크는이 멤버 함수를 호출 합니다.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

*e*<br/>
처리 되지 않은 예외를 가리킵니다.

*pMsg*<br/>
프레임 워크에서 예외를 throw 한 windows 메시지에 대 한 정보를 포함 하는 [MSG 구조체](/windows/win32/api/winuser/ns-winuser-msg) 를 가리킵니다.

### <a name="return-value"></a>반환 값

WM_CREATE 예외가 생성 되 면-1입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 직접 호출 하지 마세요.

이 멤버 함수의 기본 구현은 다음 메시지에서 생성 된 예외만 처리 합니다.

|명령|작업|
|-------------|------------|
|WM_CREATE|실패|
|WM_PAINT|영향을 받는 창의 유효성을 검사 하 여 다른 WM_PAINT 메시지가 생성 되는 것을 방지 합니다.|

예외에 대 한 전역 처리를 제공 하려면이 멤버 함수를 재정의 합니다. 기본 동작을 표시 하려는 경우에만 기본 기능을 호출 합니다.

이 멤버 함수는 메시지 펌프가 있는 스레드에서만 사용 됩니다.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a> CWinThread::P umpMessage

스레드의 메시지 루프를 포함 합니다.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>설명

`PumpMessage` 스레드의 메시지 루프를 포함 합니다. `PumpMessage` 는 `CWinThread` 스레드 메시지를 펌프 하기 위해에서 호출 합니다. `PumpMessage`을 직접 호출 하 여 메시지를 처리 하도록 하거나를 재정의 하 여 `PumpMessage` 기본 동작을 변경할 수 있습니다.

`PumpMessage`고급 사용자 에게만를 직접 호출 하 고 기본 동작을 재정의 하는 것이 좋습니다.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a> CWinThread:: ResumeThread

[SuspendThread](#suspendthread) 멤버 함수에 의해 일시 중단 된 스레드 또는 CREATE_SUSPENDED 플래그를 사용 하 여 만든 스레드 실행을 다시 시작 하기 위해 호출 됩니다.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>반환 값

성공 하는 경우 스레드의 이전 일시 중단 수입니다. `0xFFFFFFFF` 그렇지 않으면입니다. 반환 값이 0 이면 현재 스레드가 일시 중단 되지 않은 것입니다. 반환 값이 1 이면 스레드가 일시 중단 되지만 이제 다시 시작 됩니다. 반환 값이 1 보다 크면 스레드가 일시 중단 된 상태로 유지 됩니다.

### <a name="remarks"></a>설명

현재 스레드의 일시 중단 횟수가 1로 줄어듭니다. 일시 중단 횟수가 0으로 줄어들면 스레드가 실행을 다시 시작 합니다. 그렇지 않으면 스레드가 일시 중단 된 상태로 유지 됩니다.

## <a name="cwinthreadrun"></a><a name="run"></a> CWinThread:: Run

사용자 인터페이스 스레드에 대 한 기본 메시지 루프를 제공 합니다.

```
virtual int Run();
```

### <a name="return-value"></a>반환 값

**`int`** 스레드에서 반환 하는 값입니다. [Getexitcodethread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)를 호출 하 여이 값을 검색할 수 있습니다.

### <a name="remarks"></a>설명

`Run` 응용 프로그램이 [WM_QUIT](/windows/win32/winmsg/wm-quit) 메시지를 받을 때까지 Windows 메시지를 가져와 디스패치합니다. 스레드의 메시지 큐가 현재 메시지를 포함 하지 않는 경우를 `Run` 호출 `OnIdle` 하 여 유휴 시간 처리를 수행 합니다. 들어오는 메시지는 특수 처리를 위해 [PreTranslateMessage](#pretranslatemessage) 멤버 함수로 이동 하 고 표준 키보드 번역의 경우 Windows 함수 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 로 이동 합니다. 마지막으로 [Dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 함수를 호출 합니다.

`Run` 는 거의 재정의 되지 않지만 특수 동작을 구현 하도록 재정의할 수 있습니다.

이 멤버 함수는 사용자 인터페이스 스레드에만 사용 됩니다.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a> CWinThread:: SetThreadPriority

이 함수는 우선 순위 클래스 내에서 현재 스레드의 우선 순위 수준을 설정 합니다.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>매개 변수

*n 우선 순위*<br/>
우선 순위 클래스 내의 새 스레드 우선 순위 수준을 지정 합니다. 이 매개 변수는 다음 값 중 하나 여야 하며, 가장 높은 우선 순위에서 가장 낮은 값으로 나열 됩니다.

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

이러한 우선 순위에 대 한 자세한 내용은 Windows SDK [Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 를 참조 하십시오.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[CreateThread](#createthread) 가 성공적으로 반환 된 후에만 호출할 수 있습니다.

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a> CWinThread:: SuspendThread

현재 스레드의 일시 중단 횟수를 늘립니다.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>반환 값

성공 하는 경우 스레드의 이전 일시 중단 수입니다. `0xFFFFFFFF` 그렇지 않으면입니다.

### <a name="remarks"></a>설명

스레드의 일시 중단 횟수가 0 보다 높으면 해당 스레드는 실행 되지 않습니다. [ResumeThread](#resumethread) 멤버 함수를 호출 하 여 스레드를 다시 시작할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWinApp 클래스](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)
