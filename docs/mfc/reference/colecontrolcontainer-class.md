---
description: '자세히 알아보기: COleControlContainer 클래스'
title: COleControlContainer 클래스
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 6a798b7556e22ec2d2ed2a118182e946753452b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227535"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer 클래스

ActiveX 컨트롤의 컨트롤 컨테이너 역할을 합니다.

## <a name="syntax"></a>구문

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|`COleControlContainer` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|컨테이너에 의해 호스팅되는 컨트롤 사이트를 만듭니다.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|앰비언트 속성이 변경 되었음을 호스트 된 모든 컨트롤에 알립니다.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|지정 된 단추 컨트롤을 수정 합니다.|
|[COleControlContainer:: CheckRadioButton](#checkradiobutton)|그룹의 지정 된 라디오 단추를 선택 합니다.|
|[COleControlContainer:: CreateControl](#createcontrol)|호스팅된 ActiveX 컨트롤을 만듭니다.|
|[COleControlContainer::CreateOleFont](#createolefont)|OLE 글꼴을 만듭니다.|
|[COleControlContainer:: FindItem](#finditem)|지정 된 컨트롤의 사용자 지정 사이트를 반환 합니다.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|컨트롤 사이트에서 이벤트를 수락 하 고 있는지 여부를 확인 합니다.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|지정 된 앰비언트 속성을 검색 합니다.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|지정 된 대화 상자 컨트롤을 검색 합니다.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|지정 된 대화 상자 컨트롤의 값을 검색 합니다.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|지정 된 대화 상자 컨트롤의 캡션을 검색 합니다.|
|[COleControlContainer:: HandleSetFocus](#handlesetfocus)|컨테이너가 WM_SETFOCUS 메시지를 처리 하는지 여부를 결정 합니다.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|창 없는 컨트롤에 전송 된 메시지를 처리 합니다.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|지정 된 단추의 상태를 확인 합니다.|
|[COleControlContainer:: OnPaint](#onpaint)|컨테이너의 일부를 다시 그리기 위해 호출 됩니다.|
|[COleControlContainer:: OnUIActivate](#onuiactivate)|컨트롤이 내부 활성화 될 때 호출 됩니다.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|컨트롤이 비활성화 될 때 호출 됩니다.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|자식 창에서 스크롤 메시지를 받을 때 프레임 워크에서 호출 됩니다.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|지정된 컨트롤에 메시지를 보냅니다.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|지정 된 컨트롤의 값을 설정 합니다.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|지정 된 컨트롤의 텍스트를 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleControlContainer:: m_crBack](#m_crback)|컨테이너의 배경색입니다.|
|[COleControlContainer:: m_crFore](#m_crfore)|컨테이너의 전경색입니다.|
|[COleControlContainer:: m_listSitesOrWnds](#m_listsitesorwnds)|지원 되는 컨트롤 사이트의 목록입니다.|
|[COleControlContainer:: m_nWindowlessControls](#m_nwindowlesscontrols)|호스트 된 창 없는 컨트롤의 수입니다.|
|[COleControlContainer:: m_pOleFont](#m_polefont)|사용자 지정 컨트롤 사이트의 OLE 글꼴에 대 한 포인터입니다.|
|[COleControlContainer:: m_pSiteCapture](#m_psitecapture)|캡처 제어 사이트에 대 한 포인터입니다.|
|[COleControlContainer:: m_pSiteFocus](#m_psitefocus)|현재 입력 포커스가 있는 컨트롤에 대 한 포인터입니다.|
|[COleControlContainer:: m_pSiteUIActive](#m_psiteuiactive)|현재 내부 활성화 된 컨트롤에 대 한 포인터입니다.|
|[COleControlContainer:: m_pWnd](#m_pwnd)|컨트롤 컨테이너를 구현 하는 창에 대 한 포인터입니다.|
|[COleControlContainer:: m_siteMap](#m_sitemap)|사이트 맵입니다.|

## <a name="remarks"></a>설명

이 작업은에서 구현 하는 하나 이상의 ActiveX 컨트롤 사이트에 대 한 지원을 제공 하 여 수행 됩니다 `COleControlSite` . `COleControlContainer`[IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) 및 [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) 인터페이스를 완전히 구현 하 여 포함 된 ActiveX 컨트롤이 해당 자격을 내부 항목으로 처리할 수 있도록 합니다.

일반적으로이 클래스는 `COccManager` `COleControlSite` 하나 이상의 activex 컨트롤에 대 한 사용자 지정 사이트를 사용 하 여 사용자 지정 activex 컨트롤 컨테이너를 구현 하기 위해 및와 함께 사용 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>요구 사항

**헤더:** afxocc

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a> COleControlContainer::AttachControlSite

컨트롤 사이트를 만들고 연결 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
`CWnd` 개체에 대한 포인터입니다.

*nIDC*<br/>
연결할 컨트롤의 ID입니다.

### <a name="remarks"></a>설명

이 프로세스를 사용자 지정 하려면이 함수를 재정의 합니다.

> [!NOTE]
> MFC 라이브러리에 정적으로 연결 하는 경우이 함수의 첫 번째 형태를 사용 합니다. MFC 라이브러리에 동적으로 연결 하는 경우 두 번째 형식을 사용 합니다.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a> COleControlContainer::BroadcastAmbientPropertyChange

앰비언트 속성이 변경 되었음을 호스트 된 모든 컨트롤에 알립니다.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
변경 되는 앰비언트 속성의 디스패치 ID입니다.

### <a name="remarks"></a>설명

이 함수는 앰비언트 속성 값이 변경 될 때 프레임 워크에서 호출 됩니다. 이 동작을 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a> COleControlContainer::CheckDlgButton

단추의 현재 상태를 수정 합니다.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>매개 변수

*nIDButton*<br/>
수정할 단추의 ID입니다.

*nCheck*<br/>
단추의 상태를 지정 합니다. 다음 중 하나일 수 있습니다.

- BST_CHECKED 단추 상태를 확인 됨으로 설정 합니다.

- BST_INDETERMINATE 단추 상태를 회색으로 설정 하 여 비활성화 된 상태를 나타냅니다. 단추에 BS_3STATE 또는 BS_AUTO3STATE 스타일이 있는 경우에만이 값을 사용 합니다.

- BST_UNCHECKED 단추 상태를 선택 취소 됨으로 설정 합니다.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a> COleControlContainer:: CheckRadioButton

그룹에서 지정 된 라디오 단추를 선택 하 고 그룹의 나머지 단추를 지웁니다.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>매개 변수

*nIDFirstButton*<br/>
그룹의 첫 번째 라디오 단추 식별자를 지정 합니다.

*nIDLastButton*<br/>
그룹의 마지막 라디오 단추 식별자를 지정 합니다.

*nIDCheckButton*<br/>
확인할 라디오 단추의 식별자를 지정 합니다.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a> COleControlContainer::COleControlContainer

`COleControlContainer` 개체를 생성합니다.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
컨트롤 컨테이너의 부모 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

개체가 성공적으로 생성 되 면를 호출 하 여 사용자 지정 컨트롤 사이트를 추가 `AttachControlSite` 합니다.

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a> COleControlContainer:: CreateControl

지정 된 개체에 의해 호스팅되는 ActiveX 컨트롤을 만듭니다 `COleControlSite` .

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>매개 변수

*pWndCtrl*<br/>
컨트롤을 나타내는 창 개체에 대 한 포인터입니다.

*가*<br/>
컨트롤의 고유 클래스 ID입니다.

*lpszWindowName*<br/>
컨트롤에 표시 되는 텍스트에 대 한 포인터입니다. 컨트롤의 캡션 또는 텍스트 속성 (있는 경우)의 값을 설정 합니다. NULL 인 경우 컨트롤의 캡션이나 텍스트 속성은 변경 되지 않습니다.

*dwStyle*<br/>
Windows 스타일. 사용 가능한 스타일은 **설명** 섹션에 나열 되어 있습니다.

*rect*<br/>
컨트롤의 크기와 위치를 지정 합니다. 개체 또는 구조 중 하나일 수 있습니다 `CRect` `RECT` .

*nID*<br/>
컨트롤의 자식 창 ID를 지정 합니다.

*pPersist*<br/>
컨트롤의 영구 상태를 포함 하는에 대 한 포인터 `CFile` 입니다. 기본값은 NULL로, 영구 저장소에서 해당 상태를 복원 하지 않고 컨트롤이 자체적으로 초기화 됨을 나타냅니다. NULL이 아닌 경우 `CFile` 스트림 또는 저장소 형식으로 컨트롤의 영구 데이터를 포함 하는 파생 개체에 대 한 포인터 여야 합니다. 이 데이터는 이전 클라이언트 활성화에서 저장 되었을 수 있습니다. 는 `CFile` 다른 데이터를 포함할 수 있지만에 대 한 호출 시 영구 데이터의 첫 번째 바이트에 대 한 읽기-쓰기 포인터를 설정 해야 합니다 `CreateControl` .

*bStorage*<br/>
*Ppersist* 의 데이터를 또는 데이터로 해석할지 여부를 나타냅니다 `IStorage` `IStream` . *Ppersist* 의 데이터가 저장소 인 경우 *BSTORAGE* 는 TRUE 여야 합니다. *Ppersist* 의 데이터가 스트림이 면 *BSTORAGE* 는 FALSE가 됩니다. 기본값은 FALSE입니다.

*bstrLicKey*<br/>
선택적 라이선스 키 데이터입니다. 이 데이터는 런타임 라이선스 키가 필요한 컨트롤을 만드는 데에만 필요 합니다. 컨트롤에서 라이선스를 지 원하는 경우 성공 하기 위해 컨트롤을 만들기 위한 라이선스 키를 제공 해야 합니다. 기본값은 NULL입니다.

*ppNewSite*<br/>
만들고 있는 컨트롤을 호스트 하는 기존 컨트롤 사이트에 대 한 포인터입니다. 기본값은 NULL로, 새 컨트롤 사이트가 자동으로 만들어지고 새 컨트롤에 연결 됨을 나타냅니다.

*.ppt*<br/>
`POINT`컨트롤의 왼쪽 위 모퉁이가 포함 된 구조체에 대 한 포인터입니다. 컨트롤의 크기는 *psize* 값에 따라 결정 됩니다. *Ppt* 및 *psize* 값은 컨트롤의 크기와 위치를 지정 하는 선택적 메서드입니다.

*psize*<br/>
`SIZE`컨트롤의 크기를 포함 하는 구조체에 대 한 포인터입니다. 왼쪽 위 모퉁이는 *ppt* 의 값에 따라 결정 됩니다. *Ppt* 및 *psize* 값은 컨트롤의 크기와 위치를 지정 하는 선택적 메서드입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Windows *Dwstyle* 플래그의 하위 집합만에서 지원 됩니다 `CreateControl` .

- WS_VISIBLE 처음에 표시 되는 창을 만듭니다. 일반 창과 같은 컨트롤을 즉시 표시 하려는 경우에 필요 합니다.

- WS_DISABLED 처음에는 사용 하지 않도록 설정 된 창을 만듭니다. 비활성화 된 창은 사용자의 입력을 받을 수 없습니다. 컨트롤에 활성화 된 속성이 있으면를 설정할 수 있습니다.

- WS_BORDER 얇은 선 테두리가 있는 창을 만듭니다. 컨트롤에 BorderStyle 속성이 있으면를 설정할 수 있습니다.

- WS_GROUP는 컨트롤 그룹의 첫 번째 컨트롤을 지정 합니다. 사용자는 방향 키를 사용 하 여 그룹의 한 컨트롤에서 다음으로 키보드 포커스를 변경할 수 있습니다. 첫 번째 컨트롤이 같은 그룹에 속하는 WS_GROUP 스타일로 정의 된 모든 컨트롤입니다. WS_GROUP 스타일을 가진 다음 컨트롤은 그룹을 종료 하 고 다음 그룹을 시작 합니다.

- WS_TABSTOP 사용자가 TAB 키를 누를 때 키보드 포커스를 받을 수 있는 컨트롤을 지정 합니다. TAB 키를 누르면 키보드 포커스가 WS_TABSTOP 스타일의 다음 컨트롤로 변경 됩니다.

두 번째 오버 로드를 사용 하 여 기본 크기의 컨트롤을 만듭니다.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a> COleControlContainer::CreateOleFont

OLE 글꼴을 만듭니다.

```cpp
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>매개 변수

*pFont*<br/>
컨트롤 컨테이너에서 사용 되는 글꼴에 대 한 포인터입니다.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a> COleControlContainer:: FindItem

지정 된 항목을 호스팅하는 사용자 지정 사이트를 찾습니다.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
찾을 항목의 식별자입니다.

### <a name="return-value"></a>반환 값

지정 된 항목의 사용자 지정 사이트에 대 한 포인터입니다.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a> COleControlContainer::FreezeAllEvents

컨테이너에서 연결 된 컨트롤 사이트의 이벤트를 무시 하거나 해당 이벤트를 수락할지 여부를 결정 합니다.

```cpp
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>매개 변수

*bFreeze*<br/>
이벤트가 처리 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤은 컨트롤 컨테이너에서 요청 하는 경우 이벤트 발생을 중지 하는 데 필요 하지 않습니다. 계속 해 서 실행 될 수 있지만 모든 후속 이벤트는 제어 컨테이너에서 무시 됩니다.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a> COleControlContainer::GetAmbientProp

지정 된 앰비언트 속성의 값을 검색 합니다.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>매개 변수

*pSite*<br/>
앰비언트 속성이 검색 되는 컨트롤 사이트에 대 한 포인터입니다.

*dispid*<br/>
원하는 앰비언트 속성의 디스패치 ID입니다.

*pVarResult*<br/>
앰비언트 속성의 값에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a> COleControlContainer::GetDlgItem

대화 상자 또는 다른 창에서 지정 된 컨트롤 또는 자식 창에 대 한 포인터를 검색 합니다.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
검색할 대화 상자 항목의 식별자입니다.

*phWnd*<br/>
지정 된 대화 상자 항목의 창 개체 핸들에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대화 상자 항목의 창에 대 한 포인터입니다.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a> COleControlContainer::GetDlgItemInt

지정 된 컨트롤의 번역 된 텍스트 값을 검색 합니다.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
컨트롤의 식별자입니다.

*lpTrans*<br/>
함수 성공/실패 값을 받는 부울 변수에 대 한 포인터입니다 (TRUE는 성공, FALSE는 실패를 나타냄).

*bSigned 됨*<br/>
함수가 처음부터 빼기 기호에 대 한 텍스트를 검사 하 고 부호 있는 정수 값 (있는 경우)을 반환 하는지 여부를 지정 합니다. *Bsigned* 매개 변수가 TRUE 인 경우 검색할 값이 부호 있는 정수 값이 되도록 지정 하 여 반환 값을 형식으로 캐스팅 합니다 **`int`** . 확장 오류 정보를 가져오려면 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출합니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 *Lptrans* 에서 가리키는 변수는 TRUE로 설정 되 고 반환 값은 컨트롤 텍스트의 변환 된 값입니다.

함수가 실패 하면 *Lptrans* 이 가리키는 변수가 FALSE로 설정 되 고 반환 값은 0이 됩니다. 0이 가능한 번역 된 값 이므로 반환 값 0은 자체적으로 실패를 나타내지 않습니다.

*Lptrans* NULL 인 경우 함수는 성공 또는 실패에 대 한 정보를 반환 하지 않습니다.

### <a name="remarks"></a>설명

함수는 텍스트의 시작 부분에서 추가 공백을 제거한 다음 10 진수를 변환 하 여 검색 된 텍스트를 변환 합니다. 함수는 텍스트의 끝에 도달 하거나 숫자가 아닌 문자를 발견 하면 변환을 중지 합니다.

이 함수는 번역 된 값이 INT_MAX (부호 있는 숫자의 경우) 또는 UINT_MAX (부호 없는 숫자의 경우) 보다 큰 경우 0을 반환 합니다.

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a> COleControlContainer::GetDlgItemText

지정 된 컨트롤의 텍스트를 검색 합니다.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
컨트롤의 식별자입니다.

*lpStr*<br/>
컨트롤의 텍스트에 대 한 포인터입니다.

*nMaxCount*<br/>
*LpStr* 가 가리키는 버퍼에 복사할 문자열의 최대 길이 (문자 수)를 지정 합니다. 문자열의 길이가 한도를 초과 하면 문자열이 잘립니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 null 종결 문자를 포함 하지 않고 버퍼에 복사 되는 문자 수를 지정 합니다.

함수가 실패하면 반환 값은 0입니다. 확장 오류 정보를 가져오려면 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출합니다.

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a> COleControlContainer:: HandleSetFocus

컨테이너가 WM_SETFOCUS 메시지를 처리 하는지 여부를 결정 합니다.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>반환 값

컨테이너가 WM_SETFOCUS 메시지를 처리 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a> COleControlContainer::HandleWindowlessMessage

창 없는 컨트롤에 대 한 창 메시지를 처리 합니다.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>매개 변수

*message*<br/>
Windows에서 제공 하는 창 메시지의 식별자입니다.

*wParam*<br/>
메시지의 매개 변수입니다. Windows에서 제공 됩니다. 추가 메시지 관련 정보를 지정 합니다. 이 매개 변수의 내용은 *메시지* 매개 변수의 값에 따라 달라 집니다.

*lParam*<br/>
메시지의 매개 변수입니다. Windows에서 제공 됩니다. 추가 메시지 관련 정보를 지정 합니다. 이 매개 변수의 내용은 *메시지* 매개 변수의 값에 따라 달라 집니다.

*plResult*<br/>
Windows 결과 코드입니다. 메시지 처리 결과를 지정 하며 보낸 메시지에 따라 다릅니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

창 없는 컨트롤 메시지의 처리를 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a> COleControlContainer::IsDlgButtonChecked

지정 된 단추의 상태를 확인 합니다.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>매개 변수

*nIDButton*<br/>
단추 컨트롤의 식별자입니다.

### <a name="return-value"></a>반환 값

BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON 또는 BS_3STATE 스타일을 사용 하 여 만든 단추에서 반환 된 값입니다. 다음 중 하나일 수 있습니다.

- BST_CHECKED 단추를 선택 합니다.

- BST_INDETERMINATE 단추가 회색으로 표시 되어 비활성화 상태를 나타냅니다. 단추에 BS_3STATE 또는 BS_AUTO3STATE 스타일이 있는 경우에만 적용 됩니다.

- BST_UNCHECKED 단추가 선택 취소 되어 있습니다.

### <a name="remarks"></a>설명

단추가 3 가지 상태 컨트롤인 경우 멤버 함수는이를 흐리게, 확인 또는 둘 다 수행할지 여부를 결정 합니다.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a> COleControlContainer:: m_crBack

컨테이너의 배경색입니다.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a> COleControlContainer:: m_crFore

컨테이너의 전경색입니다.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a> COleControlContainer:: m_listSitesOrWnds

컨테이너에서 호스팅하는 컨트롤 사이트의 목록입니다.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a> COleControlContainer:: m_nWindowlessControls

컨트롤 컨테이너에서 호스팅하는 창 없는 컨트롤의 수입니다.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a> COleControlContainer:: m_pOleFont

사용자 지정 컨트롤 사이트의 OLE 글꼴에 대 한 포인터입니다.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a> COleControlContainer:: m_pSiteCapture

캡처 제어 사이트에 대 한 포인터입니다.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a> COleControlContainer:: m_pSiteFocus

현재 입력 포커스가 있는 컨트롤 사이트에 대 한 포인터입니다.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a> COleControlContainer:: m_pSiteUIActive

내부 활성화 된 컨트롤 사이트에 대 한 포인터입니다.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a> COleControlContainer:: m_pWnd

컨테이너와 연결 된 창 개체에 대 한 포인터입니다.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a> COleControlContainer:: m_siteMap

사이트 맵입니다.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a> COleControlContainer:: OnPaint

WM_PAINT 요청을 처리 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
컨테이너에서 사용 하는 장치 컨텍스트에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메시지가 처리 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

그리기 프로세스를 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a> COleControlContainer:: OnUIActivate

*Psite* 가 가리키는 제어 사이트가 내부에서 활성화 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>매개 변수

*pSite*<br/>
내부 활성화 될 컨트롤 사이트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

내부 활성화는 컨테이너의 주 메뉴가 내부 복합 메뉴로 바뀌는 것을 의미 합니다.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a> COleControlContainer::OnUIDeactivate

*Psite* 가 가리키는 제어 사이트가 비활성화 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>매개 변수

*pSite*<br/>
비활성화할 컨트롤 사이트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 알림이 수신 되 면 컨테이너는 해당 사용자 인터페이스를 다시 설치 하 고 포커스를 이동 해야 합니다.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a> COleControlContainer::ScrollChildren

자식 창에서 스크롤 메시지를 받을 때 프레임 워크에서 호출 됩니다.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>매개 변수

*dx*<br/>
X 축을 따라 스크롤되는 크기 (픽셀)입니다.

*dy*<br/>
Y 축을 따라 스크롤되는 크기 (픽셀)입니다.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a> COleControlContainer::SendDlgItemMessage

지정된 컨트롤에 메시지를 보냅니다.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
메시지를 받는 컨트롤의 식별자를 지정 합니다.

*message*<br/>
보낼 메시지를 지정 합니다.

*wParam*<br/>
추가 메시지 관련 정보를 지정 합니다.

*lParam*<br/>
추가 메시지 관련 정보를 지정 합니다.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a> COleControlContainer::SetDlgItemInt

대화 상자의 컨트롤 텍스트를 지정 된 정수 값의 문자열 표현으로 설정 합니다.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
컨트롤의 식별자입니다.

*N 값*<br/>
표시할 정수 값입니다.

*bSigned 됨*<br/>
*Nvalue* 매개 변수가 signed 또는 unsigned 인지 여부를 지정 합니다. 이 매개 변수가 TRUE 이면 *Nvalue* 가 서명 됩니다. 이 매개 변수가 TRUE이 고 *Nvalue* 가 0 보다 작은 경우 문자열의 첫 번째 숫자 앞에 빼기 기호가 배치 됩니다. 이 매개 변수가 FALSE 이면 *Nvalue* 는 부호 없는 값입니다.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a> COleControlContainer::SetDlgItemText

*LpszString* 에 포함 된 텍스트를 사용 하 여 지정 된 컨트롤의 텍스트를 설정 합니다.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
컨트롤의 식별자입니다.

*lpszString*<br/>
컨트롤의 텍스트에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 클래스](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager 클래스](../../mfc/reference/coccmanager-class.md)
