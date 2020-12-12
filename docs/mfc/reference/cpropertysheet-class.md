---
description: '자세히 알아보기: CPropertySheet 클래스'
title: CPropertySheet 클래스
ms.date: 11/04/2016
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
ms.openlocfilehash: f2ca56fefbb192e9ed64a97bd75bee4fbb1c6360
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301375"
---
# <a name="cpropertysheet-class"></a>CPropertySheet 클래스

속성 시트(탭 대화 상자라고도 함)를 나타냅니다.

## <a name="syntax"></a>구문

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPropertySheet:: CPropertySheet](#cpropertysheet)|`CPropertySheet` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPropertySheet:: AddPage](#addpage)|속성 시트에 페이지를 추가합니다.|
|[CPropertySheet:: 생성자](#construct)|`CPropertySheet` 개체를 생성합니다.|
|[CPropertySheet:: Create](#create)|모덜리스 속성 시트를 표시 합니다.|
|[CPropertySheet::D oModal](#domodal)|모달 속성 시트를 표시 합니다.|
|[CPropertySheet:: EnableStackedTabs](#enablestackedtabs)|속성 시트가 누적 또는 스크롤 탭을 사용 하는지 여부를 나타냅니다.|
|[CPropertySheet:: EndDialog](#enddialog)|속성 시트를 종료 합니다.|
|[CPropertySheet:: GetActiveIndex](#getactiveindex)|속성 시트의 활성 페이지 인덱스를 검색 합니다.|
|[CPropertySheet:: GetActivePage](#getactivepage)|활성 페이지 개체를 반환 합니다.|
|[CPropertySheet:: GetPage](#getpage)|지정 된 페이지에 대 한 포인터를 검색 합니다.|
|[CPropertySheet:: GetPageCount](#getpagecount)|속성 시트의 페이지 수를 검색 합니다.|
|[CPropertySheet:: GetPageIndex](#getpageindex)|속성 시트에서 지정 된 페이지의 인덱스를 검색 합니다.|
|[CPropertySheet:: GetTabControl](#gettabcontrol)|Tab 컨트롤에 대 한 포인터를 검색 합니다.|
|[CPropertySheet:: MapDialogRect](#mapdialogrect)|사각형의 대화 상자 단위를 화면 단위로 변환 합니다.|
|[CPropertySheet:: OnInitDialog](#oninitdialog)|속성 시트 초기화를 확대 하도록 재정의 합니다.|
|[CPropertySheet::P ressButton](#pressbutton)|속성 시트에서 지정 된 단추의 선택을 시뮬레이션 합니다.|
|[CPropertySheet:: RemovePage](#removepage)|속성 시트에서 페이지를 제거 합니다.|
|[CPropertySheet:: SetActivePage](#setactivepage)|활성 페이지 개체를 프로그래밍 방식으로 설정 합니다.|
|[CPropertySheet:: Set 텍스트](#setfinishtext)|마침 단추의 텍스트를 설정 합니다.|
|[CPropertySheet:: SetTitle](#settitle)|속성 시트의 캡션을 설정 합니다.|
|[CPropertySheet:: SetWizardButtons](#setwizardbuttons)|마법사 단추를 사용 하도록 설정 합니다.|
|[CPropertySheet:: SetWizardMode](#setwizardmode)|마법사 모드를 사용 하도록 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPropertySheet:: m_psh](#m_psh)|Windows [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) 구조체입니다. 기본 속성 시트 매개 변수에 대 한 액세스를 제공 합니다.|

## <a name="remarks"></a>설명

속성 시트는 `CPropertySheet` 개체와 하나 이상의 [CPropertyPage](../../mfc/reference/cpropertypage-class.md) 개체로 구성 됩니다. 프레임 워크는 속성 시트를 탭 인덱스 집합과 현재 선택 된 페이지를 포함 하는 영역으로 표시 합니다. 사용자는 적절 한 탭을 사용 하 여 특정 페이지로 이동 합니다.

`CPropertySheet` Windows 98 및 Windows NT 2000에서 도입 된 확장 된 [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) 구조에 대 한 지원을 제공 합니다. 구조에는 "워터 마크" 배경 비트맵 사용을 지 원하는 추가 플래그와 멤버가 포함 되어 있습니다.

이러한 새 이미지를 속성 시트 개체에 자동으로 표시 하려면 [CPropertySheet:: 생성자](#construct) 또는 [CPropertySheet:: CPropertySheet](#cpropertysheet)에 대 한 호출에서 비트맵과 색상표 이미지에 대 한 유효한 값을 전달 합니다.

`CPropertySheet`가 [CDialog](../../mfc/reference/cdialog-class.md)에서 파생 되지 않은 경우에도 개체 관리 `CPropertySheet` 는 개체 관리와 유사 `CDialog` 합니다. 예를 들어, 속성 시트를 만들려면 두 부분으로 구성 된 생성이 필요 합니다. 생성자를 호출한 다음 모달 속성 시트에 대해 [DoModal](#domodal) 를 호출 하거나 모덜리스 속성 시트에 대해 [Create](#create) 를 호출 합니다. `CPropertySheet` 에는 두 가지 형식의 생성자 인 [CPropertySheet:: 구문과](#construct) [CPropertySheet:: CPropertySheet](#cpropertysheet)가 있습니다.

개체를 생성할 때 `CPropertySheet` 일부 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 로 인해 첫 번째 예외가 발생할 수 있습니다. 이로 인해 시스템에서 시트를 만들기 전에 속성 시트의 스타일을 변경 하려고 합니다. 이 예외를 방지 하려면를 만들 때 다음 스타일을 설정 해야 합니다 `CPropertySheet` .

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

다음 스타일은 선택 사항이 며 첫 번째 예외를 발생 시 키 지 않습니다.

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

다른 모든 `Window Styles` 항목은 사용할 수 없으므로 사용 하도록 설정 하면 안 됩니다.

`CPropertySheet`개체와 외부 개체 간에 데이터를 교환 하는 것은 개체와 데이터를 교환 하는 것과 비슷합니다 `CDialog` . 중요 한 차이점은 속성 시트의 설정은 일반적으로 `CPropertyPage` 개체 자체가 아니라 개체의 멤버 변수입니다 `CPropertySheet` .

마법사 라는 유형의 탭 대화 상자를 만들 수 있습니다 .이 대화 상자는 사용자가 장치를 설정 하거나 뉴스레터를 만드는 등의 작업 단계를 안내 하는 일련의 속성 페이지를 사용 하 여 속성 시트로 구성 됩니다. 마법사-형식 탭 대화 상자에서 속성 페이지에 탭이 없으며 한 번에 하나의 속성 페이지만 표시 됩니다. 또한 **확인** 및 **지금 적용** 단추 대신 마법사 유형 탭 대화 상자에 **뒤로** 단추, **다음** 또는 **마침** 단추, **취소** 단추 및 **도움말** 단추가 있습니다.

마법사 유형 대화 상자를 만들려면 표준 속성 시트를 만들기 위해 수행 하는 것과 동일한 단계를 수행 하지만 [DoModal](#domodal)를 호출 하기 전에 [setwizardmode](#setwizardmode) 를 호출 합니다. 마법사 단추를 사용 하려면 플래그를 사용 하 여 [Setwizardbuttons](#setwizardbuttons)를 호출 하 고 함수 및 모양을 사용자 지정 합니다. **마침** 단추를 사용 하도록 설정 하려면 마법사의 마지막 페이지에서 사용자가 작업을 수행한 후 [setfinish 텍스트](#setfinishtext) 를 호출 합니다.

개체를 사용 하는 방법에 대 한 자세한 내용은 `CPropertySheet` 아티클 [속성 시트 및 속성 페이지](../../mfc/property-sheets-and-property-pages-in-mfc.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a> CPropertySheet:: AddPage

제공 된 페이지를 속성 시트의 맨 오른쪽 탭에 추가 합니다.

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>매개 변수

*pPage*<br/>
속성 시트에 추가할 페이지를 가리킵니다. NULL이 될 수 없습니다.

### <a name="remarks"></a>설명

페이지를 표시 하려면 왼쪽에서 오른쪽 순서로 속성 시트에 페이지를 추가 합니다.

`AddPage` 개체의 페이지 목록에 [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) 개체를 추가 `CPropertySheet` 하지만 실제로 페이지의 창을 만들지는 않습니다. 프레임 워크는 사용자가 페이지를 선택할 때까지 페이지에 대 한 창 생성을 연기 합니다.

를 사용 하 여 속성 페이지를 추가 하는 경우는 `AddPage` `CPropertySheet` 의 부모입니다 `CPropertyPage` . 속성 페이지에서 속성 시트에 대 한 액세스 권한을 얻으려면 [CWnd:: GetParent](../../mfc/reference/cwnd-class.md#getparent)를 호출 합니다.

호출할 속성 시트 창을 만들 때까지 기다릴 필요는 없습니다 `AddPage` . 일반적으로 `AddPage` [DoModal](#domodal) 또는 [Create](#create)를 호출 하기 전에를 호출 합니다.

`AddPage`속성 페이지를 표시 한 후를 호출 하면 탭 행에 새로 추가 된 페이지가 반영 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a> CPropertySheet:: 생성자

`CPropertySheet` 개체를 생성합니다.

```cpp
void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>매개 변수

*nIDCaption*<br/>
속성 시트에 사용할 캡션의 ID입니다.

*pParentWnd*<br/>
속성 시트의 부모 창에 대 한 포인터입니다. NULL 인 경우 부모 창은 응용 프로그램의 주 창이 됩니다.

*iSelectPage*<br/>
처음에 맨 위에 있는 페이지의 인덱스입니다. 기본값은 시트에 추가 되는 첫 번째 페이지입니다.

*pszCaption*<br/>
속성 시트에 사용할 캡션을 포함 하는 문자열에 대 한 포인터입니다. NULL이 될 수 없습니다.

*hbmWatermark*<br/>
속성 페이지의 워터 마크 비트맵에 대 한 핸들입니다.

*hpalWatermark*<br/>
워터 마크 비트맵 및/또는 헤더 비트맵의 색상표에 대 한 핸들입니다.

*hbmHeader*<br/>
속성 페이지의 헤더 비트맵에 대 한 핸들입니다.

### <a name="remarks"></a>설명

클래스 생성자 중 하나가 아직 호출 되지 않은 경우이 멤버 함수를 호출 합니다. 예를 들어 `Construct` 개체의 배열을 선언 하거나 할당할 때를 호출 `CPropertySheet` 합니다. 배열의 경우 `Construct` 배열의 각 멤버에 대해를 호출 해야 합니다.

속성 시트를 표시 하려면 [DoModal](#domodal) 또는 [Create](#create)를 호출 합니다. 첫 번째 매개 변수에 포함 된 문자열은 속성 시트의 캡션 표시줄에 배치 됩니다.

위에 나열 된의 세 번째 또는 네 번째 프로토타입을 사용 하 `Construct` 고 *hbmWatermark*, *HpalWatermark* 및/또는 *hbmHeader* 매개 변수에 대 한 유효한 값을 전달 하는 경우 워터 마크 및/또는 머리글 이미지를 자동으로 표시할 수 있습니다.

### <a name="example"></a>예제

다음 예제에서는를 호출 하는 상황을 보여 줍니다 `Construct` .

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a> CPropertySheet:: CPropertySheet

`CPropertySheet` 개체를 생성합니다.

```
CPropertySheet();

explicit CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

explicit CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>매개 변수

*nIDCaption*<br/>
속성 시트에 사용할 캡션의 ID입니다.

*pParentWnd*<br/>
속성 시트의 부모 창을 가리킵니다. NULL 인 경우 부모 창은 응용 프로그램의 주 창이 됩니다.

*iSelectPage*<br/>
처음에 맨 위에 있는 페이지의 인덱스입니다. 기본값은 시트에 추가 되는 첫 번째 페이지입니다.

*pszCaption*<br/>
속성 시트에 사용할 캡션을 포함 하는 문자열을 가리킵니다. NULL이 될 수 없습니다.

*hbmWatermark*<br/>
속성 시트의 배경 비트맵 핸들입니다.

*hpalWatermark*<br/>
워터 마크 비트맵 및/또는 헤더 비트맵의 색상표에 대 한 핸들입니다.

*hbmHeader*<br/>
속성 페이지의 헤더 비트맵에 대 한 핸들입니다.

### <a name="remarks"></a>설명

속성 시트를 표시 하려면 [DoModal](#domodal) 또는 [Create](#create)를 호출 합니다. 첫 번째 매개 변수에 포함 된 문자열은 속성 시트의 캡션 표시줄에 배치 됩니다.

여러 매개 변수가 있는 경우 (예: 배열을 사용 하는 경우) 대신 [구문을](#construct) 사용 `CPropertySheet` 합니다.

위의 세 번째 또는 네 번째 프로토타입을 사용 하 `CPropertySheet` 고 *hbmWatermark*, *HpalWatermark* 및/또는 *hbmHeader* 매개 변수에 대 한 유효한 값을 전달 하는 경우 워터 마크 및/또는 머리글 이미지를 자동으로 표시할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a> CPropertySheet:: Create

모덜리스 속성 시트를 표시 합니다.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
부모 창을 가리킵니다. NULL 인 경우 부모는 바탕 화면입니다.

*dwStyle*<br/>
속성 시트에 대 한 창 스타일입니다. 사용 가능한 스타일의 전체 목록은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 참조 하세요.

*dwExStyle*<br/>
속성 시트에 대 한 확장 창 스타일입니다. 사용 가능한 스타일의 전체 목록은 [확장 창 스타일](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) 을 참조 하세요.

### <a name="return-value"></a>반환 값

속성 시트가 성공적으로 생성 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

에 대 한 호출은 `Create` 생성자 내부에 있거나 생성자가 호출 된 후 호출할 수 있습니다.

*Dwstyle* 으로-1을 전달 하 여 표현 된 기본 스타일은 실제로 WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE입니다. 0을 *Dwexstyle* 으로 전달 하 여 표현 된 기본 확장 창 스타일은 실제로 WS_EX_DLGMODALFRAME 됩니다.

`Create`멤버 함수는 속성 시트를 만든 후 즉시 반환 됩니다. 속성 시트를 제거 하려면 [CWnd::D estroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)를 호출 합니다.

에 대 한 호출과 함께 표시 되는 모덜리스 속성 시트에는 `Create` 모달 속성 시트에서 확인, 취소, 지금 적용 및 도움말 단추가 없습니다. 사용자가 원하는 단추를 만들어야 합니다.

모달 속성 시트를 표시 하려면 대신 [DoModal](#domodal) 를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a> CPropertySheet::D oModal

모달 속성 시트를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

함수가 성공 하는 경우 IDOK 또는 IDCANCEL 그렇지 않으면 0 또는-1입니다. 속성 시트가 마법사로 설정 된 경우 ( [Setwizardmode](#setwizardmode)참조) `DoModal` ID_WIZFINISH 또는 IDCANCEL를 반환 합니다.

### <a name="remarks"></a>설명

반환 값은 속성 시트를 닫은 컨트롤의 ID에 해당 합니다. 이 함수가 반환 된 후에는 속성 시트와 모든 페이지에 해당 하는 창이 제거 됩니다. 개체 자체는 여전히 존재 하 게 됩니다. 일반적으로는 IDOK를 반환한 후 [CPropertyPage](../../mfc/reference/cpropertypage-class.md) 개체에서 데이터를 검색 합니다 `DoModal` .

모덜리스 속성 시트를 표시 하려면 [Create](#create) 를 대신 호출 합니다.

해당 대화 상자 리소스에서 속성 페이지를 만들면 첫 번째 예외가 발생할 수 있습니다. 그러면 속성 페이지에서 페이지를 만들기 전에 대화 상자 리소스의 스타일을 필요한 스타일로 변경 합니다. 리소스는 일반적으로 읽기 전용 이기 때문에 예외가 발생 합니다. 시스템은 예외를 처리 하 고 수정 된 리소스의 복사본을 만듭니다. 따라서 첫 번째 예외를 무시할 수 있습니다.

> [!NOTE]
> 비동기 예외 처리 모델을 사용 하 여 컴파일하는 경우에는 운영 체제에서이 예외를 처리 해야 합니다. 예외 처리 모델에 대 한 자세한 내용은 [/Ceh (예외 처리 모델)](../../build/reference/eh-exception-handling-model.md)를 참조 하세요. 이 경우 `CPropertySheet::DoModal` catch에서 모든 예외 (예:)를 처리 하는 c + + try-catch 블록을 사용 하 여에 대 한 호출을 래핑합니다 `catch (...)` . 이 블록은 운영 체제에 대 한 예외를 처리 하 고 예기치 않은 동작을 발생 시킵니다. 그러나 액세스 위반 예외가 운영 체제로 전달 되는 경우 특정 예외 형식 또는 구조적 예외 처리를 사용 하 여 c + + 예외 처리를 안전 하 게 사용할 수 있습니다.

이 첫 번째 예외가 발생 하지 않도록 하려면 속성 시트에 올바른 [창 스타일이](../../mfc/reference/styles-used-by-mfc.md#window-styles)있음을 수동으로 보장할 수 있습니다. 속성 시트에 대해 다음과 같은 스타일을 설정 해야 합니다.

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

첫 번째 예외를 발생 시 키 지 않고 다음과 같은 선택적 스타일을 사용할 수 있습니다.

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

다른 모든 Windows 스타일은 속성 시트와 호환 되지 않으므로 사용 하지 않도록 설정 합니다. 이 권장 사항은 확장 스타일에는 적용 되지 않습니다. 이러한 표준 스타일을 적절 하 게 설정 하면 속성 시트를 수정할 필요가 없으며 첫 번째 예외가 생성 되지 않습니다.

### <a name="example"></a>예제

[CPropertySheet:: AddPage](#addpage)의 예제를 참조 하세요.

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a> CPropertySheet:: EnableStackedTabs

속성 시트에서 탭의 행을 쌓을 지 여부를 나타냅니다.

```cpp
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>매개 변수

*bStacked*<br/>
속성 시트에서 누적 된 탭을 사용할 수 있는지 여부를 나타냅니다. *Bstacked* 를 FALSE로 설정 하 여 누적 된 태그 행을 사용 하지 않도록 설정 합니다.

### <a name="remarks"></a>설명

기본적으로 속성 시트의 탭이 속성 시트의 너비에서 단일 행에 맞는 것 보다 많은 경우 탭이 여러 행으로 쌓입니다. 스택 탭 대신 스크롤 탭을 사용 하려면 `EnableStackedTabs` [DoModal](#domodal) 또는 [Create](#create)를 호출 하기 전에 *bstacked* 를 FALSE로 설정 하 여를 호출 합니다.

`EnableStackedTabs`모달 또는 모덜리스 속성 시트를 만들 때를 호출 해야 합니다. 파생 클래스에이 스타일을 통합 하려면 `CPropertySheet` WM_CREATE에 대 한 메시지 처리기를 작성 합니다. 재정의 된 [CWnd:: OnCreate](../../mfc/reference/cwnd-class.md#oncreate)버전에서 `EnableStackedTabs( FALSE )` 기본 클래스 구현을 호출 하기 전에를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a> CPropertySheet:: EndDialog

속성 시트를 종료 합니다.

```cpp
void EndDialog(int nEndID);
```

### <a name="parameters"></a>매개 변수

*nEndID*<br/>
속성 시트의 반환 값으로 사용할 식별자입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 확인, 취소 또는 닫기 단추를 누를 때 프레임 워크에서 호출 됩니다. 속성 시트를 닫아야 하는 이벤트가 발생 하는 경우이 멤버 함수를 호출 합니다.

이 멤버 함수는 모달 대화 상자 에서만 사용 됩니다.

### <a name="example"></a>예제

[CPropertySheet::P ressButton](#pressbutton)의 예제를 참조 하세요.

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a> CPropertySheet:: GetActiveIndex

속성 시트 창의 활성 페이지의 인덱스 번호를 가져온 다음 반환 되는 인덱스 번호를에 대 한 매개 변수로 사용 합니다 `GetPage` .

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>반환 값

활성 페이지의 인덱스 번호입니다.

### <a name="example"></a>예제

[CPropertySheet:: GetActivePage](#getactivepage)의 예제를 참조 하세요.

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a> CPropertySheet:: GetActivePage

속성 시트 창의 활성 페이지를 검색 합니다.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>반환 값

활성 페이지에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 사용 하 여 활성 페이지에서 일부 작업을 수행할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a> CPropertySheet:: GetPage

이 속성 시트의 지정 된 페이지에 대 한 포인터를 반환 합니다.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>매개 변수

*nPage*<br/>
0부터 시작 하 여 원하는 페이지의 인덱스입니다. 0에서 속성 시트의 페이지 수보다 1 보다 작은 값 (포함) 사이 여야 합니다.

### <a name="return-value"></a>반환 값

*Npage* 매개 변수에 해당 하는 페이지에 대 한 포인터입니다.

### <a name="example"></a>예제

[CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)의 예제를 참조 하세요.

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a> CPropertySheet:: GetPageCount

현재 속성 시트에 있는 페이지 수를 결정 합니다.

```
int GetPageCount() const;
```

### <a name="return-value"></a>반환 값

속성 시트에 있는 페이지 수입니다.

### <a name="example"></a>예제

[CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)의 예제를 참조 하세요.

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a> CPropertySheet:: GetPageIndex

속성 시트에서 지정 된 페이지의 인덱스 번호를 검색 합니다.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>매개 변수

*pPage*<br/>
인덱스를 찾을 페이지를 가리킵니다. NULL이 될 수 없습니다.

### <a name="return-value"></a>반환 값

페이지의 인덱스 번호입니다.

### <a name="remarks"></a>설명

예를 들어 `GetPageIndex` [setactivepage](#setactivepage) 또는 [getpage](#getpage)를 사용 하기 위해를 사용 하 여 페이지 인덱스를 가져올 수 있습니다.

### <a name="example"></a>예제

[CPropertySheet:: GetActivePage](#getactivepage)의 예제를 참조 하세요.

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a> CPropertySheet:: GetTabControl

탭 컨트롤에 대 한 포인터를 검색 하 여 tab 컨트롤과 관련 된 작업을 수행 합니다. 즉, [Ctabctrl](../../mfc/reference/ctabctrl-class.md)에서 api를 사용 합니다.

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>반환 값

탭 컨트롤에 대 한 포인터입니다.

### <a name="remarks"></a>설명

예를 들어 초기화 하는 동안 각 탭에 비트맵을 추가 하려면이 멤버 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a> CPropertySheet:: m_psh

해당 멤버가 [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)의 특성을 저장 하는 구조체입니다.

### <a name="remarks"></a>설명

이 구조체를 사용 하 여 속성 시트가 생성 된 후 [DoModal](#domodal) 멤버 함수를 사용 하 여 표시 되기 전에이를 초기화 합니다. 예를 들어의 *dwsize* 멤버를 `m_psh` 속성 시트에 포함할 크기로 설정 합니다.

멤버 목록을 포함 하 여이 구조에 대 한 자세한 내용은 Windows SDK의 PROPSHEETHEADER를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a> CPropertySheet:: MapDialogRect

사각형의 대화 상자 단위를 화면 단위로 변환 합니다.

```cpp
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
변환할 대화 상자 좌표를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) 개체를 가리킵니다.

### <a name="remarks"></a>설명

대화 상자 단위는 대화 상자 텍스트에 사용 되는 글꼴의 평균 너비와 문자 높이에서 파생 된 현재 대화 상자 기본 단위를 기준으로 하 여 설명 됩니다. 하나의 가로 단위는 대화 상자 기본 너비 단위의 1/4이 고, 세로 단위 하나는 대화 상자 기본 높이 단위의 8-8입니다.

[Getdialogbaseunits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows 함수는 시스템 글꼴에 대 한 크기 정보를 반환 하지만, 리소스 정의 파일에서 DS_SETFONT 스타일을 사용 하는 경우 각 속성 시트에 대해 다른 글꼴을 지정할 수 있습니다. Windows SDK에 설명 된 [Mapdialogrect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows 함수는이 대화 상자에 해당 하는 글꼴을 사용 합니다.

`MapDialogRect`멤버 함수는 사각형을 사용 하 여 대화 상자를 만들거나 상자 내에 컨트롤을 배치할 수 있도록 *lpRect* 의 대화 상자 단위를 화면 단위 (픽셀)로 바꿉니다.

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a> CPropertySheet:: OnInitDialog

속성 시트 초기화를 확대 하기 위해를 재정의 합니다.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>반환 값

응용 프로그램에서 속성 시트의 컨트롤 중 하나에 입력 포커스를 설정 했는지 여부를 지정 합니다. `OnInitDialog`가 0이 아닌 값을 반환 하는 경우 Windows에서는 입력 포커스를 속성 시트의 첫 번째 컨트롤로 설정 합니다. 응용 프로그램은 입력 포커스를 속성 시트의 컨트롤 중 하나로 명시적으로 설정한 경우에만 0을 반환할 수 있습니다.

### <a name="remarks"></a>설명

이 멤버 함수는 WM_INITDIALOG 메시지에 대 한 응답으로 호출 됩니다. 이 메시지는 속성 시트가 표시 되기 직전에 발생 하는 [Create](#create) 또는 [DoModal](#domodal) 호출 중에 속성 시트에 전송 됩니다.

속성 시트가 초기화 될 때 특수 처리를 수행 해야 하는 경우이 멤버 함수를 재정의 합니다. 재정의 된 버전에서 먼저 기본 클래스를 호출 `OnInitDialog` 하지만 해당 반환 값은 무시 합니다. 일반적으로 재정의 된 멤버 함수에서 TRUE를 반환 합니다.

이 멤버 함수에는 메시지 맵 항목이 필요 하지 않습니다.

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a> CPropertySheet::P ressButton

속성 시트에서 지정 된 단추의 선택을 시뮬레이션 합니다.

```cpp
void PressButton(int nButton);
```

### <a name="parameters"></a>매개 변수

*nButton*<br/>
nButton: 누를 단추를 식별 합니다. 이 매개 변수는 다음 값 중 하나일 수 있습니다.

- PSBTN_BACK 뒤로 단추를 선택 합니다.

- PSBTN_NEXT 다음 단추를 선택 합니다.

- PSBTN_FINISH 마침 단추를 선택 합니다.

- PSBTN_OK 확인 단추를 선택 합니다.

- PSBTN_APPLYNOW 지금 적용 단추를 선택 합니다.

- PSBTN_CANCEL 취소 단추를 선택 합니다.

- PSBTN_HELP 도움말 단추를 선택 합니다.

### <a name="remarks"></a>설명

Windows SDK 보도 PSM_PRESSBUTTON 메시지에 대 한 자세한 내용은 [](/windows/win32/Controls/psm-pressbutton) 를 참조 하세요.

를 호출 하면 `PressButton` 속성 페이지에서 프레임 워크로 [PSN_APPLY](/windows/win32/Controls/psn-apply) 알림이 전송 되지 않습니다. 이 알림을 보내려면 [CPropertyPage:: OnOK](../../mfc/reference/cpropertypage-class.md#onok)를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a> CPropertySheet:: RemovePage

속성 시트에서 페이지를 제거 하 고 연결 된 창을 소멸 시킵니다.

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>매개 변수

*pPage*<br/>
속성 시트에서 제거할 페이지를 가리킵니다. NULL이 될 수 없습니다.

*nPage*<br/>
제거할 페이지의 인덱스입니다. 0에서 속성 시트의 페이지 수보다 1 보다 작은 값 (포함) 사이 여야 합니다.

### <a name="remarks"></a>설명

[CPropertyPage](../../mfc/reference/cpropertypage-class.md) 개체 자체는 창의 소유자가 닫힐 때까지 제거 되지 않습니다 `CPropertySheet` .

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a> CPropertySheet:: SetActivePage

활성 페이지를 변경 합니다.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>매개 변수

*nPage*<br/>
설정할 페이지의 인덱스입니다. 0에서 1 사이 여야 하 고 속성 시트 (포함)의 페이지 수보다 작아야 합니다.

*pPage*<br/>
속성 시트에서 설정할 페이지를 가리킵니다. NULL일 수는 없습니다.

### <a name="return-value"></a>반환 값

속성 시트가 성공적으로 활성화 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

예를 들어 `SetActivePage` 한 페이지에서 사용자의 작업이 다른 페이지를 활성 페이지로 만들어야 하는 경우를 사용 합니다.

### <a name="example"></a>예제

[CPropertySheet:: GetActivePage](#getactivepage)의 예제를 참조 하세요.

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a> CPropertySheet:: Set 텍스트

마침 명령 단추에 텍스트를 설정 합니다.

```cpp
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
마침 명령 단추에 표시 될 텍스트를 가리킵니다.

### <a name="remarks"></a>설명

`SetFinishText`을 호출 하 여 마침 명령 단추의 텍스트를 표시 하 고 마법사의 마지막 페이지에서 사용자가 작업을 완료 한 후에 다음 및 뒤로 단추를 숨깁니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a> CPropertySheet:: SetTitle

속성 시트의 캡션 (프레임 창의 제목 표시줄에 표시 되는 텍스트)을 지정 합니다.

```cpp
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>매개 변수

*nStyle*<br/>
속성 시트 제목의 스타일을 지정 합니다. 스타일은 0 또는 PSH_PROPTITLE로 지정 해야 합니다. 스타일이 PSH_PROPTITLE로 설정 된 경우 "속성" 이라는 단어가 캡션으로 지정 된 텍스트 뒤에 나타납니다. 예를 들어 `SetTitle` ("simple", PSH_PROPTITLE)를 호출 하면 "단순 속성"의 속성 시트 캡션이 생성 됩니다.

*lpszText*<br/>
속성 시트의 제목 표시줄에서 캡션으로 사용할 텍스트를 가리킵니다.

### <a name="remarks"></a>설명

기본적으로 속성 시트는 속성 시트 생성자에서 caption 매개 변수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a> CPropertySheet:: SetWizardButtons

마법사 속성 시트에서 뒤로, 다음 또는 마침 단추를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
마법사 단추의 기능 및 모양을 사용자 지정 하는 플래그 집합입니다. 이 매개 변수는 다음 값을 조합 하 여 사용할 수 있습니다.

- PSWIZB_BACK 뒤로 단추

- PSWIZB_NEXT 다음 단추

- PSWIZB_FINISH 마침 단추

- PSWIZB_DISABLEDFINISH 사용 안 함 마침 단추

### <a name="remarks"></a>설명

`SetWizardButtons`대화 상자가 열려 있는 후에만를 호출 합니다. `SetWizardButtons` [DoModal](#domodal)를 호출 하기 전에를 호출할 수 없습니다. 일반적으로 `SetWizardButtons` [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)에서를 호출 해야 합니다.

마침 단추의 텍스트를 변경 하거나 사용자가 마법사를 완료 한 후에 다음 및 뒤로 단추를 숨기려면 [Setcompleted 텍스트](#setfinishtext)를 호출 합니다. 동일한 단추가 마침 및 다음에 대해 공유 됩니다. 한 번에 완료 또는 다음 단추를 표시할 수 있지만 둘 다를 표시할 수는 없습니다.

### <a name="example"></a>예제

에는 `CPropertySheet` `CStylePage` , 및의 세 가지 마법사 속성 페이지가 `CColorPage` `CShapePage` 있습니다.  아래 코드 조각은 마법사 속성 페이지에서 **뒤로** 및 **다음** 단추를 사용 하거나 사용 하지 않도록 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a> CPropertySheet:: SetWizardMode

속성 페이지를 마법사로 설정 합니다.

```cpp
void SetWizardMode();
```

### <a name="remarks"></a>설명

마법사 속성 페이지의 주요 특징은 사용자가 탭 대신 다음 또는 마침, 뒤로 및 취소 단추를 사용 하 여 탐색 하는 것입니다.

`SetWizardMode` [DoModal](#domodal)를 호출 하기 전에를 호출 합니다. 를 호출한 후 `SetWizardMode` 에 `DoModal` 는 ID_WIZFINISH (마침 단추를 사용 하 여 닫은 경우) 또는 IDCANCEL를 반환 합니다.

`SetWizardMode` PSH_WIZARD 플래그를 설정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
