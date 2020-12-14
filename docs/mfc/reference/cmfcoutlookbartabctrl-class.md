---
description: '자세히 알아보기: CMFCOutlookBarTabCtrl 클래스'
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: b969fbb592fc3098dc8d287004fab90da6f30111
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333498"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

Microsoft Outlook의 **탐색 창** 과 시각적으로 유사한 탭 컨트롤입니다.
자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|기본 생성자입니다.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl:: AddControl](#addcontrol)|Windows 컨트롤을 Outlook 표시줄에 새 탭으로 추가 합니다.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|사용자가 탭의 이름을 바꿀 때 표시 되는 편집 상자의 크기를 결정 하기 위해 프레임 워크에서 호출 됩니다 .를 재정의 `CMFCBaseTabCtrl::CalcRectEdit` 합니다.|
|[CMFCOutlookBarTabCtrl:: CanShowFewerPageButtons](#canshowfewerpagebuttons)|크기 조정 작업을 수행 하는 동안 호출 되어 현재 표시 되는 것 보다 더 많은 Outlook 표시줄 탭 페이지 단추가 표시 될 수 있는지 여부를 확인 합니다.|
|[CMFCOutlookBarTabCtrl:: Canshow모-Epagebutton](#canshowmorepagebuttons)|현재 표시 되는 것 보다 더 많은 Outlook 표시줄 탭 페이지 단추를 표시할 수 있는지 확인 하기 위해 크기 조정 작업 중에 프레임 워크에서 호출 됩니다.|
|[CMFCOutlookBarTabCtrl:: Create](#create)|Outlook 표시줄 탭 컨트롤을 만듭니다.|
|`CMFCOutlookBarTabCtrl::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCOutlookBarTabCtrl:: EnableAnimation](#enableanimation)|활성 탭 사이에서 전환 하는 동안 발생 하는 애니메이션을 사용할 수 있는지 여부를 지정 합니다.|
|[CMFCOutlookBarTabCtrl:: EnableInPlaceEdit](#enableinplaceedit)|사용자가 Outlook 표시줄의 탭 단추에서 텍스트 레이블을 수정할 수 있는지 여부를 지정 합니다. [CMFCBaseTabCtrl:: EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit)를 재정의 합니다.|
|[CMFCOutlookBarTabCtrl:: EnableScrollButtons](#enablescrollbuttons)|사용자가 Outlook 표시줄 창에 있는 단추를 스크롤할 수 있도록 하는 단추를 사용할 수 있도록 프레임 워크에서 호출 됩니다.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|지정된 지점에 포함된 창을 확인합니다. [CMFCBaseTabCtrl:: FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd)를 재정의 합니다.|
|[CMFCOutlookBarTabCtrl:: GetBorderSize](#getbordersize)|Outlook tab 컨트롤의 테두리 크기를 반환 합니다.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|탭 컨트롤의 탭 영역 크기 및 위치를 검색합니다. [CMFCBaseTabCtrl:: GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea)를 재정의 합니다.|
|`CMFCOutlookBarTabCtrl::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCOutlookBarTabCtrl:: GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl:: IsAnimation](#isanimation)|활성 탭 사이에서 전환 하는 동안 발생 하는 애니메이션을 사용할 수 있는지 여부를 결정 합니다.|
|[CMFCOutlookBarTabCtrl:: IsMode2003](#ismode2003)|Outlook 표시줄 탭 컨트롤이 Microsoft Outlook 2003을 에뮬레이트하는 모드에 있는지 여부를 확인 합니다.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|지점이 탭 영역 내에 있는지 여부를 확인합니다. [CMFCBaseTabCtrl:: IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea)를 재정의 합니다.|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|탭이 분리 가능한지 여부를 나타냅니다. [CMFCBaseTabCtrl:: IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable)를 재정의 합니다.|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|탭이 삽입 되거나 제거 될 때 프레임 워크에서 호출 됩니다. ( `CMFCBaseTabCtrl::OnChangeTabs`을 재정의합니다.)|
|[CMFCOutlookBarTabCtrl:: OnShowFewerPageButtons](#onshowfewerpagebuttons)|표시 되는 탭 페이지 단추 수를 줄이기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCOutlookBarTabCtrl:: Onshow모 (Epagebutton)](#onshowmorepagebuttons)|표시 되는 탭 페이지 단추 수를 늘리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCOutlookBarTabCtrl:: OnShowOptions](#onshowoptions)|**탐색 창 옵션** 대화 상자를 표시 합니다.|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|탭 컨트롤의 내부 레이아웃을 다시 계산합니다. [CMFCBaseTabCtrl:: RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout)를 재정의 합니다.|
|[CMFCOutlookBarTabCtrl:: SetActiveTab](#setactivetab)|활성 탭을 설정 합니다. ( [CMFCBaseTabCtrl:: SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab)를 재정의 합니다.)|
|[CMFCOutlookBarTabCtrl:: SetBorderSize](#setbordersize)|Outlook tab 컨트롤의 테두리 크기를 설정 합니다.|
|[CMFCOutlookBarTabCtrl:: SetPageButtonTextAlign](#setpagebuttontextalign)|Outlook 표시줄의 탭 단추에서 텍스트 레이블의 맞춤을 설정 합니다.|
|[CMFCOutlookBarTabCtrl:: Set Imagelist](#settoolbarimagelist)|Outlook 2003 모드에서 Outlook 표시줄의 아래쪽에 표시 되는 아이콘을 포함 하는 비트맵을 설정 합니다 ( [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)참조).|
|[CMFCOutlookBarTabCtrl:: SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>설명

도킹을 지 원하는 Outlook 표시줄을 만들려면 개체를 사용 `CMFCOutlookBar` 하 여 outlook 표시줄 탭 컨트롤을 호스팅합니다. 자세한 내용은 [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 개체를 초기화 하 `CMFCOutlookBarTabCtrl` 고 클래스에서 다양 한 메서드를 사용 하는 방법을 보여 줍니다 `CMFCOutlookBarTabCtrl` . 이 예제에서는 Outlook 표시줄의 탭 페이지 단추에서 텍스트 레이블의 내부 편집을 사용 하도록 설정 하 고, 애니메이션을 사용 하도록 설정 하 고, 사용자가 Outlook 표시줄 창에서 단추를 통해 스크롤하고, Outlook 탭 컨트롤의 테두리 크기를 설정 하 고, Outlook 표시줄의 탭 단추에서 텍스트 레이블의 맞춤을 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [Outlook Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxoutlookbartabctrl

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a> CMFCOutlookBarTabCtrl:: AddControl

Windows 컨트롤을 Outlook 표시줄에 새 탭으로 추가 합니다.

```cpp
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>매개 변수

*pWndCtrl*<br/>
진행 추가할 컨트롤에 대 한 포인터입니다.

*lpszName*<br/>
진행 탭의 이름을 지정 합니다.

*bDetachable*<br/>
진행 TRUE 이면 페이지가 분리 가능으로 생성 됩니다.

*nImageID*<br/>
진행 새 탭에 표시할 이미지에 대 한 내부 이미지 목록의 이미지 인덱스입니다.

*Dwcontrol바 스타일*<br/>
진행 래핑된 도킹 창에 대 한 AFX_ CBRS_ * 스타일을 지정 합니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 outlook 표시줄의 새 페이지로 컨트롤을 추가 합니다.

이 함수는 [CMFCBaseTabCtrl:: AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)에서 내부적으로 호출 됩니다.

*Bdetachable* 를 TRUE로 설정 하면는 `AddControl` 내부적으로 개체를 만들고 `CDockablePaneAdapter` 추가 된 컨트롤을 래핑합니다. 탭 창의 런타임 클래스를의 런타임 클래스로 자동으로 설정 하 `CMFCOutlookBar` 고 부동 프레임의 런타임 클래스를로 설정 `CMultiPaneFrameWnd` 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `AddControl` `CMFCOutlookBarTabCtrl` . 이 코드 조각은 [Outlook Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a> CMFCOutlookBarTabCtrl:: CanShowFewerPageButtons

크기 조정 작업을 수행 하는 동안 프레임 워크에서 호출 되어 현재 표시 되는 것 보다 더 많은 Outlook 표시줄 탭 페이지 단추를 표시할 수 있는지 여부를 확인 합니다.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>반환 값

단추가 두 개 이상 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

Outlook 표시줄 탭 컨트롤은 사용 가능한 공간의 양에 따라 디스플레이에서 탭을 동적으로 추가 하거나 제거 합니다. 이 메서드는 프레임 워크에서 해당 프로세스를 지 원하는 데 사용 됩니다.

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a> CMFCOutlookBarTabCtrl:: Canshow모-Epagebutton

현재 표시 되는 것 보다 더 많은 Outlook 표시줄 탭 페이지 단추를 표시할 수 있는지 여부를 확인 하기 위해 크기 조정 작업 중에 프레임 워크에서 호출 됩니다.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>반환 값

현재 표시 되지 않는 단추가 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

Outlook 표시줄 탭 컨트롤은 사용 가능한 공간의 양에 따라 디스플레이에서 탭을 동적으로 추가 하거나 제거 합니다. 이 메서드는 프레임 워크에서 해당 프로세스를 지 원하는 데 사용 됩니다.

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a> CMFCOutlookBarTabCtrl:: Create

Outlook 표시줄 탭 컨트롤을 만듭니다.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 초기 크기와 위치 (픽셀)를 지정 합니다.

*pParentWnd*<br/>
진행 부모 창을 가리킵니다. NULL이 아니어야 합니다.

*nID*<br/>
진행 컨트롤 ID입니다.

### <a name="return-value"></a>반환 값

컨트롤이 성공적으로 만들어진 경우에는 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

일반적으로 [CMFCOutlookBar 클래스가](../../mfc/reference/cmfcoutlookbar-class.md) 프로세스의 WM_CREATE 메시지를 제어 하는 경우 outlook 표시줄 탭 컨트롤이 생성 됩니다.

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a> CMFCOutlookBarTabCtrl:: EnableAnimation

활성 탭 사이에서 전환 하는 동안 발생 하는 애니메이션을 사용할 수 있는지 여부를 지정 합니다.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 애니메이션을 사용 하거나 사용 하지 않도록 설정할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

애니메이션을 사용 하거나 사용 하지 않도록 설정 하려면이 함수를 호출 합니다. 사용자가 탭 페이지를 열면 애니메이션이 사용 하도록 설정 된 경우 페이지의 캡션이 위나 아래로 이동 합니다. 애니메이션을 사용 하지 않도록 설정 하면 페이지가 즉시 활성화 됩니다.

기본적으로 애니메이션은 사용 하도록 설정 되어 있습니다.

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a> CMFCOutlookBarTabCtrl:: EnableInPlaceEdit

사용자가 Outlook 표시줄의 탭 페이지 단추에서 텍스트 레이블을 수정할 수 있는지 여부를 지정 합니다.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
TRUE 이면 텍스트 레이블의 내부 편집을 사용 하도록 설정 합니다. FALSE 이면 내부 편집을 사용 하지 않도록 설정 합니다.

### <a name="remarks"></a>설명

탭 페이지 단추에서 텍스트 레이블의 내부 편집을 사용 하거나 사용 하지 않도록 설정 하려면이 함수를 호출 합니다. 기본적으로 내부 편집은 사용 하지 않도록 설정 됩니다.

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a> CMFCOutlookBarTabCtrl:: EnableScrollButtons

사용자가 Outlook 표시줄 창에 있는 단추를 스크롤할 수 있도록 하는 스크롤 핸들을 사용 하기 위해 프레임 워크에서 호출 됩니다.

```cpp
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 스크롤 단추를 표시할지 여부를 결정 합니다.

*bIsUp*<br/>
진행 위쪽 스크롤 막대가 표시 되는지 여부를 결정 합니다.

*bIsDown*<br/>
진행 아래쪽 스크롤 막대가 표시 되는지 여부를 결정 합니다.

### <a name="remarks"></a>설명

스크롤 단추를 표시 하도록 설정 합니다. 이 메서드는 활성 탭이 변경 되어 스크롤 단추를 복원할 때 프레임 워크에서 호출 됩니다.

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a> CMFCOutlookBarTabCtrl:: GetBorderSize

Outlook tab 컨트롤의 테두리 크기를 반환 합니다.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>반환 값

테두리 크기 (픽셀)입니다.

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a> CMFCOutlookBarTabCtrl:: GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a> CMFCOutlookBarTabCtrl:: IsAnimation

활성 탭 사이에서 전환 하는 동안 발생 하는 애니메이션을 사용할 수 있는지 여부를 지정 합니다.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>반환 값

애니메이션을 사용 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[CMFCOutlookBarTabCtrl:: enableanimation](#enableanimation) 함수를 호출 하 여 애니메이션을 활성화 하거나 비활성화 합니다.

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a> CMFCOutlookBarTabCtrl:: IsMode2003

Outlook 표시줄 탭 컨트롤이 Microsoft Outlook 2003을 에뮬레이트하는 모드에 있는지 여부를 확인 합니다.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>반환 값

Outlook 표시줄 탭 컨트롤이 Outlook 2003 모드에 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 값은 [CMFCOutlookBar:: SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)에 의해 설정 됩니다.

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a> CMFCOutlookBarTabCtrl:: OnShowFewerPageButtons

표시 되는 탭 페이지 단추 수를 줄이기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>설명

이 메서드는 컨트롤의 크기가 조정 될 때 표시 되는 페이지 탭 단추의 수를 조정 합니다.

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a> CMFCOutlookBarTabCtrl:: Onshow모 (Epagebutton)

표시 되는 탭 페이지 단추 수를 늘리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>설명

이 메서드는 컨트롤의 크기가 조정 될 때 표시 되는 탭 페이지 단추의 수를 조정 합니다.

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a> CMFCOutlookBarTabCtrl:: OnShowOptions

**탐색 창 옵션** 대화 상자를 표시 합니다.

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>설명

**탐색 창 옵션** 대화 상자를 사용 하 여 표시 되는 탭 페이지 단추와 표시 되는 순서를 선택할 수 있습니다.

이 메서드는 사용자가 컨트롤의 사용자 지정 메뉴에서 **탐색 창 옵션** 메뉴 항목을 선택할 때 프레임 워크에서 호출 됩니다.

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a> CMFCOutlookBarTabCtrl:: SetActiveTab

활성 탭을 설정 합니다. 활성 탭은 해당 내용이 표시 되는 열려 있는 탭입니다.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>매개 변수

*iTab*<br/>
진행 열 탭의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 탭이 성공적으로 열리면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

활성 탭을 설정 하는 시각적 효과는 애니메이션을 사용 하도록 설정 했는지 여부에 따라 달라 집니다. 자세한 내용은 [CMFCOutlookBarTabCtrl:: EnableAnimation](#enableanimation)를 참조 하세요.

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a> CMFCOutlookBarTabCtrl:: SetBorderSize

Outlook tab 컨트롤의 테두리 크기를 설정 합니다.

```cpp
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>매개 변수

*nBorderSize*<br/>
진행 새 테두리 크기 (픽셀)를 지정 합니다.

### <a name="remarks"></a>설명

새 테두리 크기를 설정 하 고 outlook 창 레이아웃을 다시 계산 합니다.

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a> CMFCOutlookBarTabCtrl:: SetPageButtonTextAlign

Outlook 표시줄의 탭 단추에서 텍스트 레이블의 맞춤을 설정 합니다.

```cpp
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>매개 변수

*uiAlign*<br/>
진행 텍스트 맞춤을 지정 합니다.

*bRedraw*<br/>
진행 TRUE 이면 outlook 창이 다시 그려집니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 페이지 단추에 대 한 텍스트 맞춤을 변경할 수 있습니다.

*Uialign* 은 다음 값 중 하나일 수 있습니다.

|상수|의미|
|--------------|-------------|
|TA_LEFT|왼쪽 맞춤|
|TA_CENTER|가운데 맞춤|
|TA_RIGHT|오른쪽 맞춤|

기본값은 TA_CENTER입니다.

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a> CMFCOutlookBarTabCtrl:: Set Imagelist

Outlook 표시줄의 아래쪽에 표시 되는 아이콘을 포함 하는 비트맵을 Outlook 2003 모드로 설정 합니다.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 로드할 이미지의 리소스 ID를 지정 합니다.

*cx*<br/>
진행 이미지 목록에서 이미지의 너비를 픽셀 단위로 지정 합니다.

*clrTransp*<br/>
진행 투명 한 색을 지정 하는 RGB 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 Microsoft Office 2003 모드의 도구 모음 단추에 이미지가 표시 되는 이미지 목록을 연결 합니다. 이미지 인덱스는 페이지 인덱스와 일치 해야 합니다.

Microsoft Office 2003 모드에 있지 않은 경우이 메서드를 호출 하면 안 됩니다. 자세한 내용은 [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)를 참조 하세요.

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a> CMFCOutlookBarTabCtrl:: SetVisiblePageButtons

```cpp
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>매개 변수

진행 *nVisiblePageButtons*<br/>

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl 클래스](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane 클래스](../../mfc/reference/cmfcoutlookbarpane-class.md)
