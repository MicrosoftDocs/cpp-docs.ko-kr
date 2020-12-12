---
description: '자세히 알아보기: CBaseTabbedPane 클래스'
title: CBaseTabbedPane 클래스
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: 980f2691aa9e129b0e47070d7ff095d486c45b65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122748"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 클래스

[CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 의 기능을 확장하여 탭 창 만들기를 지원합니다.

## <a name="syntax"></a>구문

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CBaseTabbedPane:: AddTab](#addtab)|탭 창에 새 탭을 추가 합니다.|
|[CBaseTabbedPane:: AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|빈 탭 창을 제거할 수 있는지 여부를 지정 합니다.|
|[CBaseTabbedPane:: ApplyRestoredTabInfo](#applyrestoredtabinfo)|레지스트리에서 로드 된 탭 설정을 탭 창에 적용 합니다.|
|[CBaseTabbedPane:: CanFloat](#canfloat)|창을 부동 상태로 만들 수 있는지 여부를 결정 합니다. [Cbasepane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)를 재정의 합니다.|
|[CBaseTabbedPane:: CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|탭 창의 캡션에 활성 탭과 동일한 텍스트가 표시 되어야 하는지 여부를 결정 합니다.|
|[CBaseTabbedPane:: ConvertToTabbedDocument](#converttotabbeddocument)|[CDockablePane:: ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)를 재정의 합니다.|
|[CBaseTabbedPane::D etachPane](#detachpane)|하나 이상의 도킹 가능한 창을 MDI 탭 문서로 변환 합니다.|
|[CBaseTabbedPane:: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|탭 창에서 캡션 텍스트를 활성 탭의 레이블 텍스트와 동기화 할 수 있는 기능을 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CBaseTabbedPane:: FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|내부 탭 순서를 기본 상태로 복원 합니다.|
|[CBaseTabbedPane:: FindBarByTabNumber](#findbarbytabnumber)|탭이 0부터 시작 하는 인덱스 (0부터 시작)로 식별 되는 경우 탭에 있는 창을 반환 합니다.|
|[CBaseTabbedPane:: FindPaneByID](#findpanebyid)|창 ID로 식별 되는 창을 반환 합니다.|
|[CBaseTabbedPane:: FloatTab](#floattab)|창이 현재 분리 가능한 탭에 있는 경우에만 창을 부동합니다.|
|[CBaseTabbedPane:: GetDefaultTabsOrder](#getdefaulttabsorder)|창에 있는 탭의 기본 순서를 반환 합니다.|
|[CBaseTabbedPane:: GetFirstVisibleTab](#getfirstvisibletab)|표시 된 첫 번째 탭에 대 한 포인터를 검색 합니다.|
|[CBaseTabbedPane:: GetMinSize](#getminsize)|창의 허용 되는 최소 크기를 검색 합니다. ( [Cpane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize)를 재정의 합니다.)|
|[CBaseTabbedPane:: GetPaneIcon](#getpaneicon)|창 아이콘에 대 한 핸들을 반환 합니다. ( [Cbasepane:: GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)를 재정의 합니다.)|
|[CBaseTabbedPane:: GetPaneList](#getpanelist)|탭 창에 포함 된 창 목록을 반환 합니다.|
|[CBaseTabbedPane:: GetTabArea](#gettabarea)|위쪽 및 아래쪽 탭 영역에 대 한 경계 사각형을 반환 합니다.|
|[CBaseTabbedPane:: GetTabsNum](#gettabsnum)|탭 창에 있는 탭의 수를 반환 합니다.|
|[CBaseTabbedPane:: GetUnderlyingWindow](#getunderlyingwindow)|내부 (래핑된) 탭 창을 가져옵니다.|
|[CBaseTabbedPane:: GetVisibleTabsNum](#getvisibletabsnum)|표시 된 탭 수를 반환 합니다.|
|[CBaseTabbedPane:: HasAutoHideMode](#hasautohidemode)|탭 창을 자동 숨기기 모드로 전환할 수 있는지 여부를 결정 합니다.|
|[CBaseTabbedPane:: IsHideSingleTab](#ishidesingletab)|탭이 하나만 표시 되는 경우 탭 창이 숨겨지는지 여부를 결정 합니다.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Serialization 중에 내부적으로 사용 됩니다.|
|[CBaseTabbedPane:: RecalcLayout](#recalclayout)|창에 대 한 레이아웃 정보를 다시 계산 합니다. ( [Cpane:: RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout)를 재정의 합니다.)|
|[CBaseTabbedPane:: RemovePane](#removepane)|탭 창에서 창을 제거 합니다.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Serialization 중에 내부적으로 사용 됩니다.|
|`CBaseTabbedPane::Serialize`|[CDockablePane:: Serialize](cdockablepane-class.md)를 재정의 합니다.|
|`CBaseTabbedPane::SerializeTabWindow`|Serialization 중에 내부적으로 사용 됩니다.|
|[CBaseTabbedPane:: SetAutoDestroy](#setautodestroy)|탭 컨트롤 막대가 자동으로 제거 되는지 여부를 결정 합니다.|
|[CBaseTabbedPane:: SetAutoHideMode](#setautohidemode)|도킹 창을 표시와 자동 숨기기 모드 사이에서 전환 합니다. [CDockablePane:: SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)를 재정의 합니다.|
|[CBaseTabbedPane:: ShowTab](#showtab)|탭을 표시 하거나 숨깁니다.|

## <a name="remarks"></a>설명

이 클래스는 추상 클래스 이므로 인스턴스화될 수 없습니다. 모든 종류의 탭 창에 공통적인 서비스를 구현 합니다.

현재 라이브러리에는 두 개의 파생 된 탭 창 클래스 ( [CTabbedPane 클래스](../../mfc/reference/ctabbedpane-class.md) 및 [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md))가 포함 되어 있습니다.

`CBaseTabbedPane`개체는 [CMFCBaseTabCtrl 클래스](../../mfc/reference/cmfcbasetabctrl-class.md) 개체에 대 한 포인터를 래핑합니다. 그러면 [CMFCBaseTabCtrl 클래스가](../../mfc/reference/cmfcbasetabctrl-class.md) 탭 창의 자식 창이 됩니다.

탭 창을 만드는 방법에 대 한 자세한 내용은 [CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md), [CTabbedPane 클래스](../../mfc/reference/ctabbedpane-class.md)및 [CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>요구 사항

**헤더:** afxBaseTabbedPane

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a> CBaseTabbedPane:: AddTab

탭 창에 새 탭을 추가 합니다.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>매개 변수

*pNewBar*<br/>
[in, out] 추가할 창에 대 한 포인터입니다. 이 메서드를 호출한 후에는이 포인터가 유효 하지 않게 될 수 있습니다. 자세한 내용은 설명 섹션을 참조하세요.

*bVisible*<br/>
진행 탭을 표시 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*bSetActive*<br/>
진행 탭을 활성 탭으로 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*bDetachable*<br/>
진행 탭을 분리할 수 있도록 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

창이 탭으로 성공적으로 추가 되 고 프로세스에서 제거 되지 않은 경우 TRUE입니다. 추가 중인 창이 형식의 개체 이면 FALSE입니다 `CBaseTabbedPane` . 자세한 내용은 설명 섹션을 참조하세요.

### <a name="remarks"></a>설명

탭 창에 새 탭으로 창을 추가 하려면이 메서드를 호출 합니다. *Pnewbar* 가 형식의 개체를 가리키면 `CBaseTabbedPane` 모든 탭이 탭 창에 복사 된 다음 *pnewbar* 가 제거 됩니다. 따라서 *Pnewbar* 는 잘못 된 포인터가 되므로 사용해 서는 안 됩니다.

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a> CBaseTabbedPane:: AllowDestroyEmptyTabbedPane

빈 탭 창을 제거할 수 있는지 여부를 지정 합니다.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>반환 값

빈 탭 창을 제거할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다. 기본 구현에서는 항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

빈 탭 창을 제거할 수 없는 경우 프레임 워크에서 창을 숨깁니다.

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a> CBaseTabbedPane:: ApplyRestoredTabInfo

레지스트리에서 탭 설정을 로드 하 고 탭 창에 적용 합니다.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>매개 변수

*bUseTabIndexes*<br/>
진행 이 매개 변수는 프레임 워크에서 내부적으로 사용 됩니다.

### <a name="remarks"></a>설명

이 메서드는 레지스트리에서 고정 상태 정보를 다시 로드할 때 프레임 워크에서 호출 됩니다. 메서드는 탭 창에서 탭 순서 및 탭 이름에 대 한 정보를 가져옵니다.

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a> CBaseTabbedPane:: CanFloat

탭 창을 부동 상태로 만들 수 있는지 여부를 지정 합니다.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>반환 값

창을 부동 상태로 만들 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a> CBaseTabbedPane:: CanSetCaptionTextToTabName

탭 창의 캡션에 활성 탭과 동일한 텍스트가 표시 되어야 하는지 여부를 결정 합니다.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>반환 값

탭 창의 캡션 텍스트가 활성 탭의 텍스트로 설정 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

메서드는 탭 창 캡션에 표시 되는 텍스트가 활성 탭의 레이블과 중복 되는지 여부를 결정 하는 데 사용 됩니다. [CBaseTabbedPane:: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)을 호출 하 여이 기능을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a> CBaseTabbedPane:: ConvertToTabbedDocument

하나 이상의 도킹 가능한 창을 MDI 탭 문서로 변환 합니다.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>매개 변수

*bActiveTabOnly*<br/>
진행 탭 창을 변환할 때 활성 탭만 변환 하려면 TRUE를 지정 합니다. 창에 있는 모든 탭을 변환 하려면 FALSE를 지정 합니다.

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a> CBaseTabbedPane::D etachPane

탭 창에서 창을 분리 합니다.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 분리할 창에 대 한 포인터입니다.

*bHide*<br/>
진행 프레임 워크가 분리 된 후 프레임 워크에서 창을 숨길지 여부를 지정 하는 부울 매개 변수입니다.

### <a name="return-value"></a>반환 값

프레임 워크가 창을 분리 했으면 TRUE이 고, 그렇지 않으면입니다. *Pbar* 가 NULL 이거나 탭 창에 없는 창을 참조 하면 FALSE입니다.

### <a name="remarks"></a>설명

가능 하면 프레임 워크는 분리 된 창을 부동 합니다. 자세한 내용은 [Cbasepane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)를 참조 하세요.

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a> CBaseTabbedPane:: EnableSetCaptionTextToTabName

탭 창에서 캡션 텍스트를 활성 탭의 레이블 텍스트와 동기화 할 수 있는 기능을 사용 하거나 사용 하지 않도록 설정 합니다.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 탭 창 캡션을 활성 탭 캡션과 동기화 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a> CBaseTabbedPane:: FillDefaultTabsOrderArray

내부 탭 순서를 기본 상태로 복원 합니다.

```cpp
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>설명

이 메서드는 프레임 워크가 Outlook 표시줄을 초기 상태로 복원할 때 호출 됩니다.

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a> CBaseTabbedPane:: FindPaneByID

창 ID로 식별 되는 창을 반환 합니다.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>매개 변수

*U바 Id*<br/>
진행 찾을 창의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

창에 대 한 포인터 (있는 경우)입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 창의 모든 탭을 비교 하 고 *Ubarid* 매개 변수로 지정 된 ID를 사용 하 여 해당 탭을 반환 합니다.

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a> CBaseTabbedPane:: FindBarByTabNumber

탭에 있는 창을 반환 합니다.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>매개 변수

*nTabNum*<br/>
진행 검색할 탭의 인덱스 (0부터 시작)를 지정 합니다.

*bGetWrappedBar*<br/>
진행 창 자체 대신 창의 기본 (래핑된) 창을 반환 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 이는 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)에서 파생 된 창에만 적용 됩니다.

### <a name="return-value"></a>반환 값

창이 있으면 검색 되는 창에 대 한 올바른 포인터가 반환 됩니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 *Ntabnum* 매개 변수로 지정 된 탭에 있는 창을 검색 합니다.

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a> CBaseTabbedPane:: FloatTab

창이 현재 분리 가능한 탭에 있는 경우에만 창을 부동합니다.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
[in, out] 부동 창에 대 한 포인터입니다.

*nTabID*<br/>
진행 탭의 인덱스 (0부터 시작)를 부동으로 지정 합니다.

*dockMethod*<br/>
진행 창을 부동으로 만드는 데 사용할 메서드를 지정 합니다. 자세한 내용은 설명 섹션을 참조하세요.

*bHide*<br/>
진행 창을 부동 소수점 앞으로 숨기려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

창이 부동이 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

현재 분리 가능한 탭에 있는 창을 부동 하려면이 메서드를 호출 합니다.

창을 프로그래밍 방식으로 분리 하려면 *dockMethod* 매개 변수에 대 한 DM_SHOW를 지정 합니다. 이전에 부동 위치에서 창을 부동 하려면 *dockMethod* 매개 변수로 DM_DBL_CLICK를 지정 합니다.

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a> CBaseTabbedPane:: GetDefaultTabsOrder

창에 있는 탭의 기본 순서를 반환 합니다.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>반환 값

`CArray`창에 있는 탭의 기본 순서를 지정 하는 개체입니다.

### <a name="remarks"></a>설명

프레임 워크는 Outlook 표시줄이 초기 상태로 다시 설정 될 때이 메서드를 호출 합니다.

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a> CBaseTabbedPane:: GetFirstVisibleTab

표시 된 첫 번째 탭에 대 한 포인터를 검색 합니다.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>매개 변수

*iTabNum*<br/>
진행 정수에 대 한 참조입니다. 이 메서드는 표시 된 첫 번째 탭의 인덱스 (0부터 시작)를이 매개 변수에 쓰고, 표시 된 탭이 없는 경우-1을 씁니다.

### <a name="return-value"></a>반환 값

성공 하면 첫 번째 표시 된 탭에 대 한 포인터이 고, 그렇지 않으면 NULL입니다.

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a> CBaseTabbedPane:: GetMinSize

창의 허용 되는 최소 크기를 검색 합니다.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>매개 변수

*size*<br/>
제한이 허용 되는 `CSize` 최소 크기로 채워지는 개체입니다.

### <a name="remarks"></a>설명

최소 창 크기를 일관 되 게 처리 하는 경우 ( [Cpane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)) *크기가* 활성 탭에 대해 허용 되는 최소 크기로 채워집니다. 그렇지 않으면 *크기* 는 [Cpane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize)의 반환 값으로 채워집니다.

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a> CBaseTabbedPane:: GetPaneIcon

창의 허용 되는 최소 크기를 검색 합니다.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>매개 변수

*size*<br/>
제한이 허용 되는 `CSize` 최소 크기로 채워지는 개체입니다.

### <a name="remarks"></a>설명

최소 창 크기를 일관 되 게 처리 하는 경우 ( [Cpane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)) *크기가* 활성 탭에 대해 허용 되는 최소 크기로 채워집니다. 그렇지 않으면 *크기* 는 [Cpane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize)의 반환 값으로 채워집니다.

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a> CBaseTabbedPane:: GetPaneList

탭 창에 포함 된 창 목록을 반환 합니다.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>매개 변수

*.lst*<br/>
제한이 `CObList` 탭 창에 포함 된 창으로 채워지는입니다.

*pRTCFilter 필터*<br/>
진행 NULL이 아닌 경우 반환 된 목록에는 지정 된 런타임 클래스의 창만 포함 됩니다.

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a> CBaseTabbedPane:: GetTabArea

위쪽 및 아래쪽 탭 영역에 대 한 경계 사각형을 반환 합니다.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>매개 변수

*rectTabAreaTop*<br/>
제한이 위쪽 탭 영역의 화면 좌표를 받습니다.

*rectTabAreaBottom*<br/>
제한이 아래쪽 탭 영역의 화면 좌표를 받습니다.

### <a name="remarks"></a>설명

위쪽 및 아래쪽 탭 영역에 대 한 경계 사각형 (화면 좌표)을 결정 하려면이 메서드를 호출 합니다.

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a> CBaseTabbedPane:: GetTabsNum

탭 창에 있는 탭의 수를 반환 합니다.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>반환 값

탭 창에 있는 탭 수입니다.

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a> CBaseTabbedPane:: GetUnderlyingWindow

내부 (래핑된) 탭 창을 가져옵니다.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>반환 값

기본 탭 창에 대 한 포인터입니다.

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a> CBaseTabbedPane:: GetVisibleTabsNum

표시 되는 탭 수를 반환 합니다.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>반환 값

0 보다 크거나 같은 표시 되는 탭 수입니다.

### <a name="remarks"></a>설명

탭 창에서 표시 되는 탭 수를 확인 하려면이 메서드를 호출 합니다.

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a> CBaseTabbedPane:: HasAutoHideMode

탭 창을 자동 숨기기 모드로 전환할 수 있는지 여부를 결정합니다.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>반환 값

창을 자동 숨기기 모드로 전환할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

자동 숨기기 모드를 사용 하지 않도록 설정 하면 탭 창 캡션에 고정 단추가 표시 되지 않습니다.

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a> CBaseTabbedPane:: IsHideSingleTab

탭이 하나만 표시 되는 경우 탭 창이 숨겨지는지 여부를 결정 합니다.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>반환 값

표시 탭이 하나만 있는 경우 탭 창이 표시 되지 않으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

하나의 탭만 열려 있으므로 창이 표시 되지 않으면이 메서드를 호출 하 여 탭 창이 제대로 작동 하는지 여부를 확인할 수 있습니다.

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a> CBaseTabbedPane:: RemovePane

탭 창에서 창을 제거 합니다.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
[in, out] 탭 창에서 제거할 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

탭 창에서 창이 성공적으로 제거 되 고 탭 창이 여전히 유효한 경우 TRUE입니다. 탭 창에서 마지막 창이 제거 되 고 탭 창이 소멸 되려고 하면 FALSE입니다. 반환 값이 FALSE 이면 탭 창을 더 이상 사용 하지 마십시오.

### <a name="remarks"></a>설명

탭 창에서 *Pbar* 매개 변수로 지정 된 창을 제거 하려면이 메서드를 호출 합니다.

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a> CBaseTabbedPane:: SetAutoDestroy

탭 컨트롤 막대가 자동으로 제거 되는지 여부를 결정 합니다.

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*bAutoDestroy*<br/>
진행 탭 창을 동적으로 만들었으며 해당 수명을 제어 하지 않는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

탭 창을 동적으로 만들고 해당 수명을 제어 하지 않는 경우 자동 소멸 모드를 TRUE로 설정 합니다. 자동 제거 모드가 TRUE 이면 프레임 워크에서 탭 창이 자동으로 제거 됩니다.

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a> CBaseTabbedPane:: ShowTab

탭을 표시 하거나 숨깁니다.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 표시 하거나 숨길 창에 대 한 포인터입니다.

*bShow*<br/>
진행 창을 표시 하려면 TRUE로 설정 합니다. FALSE 이면 창을 숨깁니다.

*bDelay*<br/>
진행 탭 레이아웃의 조정을 지연 시키려면 TRUE입니다. 그렇지 않으면 FALSE입니다.

*bActivate*<br/>
진행 탭을 활성 탭으로 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

탭이 표시 되거나 숨겨져 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하면 *Bshow* 매개 변수의 값에 따라 창이 표시 되거나 숨겨집니다. 탭을 숨기면 기본 탭 창에 마지막으로 표시 되는 탭이 표시 됩니다. 이전에 탭이 표시 되지 않은 경우 탭을 표시 하면 탭 창이 표시 됩니다.

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a> CBaseTabbedPane:: RecalcLayout

창에 대 한 레이아웃 정보를 다시 계산 합니다.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>설명

창이 부동 인 경우이 메서드는 창 크기를 미니 프레임의 현재 크기로 조정 하도록 프레임 워크에 알립니다.

창이 도킹 되어 있으면이 메서드는 아무 작업도 수행 하지 않습니다.

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a> CBaseTabbedPane:: SetAutoHideMode

탭 창에서 분리 가능한 창에 대 한 자동 숨기기 모드를 설정 합니다.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>매개 변수

*bMode*<br/>
진행 자동 숨기기 모드를 사용 하도록 설정 하려면 TRUE로 설정 합니다. 일반 도킹 모드를 사용 하려면 FALSE입니다.

*dwAlignment*<br/>
진행 만들 자동 숨기기 창의 맞춤을 지정 합니다. 가능한 값 목록은 [Cpane:: MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)를 참조 하세요.

*pCurrAutoHideBar*<br/>
[in, out] 현재 자동 숨기기 도구 모음에 대 한 포인터입니다. NULL일 수 있습니다.

*bUseTimer*<br/>
진행 사용자가 창을 자동 숨기기 모드로 전환 하거나 창을 즉시 숨길 때 자동 숨기기 효과를 사용할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

자동 숨기기 모드로 전환할 때 만들어지는 자동 숨기기 도구 모음에 대 한 포인터 이거나, 도구 모음이 생성 되지 않은 경우 NULL입니다.

### <a name="remarks"></a>설명

사용자가 고정 단추를 선택 하 여 탭 창을 자동 숨기기 모드로 전환 하거나 일반 도킹 모드로 전환 하는 경우 프레임 워크에서이 메서드를 호출 합니다.

자동 숨기기 모드는 탭 창의 분리 가능한 각 창에 대해 설정 됩니다. 분리할 수 없는 창은 무시 됩니다. 자세한 내용은 [CMFCBaseTabCtrl:: EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)를 참조 하세요.

탭 창을 프로그래밍 방식으로 자동 숨기기 모드로 전환 하려면이 메서드를 호출 합니다. 창은 주 프레임 창에 도킹 되어야 합니다 ( [CDockablePane:: GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) 는 [CPaneDivider](../../mfc/reference/cpanedivider-class.md)에 대 한 유효한 포인터를 반환 해야 함).

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)
