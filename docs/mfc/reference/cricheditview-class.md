---
description: '자세히 알아보기: CRichEditView 클래스'
title: CRichEditView 클래스
ms.date: 11/04/2016
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
ms.openlocfilehash: cf5c504058332b652023d746aaadb0c8c80fccce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264767"
---
# <a name="cricheditview-class"></a>CRichEditView 클래스

[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) 및 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)를 사용 하면 MFC의 문서 뷰 아키텍처 컨텍스트 내에서 rich edit 컨트롤의 기능을 제공 합니다.

## <a name="syntax"></a>구문

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRichEditView:: CRichEditView](#cricheditview)|`CRichEditView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRichEditView:: AdjustDialogPosition](#adjustdialogposition)|현재 선택 영역을 가리지 않도록 대화 상자를 이동 합니다.|
|[CRichEditView:: CanPaste](#canpaste)|Rich edit 뷰에 붙여 넣을 수 있는 데이터가 클립보드에 있는지 여부를 나타냅니다.|
|[CRichEditView::D oPaste](#dopaste)|이 rich edit 뷰에 OLE 항목을 붙여 넣습니다.|
|[CRichEditView:: FindText](#findtext)|대기 커서를 호출 하 여 지정 된 텍스트를 찾습니다.|
|[CRichEditView:: FindTextSimple](#findtextsimple)|지정 된 텍스트를 찾습니다.|
|[CRichEditView:: GetCharFormatSelection](#getcharformatselection)|현재 선택 영역에 대 한 문자 서식 특성을 검색 합니다.|
|[CRichEditView:: GetDocument](#getdocument)|관련 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)에 대 한 포인터를 검색 합니다.|
|[CRichEditView:: GetInPlaceActiveItem](#getinplaceactiveitem)|Rich edit 뷰에서 현재 활성 상태인 OLE 항목을 검색 합니다.|
|[CRichEditView:: GetMargins](#getmargins)|이 rich edit 뷰의 여백을 검색 합니다.|
|[CRichEditView:: GetPageRect](#getpagerect)|이 rich edit 뷰의 페이지 사각형을 검색 합니다.|
|[CRichEditView:: GetPaperSize](#getpapersize)|이 rich edit 보기의 용지 크기를 검색 합니다.|
|[CRichEditView:: GetParaFormatSelection](#getparaformatselection)|현재 선택 영역에 대 한 단락 서식 특성을 검색 합니다.|
|[CRichEditView:: GetPrintRect](#getprintrect)|이 rich edit 뷰의 인쇄 사각형을 검색 합니다.|
|[CRichEditView:: GetPrintWidth](#getprintwidth)|이 rich edit 뷰의 인쇄 너비를 검색 합니다.|
|[CRichEditView:: GetRichEditCtrl](#getricheditctrl)|Rich edit 컨트롤을 검색 합니다.|
|[CRichEditView:: GetSelectedItem](#getselecteditem)|Rich edit 뷰에서 선택한 항목을 검색 합니다.|
|[CRichEditView:: GetTextLength](#gettextlength)|Rich edit 뷰에서 텍스트의 길이를 검색 합니다.|
|[CRichEditView:: GetTextLengthEx](#gettextlengthex)|Rich edit 뷰의 문자 또는 바이트 수를 검색 합니다. 길이 결정 방법에 대 한 확장 된 플래그 목록입니다.|
|[CRichEditView:: Insertfil 개체](#insertfileasobject)|파일을 OLE 항목으로 삽입 합니다.|
|[CRichEditView:: InsertItem](#insertitem)|새 항목을 OLE 항목으로 삽입 합니다.|
|[CRichEditView:: IsRichEditFormat](#isricheditformat)|클립보드에 rich edit 또는 text 형식의 데이터가 포함 되어 있는지 여부를 나타냅니다.|
|[CRichEditView:: OnCharEffect](#onchareffect)|현재 선택 영역에 대 한 문자 서식을 설정/해제 합니다.|
|[CRichEditView:: OnParaAlign](#onparaalign)|단락의 맞춤을 변경 합니다.|
|[CRichEditView:: OnUpdateCharEffect](#onupdatechareffect)|문자 공용 멤버 함수에 대 한 명령 UI를 업데이트 합니다.|
|[CRichEditView:: OnUpdateParaAlign](#onupdateparaalign)|단락 public 멤버 함수에 대 한 명령 UI를 업데이트 합니다.|
|[CRichEditView::P rintInsideRect](#printinsiderect)|지정 된 사각형 내에서 지정 된 텍스트의 서식을 지정 합니다.|
|[CRichEditView::P rintPage](#printpage)|지정 된 페이지 내에서 지정 된 텍스트의 서식을 지정 합니다.|
|[CRichEditView:: SetCharFormat](#setcharformat)|현재 선택 영역에 대 한 문자 서식 특성을 설정 합니다.|
|[CRichEditView:: SetMargins](#setmargins)|이 rich edit 뷰의 여백을 설정 합니다.|
|[CRichEditView:: SetPaperSize](#setpapersize)|이 rich edit 보기의 용지 크기를 설정 합니다.|
|[CRichEditView:: SetParaFormat](#setparaformat)|현재 선택 영역에 대 한 단락 서식 특성을 설정 합니다.|
|[CRichEditView:: TextNotFound](#textnotfound)|컨트롤의 내부 검색 상태를 다시 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CRichEditView:: GetClipboardData](#getclipboarddata)|이 rich edit 뷰에서 범위에 대 한 클립보드 개체를 검색 합니다.|
|[CRichEditView:: GetContextMenu](#getcontextmenu)|마우스 오른쪽 단추를 클릭 하 여 사용할 상황에 맞는 메뉴를 검색 합니다.|
|[CRichEditView:: IsSelected](#isselected)|지정 된 OLE 항목이 선택 되었는지 여부를 나타냅니다.|
|[CRichEditView:: OnFindNext](#onfindnext)|하위 문자열의 다음 항목을 찾습니다.|
|[CRichEditView:: OnInitialUpdate](#oninitialupdate)|문서에 처음 연결 될 때 보기를 새로 고칩니다.|
|[CRichEditView:: OnPasteNativeObject](#onpastenativeobject)|OLE 항목에서 네이티브 데이터를 검색 합니다.|
|[CRichEditView:: On프린터 변경 됨](#onprinterchanged)|지정 된 장치에 인쇄 특성을 설정 합니다.|
|[CRichEditView:: OnReplaceAll](#onreplaceall)|지정 된 문자열의 모든 항목을 새 문자열로 바꿉니다.|
|[CRichEditView:: OnReplaceSel](#onreplacesel)|현재 선택 영역을 바꿉니다.|
|[CRichEditView:: OnTextNotFound](#ontextnotfound)|요청 된 텍스트를 찾을 수 없다는 사용자 알림을 처리 합니다.|
|[CRichEditView:: QueryAcceptData](#queryacceptdata)|의 데이터를 확인 `IDataObject` 하는 쿼리|
|[CRichEditView:: WrapChanged](#wrapchanged)|의 값을 기반으로 하 여이 rich edit 뷰의 대상 출력 장치를 조정 `m_nWordWrap` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CRichEditView:: m_nBulletIndent](#m_nbulletindent)|글머리 기호 목록의 들여쓰기 크기를 나타냅니다.|
|[CRichEditView:: m_nWordWrap](#m_nwordwrap)|자동 줄 바꿈 제약 조건을 나타냅니다.|

## <a name="remarks"></a>설명

"Rich edit 컨트롤"은 사용자가 텍스트를 입력 하 고 편집할 수 있는 창입니다. 텍스트에는 문자 및 단락 서식 지정이 할당 될 수 있으며 포함 된 OLE 개체도 포함 될 수 있습니다. Rich edit 컨트롤은 텍스트 서식 지정을 위한 프로그래밍 인터페이스를 제공 합니다. 그러나 응용 프로그램은 사용자가 서식 지정 작업을 사용 하도록 설정 하는 데 필요한 모든 사용자 인터페이스 구성 요소를 구현 해야 합니다.

`CRichEditView` 텍스트의 텍스트와 서식 특성을 유지 합니다. `CRichEditDoc` 뷰에 있는 OLE 클라이언트 항목의 목록을 유지 관리 합니다. `CRichEditCntrItem` OLE 클라이언트 항목에 대 한 컨테이너 쪽 액세스를 제공 합니다.

이 Windows 공용 컨트롤 (및 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 및 관련 클래스)은 windows 95/98 및 windows NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

MFC 응용 프로그램에서 rich edit 뷰를 사용 하는 예제는 [워드 패드](../../overview/visual-cpp-samples.md) 샘플 응용 프로그램을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>요구 사항

**헤더:** afxrich

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a> CRichEditView:: AdjustDialogPosition

현재 선택 영역을 가리지 않도록 지정 된 대화 상자를 이동 하려면이 함수를 호출 합니다.

```cpp
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>매개 변수

*pDlg*<br/>
`CDialog` 개체에 대한 포인터입니다.

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a> CRichEditView:: CanPaste

이 함수를 호출 하 여이 rich edit 뷰에 붙여 넣을 수 있는 정보가 클립보드에 포함 되어 있는지 여부를 확인 합니다.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>반환 값

이 rich edit 보기가 허용할 수 있는 형식의 데이터가 클립보드에 포함 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a> CRichEditView:: CRichEditView

개체를 만들려면이 함수를 호출 `CRichEditView` 합니다.

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a> CRichEditView::D oPaste

이 함수를 호출 하 여 *dataobj* 의 OLE 항목을 rich edit document/view에 붙여넣습니다.

```cpp
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>매개 변수

*dataobj*<br/>
붙여넣을 데이터를 포함 하는 [Coledataobject](../../mfc/reference/coledataobject-class.md) 입니다.

*f*<br/>
원하는 클립보드 형식입니다.

*hMetaPict*<br/>
붙여 넣을 항목을 나타내는 메타 파일입니다.

### <a name="remarks"></a>설명

프레임 워크는 [Queryacceptdata](#queryacceptdata)의 기본 구현에서이 함수를 호출 합니다.

이 함수는 붙여넣기에 대 한 처리기 결과에 따라 붙여넣기 유형을 결정 합니다. *Cf* 가 0 이면 새 항목은 현재 아이콘 표현을 사용 합니다. *Cf* 가 0이 아니고 *hMetaPict* 가 NULL이 아닌 경우 새 항목은 표현에 *hMetaPict* 을 사용 합니다.

## <a name="cricheditviewfindtext"></a><a name="findtext"></a> CRichEditView:: FindText

지정 된 텍스트를 찾고 현재 선택 항목으로 설정 하려면이 함수를 호출 합니다.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszFind*<br/>
검색할 문자열을 포함 합니다.

*bCase*<br/>
검색에서 대/소문자를 구분 하는지 여부를 나타냅니다.

*bWord*<br/>
검색에서 단어의 일부가 아니라 전체 단어만 일치 하는지 여부를 나타냅니다.

*bNext*<br/>
검색 방향을 나타냅니다. TRUE 이면 검색 방향이 버퍼의 끝 부분에 있습니다. FALSE 이면 검색 방향이 버퍼의 시작 부분을 향해 있습니다.

### <a name="return-value"></a>반환 값

*LpszFind* 텍스트가 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 찾기 작업 중에 대기 커서를 표시 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a> CRichEditView:: FindTextSimple

지정 된 텍스트를 찾고 현재 선택 항목으로 설정 하려면이 함수를 호출 합니다.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszFind*<br/>
검색할 문자열을 포함 합니다.

*bCase*<br/>
검색에서 대/소문자를 구분 하는지 여부를 나타냅니다.

*bWord*<br/>
검색에서 단어의 일부가 아니라 전체 단어만 일치 하는지 여부를 나타냅니다.

*bNext*<br/>
검색 방향을 나타냅니다. TRUE 이면 검색 방향이 버퍼의 끝 부분에 있습니다. FALSE 이면 검색 방향이 버퍼의 시작 부분을 향해 있습니다.

### <a name="return-value"></a>반환 값

*LpszFind* 텍스트가 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CRichEditView:: FindText](#findtext)의 예제를 참조 하세요.

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a> CRichEditView:: GetCharFormatSelection

현재 선택 영역의 문자 서식 특성을 가져오려면이 함수를 호출 합니다.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>반환 값

현재 선택 영역의 문자 서식 특성을 포함 하는 [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) 구조체입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) 메시지 및 [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) 구조를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a> CRichEditView:: GetClipboardData

프레임 워크는 [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)를 처리 하는 과정의 일부로이 함수를 호출 합니다.

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>매개 변수

*lpchrg*<br/>
*Lplpdataobj* 로 지정 된 데이터 개체에 복사할 문자 범위 (및 OLE 항목)를 지정 하는 [charrange](/windows/win32/api/richedit/ns-richedit-charrange) 구조에 대 한 포인터입니다.

*Dwo*<br/>
클립보드 작업 플래그입니다. 는 다음 값 중 하나일 수 있습니다.

- 클립보드로 복사를 RECO_COPY 합니다.

- RECO_CUT 클립보드로 잘라냅니다.

- RECO_DRAG 끌기 작업 (끌어서 놓기)

- 끌어서 놓기 작업을 RECO_DROP 합니다.

- 클립보드에서 붙여넣기를 RECO_PASTE 합니다.

*lpRichDataObj*<br/>
Rich edit 컨트롤의 클립보드 데이터를 포함 하는 [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 개체에 대 한 포인터입니다 ( [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
`IDataObject` *Lpchrg* 매개 변수에 지정 된 범위를 나타내는 개체의 주소를 받는 포인터 변수에 대 한 포인터입니다. 오류가 반환 되 면 *lplpdataobj* 의 값이 무시 됩니다.

### <a name="return-value"></a>반환 값

작업의 성공 여부를 보고 하는 HRESULT 값입니다. HRESULT에 대 한 자세한 내용은 Windows SDK의 [COM 오류 코드 구조](/windows/win32/com/structure-of-com-error-codes) 를 참조 하십시오.

### <a name="remarks"></a>설명

반환 값이 success를 나타내면 `IRichEditOleCallback::GetClipboardData` 는 `IDataObject` *lplpdataobj* 에 의해 액세스 되는를 반환 합니다. 그렇지 않으면 *lpRichDataObj* 에서 액세스 한를 반환 합니다. 사용자 고유의 클립보드 데이터를 제공 하려면이 함수를 재정의 합니다. 이 함수의 기본 구현은 E_NOTIMPL을 반환 합니다.

이는 고급 재정의 가능입니다.

자세한 내용은 Windows SDK에서 [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)및 [charrange](/windows/win32/api/richedit/ns-richedit-charrange) 를 참조 하 고 Windows SDK의 [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 를 참조 하십시오.

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a> CRichEditView:: GetContextMenu

프레임 워크는 [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)를 처리 하는 과정의 일부로이 함수를 호출 합니다.

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>매개 변수

*seltyp*<br/>
선택 유형입니다. 선택 유형 값은 설명 섹션에 설명 되어 있습니다.

*lpoleobj*<br/>
`OLEOBJECT`선택에 ole 항목이 하나 이상 포함 된 경우 선택한 첫 번째 ole 개체를 지정 하는 구조체에 대 한 포인터입니다. 선택 항목에 항목이 없으면 *lpoleobj* 가 NULL입니다. `OLEOBJECT`구조체는 OLE 개체 v-table에 대 한 포인터를 보유 합니다.

*lpchrg*<br/>
현재 선택 영역을 포함 하는 [Charrange](/windows/win32/api/richedit/ns-richedit-charrange) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

상황에 맞는 메뉴에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 함수는 마우스 오른쪽 단추 다운 처리의 일반적인 부분입니다.

선택 유형은 다음 플래그를 임의로 조합 하 여 사용할 수 있습니다.

- SEL_EMPTY 현재 선택 영역이 없음을 나타냅니다.

- SEL_TEXT 현재 선택에 텍스트가 포함 되어 있음을 나타냅니다.

- SEL_OBJECT 현재 선택에 하나 이상의 OLE 항목이 포함 되어 있음을 나타냅니다.

- SEL_MULTICHAR 현재 선택에 텍스트 문자가 둘 이상 포함 되어 있음을 나타냅니다.

- SEL_MULTIOBJECT 현재 선택에 OLE 개체가 둘 이상 포함 되어 있음을 나타냅니다.

기본 구현에서는 NULL을 반환 합니다. 이는 고급 재정의 가능입니다.

자세한 내용은 Windows SDK에서 [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) And [charrange](/windows/win32/api/richedit/ns-richedit-charrange) 를 참조 하십시오.

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a> CRichEditView:: GetDocument

이 뷰와 연결 된에 대 한 포인터를 가져오려면이 함수를 호출 `CRichEditDoc` 합니다.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>반환 값

개체와 연결 된 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) 개체에 대 한 포인터 `CRichEditView` 입니다.

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a> CRichEditView:: GetInPlaceActiveItem

이 함수를 호출 하 여이 개체에서 현재 활성화 된 OLE 항목을 가져옵니다 `CRichEditView` .

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>반환 값

Rich edit 뷰의 단일 내부 활성 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) 개체에 대 한 포인터입니다. 현재 내부 활성 상태인 OLE 항목이 없으면 NULL입니다.

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a> CRichEditView:: GetMargins

인쇄에 사용 되는 현재 여백을 검색 하려면이 함수를 호출 합니다.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>반환 값

MM_TWIPS 측정 된 인쇄에 사용 되는 여백입니다.

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a> CRichEditView:: GetPageRect

인쇄에 사용 되는 페이지의 크기를 가져오려면이 함수를 호출 합니다.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>반환 값

MM_TWIPS 측정 된 인쇄에 사용 되는 페이지의 범위입니다.

### <a name="remarks"></a>설명

이 값은 용지 크기를 기준으로 합니다.

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a> CRichEditView:: GetPaperSize

현재 용지 크기를 검색 하려면이 함수를 호출 합니다.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>반환 값

인쇄에 사용 되는 용지 크기 이며 MM_TWIPS 측정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a> CRichEditView:: GetParaFormatSelection

현재 선택 영역에 대 한 단락 서식 특성을 가져오려면이 함수를 호출 합니다.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>반환 값

현재 선택 영역에 대 한 단락 서식 특성을 포함 하는 [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) 구조체입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) 메시지 및 [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) 구조를 참조 하세요.

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a> CRichEditView:: GetPrintRect

페이지 사각형 내에서 인쇄 영역의 범위를 검색 하려면이 함수를 호출 합니다.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>반환 값

MM_TWIPS 측정 된 인쇄에 사용 되는 이미지 영역의 경계입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a> CRichEditView:: GetPrintWidth

인쇄 영역의 너비를 확인 하려면이 함수를 호출 합니다.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>반환 값

MM_TWIPS 측정 된 인쇄 영역의 너비입니다.

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a> CRichEditView:: GetRichEditCtrl

개체와 연결 된 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 개체를 검색 하려면이 함수를 호출 `CRichEditView` 합니다.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>반환 값

`CRichEditCtrl`이 뷰에 대 한 개체입니다.

### <a name="example"></a>예제

  [CRichEditView:: FindText](#findtext)의 예제를 참조 하세요.

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a> CRichEditView:: GetSelectedItem

이 함수를 호출 하 여 `CRichEditCntrItem` 이 개체에서 현재 선택 되어 있는 OLE 항목 (개체)을 검색 합니다 `CRichEditView` .

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>반환 값

개체에서 선택 된 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) 개체에 대 한 포인터 `CRichEditView` 입니다. 이 뷰에서 선택 된 항목이 없으면 NULL입니다.

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a> CRichEditView:: GetTextLength

이 함수를 호출 하 여이 개체에 있는 텍스트의 길이를 검색 `CRichEditView` 합니다.

```
long GetTextLength() const;
```

### <a name="return-value"></a>반환 값

이 개체에 있는 텍스트의 길이 `CRichEditView` 입니다.

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a> CRichEditView:: GetTextLengthEx

이 멤버 함수를 호출 하 여이 개체에 있는 텍스트의 길이를 계산 `CRichEditView` 합니다.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
텍스트 길이를 결정 하는 데 사용할 메서드를 지정 하는 값입니다. 이 멤버는 Windows SDK에 설명 된 [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) 의 flags 멤버에 나열 된 값 중 하나 이상이 될 수 있습니다.

*uCodePage*<br/>
변환에 대 한 코드 페이지 (ANSI 코드 페이지의 경우 CP_ACP, 유니코드의 경우 1200)

### <a name="return-value"></a>반환 값

편집 컨트롤의 문자 또는 바이트 수입니다. *DwFlags* 에 호환 되지 않는 플래그가 설정 된 경우이 멤버 함수는 E_INVALIDARG을 반환 합니다.

### <a name="remarks"></a>설명

`GetTextLengthEx` 텍스트의 길이를 결정 하는 추가 방법을 제공 합니다. Rich Edit 2.0 기능을 지원 합니다. 자세한 내용은 Windows SDK의 [Rich Edit Controls 정보](/windows/win32/Controls/about-rich-edit-controls) 를 참조 하세요.

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a> CRichEditView:: Insertfil 개체

이 함수를 호출 하 여 지정 된 파일 ( [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) 개체)을 rich edit 뷰에 삽입 합니다.

```cpp
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>매개 변수

*lpszFileName*<br/>
삽입할 파일의 이름을 포함 하는 문자열입니다.

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a> CRichEditView:: InsertItem

[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) 개체를 rich edit 뷰에 삽입 하려면이 함수를 호출 합니다.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
삽입할 항목에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

삽입의 성공 여부를 나타내는 HRESULT 값입니다.

### <a name="remarks"></a>설명

HRESULT에 대 한 자세한 내용은 Windows SDK의 [COM 오류 코드 구조](/windows/win32/com/structure-of-com-error-codes) 를 참조 하십시오.

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a> CRichEditView:: IsRichEditFormat

이 함수를 호출 하 여 *cf* 가 텍스트, 서식 있는 텍스트 또는 OLE 항목의 서식 있는 텍스트인 클립보드 형식 인지 확인 합니다.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>매개 변수

*f*<br/>
원하는 클립보드 형식입니다.

### <a name="return-value"></a>반환 값

*Cf* 가 서식 있는 편집 또는 텍스트 클립보드 형식이 면 0이 아닌 값입니다.

## <a name="cricheditviewisselected"></a><a name="isselected"></a> CRichEditView:: IsSelected

지정 된 OLE 항목이이 뷰에서 현재 선택 되어 있는지 확인 하려면이 함수를 호출 합니다.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>매개 변수

*pDocItem*<br/>
뷰의 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

개체가 선택 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

파생 된 뷰 클래스에 OLE 항목 선택 항목을 처리 하는 다른 메서드가 있는 경우이 함수를 재정의 합니다.

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a> CRichEditView:: m_nBulletIndent

목록에 있는 글머리 기호 항목의 들여쓰기입니다. 기본적으로 720 단위 이며 1/2 인치입니다.

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a> CRichEditView:: m_nWordWrap

이 rich edit 뷰의 자동 줄 바꿈 유형을 나타냅니다.

```
int m_nWordWrap;
```

### <a name="remarks"></a>설명

다음 값 중 하나입니다.

- `WrapNone` 자동 줄 바꿈이 없음을 나타냅니다.

- `WrapToWindow` 창의 너비를 기준으로 단어 잘림을 나타냅니다.

- `WrapToTargetDevice` 대상 장치의 특징을 기준으로 단어 잘림을 나타냅니다.

### <a name="example"></a>예제

  [CRichEditView:: WrapChanged](#wrapchanged)의 예제를 참조 하세요.

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a> CRichEditView:: OnCharEffect

현재 선택 영역에 대 한 문자 서식 효과를 전환 하려면이 함수를 호출 합니다.

```cpp
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>매개 변수

*dwMask*<br/>
현재 선택 영역에서 수정할 문자 서식 효과입니다.

*dwEffect*<br/>
설정/해제 하는 데 필요한 문자 서식 효과 목록입니다.

### <a name="remarks"></a>설명

이 함수를 호출할 때마다 현재 선택 항목에 대해 지정 된 서식 지정 효과가 설정/해제 됩니다.

*Dwmask* 및 *dwEffect* 매개 변수 및 해당 값에 대 한 자세한 내용은 Windows SDK [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) 의 해당 데이터 멤버를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a> CRichEditView:: OnFindNext

찾기/바꾸기 대화 상자에서 명령을 처리할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>매개 변수

*lpszFind*<br/>
찾을 문자열입니다.

*bNext*<br/>
검색할 방향: TRUE는 아래를 나타냅니다. FALSE, up.

*bCase*<br/>
검색에서 대/소문자를 구분 하는지 여부를 나타냅니다.

*bWord*<br/>
검색에서 전체 단어를 일치 시킬 것인지 여부를 나타냅니다.

### <a name="remarks"></a>설명

내에서 텍스트를 찾으려면이 함수를 호출 `CRichEditView` 합니다. 파생 된 뷰 클래스에 대 한 검색 특성을 변경 하려면이 함수를 재정의 합니다.

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a> CRichEditView:: OnInitialUpdate

뷰가 문서에 처음 연결 된 후 뷰가 처음 표시 되기 전에 프레임 워크에서 호출 됩니다.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>설명

이 함수의 기본 구현은 힌트 정보 없이 [CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate) 멤버 함수를 호출 합니다. 즉, *lhint* 매개 변수에 0의 기본값을 사용 하 고 *PHINT* 매개 변수에는 NULL을 사용 합니다. 문서에 대 한 정보를 필요로 하는 일회성 초기화를 수행 하려면이 함수를 재정의 합니다. 예를 들어 응용 프로그램에 고정 크기의 문서가 있는 경우이 함수를 사용 하 여 문서 크기에 따라 뷰의 스크롤 제한을 초기화할 수 있습니다. 응용 프로그램에서 가변 크기 문서를 지 원하는 경우에는 `OnUpdate` 를 사용 하 여 문서가 변경 될 때마다 스크롤 제한을 업데이트 합니다.

### <a name="example"></a>예제

  [CRichEditView:: m_nWordWrap](#m_nwordwrap)의 예제를 참조 하세요.

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a> CRichEditView:: OnPasteNativeObject

포함 된 항목에서 네이티브 데이터를 로드 하려면이 함수를 사용 합니다.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>매개 변수

*lpStg*<br/>
[IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

일반적으로에 대 한 [Colestreamfile](../../mfc/reference/colestreamfile-class.md) 을 만들어이 작업을 수행 `IStorage` 합니다. 는 `COleStreamFile` 데이터를 로드 하기 위해 라는 archive 및 [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) 에 연결할 수 있습니다.

이는 고급 재정의 가능입니다.

자세한 내용은 Windows SDK의 [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 를 참조 하세요.

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a> CRichEditView:: OnParaAlign

이 함수를 호출 하 여 선택한 단락의 단락 맞춤을 변경 합니다.

```cpp
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>매개 변수

*wAlign*<br/>
원하는 단락 맞춤입니다. 다음 값 중 하나입니다.

- 단락을 왼쪽 여백 PFA_LEFT 맞춥니다.

- 단락을 오른쪽 여백 PFA_RIGHT 맞춥니다.

- 여백 사이에 단락을 가운데 PFA_CENTER 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a> CRichEditView:: On프린터 변경 됨

프린터가 변경 될 때이 rich edit 보기의 특징을 변경 하려면이 함수를 재정의 합니다.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>매개 변수

*dcPrinter*<br/>
새 프린터에 대 한 [CDC](../../mfc/reference/cdc-class.md) 개체입니다.

### <a name="remarks"></a>설명

기본 구현에서는 용지 크기를 출력 장치 (프린터)의 실제 높이 및 너비로 설정 합니다. *Dcprinter* 와 연결 된 장치 컨텍스트가 없는 경우 기본 구현에서는 용지 크기를 8.5 x 11 인치로 설정 합니다.

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a> CRichEditView:: OnReplaceAll

바꾸기 대화 상자에서 모든 명령 바꾸기를 처리할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>매개 변수

*lpszFind*<br/>
바꿀 텍스트입니다.

*lpszReplace*<br/>
대체 텍스트입니다.

*bCase*<br/>
검색에서 대/소문자를 구분 하는지 여부를 나타냅니다.

*bWord*<br/>
검색에서 단어 단위로 선택 해야 하는지 여부를 나타냅니다.

### <a name="remarks"></a>설명

지정 된 텍스트의 모든 항목을 다른 문자열로 바꾸려면이 함수를 호출 합니다. 이 뷰에 대 한 검색 특성을 변경 하려면이 함수를 재정의 합니다.

### <a name="example"></a>예제

  [CRichEditView:: FindText](#findtext)의 예제를 참조 하세요.

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a> CRichEditView:: OnReplaceSel

바꾸기 대화 상자에서 바꾸기 명령을 처리할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>매개 변수

*lpszFind*<br/>
바꿀 텍스트입니다.

*bNext*<br/>
검색 방향을 나타냅니다. TRUE가 눌러져 있습니다. FALSE, up.

*bCase*<br/>
검색에서 대/소문자를 구분 하는지 여부를 나타냅니다.

*bWord*<br/>
검색에서 단어 단위로 선택 해야 하는지 여부를 나타냅니다.

*lpszReplace*<br/>
대체 텍스트입니다.

### <a name="remarks"></a>설명

지정 된 특정 텍스트의 한 항목을 다른 문자열로 바꾸려면이 함수를 호출 합니다. 이 뷰에 대 한 검색 특성을 변경 하려면이 함수를 재정의 합니다.

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a> CRichEditView:: OnTextNotFound

검색에 실패할 때마다 프레임 워크에서 호출 됩니다.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>매개 변수

*lpszFind*<br/>
찾을 수 없는 텍스트입니다.

### <a name="remarks"></a>설명

[Messagebeep](/windows/win32/api/winuser/nf-winuser-messagebeep)의 출력 알림을 변경 하려면이 함수를 재정의 합니다.

자세한 내용은 Windows SDK의 [Messagebeep](/windows/win32/api/winuser/nf-winuser-messagebeep) 를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a> CRichEditView:: OnUpdateCharEffect

프레임 워크는 문자 효과 명령에 대 한 명령 UI를 업데이트 하기 위해이 함수를 호출 합니다.

```cpp
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>매개 변수

*pCmdUI*<br/>
[CCmdUI](../../mfc/reference/ccmdui-class.md) 개체에 대 한 포인터입니다.

*dwMask*<br/>
문자 형식 마스크를 나타냅니다.

*dwEffect*<br/>
문자 서식 지정 효과를 나타냅니다.

### <a name="remarks"></a>설명

Mask *dwmask* 는 확인할 문자 서식 특성을 지정 합니다. *DwEffect* 플래그는 설정/해제할 문자 서식 특성을 나열 합니다.

*Dwmask* 및 *dwEffect* 매개 변수 및 해당 값에 대 한 자세한 내용은 Windows SDK [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) 의 해당 데이터 멤버를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a> CRichEditView:: OnUpdateParaAlign

프레임 워크는이 함수를 호출 하 여 단락 효과 명령에 대 한 명령 UI를 업데이트 합니다.

```cpp
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>매개 변수

*pCmdUI*<br/>
[CCmdUI](../../mfc/reference/ccmdui-class.md) 개체에 대 한 포인터입니다.

*wAlign*<br/>
확인할 단락 맞춤입니다. 다음 값 중 하나입니다.

- 단락을 왼쪽 여백 PFA_LEFT 맞춥니다.

- 단락을 오른쪽 여백 PFA_RIGHT 맞춥니다.

- 여백 사이에 단락을 가운데 PFA_CENTER 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a> CRichEditView::P rintInsideRect

이 함수를 호출 하 여 서식 있는 편집 컨트롤의 텍스트 범위를 *pDC* 로 지정 된 장치에 대 한 *rectLayout* 내에 맞게 서식 지정 합니다.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
출력 영역에 대 한 장치 컨텍스트에 대 한 포인터입니다.

*rectLayout*<br/>
출력 영역을 정의 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) .

*nIndexStart*<br/>
서식을 지정할 첫 번째 문자의 0부터 시작 하는 인덱스입니다.

*nIndexStop*<br/>
서식을 지정할 마지막 문자의 0부터 시작 하는 인덱스입니다.

*bOutput*<br/>
텍스트를 렌더링 해야 하는지 여부를 나타냅니다. FALSE 이면 텍스트를 측정 합니다.

### <a name="return-value"></a>반환 값

출력 영역에 맞는 마지막 문자의 인덱스와 1을 더한 값입니다.

### <a name="remarks"></a>설명

일반적으로이 호출 후에는 출력을 생성 하는 [CRichEditCtrl::D isplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) 에 대 한 호출이 발생 합니다.

### <a name="example"></a>예제

  [CRichEditView:: GetPaperSize](#getpapersize)의 예제를 참조 하세요.

## <a name="cricheditviewprintpage"></a><a name="printpage"></a> CRichEditView::P rintPage

*PDC* 에서 지정 된 출력 장치에 대 한 rich edit 컨트롤의 텍스트 범위를 지정 하려면이 함수를 호출 합니다.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
페이지 출력의 장치 컨텍스트에 대 한 포인터입니다.

*nIndexStart*<br/>
서식을 지정할 첫 번째 문자의 0부터 시작 하는 인덱스입니다.

*nIndexStop*<br/>
서식을 지정할 마지막 문자의 0부터 시작 하는 인덱스입니다.

### <a name="return-value"></a>반환 값

페이지에 맞는 마지막 문자의 인덱스 + 1입니다.

### <a name="remarks"></a>설명

각 페이지의 레이아웃은 [GetPageRect](#getpagerect) 및 [getprintrect](#getprintrect)에 의해 제어 됩니다. 일반적으로이 호출 후에는 출력을 생성 하는 [CRichEditCtrl::D isplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) 에 대 한 호출이 발생 합니다.

여백은 논리적 페이지가 아니라 물리적 페이지를 기준으로 합니다. 따라서 여백이 0 인 경우에는 페이지에 인쇄할 수 없는 영역이 있으므로 많은 프린터에서 텍스트를 클리핑 하는 경우가 많습니다. 텍스트를 클리핑 하지 않으려면 인쇄 하기 전에 [Setmargins](#setmargins) 을 호출 하 고 적절 한 여백을 설정 해야 합니다.

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a> CRichEditView:: QueryAcceptData

개체를 rich edit에 붙여넣기 위해 프레임 워크에서 호출 됩니다.

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>매개 변수

*lpdataobj*<br/>
쿼리할 [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 에 대 한 포인터입니다.

*lpcfFormat*<br/>
허용 되는 데이터 형식에 대 한 포인터입니다.

*Dwo*<br/>
사용되지 않습니다.

*bReally*<br/>
붙여넣기 작업을 계속할지 여부를 나타냅니다.

*hMetaFile 파일*<br/>
항목의 아이콘을 그리는 데 사용 되는 메타 파일에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

작업의 성공 여부를 보고 하는 HRESULT 값입니다.

### <a name="remarks"></a>설명

파생 된 문서 클래스에서 여러 COM 항목 조직을 처리 하려면이 함수를 재정의 합니다. 이는 고급 재정의 가능입니다.

HRESULT 및에 대 한 자세한 내용은 `IDataObject` Windows SDK의 [COM 오류 코드](/windows/win32/com/structure-of-com-error-codes) 및 [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)의 구조를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a> CRichEditView:: SetCharFormat

이 개체의 새 텍스트에 대 한 문자 서식 특성을 설정 하려면이 함수를 호출 `CRichEditView` 합니다.

```cpp
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>매개 변수

*f*<br/>
새 기본 문자 서식 특성을 포함 하는 [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) 구조체입니다.

### <a name="remarks"></a>설명

`dwMask`이 함수는 *cf* 의 멤버로 지정 된 특성만 변경 합니다.

자세한 내용은 Windows SDK [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) 메시지 및 [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) 구조를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a> CRichEditView:: SetMargins

이 함수를 호출 하 여이 rich edit 뷰의 인쇄 여백을 설정 합니다.

```cpp
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>매개 변수

*rectMargin*<br/>
MM_TWIPS로 측정 된 인쇄를 위한 새 여백 값입니다.

### <a name="remarks"></a>설명

[M_nWordWrap](#m_nwordwrap) 이면 `WrapToTargetDevice` 이 함수를 사용 하 여 인쇄 특성을 조정한 후 [WrapChanged](#wrapchanged) 를 호출 해야 합니다.

[System.drawing.printing.printdocument.printpage>](#printpage) 에서 사용 하는 여백은 논리적 페이지가 아니라 물리적 페이지를 기준으로 합니다. 따라서 여백이 0 인 경우에는 페이지에 인쇄할 수 없는 영역이 있으므로 많은 프린터에서 텍스트를 클리핑 하는 경우가 많습니다. 텍스트를 클리핑 하지 않으려면 `SetMargins` 인쇄 하기 전에 사용을 호출 하 여 적절 한 프린터 여백을 설정 해야 합니다.

### <a name="example"></a>예제

  [CRichEditView:: GetPaperSize](#getpapersize)의 예제를 참조 하세요.

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a> CRichEditView:: SetPaperSize

이 함수를 호출 하 여이 rich edit 보기를 인쇄 하기 위한 용지 크기를 설정 합니다.

```cpp
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>매개 변수

*sizePaper*<br/>
MM_TWIPS로 측정 된 인쇄를 위한 새 용지 크기 값입니다.

### <a name="remarks"></a>설명

[M_nWordWrap](#m_nwordwrap) 이면 `WrapToTargetDevice` 이 함수를 사용 하 여 인쇄 특성을 조정한 후 [WrapChanged](#wrapchanged) 를 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a> CRichEditView:: SetParaFormat

이 함수를 호출 하 여이 개체의 현재 선택 영역에 대 한 단락 서식 특성을 설정 합니다 `CRichEditView` .

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>매개 변수

*pf*<br/>
새 기본 단락 서식 특성을 포함 하는 [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) 구조체입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`dwMask`이 함수는 *pf* 의 멤버로 지정 된 특성만 변경 합니다.

자세한 내용은 Windows SDK [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) 메시지 및 [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) 구조를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a> CRichEditView:: TextNotFound

[FindText](#findtext)에 대 한 호출에 실패 한 후 [CRichEditView](../../mfc/reference/cricheditview-class.md) 컨트롤의 내부 검색 상태를 다시 설정 하려면이 함수를 호출 합니다.

```cpp
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>매개 변수

*lpszFind*<br/>
찾을 수 없는 텍스트 문자열을 포함 합니다.

### <a name="remarks"></a>설명

이 메서드는 [FindText](#findtext) 에 대 한 호출에 실패 한 후 즉시 호출 되어 컨트롤의 내부 검색 상태가 적절히 다시 설정 되는 것이 좋습니다.

*LpszFind* 매개 변수는 [FindText](#findtext)에 제공 된 문자열과 동일한 내용을 포함 해야 합니다. 내부 검색 상태를 다시 설정한 후이 메서드는 제공 된 검색 문자열을 사용 하 여 [Ontextnotfound](#ontextnotfound) 메서드를 호출 합니다.

### <a name="example"></a>예제

  [CRichEditView:: FindText](#findtext)의 예제를 참조 하세요.

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a> CRichEditView:: WrapChanged

인쇄 특성이 변경 된 경우 ( [Setmargins](#setmargins) 나 [setmargins](#setpapersize))이 함수를 호출 합니다.

```
virtual void WrapChanged();
```

### <a name="remarks"></a>설명

Rich edit 보기가 [m_nWordWrap](#m_nwordwrap) 의 변경 내용에 응답 하는 방법 또는 인쇄 특성 ( [on프린터 변경](#onprinterchanged))을 수정 하려면이 함수를 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 워드 패드](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 클래스](../../mfc/reference/cctrlview-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 클래스](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem 클래스](../../mfc/reference/cricheditcntritem-class.md)
