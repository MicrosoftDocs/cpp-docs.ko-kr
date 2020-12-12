---
description: '자세히 알아보기: CMFCToolBarEditBoxButton 클래스'
title: CMFCToolBarEditBoxButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: 1cdf401d7ef6409163334104b20d6ce92940f677
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163901"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton 클래스

편집 컨트롤 ( [CEdit 클래스](../../mfc/reference/cedit-class.md))을 포함 하는 도구 모음 단추입니다.

## <a name="syntax"></a>구문

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|`CMFCToolBarEditBoxButton` 개체를 생성합니다.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCToolBarEditBoxButton:: CanBeStretched](#canbestretched)|사용자 지정 중에 사용자가 단추를 늘릴 수 있는지 여부를 지정 합니다. [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton:: CopyFrom](#copyfrom)|다른 도구 모음 단추의 속성을 현재 단추로 복사 합니다. [에서 CMFCToolBarButton:: copyfrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)재정의 합니다.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: CreateEdit](#createedit)|단추에 새 편집 컨트롤을 만듭니다.|
|`CMFCToolBarEditBoxButton::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCToolBarEditBoxButton:: GetByCmd](#getbycmd)|`CMFCToolBarEditBoxButton`응용 프로그램에서 지정 된 명령 ID를 가진 첫 번째 개체를 검색 합니다.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|지정 된 명령 ID를 가진 첫 번째 편집 상자 도구 모음 컨트롤의 텍스트를 검색 합니다.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|단추와 연결 된 바로 가기 메뉴의 리소스 ID를 검색 합니다.|
|[CMFCToolBarEditBoxButton:: GetEditBorder](#geteditborder)|편집 상자 단추의 편집 부분에 대 한 경계 사각형을 검색 합니다.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: GetEditBox](#geteditbox)|단추에 포함 된 편집 컨트롤에 대 한 포인터를 반환 합니다.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|도구 모음 단추와 연결 된 창 핸들을 검색 합니다. [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|다시 그려야 하는 단추의 클라이언트 영역 영역을 검색 합니다. [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)를 재정의 합니다.|
|`CMFCToolBarEditBoxButton::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|사용자가 단추를 클릭할 때 단추의 테두리가 표시 되는지 여부를 결정 합니다. [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|편집 상자 단추에 평면 스타일을 사용할지 여부를 결정 합니다.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|단추가 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 처리 하는지 여부를 지정 합니다. [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|**사용자 지정** 대화 상자에 단추가 추가 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)를 재정의 합니다.|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|지정 된 장치 컨텍스트 및 도킹 상태에 대 한 단추의 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|단추가 새 도구 모음에 삽입 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton:: OnClick](#onclick)|사용자가 마우스 단추를 클릭할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)을 재정의 합니다.|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|부모 도구 모음이 WM_CTLCOLOR 메시지를 처리할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)를 재정의 합니다.|
|`CMFCToolBarEditBoxButton::OnDraw`|지정 된 스타일 및 옵션을 사용 하 여 단추를 그리기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)를 재정의 합니다.|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|**사용자 지정** 대화 상자의 **명령** 창에 단추를 그리기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|전역 글꼴이 변경 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton:: OnMove](#onmove)|부모 도구 모음이 이동 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton:: OnShow](#onshow)|단추를 표시 하거나 숨길 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton:: OnSize](#onsize)|부모 도구 모음이 크기나 위치를 변경 하 고이 변경으로 인해 크기가 변경 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)를 재정의 합니다.|
|[CMFCToolBarEditBoxButton:: OnUpdateToolTip](#onupdatetooltip)|부모 도구 모음에서 도구 설명 텍스트를 업데이트할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)를 재정의 합니다.|
|`CMFCToolBarEditBoxButton::Serialize`|보관 저장소에서이 개체를 읽거나 보관 파일에 기록 합니다. [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)를 재정의 합니다.|
|`CMFCToolBarEditBoxButton::SetACCData`|제공 된 `CAccessibilityData` 개체를 도구 모음 단추에 있는 내게 필요한 옵션 데이터로 채웁니다. [CMFCToolBarButton:: SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)를 재정의 합니다.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContents](#setcontents)|단추의 편집 컨트롤에 텍스트를 설정 합니다.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall)|지정 된 명령 ID를 가진 컨트롤 편집 단추를 찾고 해당 단추의 편집 컨트롤에 텍스트를 설정 합니다.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|단추와 연결 된 바로 가기 메뉴의 리소스 ID를 지정 합니다.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|응용 프로그램에 있는 편집 상자 단추의 평면 스타일 모양을 지정 합니다.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: system.windows.forms.control.setstyle](#setstyle)|단추의 스타일을 지정 합니다. [CMFCToolBarButton:: system.windows.forms.control.setstyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)를 재정의 합니다.|

## <a name="remarks"></a>설명

도구 모음에 편집 상자 단추를 추가 하려면 다음 단계를 수행 합니다.

1. 부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다.

2. 개체를 생성 `CMFCToolBarEditBoxButton` 합니다.

3. AFX_WM_RESETTOOLBAR 메시지를 처리 하는 메시지 처리기에서 [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)를 사용 하 여 더미 단추를 새 콤보 상자 단추로 바꿉니다.

자세한 내용은 [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `CMFCToolBarEditBoxButton` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 사용자 지정 중에 사용자가 단추를 확장할 수 있도록 지정 하 고, 사용자가 단추를 클릭 하 고, 텍스트 상자 컨트롤의 텍스트를 설정 하 고, 응용 프로그램에서 편집 상자 단추의 평면 스타일 모양을 지정 하 고, 도구 모음 편집 상자 컨트롤의 스타일을 지정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbareditboxbutton

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a> CMFCToolBarEditBoxButton:: CanBeStretched

사용자 지정 중에 사용자가 단추를 늘릴 수 있는지 여부를 지정 합니다.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>반환 값

이 메서드는 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

기본적으로 프레임 워크는 사용자 지정 중에 사용자가 도구 모음 단추를 늘이지 못하게 합니다. 이 메서드는 사용자 지정 중에 사용자가 편집 상자 도구 모음 단추를 스트레치할 수 있도록 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))을 확장 합니다.

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a> CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) 개체를 생성 합니다.

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 컨트롤 ID를 지정 합니다.

*iImage*<br/>
진행 도구 모음 이미지의 인덱스 (0부터 시작)를 지정 합니다. 이 이미지는 [Cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md) 클래스에서 유지 관리 하는 [Cmfctoolbar images 클래스](../../mfc/reference/cmfctoolbarimages-class.md) 개체에 있습니다.

*dwStyle*<br/>
진행 편집 컨트롤 스타일을 지정 합니다.

*iWidth*<br/>
진행 편집 컨트롤의 너비 (픽셀)를 지정 합니다.

### <a name="remarks"></a>설명

기본 생성자는 편집 컨트롤 스타일을 다음 조합으로 설정 합니다.

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

컨트롤의 기본 너비는 150 픽셀입니다.

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a> CMFCToolBarEditBoxButton:: CopyFrom

다른 도구 모음 단추의 속성을 현재 단추로 복사 합니다.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
진행 복사할 원본 단추에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 다른 도구 모음 단추를이 도구 모음 단추에 복사 합니다. *src* 는 형식 이어야 합니다 `CMFCToolBarEditBoxButton` .

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a> CMFCToolBarEditBoxButton:: CreateEdit

단추에 새 편집 컨트롤을 만듭니다.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 편집 컨트롤의 부모 창을 지정 합니다. NULL이 아니어야 합니다.

*rect*<br/>
진행 편집 컨트롤의 크기와 위치를 지정 합니다.

### <a name="return-value"></a>반환 값

새로 만든 편집 컨트롤에 대 한 포인터입니다. 컨트롤의 생성과 첨부 파일이 실패 하는 경우 NULL입니다.

### <a name="remarks"></a>설명

`CMFCToolBarEditBoxButton`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `CreateEdit` Windows 편집 컨트롤을 만들고이를 개체에 연결 `CMFCToolBarEditBoxButton` 합니다.

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a> CMFCToolBarEditBoxButton:: GetByCmd

`CMFCToolBarEditBoxButton`응용 프로그램에서 지정 된 명령 ID를 가진 첫 번째 개체를 검색 합니다.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 검색할 단추의 명령 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 `CMFCToolBarEditBoxButton` 명령 ID를 가진 응용 프로그램의 첫 번째 개체 이거나, 해당 개체가 없으면 NULL입니다.

### <a name="remarks"></a>설명

이 공유 유틸리티 메서드는 [CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall) 및 [CMFCToolBarEditBoxButton:: GetContentsAll](#getcontentsall) 같은 메서드에서 지정 된 명령 ID를 가진 첫 번째 편집 상자 도구 모음 컨트롤의 텍스트를 설정 하거나 가져오는 데 사용 됩니다.

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a> CMFCToolBarEditBoxButton::GetContentsAll

지정 된 명령 ID를 가진 첫 번째 편집 상자 도구 모음 컨트롤의 텍스트를 검색 합니다.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 콘텐츠를 검색할 단추의 명령 ID입니다.

### <a name="return-value"></a>반환 값

`CString`지정 된 명령 ID를 가진 첫 번째 편집 상자 도구 모음 컨트롤의 텍스트를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

`CMFCToolBarEditBoxButton`지정 된 명령 ID를 가진 개체가 없는 경우이 메서드는 빈 문자열을 반환 합니다.

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a> CMFCToolBarEditBoxButton::GetContextMenuID

단추와 연결 된 바로 가기 메뉴의 리소스 ID를 검색 합니다.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>반환 값

단추와 연결 된 바로 가기 메뉴의 리소스 ID 이거나, 단추에 연결 된 바로 가기 메뉴가 없으면 0입니다.

### <a name="remarks"></a>설명

프레임 워크는 사용자가 단추를 마우스 오른쪽 단추로 클릭할 때 리소스 ID를 사용 하 여 바로 가기 메뉴를 만듭니다.

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a> CMFCToolBarEditBoxButton:: GetEditBorder

편집 상자 단추의 편집 부분에 대 한 경계 사각형을 검색 합니다.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>매개 변수

*rectBorder*<br/>
제한이 경계 사각형을 받는 개체에 대 한 참조입니다 `CRect` .

### <a name="remarks"></a>설명

이 메서드는 클라이언트 좌표로 편집 컨트롤의 경계 사각형을 검색 합니다. 각 방향에서 사각형의 크기를 한 픽셀씩 확장 합니다.

[Cmfcvisualmanager:: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) 메서드는 개체 주위에 테두리를 그릴 때이 메서드를 호출 합니다 `CMFCToolBarEditBoxButton` .

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a> CMFCToolBarEditBoxButton:: GetEditBox

단추에 포함 된 [CEdit 클래스](../../mfc/reference/cedit-class.md) 컨트롤에 대 한 포인터를 반환 합니다.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>반환 값

단추에 포함 된 [CEdit 클래스](../../mfc/reference/cedit-class.md) 컨트롤에 대 한 포인터입니다. `CEdit`컨트롤이 아직 생성 되지 않은 경우에는 NULL입니다.

### <a name="remarks"></a>설명

`CEdit` [CMFCToolBarEditBoxButton:: createedit](#createedit)를 호출 하 여 컨트롤을 만듭니다.

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a> CMFCToolBarEditBoxButton::GetHwnd

도구 모음 단추와 연결 된 창 핸들을 검색 합니다.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>반환 값

단추와 연결 된 창 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 편집 상자 단추의 편집 컨트롤 파트에 대 한 창 핸들을 반환 하 여 [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) 메서드를 재정의 합니다.

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a> CMFCToolBarEditBoxButton::GetInvalidateRect

다시 그려야 하는 단추의 클라이언트 영역 영역을 검색 합니다.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>반환 값

다시 `CRect` 그려야 하는 영역을 지정 하는 개체입니다.

### <a name="remarks"></a>설명

이 메서드는 텍스트 레이블의 영역에를 포함 하 여 기본 클래스 구현인 [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)를 확장 합니다.

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a> CMFCToolBarEditBoxButton::HaveHotBorder

사용자가 단추를 클릭할 때 단추의 테두리가 표시 되는지 여부를 결정 합니다.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>반환 값

선택 시 단추에 테두리가 표시 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 컨트롤이 표시 되는 경우 0이 아닌 값을 반환 하 여 기본 클래스 구현인 [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)를 확장 합니다.

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a> CMFCToolBarEditBoxButton::IsFlatMode

편집 상자 단추에 평면 스타일을 사용할지 여부를 결정 합니다.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>반환 값

단추에 평면 스타일이 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본적으로 편집 상자 단추에는 평면 스타일이 있습니다. [CMFCToolBarEditBoxButton:: SetFlatMode](#setflatmode) 메서드를 사용 하 여 응용 프로그램에 대 한 기본 스타일 모양을 변경 합니다.

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a> CMFCToolBarEditBoxButton::NotifyCommand

단추가 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 처리 하는지 여부를 지정 합니다.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>매개 변수

*iNotifyCode*<br/>
진행 명령과 연결 된 알림 메시지입니다.

### <a name="return-value"></a>반환 값

단추가 WM_COMMAND 메시지를 처리 하면 TRUE이 고, 부모 도구 모음에서 메시지를 처리 해야 함을 나타내려면 FALSE입니다.

### <a name="remarks"></a>설명

프레임 워크는 부모 창에 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 보내려고 할 때이 메서드를 호출 합니다.

이 메서드는 [EN_UPDATE](/windows/win32/Controls/en-update) 알림을 처리 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))을 확장 합니다. 이 개체와 동일한 명령 ID를 가진 각 편집 상자에 대해 텍스트 레이블을이 개체의 텍스트 레이블로 설정 합니다.

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a> CMFCToolBarEditBoxButton::OnAddToCustomizePage

**사용자 지정** 대화 상자에 단추가 추가 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>설명

이 메서드는이 개체와 동일한 명령 ID를 가진 도구 모음의 편집 상자 컨트롤에서 속성을 복사 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage))을 확장 합니다. 도구 모음에이 개체와 동일한 명령 ID를 가진 편집 상자 컨트롤이 없으면이 메서드는 아무 작업도 수행 하지 않습니다.

**사용자 지정** 대화 상자에 대 한 자세한 내용은 [CMFCToolBarsCustomizeDialog 클래스](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)를 참조 하세요.

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCToolBarEditBoxButton::OnChangeParentWnd

단추가 새 도구 모음에 삽입 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 새 부모 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 개체를 다시 만들어 기본 클래스 구현 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))을 재정의 합니다 `CEdit` .

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a> CMFCToolBarEditBoxButton:: OnClick

사용자가 마우스 단추를 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 사용 되지 않는.

*bDelay*<br/>
진행 사용 되지 않는.

### <a name="return-value"></a>반환 값

단추가 클릭 메시지를 처리 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 개체가 표시 되는 경우 0이 아닌 값을 반환 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick))을 재정의 합니다 `CEdit` .

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a> CMFCToolBarEditBoxButton::OnCtlColor

부모 도구 모음이 WM_CTLCOLOR 메시지를 처리할 때 프레임 워크에서 호출 됩니다.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 장치 컨텍스트입니다.

*nCtlColor*<br/>
진행 사용 되지 않는.

### <a name="return-value"></a>반환 값

전역 창 브러시에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 제공 된 장치 컨텍스트의 텍스트와 배경색을 각각 전역 텍스트 및 배경색으로 설정 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor))을 재정의 합니다.

응용 프로그램에 사용할 수 있는 전역 옵션에 대 한 자세한 내용은 [AFX_GLOBAL_DATA 구조](../../mfc/reference/afx-global-data-structure.md)를 참조 하세요.

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a> CMFCToolBarEditBoxButton::OnGlobalFontsChanged

전역 글꼴이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>설명

이 메서드는 컨트롤의 글꼴을 전역 글꼴의 글꼴을 변경 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))을 확장 합니다.

응용 프로그램에 사용할 수 있는 전역 옵션에 대 한 자세한 내용은 [AFX_GLOBAL_DATA 구조](../../mfc/reference/afx-global-data-structure.md)를 참조 하세요.

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a> CMFCToolBarEditBoxButton:: OnMove

부모 도구 모음이 이동 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnMove();
```

### <a name="remarks"></a>설명

이 메서드는 내부 개체의 위치를 업데이트 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove))을 재정의 합니다. `CEdit`

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a> CMFCToolBarEditBoxButton:: OnShow

단추를 표시 하거나 숨길 때 프레임 워크에서 호출 됩니다.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
진행 단추의 표시 여부를 지정 합니다. 이 매개 변수가 TRUE 이면 단추가 표시 됩니다. 그렇지 않으면 단추가 표시 되지 않습니다.

### <a name="remarks"></a>설명

이 메서드는 *Bshow* 가 TRUE 인 경우 단추를 표시 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow))을 확장 합니다. 그렇지 않으면이 메서드는 단추를 숨깁니다.

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a> CMFCToolBarEditBoxButton:: OnSize

부모 도구 모음이 크기나 위치를 변경 하 고이 변경으로 인해 크기가 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>매개 변수

*iSize*<br/>
진행 단추의 새 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 개체의 크기와 위치를 업데이트 하 여 기본 클래스 구현인 [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)를 재정의 합니다 `CEdit` .

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a> CMFCToolBarEditBoxButton:: OnUpdateToolTip

부모 도구 모음에서 도구 설명 텍스트를 업데이트할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 사용 되지 않는.

*iButtonIndex*<br/>
진행 사용 되지 않는.

*wndToolTip*<br/>
진행 도구 설명 텍스트를 표시 하는 컨트롤입니다.

*str*<br/>
제한이 `CString` 업데이트 된 도구 설명 텍스트를 받는 개체입니다.

### <a name="return-value"></a>반환 값

메서드가 도구 설명 텍스트를 업데이트 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 단추의 편집 부분과 연결 된 도구 설명 텍스트를 표시 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))을 확장 합니다. 내부 `CEdit` 개체가 NULL 이거나 개체의 창 핸들이 `CEdit` 기존 창을 식별 하지 않는 경우이 메서드는 아무 작업도 수행 하지 않고 FALSE를 반환 합니다.

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a> CMFCToolBarEditBoxButton:: SetContents

텍스트 상자 컨트롤의 텍스트를 설정 합니다.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>매개 변수

*s 내용*<br/>
진행 설정할 새 텍스트를 지정 합니다.

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a> CMFCToolBarEditBoxButton::SetContentsAll

지정 된 명령 ID를 가진 [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) 개체를 찾아 해당 텍스트 상자에 지정 된 텍스트를 설정 합니다.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 텍스트가 변경 될 컨트롤의 명령 ID를 지정 합니다.

*strContents*<br/>
진행 설정할 새 텍스트를 지정 합니다.

### <a name="return-value"></a>반환 값

텍스트가 설정 된 경우 0이 아닌 값입니다. `CMFCToolBarEditBoxButton` 지정 된 명령 ID를 가진 컨트롤이 없는 경우 0입니다.

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a> CMFCToolBarEditBoxButton::SetContextMenuID

단추와 연결 된 바로 가기 메뉴의 리소스 ID를 지정 합니다.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 바로 가기 메뉴의 리소스 ID입니다.

### <a name="remarks"></a>설명

프레임 워크는 사용자가 도구 모음 단추를 마우스 오른쪽 단추로 클릭할 때 리소스 ID를 사용 하 여 바로 가기 메뉴를 만듭니다.

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a> CMFCToolBarEditBoxButton::SetFlatMode

응용 프로그램에 있는 편집 상자 단추의 평면 스타일 모양을 지정 합니다.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>매개 변수

*bFlat*<br/>
진행 편집 상자 단추의 평면 스타일입니다. 이 매개 변수가 TRUE 이면 평면 스타일 모양이 사용 됩니다. 그렇지 않으면 평면 스타일 모양이 사용 하지 않도록 설정 됩니다.

### <a name="remarks"></a>설명

편집 상자 단추의 기본 평면 스타일은 TRUE입니다. [CMFCToolBarEditBoxButton:: IsFlatMode](#isflatmode) 메서드를 사용 하 여 응용 프로그램에 대 한 기본 스타일 모양을 검색 합니다.

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a> CMFCToolBarEditBoxButton:: System.windows.forms.control.setstyle

도구 모음 편집 상자 컨트롤의 스타일을 지정 합니다.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*nStyle*<br/>
진행 설정할 새 스타일입니다.

### <a name="remarks"></a>설명

이 메서드는 [CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) 을 *nstyle* 으로 설정 합니다. 또한 응용 프로그램이 사용자 지정 모드에 있을 때 텍스트 상자를 사용 하지 않도록 설정 하 고 응용 프로그램이 사용자 지정 모드에 있지 않을 때이를 사용 하도록 설정 합니다 ( [Cmfctoolbar:: SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) 및 [cmfctoolbar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)참조). 유효한 스타일 플래그 목록은 [ToolBar 컨트롤 스타일](../../mfc/reference/toolbar-control-styles.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit 클래스](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)
