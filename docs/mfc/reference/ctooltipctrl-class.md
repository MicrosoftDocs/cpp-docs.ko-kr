---
title: CToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: 046c8a3f99e8b505ee6a6e8b534318263090e07d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502263"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

애플리케이션 도구의 용도를 설명하는 텍스트 한 줄을 표시하는 작은 팝업 창인 "도구 설명 컨트롤"의 기능을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|`CToolTipCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CToolTipCtrl::Activate](#activate)|도구 설명 컨트롤을 활성화 하 고 비활성화 합니다.|
|[CToolTipCtrl::AddTool](#addtool)|도구 설명 컨트롤을 사용 하 여 도구를 등록 합니다.|
|[CToolTipCtrl::AdjustRect](#adjustrect)|도구 설명 컨트롤의 텍스트 표시 사각형과 창 사각형 사이를 변환 합니다.|
|[CToolTipCtrl::Create](#create)|도구 설명 컨트롤을 만들어 `CToolTipCtrl` 개체에 연결 합니다.|
|[CToolTipCtrl::CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 도구 설명 컨트롤을 만들고이를 `CToolTipCtrl` 개체에 연결 합니다.|
|[CToolTipCtrl::DelTool](#deltool)|도구 설명 컨트롤에서 도구를 제거 합니다.|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|도구 설명의 크기를 검색 합니다.|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|현재 도구 설명 컨트롤이 표시 하는 도구 설명 창의 크기, 위치 및 텍스트와 같은 정보를 검색 합니다.|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|현재 도구 설명 컨트롤에 대해 설정 된 초기, 팝업 및 재생 기간을 검색 합니다.|
|[CToolTipCtrl::GetMargin](#getmargin)|도구 설명 창에 대해 설정 된 위쪽, 왼쪽, 아래쪽 및 오른쪽 여백을 검색 합니다.|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|도구 설명 창의 최대 너비를 검색 합니다.|
|[CToolTipCtrl::GetText](#gettext)|도구 설명 컨트롤이 도구에 대해 유지 관리 하는 텍스트를 검색 합니다.|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|도구 설명 창의 배경색을 검색 합니다.|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|도구 설명 창에서 텍스트 색을 검색 합니다.|
|[CToolTipCtrl::GetTitle](#gettitle)|현재 도구 설명 컨트롤의 제목을 검색 합니다.|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|도구 설명 컨트롤에 의해 유지 관리 되는 도구 수를 검색 합니다.|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|도구 설명 컨트롤이 도구에 대해 유지 관리 하는 정보를 검색 합니다.|
|[CToolTipCtrl::HitTest](#hittest)|지점을 테스트 하 여 지정 된 도구의 경계 사각형 내에 있는지 여부를 확인 합니다. 이 경우 도구에 대 한 정보를 검색 합니다.|
|[CToolTipCtrl::Pop](#pop)|표시 된 도구 설명 창을 보기에서 제거 합니다.|
|[CToolTipCtrl::Popup](#popup)|현재 도구 설명 컨트롤이 마지막 마우스 메시지의 좌표에 표시 되도록 합니다.|
|[CToolTipCtrl::RelayEvent](#relayevent)|처리를 위해 마우스 메시지를 도구 설명 컨트롤에 전달 합니다.|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|도구 설명 컨트롤의 초기, 팝업 및 재생 기간을 설정 합니다.|
|[CToolTipCtrl::SetMargin](#setmargin)|도구 설명 창의 위쪽, 왼쪽, 아래쪽 및 오른쪽 여백을 설정 합니다.|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|도구 설명 창의 최대 너비를 설정 합니다.|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|도구 설명 창의 배경색을 설정 합니다.|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|도구 설명 창의 텍스트 색을 설정 합니다.|
|[CToolTipCtrl::SetTitle](#settitle)|도구 설명에 표준 아이콘 및 제목 문자열을 추가 합니다.|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|도구 설명에서 도구에 대해 유지 관리 하는 정보를 설정 합니다.|
|[CToolTipCtrl::SetToolRect](#settoolrect)|도구에 대 한 새 경계 사각형을 설정 합니다.|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|도구 설명 창의 비주얼 스타일을 설정 합니다.|
|[CToolTipCtrl::Update](#update)|현재 도구를 강제로 다시 그리도록 합니다.|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|도구에 대 한 도구 설명 텍스트를 설정 합니다.|

## <a name="remarks"></a>설명

"도구"는 자식 창이 나 컨트롤과 같은 창 또는 창의 클라이언트 영역에 있는 응용 프로그램 정의 사각형 영역 중 하나입니다. 도구 설명은 대부분 사용자가 도구에 커서를 놓고 약 0.5 초 동안 유지 되는 경우에만 표시 되는 대부분의 시간에 숨겨져 있습니다. 도구 설명이 커서 근처에 표시 되 고 사용자가 마우스 단추를 클릭 하거나 도구 밖으로 커서를 이동 하면 사라집니다.

`CToolTipCtrl`도구 설명의 초기 시간 및 기간, 도구 설명 텍스트를 둘러싸는 여백 너비, 도구 설명 창 자체의 너비 및 도구 설명의 배경색과 텍스트 색을 제어 하는 기능을 제공 합니다. 단일 도구 설명 컨트롤은 둘 이상의 도구에 대 한 정보를 제공할 수 있습니다.

클래스 `CToolTipCtrl` 는 Windows의 공용 도구 설명 컨트롤의 기능을 제공 합니다. 이 컨트롤 (및 `CToolTipCtrl` 클래스)은 windows 95/98 및 windows NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

도구 설명을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [CFrameWnd에서 파생 되지 않은 Windows의 도구 설명](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)을 참조 하세요.

사용 `CToolTipCtrl`에 대 한 자세한 내용은 [컨트롤](../../mfc/controls-mfc.md) 및 [CToolTipCtrl 사용](../../mfc/using-ctooltipctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

##  <a name="activate"></a>  CToolTipCtrl::Activate

도구 설명 컨트롤을 활성화 하거나 비활성화 하려면이 함수를 호출 합니다.

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>매개 변수

*bActivate*<br/>
도구 설명 컨트롤을 활성화 또는 비활성화 할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

*Bactivate* 가 TRUE 이면 컨트롤이 활성화 됩니다. FALSE 이면 비활성화 됩니다.

도구 설명 컨트롤이 활성화 되어 있으면 커서가 컨트롤에 등록 된 도구에 있는 경우 도구 설명 정보가 표시 됩니다. 비활성 상태인 경우 커서가 도구에 있는 경우에도 도구 설명 정보가 나타나지 않습니다.

### <a name="example"></a>예제

  [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)의 예제를 참조 하세요.

##  <a name="addtool"></a>  CToolTipCtrl::AddTool

도구 설명 컨트롤을 사용 하 여 도구를 등록 합니다.

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
도구를 포함 하는 창에 대 한 포인터입니다.

*nIDText*<br/>
도구의 텍스트를 포함 하는 문자열 리소스의 ID입니다.

*lpRectTool*<br/>
도구의 경계 사각형의 좌표를 포함 하는 [RECT](/previous-versions/dd162897\(v=vs.85\)) 구조체에 대 한 포인터입니다. 좌표는 *pWnd*으로 식별 되는 창 클라이언트 영역의 왼쪽 위 모퉁이를 기준으로 합니다.

*nIDTool*<br/>
도구의 ID입니다.

*lpszText*<br/>
도구의 텍스트에 대 한 포인터입니다. 이 매개 변수에 LPSTR_TEXTCALLBACK 값이 포함 된 경우 TTN_NEEDTEXT 알림 메시지는 *pWnd* 가 가리키는 창의 부모로 이동 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*LpRectTool* 및 *nIDTool* 매개 변수는 모두 유효 해야 하며 *LpRectTool* 가 NULL 인 경우 *nIDTool* 는 0 이어야 합니다.

도구 설명 컨트롤을 둘 이상의 도구와 연결할 수 있습니다. 도구 설명 컨트롤에 도구를 등록 하려면이 함수를 호출 합니다. 그러면 커서가 도구에 있을 때 도구 설명에 저장 된 정보가 표시 됩니다.

> [!NOTE]
>  를 사용 하 `AddTool`는 정적 컨트롤에는 도구 설명을 설정할 수 없습니다.

### <a name="example"></a>예제

  [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)의 예제를 참조 하세요.

##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect

Tooltip 컨트롤의 텍스트 표시 사각형과 창 사각형 사이를 변환 합니다.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>매개 변수

*lprc*<br/>
도구 설명 창 사각형이 나 텍스트 표시 사각형을 보유 하는 [RECT](/previous-versions/dd162897\(v=vs.85\)) 구조체에 대 한 포인터입니다.

*bLarger*<br/>
TRUE 이면 *lprc* 가 텍스트 표시 사각형을 지정 하는 데 사용 되 고 해당 창 사각형이 수신 됩니다. FALSE 이면 *lprc* 가 창 사각형을 지정 하는 데 사용 되 고 해당 텍스트 표시 사각형을 수신 합니다.

### <a name="return-value"></a>반환 값

사각형이 성공적으로 조정 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 창 사각형에서 도구 설명 컨트롤의 텍스트 표시 사각형을 계산 하거나 지정 된 텍스트 표시 사각형을 표시 하는 데 필요한 도구 설명 창 사각형을 계산 합니다.

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)의 동작을 구현 합니다.

##  <a name="create"></a>  CToolTipCtrl::Create

도구 설명 컨트롤을 만들어 `CToolTipCtrl` 개체에 연결 합니다.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
도구 설명 컨트롤의 부모 창 (일반적 `CDialog`으로)을 지정 합니다. NULL이 아니어야 합니다.

*dwStyle*<br/>
도구 설명 컨트롤의 스타일을 지정 합니다. 자세한 내용은 **설명** 부분을 참조 하세요.

### <a name="return-value"></a>반환 값

`CToolTipCtrl` 개체가 성공적으로 생성 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

두 단계로을 `CToolTipCtrl` 생성 합니다. 먼저 생성자를 호출 하 여 `CToolTipCtrl` 개체를 생성 한 다음를 호출 `Create` 하 여 도구 설명 컨트롤을 만들고 `CToolTipCtrl` 개체에 연결 합니다.

*Dwstyle* 매개 변수는 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 임의로 조합 하 여 사용할 수 있습니다. 또한 도구 설명 컨트롤에는 다음과 같은 두 가지 클래스 관련 스타일이 있습니다. TTS_ALWAYSTIP 및 TTS_NOPREFIX.

|스타일|의미|
|-----------|-------------|
|TTS_ALWAYSTIP|도구 설명 컨트롤의 소유자 창이 활성 상태 인지 비활성 상태 인지에 관계 없이 커서가 도구에 있을 때 도구 설명을 표시 하도록 지정 합니다. 이 스타일을 사용 하지 않으면 도구의 소유자 창이 활성 상태 이면 도구 설명 컨트롤이 표시 되지만 비활성 상태인 경우에는 표시 되지 않습니다.|
|TTS_NOPREFIX|이 스타일을 설정 하면 시스템에서 문자열의 앰퍼샌드 (&) 문자를 제거 하지 않습니다. 도구 설명 컨트롤에 TTS_NOPREFIX 스타일이 없는 경우 시스템은 자동으로 앰퍼샌드 문자를 제거 하 여 응용 프로그램에서 메뉴 항목 및 도구 설명 컨트롤의 텍스트와 동일한 문자열을 사용할 수 있도록 합니다.|

도구 설명 컨트롤에는 컨트롤을 만들 때 지정 하는지 여부에 관계 없이 WS_POPUP 및 WS_EX_TOOLWINDOW 창 스타일이 있습니다.

확장 된 windows 스타일을 사용 하 여 도구 설명 컨트롤을 만들려면 대신 `Create` [CToolTipCtrl:: createex](#createex) 를 호출 합니다.

### <a name="example"></a>예제

  [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)의 예제를 참조 하세요.

##  <a name="createex"></a>  CToolTipCtrl::CreateEx

컨트롤 (자식 창)을 만들어 `CToolTipCtrl` 개체와 연결 합니다.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
컨트롤의 부모 창에 대 한 포인터입니다.

*dwStyle*<br/>
도구 설명 컨트롤의 스타일을 지정 합니다. 자세한 내용은 [Create](#create) 의 **설명** 섹션을 참조 하세요.

*dwStyleEx*<br/>
만들려는 컨트롤의 확장 스타일을 지정 합니다. 확장 된 Windows 스타일의 목록에 대해서는 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 에 대 한 *dwexstyle* 매개 변수를 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

대신를 사용 `CreateEx`하 여 windows 확장 스타일 앞에 WS_EX_ 지정 된 확장 된 windows 스타일을 적용 합니다 `Create` .

##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl

`CToolTipCtrl` 개체를 생성합니다.

```
CToolTipCtrl();
```

### <a name="remarks"></a>설명

개체를 생성 `Create` 한 후에는를 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>  CToolTipCtrl::DelTool

도구 설명 컨트롤에서 지 원하는 도구 컬렉션에서 *pWnd* 및 *nIDTool* 로 지정 된 도구를 제거 합니다.

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
도구를 포함 하는 창에 대 한 포인터입니다.

*nIDTool*<br/>
도구의 ID입니다.

##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize

도구 설명의 크기를 검색 합니다.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>매개 변수

*lpToolInfo*<br/>
도구 설명의 [Toolinfo](/windows/win32/api/commctrl/ns-commctrl-toolinfow) 구조에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

도구 설명의 크기입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)의 동작을 구현 합니다.

##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool

현재 도구 설명 컨트롤에 의해 표시 되는 도구 설명 창의 크기, 위치 및 텍스트와 같은 정보를 검색 합니다.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*lpToolInfo*|제한이 현재 도구 설명 창에 대 한 정보를 수신 하는 [Toolinfo](/windows/win32/api/commctrl/ns-commctrl-toolinfow) 구조체에 대 한 포인터입니다.|

### <a name="return-value"></a>반환 값

정보가 성공적으로 검색 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에 설명 된 [TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 현재 도구 설명 창에 대 한 정보를 검색 합니다.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime

도구 설명 컨트롤에 대해 현재 기간을 설정 하는 초기, 팝업 및 상태를 검색 합니다.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>매개 변수

*dwDuration*<br/>
검색 되는 기간 값을 지정 하는 플래그입니다. 이 매개 변수는 다음 값 중 하나일 수 있습니다.

- TTDT_AUTOPOP는 포인터가 도구의 경계 사각형 내에 고정 되어 있는 경우 도구 설명 창이 계속 표시 되는 시간을 검색 합니다.

- TTDT_INITIAL 도구 설명 창이 나타나기 전에 포인터가 도구의 경계 사각형 내에 고정 되어 있어야 하는 시간을 검색 합니다.

- TTDT_RESHOW는 포인터가 한 도구에서 다른 도구로 이동할 때 후속 도구 설명 창이 표시 되는 데 걸리는 시간을 검색 합니다.

### <a name="return-value"></a>반환 값

지정 된 지연 시간 (밀리초)입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)의 동작을 구현 합니다.

##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin

도구 설명 창에 대해 설정 된 위쪽, 왼쪽, 아래쪽 및 오른쪽 여백을 검색 합니다.

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>매개 변수

*lprc*<br/>
여백 정보를 `RECT` 수신 하는 구조체의 주소입니다. [RECT](/previous-versions/dd162897\(v=vs.85\)) 구조체의 멤버는 경계 사각형을 정의 하지 않습니다. 이 메시지의 목적에 따라 구조 멤버는 다음과 같이 해석 됩니다.

|멤버|텍스트로|
|------------|--------------------|
|`top`|도구 설명 텍스트의 위쪽 테두리와 위쪽 사이의 거리 (픽셀)입니다.|
|`left`|팁 텍스트의 왼쪽 테두리와 왼쪽 끝 사이의 거리 (픽셀)입니다.|
|`bottom`|아래쪽 테두리와 팁 텍스트의 아래쪽 사이의 거리 (픽셀)입니다.|
|`right`|오른쪽 테두리와 팁 텍스트의 오른쪽 끝 사이의 거리 (픽셀)입니다.|

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)의 동작을 구현 합니다.

##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth

도구 설명 창의 최대 너비를 검색 합니다.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>반환 값

도구 설명 창의 최대 너비입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)의 동작을 구현 합니다.

##  <a name="gettext"></a>  CToolTipCtrl::GetText

도구 설명 컨트롤이 도구에 대해 유지 관리 하는 텍스트를 검색 합니다.

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>매개 변수

*str*<br/>
도구의 텍스트를 `CString` 받는 개체에 대 한 참조입니다.

*pWnd*<br/>
도구를 포함 하는 창에 대 한 포인터입니다.

*nIDTool*<br/>
도구의 ID입니다.

### <a name="remarks"></a>설명

*PWnd* 및 *nIDTool* 매개 변수는 도구를 식별 합니다. 이전에를 `CToolTipCtrl::AddTool`호출 하 여 도구 설명 컨트롤에 해당 도구를 등록 한 경우 *str* 매개 변수에서 참조 하는 개체에는 도구의 텍스트가 할당 됩니다.

##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor

도구 설명 창의 배경색을 검색 합니다.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>반환 값

배경색을 나타내는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor)의 동작을 구현 합니다.

##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor

도구 설명 창에서 텍스트 색을 검색 합니다.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>반환 값

텍스트 색을 나타내는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)의 동작을 구현 합니다.

##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle

현재 도구 설명 컨트롤의 제목을 검색 합니다.

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*pttgt*|제한이 ToolTip 컨트롤에 대 한 정보를 포함 하는 [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) 구조체에 대 한 포인터입니다. 이 메서드가 반환 될 때 [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) 구조체의 *pszTitle* 멤버는 제목의 텍스트를 가리킵니다.|

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에 설명 된 [TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle) 메시지를 보냅니다.

##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount

도구 설명 컨트롤에 등록 된 도구 수를 검색 합니다.

```
int GetToolCount() const;
```

### <a name="return-value"></a>반환 값

도구 설명 컨트롤에 등록 된 도구 수입니다.

##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo

도구 설명 컨트롤이 도구에 대해 유지 관리 하는 정보를 검색 합니다.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>매개 변수

*ToolInfo*<br/>
도구의 텍스트를 `TOOLINFO` 받는 개체에 대 한 참조입니다.

*pWnd*<br/>
도구를 포함 하는 창에 대 한 포인터입니다.

*nIDTool*<br/>
도구의 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`hwnd` *Ctoolinfo* 에서 참조 하는 [toolinfo](/windows/win32/api/commctrl/ns-commctrl-toolinfow) 구조의 및 `uId` 멤버가 도구를 식별 합니다. 이전 호출 `AddTool`을 통해 도구 설명 컨트롤에 해당 도구를 등록 한 경우이 구조는 `TOOLINFO` 도구에 대 한 정보로 채워집니다.

##  <a name="hittest"></a>  CToolTipCtrl::HitTest

지점을 테스트 하 여 지정 된 도구의 경계 사각형 내에 있는지 여부를 확인 하 고, 해당 하는 경우 도구에 대 한 정보를 검색 합니다.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
도구를 포함 하는 창에 대 한 포인터입니다.

*pt*<br/>
테스트할 점의 좌표 `CPoint` 를 포함 하는 개체에 대 한 포인터입니다.

*lpToolInfo*<br/>
도구에 대 한 정보를 포함 하는 [Toolinfo](/windows/win32/api/commctrl/ns-commctrl-toolinfow) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

적중 테스트 정보로 지정 된 점이 도구의 경계 사각형 내에 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수가 0이 아닌 값을 반환 하는 경우 *Lptoolinfo* 가 가리키는 구조는 점이 가리키는 사각형 내의 도구에 대 한 정보로 채워집니다.

구조 `TTHITTESTINFO` 는 다음과 같이 정의 됩니다.

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   도구의 핸들을 지정 합니다.

- `pt`

   점이 도구의 경계 사각형에 있는 경우 점의 좌표를 지정 합니다.

- `ti`

   도구에 대 한 정보입니다. `TOOLINFO` 구조체에 대 한 자세한 내용은 [CToolTipCtrl:: gettoolinfo](#gettoolinfo)를 참조 하세요.

##  <a name="pop"></a>  CToolTipCtrl::Pop

표시 된 도구 설명 창을 뷰에서 제거 합니다.

```
void Pop();
```

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_POP](/windows/win32/Controls/ttm-pop)의 동작을 구현 합니다.

##  <a name="popup"></a>  CToolTipCtrl::Popup

현재 도구 설명 컨트롤이 마지막 마우스 메시지의 좌표에 표시 되도록 합니다.

```
void Popup();
```

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에 설명 된 [TTM_POPUP](/windows/win32/Controls/ttm-popup) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 도구 설명 창을 표시 합니다.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent

처리를 위해 마우스 메시지를 도구 설명 컨트롤에 전달 합니다.

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>매개 변수

*lpMsg*<br/>
릴레이할 메시지를 포함 하는 [MSG](/windows/win32/api/winuser/ns-winuser-msg) 구조에 대 한 포인터입니다.

### <a name="remarks"></a>설명

도구 설명 컨트롤은로 `RelayEvent`전송 되는 다음 메시지만 처리 합니다.

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>예제

  [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)의 예제를 참조 하세요.

##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime

도구 설명 컨트롤에 대 한 지연 시간을 설정 합니다.

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>매개 변수

*nDelay*<br/>
새 지연 시간 (밀리초)을 지정 합니다.

*dwDuration*<br/>
검색 되는 기간 값을 지정 하는 플래그입니다. 유효한 값에 대 한 설명은 [CToolTipCtrl:: GetDelayTime](#getdelaytime) 을 참조 하세요.

*iTime*<br/>
지정 된 지연 시간 (밀리초)입니다.

### <a name="remarks"></a>설명

지연 시간은 도구 설명 창이 나타나기 전에 커서를 도구에 유지 해야 하는 시간입니다. 기본 지연 시간은 500 밀리초입니다.

##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin

도구 설명 창의 위쪽, 왼쪽, 아래쪽 및 오른쪽 여백을 설정 합니다.

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>매개 변수

*lprc*<br/>
설정할 여백 정보 `RECT` 를 포함 하는 구조체의 주소입니다. `RECT` 구조체의 멤버는 경계 사각형을 정의 하지 않습니다. 여백 정보에 대 한 설명은 [CToolTipCtrl:: GetMargin](#getmargin) 를 참조 하세요.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)의 동작을 구현 합니다.

##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth

도구 설명 창의 최대 너비를 설정 합니다.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>매개 변수

*iWidth*<br/>
설정할 최대 도구 설명 창 너비입니다.

### <a name="return-value"></a>반환 값

이전의 최대 팁 너비입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)의 동작을 구현 합니다.

##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor

도구 설명 창의 배경색을 설정 합니다.

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>매개 변수

*clr*<br/>
새 배경색입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)의 동작을 구현 합니다.

##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor

도구 설명 창의 텍스트 색을 설정 합니다.

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>매개 변수

*clr*<br/>
새 텍스트 색입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)의 동작을 구현 합니다.

##  <a name="settitle"></a>  CToolTipCtrl::SetTitle

도구 설명에 표준 아이콘 및 제목 문자열을 추가 합니다.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>매개 변수

*uIcon*<br/>
Windows SDK에서 [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) 의 *아이콘* 을 참조 하세요.

*lpstrTitle*<br/>
제목 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)의 동작을 구현 합니다.

##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo

도구 설명에서 도구에 대해 유지 관리 하는 정보를 설정 합니다.

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>매개 변수

*lpToolInfo*<br/>
설정할 정보를 지정 하는 [Toolinfo](/windows/win32/api/commctrl/ns-commctrl-toolinfow) 구조체에 대 한 포인터입니다.

##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect

도구에 대 한 새 경계 사각형을 설정 합니다.

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
도구를 포함 하는 창에 대 한 포인터입니다.

*nIDTool*<br/>
도구의 ID입니다.

*lpRect*<br/>
새 경계 사각형을 지정 하는 [RECT](/previous-versions/dd162897\(v=vs.85\)) 구조체에 대 한 포인터입니다.

##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme

도구 설명 창의 비주얼 스타일을 설정 합니다.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>매개 변수

*pszSubAppName*<br/>
설정할 비주얼 스타일을 포함 하는 유니코드 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

반환 값은 사용 되지 않습니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 [TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme) 메시지의 기능을 에뮬레이트합니다.

##  <a name="update"></a>  CToolTipCtrl::Update

현재 도구를 강제로 다시 그리도록 합니다.

```
void Update();
```

##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText

이 컨트롤의 도구에 대 한 도구 설명 텍스트를 업데이트 합니다.

```
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
도구의 텍스트에 대 한 포인터입니다.

*pWnd*<br/>
도구를 포함 하는 창에 대 한 포인터입니다.

*nIDTool*<br/>
도구의 ID입니다.

*nIDText*<br/>
도구의 텍스트를 포함 하는 문자열 리소스의 ID입니다.

## <a name="see-also"></a>참고자료

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 클래스](../../mfc/reference/ctoolbar-class.md)
