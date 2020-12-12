---
description: '자세한 정보: CView 클래스'
title: CView 클래스
ms.date: 11/04/2016
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
ms.openlocfilehash: 8bb45bff3f63c2c1f9fd01d9c50091f5a3117d74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318483"
---
# <a name="cview-class"></a>CView 클래스

사용자 정의 뷰 클래스에 대한 기본 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CView:: CView](#cview)|`CView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CView::D oPreparePrinting](#doprepareprinting)|인쇄 대화 상자를 표시 하 고 프린터 장치 컨텍스트를 만듭니다. 멤버 함수를 재정의할 때를 호출 `OnPreparePrinting` 합니다.|
|[CView:: GetDocument](#getdocument)|뷰와 연결 된 문서를 반환 합니다.|
|[CView:: IsSelected](#isselected)|문서 항목이 선택 되었는지 여부를 테스트 합니다. OLE 지원에 필요 합니다.|
|[CView:: System.windows.uielement.ondragenter](#ondragenter)|항목을 뷰의 끌어서 놓기 영역으로 처음 끌 때 호출 됩니다.|
|[CView:: System.windows.uielement.ondragleave](#ondragleave)|끌어 온 항목이 뷰의 끌어서 놓기 영역을 벗어나면 호출 됩니다.|
|[CView:: System.windows.uielement.ondragover](#ondragover)|뷰의 끌어서 놓기 영역 위로 항목을 끌 때 호출 됩니다.|
|[CView:: OnDragScroll](#ondragscroll)|커서를 창의 스크롤 영역으로 끌 지 여부를 결정 하기 위해 호출 됩니다.|
|[CView:: OnDrop](#ondrop)|뷰의 끌어서 놓기 영역 (기본 처리기)에 항목을 놓을 때 호출 됩니다.|
|[CView:: OnDropEx](#ondropex)|뷰의 끌어서 놓기 영역 (기본 처리기)에 항목을 놓을 때 호출 됩니다.|
|[CView:: OnInitialUpdate](#oninitialupdate)|뷰가 문서에 먼저 첨부 된 후에 호출 됩니다.|
|[CView:: OnPrepareDC](#onpreparedc)|`OnDraw`화면 표시에 대해 멤버 함수를 호출 하기 전이나 `OnPrint` 인쇄 또는 인쇄 미리 보기에 대해 멤버 함수가 호출 되기 전에 호출 됩니다.|
|[CView:: OnScroll](#onscroll)|OLE 항목을 뷰의 테두리 밖으로 끌 때 호출 됩니다.|
|[CView:: OnScrollBy](#onscrollby)|활성 내부 OLE 항목을 포함 하는 뷰가 스크롤될 때 호출 됩니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CView:: OnActivateFrame](#onactivateframe)|뷰를 포함 하는 프레임 창이 활성화 또는 비활성화 되 면 호출 됩니다.|
|[CView:: OnActivateView](#onactivateview)|뷰가 활성화 될 때 호출 됩니다.|
|[CView::OnBeginPrinting](#onbeginprinting)|인쇄 작업이 시작 되 면 호출 됩니다. GDI (그래픽 장치 인터페이스) 리소스를 할당 하도록 재정의 합니다.|
|[CView:: OnDraw](#ondraw)|화면 표시, 인쇄 또는 인쇄 미리 보기를 위해 문서의 이미지를 렌더링 하기 위해 호출 됩니다. 구현이 필요 합니다.|
|[CView:: OnEndPrinting](#onendprinting)|인쇄 작업이 종료 되 면 호출 됩니다. GDI 리소스 할당 해제를 재정의 합니다.|
|[CView:: OnEndPrintPreview](#onendprintpreview)|미리 보기 모드가 종료 될 때 호출 됩니다.|
|[CView:: OnPreparePrinting](#onprepareprinting)|문서를 인쇄 하거나 미리 보기 전에 호출 됩니다. 인쇄를 초기화 대화 상자를 재정의 합니다.|
|[CView:: OnPrint](#onprint)|문서 페이지를 인쇄 하거나 미리 보기 위해 호출 됩니다.|
|[CView:: OnUpdate](#onupdate)|문서를 수정 했음을 뷰에 알리기 위해 호출 됩니다.|

## <a name="remarks"></a>설명

보기는 문서에 첨부 되 고 문서와 사용자 간의 중개자 역할을 합니다. 뷰는 화면 또는 프린터에서 문서의 이미지를 렌더링 하 고 사용자 입력을 문서에 대 한 작업으로 해석 합니다.

뷰는 프레임 창의 자식입니다. 분할자 창의 경우와 같이 둘 이상의 뷰에서 프레임 창을 공유할 수 있습니다. 뷰 클래스, 프레임 창 클래스 및 문서 클래스 간의 관계는 개체에 의해 설정 됩니다 `CDocTemplate` . 사용자가 새 창을 열거나 기존 창을 분할 하는 경우 프레임 워크는 새 보기를 생성 하 고 문서에 연결 합니다.

뷰는 한 문서에만 연결 될 수 있지만 문서를 한 번에 여러 개의 뷰 (예: MDI (다중 문서 인터페이스) 응용 프로그램의 여러 자식 창 또는 분할자 창에 표시 되는 경우)에 연결할 수 있습니다. 응용 프로그램은 지정 된 문서 형식에 대해 다양 한 유형의 보기를 지원할 수 있습니다. 예를 들어, 워드 프로세싱 프로그램은 문서에 대 한 전체 텍스트 뷰와 섹션 제목만 표시 하는 개요 보기를 모두 제공할 수 있습니다. 분할자 창을 사용 하는 경우 이러한 여러 유형의 뷰를 별도의 프레임 창에 배치 하거나 단일 프레임 창의 별도 창에 배치할 수 있습니다.

보기는 키보드 입력, 마우스 입력 또는 끌어서 놓기를 통한 입력 또는 메뉴, 도구 모음 또는 스크롤 막대의 명령과 같은 여러 유형의 입력을 처리 해야 할 수 있습니다. 뷰는 프레임 창에 의해 전달 된 명령을 수신 합니다. 지정 된 명령을 처리 하지 않는 뷰에서는 명령을 연결 된 문서에 전달 합니다. 모든 명령 대상과 마찬가지로 보기는 메시지 맵을 통해 메시지를 처리 합니다.

뷰는 문서 데이터를 표시 하 고 수정 하는 것은 아니지만 문서 데이터를 저장 하는 일을 담당 합니다. 문서는 해당 데이터에 대 한 필요한 세부 정보를 포함 하는 뷰를 제공 합니다. 뷰가 문서의 데이터 멤버에 직접 액세스 하도록 하거나, 클래스 클래스에 멤버 함수를 제공 하 여 뷰 클래스에서 호출할 수 있습니다.

문서의 데이터가 변경 되 면 일반적으로 변경 내용을 담당 하는 뷰가 문서에 대해 [CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) 함수를 호출 하 여 `OnUpdate` 각에 대 한 멤버 함수를 호출 하 여 다른 모든 뷰에 알립니다. 의 기본 구현에서는 `OnUpdate` 뷰의 전체 클라이언트 영역을 무효화 합니다. 이를 재정의 하 여 문서의 수정 된 부분에 매핑되는 클라이언트 영역의 영역만 무효화할 수 있습니다.

를 사용 하려면 `CView` 클래스에서 클래스를 파생 시키고 `OnDraw` 화면 표시를 수행 하는 멤버 함수를 구현 합니다. 를 사용 하 여 `OnDraw` 인쇄 및 인쇄 미리 보기를 수행할 수도 있습니다. 프레임 워크는 문서 인쇄 및 미리 보기에 대 한 인쇄 루프를 처리 합니다.

뷰는 [cwnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) 및 [Cwnd:: onhscroll](../../mfc/reference/cwnd-class.md#onvscroll) 멤버 함수를 사용 하 여 스크롤 막대 메시지를 처리 합니다. 이러한 함수에서 스크롤 막대 메시지 처리를 구현 하거나, `CView` 파생 클래스 [CScrollView](../../mfc/reference/cscrollview-class.md) 를 사용 하 여 스크롤을 처리할 수 있습니다.

외에도 `CScrollView` MFC 라이브러리는에서 파생 된 9 개의 다른 클래스를 제공 합니다 `CView` .

- [CCtrlView](../../mfc/reference/cctrlview-class.md), tree, list 및 rich edit 컨트롤을 사용 하 여 문서 뷰 아키텍처를 사용할 수 있도록 하는 뷰입니다.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)대화 상자 컨트롤의 데이터베이스 레코드를 표시 하는 뷰입니다.

- [Ceditview](../../mfc/reference/ceditview-class.md)-간단한 여러 줄 텍스트 편집기를 제공 하는 뷰입니다. `CEditView`개체를 대화 상자에서 컨트롤로 사용 하 고 문서에 대 한 보기를 사용할 수 있습니다.

- [CFormView](../../mfc/reference/cformview-class.md)-대화 상자 컨트롤을 포함 하며 대화 상자 템플릿 리소스를 기반으로 하는 스크롤 가능한 뷰입니다.

- [CListView](../../mfc/reference/clistview-class.md)-목록 컨트롤을 사용 하 여 문서 뷰 아키텍처를 사용할 수 있도록 하는 뷰입니다.

- [CRecordView](../../mfc/reference/crecordview-class.md)대화 상자 컨트롤의 데이터베이스 레코드를 표시 하는 뷰입니다.

- Rich edit 컨트롤을 사용 하 여 문서 뷰 아키텍처를 사용할 수 있도록 하는 [CRichEditView](../../mfc/reference/cricheditview-class.md)입니다.

- [CScrollView](../../mfc/reference/cscrollview-class.md)자동으로 스크롤 기능을 제공 하는 뷰입니다.

- [Ctreeview](../../mfc/reference/ctreeview-class.md)-트리 컨트롤과 문서 뷰 아키텍처를 사용할 수 있도록 하는 뷰입니다.

클래스에는 `CView` `CPreviewView` 프레임 워크에서 인쇄 미리 보기를 수행 하는 데 사용 되는 라는 파생 된 구현 클래스도 있습니다. 이 클래스는 도구 모음, 단일 또는 이중 페이지 미리 보기, 확대/축소, 미리 보기 된 이미지를 확대 하는 등 인쇄 미리 보기 창에 고유한 기능에 대 한 지원을 제공 합니다. 인쇄 미리 보기 `CPreviewView` 모드에서 편집을 지원 하려는 경우와 같이 인쇄 미리 보기에 대해 고유한 인터페이스를 구현 하려는 경우가 아니면의 멤버 함수를 호출 하거나 재정의할 필요가 없습니다. 사용에 대 한 자세한 내용은 `CView` [문서/뷰 아키텍처](../../mfc/document-view-architecture.md) 및 [인쇄](../../mfc/printing.md)를 참조 하세요. 또한 인쇄 미리 보기 사용자 지정에 대 한 자세한 내용은 [기술 참고 사항 30](../../mfc/tn030-customizing-printing-and-print-preview.md) 을 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a> CView:: CView

`CView` 개체를 생성합니다.

```
CView();
```

### <a name="remarks"></a>설명

프레임 워크는 새 프레임 창이 만들어지거나 창이 분할 될 때 생성자를 호출 합니다. [Oninitialupdate](#oninitialupdate) 멤버 함수를 재정의 하 여 문서가 연결 된 후 뷰를 초기화 합니다.

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a> CView::D oPreparePrinting

[Onprepareprinting](#onprepareprinting) 재정의에서이 함수를 호출 하 여 인쇄 대화 상자를 호출 하 고 프린터 장치 컨텍스트를 만듭니다.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>매개 변수

*pInfo*<br/>
현재 인쇄 작업을 설명하는 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

인쇄 또는 인쇄 미리 보기를 시작할 수 있는 경우 0이 아님 작업이 취소 된 경우 0입니다.

### <a name="remarks"></a>설명

이 함수의 동작은 인쇄 또는 인쇄 미리 보기 ( `m_bPreview` *pinfo* 매개 변수의 멤버에 의해 지정 됨)에 대해 호출 되는지 여부에 따라 달라 집니다. 파일이 인쇄 되는 경우이 함수는 *Pinfo* 가 가리키는 [cprintinfo](../../mfc/reference/cprintinfo-structure.md) 구조체의 값을 사용 하 여 인쇄 대화 상자를 호출 합니다. 사용자가 대화 상자를 닫은 후이 함수는 대화 상자에서 지정한 설정을 기반으로 프린터 장치 컨텍스트를 만들고 *Pinfo* 매개 변수를 통해이 장치 컨텍스트를 반환 합니다. 이 장치 컨텍스트는 문서를 인쇄 하는 데 사용 됩니다.

파일을 미리 보는 경우이 함수는 현재 프린터 설정을 사용 하 여 프린터 장치 컨텍스트를 만듭니다. 이 장치 컨텍스트는 미리 보기 중에 프린터를 시뮬레이션 하는 데 사용 됩니다.

## <a name="cviewgetdocument"></a><a name="getdocument"></a> CView:: GetDocument

뷰 문서에 대 한 포인터를 가져오려면이 함수를 호출 합니다.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>반환 값

뷰와 연결 된 [CDocument](../../mfc/reference/cdocument-class.md) 개체에 대 한 포인터입니다. 뷰가 문서에 연결 되지 않은 경우 NULL입니다.

### <a name="remarks"></a>설명

이렇게 하면 문서의 멤버 함수를 호출할 수 있습니다.

## <a name="cviewisselected"></a><a name="isselected"></a> CView:: IsSelected

지정 된 문서 항목이 선택 되어 있는지 여부를 확인 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>매개 변수

*pDocItem*<br/>
테스트 중인 문서 항목을 가리킵니다.

### <a name="return-value"></a>반환 값

지정 된 문서 항목이 선택 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현에서는 FALSE를 반환 합니다. [Cdocitem](../../mfc/reference/cdocitem-class.md) 개체를 사용 하 여 선택 항목을 구현 하는 경우이 함수를 재정의 합니다. 뷰에 OLE 항목이 포함 되어 있으면이 함수를 재정의 해야 합니다.

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a> CView:: OnActivateFrame

뷰를 포함 하는 프레임 창이 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>매개 변수

*nState*<br/>
프레임 창이 활성화 또는 비활성화 되는지 여부를 지정 합니다. 다음 값 중 하나일 수 있습니다.

- 프레임 창이 비활성화 되 WA_INACTIVE입니다.

- 예를 들어 키보드 인터페이스를 사용 하 여 창을 선택 하는 등의 방법으로 마우스 클릭 이외의 방법으로 프레임 창을 활성화 하는 WA_ACTIVE.

- 마우스를 클릭 하 여 프레임 창을 활성화 하는 WA_CLICKACTIVE

*pFrameWnd*<br/>
활성화할 프레임 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

뷰와 연결 된 프레임 창이 활성화 또는 비활성화 되는 경우 특별 한 처리를 수행 하려면이 멤버 함수를 재정의 합니다. 예를 들어, [CFormView](../../mfc/reference/cformview-class.md) 는 포커스가 있는 컨트롤을 저장 하 고 복원할 때이 재정의를 수행 합니다.

## <a name="cviewonactivateview"></a><a name="onactivateview"></a> CView:: OnActivateView

뷰가 활성화 또는 비활성화 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>매개 변수

*bActivate*<br/>
뷰가 활성화 또는 비활성화 되는지 여부를 나타냅니다.

*pActivateView*<br/>
활성화 되 고 있는 뷰 개체를 가리킵니다.

*pDeactiveView*<br/>
비활성화 되 고 있는 뷰 개체를 가리킵니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 활성화 되는 뷰에 포커스를 설정 합니다. 뷰가 활성화 또는 비활성화 될 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다. 예를 들어 비활성 뷰와 활성 뷰를 구분 하는 특별 한 시각적 신호를 제공 하려는 경우 *Bactivate* 매개 변수를 검사 하 고 그에 따라 뷰의 모양을 업데이트 합니다.

응용 프로그램의 주 프레임 창이 활성 뷰를 변경 하지 않고 활성화 된 경우 (예: 응용 프로그램 내에서 한 뷰가 다른 응용 프로그램에서 다른 응용 프로그램으로 포커스가 전송 되는 경우 또는 MDI 자식 창 간에 전환 하는 경우)에는 *pactivateview* 및 *pdeactiveview* 매개 변수가 동일한 뷰를 가리킵니다. 이렇게 하면 필요한 경우 뷰가 해당 팔레트를 다시 인식할 수 있습니다.

이러한 매개 변수는 [CFrameWnd:: GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) 에서 반환 하는 것과 다른 뷰를 사용 하 여 [CFrameWnd:: setactiveview](../../mfc/reference/cframewnd-class.md#setactiveview) 를 호출 하는 경우에 다릅니다. 이는 분할자 창에서 가장 자주 발생 합니다.

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a> CView:: OnBeginPrinting

`OnPreparePrinting` 이 호출된 후 인쇄 또는 인쇄 미리 보기 작업을 시작할 때 프레임워크에서 호출됩니다.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
프린터 디바이스 컨텍스트를 가리킵니다.

*pInfo*<br/>
현재 인쇄 작업을 설명하는 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 구조체를 가리킵니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 아무 작업도 수행하지 않습니다. 인쇄용으로 특별히 필요한 GDI 리소스(예: 펜 또는 글꼴)를 할당하려면 이 함수를 재정의합니다. GDI 개체를 사용하는 각 페이지에 대한 [OnPrint](#onprint) 멤버 함수 내에서 디바이스 컨텍스트로 GDI 개체를 선택합니다. 동일한 view 개체를 사용하여 화면 표시와 인쇄를 모두 수행하는 경우 각 화면 표시에 필요한 GDI 리소스에 별도의 변수를 사용합니다. 이렇게 하면 인쇄하는 동안 화면을 업데이트할 수 있습니다.

또한 이 함수를 사용하여 프린터 디바이스 컨텍스트의 속성에 따라 초기화를 수행할 수 있습니다. 예를 들어 문서를 인쇄하는 데 필요한 페이지 수는 사용자가 인쇄 대화 상자에서 지정한 설정(예: 페이지 길이)에 따라 다를 수 있습니다. 이러한 상황에서는 일반적인 경우와 달리 [OnPreparePrinting](#onprepareprinting) 멤버 함수에서 문서 길이를 지정할 수 없습니다. 대화 상자 설정에 따라 프린터 디바이스 컨텍스트가 만들어질 때까지 기다려야 합니다. [OnBeginPrinting](#onbeginprinting) 은 프린터 디바이스 컨텍스트를 나타내는 [CDC](../../mfc/reference/cdc-class.md) 개체에 대한 액세스를 제공하는 첫 번째 재정의 가능 함수이므로 이 함수에서 문서 길이를 설정할 수 있습니다. 이때까지 문서 길이를 지정하지 않으면 인쇄 미리 보기 중에 스크롤 막대가 표시되지 않습니다.

## <a name="cviewondragenter"></a><a name="ondragenter"></a> CView:: System.windows.uielement.ondragenter

마우스를 놓기 대상 창의 스크롤이 아닌 영역에 처음으로 가져갈 때 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pDataObject*<br/>
뷰의 놓기 영역으로 끌고 있는 [Coledataobject](../../mfc/reference/coledataobject-class.md) 를 가리킵니다.

*dwKeyState*<br/>
보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.

*까지*<br/>
뷰의 클라이언트 영역을 기준으로 하는 현재 마우스 위치입니다.

### <a name="return-value"></a>반환 값

사용자가이 위치에서 개체를 삭제 한 경우 발생 하는 삭제 유형을 나타내는 DROPEFFECT 열거 형식의 값입니다. Drop 형식은 일반적으로 *Dwkeystate* 로 표시 되는 현재 키 상태에 따라 달라 집니다. DROPEFFECT 값에 대 한 keystates 표준 매핑은 다음과 같습니다.

- 이 창에서 데이터 개체를 삭제할 수 DROPEFFECT_NONE.

- MK_CONTROL &#124;에 대 한 DROPEFFECT_LINK MK_SHIFT 개체와 해당 서버 간의 링크를 만듭니다.

- MK_CONTROL에 대 한 DROPEFFECT_COPY는 삭제 된 개체의 복사본을 만듭니다.

- MK_ALT에 대 한 DROPEFFECT_MOVE는 삭제 된 개체의 복사본을 만들고 원래 개체를 삭제 합니다. 이는 뷰가이 데이터 개체를 허용할 수 있는 경우 일반적으로 기본 삭제 효과입니다.

자세한 내용은 MFC 고급 개념 샘플 [OCLIENT](../../overview/visual-cpp-samples.md)를 참조 하세요.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행 하지 않고 DROPEFFECT_NONE을 반환 하는 것입니다.

[System.windows.uielement.ondragover](#ondragover) 멤버 함수에 대 한 이후 호출을 준비 하려면이 함수를 재정의 합니다. 나중에 멤버 함수에서 사용할 수 있도록 데이터 개체에서 필요한 모든 데이터를 검색 해야 합니다 `OnDragOver` . 또한 사용자에 게 시각적 피드백을 제공 하기 위해 뷰를 업데이트 해야 합니다. 자세한 내용은 [OLE 끌어서 놓기: 놓기 대상 구현](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)문서를 참조 하세요.

## <a name="cviewondragleave"></a><a name="ondragleave"></a> CView:: System.windows.uielement.ondragleave

마우스를 해당 창에 대 한 올바른 끌어 놓기 영역 밖으로 이동할 때 끌기 작업을 수행 하는 동안 프레임 워크에서 호출 됩니다.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>설명

개체를 끌어서 놓는 동안 시각적 사용자 의견을 제거 하는 등의 방법으로 [system.windows.uielement.ondragenter](#ondragenter) 또는 [system.windows.uielement.ondragover](#ondragover) 호출 중에 수행 된 작업을 모두 정리 해야 하는 경우이 함수를 재정의 합니다.

## <a name="cviewondragover"></a><a name="ondragover"></a> CView:: System.windows.uielement.ondragover

놓기 대상 창 위로 마우스를 이동할 때 끌기 작업을 수행 하는 동안 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pDataObject*<br/>
놓기 대상 위로 끌고 있는 [Coledataobject](../../mfc/reference/coledataobject-class.md) 를 가리킵니다.

*dwKeyState*<br/>
보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.

*까지*<br/>
뷰 클라이언트 영역을 기준으로 하는 현재 마우스 위치입니다.

### <a name="return-value"></a>반환 값

사용자가이 위치에서 개체를 삭제 한 경우 발생 하는 삭제 유형을 나타내는 DROPEFFECT 열거 형식의 값입니다. 삭제 유형은 *Dwkeystate* 로 표시 되는 현재 키 상태에 따라 달라 집니다. DROPEFFECT 값에 대 한 keystates 표준 매핑은 다음과 같습니다.

- 이 창에서 데이터 개체를 삭제할 수 DROPEFFECT_NONE.

- MK_CONTROL &#124;에 대 한 DROPEFFECT_LINK MK_SHIFT 개체와 해당 서버 간의 링크를 만듭니다.

- MK_CONTROL에 대 한 DROPEFFECT_COPY는 삭제 된 개체의 복사본을 만듭니다.

- MK_ALT에 대 한 DROPEFFECT_MOVE는 삭제 된 개체의 복사본을 만들고 원래 개체를 삭제 합니다. 이는 뷰가 데이터 개체를 받아들일 수 있는 경우 일반적으로 기본 삭제 효과입니다.

자세한 내용은 MFC 고급 개념 샘플 [OCLIENT](../../overview/visual-cpp-samples.md)를 참조 하세요.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행 하지 않고 DROPEFFECT_NONE을 반환 하는 것입니다.

끌기 작업을 수행 하는 동안 사용자에 게 시각적 피드백을 제공 하려면이 함수를 재정의 합니다. 이 함수는 지속적으로 호출 되기 때문에 포함 된 모든 코드는 가능한 한 최적화 되어야 합니다. 자세한 내용은 [OLE 끌어서 놓기: 놓기 대상 구현](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)문서를 참조 하세요.

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a> CView:: OnDragScroll

[System.windows.uielement.ondragenter](#ondragenter) 또는 [system.windows.uielement.ondragover](#ondragover) 를 호출 하 여 해당 지점이 스크롤 영역에 있는지 여부를 확인 하기 전에 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*dwKeyState*<br/>
보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.

*까지*<br/>
화면에 상대적인 커서 위치 (픽셀)를 포함 합니다.

### <a name="return-value"></a>반환 값

사용자가이 위치에서 개체를 삭제 한 경우 발생 하는 삭제 유형을 나타내는 DROPEFFECT 열거 형식의 값입니다. Drop 형식은 일반적으로 *Dwkeystate* 로 표시 되는 현재 키 상태에 따라 달라 집니다. DROPEFFECT 값에 대 한 keystates 표준 매핑은 다음과 같습니다.

- 이 창에서 데이터 개체를 삭제할 수 DROPEFFECT_NONE.

- MK_CONTROL &#124;에 대 한 DROPEFFECT_LINK MK_SHIFT 개체와 해당 서버 간의 링크를 만듭니다.

- MK_CONTROL에 대 한 DROPEFFECT_COPY는 삭제 된 개체의 복사본을 만듭니다.

- MK_ALT에 대 한 DROPEFFECT_MOVE는 삭제 된 개체의 복사본을 만들고 원래 개체를 삭제 합니다.

- DROPEFFECT_SCROLL는 끌기 스크롤 작업이 대상 뷰에서 발생 하거나 발생 하 고 있음을 나타냅니다.

자세한 내용은 MFC 고급 개념 샘플 [OCLIENT](../../overview/visual-cpp-samples.md)를 참조 하세요.

### <a name="remarks"></a>설명

이 이벤트에 특별 한 동작을 제공 하려는 경우이 함수를 재정의 합니다. 기본 구현은 각 창의 테두리 안쪽에 있는 기본 스크롤 영역으로 커서를 끌 때 자동으로 창을 스크롤합니다. 자세한 내용은 [OLE 끌어서 놓기: 놓기 대상 구현](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)문서를 참조 하세요.

## <a name="cviewondraw"></a><a name="ondraw"></a> CView:: OnDraw

문서 이미지를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
문서 이미지를 렌더링 하는 데 사용할 장치 컨텍스트를 가리킵니다.

### <a name="remarks"></a>설명

프레임 워크는 화면 표시, 인쇄 및 인쇄 미리 보기를 수행 하기 위해이 함수를 호출 하 고 각 경우에 다른 장치 컨텍스트를 전달 합니다. 기본 구현은 없습니다.

문서 보기를 표시 하려면이 함수를 재정의 해야 합니다. *PDC* 매개 변수가 가리키는 [CDC](../../mfc/reference/cdc-class.md) 개체를 사용 하 여 GDI (그래픽 장치 인터페이스) 호출을 만들 수 있습니다. 그리기 전에 GDI 리소스 (예: 펜 또는 글꼴)를 장치 컨텍스트로 선택한 후 나중에 선택 취소할 수 있습니다. 일반적으로 그리기 코드는 장치 독립적 일 수 있습니다. 즉, 이미지를 표시 하는 장치 유형에 대 한 정보가 필요 하지 않습니다.

그리기를 최적화 하려면 장치 컨텍스트의 [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) 멤버 함수를 호출 하 여 지정 된 사각형을 그릴지 여부를 확인 합니다. 일반 화면 표시와 인쇄를 구분 해야 하는 경우 장치 컨텍스트의 [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) 멤버 함수를 호출 합니다.

## <a name="cviewondrop"></a><a name="ondrop"></a> CView:: OnDrop

사용자가 유효한 놓기 대상에 대해 데이터 개체를 해제할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

' pDataObject *는 놓기 대상에 놓을 [Coledataobject](../../mfc/reference/coledataobject-class.md) 를 가리킵니다.

*dropEffect*<br/>
사용자가 요청한 삭제 효과입니다.

- DROPEFFECT_COPY은 삭제 되는 데이터 개체의 복사본을 만듭니다.

- DROPEFFECT_MOVE 데이터 개체를 현재 마우스 위치로 이동 합니다.

- DROPEFFECT_LINK는 데이터 개체와 해당 서버 간에 링크를 만듭니다.

*까지*<br/>
뷰 클라이언트 영역을 기준으로 하는 현재 마우스 위치입니다.

### <a name="return-value"></a>반환 값

삭제에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행 하지 않으며 FALSE를 반환 합니다.

뷰의 클라이언트 영역에 OLE drop 효과를 구현 하려면이 함수를 재정의 합니다. 클립보드 데이터 형식 및 지정 된 지점에서 삭제 된 데이터에 대해 *Pdataobject* 를 통해 데이터 개체를 검사할 수 있습니다.

> [!NOTE]
> 이 뷰 클래스에 [Ondropex](#ondropex) 에 대 한 재정의가 있는 경우 프레임 워크는이 함수를 호출 하지 않습니다.

## <a name="cviewondropex"></a><a name="ondropex"></a> CView:: OnDropEx

사용자가 유효한 놓기 대상에 대해 데이터 개체를 해제할 때 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pDataObject*<br/>
놓기 대상에 놓을 [Coledataobject](../../mfc/reference/coledataobject-class.md) 를 가리킵니다.

*dropDefault*<br/>
사용자가 현재 키 상태를 기준으로 기본 drop 작업에 대해 선택한 효과입니다. DROPEFFECT_NONE 수 있습니다. Drop 효과는 설명 섹션에 설명 되어 있습니다.

*dropList*<br/>
Drop 소스가 지 원하는 drop 효과 목록입니다. 놓기 효과 값은 비트 OR ( **&#124;**) 연산을 사용 하 여 결합할 수 있습니다. Drop 효과는 설명 섹션에 설명 되어 있습니다.

*까지*<br/>
뷰 클라이언트 영역을 기준으로 하는 현재 마우스 위치입니다.

### <a name="return-value"></a>반환 값

*Point* 로 지정 된 위치에서 삭제 시도로 인해 발생 하는 낙하 효과입니다. 이 값은 *dropEffectList* 에 지정 된 값 중 하나 여야 합니다. Drop 효과는 설명 섹션에 설명 되어 있습니다.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행 하지 않고 더미 값 (-1)을 반환 하 여 프레임 워크에서 [Ondrop](#ondrop) 처리기를 호출 해야 함을 나타내는 것입니다.

마우스 오른쪽 단추 끌어서 놓기의 효과를 구현 하려면이 함수를 재정의 합니다. 마우스 오른쪽 단추 끌어서 놓기는 일반적으로 마우스 오른쪽 단추를 놓을 때 선택할 수 있는 메뉴를 표시 합니다.

의 재정의는 마우스 `OnDropEx` 오른쪽 단추를 쿼리해야 합니다. [Getkeystate](/windows/win32/api/winuser/nf-winuser-getkeystate) 를 호출 하거나 [system.windows.uielement.ondragenter](#ondragenter) 처리기에서 오른쪽 마우스 단추 상태를 저장할 수 있습니다.

- 마우스 오른쪽 단추를 누른 경우에는 삭제 원본에의 한 놓기 효과 지원을 제공 하는 팝업 메뉴가 재정의에 표시 되어야 합니다.

  - *DropList* 를 검사 하 여 놓기 원본에서 지 원하는 놓기 효과를 확인 합니다. 팝업 메뉴 에서만 이러한 작업을 사용 하도록 설정 합니다.

  - [Setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) 을 사용 하 여 *dropdefault* 를 기준으로 기본 동작을 설정 합니다.

  - 마지막으로 팝업 메뉴에서 사용자 선택에 표시 된 작업을 수행 합니다.

- 마우스 오른쪽 단추를 다운 하지 않으면 재정의에서이를 표준 drop 요청으로 처리 해야 합니다. *Dropdefault* 에 지정 된 drop 효과를 사용 합니다. 또는 재정의에서 더미 값 (-1)을 반환 하 여이 drop 작업을 처리 함을 나타낼 수 있습니다 `OnDrop` .

*Pdataobject* 를 사용 하 여 `COleDataObject` 지정 된 지점에서 삭제 된 클립보드 데이터 형식 및 데이터를 검사 합니다.

Drop effects는 drop 작업과 관련 된 동작을 설명 합니다. 다음 drop effects 목록을 참조 하십시오.

- Drop을 사용할 수 DROPEFFECT_NONE.

- DROPEFFECT_COPY 복사 작업이 수행 됩니다.

- DROPEFFECT_MOVE 이동 작업이 수행 됩니다.

- 끌어 놓은 데이터에서 원래 데이터로의 링크를 설정 DROPEFFECT_LINK 합니다.

- DROPEFFECT_SCROLL는 끌기 스크롤 작업이 대상에서 발생 하거나 발생 하려고 함을 나타냅니다.

기본 메뉴 명령을 설정 하는 방법에 대 한 자세한 내용은 Windows SDK의 [Setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) 및이 볼륨의 [CMenu:: GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) 을 참조 하세요.

## <a name="cviewonendprinting"></a><a name="onendprinting"></a> CView:: OnEndPrinting

문서를 인쇄 하거나 미리 본 후 프레임 워크에서 호출 됩니다.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
프린터 디바이스 컨텍스트를 가리킵니다.

*pInfo*<br/>
현재 인쇄 작업을 설명하는 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 구조체를 가리킵니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 아무 작업도 수행하지 않습니다. [Onbeginprinting](#onbeginprinting) 멤버 함수에서 할당 한 모든 GDI 리소스를 해제 하려면이 함수를 재정의 합니다.

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a> CView:: OnEndPrintPreview

사용자가 인쇄 미리 보기 모드를 종료할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
프린터 디바이스 컨텍스트를 가리킵니다.

*pInfo*<br/>
현재 인쇄 작업을 설명하는 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 구조체를 가리킵니다.

*까지*<br/>
페이지에서 미리 보기 모드에 마지막으로 표시 된 지점을 지정 합니다.

*pView*<br/>
미리 보기에 사용 되는 뷰 개체를 가리킵니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 [OnEndPrinting](#onendprinting) 멤버 함수를 호출 하 고 주 프레임 창을 인쇄 미리 보기가 시작 되기 전의 상태로 복원 합니다. 미리 보기 모드가 종료 될 때 특수 처리를 수행 하려면이 함수를 재정의 합니다. 예를 들어 미리 보기 모드에서 일반 디스플레이 모드로 전환할 때 문서에서 사용자의 위치를 유지 하려면 *point* 매개 변수 및 `m_nCurPage` `CPrintInfo` *pinfo* 매개 변수가 가리키는 구조체의 멤버에 설명 된 위치로 스크롤할 수 있습니다.

일반적으로 함수 끝의 재정의에서의 기본 클래스 버전을 항상 호출 `OnEndPrintPreview` 합니다.

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a> CView:: OnInitialUpdate

뷰가 문서에 처음 연결 된 후 뷰가 처음 표시 되기 전에 프레임 워크에서 호출 됩니다.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>설명

이 함수의 기본 구현은 힌트 정보 없이 [OnUpdate](#onupdate) 멤버 함수를 호출 합니다. 즉, *lhint* 매개 변수에 0의 기본값을 사용 하 고 *PHINT* 매개 변수에는 NULL을 사용 합니다. 문서에 대 한 정보를 필요로 하는 일회성 초기화를 수행 하려면이 함수를 재정의 합니다. 예를 들어 응용 프로그램에 고정 크기의 문서가 있는 경우이 함수를 사용 하 여 문서 크기에 따라 뷰의 스크롤 제한을 초기화할 수 있습니다. 응용 프로그램에서 가변 크기 문서를 지 원하는 경우 [OnUpdate](#onupdate) 를 사용 하 여 문서가 변경 될 때마다 스크롤 제한을 업데이트 합니다.

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a> CView:: OnPrepareDC

화면 표시에 대해 [OnDraw](#ondraw) 멤버 함수를 호출 하 고 인쇄 또는 인쇄 미리 보기 중에 각 페이지에 대해 [OnPrint](#onprint) 멤버 함수를 호출 하기 전에 프레임 워크에서 호출 됩니다.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
문서 이미지를 렌더링 하는 데 사용할 장치 컨텍스트를 가리킵니다.

*pInfo*<br/>
인쇄 또는 인쇄 미리 보기에 대해를 호출 하는 경우 현재 인쇄 작업을 설명 하는 [Cprintinfo](../../mfc/reference/cprintinfo-structure.md) 구조체를 가리킵니다. `OnPrepareDC` `m_nCurPage` 멤버는 인쇄할 페이지를 지정 합니다. `OnPrepareDC`가 화면 표시를 위해 호출 되는 경우이 매개 변수는 NULL입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 화면 표시를 위해 함수가 호출 되는 경우 아무 작업도 수행 하지 않습니다. 그러나이 함수는 장치 컨텍스트의 특성을 조정 하기 위해 [CScrollView](../../mfc/reference/cscrollview-class.md)와 같은 파생 클래스에서 재정의 됩니다. 따라서 재정의를 시작할 때 항상 기본 클래스 구현을 호출 해야 합니다.

인쇄를 위해 함수가 호출 되는 경우 기본 구현은 *Pinfo* 매개 변수에 저장 된 페이지 정보를 검사 합니다. 문서의 길이가 지정 되지 않은 경우 `OnPrepareDC` 은 문서를 한 페이지 길게 가정 하 고 한 페이지가 인쇄 된 후 인쇄 루프를 중지 합니다. 함수는 `m_bContinuePrinting` 구조체의 멤버를 FALSE로 설정 하 여 인쇄 루프를 중지 합니다.

`OnPrepareDC`다음과 같은 이유로를 재정의 합니다.

- 지정 된 페이지에 대 한 필요에 따라 장치 컨텍스트의 특성을 조정 합니다. 예를 들어 장치 컨텍스트의 매핑 모드나 기타 특성을 설정 해야 하는 경우이 함수에서이 작업을 수행 합니다.

- 인쇄 시간 페이지 매김을 수행 하려면입니다. 일반적으로 인쇄를 시작할 때 [Onprepareprinting](#onprepareprinting) 멤버 함수를 사용 하 여 문서의 길이를 지정 합니다. 그러나 문서를 미리 알 수 없는 경우 (예를 들어 데이터베이스에서 레코드 수를 확인 하는 경우) 문서를 인쇄 하는 `OnPrepareDC` 동안 문서의 끝을 테스트 하도록를 재정의 합니다. 인쇄할 문서가 더 이상 없으면 `m_bContinuePrinting` 구조체의 멤버를 `CPrintInfo` FALSE로 설정 합니다.

- 페이지 별로 프린터에 이스케이프 코드를 전송 하는 것을 말합니다. 에서 이스케이프 코드를 보내려면 `OnPrepareDC` `Escape` *pDC* 매개 변수의 멤버 함수를 호출 합니다.

재정의를 시작할 때의 기본 클래스 버전을 호출 `OnPrepareDC` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a> CView:: OnPreparePrinting

문서를 인쇄 하거나 미리 보기 전에 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>매개 변수

*pInfo*<br/>
현재 인쇄 작업을 설명하는 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

0이 아니면 인쇄를 시작 합니다. 인쇄 작업이 취소 된 경우 0입니다.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행하지 않습니다.

인쇄 및 인쇄 미리 보기를 사용 하도록 설정 하려면이 함수를 재정의 해야 합니다. [Doprepareprinting](#doprepareprinting) 멤버 함수를 호출 하 고 *pinfo* 매개 변수를 전달한 다음 반환 값을 반환 합니다. `DoPreparePrinting`인쇄 대화 상자를 표시 하 고 프린터 장치 컨텍스트를 만듭니다. 기본값 이외의 값을 사용 하 여 인쇄 대화 상자를 초기화 하려면 *Pinfo* 의 멤버에 값을 할당 합니다. 예를 들어 문서의 길이를 알고 있는 경우를 호출 하기 전에 *Pinfo* 의 [setmaxpage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) 멤버 함수에 값을 전달 `DoPreparePrinting` 합니다. 이 값은 인쇄 대화 상자의 범위 부분에 있는 끝: 상자에 표시 됩니다.

`DoPreparePrinting` 미리 보기 작업에 대 한 인쇄 대화 상자를 표시 하지 않습니다. 인쇄 작업에 대 한 인쇄 대화 상자를 무시 하려면 `m_bPreview` *pinfo* 의 멤버가 FALSE 인지 확인 하 고,이를에 전달 하기 전에 TRUE로 설정 하 고 `DoPreparePrinting` 나중에 false로 다시 설정 합니다.

프린터 장치 컨텍스트를 나타내는 개체에 액세스 해야 하는 초기화를 수행 해야 하는 경우 `CDC` (예: 문서의 길이를 지정 하기 전에 페이지 크기를 확인 해야 하는 경우) 멤버 함수를 재정의 `OnBeginPrinting` 합니다.

`m_nNumPreviewPages` `m_strPageDesc` *Pinfo* 매개 변수의 또는 멤버 값을 설정 하려면를 호출한 후이 작업을 수행 `DoPreparePrinting` 합니다. `DoPreparePrinting`멤버 함수는 `m_nNumPreviewPages` 을 응용 프로그램의에 있는 값으로 설정 합니다. INI 파일을 만들고 `m_strPageDesc` 를 기본값으로 설정 합니다.

### <a name="example"></a>예제

  `OnPreparePrinting` `DoPreparePrinting` 프레임 워크에서 인쇄 대화 상자를 표시 하 고 프린터 DC를 만들도록 재정의를 재정의 하 고 재정의를 호출 합니다.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

문서에 포함 된 페이지 수를 알고 있는 경우를 호출 하기 전에에서 최대 페이지를 설정 `OnPreparePrinting` `DoPreparePrinting` 합니다. 프레임 워크에서는 인쇄 대화 상자의 "대상" 상자에 최대 페이지 번호를 표시 합니다.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a> CView:: OnPrint

문서 페이지를 인쇄 하거나 미리 보기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
프린터 디바이스 컨텍스트를 가리킵니다.

*pInfo*<br/>
`CPrintInfo`현재 인쇄 작업을 설명 하는 구조체를 가리킵니다.

### <a name="remarks"></a>설명

출력 되는 각 페이지에 대해 프레임 워크는 [Onpreparedc](#onpreparedc) 멤버 함수를 호출한 직후이 함수를 호출 합니다. 출력 되는 페이지는 `m_nCurPage` *pinfo* 가 가리키는 [cprintinfo](../../mfc/reference/cprintinfo-structure.md) 구조체의 멤버에 의해 지정 됩니다. 기본 구현에서는 [OnDraw](#ondraw) 멤버 함수를 호출 하 고이를 프린터 장치 컨텍스트로 전달 합니다.

다음과 같은 이유로이 함수를 재정의 합니다.

- 다중 페이지 문서 인쇄를 허용 합니다. 현재 인쇄 중인 페이지에 해당 하는 문서 부분만 렌더링 합니다. 를 사용 하 여 렌더링을 수행 하는 경우 `OnDraw` 문서에서 적절 한 부분만 인쇄 되도록 뷰포트 원본을 조정할 수 있습니다.

- 인쇄 된 이미지가 화면 이미지와 다르게 보이도록 (즉, 응용 프로그램이 WYSIWYG가 아닌 경우). 에 프린터 장치 컨텍스트를 전달 하는 대신 `OnDraw` 장치 컨텍스트를 사용 하 여 화면에 표시 되지 않은 특성을 사용 하 여 이미지를 렌더링 합니다.

   화면 표시에 사용 하지 않는 인쇄용 GDI 리소스가 필요한 경우 그리기 전에 장치 컨텍스트로 선택 하 고 나중에 선택 취소 합니다. 이러한 GDI 리소스는 [Onbeginprinting](#onbeginprinting) 에 할당 되 고 [OnEndPrinting](#onendprinting)에서 해제 되어야 합니다.

- 머리글 또는 바닥글을 구현 합니다. `OnDraw`에서 인쇄할 수 있는 영역을 제한 하 여 렌더링을 수행 하는 데에도를 사용할 수 있습니다.

`m_rectDraw` *Pinfo* 매개 변수의 멤버는 논리적 단위로 페이지의 인쇄 가능한 영역을 설명 합니다.

재정의에서를 호출 하지 마세요 `OnPrepareDC` `OnPrint` . 프레임 워크는를 `OnPrepareDC` 호출 하기 전에를 자동으로 호출 `OnPrint` 합니다.

### <a name="example"></a>예제

다음은 재정의 된 함수에 대 한 기본 구조입니다 `OnPrint` .

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

다른 예는 [CRichEditView::P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect)를 참조 하세요.

## <a name="cviewonscroll"></a><a name="onscroll"></a> CView:: OnScroll

스크롤이 가능한 지 여부를 확인 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>매개 변수

*nScrollCode*<br/>
사용자의 스크롤 요청을 나타내는 스크롤 막대 코드입니다. 이 매개 변수는 두 부분으로 구성 됩니다. 즉, 가로로 발생 하는 스크롤의 유형을 결정 하는 하위 바이트와 세로로 발생 하는 스크롤의 유형을 결정 하는 상위 바이트입니다.

- SB_BOTTOM 아래쪽으로 스크롤됩니다.

- SB_LINEDOWN 한 줄 아래로 스크롤합니다.

- SB_LINEUP 한 줄 위로 스크롤합니다.

- SB_PAGEDOWN 한 페이지 아래로 스크롤합니다.

- SB_PAGEUP 한 페이지를 위로 스크롤합니다.

- 스크롤 상자를 지정한 위치로 끕니다 SB_THUMBTRACK 합니다. 현재 위치는 *Npos* 에 지정 됩니다.

- SB_TOP 맨 위로 스크롤합니다.

*nPos*<br/>
스크롤 막대 코드가 SB_THUMBTRACK 경우 현재 스크롤 상자 위치를 포함 합니다. 그렇지 않은 경우에는 사용 되지 않습니다. 초기 스크롤 범위에 따라 *Npos* 는 음수일 수 있으며 필요한 경우로 캐스팅 해야 합니다 **`int`** .

*bDoScroll*<br/>
지정 된 스크롤 동작을 실제로 수행할지 여부를 결정 합니다. TRUE 이면 스크롤이 수행 됩니다. FALSE 이면 스크롤이 발생 하지 않아야 합니다.

### <a name="return-value"></a>반환 값

*Bdoscroll* 이 TRUE이 고 뷰가 실제로 스크롤 된 경우 0이 아닌 값을 반환 합니다. 그렇지 않으면 0입니다. *Bdoscroll* 이 FALSE 인 경우 실제로 스크롤이 수행 되지 않더라도 *BDOSCROLL* 이 TRUE 일 경우 반환 된 값을 반환 합니다.

### <a name="remarks"></a>설명

이 함수는 뷰가 스크롤 막대 메시지를 받을 때 *Bdoscroll* 이 TRUE로 설정 된 프레임 워크에서 호출 됩니다. 이 경우 실제로 뷰를 스크롤해야 합니다. 다른 경우에는 스크롤이 실제로 수행 되기 전에 OLE 항목을 놓기 대상의 자동 스크롤 영역으로 처음 끌 때 *Bdoscroll* 을 FALSE로 설정 하 여이 함수를 호출 합니다. 이 경우 실제로 뷰를 스크롤해야 하는 것은 아닙니다.

## <a name="cviewonscrollby"></a><a name="onscrollby"></a> CView:: OnScrollBy

사용자가 보기의 현재 테두리를 기준으로 OLE 항목을 끌거나 세로 또는 가로 스크롤 막대를 조작 하 여 문서의 현재 보기를 벗어난 영역을 볼 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>매개 변수

*sizeScroll*<br/>
가로 및 세로로 스크롤 된 픽셀 수입니다.

*bDoScroll*<br/>
뷰의 스크롤이 발생 하는지 여부를 결정 합니다. TRUE 이면 스크롤이 수행 됩니다. FALSE 이면 스크롤이 수행 되지 않습니다.

### <a name="return-value"></a>반환 값

뷰를 스크롤할 수 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

파생 된 클래스에서이 메서드는 뷰가 사용자가 요청한 방향으로 스크롤할 수 있는지 여부를 확인 한 다음 필요한 경우 새 영역을 업데이트 합니다. 이 함수는 실제 스크롤 요청을 수행 하기 위해 [cwnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) 및 [Cwnd:: onhscroll](../../mfc/reference/cwnd-class.md#onvscroll) 에서 자동으로 호출 됩니다.

이 메서드의 기본 구현에서는 뷰를 변경 하지 않지만 호출 하지 않는 경우 뷰는 파생 클래스에서 스크롤되지 않습니다 `CScrollView` .

문서 너비 또는 높이가 32767 픽셀을 초과 하는 경우 `OnScrollBy` 이 잘못 된 *sizeScroll* 인수를 사용 하 여 호출 되므로 32767 이전 스크롤은 실패 합니다.

## <a name="cviewonupdate"></a><a name="onupdate"></a> CView:: OnUpdate

뷰의 문서가 수정 된 후 프레임 워크에서 호출 됩니다. 이 함수는 [CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) 에 의해 호출 되며, 뷰에서 해당 수정 내용을 반영 하도록 표시를 업데이트할 수 있습니다.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>매개 변수

*pSender*<br/>
문서를 수정한 뷰를 가리키거나 모든 뷰를 업데이트할 경우 NULL입니다.

*lHint*<br/>
수정 내용에 대 한 정보를 포함 합니다.

*pHint*<br/>
수정 내용에 대 한 정보를 저장 하는 개체를 가리킵니다.

### <a name="remarks"></a>설명

이는 [Oninitialupdate](#oninitialupdate)의 기본 구현에 의해도 호출 됩니다. 기본 구현에서는 전체 클라이언트 영역을 무효화 하 고 다음 WM_PAINT 메시지가 수신 될 때 그리기를 위해 표시 합니다. 문서의 수정 된 부분에 매핑되는 영역만 업데이트 하려면이 함수를 재정의 합니다. 이렇게 하려면 힌트 매개 변수를 사용 하 여 수정 내용에 대 한 정보를 전달 해야 합니다.

*Lhint* 를 사용 하려면 특정 힌트 값 (일반적으로 비트 마스크 또는 열거 형식)을 정의 하 고 문서에서 다음 값 중 하나를 전달 하도록 합니다. *Phint* 를 사용 하려면 [CObject](../../mfc/reference/cobject-class.md) 에서 힌트 클래스를 파생 시키고 문서에서 힌트 개체에 대 한 포인터를 전달 하도록 합니다. 재정의할 때 `OnUpdate` [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) 멤버 함수를 사용 하 여 힌트 개체의 런타임 형식을 확인 합니다.

일반적으로에서 직접 그리기를 수행 하면 안 `OnUpdate` 됩니다. 대신, 장치 좌표에서 업데이트를 필요로 하는 영역을 설명 하는 사각형을 결정 합니다. 이 사각형을 [CWnd:: InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)에 전달 합니다. 이렇게 하면 다음에 [WM_PAINT](/windows/win32/gdi/wm-paint) 메시지가 수신 될 때 그리기가 발생 합니다.

*Lhint* 가 0이 고 *PHINT* 가 NULL 이면 문서에서 일반 업데이트 알림을 보냈습니다. 뷰가 일반 업데이트 알림을 받거나 힌트를 디코딩할 수 없는 경우 전체 클라이언트 영역을 무효화 해야 합니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd 클래스](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC 클래스](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 클래스](../../mfc/reference/cdocument-class.md)
