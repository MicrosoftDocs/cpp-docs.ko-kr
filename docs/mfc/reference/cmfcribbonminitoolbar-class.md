---
description: '자세히 알아보기: CMFCRibbonMiniToolBar 클래스'
title: CMFCRibbonMiniToolBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 7215349323f8039bccb24860e4e5ad663bd24bcd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273945"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar 클래스

상황별 팝업 도구 모음을 구현합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|기본 생성자입니다.|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCRibbonMiniToolBar::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|( `CMFCPopupMenu::IsRibbonMiniToolBar`을 재정의합니다.)|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|도구 모음에 표시되는 명령의 목록을 설정합니다.|
|[CMFCRibbonMiniToolBar::Show](#show)|지정된 화면 좌표에 미니 도구 모음을 표시합니다.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|상황에 맞는 메뉴와 함께 미니 도구 모음을 표시합니다.|

## <a name="remarks"></a>설명

미니 도구 모음은 일반적으로 사용자가 문서에서 개체를 선택한 후에 표시됩니다. 예를 들어 사용자가 문서 작성 프로그램에서 텍스트 블록을 선택하고 나면 애플리케이션은 텍스트 서식 지정 명령이 포함된 미니 도구 모음을 표시합니다.

마우스 포인터가 미니 도구 모음의 범위를 벗어나면 미니 도구 모음은 투명해집니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxRibbonMiniToolBar

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a> CMFCRibbonMiniToolBar:: SetCommands

도구 모음에 표시되는 명령의 목록을 설정합니다.

```cpp
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>매개 변수

*pRibbonBar*<br/>
진행 미니 도구 모음이 표시할 단추를 검색 하는 리본 표시줄입니다.

*lstCommands*<br/>
진행 미니 도구 모음에 표시 되는 명령 목록입니다. 모든 리본 범주를 검색 하 여 관련 단추를 찾습니다.

### <a name="remarks"></a>설명

미니 도구 모음에 표시 되는 명령 목록을 설정 하려면이 함수를 사용 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `SetCommands` `CMFCRibbonMiniToolBar` . 이 코드 조각은 [MS Office 2007 Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a> CMFCRibbonMiniToolBar:: Show

지정된 화면 좌표에 미니 도구 모음을 표시합니다.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 화면 좌표에서 미니 도구 모음의 가로 위치를 지정 합니다.

*y*<br/>
진행 화면 좌표에서 미니 도구 모음의 세로 위치를 지정 합니다.

### <a name="return-value"></a>반환 값

미니 도구 모음이 성공적으로 표시 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a> CMFCRibbonMiniToolBar:: ShowWithContextMenu

상황에 맞는 메뉴와 함께 미니 도구 모음을 표시합니다.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 화면 좌표에서 상황에 맞는 메뉴의 가로 위치를 지정 합니다.

*y*<br/>
진행 화면 좌표에서 상황에 맞는 메뉴의 세로 위치를 지정 합니다.

*uiMenuResID*<br/>
진행 표시할 상황에 맞는 메뉴의 리소스 ID를 지정 합니다.

*pWndOwner*<br/>
진행 상황에 맞는 메뉴에서 메시지를 수신 하는 창을 식별 합니다.

### <a name="return-value"></a>반환 값

상황에 맞는 메뉴가 성공적으로 표시 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 상황에 맞는 메뉴가 있는 미니 도구 모음을 표시 합니다. 상황에 맞는 메뉴는 미니 도구 모음 아래에 15 픽셀 배치 됩니다.

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a> CMFCRibbonMiniToolBar:: Iscontext Umode

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a> CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
