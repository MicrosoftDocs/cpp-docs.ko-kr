---
description: '자세히 알아보기: CMFCDropDownToolbarButton 클래스'
title: CMFCDropDownToolbarButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: b2a62b22a04047f2fbe4a99b2bceb12e271a2d85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293926"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 클래스

클릭할 때 일반 단추처럼 동작하는 도구 모음 단추의 한 종류입니다. 그러나 사용자가 도구 모음 단추를 누르고 있으면 드롭다운 도구 모음 ( [CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md) )이 열립니다.

## <a name="syntax"></a>구문

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|`CMFCDropDownToolbarButton` 개체를 생성합니다.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCDropDownToolbarButton:: CopyFrom](#copyfrom)|다른 도구 모음 단추의 속성을 현재 단추로 복사 합니다. [에서 CMFCToolBarButton:: copyfrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)재정의 합니다.|
|`CMFCDropDownToolbarButton::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCDropDownToolbarButton::D ropDownToolbar](#dropdowntoolbar)|드롭다운 도구 모음을 엽니다.|
|[CMFCDropDownToolbarButton:: ExportToMenuButton](#exporttomenubutton)|도구 모음 단추에서 메뉴로 텍스트를 복사 합니다. [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)을 재정의 합니다.|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|단추와 연결 된 드롭다운 도구 모음을 검색 합니다.|
|`CMFCDropDownToolbarButton::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCDropDownToolbarButton:: IsDropDown](#isdropdown)|드롭다운 도구 모음이 현재 열려 있는지 여부를 확인 합니다.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|확장 테두리를 사용 하 여 단추를 표시할 수 있는지 여부를 결정 합니다. [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)를 재정의 합니다.|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|지정 된 장치 컨텍스트 및 도킹 상태에 대 한 단추의 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)를 재정의 합니다.|
|`CMFCDropDownToolbarButton::OnCancelMode`|[WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode) 메시지를 처리 하기 위해 프레임 워크에서 호출 됩니다. ( `CMCToolBarButton::OnCancelMode`을 재정의합니다.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|단추가 새 도구 모음에 삽입 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)를 재정의 합니다.|
|[CMFCDropDownToolbarButton:: OnClick](#onclick)|사용자가 마우스 단추를 클릭할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)을 재정의 합니다.|
|[CMFCDropDownToolbarButton:: On클릭](#onclickup)|사용자가 마우스 단추를 놓을 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: on클릭](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)을 재정의 합니다.|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|부모 도구 모음이 WM_HELPHITTEST 메시지를 처리할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)를 재정의 합니다.|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|응용 프로그램에서 부모 도구 모음에 바로 가기 메뉴를 표시할 때 제공 된 메뉴를 수정 합니다. [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)를 재정의 합니다.|
|[CMFCDropDownToolbarButton:: OnDraw](#ondraw)|지정 된 스타일 및 옵션을 사용 하 여 단추를 그리기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)를 재정의 합니다.|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|**사용자 지정** 대화 상자의 **명령** 창에 단추를 그리기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)를 재정의 합니다.|
|[CMFCDropDownToolbarButton:: Serialize](#serialize)|보관 저장소에서이 개체를 읽거나 보관 파일에 기록 합니다. [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)를 재정의 합니다.|
|[CMFCDropDownToolbarButton:: SetDefaultCommand](#setdefaultcommand)|사용자가 단추를 클릭할 때 프레임 워크에서 사용 하는 기본 명령을 설정 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay)|드롭다운 도구 모음이 나타나기 전에 사용자가 마우스 단추를 누른 상태를 유지 해야 하는 기간을 지정 합니다.|

## <a name="remarks"></a>설명

는 `CMFCDropDownToolBarButton` 단추의 오른쪽 아래 모퉁이에 작은 화살표가 있다는 점에서 일반 단추와 다릅니다. 사용자가 드롭다운 도구 모음에서 단추를 선택 하면 프레임 워크는 최상위 도구 모음 단추 (오른쪽 아래 모퉁이에 작은 화살표가 있는 단추)에 해당 아이콘을 표시 합니다.

드롭다운 도구 모음을 구현 하는 방법에 대 한 자세한 내용은 [CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md)를 참조 하세요.

`CMFCDropDownToolBarButton`개체를 [cmfc기능](../../mfc/reference/cmfctoolbarmenubutton-class.md) 메뉴의 클래스 개체로 내보내고 팝업 메뉴와 함께 메뉴 단추로 표시할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a> CMFCDropDownToolbarButton:: CopyFrom

다른 도구 모음 단추의 속성을 현재 단추로 복사 합니다.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
진행 복사할 원본 단추에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 다른 도구 모음 단추를이 도구 모음 단추에 복사 합니다. *src* 는 형식 이어야 합니다 `CMFCDropDownToolbarButton` .

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a> CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

`CMFCDropDownToolbarButton` 개체를 생성합니다.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
진행 단추의 기본 텍스트입니다.

*pToolBar*<br/>
진행 `CMFCDropDownToolBar` 사용자가 단추를 누를 때 표시 되는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

생성자의 두 번째 오버 로드는 *Ptoolbar* 에서 지정 하는 도구 모음에 있는 첫 번째 단추를 드롭다운 단추로 복사 합니다.

일반적으로 드롭다운 도구 모음 단추는 *Ptoolbar* 에서 지정 하는 도구 모음에서 가장 최근에 사용한 단추의 텍스트를 사용 합니다. 단추가 메뉴 단추로 변환 되거나 **사용자 지정** 대화 상자의 **명령** 탭에 표시 될 때 *lpszName* 에 지정 된 텍스트를 사용 합니다. **사용자 지정** 대화 상자에 대 한 자세한 내용은 [CMFCToolBarsCustomizeDialog 클래스](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)를 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCDropDownToolbarButton` . 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a> CMFCDropDownToolbarButton::D ropDownToolbar

드롭다운 도구 모음을 엽니다.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 드롭다운 프레임의 부모 창이 며 드롭다운 도구 모음 단추의 부모 창을 사용 하는 경우 NULL입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[CMFCDropDownToolbarButton:: OnClick](#onclick) 메서드는이 메서드를 호출 하 여 사용자가 도구 모음 단추를 누르고 있을 때 드롭다운 도구 모음을 엽니다.

이 메서드는 [CMFCDropDownFrame:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create) 메서드를 사용 하 여 드롭다운 도구 모음을 만듭니다. 부모 도구 모음이 세로로 도킹 된 경우이 메서드는 맞춤에 따라 부모 도구 모음의 왼쪽 또는 오른쪽에 드롭다운 도구 모음을 배치 합니다. 그렇지 않으면이 메서드는 드롭다운 도구 모음을 부모 도구 모음 아래에 배치 합니다.

*PWnd* 가 NULL이 고 드롭다운 도구 모음 단추에 부모 창이 없으면이 메서드는 실패 합니다.

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a> CMFCDropDownToolbarButton:: ExportToMenuButton

도구 모음 단추에서 메뉴로 텍스트를 복사 합니다.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>매개 변수

*menuButton*<br/>
진행 대상 메뉴 단추에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 0이 아니고, 실패하면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 기본 클래스 구현 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton))을 호출한 다음이 단추의 각 도구 모음 메뉴 항목이 포함 된 팝업 메뉴를 대상 메뉴 단추에 추가 합니다. 이 메서드는 팝업 메뉴에 하위 메뉴를 추가 하지 않습니다.

부모 도구 모음이 `m_pToolBar` NULL 이거나 기본 클래스 구현에서 FALSE를 반환 하는 경우이 메서드는 실패 합니다.

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a> CMFCDropDownToolbarButton::GetDropDownToolBar

단추와 연결 된 드롭다운 도구 모음을 검색 합니다.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>반환 값

단추와 연결 된 드롭다운 도구 모음입니다.

### <a name="remarks"></a>설명

이 메서드는 데이터 멤버를 반환 합니다 `m_pToolBar` .

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a> CMFCDropDownToolbarButton:: IsDropDown

드롭다운 도구 모음이 현재 열려 있는지 여부를 확인 합니다.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>반환 값

드롭다운 도구 모음이 현재 열려 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

프레임 워크는 [CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar) 메서드를 사용 하 여 드롭다운 도구 모음을 엽니다. 사용자가 드롭다운 도구 모음의 비클라이언트 영역에 있는 왼쪽 마우스 단추를 누르면 프레임 워크가 드롭다운 도구 모음을 닫습니다.

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a> CMFCDropDownToolbarButton::IsExtraSize

확장 테두리를 사용 하 여 단추를 표시할 수 있는지 여부를 결정 합니다.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>반환 값

확장 테두리를 사용 하 여 도구 모음 단추를 표시할 수 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

확장 된 테두리에 대 한 자세한 내용은 [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)를 참조 하세요.

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a> CMFCDropDownToolbarButton:: m_uiShowBarDelay

드롭다운 도구 모음이 나타나기 전에 사용자가 마우스 단추를 누른 상태를 유지 해야 하는 기간을 지정 합니다.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>설명

지연 시간은 밀리초 단위로 측정 됩니다. 기본값은 500입니다. 이 공유 데이터 멤버의 값을 변경 하 여 다른 지연을 설정할 수 있습니다.

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a> CMFCDropDownToolbarButton::OnCalculateSize

지정 된 장치 컨텍스트 및 도킹 상태에 대 한 단추의 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 장치 컨텍스트입니다.

*sizeDefault*<br/>
진행 단추의 기본 크기입니다.

*bHorz*<br/>
진행 부모 도구 모음의 도크 상태입니다. 이 매개 변수는 도구 모음이 가로로 도킹 되거나 부동 인 경우 TRUE이 고, 도구 모음이 세로로 도킹 된 경우에는 FALSE입니다.

### <a name="return-value"></a>반환 값

`SIZE`단추의 크기 (픽셀)를 포함 하는 구조체입니다.

### <a name="remarks"></a>설명

이 메서드는 드롭다운 화살표의 너비를 단추 크기의 가로 차원에 추가 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize))을 확장 합니다.

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCDropDownToolbarButton::OnChangeParentWnd

단추가 새 도구 모음에 삽입 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 새 부모 창입니다.

### <a name="remarks"></a>설명

이 메서드는 텍스트 레이블 ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext))을 지우고 [CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) 및 [CMFCToolBarButton:: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) 데이터 멤버를 FALSE로 설정 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))을 재정의 합니다.

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a> CMFCDropDownToolbarButton:: OnClick

사용자가 마우스 단추를 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 도구 모음 단추의 부모 창입니다.

*bDelay*<br/>
진행 메시지를 지연 시간으로 처리 해야 하면 TRUE입니다.

### <a name="return-value"></a>반환 값

단추가 클릭 메시지를 처리 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 드롭다운 도구 모음의 상태를 업데이트 하 여 기본 클래스 구현인 [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)을 확장 합니다.

사용자가 도구 모음 단추를 클릭 하면이 메서드는 [CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay) 데이터 멤버로 지정 된 시간 동안 대기한 다음 [CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar) 메서드를 사용 하 여 드롭다운 도구 모음을 여는 타이머를 만듭니다. 이 메서드는 사용자가 도구 모음 단추를 두 번 클릭할 때 드롭다운 도구 모음을 닫습니다.

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a> CMFCDropDownToolbarButton:: On클릭

사용자가 마우스 단추를 놓을 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>반환 값

단추가 클릭 메시지를 처리 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 드롭다운 도구 모음의 상태를 업데이트 하 여 기본 클래스 구현인 [CMFCToolBarButton:: on클릭](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)을 확장 합니다.

이 메서드는 활성 상태인 경우 드롭다운 도구 모음 타이머를 중지 합니다. 드롭다운 도구 모음이 열려 있는 경우이를 닫습니다.

드롭다운 도구 모음 및 드롭다운 도구 모음 타이머에 대 한 자세한 내용은 [CMFCDropDownToolbarButton:: OnClick](#onclick)을 참조 하세요.

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a> CMFCDropDownToolbarButton::OnContextHelp

부모 도구 모음이 WM_HELPHITTEST 메시지를 처리할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 도구 모음 단추의 부모 창입니다.

### <a name="return-value"></a>반환 값

단추가 도움말 메시지를 처리 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 *Bdelay* 가 FALSE로 설정 된 [CMFCDropDownToolbarButton:: OnClick](#onclick) 메서드를 호출 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp))을 확장 합니다. 이 메서드는 [CMFCDropDownToolbarButton:: OnClick](#onclick)에서 반환 된 값을 반환 합니다.

WM_HELPHITTEST 메시지에 대 한 자세한 내용은 [TN028: Context-Sensitive Help Support](../../mfc/tn028-context-sensitive-help-support.md)을 참조 하십시오.

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a> CMFCDropDownToolbarButton::OnCustomizeMenu

응용 프로그램에서 부모 도구 모음에 바로 가기 메뉴를 표시할 때 제공 된 메뉴를 수정 합니다.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>매개 변수

*pMenu*<br/>
진행 사용자 지정할 메뉴입니다.

### <a name="return-value"></a>반환 값

이 메서드는 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 다음 메뉴 항목을 사용 하지 않도록 설정 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu))을 확장 합니다.

- **단추 이미지 복사**

- **단추 모양**

- **이미지**

- **Text**

- **이미지 및 텍스트**

프레임 워크가 사용자 지정 모드에서 표시 하는 바로 가기 메뉴를 수정 하려면이 메서드를 재정의 합니다.

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a> CMFCDropDownToolbarButton:: OnDraw

지정 된 스타일 및 옵션을 사용 하 여 단추를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 장치 컨텍스트입니다.

*rect*<br/>
진행 단추의 경계 사각형입니다.

*pImages*<br/>
진행 단추와 연결 된 도구 모음 이미지의 컬렉션입니다.

*bHorz*<br/>
진행 부모 도구 모음의 도크 상태입니다. 이 매개 변수는 단추가 가로로 도킹 된 경우 TRUE이 고 단추가 세로로 도킹 되 면 FALSE입니다.

*bCustomizeMode*<br/>
진행 도구 모음이 사용자 지정 모드에 있는지 여부를 지정 합니다. 이 매개 변수는 도구 모음이 사용자 지정 모드에 있으면 TRUE이 고 도구 모음이 사용자 지정 모드에 있지 않으면 FALSE입니다.

*bHighlight*<br/>
진행 단추가 강조 표시 되는지 여부를 지정 합니다. 이 매개 변수는 단추가 강조 표시 된 경우 TRUE이 고 단추가 강조 표시 되지 않으면 FALSE입니다.

*bDrawBorder*<br/>
진행 단추에 테두리를 표시할지 여부를 지정 합니다. 이 매개 변수는 단추에 테두리가 표시 되어야 하는 경우 TRUE이 고, 단추에 테두리가 표시 되지 않으면 FALSE입니다.

*bGrayDisabledButtons*<br/>
진행 사용 하지 않도록 설정 된 단추를 음영 할지 아니면 비활성화 된 이미지 컬렉션을 사용할지를 지정 합니다. 이 매개 변수는 비활성화 된 단추를 회색으로 표시 해야 하는 경우 TRUE이 고,이 메서드가 비활성화 된 이미지 컬렉션을 사용 해야 하는 경우 FALSE

### <a name="remarks"></a>설명

이 메서드를 재정의 하 여 도구 모음 단추 그리기를 사용자 지정할 수 있습니다.

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a> CMFCDropDownToolbarButton::OnDrawOnCustomizeList

**사용자 지정** 대화 상자의 **명령** 창에 단추를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 장치 컨텍스트입니다.

*rect*<br/>
진행 단추의 경계 사각형입니다.

*bSelected*<br/>
진행 단추를 선택 했는지 여부를 나타냅니다. 이 매개 변수가 TRUE 이면 단추가 선택 됩니다. 이 매개 변수가 FALSE 이면 단추가 선택 되지 않습니다.

### <a name="return-value"></a>반환 값

지정 된 장치 컨텍스트에 있는 단추의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 소유자 그리기 목록 상자에 단추를 표시 해야 하는 경우 사용자 지정 대화 상자 ( **명령** 탭)에서 호출 됩니다.

이 메서드는 단추의 텍스트 레이블을 단추의 이름 (즉, 생성자에 전달 된 *lpszName* 매개 변수 값)으로 변경 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist))을 확장 합니다.

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a> CMFCDropDownToolbarButton:: Serialize

보관 저장소에서이 개체를 읽거나 보관 파일에 기록 합니다.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
진행 `CArchive` Serialize 할 또는를 사용할 개체입니다.

### <a name="remarks"></a>설명

이 메서드는 부모 도구 모음의 리소스 ID를 serialize 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize))을 확장 합니다. 보관 파일이 로드 될 때 ( [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading) 은 0이 아닌 값을 반환 함)이 메서드는 `m_pToolBar` 데이터 멤버를 SERIALIZE 된 리소스 ID를 포함 하는 도구 모음으로 설정 합니다.

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a> CMFCDropDownToolbarButton:: SetDefaultCommand

사용자가 단추를 클릭할 때 프레임 워크에서 사용 하는 기본 명령을 설정 합니다.

```cpp
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 기본 명령의 ID입니다.

### <a name="remarks"></a>설명

사용자가 단추를 클릭할 때 프레임 워크가 실행 하는 기본 명령을 지정 하려면이 메서드를 호출 합니다. *Uicmd* 로 지정 된 명령 ID를 가진 항목은 부모 드롭다운 도구 모음에 있어야 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Cmfc, Menubutton 클래스](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)
