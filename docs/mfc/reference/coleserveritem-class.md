---
description: '자세히 알아보기: COleServerItem 클래스'
title: COleServerItem 클래스
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: 30f99e6ee62406b47a493781586d8ed8b11a60b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226651"
---
# <a name="coleserveritem-class"></a>COleServerItem 클래스

OLE 항목에 대한 서버 인터페이스를 제공합니다.

## <a name="syntax"></a>구문

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|`COleServerItem` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|개체에 프레젠테이션 및 변환 형식을 배치 `COleDataSource` 합니다.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|항목을 클립보드에 복사 합니다.|
|[COleServerItem::DoDragDrop](#dodragdrop)|끌어서 놓기 작업을 수행 합니다.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|데이터 전송 (끌어서 놓기 또는 클립보드)에 사용할 데이터 원본을 가져옵니다.|
|[COleServerItem::GetDocument](#getdocument)|항목을 포함 하는 서버 문서를 반환 합니다.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|OLE 항목에 대 한 CF_EMBEDSOURCE 데이터를 가져옵니다.|
|[COleServerItem::GetItemName](#getitemname)|항목의 이름을 반환 합니다. 연결 된 항목에만 사용 됩니다.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|OLE 항목에 대 한 CF_LINKSOURCE 데이터를 가져옵니다.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|OLE 항목에 대 한 CF_OBJECTDESCRIPTOR 데이터를 가져옵니다.|
|[COleServerItem::IsConnected](#isconnected)|항목이 현재 활성 컨테이너에 연결 되어 있는지 여부를 나타냅니다.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|항목이 링크 된 OLE 항목을 나타내는지 여부를 나타냅니다.|
|[COleServerItem::NotifyChanged](#notifychanged)|자동 링크 업데이트를 사용 하 여 모든 컨테이너를 업데이트 합니다.|
|[COleServerItem::OnDoVerb](#ondoverb)|동사를 실행 하기 위해 호출 됩니다.|
|[COleServerItem::OnDraw](#ondraw)|컨테이너가 항목을 그리도록 요청할 때 호출 됩니다. 구현이 필요 합니다.|
|[COleServerItem::OnDrawEx](#ondrawex)|특수 항목 그리기를 위해 호출 됩니다.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|클립보드로 복사 되는 데이터를 가져오기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerItem::OnGetExtent](#ongetextent)|OLE 항목의 크기를 검색 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerItem:: OnInitFromData](#oninitfromdata)|지정 된 데이터 전송 개체의 내용을 사용 하 여 OLE 항목을 초기화 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|업데이트 해야 하는 연결 된 항목이 있는지 여부를 확인 하기 위해 호출 됩니다.|
|[COleServerItem::OnRenderData](#onrenderdata)|지연 된 렌더링의 일부로 데이터를 검색 합니다.|
|[COleServerItem:: OnRenderFileData](#onrenderfiledata)|`CFile`지연 된 렌더링의 일부로 데이터를 개체로 검색 합니다.|
|[COleServerItem:: OnRenderGlobalData](#onrenderglobaldata)|지연 된 렌더링의 일부로 HGLOBAL 데이터를 검색 합니다.|
|[COleServerItem:: OnSetColorScheme](#onsetcolorscheme)|항목의 색 구성표를 설정 하기 위해 호출 됩니다.|
|[COleServerItem:: OnSetData](#onsetdata)|항목의 데이터를 설정 하기 위해 호출 됩니다.|
|[COleServerItem::OnSetExtent](#onsetextent)|OLE 항목의 크기를 설정 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerItem::OnUpdate](#onupdate)|항목이 속한 문서의 일부가 변경 될 때 호출 됩니다.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|서버 문서에 있는 모든 항목의 프레젠테이션 캐시를 업데이트 하기 위해 호출 됩니다.|
|[COleServerItem:: SetItemName](#setitemname)|항목의 이름을 설정 합니다. 연결 된 항목에만 사용 됩니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|변환 형식을 저장 하는 데 사용 되는 개체를 가져옵니다.|
|[COleServerItem:: OnHide](#onhide)|OLE 항목을 숨기기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerItem::OnOpen](#onopen)|OLE 항목을 자체의 최상위 창에 표시 하기 위해 프레임 워크에서 호출 됩니다.|
|[COleServerItem:: OnShow](#onshow)|컨테이너가 항목을 표시 하도록 요청할 때 호출 됩니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|표시 되는 OLE 항목의 양에 대해 서버에 알립니다.|

## <a name="remarks"></a>설명

연결 된 항목은 서버 문서의 일부 또는 전체를 나타낼 수 있습니다. 포함 된 항목은 항상 전체 서버 문서를 나타냅니다.

`COleServerItem`이 클래스는 일반적으로 컨테이너 응용 프로그램의 요청에 대 한 응답으로 OLE 시스템 dll (동적 연결 라이브러리)에 의해 호출 되는 여러 개의 재정의 가능한 멤버 함수를 정의 합니다. 이러한 멤버 함수를 사용 하면 컨테이너 응용 프로그램에서 항목을 표시 하거나, 동사를 실행 하거나, 다양 한 형식으로 데이터를 검색 하는 등의 다양 한 방법으로 간접적으로 항목을 조작할 수 있습니다.

를 사용 하려면 `COleServerItem` 클래스에서 클래스를 파생 시키고 [OnDraw](#ondraw) 및 [Serialize](../../mfc/reference/cobject-class.md#serialize) 멤버 함수를 구현 합니다. `OnDraw`함수는 컨테이너 응용 프로그램이 복합 문서를 열 때 표시 될 수 있도록 항목의 메타 파일 표현을 제공 합니다. `Serialize`의 함수는 `CObject` 항목의 기본 표현을 제공 하 여 포함 된 항목이 서버와 컨테이너 응용 프로그램 간에 전송 될 수 있도록 합니다. [Ongetextent](#ongetextent) 컨테이너에 항목의 기본 크기를 제공 하 여 컨테이너에서 항목의 크기를 조정 하도록 합니다.

서버 및 관련 항목에 대 한 자세한 내용은 [컨테이너: 고급 기능](../../mfc/containers-advanced-features.md)문서에서 서버 [: 서버 구현](../../mfc/servers-implementing-a-server.md) 및 "컨테이너/서버 응용 프로그램 만들기" 문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a> COleServerItem:: AddOtherClipboardData

지정 된 개체의 OLE 항목에 대 한 표시 및 변환 형식을 지정 하려면이 함수를 호출 `COleDataSource` 합니다.

```cpp
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>매개 변수

*pDataSource*<br/>
데이터가 배치 되어야 하는 개체에 대 한 포인터 `COleDataSource` 입니다.

### <a name="remarks"></a>설명

항목에 대 한 프레젠테이션 형식 (메타 파일 그림)을 제공 하려면 [OnDraw](#ondraw) 멤버 함수를 구현 해야 합니다. 다른 변환 형식을 지원 하려면 [Getdatasource](#getdatasource) 에서 반환 된 [coledatasource](../../mfc/reference/coledatasource-class.md) 개체를 사용 하 여 등록 하 고, [onrenderdata](#onrenderdata) 멤버 함수를 재정의 하 여 지원 하려는 형식으로 데이터를 제공 합니다.

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a> COleServerItem:: COleServerItem

개체를 생성 `COleServerItem` 하 여 서버 문서의 문서 항목 컬렉션에 추가 합니다.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>매개 변수

*pServerDoc*<br/>
새 항목을 포함 하는 문서에 대 한 포인터입니다.

*bAutoDelete*<br/>
개체에 대 한 링크를 해제할 때 개체를 삭제할 수 있는지 여부를 나타내는 플래그입니다. 개체가 문서 데이터에서 삭제 해야 하는 정수 부분인 경우이를 FALSE로 설정 `COleServerItem` 합니다. 개체가 프레임 워크에서 삭제할 수 있는 문서 데이터의 범위를 식별 하는 데 사용 되는 보조 구조 이면이를 TRUE로 설정 합니다.

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a> COleServerItem:: CopyToClipboard

OLE 항목을 클립보드에 복사 하려면이 함수를 호출 합니다.

```cpp
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>매개 변수

*bIncludeLink*<br/>
링크 데이터를 클립보드에 복사 해야 하는 경우 TRUE로 설정 합니다. 서버 응용 프로그램에서 링크를 지원 하지 않는 경우이를 FALSE로 설정 합니다.

### <a name="remarks"></a>설명

함수는 [OnGetClipboardData](#ongetclipboarddata) 멤버 함수를 사용 하 여 OLE 항목의 데이터를 포함 하는 [coledatasource](../../mfc/reference/coledatasource-class.md) 개체를 지원 되는 형식으로 만듭니다. 그러면 함수는 `COleDataSource` [Coledatasource:: setclipboard](../../mfc/reference/coledatasource-class.md#setclipboard) 함수를 사용 하 여 개체를 클립보드에 배치 합니다. `COleDataSource`개체는 항목의 네이티브 데이터와 해당 표시를 CF_METAFILEPICT 형식으로 포함 하 고 지원 하도록 선택한 변환 형식의 데이터를 포함 합니다. 이 멤버 함수가 작동 하려면 [직렬화](../../mfc/reference/cobject-class.md#serialize) 및 [OnDraw](#ondraw) 를 구현 해야 합니다.

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a> COleServerItem::D oDragDrop

`DoDragDrop`멤버 함수를 호출 하 여 끌어서 놓기 작업을 수행 합니다.

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>매개 변수

*lpRectItem*<br/>
화면에서 클라이언트 영역을 기준으로 하는 항목의 사각형 (픽셀)입니다.

*ptOffset*<br/>
끌기를 시작할 때의 마우스 위치가 있는 *Lpitemrect* 의 오프셋입니다.

*bIncludeLink*<br/>
링크 데이터를 클립보드에 복사 해야 하는 경우 TRUE로 설정 합니다. 응용 프로그램에서 링크를 지원 하지 않는 경우 FALSE로 설정 합니다.

*dwEffects*<br/>
끌기 소스에서 끌기 작업을 허용 하는 효과를 결정 합니다 (복사, 이동 및 링크의 조합).

*lpRectStartDrag*<br/>
끌기가 실제로 시작 되는 위치를 정의 하는 사각형에 대 한 포인터입니다. 자세한 내용은 아래 설명 부분을 참조하십시오.

### <a name="return-value"></a>반환 값

DROPEFFECT 열거형의 값입니다. DROPEFFECT_MOVE 경우 원래 데이터를 제거 해야 합니다.

### <a name="remarks"></a>설명

끌어서 놓기 작업은 즉시 시작 되지 않습니다. 마우스 커서가 *lpRectStartDrag* 로 지정 된 사각형을 벗어날 때까지 또는 지정 된 시간 (밀리초)이 경과 될 때까지 대기 합니다. *LpRectStartDrag* 가 NULL 인 경우 마우스 커서가 한 픽셀씩 이동할 때 끌기가 시작 되도록 기본 사각형이 사용 됩니다.

지연 시간은 레지스트리 키 설정에 의해 지정 됩니다. [Cwinapp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) 또는 [Cwinapp:: writeprofilestring](../../mfc/reference/cwinapp-class.md#writeprofileint)를 호출 하 여 지연 시간을 변경할 수 있습니다. 지연 시간을 지정 하지 않으면 기본값인 200 밀리초가 사용 됩니다. 끌기 지연 시간은 다음과 같이 저장 됩니다.

- Windows NT 끌어서 지연 시간은 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini \Windows\DragDelay.에 저장 됩니다.

- Windows 2.x 끌어 놓기 지연 시간은 WIN.INI 파일의 [Windows} 섹션 아래에 저장 됩니다.

- Windows 95/98 끌어서 지연 시간은 캐시 된 버전의 WIN.INI에 저장 됩니다.

레지스트리 또는에서 끌어서 지연 정보를 저장 하는 방법에 대 한 자세한 내용 INI 파일 Windows SDK의 [Writeprofilestring](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 을 참조 하십시오.

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a> COleServerItem:: GetClipboardData

[CopyToClipboard](#copytoclipboard) 를 호출한 경우이 함수를 호출 하 여 클립보드에 복사 되는 모든 데이터로 지정 된 [coledatasource](../../mfc/reference/coledatasource-class.md) 개체를 채웁니다 ( [dodragdrop](#dodragdrop)을 호출한 경우에도 동일한 데이터가 전송 됨).

```cpp
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>매개 변수

*pDataSource*<br/>
`COleDataSource`지원 되는 모든 형식으로 OLE 항목의 데이터를 수신 하는 개체에 대 한 포인터입니다.

*bIncludeLink*<br/>
링크 데이터를 클립보드에 복사 해야 하면 TRUE입니다. 서버 응용 프로그램에서 링크를 지원 하지 않으면 FALSE입니다.

*lpOffset*<br/>
개체의 원점에서 마우스 커서의 오프셋 (픽셀)입니다.

*lpSize*<br/>
개체의 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

이 함수는 [GetEmbedSourceData](#getembedsourcedata) 멤버 함수를 호출 하 여 OLE 항목에 대 한 네이티브 데이터를 가져오고 [AddOtherClipboardData](#addotherclipboarddata) member 함수를 호출 하 여 프레젠테이션 형식 및 지원 되는 변환 형식을 가져옵니다. *Bincludelink* 가 TRUE 이면 함수는 항목에 대 한 링크 데이터를 가져오기 위해 [GetLinkSourceData](#getlinksourcedata) 도 호출 합니다.

`COleDataSource`에서 제공 하는 형식 앞 이나 뒤에 개체의 형식을 추가 하려면이 함수를 재정의 `CopyToClipboard` 합니다.

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a> COleServerItem:: GetDataSource

서버 응용 프로그램에서 지 원하는 변환 형식을 저장 하는 데 사용 되는 [Coledatasource](../../mfc/reference/coledatasource-class.md) 개체를 가져오려면이 함수를 호출 합니다.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>반환 값

`COleDataSource`변환 형식을 저장 하는 데 사용 되는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터 전송 작업 중 서버 응용 프로그램에서 다양 한 형식의 데이터를 제공 하도록 하려면 `COleDataSource` 이 함수에서 반환 하는 개체에 해당 형식을 등록 합니다. 예를 들어 클립보드 또는 끌어서 놓기 작업에 대 한 OLE 항목의 CF_TEXT 표현을 제공 하려는 경우이 함수가 반환 하는 개체에 형식을 등록 한 `COleDataSource` 다음 `OnRenderXxxData` 멤버 함수를 재정의 하 여 데이터를 제공 합니다.

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a> COleServerItem:: GetDocument

항목을 포함 하는 문서에 대 한 포인터를 가져오려면이 함수를 호출 합니다.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>반환 값

항목을 포함 하는 문서에 대 한 포인터입니다. 항목이 문서의 일부가 아니면 NULL입니다.

### <a name="remarks"></a>설명

이를 통해 생성자에 인수로 전달한 서버 문서에 액세스할 수 있습니다 `COleServerItem` .

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a> COleServerItem:: GetEmbedSourceData

OLE 항목에 대 한 CF_EMBEDSOURCE 데이터를 가져오려면이 함수를 호출 합니다.

```cpp
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>매개 변수

*lpStgMedium*<br/>
OLE 항목에 대 한 CF_EMBEDSOURCE 데이터를 수신 하는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 형식은 항목의 네이티브 데이터를 포함 합니다. `Serialize`이 함수가 제대로 작동 하려면 멤버 함수를 구현 해야 합니다.

그런 다음 [Coledatasource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata)를 사용 하 여 결과를 데이터 원본에 추가할 수 있습니다. 이 함수는 [COleServerItem:: OnGetClipboardData](#ongetclipboarddata)에 의해 자동으로 호출 됩니다.

자세한 내용은 Windows SDK에서 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 을 참조 하세요.

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a> COleServerItem:: GetItemName

항목의 이름을 가져오려면이 함수를 호출 합니다.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>반환 값

항목의 이름입니다.

### <a name="remarks"></a>설명

일반적으로 연결 된 항목에 대해서만이 함수를 호출 합니다.

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a> COleServerItem:: GetLinkSourceData

OLE 항목에 대 한 CF_LINKSOURCE 데이터를 가져오려면이 함수를 호출 합니다.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>매개 변수

*lpStgMedium*<br/>
OLE 항목에 대 한 CF_LINKSOURCE 데이터를 수신 하는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 형식에는 ole 항목의 형식을 설명 하는 CLSID와 OLE 항목을 포함 하는 문서를 찾는 데 필요한 정보가 포함 됩니다.

그런 다음 [Coledatasource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata)를 사용 하 여 결과를 데이터 원본에 추가할 수 있습니다. 이 함수는 [OnGetClipboardData](#ongetclipboarddata)에 의해 자동으로 호출 됩니다.

자세한 내용은 Windows SDK에서 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 을 참조 하세요.

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a> COleServerItem:: GetObjectDescriptorData

OLE 항목에 대 한 CF_OBJECTDESCRIPTOR 데이터를 가져오려면이 함수를 호출 합니다.

```cpp
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>매개 변수

*lpOffset*<br/>
OLE 항목의 왼쪽 위 모퉁이에서 마우스 클릭의 오프셋입니다. NULL일 수 있습니다.

*lpSize*<br/>
OLE 항목의 크기입니다. NULL일 수 있습니다.

*lpStgMedium*<br/>
OLE 항목에 대 한 CF_OBJECTDESCRIPTOR 데이터를 수신 하는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조에 대 한 포인터입니다.

### <a name="remarks"></a>설명

정보는 `STGMEDIUM` *lpStgMedium* 가 가리키는 구조에 복사 됩니다. 이 형식에는 붙여넣기 특수 대화 상자에 필요한 정보가 포함 됩니다.

자세한 내용은 Windows SDK에서 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 을 참조 하세요.

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a> COleServerItem:: IsConnected

OLE 항목이 연결 되어 있는지 확인 하려면이 함수를 호출 합니다.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>반환 값

항목이 연결 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

하나 이상의 컨테이너에 항목에 대 한 참조가 있는 경우 OLE 항목은 연결 된 것으로 간주 됩니다. 참조 횟수가 0 보다 크거나 포함 된 항목인 경우 항목이 연결 됩니다.

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a> COleServerItem:: IsLinkedItem

OLE 항목이 연결 된 항목 인지 확인 하려면이 함수를 호출 합니다.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>반환 값

항목이 링크 된 항목인 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

항목이 유효 하 고 문서의 포함 된 항목 목록에 반환 되지 않은 경우 항목이 연결 됩니다. 연결 된 항목이 컨테이너에 연결 되어 있거나 연결 되어 있지 않을 수 있습니다.

연결 된 항목과 포함 항목 모두에 대해 동일한 클래스를 사용 하는 것이 일반적입니다. `IsLinkedItem` 연결 된 항목이 포함 된 항목과 다르게 동작 하도록 할 수 있습니다. 단, 코드의 공통적인 경우도 많습니다.

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a> COleServerItem:: m_sizeExtent

이 멤버는 컨테이너 문서에 표시 되는 개체의 양을 서버에 알려 줍니다.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>설명

[Onsetextent](#onsetextent) 기본 구현에서는이 멤버를 설정 합니다.

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a> COleServerItem:: NotifyChanged

연결 된 항목이 변경 된 후이 함수를 호출 합니다.

```cpp
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>매개 변수

*nDrawAspect*<br/>
변경 된 OLE 항목의 모양을 나타내는 DVASPECT 열거형의 값입니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- DVASPECT_CONTENT 항목은 해당 컨테이너 내에 포함 된 개체로 표시 될 수 있는 방식으로 표시 됩니다.

- DVASPECT_THUMBNAIL 항목은 검색 도구에 표시 될 수 있도록 "축소판 그림" 표현으로 렌더링 됩니다.

- DVASPECT_ICON 항목은 아이콘으로 표시 됩니다.

- DVASPECT_DOCPRINT 항목은 파일 메뉴의 인쇄 명령을 사용 하 여 인쇄 된 것 처럼 표시 됩니다.

### <a name="remarks"></a>설명

컨테이너 항목이 자동 링크를 사용 하 여 문서에 연결 된 경우 해당 항목은 변경 내용을 반영 하도록 업데이트 됩니다. MFC 라이브러리를 사용 하 여 작성 된 컨테이너 응용 프로그램에서 [COleClientItem:: OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 가 응답으로 호출 됩니다.

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a> COleServerItem:: OnDoVerb

지정 된 동사를 실행 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>매개 변수

*iVerb*<br/>
실행할 동사를 지정 합니다. 다음 중 하나일 수 있습니다.

|값|의미|기호|
|-----------|-------------|------------|
|0|기본 동사|OLEIVERB_PRIMARY|
|1|보조 동사|(없음)|
|- 1|편집할 항목 표시|OLEIVERB_SHOW|
|- 2|별도 창의 항목 편집|OLEIVERB_OPEN|
|- 3|항목 숨기기|OLEIVERB_HIDE|

-1 값은 일반적으로 다른 동사의 별칭입니다. 열린 편집이 지원 되지 않는 경우-2는-1과 동일한 효과를 가집니다. 추가 값은 Windows SDK에서 [IOleObject::D 초과 b](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 를 참조 하세요.

### <a name="remarks"></a>설명

MFC 라이브러리를 사용 하 여 컨테이너 응용 프로그램을 작성 한 경우이 함수는 해당 개체의 [COleClientItem:: Activate](../../mfc/reference/coleclientitem-class.md#activate) 멤버 함수가 호출 될 때 호출 됩니다 `COleClientItem` . 기본 구현에서는 기본 동사 나 OLEIVERB_SHOW 지정 된 경우에는 [Onshow](#onshow) 멤버 함수를 호출 하 고, 보조 동사 또는 OLEIVERB_OPEN 지정 된 경우에는 [OnOpen](#onopen) 를, OLEIVERB_HIDE 지정 된 경우 [onshow](#onhide) 를 호출 합니다. 기본 구현에서는 `OnShow` *iverb* 가 위에 나열 된 동사 중 하나가 아닌 경우를 호출 합니다.

기본 동사가 항목을 표시 하지 않는 경우이 함수를 재정의 합니다. 예를 들어 항목이 소리 기록이 고 해당 기본 동사가 재생 되는 경우 항목을 재생 하기 위해 서버 응용 프로그램을 표시할 필요가 없습니다.

자세한 내용은 Windows SDK의 [IOleObject::D 과도 b](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 를 참조 하세요.

## <a name="coleserveritemondraw"></a><a name="ondraw"></a> COleServerItem:: OnDraw

OLE 항목을 메타 파일로 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
항목을 그릴 [CDC](../../mfc/reference/cdc-class.md) 개체에 대 한 포인터입니다. 표시 컨텍스트는 특성 표시 컨텍스트에 자동으로 연결 되므로 특성 함수를 호출할 수 있습니다. 단,이 경우 메타 파일을 특정 장치로 지정 해야 합니다.

*rSize*<br/>
메타 파일을 그릴 크기 (HIMETRIC 단위)입니다.

### <a name="return-value"></a>반환 값

항목이 성공적으로 그려진 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

OLE 항목의 메타 파일 표현은 컨테이너 응용 프로그램에 항목을 표시 하는 데 사용 됩니다. 컨테이너 응용 프로그램이 MFC 라이브러리를 사용 하 여 작성 된 경우 해당 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 개체의 [Draw](../../mfc/reference/coleclientitem-class.md#draw) 멤버 함수에서 메타 파일을 사용 합니다. 기본 구현은 없습니다. 지정 된 장치 컨텍스트에 항목을 그리려면이 함수를 재정의 해야 합니다.

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a> COleServerItem:: OnDrawEx

모든 그리기를 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
항목을 그릴 [CDC](../../mfc/reference/cdc-class.md) 개체에 대 한 포인터입니다. 특성 함수를 호출할 수 있도록 DC가 특성 DC에 자동으로 연결 됩니다.

*nDrawAspect*<br/>
DVASPECT 열거형의 값입니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- DVASPECT_CONTENT 항목은 해당 컨테이너 내에 포함 된 개체로 표시 될 수 있는 방식으로 표시 됩니다.

- DVASPECT_THUMBNAIL 항목은 검색 도구에 표시 될 수 있도록 "축소판 그림" 표현으로 렌더링 됩니다.

- DVASPECT_ICON 항목은 아이콘으로 표시 됩니다.

- DVASPECT_DOCPRINT 항목은 파일 메뉴의 인쇄 명령을 사용 하 여 인쇄 된 것 처럼 표시 됩니다.

*rSize*<br/>
HIMETRIC unit에 있는 항목의 크기입니다.

### <a name="return-value"></a>반환 값

항목이 성공적으로 그려진 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

DVASPECT DVASPECT_CONTENT 같을 때 기본 구현에서는를 호출 하 고, `OnDraw` 그렇지 않으면 실패 합니다.

이 함수를 재정의 하 여 DVASPECT_ICON 또는 DVASPECT_THUMBNAIL와 같은 DVASPECT_CONTENT 이외의 다른 요소에 대 한 프레젠테이션 데이터를 제공 합니다.

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a> COleServerItem:: OnGetClipboardData

[CopyToClipboard](#copytoclipboard) 멤버 함수를 호출하여 클립보드에 배치 되는 모든 데이터를 포함하는 `COleDataSource` 개체를 가져오기 위해 프레임 워크에서 호출됩니다.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>매개 변수

*bIncludeLink*<br/>
링크 데이터를 클립보드에 복사 해야 하는 경우 TRUE로 설정 합니다. 서버 응용 프로그램에서 링크를 지원 하지 않는 경우이를 FALSE로 설정 합니다.

*lpOffset*<br/>
개체의 원점에서 마우스 커서의 오프셋 (픽셀)입니다.

*lpSize*<br/>
개체의 크기 (픽셀)입니다.

### <a name="return-value"></a>반환 값

클립보드 데이터를 포함 하는 [Coledatasource](../../mfc/reference/coledatasource-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현에서는 [GetClipboardData](#getclipboarddata)를 호출 합니다.

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a> COleServerItem:: OnGetExtent

OLE 항목의 크기 (HIMETRIC 단위)를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>매개 변수

*nDrawAspect*<br/>
범위를 검색할 OLE 항목의 측면을 지정 합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- DVASPECT_CONTENT 항목은 해당 컨테이너 내에 포함 된 개체로 표시 될 수 있는 방식으로 표시 됩니다.

- DVASPECT_THUMBNAIL 항목은 검색 도구에 표시 될 수 있도록 "축소판 그림" 표현으로 렌더링 됩니다.

- DVASPECT_ICON 항목은 아이콘으로 표시 됩니다.

- DVASPECT_DOCPRINT 항목은 파일 메뉴의 인쇄 명령을 사용 하 여 인쇄 된 것 처럼 표시 됩니다.

*rSize*<br/>
`CSize`OLE 항목의 크기를 수신 하는 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

MFC 라이브러리를 사용 하 여 컨테이너 응용 프로그램을 작성 한 경우이 함수는 해당 개체의 [Getextent](../../mfc/reference/coleclientitem-class.md#getextent) 멤버 함수가 호출 될 때 호출 됩니다 `COleClientItem` . 기본 구현은 아무 작업도 수행하지 않습니다. 직접 구현 해야 합니다. OLE 항목의 크기에 대 한 요청을 처리할 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다.

## <a name="coleserveritemonhide"></a><a name="onhide"></a> COleServerItem:: OnHide

OLE 항목을 숨기기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnHide();
```

### <a name="remarks"></a>설명

기본 호출 `COleServerDoc::OnShowDocument( FALSE )` 입니다. 또한 함수는 OLE 항목이 숨겨져 있음을 컨테이너에 알립니다. OLE 항목을 숨길 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다.

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a> COleServerItem:: OnInitFromData

*Pdataobject* 의 콘텐츠를 사용 하 여 OLE 항목을 초기화 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>매개 변수

*pDataObject*<br/>
OLE 항목을 초기화 하기 위한 다양 한 형식의 데이터가 들어 있는 OLE 데이터 개체에 대 한 포인터입니다.

*bCreation*<br/>
컨테이너 응용 프로그램에서 새로 만드는 OLE 항목을 초기화 하기 위해 함수가 호출 되 면 TRUE입니다. 기존 OLE 항목의 내용을 바꾸기 위해 함수가 호출 되 면 FALSE입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Bcreation* 이 TRUE 인 경우 컨테이너에서 현재 선택 영역을 기반으로 새 개체 삽입을 구현 하는 경우이 함수가 호출 됩니다. 선택한 데이터는 새 OLE 항목을 만들 때 사용 됩니다. 예를 들어 스프레드시트 프로그램에서 셀 범위를 선택한 다음 새 개체 삽입을 사용 하 여 선택한 범위의 값을 기준으로 차트를 만들 수 있습니다. 기본 구현은 아무 작업도 수행하지 않습니다. 이 함수를 재정의 하 여 *Pdataobject* 에서 제공 하는 허용 가능한 형식을 선택 하 고 제공 된 데이터를 기반으로 OLE 항목을 초기화 합니다. 이는 고급 재정의 가능입니다.

자세한 내용은 Windows SDK [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) 를 참조 하세요.

## <a name="coleserveritemonopen"></a><a name="onopen"></a> COleServerItem:: OnOpen

서버 응용 프로그램의 개별 인스턴스에 OLE 항목을 표시 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnOpen();
```

### <a name="remarks"></a>설명

기본 구현에서는 OLE 항목을 포함 하는 문서를 표시 하는 첫 번째 프레임 창을 활성화 합니다. 응용 프로그램이 미니 서버 이면 기본 구현에 주 창이 표시 됩니다. 또한 함수는 OLE 항목이 열려 있음을 컨테이너에 알립니다.

OLE 항목을 열 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다. 이는 선택 항목을 열 때 링크로 설정 하려는 연결 된 항목에 특히 일반적입니다.

자세한 내용은 Windows SDK에서 [IOleClientSite:: OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) 를 참조 하세요.

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a> COleServerItem:: OnQueryUpdateItems

현재 서버 문서에 있는 링크 된 항목이 만료 되었는지 확인 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>반환 값

업데이트를 필요로 하는 항목이 문서에 있는 경우 0이 아닌 것입니다. 모든 항목이 최신 상태 이면 0입니다.

### <a name="remarks"></a>설명

원본 문서가 변경 되었지만 링크 된 항목이 문서의 변경 내용을 반영 하도록 업데이트 되지 않은 경우 항목이 만료 됩니다.

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a> COleServerItem:: OnRenderData

지정 된 형식의 데이터를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
정보를 요청 하는 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

*lpStgMedium*<br/>
데이터가 반환 되는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 형식은 이전에 `COleDataSource` 지연 렌더링을 위해 [delayrenderdata](../../mfc/reference/coledatasource-class.md#delayrenderdata) 또는 [delayrenderfiledata](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) 멤버 함수를 사용 하 여 개체에 배치 되었습니다. 이 함수의 기본 구현은 제공 된 저장소 미디어가 파일 또는 메모리 일 경우 각각 [Onrenderfiledata](#onrenderfiledata) 또는 [onrenderfiledata](#onrenderglobaldata)를 호출 합니다. 이러한 형식이 모두 제공 되지 않으면 기본 구현에서 0을 반환 하 고 아무 작업도 수행 하지 않습니다.

*LpStgMedium* ->  *tymed* 가 TYMED_NULL 경우 STGMEDIUM *tymed* 에 지정 >된 대로를 할당 하 고 채워야 합니다. TYMED_NULL 하지 않으면 데이터를 사용 하 여 STGMEDIUM를 채워야 합니다.

이는 고급 재정의 가능입니다. 요청 된 형식 및 중간에 데이터를 제공 하려면이 함수를 재정의 합니다. 데이터에 따라이 함수의 다른 버전 중 하나를 대신 재정의할 수 있습니다. 데이터가 작고 크기가 고정 되어 있으면를 재정의 `OnRenderGlobalData` 합니다. 데이터가 파일에 있거나 가변 크기인 경우를 재정의 `OnRenderFileData` 합니다.

자세한 내용은 Windows SDK에서 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)및 [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) 를 참조 하세요.

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a> COleServerItem:: OnRenderFileData

저장소 미디어가 파일인 경우 지정 된 형식으로 데이터를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
정보를 요청 하는 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

*.Pfile*<br/>
`CFile`데이터가 렌더링 될 개체를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 형식은 이전에 `COleDataSource` 지연 된 렌더링을 위해 [Delayrenderdata](../../mfc/reference/coledatasource-class.md#delayrenderdata) 멤버 함수를 사용 하 여 개체에 배치 되었습니다. 이 함수의 기본 구현은 단순히 FALSE를 반환 합니다.

이는 고급 재정의 가능입니다. 요청 된 형식 및 중간에 데이터를 제공 하려면이 함수를 재정의 합니다. 데이터에 따라이 함수의 다른 버전 중 하나를 대신 재정의 하는 것이 좋습니다. 여러 저장소 미디어를 처리 하려는 경우 [Onrenderdata](#onrenderdata)를 재정의 합니다. 데이터가 파일에 있거나 가변 크기인 경우 [Onrenderfiledata](#onrenderfiledata)를 재정의 합니다.

자세한 내용은 Windows SDK에서 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 및 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 를 참조 하세요.

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a> COleServerItem:: OnRenderGlobalData

지정 된 저장 미디어가 전역 메모리 인 경우 지정 된 형식의 데이터를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
정보를 요청 하는 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

*phGlobal*<br/>
데이터가 반환 될 전역 메모리의 핸들을 가리킵니다. 메모리가 할당 되지 않은 경우이 매개 변수는 NULL이 될 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 형식은 이전에 `COleDataSource` 지연 된 렌더링을 위해 [Delayrenderdata](../../mfc/reference/coledatasource-class.md#delayrenderdata) 멤버 함수를 사용 하 여 개체에 배치 되었습니다. 이 함수의 기본 구현은 단순히 FALSE를 반환 합니다.

*Phglobal* 이 NULL 인 경우 새 HGLOBAL을 할당 하 고 *phglobal* 에 반환 해야 합니다. 그렇지 않으면 *Phglobal* 로 지정 된 HGLOBAL 데이터를 채워야 합니다. HGLOBAL에 배치 되는 데이터의 양은 메모리 블록의 현재 크기를 초과 하면 안 됩니다. 또한 블록을 더 큰 크기에 다시 할당할 수 없습니다.

이는 고급 재정의 가능입니다. 요청 된 형식 및 중간에 데이터를 제공 하려면이 함수를 재정의 합니다. 데이터에 따라이 함수의 다른 버전 중 하나를 대신 재정의할 수 있습니다. 여러 저장소 미디어를 처리 하려는 경우 [Onrenderdata](#onrenderdata)를 재정의 합니다. 데이터가 파일에 있거나 가변 크기인 경우 [Onrenderfiledata](#onrenderfiledata)를 재정의 합니다.

자세한 내용은 Windows SDK에서 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 및 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 를 참조 하세요.

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a> COleServerItem:: OnSetColorScheme

OLE 항목을 편집할 때 사용할 색상표를 지정 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>매개 변수

*lpLogPalette*<br/>
Windows [Logpalette](/windows/win32/api/wingdi/ns-wingdi-logpalette) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

색상표를 사용 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

MFC 라이브러리를 사용 하 여 컨테이너 응용 프로그램을 작성 한 경우이 함수는 해당 개체의 [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 함수가 호출 될 때 호출 됩니다 `COleClientItem` . 기본 구현에서는 FALSE를 반환 합니다. 권장 색상표를 사용 하려면이 함수를 재정의 합니다. 서버 응용 프로그램은 제안 된 색상표를 사용할 필요가 없습니다.

자세한 내용은 Windows SDK에서 [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 를 참조 하세요.

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a> COleServerItem:: OnSetData

OLE 항목의 데이터를 지정 된 데이터로 바꾸기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
데이터의 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체에 대 한 포인터입니다.

*lpStgMedium*<br/>
데이터가 있는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체에 대 한 포인터입니다.

*bRelease*<br/>
함수 호출을 완료 한 후 저장소 미디어의 소유권이 있는 사용자를 나타냅니다. 호출자는 저장소 미디어를 대신해 할당 된 리소스를 해제할 책임이 있는 사용자를 결정 합니다. 호출자가 *bRelease* 를 설정 하 여이를 수행 합니다. *BRelease* 가 0이 아닌 경우 서버 항목은 소유권을 가지 며 사용이 끝나면 미디어를 해제 합니다. *BRelease* 가 0 이면 호출자는 소유권을 유지 하 고 서버 항목은 호출 기간 동안만 저장소 미디어를 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

서버 항목은 성공적으로 가져올 때까지 데이터 소유권을 받지 않습니다. 즉, 0을 반환 하는 경우에는 소유권을 사용 하지 않습니다. 데이터 원본에서 소유권을 가져오는 경우 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 함수를 호출 하 여 저장소 미디어를 해제 합니다.

기본 구현은 아무 작업도 수행하지 않습니다. OLE 항목의 데이터를 지정 된 데이터로 바꾸려면이 함수를 재정의 합니다. 이는 고급 재정의 가능입니다.

자세한 내용은 Windows SDK에서 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)및 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 를 참조 하세요.

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a> COleServerItem:: OnSetExtent

컨테이너 문서에서 사용할 수 있는 공간 크기를 OLE 항목에 알리기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>매개 변수

*nDrawAspect*<br/>
범위가 지정 되는 OLE 항목의 측면을 지정 합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- DVASPECT_CONTENT 항목은 해당 컨테이너 내에 포함 된 개체로 표시 될 수 있는 방식으로 표시 됩니다.

- DVASPECT_THUMBNAIL 항목은 검색 도구에 표시 될 수 있도록 "축소판 그림" 표현으로 렌더링 됩니다.

- DVASPECT_ICON 항목은 아이콘으로 표시 됩니다.

- DVASPECT_DOCPRINT 항목은 파일 메뉴의 인쇄 명령을 사용 하 여 인쇄 된 것 처럼 표시 됩니다.

*size*<br/>
OLE 항목의 새 크기를 지정 하는 [csize](../../atl-mfc-shared/reference/csize-class.md) 구조체입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

컨테이너 응용 프로그램이 MFC 라이브러리를 사용 하 여 작성 된 경우이 함수는 해당 개체의 [Setextent](../../mfc/reference/coleclientitem-class.md#setextent) 멤버 함수가 호출 될 때 호출 됩니다 `COleClientItem` . *Ndrawaspect* DVASPECT_CONTENT 되는 경우 기본 구현은 [m_sizeExtent](#m_sizeextent) 멤버를 지정 된 크기로 설정 합니다. 그렇지 않으면 0을 반환 합니다. 항목의 크기를 변경할 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다.

## <a name="coleserveritemonshow"></a><a name="onshow"></a> COleServerItem:: OnShow

OLE 항목을 표시 하도록 서버 응용 프로그램에 지시 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnShow();
```

### <a name="remarks"></a>설명

이 함수는 일반적으로 컨테이너 응용 프로그램의 사용자가 항목을 만들거나 편집 등의 동사를 실행 하 여 항목을 표시 해야 하는 경우 호출 됩니다. 기본 구현에서는 내부 활성화를 시도 합니다. 이 작업이 실패 하면 함수는 `OnOpen` 멤버 함수를 호출 하 여 OLE 항목을 별도의 창에 표시 합니다.

OLE 항목이 표시 될 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다.

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a> COleServerItem:: OnUpdate

항목이 수정 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>매개 변수

*pSender*<br/>
문서를 수정한 항목에 대 한 포인터입니다. NULL일 수 있습니다.

*lHint*<br/>
수정에 대 한 정보를 포함 합니다.

*pHint*<br/>
수정에 대 한 정보를 저장 하는 개체에 대 한 포인터입니다.

*nDrawAspect*<br/>
DVASPECT 열거형의 값입니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- DVASPECT_CONTENT 항목은 해당 컨테이너 내에 포함 된 개체로 표시 될 수 있는 방식으로 표시 됩니다.

- DVASPECT_THUMBNAIL 항목은 검색 도구에 표시 될 수 있도록 "축소판 그림" 표현으로 렌더링 됩니다.

- DVASPECT_ICON 항목은 아이콘으로 표시 됩니다.

- DVASPECT_DOCPRINT 항목은 파일 메뉴의 인쇄 명령을 사용 하 여 인쇄 된 것 처럼 표시 됩니다.

### <a name="remarks"></a>설명

기본 구현에서는 힌트 또는 송신자와 상관 없이 [NotifyChanged](#notifychanged)를 호출 합니다.

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a> COleServerItem:: OnUpdateItems

서버 문서의 모든 항목을 업데이트 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>설명

기본 구현에서는 문서의 모든 개체에 대해 [Updatelink](../../mfc/reference/coleclientitem-class.md#updatelink) 를 호출 합니다 `COleClientItem` .

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a> COleServerItem:: SetItemName

연결 된 항목을 만들어 해당 이름을 설정할 때이 함수를 호출 합니다.

```cpp
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>매개 변수

*lpszItemName*<br/>
항목의 새 이름에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이름은 문서 내에서 고유 해야 합니다. 연결 된 항목을 편집 하기 위해 서버 응용 프로그램을 호출 하면 응용 프로그램에서이 이름을 사용 하 여 항목을 찾습니다. 포함 된 항목에 대해이 함수를 호출할 필요가 없습니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem 클래스](../../mfc/reference/cdocitem-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 클래스](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc 클래스](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer 클래스](../../mfc/reference/coletemplateserver-class.md)
