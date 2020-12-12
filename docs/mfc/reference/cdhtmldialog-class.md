---
description: '자세히 알아보기: CDHtmlDialog 클래스'
title: CDHtmlDialog 클래스
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: aa99d10b0d0ff6920f839d7588d80f489b971384
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185286"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog 클래스

는 대화 상자 리소스가 아닌 HTML을 사용 하 여 사용자 인터페이스를 구현 하는 대화 상자를 만드는 데 사용 됩니다.

## <a name="syntax"></a>구문

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDHtmlDialog:: CDHtmlDialog](#cdhtmldialog)|CDHtmlDialog 개체를 생성 합니다.|
|[CDHtmlDialog:: ~ CDHtmlDialog](#_dtorcdhtmldialog)|CDHtmlDialog 개체를 소멸 시킵니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|로드 된 페이지의 스크립팅 개체가 컨트롤 사이트의 외부 디스패치에 액세스할 수 있는지 여부를 확인 하기 위해 액세스 권한으로 호출 되는 Overridable입니다. 디스패치가 스크립팅에 안전 하거나 현재 영역에서 스크립팅에 안전 하지 않은 개체를 허용 하는지 확인 합니다.|
|[CDHtmlDialog:: CreateControlSite](#createcontrolsite)|대화 상자에서 WebBrowser 컨트롤을 호스트할 컨트롤 사이트 인스턴스를 만드는 데 사용 되는 재정의 가능입니다.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|HTML 페이지에서 ActiveX 컨트롤의 속성 값과 멤버 변수 간에 데이터를 교환 합니다.|
|[CDHtmlDialog::D DX_DHtml_CheckBox](#ddx_dhtml_checkbox)|멤버 변수와 HTML 페이지의 확인란 간에 데이터를 교환 합니다.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|HTML 페이지의 멤버 변수와 HTML 요소 속성 간에 데이터를 교환 합니다.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|멤버 변수와 HTML 페이지의 라디오 단추 간에 데이터를 교환 합니다.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|HTML 페이지의 목록 상자 인덱스를 가져오거나 설정 합니다.|
|[CDHtmlDialog::D DX_DHtml_SelectString](#ddx_dhtml_selectstring)|HTML 페이지에서 현재 인덱스를 기반으로 하는 목록 상자 항목의 표시 텍스트를 가져오거나 설정 합니다.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|HTML 페이지의 현재 인덱스를 기반으로 하는 목록 상자 항목의 값을 가져오거나 설정 합니다.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|모덜리스 대화 상자를 소멸 시킵니다.|
|[CDHtmlDialog:: EnableModeless](#enablemodeless)|모덜리스 대화 상자를 사용 합니다.|
|[CDHtmlDialog:: FilterDataObject](#filterdataobject)|호스팅된 브라우저에서 만든 클립보드 데이터 개체를 대화 상자에서 필터링 할 수 있습니다.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|`IDispatch`HTML 문서에 포함 된 ActiveX 컨트롤에서 인터페이스를 검색 합니다.|
|[CDHtmlDialog:: GetControlProperty](#getcontrolproperty)|지정 된 ActiveX 컨트롤의 요청 된 속성을 검색 합니다.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|현재 문서와 연결 된 URL (Uniform Resource Locator)을 검색 합니다.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|현재 로드 된 HTML 문서에서 IHTMLDocument2 인터페이스를 검색 합니다.|
|[CDHtmlDialog:: GetDropTarget](#getdroptarget)|대화에서 대체 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)를 제공할 수 있도록 놓기 대상으로 사용 되는 경우 포함 된 WebBrowser 컨트롤에서 호출 됩니다.|
|[CDHtmlDialog:: GetElement](#getelement)|HTML 요소에 대 한 인터페이스를 가져옵니다.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|`innerHTML`HTML 요소의 속성을 검색 합니다.|
|[CDHtmlDialog:: GetElementInterface](#getelementinterface)|HTML 요소에서 요청 된 인터페이스 포인터를 검색 합니다.|
|[CDHtmlDialog:: GetElementProperty](#getelementproperty)|HTML 요소의 속성 값을 검색 합니다.|
|[CDHtmlDialog:: GetElementText](#getelementtext)|`innerText`HTML 요소의 속성을 검색 합니다.|
|[CDHtmlDialog::GetEvent](#getevent)|`IHTMLEventObj`현재 이벤트 개체에 대 한 포인터를 가져옵니다.|
|[CDHtmlDialog::GetExternal](#getexternal)|호스트의 인터페이스를 가져옵니다 `IDispatch` .|
|[CDHtmlDialog:: GetHostInfo](#gethostinfo)|호스트의 UI 기능을 검색 합니다.|
|[CDHtmlDialog:: GetOptionKeyPath](#getoptionkeypath)|사용자 기본 설정이 저장 되는 레지스트리 키를 검색 합니다.|
|[CDHtmlDialog::HideUI](#hideui)|호스트의 UI를 숨깁니다.|
|[CDHtmlDialog:: IsExternalDispatchSafe](#isexternaldispatchsafe)|호스트의 인터페이스를 스크립팅에 안전 하 게 사용할 수 있는지 여부를 나타냅니다 `IDispatch` .|
|[CDHtmlDialog:: LoadFromResource](#loadfromresource)|지정 된 리소스를 WebBrowser 컨트롤에 로드 합니다.|
|[CDHtmlDialog:: Navigate](#navigate)|지정 된 URL로 이동 합니다.|
|[CDHtmlDialog:: OnBeforeNavigate](#onbeforenavigate)|탐색 이벤트가 발생 하기 전에 프레임 워크에서 호출 됩니다.|
|[CDHtmlDialog:: OnDocumentComplete](#ondocumentcomplete)|문서가 READYSTATE_COMPLETE 상태에 도달 했을 때 응용 프로그램에 알리기 위해 프레임 워크에서 호출 됩니다.|
|[CDHtmlDialog:: OnDocWindowActivate](#ondocwindowactivate)|문서 창이 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.|
|[CDHtmlDialog:: On프레임 창 활성화](#onframewindowactivate)|프레임 창이 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.|
|[CDHtmlDialog:: OnInitDialog](#oninitdialog)|WM_INITDIALOG 메시지에 대 한 응답으로 호출 됩니다.|
|[CDHtmlDialog:: OnNavigateComplete](#onnavigatecomplete)|탐색 이벤트가 완료 된 후 프레임 워크에서 호출 됩니다.|
|[CDHtmlDialog:: ResizeBorder](#resizeborder)|테두리 공간 크기를 조정 해야 함을 개체에 경고 합니다.|
|[CDHtmlDialog:: SetControlProperty](#setcontrolproperty)|ActiveX 컨트롤의 속성을 새 값으로 설정 합니다.|
|[CDHtmlDialog:: SetElementHtml](#setelementhtml)|`innerHTML`HTML 요소의 속성을 설정 합니다.|
|[CDHtmlDialog:: SetElementProperty](#setelementproperty)|HTML 요소의 속성을 설정 합니다.|
|[CDHtmlDialog:: SetElementText](#setelementtext)|`innerText`HTML 요소의 속성을 설정 합니다.|
|[CDHtmlDialog:: SetExternalDispatch](#setexternaldispatch)|호스트의 인터페이스를 설정 `IDispatch` 합니다.|
|[CDHtmlDialog:: SetHostFlags](#sethostflags)|호스트의 UI 플래그를 설정 합니다.|
|[CDHtmlDialog:: ShowContextMenu](#showcontextmenu)|상황에 맞는 메뉴가 표시 되기 전에 호출 됩니다.|
|[CDHtmlDialog:: ShowUI](#showui)|호스트의 UI를 표시 합니다.|
|[CDHtmlDialog:: TranslateAccelerator](#translateaccelerator)|메뉴 액셀러레이터 키 메시지를 처리 하기 위해 호출 됩니다.|
|[CDHtmlDialog:: TranslateUrl](#translateurl)|로드할 URL을 수정 하기 위해 호출 됩니다.|
|[CDHtmlDialog:: UpdateUI](#updateui)|명령 상태가 변경 되었음을 호스트에 알리기 위해 호출 됩니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|HTML 문서 제목을 대화 상자 캡션으로 사용할지 여부를 나타냅니다.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|표시할 HTML 리소스의 리소스 ID입니다.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|웹 브라우저 응용 프로그램에 대 한 포인터입니다.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|HTML 문서에 대 한 포인터입니다.|
|[CDHtmlDialog:: m_strCurrentUrl](#m_strcurrenturl)|현재 URL입니다.|
|[CDHtmlDialog:: m_szHtmlResID](#m_szhtmlresid)|HTML 리소스 ID의 문자열 버전입니다.|

## <a name="remarks"></a>설명

`CDHtmlDialog` html 리소스 또는 URL에서 표시할 HTML을 로드할 수 있습니다.

`CDHtmlDialog` 는 HTML 컨트롤을 사용 하 여 데이터 교환을 수행 하 고 단추 클릭과 같은 HTML 컨트롤의 이벤트를 처리할 수도 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdhtml

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a> DDX_DHtml 도우미 매크로

DDX_DHtml 도우미 매크로를 사용 하면 HTML 페이지에서 일반적으로 사용 되는 컨트롤 속성에 쉽게 액세스할 수 있습니다.

### <a name="data-exchange-macros"></a>데이터 교환 매크로

|Name|설명|
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|선택한 컨트롤에서 Value 속성을 설정 하거나 검색 합니다.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|현재 요소의 시작 태그와 끝 태그 사이에 있는 텍스트를 설정 하거나 검색 합니다.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|현재 요소의 시작 태그와 끝 태그 사이에 HTML을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|대상 URL 또는 앵커 지점을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|대상 창 또는 프레임을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|문서에서 이미지 또는 비디오 클립의 이름을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|연결 된 프레임의 URL을 설정 하거나 검색 합니다.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|연결 된 프레임의 URL을 설정 하거나 검색 합니다.|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a> CDHtmlDialog:: CanAccessExternal

로드 된 페이지의 스크립팅 개체가 컨트롤 사이트의 외부 디스패치에 액세스할 수 있는지 여부를 확인 하기 위해 액세스 권한으로 호출 되는 Overridable입니다. 디스패치가 스크립팅에 안전 하거나 현재 영역에서 스크립팅에 안전 하지 않은 개체를 허용 하는지 확인 합니다.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a> CDHtmlDialog:: CDHtmlDialog

리소스 기반 동적 HTML 대화 상자를 생성 합니다.

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszTemplateName*<br/>
대화 상자 템플릿 리소스의 이름인 null로 끝나는 문자열입니다.

*szHtmlResID*<br/>
HTML 리소스의 이름인 null로 끝나는 문자열입니다.

*pParentWnd*<br/>
Dialog 개체가 속한 부모 또는 소유자 창 개체 ( [CWnd](../../mfc/reference/cwnd-class.md)형식)에 대 한 포인터입니다. NULL 인 경우에는 대화 상자 개체의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

*nIDTemplate*<br/>
대화 상자 템플릿 리소스의 ID 번호를 포함 합니다.

*nHtmlResID*<br/>
HTML 리소스의 ID 번호를 포함 합니다.

### <a name="remarks"></a>설명

생성자의 두 번째 형태는 템플릿 이름을 통해 대화 상자 리소스에 대 한 액세스를 제공 합니다. 세 번째 형식의 생성자는 리소스 템플릿의 ID를 통해 대화 상자 리소스에 대 한 액세스를 제공 합니다. 일반적으로 ID는 **IDD_** 접두사로 시작 합니다.

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a> CDHtmlDialog:: ~ CDHtmlDialog

CDHtmlDialog 개체를 소멸 시킵니다.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>설명

[CWnd::D estroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) 멤버 함수를 사용 하 여 [CDialog:: Create](../../mfc/reference/cdialog-class.md#create)에서 만든 모덜리스 대화 상자를 삭제 해야 합니다.

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a> CDHtmlDialog:: CreateControlSite

대화 상자에서 WebBrowser 컨트롤을 호스트할 컨트롤 사이트 인스턴스를 만드는 데 사용 되는 재정의 가능입니다.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>매개 변수

*pContainer*<br/>
[COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md) 개체에 대 한 포인터입니다.

*ppSite*<br/>
[COleControlSite](../../mfc/reference/colecontrolsite-class.md)에 대 한 포인터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 재정의 하 여 사용자 고유의 컨트롤 사이트 클래스의 인스턴스를 반환할 수 있습니다.

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a> CDHtmlDialog::D DX_DHtml_AxControl

HTML 페이지에서 ActiveX 컨트롤의 속성 값과 멤버 변수 간에 데이터를 교환 합니다.

```cpp
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*szId*<br/>
ActiveX 컨트롤의 HTML 소스에 있는 개체 태그의 ID 매개 변수 값입니다.

*dispId*<br/>
데이터를 교환 하려는 속성의 디스패치 ID입니다.

*szPropName*<br/>
속성의 이름입니다.

*var*<br/>
ActiveX 컨트롤 속성과 교환 되는 값을 보유 하는 VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md)또는 [CComVariant](../../atl/reference/ccomvariant-class.md)형식의 데이터 멤버입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a> CDHtmlDialog::D DX_DHtml_CheckBox

멤버 변수와 HTML 페이지의 확인란 간에 데이터를 교환 합니다.

```cpp
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*szId*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*value*<br/>
교환 되는 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a> CDHtmlDialog::D DX_DHtml_ElementText

HTML 페이지의 멤버 변수와 HTML 요소 속성 간에 데이터를 교환 합니다.

```cpp
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*szId*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*dispId*<br/>
데이터를 교환 하려는 HTML 요소의 디스패치 ID입니다.

*value*<br/>
교환 되는 값입니다.

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a> CDHtmlDialog::D DX_DHtml_Radio

멤버 변수와 HTML 페이지의 라디오 단추 간에 데이터를 교환 합니다.

```cpp
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*szId*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*value*<br/>
교환 되는 값입니다.

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a> CDHtmlDialog::D DX_DHtml_SelectIndex

HTML 페이지의 목록 상자 인덱스를 가져오거나 설정 합니다.

```cpp
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*szId*<br/>
HTML 컨트롤의 매개 변수에 대해 지정한 값입니다 `id` .

*value*<br/>
교환 되는 값입니다.

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a> CDHtmlDialog::D DX_DHtml_SelectString

HTML 페이지에서 현재 인덱스를 기반으로 하는 목록 상자 항목의 표시 텍스트를 가져오거나 설정 합니다.

```cpp
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*szId*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*value*<br/>
교환 되는 값입니다.

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a> CDHtmlDialog::D DX_DHtml_SelectValue

HTML 페이지의 현재 인덱스를 기반으로 하는 목록 상자 항목의 값을 가져오거나 설정 합니다.

```cpp
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*szId*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*value*<br/>
교환 되는 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a> CDHtmlDialog::D estroyModeless

개체에서 모덜리스 대화 상자를 분리 `CDHtmlDialog` 하 고 개체를 소멸 시킵니다.

```cpp
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a> CDHtmlDialog:: EnableModeless

모덜리스 대화 상자를 사용 합니다.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>매개 변수

*fEnable*<br/>
Windows SDK에서 *Fenable* in [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a> CDHtmlDialog:: FilterDataObject

호스팅된 브라우저에서 만든 클립보드 데이터 개체를 대화 상자에서 필터링 할 수 있습니다.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>매개 변수

*pDO*<br/>
Windows SDK에서 PDO [:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) 의 *pDO* 를 참조 하세요.

*ppDORet*<br/>
Windows SDK에서 *Ppg Oret* 를 참조 하십시오 `IDocHostUIHandler::FilterDataObject` .

### <a name="return-value"></a>반환 값

S_FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 CDHtmlDialog의 [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))구현입니다.

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a> CDHtmlDialog:: GetControlDispatch

[GetDHtmlDocument](#getdhtmldocument)에서 반환하는 HTML 문서에 포함된 ActiveX 컨트롤에서 인터페이스 `IDispatch`를 검색합니다.

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>매개 변수

*szId*<br/>
ActiveX 컨트롤의 HTML ID입니다.

*ppdisp*<br/>
`IDispatch`웹 페이지에 있는 경우 컨트롤의 인터페이스입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a> CDHtmlDialog:: GetControlProperty

지정 된 ActiveX 컨트롤의 요청 된 속성을 검색 합니다.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>매개 변수

*szId*<br/>
ActiveX 컨트롤의 HTML ID입니다.

*szPropName*<br/>
현재 사용자의 기본 로캘의 속성 이름입니다.

*pdispControl*<br/>
`IDispatch`ActiveX 컨트롤의 포인터입니다.

*dispId*<br/>
속성의 디스패치 ID입니다.

### <a name="return-value"></a>반환 값

요청 된 속성을 포함 하는 variant 이거나, 컨트롤 또는 속성을 찾을 수 없는 경우 빈 variant입니다.

### <a name="remarks"></a>설명

오버 로드는 최하위 수준에서 가장 효율적으로 나열 됩니다.

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a> CDHtmlDialog:: GetCurrentUrl

현재 문서와 연결 된 URL (Uniform Resource Locator)을 검색 합니다.

```cpp
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>매개 변수

*szUrl*<br/>
검색할 URL을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a> CDHtmlDialog:: GetDHtmlDocument

현재 로드 된 HTML 문서에서 [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) 인터페이스를 검색 합니다.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>매개 변수

HTML 문서에 대 한 포인터에 포인터를 *\* \* pphtmlDoc* 합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다. 성공 하면 S_OK을 반환 합니다.

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a> CDHtmlDialog:: GetDropTarget

대화에서 대체 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)를 제공할 수 있도록 놓기 대상으로 사용 되는 경우 포함 된 WebBrowser 컨트롤에서 호출 됩니다.

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>매개 변수

*pDropTarget*<br/>
Windows SDK에서 [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) 의 *pdroptarget* 을 참조 하세요.

*ppDropTarget*<br/>
Windows SDK의 *Ppdroptarget* 을 참조 하십시오 `IDocHostUIHandler::GetDropTarget` .

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a> CDHtmlDialog:: GetElement

*Szelementid* 로 지정 된 HTML 요소에 대 한 인터페이스를 반환 합니다.

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

*ppdisp*<br/>
`IDispatch`요청 된 요소 또는 요소 컬렉션에 대 한 포인터입니다.

*pbCollection*<br/>
*Ppdisp* 가 나타내는 개체가 단일 요소 인지 아니면 요소의 컬렉션 인지를 나타내는 부울입니다.

*pphtmlElement*<br/>
`IHTMLElement`요청 된 요소에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

지정 된 ID를 가진 둘 이상의 요소가 있을 수 있는 조건을 처리 해야 하는 경우 첫 번째 오버 로드를 사용 합니다. 마지막 매개 변수를 사용 하 여 반환 된 인터페이스 포인터가 컬렉션 또는 단일 항목에 대 한 것인지 여부를 확인할 수 있습니다. 인터페이스 포인터가 컬렉션에 있는 경우를 쿼리하고 `IHTMLElementCollection` 해당 속성을 사용 `item` 하 여 서 수 위치로 요소를 참조할 수 있습니다.

페이지에 동일한 ID를 가진 요소가 둘 이상 있으면 두 번째 오버 로드가 실패 합니다.

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a> CDHtmlDialog:: GetElementHtml

`innerHTML` *Szelementid* 로 식별 되는 HTML 요소의 속성을 검색 합니다.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

### <a name="return-value"></a>반환 값

`innerHTML` *Szelementid* 또는 NULL (요소를 찾을 수 없는 경우)로 식별 되는 HTML 요소의 속성입니다.

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a> CDHtmlDialog:: GetElementInterface

*Szelementid* 로 식별 되는 HTML 요소에서 요청 된 인터페이스 포인터를 검색 합니다.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

*ppvObj*<br/>
요소를 찾아 쿼리가 성공 하면 요청 된 인터페이스 포인터로 채워질 포인터의 주소입니다.

*refiid*<br/>
요청 된 인터페이스의 IID (인터페이스 ID)입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a> CDHtmlDialog:: GetElementProperty

*Szelementid* 로 식별 되는 HTML 요소에서 *dispId* 로 식별 된 속성의 값을 검색 합니다.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

*dispId*<br/>
속성의 디스패치 ID입니다.

### <a name="return-value"></a>반환 값

속성 또는 요소를 찾을 수 없는 경우 속성의 값 또는 빈 variant입니다.

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a> CDHtmlDialog:: GetElementText

`innerText` *Szelementid* 로 식별 되는 HTML 요소의 속성을 검색 합니다.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

### <a name="return-value"></a>반환 값

`innerText` *Szelementid* 또는 NULL로 식별 되는 HTML 요소의 속성 이거나, 속성 또는 요소를 찾을 수 없는 경우 NULL입니다.

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a> CDHtmlDialog:: GetEvent

`IHTMLEventObj`현재 이벤트 개체에 대 한 포인터를 반환 합니다.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>매개 변수

*ppEventObj*<br/>
인터페이스 포인터로 채워질 포인터의 주소입니다 `IHTMLEventObj` .

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 함수는 DHTML 이벤트 처리기 내 에서만 호출 해야 합니다.

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a> CDHtmlDialog:: GetExternal

호스트의 인터페이스를 가져옵니다 `IDispatch` .

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>매개 변수

*ppDispatch*<br/>
Windows SDK에서 [IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) 의 *ppdispatch* 를 참조 하세요.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 E_NOTIMPL을 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 CDHtmlDialog의 [IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))구현입니다.

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a> CDHtmlDialog:: GetHostInfo

호스트의 UI 기능을 검색 합니다.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>매개 변수

*pInfo*<br/>
Windows SDK에서 *Pinfo* 의 [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) 을 참조 하세요.

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a> CDHtmlDialog:: GetOptionKeyPath

사용자 기본 설정이 저장 되는 레지스트리 키를 검색 합니다.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>매개 변수

*pchKey*<br/>
Windows SDK에서 *Pchkey* 의 [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) 을 참조 하세요.

*dw*<br/>
Windows SDK에서 *dw* 를 참조 `IDocHostUIHandler::GetOptionKeyPath` 하세요.

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a> CDHtmlDialog:: HideUI

호스트의 UI를 숨깁니다.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a> CDHtmlDialog:: IsExternalDispatchSafe

호스트의 인터페이스를 스크립팅에 안전 하 게 사용할 수 있는지 여부를 나타냅니다 `IDispatch` .

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>반환 값

FALSE를 반환 합니다.

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a> CDHtmlDialog:: LoadFromResource

DHTML 대화 상자의 WebBrowser 컨트롤에 지정 된 리소스를 로드 합니다.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>매개 변수

*lpszResource*<br/>
로드할 리소스의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*nRes*<br/>
로드할 리소스의 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a> CDHtmlDialog:: m_bUseHtmlTitle

HTML 문서 제목을 대화 상자 캡션으로 사용할지 여부를 나타냅니다.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>설명

**M** _ **busehtmltitle** 이 TRUE 이면 대화 상자 캡션이 HTML 문서의 제목과 동일 하 게 설정 됩니다. 그렇지 않으면 대화 상자 리소스의 캡션이 사용 됩니다.

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a> CDHtmlDialog:: m_nHtmlResID

표시할 HTML 리소스의 리소스 ID입니다.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a> CDHtmlDialog:: m_pBrowserApp

웹 브라우저 응용 프로그램에 대 한 포인터입니다.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a> CDHtmlDialog:: m_spHtmlDoc

HTML 문서에 대 한 포인터입니다.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a> CDHtmlDialog:: m_strCurrentUrl

현재 URL입니다.

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a> CDHtmlDialog:: m_szHtmlResID

HTML 리소스 ID의 문자열 버전입니다.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a> CDHtmlDialog:: Navigate

*LpszURL* 에 지정 된 URL로 식별 되는 리소스로 이동 합니다.

```cpp
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>매개 변수

*lpszURL*<br/>
대상으로 지정할 URL을 포함 하는 문자열에 대 한 포인터입니다.

*dwFlags*<br/>
기록 목록에 리소스를 추가할지 여부를 지정 하는 변수의 플래그, 캐시에 대 한 읽기 또는 캐시에서 쓰기, 새 창에 리소스를 표시할지 여부를 지정 하는 변수의 플래그입니다. 변수는 [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) 열거형에 정의 된 값의 조합일 수 있습니다.

*lpszTargetFrameName*<br/>
리소스를 표시할 프레임의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*lpszHeaders*<br/>
서버에 보낼 HTTP 헤더를 지정 하는 값에 대 한 포인터입니다. 이러한 헤더는 기본 Internet Explorer 헤더에 추가 됩니다. 헤더는 서버에 필요한 작업, 서버로 전달 되는 데이터 형식 또는 상태 코드와 같은 정보를 지정할 수 있습니다. URL이 HTTP URL이 아니면이 매개 변수는 무시 됩니다.

*lpvPostData*<br/>
HTTP POST 트랜잭션과 함께 보낼 데이터에 대 한 포인터입니다. 예를 들어 POST 트랜잭션은 HTML 폼에 의해 수집 된 데이터를 전송 하는 데 사용 됩니다. 이 매개 변수가 post 데이터를 지정 하지 않으면에서 `Navigate` HTTP GET 트랜잭션을 발급 합니다. URL이 HTTP URL이 아니면이 매개 변수는 무시 됩니다.

*dwPostDataLen*<br/>
HTTP POST 트랜잭션과 함께 보낼 데이터입니다. 예를 들어 POST 트랜잭션은 HTML 폼에 의해 수집 된 데이터를 전송 하는 데 사용 됩니다. 이 매개 변수가 post 데이터를 지정 하지 않으면에서 `Navigate` HTTP GET 트랜잭션을 발급 합니다. URL이 HTTP URL이 아니면이 매개 변수는 무시 됩니다.

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a> CDHtmlDialog:: OnBeforeNavigate

탐색이 발생 하기 전에 이벤트를 발생 시키는 프레임 워크에서 호출 됩니다.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
`IDispatch` 개체에 대한 포인터입니다.

*szUrl*<br/>
탐색할 URL을 포함 하는 문자열에 대 한 포인터입니다.

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a> CDHtmlDialog:: OnDocumentComplete

문서에서 READYSTATE_COMPLETE 상태를 달성 했을 때 응용 프로그램에 알리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
`IDispatch` 개체에 대한 포인터입니다.

*szUrl*<br/>
탐색 한 URL을 포함 하는 문자열에 대 한 포인터입니다.

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a> CDHtmlDialog:: OnDocWindowActivate

문서 창이 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>매개 변수

*fActivate*<br/>
Windows SDK에서 *Factivate* in [IDocHostUIHandler:: ondocwindowactivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) in을 참조 하세요.

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a> CDHtmlDialog:: On프레임 창 활성화

프레임 창이 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>매개 변수

*fActivate*<br/>
Windows SDK에서 *Factivate* in [IDocHostUIHandler:: onframewindowactivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) in을 참조 하세요.

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: OnCDHtmlDialog Windowactivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))의 구현입니다.

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a> CDHtmlDialog:: OnInitDialog

WM_INITDIALOG 메시지에 대 한 응답으로 호출 됩니다.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>반환 값

기본 구현에서는 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

이 메시지는 `Create` `CreateIndirect` `DoModal` 대화 상자가 표시 되기 직전에 발생 하는, 또는 호출 중에 대화 상자에 전송 됩니다.

대화 상자가 초기화 될 때 특수 처리를 수행 해야 하는 경우이 멤버 함수를 재정의 합니다. 재정의 된 버전에서 먼저 기본 클래스를 호출 `OnInitDialog` 하지만 해당 반환 값은 무시 합니다. 일반적으로 재정의 된 멤버 함수에서 TRUE를 반환 합니다.

Windows에서는 `OnInitDialog` 메시지 맵을 통해서가 아니라 모든 MFC 라이브러리 대화 상자에 공통 된 표준 전역 대화 상자 프로시저를 통해 함수를 호출 하므로이 멤버 함수에 대 한 메시지 맵 항목은 필요 하지 않습니다.

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a> CDHtmlDialog:: OnNavigateComplete

지정 된 URL에 대 한 탐색이 완료 된 후 프레임 워크에서 호출 됩니다.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
`IDispatch` 개체에 대한 포인터입니다.

*szUrl*<br/>
탐색 한 URL을 포함 하는 문자열에 대 한 포인터입니다.

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a> CDHtmlDialog:: ResizeBorder

테두리 공간 크기를 조정 해야 함을 개체에 경고 합니다.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>매개 변수

*prcBorder*<br/>
Windows SDK에서 *Prcborder* in [IDocHostUIHandler:: ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) 를 참조 하세요.

*pUIWindow*<br/>
Windows SDK에서 *pUIWindow* 을 참조 `IDocHostUIHandler::ResizeBorder` 하세요.

*fFrameWindow*<br/>
Windows SDK의에서 *Ffewindow* 을 참조 하세요 `IDocHostUIHandler::ResizeBorder` .

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a> CDHtmlDialog:: SetControlProperty

ActiveX 컨트롤의 속성을 새 값으로 설정 합니다.

```cpp
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
ActiveX 컨트롤의 HTML ID입니다.

*dispId*<br/>
설정할 속성의 디스패치 ID입니다.

*pVar*<br/>
새 속성 값을 포함 하는 변형에 대 한 포인터입니다.

*pdispControl*<br/>
ActiveX 컨트롤의 인터페이스에 대 한 포인터 `IDispatch` 입니다.

*szPropName*<br/>
설정할 속성의 이름을 포함 하는 문자열입니다.

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a> CDHtmlDialog:: SetElementHtml

`innerHTML`HTML 요소의 속성을 설정 합니다.

```cpp
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

*bstrText*<br/>
`innerHTML` 속성의 새 값입니다.

*punkElem*<br/>
`IUnknown`HTML 요소의 포인터입니다.

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a> CDHtmlDialog:: SetElementProperty

HTML 요소의 속성을 설정 합니다.

```cpp
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

*dispId*<br/>
설정할 속성의 디스패치 ID입니다.

*pVar*<br/>
속성의 새 값입니다.

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a> CDHtmlDialog:: SetElementText

`innerText`HTML 요소의 속성을 설정 합니다.

```cpp
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>매개 변수

*szElementId*<br/>
HTML 요소의 ID입니다.

*bstrText*<br/>
`innerText` 속성의 새 값입니다.

*punkElem*<br/>
`IUnknown`HTML 요소의 포인터입니다.

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a> CDHtmlDialog:: SetExternalDispatch

호스트의 인터페이스를 설정 `IDispatch` 합니다.

```cpp
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>매개 변수

*pdispExternal*<br/>
새 `IDispatch` 인터페이스입니다.

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a> CDHtmlDialog:: SetHostFlags

호스트 UI 플래그를 설정 합니다.

```cpp
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
가능한 값은 Windows SDK에서 [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) 을 참조 하세요.

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a> CDHtmlDialog:: ShowContextMenu

상황에 맞는 메뉴가 표시 되기 전에 호출 됩니다.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>매개 변수

*dwID*<br/>
Windows SDK에서 [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) 의 *ewid* 를 참조 하세요.

*.ppt*<br/>
Windows SDK의 *ppt* 를 참조 `IDocHostUIHandler::ShowContextMenu` 하세요.

*pcmdtReserved*<br/>
Windows SDK의 *Pcmdtreserved* 을 참조 하세요 `IDocHostUIHandler::ShowContextMenu` .

*pdispReserved*<br/>
Windows SDK에서 *pdispReserved* 을 참조 `IDocHostUIHandler::ShowContextMenu` 하세요.

### <a name="return-value"></a>반환 값

S_FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 CDHtmlDialog의 [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))구현입니다.

## <a name="cdhtmldialogshowui"></a><a name="showui"></a> CDHtmlDialog:: ShowUI

호스트의 UI를 표시 합니다.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>매개 변수

*dwID*<br/>
Windows SDK에서 [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) 의 d *wid* 를 참조 하세요.

*pActiveObject*<br/>
Windows SDK의에서 *d pActiveObject* 를 참조 하십시오 `IDocHostUIHandler::ShowUI` .

*pCommandTarget*<br/>
Windows SDK에서 *Pcommandtarget* 을 참조 하십시오 `IDocHostUIHandler::ShowUI` .

*pFrame*<br/>
Windows SDK에서 *Pframe* 을 참조 하십시오 `IDocHostUIHandler::ShowUI` .

*pDoc*<br/>
Windows SDK에서 *Pdoc* in을 참조 `IDocHostUIHandler::ShowUI` 하세요.

### <a name="return-value"></a>반환 값

S_FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a> CDHtmlDialog:: TranslateAccelerator

메뉴 액셀러레이터 키 메시지를 처리 하기 위해 호출 됩니다.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>매개 변수

*lpMsg*<br/>
Windows SDK에서 *Lpmsg* in [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) 을 참조 하세요.

*pguidCmdGroup*<br/>
Windows SDK에서 *pguidCmdGroup* 을 참조 `IDocHostUIHandler::TranslateAccelerator` 하세요.

*nCmdID*<br/>
Windows SDK에서 *Ncmdid* 를 참조 하세요 `IDocHostUIHandler::TranslateAccelerator` .

### <a name="return-value"></a>반환 값

S_FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a> CDHtmlDialog:: TranslateUrl

로드할 URL을 수정 하기 위해 호출 됩니다.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>매개 변수

*dwTranslate*<br/>
Windows SDK에서 *Dwtranslate* in [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) 를 참조 하세요.

*pchURLIn*<br/>
Windows SDK의에서 *Pchurlin* 을 참조 하세요 `IDocHostUIHandler::TranslateUrl` .

*ppchURLOut*<br/>
Windows SDK의 *Ppchurlout* 를 참조 `IDocHostUIHandler::TranslateUrl` 하세요.

### <a name="return-value"></a>반환 값

S_FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))의 CDHtmlDialog 구현입니다.

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a> CDHtmlDialog:: UpdateUI

명령 상태가 변경 되었음을 호스트에 알리기 위해 호출 됩니다.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 CDHtmlDialog의 [IDocHostUIHandler:: UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))구현입니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml 도우미 매크로](#ddx_dhtml_helper_macros)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
