---
description: '자세히 알아보기: COleServerDoc 클래스'
title: COleServerDoc 클래스
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: b96327f2e3e59d4c9941a8e930be70aee3bb58e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226690"
---
# <a name="coleserverdoc-class"></a>COleServerDoc 클래스

OLE 서버 문서의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleServerDoc:: COleServerDoc](#coleserverdoc)|`COleServerDoc` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleServerDoc:: Docobject](#activatedocobject)|연결 된 DocObject 문서를 활성화 합니다.|
|[COleServerDoc:: ActivateInPlace](#activateinplace)|내부 편집을 위해 문서를 활성화 합니다.|
|[COleServerDoc::D eactivateAndUndo](#deactivateandundo)|서버의 사용자 인터페이스를 비활성화 합니다.|
|[COleServerDoc::D iscardUndoState](#discardundostate)|실행 취소 상태 정보를 삭제 합니다.|
|[COleServerDoc:: GetClientSite](#getclientsite)|기본 인터페이스에 대 한 포인터를 검색 `IOleClientSite` 합니다.|
|[COleServerDoc:: GetEmbeddedItem](#getembeddeditem)|전체 문서를 나타내는 항목에 대 한 포인터를 반환 합니다.|
|[COleServerDoc:: GetItemClipRect](#getitemcliprect)|내부 편집을 위해 현재 클리핑 사각형을 반환 합니다.|
|[COleServerDoc:: GetItemPosition](#getitemposition)|내부 편집을 위해 컨테이너 응용 프로그램의 클라이언트 영역을 기준으로 현재 위치 사각형을 반환 합니다.|
|[COleServerDoc:: Get확대/비율](#getzoomfactor)|확대/축소 비율 (픽셀)을 반환 합니다.|
|[COleServerDoc:: IsDocObject](#isdocobject)|문서가 DocObject 인지 여부를 확인 합니다.|
|[COleServerDoc:: IsEmbedded](#isembedded)|문서가 컨테이너 문서에 포함 되어 있는지, 아니면 독립 실행형으로 실행 중인지를 나타냅니다.|
|[COleServerDoc:: IsInPlaceActive](#isinplaceactive)|항목이 현재 활성화 된 경우 TRUE를 반환 합니다.|
|[COleServerDoc:: NotifyChanged](#notifychanged)|사용자가 문서를 변경 했음을 컨테이너에 알립니다.|
|[COleServerDoc:: NotifyClosed](#notifyclosed)|사용자가 문서를 닫 혔 음을 컨테이너에 알립니다.|
|[COleServerDoc:: NotifyRename](#notifyrename)|사용자가 문서의 이름을 변경 했음을 컨테이너에 알립니다.|
|[COleServerDoc:: NotifySaved](#notifysaved)|사용자가 문서를 저장 했음을 컨테이너에 알립니다.|
|[COleServerDoc:: OnDeactivate](#ondeactivate)|사용자가 현재 위치의 활성화 된 항목을 비활성화할 때 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnDeactivateUI](#ondeactivateui)|내부 활성화를 위해 만들어진 컨트롤 및 기타 사용자 인터페이스 요소를 삭제 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnDocWindowActivate](#ondocwindowactivate)|컨테이너의 문서 프레임 창이 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnResizeBorder](#onresizeborder)|컨테이너 응용 프로그램의 프레임 창 또는 문서 창의 크기가 조정 될 때 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnShowControlBars](#onshowcontrolbars)|내부 편집을 위한 컨트롤 막대를 표시 하거나 숨기도록 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnUpdateDocument](#onupdatedocument)|포함 된 항목인 서버 문서를 저장할 때 컨테이너 항목의 복사본을 업데이트 하는 경우 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: RequestPositionChange](#requestpositionchange)|내부 편집 프레임의 위치를 변경 합니다.|
|[COleServerDoc:: SaveEmbedding](#saveembedding)|컨테이너 응용 프로그램에 문서를 저장 하도록 지시 합니다.|
|[COleServerDoc:: ScrollContainerBy](#scrollcontainerby)|컨테이너 문서를 스크롤합니다.|
|[COleServerDoc:: UpdateAllItems](#updateallitems)|사용자가 문서를 변경 했음을 컨테이너에 알립니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[COleServerDoc:: CreateInPlaceFrame](#createinplaceframe)|내부 편집을 위해 프레임 창을 만들기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerDoc::D estroyInPlaceFrame](#destroyinplaceframe)|내부 편집을 위해 프레임 창을 제거 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: GetDocObjectServer](#getdocobjectserver)|새 개체를 만들고 `CDocObjectServer` 이 문서가 DocObject 컨테이너 임을 나타내려면이 함수를 재정의 합니다.|
|[COleServerDoc:: OnClose](#onclose)|컨테이너가 문서를 닫으려고 할 때 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnExecOleCmd](#onexecolecmd)|지정 된 명령을 실행 하거나 명령에 대 한 도움말을 표시 합니다.|
|[COleServerDoc:: On프레임 창 활성화](#onframewindowactivate)|컨테이너의 프레임 창이 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem)|전체 문서를 나타내는를 가져오기 위해 호출 됩니다. `COleServerItem` 포함 된 항목을 가져오는 데 사용 됩니다. 구현이 필요 합니다.|
|[COleServerDoc:: OnReactivateAndUndo](#onreactivateandundo)|내부 편집 중에 수행 된 변경 내용을 취소 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnSetHostNames](#onsethostnames)|컨테이너에서 포함 된 개체의 창 제목을 설정 하는 경우 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnSetItemRects](#onsetitemrects)|컨테이너 응용 프로그램의 창 내에서 내부 편집 프레임 창을 배치 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerDoc:: OnShowDocument](#onshowdocument)|문서를 표시 하거나 숨기도록 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

서버 문서는 포함 되거나 연결 된 항목에 대 한 서버 인터페이스를 나타내는 [COleServerItem](../../mfc/reference/coleserveritem-class.md) 개체를 포함할 수 있습니다. 컨테이너에서 서버 응용 프로그램을 시작 하 여 포함 된 항목을 편집 하는 경우 항목이 자체 서버 문서로 로드 됩니다. 개체는 개체 `COleServerDoc` 를 하나만 포함 `COleServerItem` 하며 전체 문서로 구성 됩니다. 연결 된 항목을 편집 하기 위해 컨테이너에서 서버 응용 프로그램을 시작 하면 기존 문서가 디스크에서 로드 됩니다. 문서 내용의 일부가 강조 표시 되어 연결 된 항목을 표시 합니다.

`COleServerDoc` 개체에는 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 클래스의 항목이 포함 될 수도 있습니다. 이렇게 하면 컨테이너 서버 응용 프로그램을 만들 수 있습니다. 프레임 워크는 개체를 제공 `COleClientItem` 하는 동안 항목을 적절 하 게 저장 하는 함수를 제공 합니다 `COleServerItem` .

서버 응용 프로그램에서 링크를 지원 하지 않는 경우 서버 문서에는 항상 전체 포함 개체를 문서로 나타내는 서버 항목이 하나만 포함 됩니다. 서버 응용 프로그램에서 링크를 지 원하는 경우에는 선택 항목이 클립보드로 복사 될 때마다 서버 항목을 만들어야 합니다.

를 사용 하려면 `COleServerDoc` 클래스에서 클래스를 파생 시키고 서버에서 포함 된 항목을 지원할 수 있도록 하는 [OnGetEmbeddedItem](#ongetembeddeditem) 멤버 함수를 구현 합니다. 에서 클래스를 파생 시켜 `COleServerItem` 문서의 항목을 구현 하 고에서 해당 클래스의 개체를 반환 `OnGetEmbeddedItem` 합니다.

연결 된 항목을 지원 하기 위해에서는 `COleServerDoc` [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) 멤버 함수를 제공 합니다. 기본 구현을 사용 하거나 문서 항목을 관리 하는 고유한 방법이 있는 경우이를 재정의할 수 있습니다.

`COleServerDoc`응용 프로그램에서 지 원하는 각 서버 문서 형식에 대해 하나의 파생 클래스가 필요 합니다. 예를 들어 서버 응용 프로그램이 워크시트와 차트를 지 원하는 경우 두 개의 `COleServerDoc` 파생 클래스가 필요 합니다.

서버에 대 한 자세한 내용은 서버 [: 서버 구현](../../mfc/servers-implementing-a-server.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a> COleServerDoc:: Docobject

연결 된 DocObject 문서를 활성화 합니다.

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>설명

기본적으로는 `COleServerDoc` 액티브 문서 (DocObjects 라고도 함)를 지원 하지 않습니다. 이 지원을 사용 하도록 설정 하려면 [GetDocObjectServer](#getdocobjectserver) And 클래스 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)를 참조 하세요.

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a> COleServerDoc:: ActivateInPlace

내부 편집을 위해 항목을 활성화 합니다.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 그렇지 않으면 0이 고, 항목이 완전히 열려 있음을 나타냅니다.

### <a name="remarks"></a>설명

이 함수는 내부 활성화에 필요한 모든 작업을 수행 합니다. 내부 프레임 창을 만들고 활성화 한 후 항목으로 크기를 조정 하 고, 공유 메뉴와 기타 컨트롤을 설정 하 고, 항목을 뷰로 스크롤하고, 내부 프레임 창으로 포커스를 설정 합니다.

이 함수는 [COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onshow)의 기본 구현에 의해 호출 됩니다. 응용 프로그램이 내부 활성화에 대해 다른 동사 (예: Play)를 지 원하는 경우이 함수를 호출 합니다.

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a> COleServerDoc:: COleServerDoc

`COleServerDoc`OLE 시스템 dll과 연결 하지 않고 개체를 생성 합니다.

```
COleServerDoc();
```

### <a name="remarks"></a>설명

OLE와의 통신을 열려면 [COleLinkingDoc:: Register](../../mfc/reference/colelinkingdoc-class.md#register) 를 호출 해야 합니다. 응용 프로그램에서 [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) 를 사용 하는 경우, `COleLinkingDoc::Register` `COleLinkingDoc` 및의 구현을 통해가 호출 됩니다 `OnNewDocument` `OnOpenDocument` `OnSaveDocument` .

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a> COleServerDoc:: CreateInPlaceFrame

프레임 워크는이 함수를 호출 하 여 내부 편집을 위해 프레임 창을 만듭니다.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
컨테이너 응용 프로그램의 부모 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

내부 프레임 창에 대 한 포인터 이거나, 실패 한 경우 NULL입니다.

### <a name="remarks"></a>설명

기본 구현에서는 문서 템플릿에 지정 된 정보를 사용 하 여 프레임을 만듭니다. 사용 되는 보기는 문서에 대해 만들어진 첫 번째 뷰입니다. 이 보기는 일시적으로 원래 프레임에서 분리 되어 새로 만든 프레임에 연결 됩니다.

이는 고급 재정의 가능입니다.

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a> COleServerDoc::D eactivateAndUndo

응용 프로그램에서 실행 취소를 지원 하 고 사용자가 항목을 활성화 한 후 편집 하기 전에 실행 취소를 선택 하는 경우이 함수를 호출 합니다.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아닌 값이고, 실패하면 0입니다.

### <a name="remarks"></a>설명

MFC 라이브러리를 사용 하 여 컨테이너 응용 프로그램을 작성 하는 경우이 함수를 호출 하면 서버 사용자 인터페이스를 비활성화 하는 [COleClientItem:: OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) 가 호출 됩니다.

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a> COleServerDoc::D estroyInPlaceFrame

프레임 워크는이 함수를 호출 하 여 내부 프레임 창을 소멸 하 고 내부 활성화 전의 상태로 서버 응용 프로그램의 문서 창을 반환 합니다.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>매개 변수

*pFrameWnd*<br/>
제거할 내부 프레임 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이는 고급 재정의 가능입니다.

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a> COleServerDoc::D iscardUndoState

사용자가 취소할 수 없는 편집 작업을 수행 하는 경우이 함수를 호출 하 여 컨테이너 응용 프로그램이 실행 취소 상태 정보를 강제로 삭제 하도록 합니다.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아닌 값이고, 실패하면 0입니다.

### <a name="remarks"></a>설명

실행 취소를 지 원하는 서버에서 사용할 수 없는 실행 취소 상태 정보에 사용 되는 리소스를 해제할 수 있도록이 함수가 제공 됩니다.

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a> COleServerDoc:: GetClientSite

기본 인터페이스에 대 한 포인터를 검색 `IOleClientSite` 합니다.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>반환 값

기본 [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) 인터페이스에 대 한 포인터를 검색 합니다.

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a> COleServerDoc:: GetDocObjectServer

새 항목을 만들고이 항목에 대 한 포인터를 반환 하려면이 함수를 재정의 `CDocObjectServer` 합니다.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>매개 변수

*pDocSite*<br/>
`IOleDocumentSite`이 문서를 서버에 연결 하는 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

에 대 한 포인터 `CDocObjectServer` 입니다. 작업이 실패 한 경우 NULL입니다.

### <a name="remarks"></a>설명

DocObject 서버가 활성화 되 면 NULL이 아닌 포인터를 반환 하면 클라이언트가 DocObjects를 지원할 수 있음을 보여 줍니다. 기본 구현에서는 NULL을 반환 합니다.

DocObjects를 지 원하는 문서에 대 한 일반적인 구현은 단순히 새 개체를 할당 `CDocObjectServer` 하 고 호출자에 게 반환 합니다. 예를 들어:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a> COleServerDoc:: GetEmbeddedItem

전체 문서를 나타내는 항목에 대 한 포인터를 가져오려면이 함수를 호출 합니다.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>반환 값

전체 문서를 나타내는 항목에 대 한 포인터입니다. 작업이 실패 한 경우 NULL입니다.

### <a name="remarks"></a>설명

기본 구현을 사용 하지 않는 가상 함수인 [COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem)를 호출 합니다.

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a> COleServerDoc:: GetItemClipRect

`GetItemClipRect`멤버 함수를 호출 하 여 현재 편집 중인 항목의 클리핑 사각형 좌표를 가져옵니다.

```cpp
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>매개 변수

*lpClipRect*<br/>
`RECT` `CRect` 항목의 클리핑 사각형 좌표를 받는 구조체 또는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

좌표는 컨테이너 응용 프로그램 창의 클라이언트 영역을 기준으로 하는 픽셀 단위입니다.

그리기는 클리핑 사각형 외부에서 발생 하면 안 됩니다. 일반적으로 그리기는 자동으로 제한 됩니다. 이 함수를 사용 하 여 사용자가 문서에서 표시 되는 부분을 벗어나 스크롤 되었는지 여부를 확인 합니다. 그렇다면 [ScrollContainerBy](#scrollcontainerby)에 대 한 호출을 통해 필요에 따라 컨테이너 문서를 스크롤합니다.

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a> COleServerDoc:: GetItemPosition

`GetItemPosition`멤버 함수를 호출 하 여 현재 편집 중인 항목의 좌표를 가져옵니다.

```cpp
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>매개 변수

*lpPosRect*<br/>
`RECT`항목의 좌표를 받는 구조체 또는 개체에 대 한 포인터 `CRect` 입니다.

### <a name="remarks"></a>설명

좌표는 컨테이너 응용 프로그램 창의 클라이언트 영역을 기준으로 하는 픽셀 단위입니다.

항목의 위치를 현재 클리핑 사각형과 비교 하 여 화면에 항목이 표시 되거나 표시 되지 않는 범위를 결정할 수 있습니다.

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a> COleServerDoc:: Get확대/비율

`GetZoomFactor`멤버 함수는 내부 편집을 위해 활성화 된 항목의 "확대/축소 비율"을 결정 합니다.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>매개 변수

*lpSizeNum*<br/>
`CSize`확대/축소 비율의 분자를 포함 하는 클래스의 개체에 대 한 포인터입니다. NULL일 수 있습니다.

*lpSizeDenom*<br/>
`CSize`확대/축소 비율의 분모를 보유할 클래스의 개체에 대 한 포인터입니다. NULL일 수 있습니다.

*lpPosRect*<br/>
`CRect`항목의 새 위치를 설명 하는 클래스의 개체에 대 한 포인터입니다. 이 인수가 NULL 이면 함수는 항목의 현재 위치를 사용 합니다.

### <a name="return-value"></a>반환 값

항목이 내부 편집을 위해 활성화 되 고 확대/축소 비율이 100% (1:1)가 아닌 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

확대/축소 비율 (픽셀)은 항목 크기의 현재 범위에 대 한 비율입니다. 컨테이너 응용 프로그램에서 항목의 범위를 설정 하지 않은 경우 해당 자연 범위 ( [COleServerItem:: OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)에 의해 결정 됨)가 사용 됩니다.

함수는 처음 두 인수를 항목의 "확대/축소 비율"의 분자와 분모로 설정 합니다. 항목을 편집 하지 않는 경우 함수는 이러한 인수를 기본값 100% (또는 1:1)로 설정 하 고 0을 반환 합니다. 자세한 내용은 Technical Note 40, [MFC/OLE In-Place 크기 조정 및 확대/축소](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)를 참조 하세요.

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a> COleServerDoc:: IsDocObject

문서가 DocObject 인지 여부를 확인 합니다.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>반환 값

문서가 DocObject 이면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a> COleServerDoc:: IsEmbedded

`IsEmbedded`멤버 함수를 호출 하 여 문서가 컨테이너에 포함 된 개체를 나타내는지 여부를 확인 합니다.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>반환 값

`COleServerDoc`개체가 컨테이너에 포함 된 개체를 나타내는 문서 이면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

파일에서 로드 된 문서는 컨테이너 응용 프로그램에 의해 링크로 조작 될 수 있지만 포함 되지 않습니다. 컨테이너 문서에 포함 된 문서는 포함 된 것으로 간주 됩니다.

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a> COleServerDoc:: IsInPlaceActive

`IsInPlaceActive`멤버 함수를 호출 하 여 항목이 현재 내부 활성 상태 인지 여부를 확인 합니다.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>반환 값

`COleServerDoc`개체가 현재 활성화 되어 있으면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a> COleServerDoc:: NotifyChanged

문서가 변경 된 문서에 연결 된 모든 항목을 알리려면이 함수를 호출 합니다.

```cpp
void NotifyChanged();
```

### <a name="remarks"></a>설명

일반적으로 사용자가 서버 문서의 크기와 같은 일부 전역 특성을 변경한 후이 함수를 호출 합니다. OLE 항목이 자동 링크를 사용 하 여 문서에 연결 된 경우 해당 항목은 변경 내용을 반영 하도록 업데이트 됩니다. MFC 라이브러리로 작성 된 컨테이너 응용 프로그램에서의 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 멤버 함수가 `COleClientItem` 호출 됩니다.

> [!NOTE]
> 이 함수는 OLE 1과의 호환성을 위해 포함 되었습니다. 새 응용 프로그램은 [UpdateAllItems](#updateallitems)를 사용 해야 합니다.

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a> COleServerDoc:: NotifyClosed

문서가 닫 혔 음을 컨테이너에 알리려면이 함수를 호출 합니다.

```cpp
void NotifyClosed();
```

### <a name="remarks"></a>설명

사용자가 파일 메뉴에서 닫기 명령을 선택 하면 `NotifyClosed` 가 `COleServerDoc` [onclosedocument](../../mfc/reference/cdocument-class.md#onclosedocument) 멤버 함수 구현에 의해 호출 됩니다. MFC 라이브러리로 작성 된 컨테이너 응용 프로그램에서의 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 멤버 함수가 `COleClientItem` 호출 됩니다.

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a> COleServerDoc:: NotifyRename

사용자가 서버 문서의 이름을 바꾼 후이 함수를 호출 합니다.

```cpp
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>매개 변수

*lpszNewName*<br/>
서버 문서의 새 이름을 지정 하는 문자열에 대 한 포인터입니다. 일반적으로 정규화 된 경로입니다.

### <a name="remarks"></a>설명

사용자가 파일 메뉴에서 다른 이름으로 저장 명령을 선택 하면 `NotifyRename` 는 `COleServerDoc` [onsavedocument](../../mfc/reference/cdocument-class.md#onsavedocument) 멤버 함수 구현에 의해 호출 됩니다. 이 함수는 OLE 시스템 Dll에이를 알리고 컨테이너에이를 알립니다. MFC 라이브러리로 작성 된 컨테이너 응용 프로그램에서의 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 멤버 함수가 `COleClientItem` 호출 됩니다.

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a> COleServerDoc:: NotifySaved

사용자가 서버 문서를 저장 한 후이 함수를 호출 합니다.

```cpp
void NotifySaved();
```

### <a name="remarks"></a>설명

사용자가 파일 메뉴에서 저장 명령을 선택 하면 `NotifySaved` `COleServerDoc` 의 [onsavedocument](../../mfc/reference/cdocument-class.md#onsavedocument)구현에 따라가 호출 됩니다. 이 함수는 OLE 시스템 Dll에이를 알리고 컨테이너에이를 알립니다. MFC 라이브러리로 작성 된 컨테이너 응용 프로그램에서의 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 멤버 함수가 `COleClientItem` 호출 됩니다.

## <a name="coleserverdoconclose"></a><a name="onclose"></a> COleServerDoc:: OnClose

컨테이너에서 서버 문서를 닫도록 요청할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>매개 변수

*dwCloseOption*<br/>
OLECLOSE 열거형의 값입니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- 파일이 수정 된 경우 저장 되 OLECLOSE_SAVEIFDIRTY 합니다.

- 파일이 저장 되지 않고 닫혀 OLECLOSE_NOSAVE 합니다.

- OLECLOSE_PROMPTSAVE 파일을 수정한 경우 사용자에 게 파일을 저장 하 라는 메시지가 표시 됩니다.

### <a name="remarks"></a>설명

기본 구현에서는를 호출 `CDocument::OnCloseDocument` 합니다.

자세한 내용 및 추가 값은 Windows SDK에서 [Oleclose](/windows/win32/api/oleidl/ne-oleidl-oleclose) 을 참조 하세요.

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a> COleServerDoc:: OnDeactivate

사용자가 현재 내부 활성 상태인 연결 된 항목 또는 연결 된 항목을 비활성화할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>설명

이 함수는 컨테이너 응용 프로그램의 사용자 인터페이스를 원래 상태로 복원 하 고 내부 활성화에 대해 만들어진 모든 메뉴 및 기타 컨트롤을 소멸 시킵니다.

실행 취소 상태 정보는이 시점에서 무조건 해제 해야 합니다.

자세한 내용은 [활성화](../../mfc/activation-cpp.md)문서를 참조 하세요.

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a> COleServerDoc:: OnDeactivateUI

현재 위치의 활성화 된 항목을 사용자가 비활성화 하면 호출 됩니다.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>매개 변수

*bUndoable*<br/>
편집 변경 내용을 취소할 수 있는지 여부를 지정 합니다.

### <a name="remarks"></a>설명

이 함수는 컨테이너 응용 프로그램의 사용자 인터페이스를 원래 상태로 복원 하 고 내부 활성화를 위해 만들어진 모든 메뉴 및 기타 컨트롤을 숨깁니다.

프레임 워크는 항상 *bUndoable* 을 FALSE로 설정 합니다. 서버에서 실행 취소를 지원 하 고 작업을 실행 취소할 수 있는 경우 *bUndoable* 를 TRUE로 설정 하 여 기본 클래스 구현을 호출 합니다.

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a> COleServerDoc:: OnDocWindowActivate

프레임 워크는이 함수를 호출 하 여 내부 편집을 위해 문서 창을 활성화 하거나 비활성화 합니다.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>매개 변수

*bActivate*<br/>
문서 창을 활성화 또는 비활성화 할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

기본 구현에서는 프레임 수준 사용자 인터페이스 요소를 적절 하 게 제거 하거나 추가 합니다. 항목을 포함 하는 문서가 활성화 또는 비활성화 될 때 추가 작업을 수행 하려면이 함수를 재정의 합니다.

자세한 내용은 [활성화](../../mfc/activation-cpp.md)문서를 참조 하세요.

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a> COleServerDoc:: OnExecOleCmd

프레임 워크는이 함수를 호출 하 여 지정 된 명령을 실행 하거나 명령에 대 한 도움말을 표시 합니다.

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>매개 변수

*pguidCmdGroup*<br/>
명령 집합을 식별 하는 GUID에 대 한 포인터입니다. 기본 명령 그룹을 나타내는 NULL 일 수 있습니다.

*nCmdID*<br/>
실행할 명령입니다. *PguidCmdGroup* 로 식별 되는 그룹에 있어야 합니다.

*nCmdExecOut*<br/>
개체에서 명령을 실행 해야 하는 방법입니다. OLECMDEXECOPT 열거형의 다음 값 중 하나 이상이 있습니다.

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
명령에 대 한 입력 인수가 포함 된 VARIANTARG에 대 한 포인터입니다. NULL일 수 있습니다.

*pvarargOut*<br/>
명령에서 출력 반환 값을 받는 VARIANTARG에 대 한 포인터입니다. NULL일 수 있습니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 반환 합니다. 그렇지 않으면 다음 오류 코드 중 하나입니다.

|값|설명|
|-----------|-----------------|
|E_UNEXPECTED|예기치 않은 오류가 발생 했습니다.|
|E_FAIL|오류가 발생했습니다.|
|E_NOTIMPL|MFC 자체가 명령을 변환 하 고 디스패치하기를 시도할지를 나타냅니다.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* 가 NULL이 아니고 인식 된 명령 그룹을 지정 하지 않습니다.|
|OLECMDERR_E_NOTSUPPORTED|*Ncmdid* 가 *pguidCmdGroup* 그룹의 올바른 명령으로 인식 되지 않습니다.|
|OLECMDERR_DISABLED|*Ncmdid* 로 식별 된 명령이 비활성화 되어 실행할 수 없습니다.|
|OLECMDERR_NOHELP|호출자가 *Ncmdid* 로 식별 된 명령에 대 한 도움말을 요청 했지만 사용할 수 있는 도움말이 없습니다.|
|OLECMDERR_CANCELED|사용자가 실행을 취소 했습니다.|

### <a name="remarks"></a>설명

`COleCmdUI` 를 사용 하 여 DocObject 사용자 인터페이스 명령의 다른 속성을 설정, 업데이트 및 설정할 수 있습니다. 명령을 초기화 한 후에는를 사용 하 여 명령을 실행할 수 있습니다 `OnExecOleCmd` .

프레임 워크는 OLE 문서 명령을 변환 하 고 디스패치하기 전에 함수를 호출 합니다. 표준 OLE 문서 명령을 처리 하기 위해이 함수를 재정의할 필요는 없지만 고유한 사용자 지정 명령을 처리 하거나 매개 변수를 허용 하거나 결과를 반환 하는 명령을 처리 하려는 경우에는이 함수에 대 한 재정의를 제공 해야 합니다.

대부분의 명령은 인수 또는 반환 값을 사용 하지 않습니다. 대부분의 명령은 호출자가 *Pvarargin* 및 *Pvarargin* 에 대 한 null을 전달할 수 있습니다. 입력 값을 필요로 하는 명령의 경우 호출자는 VARIANTARG 변수를 선언 하 고 초기화 하 고 *의 Pvarargin* 변수에 포인터를 전달할 수 있습니다. 단일 값이 필요한 명령의 경우 인수를 VARIANTARG에 직접 저장 하 고 함수에 전달할 수 있습니다. 지원 되는 형식 (예: 및 SAFEARRAY) 중 하나를 사용 하 여 VARIANTARG 내에서 여러 인수를 패키지 해야 합니다 `IDispatch` .

마찬가지로, 명령에서 인수를 반환 하는 경우 호출자는 VARIANTARG을 선언 하 고, VT_EMPTY로 초기화 하 고, *Pvarargout* 에서 해당 주소를 전달 합니다. 명령에서 단일 값을 반환 하는 경우 개체는 해당 값을 *Pvarargout* 에 직접 저장할 수 있습니다. 여러 출력 값은 VARIANTARG에 적절 한 방식으로 패키지 되어야 합니다.

이 함수의 기본 클래스 구현에서는 명령 대상과 연결 된 OLE_COMMAND_MAP 구조를 탐색 하 고 적절 한 처리기에 명령을 디스패치합니다. 기본 클래스 구현은 인수나 반환 값을 허용 하지 않는 명령 에서만 작동 합니다. 인수 또는 반환 값을 허용 하는 명령을 처리 해야 하는 경우이 함수를 재정의 하 고 *Pvarargin* 및 *Pvarargin* 매개 변수를 직접 사용 해야 합니다.

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a> COleServerDoc:: On프레임 창 활성화

프레임 워크는 컨테이너 응용 프로그램의 프레임 창이 활성화 또는 비활성화 될 때이 함수를 호출 합니다.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>매개 변수

*bActivate*<br/>
프레임 창을 활성화 또는 비활성화 할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

기본 구현에서는 프레임 창이 있을 수 있는 모든 도움말 모드를 취소 합니다. 프레임 창이 활성화 또는 비활성화 될 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다.

자세한 내용은 [활성화](../../mfc/activation-cpp.md)문서를 참조 하세요.

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a> COleServerDoc:: OnGetEmbeddedItem

컨테이너 응용 프로그램이 서버 응용 프로그램을 호출 하 여 포함 된 항목을 만들거나 편집할 때 프레임 워크에서 호출 됩니다.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>반환 값

전체 문서를 나타내는 항목에 대 한 포인터입니다. 작업이 실패 한 경우 NULL입니다.

### <a name="remarks"></a>설명

기본 구현은 없습니다. 전체 문서를 나타내는 항목을 반환 하려면이 함수를 재정의 해야 합니다. 이 반환 값은 파생 클래스의 개체 여야 합니다 `COleServerItem` .

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a> COleServerDoc:: OnReactivateAndUndo

사용자가 내부에서 활성화 되 고, 변경 되 고, 이후에 비활성화 된 항목에 대 한 변경 내용을 취소 하도록 선택 하면 프레임 워크에서이 함수를 호출 합니다.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 구현은 실패를 나타내기 위해 FALSE를 반환 한다는 점을 제외 하 고는 아무것도 수행 하지 않습니다.

응용 프로그램에서 실행 취소를 지 원하는 경우이 함수를 재정의 합니다. 일반적으로 실행 취소 작업을 수행한 다음를 호출 하 여 항목을 활성화 `ActivateInPlace` 합니다. MFC 라이브러리를 사용 하 여 컨테이너 응용 프로그램을 작성 하는 경우를 호출 하면 `COleClientItem::ReactivateAndUndo` 이 함수가 호출 됩니다.

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a> COleServerDoc:: OnResizeBorder

프레임 워크는 컨테이너 응용 프로그램의 프레임 창 크기가 변경 될 때이 함수를 호출 합니다.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>매개 변수

*lpRectBorder*<br/>
`RECT` `CRect` 테두리의 좌표를 지정 하는 개체 또는 구조체에 대 한 포인터입니다.

*lpUIWindow*<br/>
`IOleInPlaceUIWindow`현재 내부 편집 세션을 소유 하는 클래스의 개체에 대 한 포인터입니다.

*bFrame*<br/>
*LpUIWindow* 가 컨테이너 응용 프로그램의 최상위 프레임 창을 가리키거나 *lpUIWindow* 가 컨테이너 응용 프로그램의 문서 수준 프레임 창을 가리키는 경우 TRUE입니다.

### <a name="remarks"></a>설명

이 함수는 새 창 크기에 따라 도구 모음 및 기타 사용자 인터페이스 요소 크기를 조정 하 고 조정 합니다.

자세한 내용은 Windows SDK에서 [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) 을 참조 하세요.

이는 고급 재정의 가능입니다.

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a> COleServerDoc:: OnSetHostNames

컨테이너가이 문서에 대 한 호스트 이름을 설정 하거나 변경할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>매개 변수

*lpszHost*<br/>
컨테이너 응용 프로그램의 이름을 지정 하는 문자열에 대 한 포인터입니다.

*lpszHostObj*<br/>
문서의 컨테이너 이름을 지정 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 구현에서는이 문서를 참조 하는 모든 보기의 문서 제목을 변경 합니다.

응용 프로그램에서 다른 메커니즘을 통해 제목을 설정 하는 경우이 함수를 재정의 합니다.

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a> COleServerDoc:: OnSetItemRects

프레임 워크는이 함수를 호출 하 여 내부 편집 프레임 창을 컨테이너 응용 프로그램의 프레임 창에 배치 합니다.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>매개 변수

*lpPosRect*<br/>
`RECT` `CRect` 컨테이너 응용 프로그램의 클라이언트 영역을 기준으로 내부 프레임 창의 위치를 지정 하는 구조체 또는 개체에 대 한 포인터입니다.

*lpClipRect*<br/>
`RECT` `CRect` 컨테이너 응용 프로그램의 클라이언트 영역을 기준으로 내부 프레임 창의 클리핑 사각형을 지정 하는 구조체 또는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

필요한 경우이 함수를 재정의 하 여 뷰의 확대/축소 비율을 업데이트 합니다.

이 함수는 일반적으로 호출에 대 한 응답으로 호출 됩니다 .이 함수는 `RequestPositionChange` 컨테이너에서 내부 항목의 위치 변경을 요청 하기 위해 언제 든 지 호출할 수 있습니다.

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a> COleServerDoc:: OnShowControlBars

프레임 워크는이 함수를 호출 하 여 *pFrameWnd* 으로 식별 되는 프레임 창과 연결 된 서버 응용 프로그램의 컨트롤 막대를 표시 하거나 숨깁니다.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*pFrameWnd*<br/>
컨트롤 막대를 숨기 거 나 표시 해야 하는 프레임 창에 대 한 포인터입니다.

*bShow*<br/>
컨트롤 막대를 표시할지 또는 숨길지를 결정 합니다.

### <a name="remarks"></a>설명

기본 구현에서는 해당 프레임 창이 소유 하 고 있는 모든 컨트롤 막대를 열거 하 고 숨기 거 나 표시 합니다.

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a> COleServerDoc:: OnShowDocument

`OnShowDocument`서버 문서를 숨기 거 나 표시 해야 하는 경우 프레임 워크는 함수를 호출 합니다.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
문서에 대 한 사용자 인터페이스를 표시 하거나 숨길지 여부를 지정 합니다.

### <a name="remarks"></a>설명

*Bshow* 가 TRUE 이면 필요에 따라 기본 구현에서 서버 응용 프로그램을 활성화 하 고 컨테이너 응용 프로그램이 해당 창을 스크롤하여 항목이 표시 되도록 합니다. *Bshow* 가 FALSE 인 경우 기본 구현에서는를 호출 하 여 항목을 비활성화 `OnDeactivate` 한 다음 첫 번째 문서를 제외 하 고 문서에 대해 만들어진 모든 프레임 창을 소멸 하거나 숨깁니다. 표시 되는 문서가 남아 있지 않으면 기본 구현에서 서버 응용 프로그램을 숨깁니다.

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a> COleServerDoc:: OnUpdateDocument

복합 문서에 포함 된 항목인 문서를 저장할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>반환 값

문서가 성공적으로 업데이트 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 구현에서는 [COleServerDoc:: NotifySaved](#notifysaved) 및 [COleServerDoc:: saveembedding](#saveembedding) 멤버 함수를 호출한 다음 문서를 clean으로 표시 합니다. 포함 된 항목을 업데이트할 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다.

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a> COleServerDoc:: RequestPositionChange

컨테이너 응용 프로그램이 항목의 위치를 변경 하도록 하려면이 멤버 함수를 호출 합니다.

```cpp
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>매개 변수

*lpPosRect*<br/>
`RECT`항목의 새 위치를 포함 하는 구조체 또는 개체에 대 한 포인터 `CRect` 입니다.

### <a name="remarks"></a>설명

이 함수는 `UpdateAllItems` 내부 활성 항목의 데이터가 변경 된 경우 일반적으로와 함께 호출 됩니다. 이 호출을 수행 하면 컨테이너는를 호출 하 여 변경을 수행할 수도 있고 그렇지 않을 수도 있습니다 `OnSetItemRects` . 결과 위치가 요청한 것과 다를 수 있습니다.

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a> COleServerDoc:: SaveEmbedding

컨테이너 응용 프로그램에 포함 된 개체를 저장 하도록 지시 하려면이 함수를 호출 합니다.

```cpp
void SaveEmbedding();
```

### <a name="remarks"></a>설명

이 함수는에서 자동으로 호출 됩니다 `OnUpdateDocument` . 이 함수를 사용 하면 항목이 디스크에서 업데이트 되므로 일반적으로 특정 사용자 작업의 결과로만 호출 됩니다.

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a> COleServerDoc:: ScrollContainerBy

`ScrollContainerBy`멤버 함수를 호출 하 여 컨테이너 문서를로 표시 되는 크기 (픽셀) 만큼 스크롤합니다 `sizeScroll` .

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>매개 변수

*sizeScroll*<br/>
컨테이너 문서를 스크롤 하는 정도를 나타냅니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

양수 값은 아래로 스크롤하고 오른쪽으로 스크롤 하는 것을 의미 합니다. 음수 값은 위쪽 및 왼쪽으로 스크롤 하는 것을 의미 합니다.

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a> COleServerDoc:: UpdateAllItems

문서가 변경 된 문서에 연결 된 모든 항목을 알리려면이 함수를 호출 합니다.

```cpp
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>매개 변수

*pSender*<br/>
문서를 수정한 항목에 대 한 포인터 이거나 모든 항목을 업데이트할 경우 NULL입니다.

*lHint*<br/>
수정에 대 한 정보를 포함 합니다.

*pHint*<br/>
수정에 대 한 정보를 저장 하는 개체에 대 한 포인터입니다.

*nDrawAspect*<br/>
항목을 그리는 방법을 결정 합니다. 이 값은 DVASPECT 열거형의 값입니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- DVASPECT_CONTENT 항목은 해당 컨테이너 내에 포함 된 개체로 표시 될 수 있는 방식으로 표시 됩니다.

- DVASPECT_THUMBNAIL 항목은 검색 도구에 표시 될 수 있도록 "축소판 그림" 표현으로 렌더링 됩니다.

- DVASPECT_ICON 항목은 아이콘으로 표시 됩니다.

- DVASPECT_DOCPRINT 항목은 파일 메뉴의 인쇄 명령을 사용 하 여 인쇄 된 것 처럼 표시 됩니다.

### <a name="remarks"></a>설명

일반적으로 사용자가 서버 문서를 변경한 후이 함수를 호출 합니다. OLE 항목이 자동 링크를 사용 하 여 문서에 연결 된 경우 해당 항목은 변경 내용을 반영 하도록 업데이트 됩니다. MFC 라이브러리로 작성 된 컨테이너 응용 프로그램에서의 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 멤버 함수가 `COleClientItem` 호출 됩니다.

이 함수는 `OnUpdate` 송신 항목을 제외한 각 문서 항목에 대해 구성원 함수를 호출 하 여 *phint*, *Lhint* 및 *ndrawaspect* 를 전달 합니다. 이러한 매개 변수를 사용 하 여 문서에 대 한 수정 내용에 대 한 정보를 항목에 전달 합니다. *Lhint* 를 사용 하 여 정보를 인코딩하거나, `CObject` 파생 클래스를 정의 하 여 수정에 대 한 정보를 저장 하 고 *phint* 를 사용 하 여 해당 클래스의 개체를 전달할 수 있습니다. `OnUpdate`파생 클래스의 멤버 함수를 재정의 `COleServerItem` 하 여 프레젠테이션이 변경 되었는지 여부에 따라 각 항목의 업데이트를 최적화 합니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc 클래스](../../mfc/reference/colelinkingdoc-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 클래스](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc 클래스](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer 클래스](../../mfc/reference/coletemplateserver-class.md)
