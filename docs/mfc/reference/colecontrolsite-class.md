---
description: '자세히 알아보기: COleControlSite 클래스'
title: COleControlSite 클래스
ms.date: 11/04/2016
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
ms.openlocfilehash: 3fecd9f81baec29a205dbdf4a10ee7d4927c3823
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227458"
---
# <a name="colecontrolsite-class"></a>COleControlSite 클래스

사용자 지정 클라이언트 측 컨트롤 인터페이스를 지원합니다.

## <a name="syntax"></a>구문

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|`COleControlSite` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleControlSite:: BindDefaultProperty](#binddefaultproperty)|호스팅된 컨트롤의 기본 속성을 데이터 소스에 바인딩합니다.|
|[COleControlSite:: BindProperty](#bindproperty)|호스팅된 컨트롤의 속성을 데이터 소스에 바인딩합니다.|
|[COleControlSite:: CreateControl](#createcontrol)|호스팅된 ActiveX 컨트롤을 만듭니다.|
|[COleControlSite::D estroyControl](#destroycontrol)|호스팅된 컨트롤을 소멸 시킵니다.|
|[COleControlSite::D 초과 b](#doverb)|호스팅된 컨트롤의 특정 동사를 실행 합니다.|
|[COleControlSite:: EnableDSC](#enabledsc)|컨트롤 사이트에 대 한 데이터 소싱을 사용 하도록 설정 합니다.|
|[COleControlSite:: EnableWindow](#enablewindow)|컨트롤 사이트를 사용 하도록 설정 합니다.|
|[COleControlSite:: FreezeEvents](#freezeevents)|컨트롤 사이트에서 이벤트를 수락 하는지 여부를 지정 합니다.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|호스팅된 컨트롤의 기본 단추 코드를 검색 합니다.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|컨트롤의 식별자를 검색 합니다.|
|[COleControlSite::GetEventIID](#geteventiid)|호스팅된 컨트롤의 이벤트 인터페이스 ID를 검색 합니다.|
|[COleControlSite:: GetExStyle](#getexstyle)|컨트롤 사이트의 확장 스타일을 검색 합니다.|
|[COleControlSite:: GetProperty](#getproperty)|호스팅된 컨트롤의 특정 속성을 검색 합니다.|
|[COleControlSite:: GetStyle](#getstyle)|컨트롤 사이트의 스타일을 검색 합니다.|
|[COleControlSite:: GetWindowText](#getwindowtext)|호스팅된 컨트롤의 텍스트를 검색 합니다.|
|[COleControlSite:: InvokeHelper](#invokehelper)|호스팅된 컨트롤의 특정 메서드를 호출 합니다.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|인수의 변수 목록을 사용 하 여 호스트 된 컨트롤의 특정 메서드를 호출 합니다.|
|[COleControlSite:: IsDefaultButton](#isdefaultbutton)|컨트롤이 창의 기본 단추 인지 여부를 확인 합니다.|
|[COleControlSite:: IsWindowEnabled](#iswindowenabled)|컨트롤 사이트의 표시 상태를 확인 합니다.|
|[COleControlSite::ModifyStyle](#modifystyle)|컨트롤 사이트의 현재 확장 스타일을 수정 합니다.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|컨트롤 사이트의 현재 스타일을 수정 합니다.|
|[COleControlSite:: MoveWindow](#movewindow)|컨트롤 사이트의 위치를 변경 합니다.|
|[COleControlSite:: QuickActivate](#quickactivate)|호스팅된 컨트롤을 신속 하 게 활성화 합니다.|
|[COleControlSite:: SafeSetProperty](#safesetproperty)|예외를 throw 할 가능성 없이 컨트롤의 속성 또는 메서드를 설정 합니다.|
|[COleControlSite:: SetDefaultButton](#setdefaultbutton)|창의 기본 단추를 설정 합니다.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|컨트롤의 식별자를 검색 합니다.|
|[COleControlSite:: SetFocus](#setfocus)|컨트롤 사이트에 포커스를 설정 합니다.|
|[COleControlSite:: SetProperty](#setproperty)|호스팅된 컨트롤의 특정 속성을 설정 합니다.|
|[COleControlSite:: SetPropertyV](#setpropertyv)|인수의 변수 목록을 사용 하 여 호스트 된 컨트롤의 특정 속성을 설정 합니다.|
|[COleControlSite:: SetWindowPos](#setwindowpos)|컨트롤 사이트의 위치를 설정 합니다.|
|[COleControlSite:: SetWindowText](#setwindowtext)|호스팅된 컨트롤의 텍스트를 설정 합니다.|
|[COleControlSite:: ShowWindow](#showwindow)|컨트롤 사이트를 표시 하거나 숨깁니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|호스팅된 컨트롤에 대 한 키보드 정보 및 니모닉을 검색 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleControlSite:: m_bIsWindowless](#m_biswindowless)|호스팅된 컨트롤이 창 없는 컨트롤 인지 여부를 확인 합니다.|
|[COleControlSite:: m_ctlInfo](#m_ctlinfo)|컨트롤의 키보드 처리에 대 한 정보를 포함 합니다.|
|[COleControlSite:: m_dwEventSink](#m_dweventsink)|컨트롤의 연결 지점에 대 한 쿠키입니다.|
|[COleControlSite:: m_dwMiscStatus](#m_dwmiscstatus)|호스팅된 컨트롤의 기타 상태입니다.|
|[COleControlSite:: m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink`컨트롤의 쿠키입니다.|
|[COleControlSite:: m_dwStyle](#m_dwstyle)|호스팅된 컨트롤의 스타일입니다.|
|[COleControlSite:: m_hWnd](#m_hwnd)|컨트롤 사이트의 핸들입니다.|
|[COleControlSite:: m_iidEvents](#m_iidevents)|호스팅된 컨트롤의 이벤트 인터페이스 ID입니다.|
|[COleControlSite:: m_nID](#m_nid)|호스트 된 컨트롤의 ID입니다.|
|[COleControlSite:: m_pActiveObject](#m_pactiveobject)|`IOleInPlaceActiveObject`호스팅된 컨트롤의 개체에 대 한 포인터입니다.|
|[COleControlSite:: m_pCtrlCont](#m_pctrlcont)|호스팅된 컨트롤의 컨테이너입니다.|
|[COleControlSite:: m_pInPlaceObject](#m_pinplaceobject)|`IOleInPlaceObject`호스팅된 컨트롤의 개체에 대 한 포인터입니다.|
|[COleControlSite:: m_pObject](#m_pobject)|컨트롤의 인터페이스에 대 한 포인터 `IOleObjectInterface` 입니다.|
|[COleControlSite:: m_pWindowlessObject](#m_pwindowlessobject)|컨트롤의 인터페이스에 대 한 포인터 `IOleInPlaceObjectWindowless` 입니다.|
|[COleControlSite:: m_pWndCtrl](#m_pwndctrl)|호스팅된 컨트롤의 창 개체에 대 한 포인터입니다.|
|[COleControlSite:: m_rect](#m_rect)|컨트롤 사이트의 차원입니다.|

## <a name="remarks"></a>설명

이 지원은 포함 된 ActiveX 컨트롤이 표시 사이트의 위치 및 범위, 해당 모니커, 사용자 인터페이스, 앰비언트 속성 및 해당 컨테이너에서 제공 하는 기타 리소스에 대 한 정보를 얻는 기본 방법입니다. `COleControlSite`[IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite), [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), `IBoundObjectSite` , `INotifyDBEvents` , [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) 인터페이스를 완전히 구현 합니다. 또한 IDispatch 인터페이스 (앰비언트 속성 및 이벤트 싱크에 대 한 지원 제공)도 구현 됩니다.

를 사용 하 여 ActiveX 컨트롤 사이트를 만들려면 `COleControlSite` 에서 클래스를 파생 시킵니다 `COleControlSite` . 컨테이너의 `CWnd` 파생 클래스 (예를 들어, 대화 상자)에서 함수를 재정의 `CWnd::CreateControlSite` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>요구 사항

**헤더:** afxocc

## <a name="colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a> COleControlSite:: BindDefaultProperty

형식 라이브러리에 표시 된 대로 호출 하는 개체의 기본 단순 바인딩된 속성을 데이터 소스 컨트롤의 DataSource, UserName, Password 및 SQL 속성으로 정의 된 기본 커서에 바인딩합니다.

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
데이터 소스 컨트롤에 바인딩할 데이터 바인딩된 컨트롤에 대 한 속성의 DISPID를 지정 합니다.

*vtProp*<br/>
바인딩할 속성의 유형 (예: VT_BSTR, VT_VARIANT 등)을 지정 합니다.

*szFieldName*<br/>
속성이 바인딩되는 데이터 소스 컨트롤에서 제공 하는 커서의 열 이름을 지정 합니다.

*pDSCWnd*<br/>
`CWnd`속성이 바인딩되는 데이터 소스 컨트롤을 호스팅하는 파생 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CWnd`이 함수를 호출 하는 개체는 데이터 바인딩된 컨트롤 이어야 합니다.

## <a name="colecontrolsitebindproperty"></a><a name="bindproperty"></a> COleControlSite:: BindProperty

형식 라이브러리에 표시 된 대로 호출 하는 개체의 단순 바인딩된 속성을 데이터 소스 컨트롤의 DataSource, UserName, Password 및 SQL 속성으로 정의 된 기본 커서에 바인딩합니다.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>매개 변수

*dwDispId*<br/>
데이터 소스 컨트롤에 바인딩할 데이터 바인딩된 컨트롤에 대 한 속성의 DISPID를 지정 합니다.

*pWndDSC*<br/>
`CWnd`속성이 바인딩되는 데이터 소스 컨트롤을 호스팅하는 파생 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CWnd`이 함수를 호출 하는 개체는 데이터 바인딩된 컨트롤 이어야 합니다.

## <a name="colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a> COleControlSite::COleControlSite

새 `COleControlSite` 개체를 생성합니다.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>매개 변수

*pCtrlCont*<br/>
AtiveX 컨트롤을 호스팅하는 창을 나타내는 컨트롤의 컨테이너에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 [Coccmanager:: CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) 함수에 의해 호출 됩니다. 컨테이너 생성을 사용자 지정 하는 방법에 대 한 자세한 내용은 [Coccmanager:: CreateSite](../../mfc/reference/coccmanager-class.md#createsite)를 참조 하세요.

## <a name="colecontrolsitecreatecontrol"></a><a name="createcontrol"></a> COleControlSite:: CreateControl

개체에서 호스팅하는 ActiveX 컨트롤을 만듭니다 `COleControlSite` .

```
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);

virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>매개 변수

*pWndCtrl*<br/>
컨트롤을 나타내는 창 개체에 대 한 포인터입니다.

*가*<br/>
컨트롤의 고유 클래스 ID입니다.

*lpszWindowName*<br/>
컨트롤에 표시 되는 텍스트에 대 한 포인터입니다. Winodw의 캡션 또는 텍스트 속성 (있는 경우)의 값을 설정 합니다.

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

*.ppt*<br/>
`POINT`컨트롤의 왼쪽 위 모퉁이가 포함 된 구조체에 대 한 포인터입니다. 컨트롤의 크기는 *psize* 값에 따라 결정 됩니다. *Ppt* 및 *psize* 값은 컨트롤의 크기와 위치를 지정 하는 선택적 메서드입니다.

*psize*<br/>
`SIZE`컨트롤의 크기를 포함 하는 구조체에 대 한 포인터입니다. 왼쪽 위 모퉁이는 *ppt* 의 값에 따라 결정 됩니다. *Ppt* 및 *psize* 값은 컨트롤의 크기와 위치를 지정 하는 선택적 메서드입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

Windows *Dwstyle* 플래그의 하위 집합만에서 지원 됩니다 `CreateControl` .

- WS_VISIBLE 처음에 표시 되는 창을 만듭니다. 일반 창과 같은 컨트롤을 즉시 표시 하려는 경우에 필요 합니다.

- WS_DISABLED 처음에는 사용 하지 않도록 설정 된 창을 만듭니다. 비활성화 된 창은 사용자의 입력을 받을 수 없습니다. 컨트롤에 활성화 된 속성이 있으면를 설정할 수 있습니다.

- WS_BORDER 얇은 선 테두리가 있는 창을 만듭니다. 컨트롤에 BorderStyle 속성이 있으면를 설정할 수 있습니다.

- WS_GROUP는 컨트롤 그룹의 첫 번째 컨트롤을 지정 합니다. 사용자는 방향 키를 사용 하 여 그룹의 한 컨트롤에서 다음으로 키보드 포커스를 변경할 수 있습니다. 첫 번째 컨트롤이 같은 그룹에 속하는 WS_GROUP 스타일로 정의 된 모든 컨트롤입니다. WS_GROUP 스타일을 가진 다음 컨트롤은 그룹을 종료 하 고 다음 그룹을 시작 합니다.

- WS_TABSTOP 사용자가 TAB 키를 누를 때 키보드 포커스를 받을 수 있는 컨트롤을 지정 합니다. TAB 키를 누르면 키보드 포커스가 WS_TABSTOP 스타일의 다음 컨트롤로 변경 됩니다.

두 번째 오버 로드를 사용 하 여 기본 크기의 컨트롤을 만듭니다.

## <a name="colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a> COleControlSite::D estroyControl

개체를 소멸 시킵니다 `COleControlSite` .

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

작업이 완료 되 면 메모리에서 개체가 해제 되 고 개체에 대 한 모든 포인터가 더 이상 유효 하지 않게 됩니다.

## <a name="colecontrolsitedoverb"></a><a name="doverb"></a> COleControlSite::D 초과 b

지정 된 동사를 실행 합니다.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>매개 변수

*nVerb*<br/>
실행할 동사를 지정 합니다. 다음 중 하나를 포함할 수 있습니다.

|값|의미|기호|
|-----------|-------------|------------|
|0|기본 동사|OLEIVERB_PRIMARY|
|-1|보조 동사|(없음)|
|1|편집할 개체를 표시 합니다.|OLEIVERB_SHOW|
|-2|별도의 창에서 항목을 편집 합니다.|OLEIVERB_OPEN|
|-3|개체를 숨깁니다.|OLEIVERB_HIDE|
|-4|내부에서 컨트롤을 활성화 합니다.|OLEIVERB_UIACTIVATE|
|-5|추가 사용자 인터페이스 요소 없이 내부에서 컨트롤을 활성화 합니다.|OLEIVERB_INPLACEACTIVATE|
|-7|컨트롤의 속성을 표시 합니다.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
항목을 활성화 하는 메시지에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 함수는 컨트롤의 인터페이스를 통해 직접 `IOleObject` 를 호출 하 여 지정 된 동사를 실행 합니다. 이 함수 호출의 결과로 예외가 throw 되 면 HRESULT 오류 코드가 반환 됩니다.

자세한 내용은 Windows SDK의 [IOleObject::D 과도 b](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 를 참조 하세요.

## <a name="colecontrolsiteenabledsc"></a><a name="enabledsc"></a> COleControlSite:: EnableDSC

컨트롤 사이트에 대 한 데이터 소싱을 사용 하도록 설정 합니다.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>설명

컨트롤 사이트에 대 한 데이터 소싱을 활성화 하 고 초기화 하기 위해 프레임 워크에서 호출 됩니다. 사용자 지정 동작을 제공 하려면이 함수를 재정의 합니다.

## <a name="colecontrolsiteenablewindow"></a><a name="enablewindow"></a> COleControlSite:: EnableWindow

컨트롤 사이트에 마우스 및 키보드 입력을 사용 하거나 사용 하지 않도록 설정 합니다.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
창을 사용 하거나 사용 하지 않도록 설정할지 여부를 지정 합니다. 창 입력을 사용 하려면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

이전에 창을 사용할 수 없는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

## <a name="colecontrolsitefreezeevents"></a><a name="freezeevents"></a> COleControlSite:: FreezeEvents

컨트롤 사이트에서 컨트롤에서 발생 하는 이벤트를 처리할지 아니면 무시할지를 지정 합니다.

```cpp
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>매개 변수

*bFreeze*<br/>
컨트롤 사이트에서 이벤트 수락을 중지하려는지를 지정합니다. 컨트롤이 이벤트를 수락 하지 않으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Bfreeze* 가 TRUE 인 경우 컨트롤 사이트는 이벤트를 중지 하도록 컨트롤에 요청 합니다. *Bfreeze* 가 FALSE 인 경우 컨트롤 사이트는 이벤트를 계속 발생 하도록 컨트롤에 요청 합니다.

> [!NOTE]
> 컨트롤은 컨트롤 사이트에서 요청 하는 경우 이벤트 발생을 중지 하는 데 필요 하지 않습니다. 계속 해 서 실행 될 수 있지만 모든 후속 이벤트는 제어 사이트에서 무시 됩니다.

## <a name="colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a> COleControlSite::GetControlInfo

컨트롤의 키보드 니모닉 및 키보드 동작에 대 한 정보를 검색 합니다.

```cpp
void GetControlInfo();
```

### <a name="remarks"></a>설명

정보는 [COleControlSite:: m_ctlInfo](#m_ctlinfo)에 저장 됩니다.

## <a name="colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a> COleControlSite::GetDefBtnCode

컨트롤이 기본 푸시 단추 인지 여부를 확인 합니다.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>반환 값

다음 값 중 하나일 수 있습니다.

- DLGC_DEFPUSHBUTTON 컨트롤은 대화 상자의 기본 단추입니다.

- DLGC_UNDEFPUSHBUTTON 컨트롤이 대화 상자의 기본 단추가 아닙니다.

- **0** 컨트롤은 단추가 아닙니다.

## <a name="colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a> COleControlSite::GetDlgCtrlID

컨트롤의 식별자를 검색 합니다.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>반환 값

컨트롤의 대화 상자 항목 식별자입니다.

## <a name="colecontrolsitegeteventiid"></a><a name="geteventiid"></a> COleControlSite::GetEventIID

컨트롤의 기본 이벤트 인터페이스에 대 한 포인터를 검색 합니다.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>매개 변수

*piid*<br/>
인터페이스 ID에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다. 성공 하면 *piid* 에 컨트롤의 기본 이벤트 인터페이스에 대 한 인터페이스 ID가 포함 됩니다.

## <a name="colecontrolsitegetexstyle"></a><a name="getexstyle"></a> COleControlSite:: GetExStyle

창의 확장 스타일을 검색 합니다.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>반환 값

컨트롤 창의 확장 스타일입니다.

### <a name="remarks"></a>설명

일반 스타일을 검색 하려면 [COleControlSite:: GetStyle](#getstyle)을 호출 합니다.

## <a name="colecontrolsitegetproperty"></a><a name="getproperty"></a> COleControlSite:: GetProperty

*Dwdispid* 로 지정 된 컨트롤 속성을 가져옵니다.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
검색할 컨트롤의 기본 인터페이스에 있는 속성의 디스패치 ID를 식별 `IDispatch` 합니다.

*vtProp*<br/>
검색할 속성의 유형을 지정 합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*pvProp*<br/>
속성 값을 받을 변수의 주소입니다. *VtProp* 에 지정 된 형식과 일치 해야 합니다.

### <a name="remarks"></a>설명

*PvProp* 을 통해 값이 반환 됩니다.

## <a name="colecontrolsitegetstyle"></a><a name="getstyle"></a> COleControlSite:: GetStyle

컨트롤 사이트의 스타일을 검색 합니다.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>반환 값

창의 스타일입니다.

### <a name="remarks"></a>설명

가능한 값 목록은 [Windows 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 참조 하세요. 컨트롤 사이트의 확장 스타일을 검색 하려면 [COleControlSite:: GetExStyle](#getexstyle)을 호출 합니다.

## <a name="colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a> COleControlSite:: GetWindowText

컨트롤의 현재 텍스트를 검색 합니다.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>매개 변수

*str*<br/>
`CString`컨트롤의 현재 텍스트를 포함 하는 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

컨트롤에서 캡션 스톡 속성을 지 원하는 경우에는이 값이 반환 됩니다. Caption 스톡 속성이 지원 되지 않는 경우 Text 속성의 값이 반환 됩니다.

## <a name="colecontrolsiteinvokehelper"></a><a name="invokehelper"></a> COleControlSite:: InvokeHelper

*Wflags* 로 지정 된 컨텍스트에서 *dwdispid* 로 지정 된 메서드 또는 속성을 호출 합니다.

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
호출 될 컨트롤의 인터페이스에 있는 속성 또는 메서드의 디스패치 ID를 식별 `IDispatch` 합니다.

*wFlags*<br/>
IDispatch::Invoke 호출의 컨텍스트를 설명하는 플래그입니다. 가능한 *Wflags* 값 `IDispatch::Invoke` 은 Windows SDK에서를 참조 하세요.

*vtRet*<br/>
반환 값 형식을 지정합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*pvRet*<br/>
속성 값이나 반환 값을 받을 변수의 주소입니다. *Vtret* 에 지정 된 형식과 일치 해야 합니다.

*pbParamInfo*<br/>
*Pbparaminfo* 다음에 매개 변수의 형식을 지정 하는 null로 끝나는 바이트 문자열에 대 한 포인터입니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*...*<br/>
*Pbparaminfo* 에 지정 된 형식의 매개 변수 목록입니다.

### <a name="remarks"></a>설명

*Pbparaminfo* 매개 변수는 메서드나 속성에 전달 되는 매개 변수의 형식을 지정 합니다. 인수의 변수 목록은 구문 선언에서 ...로 표시됩니다.

이 함수는 매개 변수를 VARIANTARG 값으로 변환한 다음 `IDispatch::Invoke` 컨트롤에서 메서드를 호출 합니다. `IDispatch::Invoke` 호출에 실패하면 이 함수가 예외를 throw합니다. 에서 반환 하는 상태 코드가 `IDispatch::Invoke` 인 경우 `DISP_E_EXCEPTION` 이 함수는 개체를 throw 하 고 `COleDispatchException` , 그렇지 않으면을 throw `COleException` 합니다.

## <a name="colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a> COleControlSite::InvokeHelperV

*Wflags* 로 지정 된 컨텍스트에서 *dwdispid* 로 지정 된 메서드 또는 속성을 호출 합니다.

```
virtual void InvokeHelperV(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo,
    va_list argList);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
호출 될 컨트롤의 인터페이스에 있는 속성 또는 메서드의 디스패치 ID를 식별 `IDispatch` 합니다.

*wFlags*<br/>
IDispatch::Invoke 호출의 컨텍스트를 설명하는 플래그입니다.

*vtRet*<br/>
반환 값 형식을 지정합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*pvRet*<br/>
속성 값이나 반환 값을 받을 변수의 주소입니다. *Vtret* 에 지정 된 형식과 일치 해야 합니다.

*pbParamInfo*<br/>
*Pbparaminfo* 다음에 매개 변수의 형식을 지정 하는 null로 끝나는 바이트 문자열에 대 한 포인터입니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*argList*<br/>
가변 인수 목록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*Pbparaminfo* 매개 변수는 메서드나 속성에 전달 되는 매개 변수의 형식을 지정 합니다. 호출 되는 메서드 또는 속성에 대 한 추가 매개 변수는 *va_list* 매개 변수를 사용 하 여 전달할 수 있습니다.

일반적으로이 함수는에 의해 호출 됩니다 `COleControlSite::InvokeHelper` .

## <a name="colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a> COleControlSite:: IsDefaultButton

컨트롤이 기본 단추 인지 여부를 확인 합니다.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>반환 값

컨트롤이 창의 기본 단추 이면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

## <a name="colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a> COleControlSite:: IsWindowEnabled

컨트롤 사이트를 사용할 수 있는지 여부를 확인 합니다.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>반환 값

컨트롤이 활성화 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 값은 컨트롤의 활성화 된 스톡 속성에서 검색 됩니다.

## <a name="colecontrolsitem_biswindowless"></a><a name="m_biswindowless"></a> COleControlSite:: m_bIsWindowless

개체가 창 없는 컨트롤 인지 여부를 확인 합니다.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>설명

컨트롤에 창이 없으면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="colecontrolsitem_ctlinfo"></a><a name="m_ctlinfo"></a> COleControlSite:: m_ctlInfo

컨트롤에서 키보드 입력을 처리 하는 방법에 대 한 정보입니다.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>설명

이 정보는 [CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo) 구조에 저장 됩니다.

## <a name="colecontrolsitem_dweventsink"></a><a name="m_dweventsink"></a> COleControlSite:: m_dwEventSink

컨트롤의 이벤트 싱크에 있는 연결 지점의 쿠키를 포함 합니다.

```
DWORD m_dwEventSink;
```

## <a name="colecontrolsitem_dwmiscstatus"></a><a name="m_dwmiscstatus"></a> COleControlSite:: m_dwMiscStatus

컨트롤에 대 한 기타 정보를 포함 합니다.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK에서 [Olemisc](/windows/win32/api/oleidl/ne-oleidl-olemisc)를 참조 하십시오.

## <a name="colecontrolsitem_dwpropnotifysink"></a><a name="m_dwpropnotifysink"></a> COleControlSite:: m_dwPropNotifySink

[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 쿠키를 포함 합니다.

```
DWORD m_dwPropNotifySink;
```

## <a name="colecontrolsitem_dwstyle"></a><a name="m_dwstyle"></a> COleControlSite:: m_dwStyle

컨트롤의 창 스타일을 포함 합니다.

```
DWORD m_dwStyle;
```

## <a name="colecontrolsitem_hwnd"></a><a name="m_hwnd"></a> COleControlSite:: m_hWnd

컨트롤의 HWND를 포함 하거나 컨트롤이 창 없는 경우 NULL을 포함 합니다.

```
HWND m_hWnd;
```

## <a name="colecontrolsitem_iidevents"></a><a name="m_iidevents"></a> COleControlSite:: m_iidEvents

컨트롤의 기본 이벤트 싱크 인터페이스의 인터페이스 ID를 포함 합니다.

```
IID m_iidEvents;
```

## <a name="colecontrolsitem_nid"></a><a name="m_nid"></a> COleControlSite:: m_nID

컨트롤의 대화 상자 항목 ID를 포함 합니다.

```
UINT m_nID;
```

## <a name="colecontrolsitem_pactiveobject"></a><a name="m_pactiveobject"></a> COleControlSite:: m_pActiveObject

컨트롤의 [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) 인터페이스를 포함 합니다.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

## <a name="colecontrolsitem_pctrlcont"></a><a name="m_pctrlcont"></a> COleControlSite:: m_pCtrlCont

폼을 나타내는 컨트롤의 컨테이너를 포함 합니다.

```
COleControlContainer* m_pCtrlCont;
```

## <a name="colecontrolsitem_pinplaceobject"></a><a name="m_pinplaceobject"></a> COleControlSite:: m_pInPlaceObject

`IOleInPlaceObject`컨트롤의 [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) 인터페이스를 포함 합니다.

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

## <a name="colecontrolsitem_pobject"></a><a name="m_pobject"></a> COleControlSite:: m_pObject

`IOleObjectInterface`컨트롤의 인터페이스를 포함 합니다.

```
LPOLEOBJECT m_pObject;
```

## <a name="colecontrolsitem_pwindowlessobject"></a><a name="m_pwindowlessobject"></a> COleControlSite:: m_pWindowlessObject

`IOleInPlaceObjectWindowless`컨트롤의 [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) 인터페이스를 포함 합니다.

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

## <a name="colecontrolsitem_pwndctrl"></a><a name="m_pwndctrl"></a> COleControlSite:: m_pWndCtrl

컨트롤 자체를 나타내는 개체에 대 한 포인터를 포함 합니다 `CWnd` .

```
CWnd* m_pWndCtrl;
```

## <a name="colecontrolsitem_rect"></a><a name="m_rect"></a> COleControlSite:: m_rect

컨테이너의 창에 상대적인 컨트롤의 범위를 포함 합니다.

```
CRect m_rect;
```

## <a name="colecontrolsitemodifystyle"></a><a name="modifystyle"></a> COleControlSite::ModifyStyle

컨트롤의 스타일을 수정 합니다.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>매개 변수

*dwRemove*<br/>
현재 창 스타일에서 제거할 스타일입니다.

*dwAdd*<br/>
현재 창 스타일에서 추가 되는 스타일입니다.

*nFlags*<br/>
창 위치 지정 플래그입니다. 가능한 값 목록은 Windows SDK의 [Setwindowpos](/windows/win32/api/winuser/nf-winuser-setwindowpos) 함수를 참조 하세요.

### <a name="return-value"></a>반환 값

스타일이 변경 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

컨트롤의 스톡 Enabled 속성이 WS_DISABLED 설정에 맞게 수정 됩니다. 컨트롤의 스톡 Border Style 속성이 WS_BORDER에 대해 요청 된 설정과 일치 하도록 수정 됩니다. 다른 모든 스타일은 컨트롤의 창 핸들 (있는 경우)에 직접 적용 됩니다.

컨트롤의 창 스타일을 수정 합니다. 비트 OR (&#124;) 연산자를 사용 하 여 추가 하거나 제거할 스타일을 결합할 수 있습니다. 사용 가능한 창 스타일에 대 한 자세한 내용은 Windows SDK의 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 함수를 참조 하세요.

*Nflags* 가 0이 아닌 경우는 `ModifyStyle` Win32 함수를 호출 하 `SetWindowPos` 고 다음 4 개의 플래그와 *n 플래그* 를 결합 하 여 창을 다시 그립니다.

- SWP_NOSIZE 현재 크기를 유지 합니다.

- SWP_NOMOVE 현재 위치를 유지 합니다.

- SWP_NOZORDER 현재 Z 순서를 유지 합니다.

- SWP_NOACTIVATE는 창을 활성화 하지 않습니다.

창의 확장 스타일을 수정 하려면 [ModifyStyleEx](#modifystyleex)를 호출 합니다.

## <a name="colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a> COleControlSite::ModifyStyleEx

컨트롤의 확장 스타일을 수정 합니다.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>매개 변수

*dwRemove*<br/>
현재 창 스타일에서 제거할 확장 스타일입니다.

*dwAdd*<br/>
현재 창 스타일에서 추가 될 확장 스타일입니다.

*nFlags*<br/>
창 위치 지정 플래그입니다. 가능한 값 목록은 Windows SDK의 [Setwindowpos](/windows/win32/api/winuser/nf-winuser-setwindowpos) 함수를 참조 하세요.

### <a name="return-value"></a>반환 값

스타일이 변경 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

컨트롤의 스톡 모양 속성이 WS_EX_CLIENTEDGE 설정에 맞게 수정 됩니다. 다른 모든 확장 창 스타일은 컨트롤의 창 핸들 (있는 경우)에 직접 적용 됩니다.

컨트롤 사이트 개체의 창 확장 스타일을 수정 합니다. 비트 OR (&#124;) 연산자를 사용 하 여 추가 하거나 제거할 스타일을 결합할 수 있습니다. 사용 가능한 창 스타일에 대 한 자세한 내용은 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 함수를 참조 하세요.

*Nflags* 가 0이 아닌 경우는 `ModifyStyleEx` Win32 함수를 호출 하 `SetWindowPos` 고 다음 4 개의 플래그와 *n 플래그* 를 결합 하 여 창을 다시 그립니다.

- SWP_NOSIZE 현재 크기를 유지 합니다.

- SWP_NOMOVE 현재 위치를 유지 합니다.

- SWP_NOZORDER 현재 Z 순서를 유지 합니다.

- SWP_NOACTIVATE는 창을 활성화 하지 않습니다.

창의 확장 스타일을 수정 하려면 [ModifyStyle](#modifystyle)를 호출 합니다.

## <a name="colecontrolsitemovewindow"></a><a name="movewindow"></a> COleControlSite:: MoveWindow

컨트롤의 위치를 변경 합니다.

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
창 왼쪽의 새 위치입니다.

*y*<br/>
창 위쪽의 새 위치입니다.

*nWidth*<br/>
창의 새 너비입니다.

*nHeight*<br/>
창의 새 높이입니다.

## <a name="colecontrolsitequickactivate"></a><a name="quickactivate"></a> COleControlSite:: QuickActivate

포함 된 컨트롤을 신속 하 게 활성화 합니다.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>반환 값

컨트롤 사이트가 활성화 된 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

사용자가 컨트롤의 생성 프로세스를 재정의 하는 경우에만이 함수를 호출 해야 합니다.

`IPersist*::Load` `IPersist*::InitNew` 빠른 활성화가 수행 된 후 및 메서드를 호출 해야 합니다. 컨트롤은 빠른 활성화 중에 컨테이너의 싱크에 대 한 연결을 설정 해야 합니다. 그러나 이러한 연결은 `IPersist*::Load` 또는가 호출 될 때까지 라이브가 아닙니다 `IPersist*::InitNew` .

## <a name="colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a> COleControlSite:: SafeSetProperty

*Dwdispid* 로 지정 된 컨트롤 속성을 설정 합니다.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
설정할 컨트롤의 인터페이스에 있는 속성 또는 메서드의 디스패치 ID를 식별 `IDispatch` 합니다.

*vtProp*<br/>
설정할 속성의 유형을 지정 합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*...*<br/>
*VtProp* 에 의해 지정 된 형식의 단일 매개 변수입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 및와 달리 `SetProperty` `SetPropertyV` 오류가 발생 한 경우 (예: 존재 하지 않는 속성을 설정 하려는 경우) 예외가 throw 되지 않습니다.

## <a name="colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a> COleControlSite:: SetDefaultButton

컨트롤을 기본 단추로 설정 합니다.

```cpp
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>매개 변수

*bDefault*<br/>
컨트롤이 기본 단추가 되도록 하려면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤에 OLEMISC_ACTSLIKEBUTTON 상태 비트가 설정 되어 있어야 합니다.

## <a name="colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a> COleControlSite::SetDlgCtrlID

컨트롤의 대화 상자 항목 식별자에 대 한 값을 변경 합니다.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
새 식별자 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 창의 이전 대화 상자 항목 식별자입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="colecontrolsitesetfocus"></a><a name="setfocus"></a> COleControlSite:: SetFocus

포커스를 컨트롤에 설정 합니다.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>매개 변수

*lpmsg*<br/>
[MSG 구조체](/windows/win32/api/winuser/ns-winuser-msg)에 대 한 포인터입니다. 이 구조는 `SetFocus` 현재 제어 사이트에 포함 된 컨트롤에 대 한 요청을 트리거하는 Windows 메시지를 포함 합니다.

### <a name="return-value"></a>반환 값

이전에 포커스가 있던 창에 대 한 포인터입니다.

## <a name="colecontrolsitesetproperty"></a><a name="setproperty"></a> COleControlSite:: SetProperty

*Dwdispid* 로 지정 된 컨트롤 속성을 설정 합니다.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
설정할 컨트롤의 인터페이스에 있는 속성 또는 메서드의 디스패치 ID를 식별 `IDispatch` 합니다.

*vtProp*<br/>
설정할 속성의 유형을 지정 합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*...*<br/>
*VtProp* 에 의해 지정 된 형식의 단일 매개 변수입니다.

### <a name="remarks"></a>설명

에 `SetProperty` 오류가 발생 하면 예외가 throw 됩니다.

예외의 형식은 속성 또는 메서드를 설정 하려는 시도의 반환 값에 의해 결정 됩니다. 반환 값이 이면이 `DISP_E_EXCEPTION` `COleDispatchExcpetion` throw 되 고, 그렇지 않으면이 throw 됩니다 `COleException` .

## <a name="colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a> COleControlSite:: SetPropertyV

*Dwdispid* 로 지정 된 컨트롤 속성을 설정 합니다.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
설정할 컨트롤의 인터페이스에 있는 속성 또는 메서드의 디스패치 ID를 식별 `IDispatch` 합니다.

*vtProp*<br/>
설정할 속성의 유형을 지정 합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)의 설명 섹션을 참조하세요.

*argList*<br/>
인수 목록에 대한 포인터입니다.

### <a name="remarks"></a>설명

호출 되는 메서드 또는 속성에 대 한 추가 매개 변수는 *arg_list* 매개 변수를 사용 하 여 인수가 될 수 있습니다. 에 `SetProperty` 오류가 발생 하면 예외가 throw 됩니다.

예외의 형식은 속성 또는 메서드를 설정 하려는 시도의 반환 값에 의해 결정 됩니다. 반환 값이 이면이 `DISP_E_EXCEPTION` `COleDispatchExcpetion` throw 되 고, 그렇지 않으면이 throw 됩니다 `COleException` .

## <a name="colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a> COleControlSite:: SetWindowPos

컨트롤 사이트의 크기, 위치 및 Z 순서를 설정 합니다.

```
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT nFlags);
```

### <a name="parameters"></a>매개 변수

*pWndInsertAfter*<br/>
창에 대 한 포인터입니다.

*x*<br/>
창 왼쪽의 새 위치입니다.

*y*<br/>
창 위쪽의 새 위치입니다.

*cx*<br/>
창의 새 너비입니다.

*cy*<br/>
창의 새 높이입니다.

*nFlags*<br/>
창 크기 조정 및 위치 지정 플래그를 지정 합니다. 가능한 값은 Windows SDK에서 [Setwindowpos](/windows/win32/api/winuser/nf-winuser-setwindowpos) 의 설명 섹션을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

## <a name="colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a> COleControlSite:: SetWindowText

컨트롤 사이트에 대 한 텍스트를 설정 합니다.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>매개 변수

*lpszString*<br/>
새 제목 또는 컨트롤 텍스트로 사용 되는 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 먼저 캡션 스톡 속성을 설정 하려고 시도 합니다. Caption 스톡 속성이 지원 되지 않는 경우 Text 속성이 대신 설정 됩니다.

## <a name="colecontrolsiteshowwindow"></a><a name="showwindow"></a> COleControlSite:: ShowWindow

창의 표시 상태를 설정 합니다.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>매개 변수

*nCmdShow*<br/>
컨트롤 사이트를 표시 하는 방법을 지정 합니다. 다음 값 중 하나 여야 합니다.

- SW_HIDE이 창을 숨기고 다른 창으로 활성화를 전달 합니다.

- SW_MINIMIZE 창을 최소화 하 고 시스템 목록에서 최상위 창을 활성화 합니다.

- SW_RESTORE 활성화 되 고 창이 표시 됩니다. 창이 최소화 되거나 최대화 된 경우 Windows에서 원래 크기와 위치로 복원 합니다.

- SW_SHOW 창을 활성화 하 고 현재 크기와 위치에 표시 합니다.

- SW_SHOWMAXIMIZED 창을 활성화 하 고 최대화 된 창으로 표시 합니다.

- SW_SHOWMINIMIZED 창을 활성화 하 고 아이콘으로 표시 합니다.

- SW_SHOWMINNOACTIVE 창을 아이콘으로 표시 합니다. 현재 활성 상태인 창은 활성 상태로 유지 됩니다.

- SW_SHOWNA 현재 상태로 창을 표시 합니다. 현재 활성 상태인 창은 활성 상태로 유지 됩니다.

- SW_SHOWNOACTIVATE 가장 최근의 크기와 위치로 창을 표시 합니다. 현재 활성 상태인 창은 활성 상태로 유지 됩니다.

- SW_SHOWNORMAL 활성화 되 고 창이 표시 됩니다. 창이 최소화 되거나 최대화 된 경우 Windows에서 원래 크기와 위치로 복원 합니다.

### <a name="return-value"></a>반환 값

창이 이전에 표시 되는 경우 0이 아닙니다. 이전에 창을 숨긴 경우 0입니다.

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer 클래스](../../mfc/reference/colecontrolcontainer-class.md)
