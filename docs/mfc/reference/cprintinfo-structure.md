---
description: '자세히 알아보기: CPrintInfo 구조체'
title: CPrintInfo 구조체
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 355bcf2f04b32756ae16147465054e945d70cf78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343390"
---
# <a name="cprintinfo-structure"></a>CPrintInfo 구조체

인쇄 또는 인쇄 미리 보기 작업에 대 한 정보를 저장 합니다.

## <a name="syntax"></a>구문

```
struct CPrintInfo
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPrintInfo:: GetFromPage](#getfrompage)|인쇄할 첫 페이지의 번호를 반환 합니다.|
|[CPrintInfo:: GetMaxPage](#getmaxpage)|문서의 마지막 페이지 번호를 반환 합니다.|
|[CPrintInfo:: GetMinPage](#getminpage)|문서의 첫 페이지 번호를 반환 합니다.|
|[CPrintInfo:: GetOffsetPage](#getoffsetpage)|결합 된 DocObject 인쇄 작업에서 인쇄 되는 DocObject 항목의 첫 페이지 앞에 있는 페이지 수를 반환 합니다.|
|[CPrintInfo:: GetToPage](#gettopage)|인쇄할 마지막 페이지 번호를 반환 합니다.|
|[CPrintInfo:: SetMaxPage](#setmaxpage)|문서의 마지막 페이지 번호를 설정 합니다.|
|[CPrintInfo:: SetMinPage](#setminpage)|문서의 첫 페이지 번호를 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPrintInfo:: m_bContinuePrinting](#m_bcontinueprinting)|프레임 워크에서 인쇄 루프를 계속할지 여부를 나타내는 플래그를 포함 합니다.|
|[CPrintInfo:: m_bDirect](#m_bdirect)|인쇄 대화 상자를 표시 하지 않고 문서를 직접 인쇄할지 여부를 나타내는 플래그를 포함 합니다.|
|[CPrintInfo:: m_bDocObject](#m_bdocobject)|인쇄 중인 문서가 DocObject 인지 여부를 나타내는 플래그를 포함 합니다.|
|[CPrintInfo:: m_bPreview](#m_bpreview)|문서를 미리 보는 중인지를 나타내는 플래그를 포함 합니다.|
|[CPrintInfo:: m_dwFlags](#m_dwflags)|DocObject 인쇄 작업을 지정 합니다.|
|[CPrintInfo:: m_lpUserData](#m_lpuserdata)|사용자가 만든 구조체에 대 한 포인터를 포함 합니다.|
|[CPrintInfo:: m_nCurPage](#m_ncurpage)|현재 인쇄 중인 페이지 수를 식별 합니다.|
|[CPrintInfo:: m_nJobNumber](#m_njobnumber)|현재 인쇄 작업에 대해 운영 체제에서 할당 한 작업 번호를 지정 합니다.|
|[CPrintInfo:: m_nNumPreviewPages](#m_nnumpreviewpages)|미리 보기 창에 표시 되는 페이지 수를 식별 합니다. 1 또는 2 중 하나입니다.|
|[CPrintInfo:: m_nOffsetPage](#m_noffsetpage)|결합 된 DocObject 인쇄 작업에서 특정 DocObject의 첫 번째 페이지에 대 한 오프셋을 지정 합니다.|
|[CPrintInfo:: m_pPD](#m_ppd)|`CPrintDialog`인쇄 대화 상자에 사용 되는 개체에 대 한 포인터를 포함 합니다.|
|[CPrintInfo:: m_rectDraw](#m_rectdraw)|현재 사용할 수 있는 페이지 영역을 정의 하는 사각형을 지정 합니다.|
|[CPrintInfo:: m_strPageDesc](#m_strpagedesc)|페이지 번호 표시에 대 한 형식 문자열을 포함 합니다.|

## <a name="remarks"></a>설명

`CPrintInfo` 는 구조체 이며 기본 클래스를 포함 하지 않습니다.

프레임 워크는 `CPrintInfo` 인쇄 또는 인쇄 미리 보기 명령이 선택 될 때마다 개체를 만들고 명령이 완료 되 면이를 소멸 시킵니다.

`CPrintInfo` 인쇄 작업 전체에 대 한 정보를 포함 합니다. 예를 들어 인쇄 되는 페이지 범위 및 인쇄 작업의 현재 상태 (예: 현재 인쇄 중인 페이지)에 대 한 정보를 포함 합니다. 일부 정보는 연결 된 [CPrintDialog](../../mfc/reference/cprintdialog-class.md) 개체에 저장 됩니다. 이 개체는 인쇄 대화 상자에서 사용자가 입력 한 값을 포함 합니다.

`CPrintInfo`개체는 인쇄 프로세스 중에 프레임 워크와 뷰 클래스 사이에 전달 되며 둘 간에 정보를 교환 하는 데 사용 됩니다. 예를 들어 프레임 워크는의 멤버에 값을 할당 하 여 인쇄할 문서 페이지를 뷰 클래스에 알립니다 `m_nCurPage` `CPrintInfo` . 뷰 클래스는 값을 검색 하 고 지정 된 페이지의 실제 인쇄를 수행 합니다.

또 다른 예는 문서를 인쇄할 때까지 문서 길이를 알 수 없는 경우입니다. 이 경우 뷰 클래스는 페이지가 인쇄 될 때마다 문서의 끝을 테스트 합니다. 끝에 도달 하면 뷰 클래스는 `m_bContinuePrinting` 의 멤버를 FALSE로 설정 합니다. `CPrintInfo` 그러면 프레임 워크에서 인쇄 루프를 중지 하는 것을 알 수 있습니다.

`CPrintInfo` 는 "참고 항목"에 나열 된 멤버 함수에서 사용 됩니다 `CView` . MFC 라이브러리에서 제공 하는 인쇄 아키텍처에 대 한 자세한 내용은 [프레임 창](../../mfc/frame-windows.md) 및 [문서/뷰 아키텍처](../../mfc/document-view-architecture.md) 및 [인쇄](../../mfc/printing.md) 및 [인쇄 문서: 다중 페이지 문서](../../mfc/multipage-documents.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CPrintInfo`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a> CPrintInfo:: GetFromPage

인쇄할 첫 페이지의 번호를 검색 하려면이 함수를 호출 합니다.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>반환 값

인쇄할 첫 페이지의 번호입니다.

### <a name="remarks"></a>설명

이 값은 인쇄 대화 상자에서 사용자가 지정한 값 이며 멤버가 참조 하는 개체에 저장 됩니다 `CPrintDialog` `m_pPD` . 사용자가 값을 지정 하지 않은 경우 기본값은 문서의 첫 페이지입니다.

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a> CPrintInfo:: GetMaxPage

문서의 마지막 페이지 번호를 검색 하려면이 함수를 호출 합니다.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>반환 값

문서의 마지막 페이지 번호입니다.

### <a name="remarks"></a>설명

이 값은 멤버에서 참조 하는 개체에 저장 됩니다 `CPrintDialog` `m_pPD` .

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a> CPrintInfo:: GetMinPage

문서의 첫 페이지 번호를 검색 하려면이 함수를 호출 합니다.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>반환 값

문서의 첫 페이지 번호입니다.

### <a name="remarks"></a>설명

이 값은 멤버에서 참조 하는 개체에 저장 됩니다 `CPrintDialog` `m_pPD` .

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a> CPrintInfo:: GetOffsetPage

DocObject 클라이언트에서 여러 DocObject 항목을 인쇄할 때 오프셋을 검색 하려면이 함수를 호출 합니다.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>반환 값

결합 된 DocObject 인쇄 작업에서 인쇄 되는 DocObject 항목의 첫 페이지 앞에 있는 페이지 수입니다.

### <a name="remarks"></a>설명

이 값은 멤버에서 참조 `m_nOffsetPage` 합니다. 문서의 첫 페이지는 `m_nOffsetPage` 다른 활성 문서와 함께 DocObject로 인쇄 될 때 값 + 1로 번호가 지정 됩니다. `m_nOffsetPage`멤버는 값이 TRUE 인 경우에만 유효 `m_bDocObject` 합니다.

## <a name="cprintinfogettopage"></a><a name="gettopage"></a> CPrintInfo:: GetToPage

인쇄할 마지막 페이지 번호를 검색 하려면이 함수를 호출 합니다.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>반환 값

인쇄할 마지막 페이지 번호입니다.

### <a name="remarks"></a>설명

이 값은 인쇄 대화 상자에서 사용자가 지정한 값 이며 멤버가 참조 하는 개체에 저장 됩니다 `CPrintDialog` `m_pPD` . 사용자가 값을 지정 하지 않은 경우 기본값은 문서의 마지막 페이지입니다.

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a> CPrintInfo:: m_bContinuePrinting

프레임 워크에서 인쇄 루프를 계속할지 여부를 나타내는 플래그를 포함 합니다.

### <a name="remarks"></a>설명

인쇄 시간 페이지 매김을 수행 하는 경우 문서의 끝에 도달한 후 재정의에서이 멤버를 FALSE로 설정할 수 있습니다 `CView::OnPrepareDC` . 멤버 함수를 사용 하 여 인쇄 작업을 시작할 때 문서 길이를 지정 하는 경우이 변수를 수정할 필요가 없습니다 `SetMaxPage` . `m_bContinuePrinting`멤버는 BOOL 형식의 공용 변수입니다.

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a> CPrintInfo:: m_bDirect

직접 인쇄를 위해 인쇄 대화 상자를 무시 하는 경우 프레임 워크는이 멤버를 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

인쇄 대화 상자는 일반적으로 셸에서 인쇄 하거나 명령 ID ID_FILE_PRINT_DIRECT를 사용 하 여 인쇄를 수행 하는 경우에 무시 됩니다.

일반적으로이 멤버를 변경 하지 않지만 변경 하는 경우 cview: [: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)재정의에서 [Cview::D oprepareprinting](../../mfc/reference/cview-class.md#doprepareprinting) 를 호출 하기 전에 변경 합니다.

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a> CPrintInfo:: m_bDocObject

인쇄 중인 문서가 DocObject 인지 여부를 나타내는 플래그를 포함 합니다.

### <a name="remarks"></a>설명

`m_dwFlags` `m_nOffsetPage` 이 플래그가 TRUE가 아니면 데이터 멤버 및가 유효 하지 않습니다.

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a> CPrintInfo:: m_bPreview

문서를 미리 보는 중인지를 나타내는 플래그를 포함 합니다.

### <a name="remarks"></a>설명

이는 사용자가 실행 한 명령에 따라 프레임 워크에 의해 설정 됩니다. 인쇄 미리 보기 작업에 대 한 인쇄 대화 상자는 표시 되지 않습니다. `m_bPreview`멤버는 BOOL 형식의 공용 변수입니다.

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a> CPrintInfo:: m_dwFlags

DocObject 인쇄 작업을 지정 하는 플래그의 조합을 포함 합니다.

### <a name="remarks"></a>설명

데이터 멤버가 TRUE 인 경우 `m_bDocObject` 에만 유효 합니다.

플래그는 다음 값 중 하나 이상이 될 수 있습니다.

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a> CPrintInfo:: m_lpUserData

사용자가 만든 구조체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

이를 사용 하 여 뷰 클래스에 저장 하지 않으려는 인쇄 관련 데이터를 저장할 수 있습니다. `m_lpUserData`멤버는 LPVOID 형식의 공용 변수입니다.

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a> CPrintInfo:: m_nCurPage

현재 페이지의 번호를 포함 합니다.

### <a name="remarks"></a>설명

프레임 워크는 `CView::OnPrepareDC` `CView::OnPrint` 문서의 각 페이지에 대해 및를 한 번 호출 하 고,이 멤버의 값은에서 반환 된 값에서로 반환 `GetFromPage` `GetToPage` 됩니다. 및의 재정의에서이 멤버 `CView::OnPrepareDC` 를 사용 `CView::OnPrint` 하 여 문서의 지정 된 페이지를 인쇄 합니다.

미리 보기 모드를 처음 호출 하면 프레임 워크에서이 멤버의 값을 읽어 처음에 미리 볼 문서 페이지를 결정 합니다. 의 재정의에서이 멤버의 값을 설정 `CView::OnPreparePrinting` 하 여 미리 보기 모드를 시작할 때 문서에서 사용자의 현재 위치를 유지할 수 있습니다. `m_nCurPage`멤버가 UINT 형식의 공용 변수입니다.

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a> CPrintInfo:: m_nJobNumber

현재 인쇄 작업에 대해 운영 체제에서 할당 한 작업 번호를 나타냅니다.

### <a name="remarks"></a>설명

작업이 아직 인쇄 되지 않은 경우 (즉, `CPrintInfo` 개체가 새로 생성 되어 인쇄에 사용 되지 않은 경우) 또는 작업을 시작 하는 동안 오류가 발생 한 경우에는이 값이 SP_ERROR 수 있습니다.

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a> CPrintInfo:: m_nNumPreviewPages

미리 보기 모드에 표시 되는 페이지 수를 포함 합니다. 1 또는 2 일 수 있습니다.

### <a name="remarks"></a>설명

`m_nNumPreviewPages`멤버가 UINT 형식의 공용 변수입니다.

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a> CPrintInfo:: m_nOffsetPage

결합 된 DocObject 인쇄 작업에서 특정 DocObject의 첫 페이지 앞에 있는 페이지 수를 포함 합니다.

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a> CPrintInfo:: m_pPD

`CPrintDialog`인쇄 작업에 대 한 인쇄 대화 상자를 표시 하는 데 사용 되는 개체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

`m_pPD`멤버는에 대 한 포인터로 선언 된 공용 변수입니다 `CPrintDialog` .

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a> CPrintInfo:: m_rectDraw

논리적 좌표에서 페이지의 사용 가능한 그리기 영역을 지정 합니다.

### <a name="remarks"></a>설명

재정의에서이를 참조할 수 있습니다 `CView::OnPrint` . 이 멤버를 사용 하 여 머리글, 바닥글 등을 인쇄 한 후 사용할 수 있는 영역을 계속 추적할 수 있습니다. `m_rectDraw`멤버는 형식의 공용 변수입니다 `CRect` .

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a> CPrintInfo:: m_strPageDesc

인쇄 미리 보기 중에 페이지 번호를 표시 하는 데 사용 되는 서식 문자열을 포함 합니다. 이 문자열은 두 개의 부분 문자열로 구성 됩니다. 하나는 단일 페이지 표시를 위한 것이 고 다른 하나는 ' \n ' 문자로 종료 됩니다.

### <a name="remarks"></a>설명

프레임 워크는 "Page%u\nPages% u-%u\n"을 기본값으로 사용 합니다. 페이지 번호에 다른 형식을 지정 하려면의 재정의에 형식 문자열을 지정 `CView::OnPreparePrinting` 합니다. `m_strPageDesc`멤버는 형식의 공용 변수입니다 `CString` .

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a> CPrintInfo:: SetMaxPage

문서의 마지막 페이지 번호를 지정 하려면이 함수를 호출 합니다.

```cpp
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>매개 변수

*nMaxPage*<br/>
문서의 마지막 페이지 번호입니다.

### <a name="remarks"></a>설명

이 값은 멤버에서 참조 하는 개체에 저장 됩니다 `CPrintDialog` `m_pPD` . 문서의 길이가 인쇄 되기 전에 알려진 경우의 재정의에서이 함수를 호출 `CView::OnPreparePrinting` 합니다. 문서의 길이가 인쇄 대화 상자에서 사용자가 지정한 설정에 따라 달라 지는 경우의 재정의에서이 함수를 호출 `CView::OnBeginPrinting` 합니다. 문서 길이가 인쇄 될 때까지 알 수 없는 경우 멤버를 사용 `m_bContinuePrinting` 하 여 인쇄 루프를 제어 합니다.

### <a name="example"></a>예제

  [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)의 예제를 참조 하세요.

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a> CPrintInfo:: SetMinPage

이 함수를 호출 하 여 문서의 첫 페이지 번호를 지정 합니다.

```cpp
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>매개 변수

*nMinPage*<br/>
문서의 첫 페이지 번호입니다.

### <a name="remarks"></a>설명

페이지 번호는 일반적으로 1부터 시작 합니다. 이 값은 멤버에서 참조 하는 개체에 저장 됩니다 `CPrintDialog` `m_pPD` .

## <a name="see-also"></a>참고 항목

[MFC 샘플 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView:: OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView:: OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView:: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView:: OnPrint](../../mfc/reference/cview-class.md#onprint)
