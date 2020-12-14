---
description: '자세히 알아보기: COleMessageFilter 클래스'
title: COleMessageFilter 클래스
ms.date: 11/04/2016
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
ms.openlocfilehash: f0ab1d473704f5355933c04072a195c12fb71c73
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226898"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter 클래스

OLE 애플리케이션의 상호 작용으로 요구되는 동시성을 관리합니다.

## <a name="syntax"></a>구문

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|`COleMessageFilter` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|응용 프로그램을 사용 중 상태로 전환 합니다.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|호출 된 응용 프로그램이 사용 중일 때 표시 되는 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|호출 된 응용 프로그램이 응답 하지 않을 때 표시 되는 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[COleMessageFilter::EndBusyState](#endbusystate)|응용 프로그램의 사용 중 상태를 종료 합니다.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|OLE 호출이 진행 되는 동안 메시지를 처리 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleMessageFilter:: Register](#register)|OLE 시스템 Dll을 사용 하 여 메시지 필터를 등록 합니다.|
|[COleMessageFilter:: Revoke](#revoke)|OLE 시스템 Dll을 사용 하 여 메시지 필터의 등록을 취소 합니다.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|OLE 호출에 대 한 사용 중인 응용 프로그램의 회신을 결정 합니다.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|응용 프로그램이 OLE 호출에 대 한 응답을 기다리는 기간을 결정 합니다.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|사용 중인 응용 프로그램에 대 한 호출 응용 프로그램의 응답을 결정 합니다.|

## <a name="remarks"></a>설명

`COleMessageFilter`클래스는 OLE 자동화 응용 프로그램 뿐만 아니라 서버 및 컨테이너 응용 프로그램을 시각적으로 편집 하는 데 유용 합니다. 호출 되는 서버 응용 프로그램의 경우이 클래스를 사용 하 여 다른 컨테이너 응용 프로그램에서 들어오는 호출이 취소 되거나 나중에 다시 시도 되도록 응용 프로그램을 "사용 중"으로 만들 수 있습니다. 이 클래스는 호출 된 응용 프로그램이 사용 중일 때 호출 응용 프로그램에서 수행할 작업을 결정 하는 데에도 사용할 수 있습니다.

일반적으로는 문서 또는 다른 OLE 액세스 가능 개체가 소멸 될 때 서버 응용 프로그램에서 [BeginBusyState](#beginbusystate) 및 [EndBusyState](#endbusystate) 를 호출 하는 데 사용 됩니다. 이러한 호출은 사용자 인터페이스 업데이트 중에 [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle) 에서 수행 됩니다.

기본적으로 `COleMessageFilter` 응용 프로그램이 초기화 될 때 개체가 할당 됩니다. [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)를 사용 하 여 검색할 수 있습니다.

이 클래스는 고급 클래스입니다. 이러한 작업은 직접 사용할 필요가 거의 없습니다.

자세한 내용은 서버 [: 서버 구현](../../mfc/servers-implementing-a-server.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a> COleMessageFilter::BeginBusyState

사용 중 상태를 시작 하려면이 함수를 호출 합니다.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>설명

[EndBusyState](#endbusystate) 와 함께 작동 하 여 응용 프로그램의 사용 중 상태를 제어 합니다. [SetBusyReply](#setbusyreply) 함수는 응용 프로그램이 사용 중일 때 호출 하는 응용 프로그램에 대 한 응답을 결정 합니다.

`BeginBusyState`및는 `EndBusyState` 각각 응용 프로그램이 사용 중인지 여부를 확인 하는 카운터를 호출 합니다. 예를 들어,에 대 `BeginBusyState` 한 두 번 `EndBusyState` 의 호출은 여전히 사용 중 상태를 초래 합니다. 사용 중인 상태를 취소 하려면 동일한 횟수의 호출을 호출 해야 `EndBusyState` `BeginBusyState` 합니다.

기본적으로 프레임 워크는 [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle)에서 수행 하는 유휴 처리 중 사용 중 상태로 전환 됩니다. 응용 프로그램에서 ON_COMMANDUPDATEUI 알림을 처리 하는 동안에는 유휴 처리가 완료 된 후에 들어오는 호출이 나중에 처리 됩니다.

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a> COleMessageFilter::COleMessageFilter

`COleMessageFilter` 개체를 만듭니다.

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a> COleMessageFilter::EnableBusyDialog

OLE 호출 중에 메시지 보류 중 지연 ( [SetRetryReply](#setretryreply)참조)이 만료 될 때 표시 되는 사용 중 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>매개 변수

*베 작업 중*<br/>
"사용 중" 대화 상자를 사용 하거나 사용 하지 않도록 설정할지 여부를 지정 합니다.

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a> COleMessageFilter::EnableNotRespondingDialog

"응답 없음" 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다 .이 대화 상자는 OLE 호출 중에 키보드 또는 마우스 메시지가 보류 중이 고 호출 시간이 초과 된 경우 표시 됩니다.

```cpp
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnableNotResponding*<br/>
"응답 하지 않음" 대화 상자를 사용 하거나 사용 하지 않도록 설정할지 여부를 지정 합니다.

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a> COleMessageFilter::EndBusyState

이 함수를 호출 하 여 사용 중인 상태를 종료 합니다.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>설명

[BeginBusyState](#beginbusystate) 와 함께 작동 하 여 응용 프로그램의 사용 중 상태를 제어 합니다. [SetBusyReply](#setbusyreply) 함수는 응용 프로그램이 사용 중일 때 호출 하는 응용 프로그램에 대 한 응답을 결정 합니다.

`BeginBusyState`및는 `EndBusyState` 각각 응용 프로그램이 사용 중인지 여부를 확인 하는 카운터를 호출 합니다. 예를 들어,에 대 `BeginBusyState` 한 두 번 `EndBusyState` 의 호출은 여전히 사용 중 상태를 초래 합니다. 사용 중인 상태를 취소 하려면 동일한 횟수의 호출을 호출 해야 `EndBusyState` `BeginBusyState` 합니다.

기본적으로 프레임 워크는 [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle)에서 수행 하는 유휴 처리 중 사용 중 상태로 전환 됩니다. 응용 프로그램에서 ON_UPDATE_COMMAND_UI 알림을 처리 하는 동안 들어오는 호출은 유휴 처리가 완료 된 후 처리 됩니다.

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a> COleMessageFilter::OnMessagePending

OLE 호출이 진행 되는 동안 메시지를 처리 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

*pMsg*<br/>
보류 중인 메시지에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아닌 값이고, 실패하면 0입니다.

### <a name="remarks"></a>설명

호출 응용 프로그램에서 호출이 완료 될 때까지 대기 하는 경우 프레임 워크는 `OnMessagePending` 보류 중인 메시지에 대 한 포인터를 사용 하 여를 호출 합니다. 기본적으로 프레임 워크는 WM_PAINT 메시지를 디스패치 하므로 시간이 오래 걸리는 호출 중에 창 업데이트가 발생할 수 있습니다.

활성화 되기 전에 [등록](#register) 에 대 한 호출을 통해 메시지 필터를 등록 해야 합니다.

## <a name="colemessagefilterregister"></a><a name="register"></a> COleMessageFilter:: Register

OLE 시스템 Dll을 사용 하 여 메시지 필터를 등록 합니다.

```
BOOL Register();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아닌 값이고, 실패하면 0입니다.

### <a name="remarks"></a>설명

메시지 필터는 시스템 Dll에 등록 되지 않은 경우에는 적용 되지 않습니다. 일반적으로 응용 프로그램의 초기화 코드는 응용 프로그램의 메시지 필터를 등록 합니다. 응용 프로그램에 의해 등록 된 다른 모든 메시지 필터는 프로그램이 [취소](#revoke)를 호출 하 여 종료 되기 전에 취소 되어야 합니다.

프레임 워크의 기본 메시지 필터는 초기화 하는 동안 자동으로 등록 되 고 종료 시 해지 됩니다.

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a> COleMessageFilter:: Revoke

[등록](#register)에 대 한 호출에 의해 수행 된 이전 등록을 취소 합니다.

```cpp
void Revoke();
```

### <a name="remarks"></a>설명

프로그램이 종료 되기 전에 메시지 필터를 취소 해야 합니다.

프레임 워크에서 자동으로 만들어지고 등록 된 기본 메시지 필터도 자동으로 취소 됩니다.

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a> COleMessageFilter::SetBusyReply

이 함수는 응용 프로그램의 "사용 중인 회신"을 설정 합니다.

```cpp
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>매개 변수

*nBusyReply*<br/>
`SERVERCALL`COMPOBJ에 정의 된 열거형의 값입니다. 다음 값 중 하나를 사용할 수 있습니다.

- 응용 프로그램에서 호출을 받아들일 수 SERVERCALL_ISHANDLED 있지만 특정 호출을 처리 하는 동안 실패할 수 있습니다.

- 응용 프로그램 SERVERCALL_REJECTED에서 호출을 처리할 수 없습니다.

- 응용 프로그램이 일시적으로 호출을 처리할 수 없는 상태에 있는 SERVERCALL_RETRYLATER.

### <a name="remarks"></a>설명

[BeginBusyState](#beginbusystate) 및 [EndBusyState](#endbusystate) 함수는 응용 프로그램의 사용 중 상태를 제어 합니다.

에 대 한 호출로 응용 프로그램을 사용 하는 경우 `BeginBusyState` 마지막 설정에 의해 결정 된 값을 사용 하 여 OLE 시스템 dll의 호출에 응답 `SetBusyReply` 합니다. 호출 응용 프로그램은이 사용 중인 회신을 사용 하 여 수행할 작업을 결정 합니다.

기본적으로 사용 중인 회신은 SERVERCALL_RETRYLATER입니다. 이렇게 하면 호출 하는 응용 프로그램이 가능한 한 빨리 호출을 다시 시도 합니다.

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a> COleMessageFilter::SetMessagePendingDelay

호출 응용 프로그램에서 추가 작업을 수행 하기 전에 호출 된 응용 프로그램의 응답을 기다리는 기간을 결정 합니다.

```cpp
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>매개 변수

*nTimeout*<br/>
메시지의 보류 중인 지연 시간 (밀리초)입니다.

### <a name="remarks"></a>설명

이 함수는 [SetRetryReply](#setretryreply)와 함께 작동 합니다.

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a> COleMessageFilter::SetRetryReply

호출 된 응용 프로그램에서 사용 중인 응답을 받을 때 호출 응용 프로그램의 작업을 결정 합니다.

```cpp
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>매개 변수

*nRetryReply*<br/>
재시도 간격 (밀리초)입니다.

### <a name="remarks"></a>설명

호출 된 응용 프로그램이 사용 중임을 나타내는 경우 호출 응용 프로그램은 서버가 더 이상 사용 되지 않거나, 즉시 다시 시도 하거나, 지정 된 간격 후에 다시 시도 될 때까지 대기 하도록 결정할 수 있습니다. 호출을 모두 취소 하도록 결정할 수도 있습니다.

호출자의 응답은 함수 및 SetMessagePendingDelay에 의해 제어 됩니다 `SetRetryReply` . [](#setmessagependingdelay) `SetRetryReply` 호출 응용 프로그램에서 지정 된 호출을 다시 시도 하는 동안 대기 해야 하는 기간을 결정 합니다. `SetMessagePendingDelay` 추가 작업을 수행 하기 전에 호출 응용 프로그램이 서버의 응답을 기다리는 기간을 결정 합니다.

일반적으로 기본값은 허용 되며 변경할 필요가 없습니다. 프레임 워크는 호출이 통과할 때까지 또는 메시지 보류 중 지연 시간이 만료 될 때까지 *nRetryReply* 밀리초 마다 호출을 다시 시도 합니다. *NRetryReply* 에 대 한 값 0은 즉시 다시 시도를 지정 하 고-1은 호출 취소를 지정 합니다.

메시지 보류 중 지연이 만료 된 경우 사용자가 호출을 취소 하거나 다시 시도할 수 있도록 OLE "사용 중 대화 상자" ( [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)참조)가 표시 됩니다. [EnableBusyDialog](#enablebusydialog) 을 호출 하 여이 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다.

호출 하는 동안 키보드 또는 마우스 메시지가 보류 중이 고 호출 시간이 초과 되 면 (메시지 보류 지연 시간 초과) "응답 하지 않음" 대화 상자가 표시 됩니다. [EnableNotRespondingDialog](#enablenotrespondingdialog) 을 호출 하 여이 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다. 일반적으로이 상태는 문제가 발생 하 여 사용자가 성급를 받고 있음을 나타냅니다.

대화 상자를 사용할 수 없는 경우 현재 "다시 시도 회신"은 사용 중인 응용 프로그램에 대 한 호출에 항상 사용 됩니다.

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)
