---
description: '자세히 알아보기: CAtlServiceModuleT 클래스'
title: CAtlServiceModuleT 클래스
ms.date: 05/06/2019
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 591d057437fb4386435a1f952170dfb8d6a71773
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147201"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 클래스

이 클래스는 서비스를 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CAtlServiceModuleT` 입니다.

*nServiceNameID*<br/>
서비스의 리소스 식별자입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlServiceModuleT:: CAtlServiceModuleT](#catlservicemodulet)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlServiceModuleT:: Handler](#handler)|서비스에 대 한 처리기 루틴입니다.|
|[CAtlServiceModuleT:: InitializeSecurity](#initializesecurity)|서비스에 대 한 기본 보안 설정을 제공 합니다.|
|[CAtlServiceModuleT:: Install](#install)|서비스를 설치 하 고 만듭니다.|
|[CAtlServiceModuleT:: IsInstalled](#isinstalled)|서비스가 설치 되었는지 확인 합니다.|
|[CAtlServiceModuleT:: LogEvent](#logevent)|이벤트 로그에 씁니다.|
|[CAtlServiceModuleT:: OnContinue](#oncontinue)|서비스를 계속 하려면이 메서드를 재정의 합니다.|
|[CAtlServiceModuleT:: OnInterrogate](#oninterrogate)|서비스를 검사 하려면이 메서드를 재정의 합니다.|
|[CAtlServiceModuleT:: OnPause](#onpause)|서비스를 일시 중지 하려면이 메서드를 재정의 합니다.|
|[CAtlServiceModuleT:: OnShutdown](#onshutdown)|서비스를 종료 하려면이 메서드를 재정의 합니다.|
|[CAtlServiceModuleT:: OnStop](#onstop)|서비스를 중지 하려면이 메서드를 재정의 합니다.|
|[CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest)|서비스에 대 한 알 수 없는 요청을 처리 하려면이 메서드를 재정의 합니다.|
|[CAtlServiceModuleT::P arseCommandLine](#parsecommandline)|명령줄을 구문 분석 하 고 필요한 경우 등록을 수행 합니다.|
|[CAtlServiceModuleT::P reMessageLoop](#premessageloop)|이 메서드는 메시지 루프를 입력 하기 바로 전에 호출 됩니다.|
|[CAtlServiceModuleT:: RegisterAppId](#registerappid)|레지스트리에 서비스를 등록 합니다.|
|[CAtlServiceModuleT:: Run](#run)|서비스를 실행 합니다.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|서비스 제어 관리자에 의해 호출 되는 메서드입니다.|
|[CAtlServiceModuleT:: SetServiceStatus](#setservicestatus)|서비스 상태를 업데이트 합니다.|
|[CAtlServiceModuleT:: Start](#start)|`CAtlServiceModuleT::WinMain`서비스가 시작 될 때에 의해 호출 됩니다.|
|[CAtlServiceModuleT:: Uninstall](#uninstall)|서비스를 중지 하 고 제거 합니다.|
|[CAtlServiceModuleT:: Unlock](#unlock)|서비스의 잠금 횟수를 감소 시킵니다.|
|[CAtlServiceModuleT:: UnregisterAppId](#unregisterappid)|레지스트리에서 서비스를 제거 합니다.|
|[CAtlServiceModuleT:: WinMain](#winmain)|이 메서드는 서비스를 실행 하는 데 필요한 코드를 구현 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAtlServiceModuleT:: m_bService](#m_bservice)|프로그램이 서비스로 실행 중임을 나타내는 플래그입니다.|
|[CAtlServiceModuleT:: m_dwThreadID](#m_dwthreadid)|스레드 식별자를 저장 하는 멤버 변수입니다.|
|[CAtlServiceModuleT:: m_hServiceStatus](#m_hservicestatus)|현재 서비스에 대 한 상태 정보 구조에 핸들을 저장 하는 멤버 변수입니다.|
|[CAtlServiceModuleT:: m_status](#m_status)|현재 서비스에 대 한 상태 정보 구조를 저장 하는 멤버 변수입니다.|
|[CAtlServiceModuleT:: m_szServiceName](#m_szservicename)|등록할 서비스의 이름입니다.|

## <a name="remarks"></a>설명

`CAtlServiceModuleT`[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)에서 파생 된는 ATL 서비스 모듈을 구현 합니다. `CAtlServiceModuleT` 명령줄 처리, 설치, 등록 및 제거를 위한 메서드를 제공 합니다. 추가 기능이 필요한 경우 이러한 메서드 및 기타 메서드를 재정의할 수 있습니다.

이 클래스는 이전 버전의 ATL에서 사용 되는 사용 되지 않는 [CComModule 클래스](../../atl/reference/ccommodule-class.md) 를 대체 합니다. 자세한 내용은 [ATL 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a> CAtlServiceModuleT:: CAtlServiceModuleT

생성자입니다.

```cpp
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>설명

데이터 멤버를 초기화 하 고 초기 서비스 상태를 설정 합니다.

## <a name="catlservicemodulethandler"></a><a name="handler"></a> CAtlServiceModuleT:: Handler

서비스에 대 한 처리기 루틴입니다.

```cpp
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>매개 변수

*dwOpcode*<br/>
처리기 작업을 정의 하는 스위치입니다. 자세한 내용은 설명 부분을 참조 하십시오.

### <a name="remarks"></a>설명

SCM (서비스 제어 관리자)이 서비스 상태를 검색 하기 위해 호출 하 고 중지 또는 일시 중지와 같은 명령을 실행 하는 코드입니다. SCM은 아래에 표시 된 작업 코드를에 전달 하 여 서비스가 수행 해야 하는 작업을 `Handler` 표시 합니다.

|작업 코드|의미|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|서비스를 중지합니다. [CAtlServiceModuleT:: OnStop](#onstop) 메서드를 재정의 하 여 동작을 변경 합니다.|
|SERVICE_CONTROL_PAUSE|사용자를 구현 했습니다. 서비스를 일시 중지 하려면 [CAtlServiceModuleT:: OnPause](#onpause) 에서 빈 메서드를 재정의 합니다.|
|SERVICE_CONTROL_CONTINUE|사용자를 구현 했습니다. 서비스를 계속 하려면 [CAtlServiceModuleT:: OnContinue](#oncontinue) 에서 빈 메서드를 재정의 합니다.|
|SERVICE_CONTROL_INTERROGATE|사용자를 구현 했습니다. 서비스를 조사 하려면 [CAtlServiceModuleT:: Oninterrogate](#oninterrogate) 의 빈 메서드를 재정의 합니다.|
|SERVICE_CONTROL_SHUTDOWN|사용자를 구현 했습니다. 서비스를 종료 하려면 [CAtlServiceModuleT:: OnShutdown](#onshutdown) 의 빈 메서드를 재정의 합니다.|

작업 코드를 인식할 수 없는 경우 [CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest) 메서드가 호출 됩니다.

기본 ATL 생성 서비스는 중지 명령만 처리 합니다. SCM이 중지 명령을 전달 하는 경우 서비스는 SCM에 프로그램이 중지 됨을 알립니다. 그런 다음 서비스는를 호출 `PostThreadMessage` 하 여 종료 메시지를 자체에 게시 합니다. 그러면 메시지 루프가 종료 되 고 서비스가 궁극적으로 닫힙니다.

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a> CAtlServiceModuleT:: InitializeSecurity

서비스에 대 한 기본 보안 설정을 제공 합니다.

```cpp
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

에서 파생 되는 모든 클래스는 `CAtlServiceModuleT` 파생 클래스에서이 메서드를 구현 해야 합니다.

에 대 한 호출에서 RPC_C_IMP_LEVEL_IDENTIFY의 가장 수준 및 null이 아닌 보안 설명자를 사용 하 여 PKT 수준 인증을 사용 `CoInitializeSecurity` 합니다.

마법사에서 생성 된 특성을 가진 서비스 프로젝트의 경우

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

특성을 사용 하는 서비스 프로젝트의 경우

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a> CAtlServiceModuleT:: Install

서비스를 설치 하 고 만듭니다.

```cpp
BOOL Install() throw();
```

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

서비스를 SCM (서비스 제어 관리자) 데이터베이스에 설치한 다음 서비스 개체를 만듭니다. 서비스를 만들 수 없으면 메시지 상자가 표시 되 고 메서드에서 FALSE를 반환 합니다.

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a> CAtlServiceModuleT:: IsInstalled

서비스가 설치 되었는지 확인 합니다.

```cpp
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>반환 값

서비스가 설치 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a> CAtlServiceModuleT:: LogEvent

이벤트 로그에 씁니다.

```cpp
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>매개 변수

*pszFormat*<br/>
이벤트 로그에 쓸 문자열입니다.

*...*<br/>
이벤트 로그에 기록할 선택적 추가 문자열입니다.

### <a name="remarks"></a>설명

이 메서드는 [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw)함수를 사용 하 여 세부 정보를 이벤트 로그에 기록 합니다. 서비스가 실행 되 고 있지 않으면 해당 문자열이 콘솔로 전송 됩니다.

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a> CAtlServiceModuleT:: m_bService

프로그램이 서비스로 실행 중임을 나타내는 플래그입니다.

```cpp
BOOL m_bService;
```

### <a name="remarks"></a>설명

응용 프로그램 EXE와 서비스 EXE를 구분 하는 데 사용 됩니다.

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a> CAtlServiceModuleT:: m_dwThreadID

서비스의 스레드 식별자를 저장 하는 멤버 변수입니다.

```cpp
DWORD m_dwThreadID;
```

### <a name="remarks"></a>설명

이 변수는 현재 스레드의 스레드 식별자를 저장 합니다.

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a> CAtlServiceModuleT:: m_hServiceStatus

현재 서비스에 대 한 상태 정보 구조에 핸들을 저장 하는 멤버 변수입니다.

```cpp
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>설명

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) 구조에는 서비스에 대 한 정보가 포함 되어 있습니다.

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a> CAtlServiceModuleT:: m_status

현재 서비스에 대 한 상태 정보 구조를 저장 하는 멤버 변수입니다.

```cpp
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>설명

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) 구조에는 서비스에 대 한 정보가 포함 되어 있습니다.

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a> CAtlServiceModuleT:: m_szServiceName

등록할 서비스의 이름입니다.

```cpp
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>설명

서비스 이름을 저장 하는 null로 끝나는 문자열입니다.

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a> CAtlServiceModuleT:: OnContinue

서비스를 계속 하려면이 메서드를 재정의 합니다.

```cpp
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a> CAtlServiceModuleT:: OnInterrogate

서비스를 검사 하려면이 메서드를 재정의 합니다.

```cpp
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a> CAtlServiceModuleT:: OnPause

서비스를 일시 중지 하려면이 메서드를 재정의 합니다.

```cpp
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a> CAtlServiceModuleT:: OnShutdown

서비스를 종료 하려면이 메서드를 재정의 합니다.

```cpp
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a> CAtlServiceModuleT:: OnStop

서비스를 중지 하려면이 메서드를 재정의 합니다.

```cpp
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a> CAtlServiceModuleT:: OnUnknownRequest

서비스에 대 한 알 수 없는 요청을 처리 하려면이 메서드를 재정의 합니다.

```cpp
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>매개 변수

*dwOpcode*<br/>
예약되어 있습니다.

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a> CAtlServiceModuleT::P arseCommandLine

명령줄을 구문 분석 하 고 필요한 경우 등록을 수행 합니다.

```cpp
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>매개 변수

*lpCmdLine*<br/>
명령줄입니다.

*pnRetCode*<br/>
등록에 해당 하는 HRESULT입니다 (발생 한 경우).

### <a name="return-value"></a>반환 값

성공 하면 true를 반환 하 고, 명령줄에 제공 된 RGS 파일을 등록할 수 없으면 false를 반환 합니다.

### <a name="remarks"></a>설명

명령줄을 구문 분석 하 고 필요한 경우 제공 된 RGS 파일의 등록 또는 등록을 취소 합니다. 이 메서드는 [CAtlExeModuleT::P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline) 를 호출 하 여 **/RegServer** 및 **/UnregServer** 를 확인 합니다. **-/Service** 인수를 추가 하면 서비스를 등록 합니다.

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a> CAtlServiceModuleT::P reMessageLoop

이 메서드는 메시지 루프를 입력 하기 바로 전에 호출 됩니다.

```cpp
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>매개 변수

*nShowCmd*<br/>
이 매개 변수는 [CAtlExeModuleT::P remessageloop](../../atl/reference/catlexemodulet-class.md#premessageloop)에 전달 됩니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

서비스에 대 한 사용자 지정 초기화 코드를 추가 하려면이 메서드를 재정의 합니다.

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a> CAtlServiceModuleT:: RegisterAppId

레지스트리에 서비스를 등록 합니다.

```cpp
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>매개 변수

*bService*<br/>
서비스로 등록 하려면 true 여야 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlservicemoduletrun"></a><a name="run"></a> CAtlServiceModuleT:: Run

서비스를 실행 합니다.

```cpp
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>매개 변수

*nShowCmd*<br/>
창이 표시 되는 방법을 지정 합니다. 이 매개 변수는 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) 섹션에서 설명 하는 값 중 하나일 수 있습니다. 기본값은 SW_HIDE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

호출 된 후 `Run` [CAtlServiceModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)및 [CAtlExeModuleT::P ostmessageloop](../../atl/reference/catlexemodulet-class.md#postmessageloop)를 호출 합니다.

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a> CAtlServiceModuleT:: ServiceMain

이 메서드는 서비스 제어 관리자에 의해 호출 됩니다.

```cpp
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>매개 변수

*dwArgc*<br/>
Argc 인수입니다.

*lpszArgv*<br/>
Argv 인수입니다.

### <a name="remarks"></a>설명

SCM (서비스 제어 관리자)은 `ServiceMain` 제어판에서 서비스 응용 프로그램을 열고 서비스를 선택 하 고 시작을 클릭 하면 호출 됩니다.

SCM `ServiceMain` 이 호출 되 면 서비스는 scm에 처리기 함수를 제공 해야 합니다. 이 함수를 통해 SCM은 서비스의 상태를 가져오고 특정 지침 (예: 일시 중지 또는 중지)을 전달할 수 있습니다. 그런 다음 [CAtlServiceModuleT:: Run](#run) 을 호출 하 여 서비스의 주요 작업을 수행 합니다. `Run` 서비스가 중지 될 때까지 계속 실행 됩니다.

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a> CAtlServiceModuleT:: SetServiceStatus

이 메서드는 서비스 상태를 업데이트 합니다.

```cpp
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>매개 변수

*dwState*<br/>
새 상태입니다. 가능한 값에 대해서는 [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) 을 참조 하세요.

### <a name="remarks"></a>설명

서비스에 대 한 서비스 제어 관리자의 상태 정보를 업데이트 합니다. [CAtlServiceModuleT:: Run](#run), [CAtlServiceModuleT:: ServiceMain](#servicemain) 및 기타 처리기 메서드에서 호출 됩니다. 또한 상태는 [CAtlServiceModuleT:: m_status](#m_status)멤버 변수에 저장 됩니다.

## <a name="catlservicemoduletstart"></a><a name="start"></a> CAtlServiceModuleT:: Start

`CAtlServiceModuleT::WinMain`서비스가 시작 될 때에 의해 호출 됩니다.

```cpp
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>매개 변수

*nShowCmd*<br/>
창이 표시 되는 방법을 지정 합니다. 이 매개 변수는 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) 섹션에서 설명 하는 값 중 하나일 수 있습니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[CAtlServiceModuleT:: WinMain](#winmain) 메서드는 레지스트리 항목을 제거 하 고 모듈을 제거 하는 작업과 관련 된 작업 뿐만 아니라 등록과 설치를 모두 처리 합니다. 서비스가 실행 되 면는를 `WinMain` 호출 `Start` 합니다.

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a> CAtlServiceModuleT:: Uninstall

서비스를 중지 하 고 제거 합니다.

```cpp
BOOL Uninstall() throw();
```

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

서비스 실행을 중지 하 고 서비스 제어 관리자 데이터베이스에서 서비스를 제거 합니다.

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a> CAtlServiceModuleT:: Unlock

서비스의 잠금 횟수를 감소 시킵니다.

```cpp
LONG Unlock() throw();
```

### <a name="return-value"></a>반환 값

진단 및 디버깅에 유용 하 게 사용할 수 있는 잠금 수를 반환 합니다.

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a> CAtlServiceModuleT:: UnregisterAppId

레지스트리에서 서비스를 제거 합니다.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a> CAtlServiceModuleT:: WinMain

이 메서드는 서비스를 시작 하는 데 필요한 코드를 구현 합니다.

```cpp
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>매개 변수

*nShowCmd*<br/>
창이 표시 되는 방법을 지정 합니다. 이 매개 변수는 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) 섹션에서 설명 하는 값 중 하나일 수 있습니다.

### <a name="return-value"></a>반환 값

서비스의 반환 값을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 명령줄 ( [CAtlServiceModuleT::P arsecommandline](#parsecommandline))을 처리 한 다음 [CAtlServiceModuleT:: Start](#start)를 사용 하 여 서비스를 시작 합니다.

## <a name="see-also"></a>참고 항목

[CAtlExeModuleT 클래스](../../atl/reference/catlexemodulet-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
