---
description: '자세한 정보: CMFCBaseVisualManager 클래스'
title: CMFCBaseVisualManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
ms.openlocfilehash: 14727eea4bcefdc7b7de53f19f188d7cb9c528c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284982"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 클래스

파생 된 visual 관리자와 Windows 테마 API 간의 계층입니다.

`CMFCBaseVisualManager` UxTheme.dll를 로드 하 고, 사용 가능한 경우 Windows 테마 API 메서드에 대 한 액세스를 관리 합니다.

이 클래스는 내부용 으로만 사용 됩니다.

## <a name="syntax"></a>구문

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|[CMFCBaseVisualManager:: CMFCBaseVisualManager](#cmfcbasevisualmanager)|`CMFCBaseVisualManager` 개체를 생성하고 초기화합니다.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCBaseVisualManager::D rawCheckBox](#drawcheckbox)|현재 Windows 테마를 사용 하 여 확인란 컨트롤을 그립니다.|
|[CMFCBaseVisualManager::D rawComboBorder](#drawcomboborder)|현재 Windows 테마를 사용 하 여 콤보 상자 테두리를 그립니다.|
|[CMFCBaseVisualManager::D rawComboDropButton](#drawcombodropbutton)|현재 Windows 테마를 사용 하 여 콤보 상자 드롭다운 단추를 그립니다.|
|[CMFCBaseVisualManager::D rawPushButton](#drawpushbutton)|현재 Windows 테마를 사용 하 여 누름 단추를 그립니다.|
|[CMFCBaseVisualManager::D rawRadioButton](#drawradiobutton)|현재 Windows 테마를 사용 하 여 라디오 단추 컨트롤을 그립니다.|
|[CMFCBaseVisualManager::D rawStatusBarProgress](#drawstatusbarprogress)|현재 Windows 테마를 사용 하 여 상태 표시줄 컨트롤 ( [Cmfcstatusbar 클래스](../../mfc/reference/cmfcstatusbar-class.md))에 진행률 표시줄을 그립니다.|
|[CMFCBaseVisualManager:: Fillre바 창](#fillrebarpane)|현재 Windows 테마를 사용 하 여 rebar 컨트롤의 배경을 채웁니다.|
|[CMFCBaseVisualManager:: GetStandardWindowsTheme](#getstandardwindowstheme)|현재 Windows 테마를 가져옵니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|-|-|
|[CMFCBaseVisualManager:: CleanUpThemes](#cleanupthemes)|`CloseThemeData`에서 가져온 모든 핸들에 대해를 호출 `UpdateSystemColors` 합니다.|
|[CMFCBaseVisualManager:: UpdateSystemColors](#updatesystemcolors)|`OpenThemeData`을 호출 하 여 다양 한 컨트롤을 그리기 위한 핸들을 가져옵니다. 창, 도구 모음, 단추 등|

## <a name="remarks"></a>설명

이 클래스의 개체를 직접 인스턴스화할 필요는 없습니다.

이 클래스는 모든 시각적 관리자의 기본 클래스 이므로 [Cmfcvisualmanager:: GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)를 호출 하 고, 현재 시각적 관리자에 대 한 포인터를 가져오고, 해당 포인터를 사용 하기 위한 메서드에 액세스할 수 있습니다 `CMFCBaseVisualManager` . 그러나 현재 Windows 테마를 사용 하 여 컨트롤을 표시 해야 하는 경우 인터페이스를 사용 하는 것이 좋습니다 `CMFCVisualManagerWindows` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxvisualmanager

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a> CMFCBaseVisualManager:: CleanUpThemes

`CloseThemeData`에서 가져온 모든 핸들에 대해를 호출 `UpdateSystemColors` 합니다.

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>설명

내부 전용입니다.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a> CMFCBaseVisualManager:: CMFCBaseVisualManager

`CMFCBaseVisualManager` 개체를 생성하고 초기화합니다.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a> CMFCBaseVisualManager::D rawCheckBox

현재 Windows 테마를 사용 하 여 확인란 컨트롤을 그립니다.

```
virtual BOOL DrawCheckBox(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    int nState,
    BOOL bEnabled,
    BOOL bPressed);

);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 확인란의 경계 사각형입니다.

*bHighlighted 표시*<br/>
진행 확인란이 강조 표시 되는지 여부를 지정 합니다.

*nState*<br/>
[in] 0 (선택 하지 않음), 1 (확인 된 표준)

2 (mixed normal의 경우)

*bEnabled*<br/>
진행 확인란의 설정 여부를 지정 합니다.

*bPressed*<br/>
진행 확인란을 눌렀는지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

테마 API를 사용 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*Nstate* 의 값은 다음 확인란 스타일에 해당 합니다.

|nState|확인란 스타일|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a> CMFCBaseVisualManager::D rawComboBorder

현재 Windows 테마를 사용 하 여 콤보 상자 테두리를 그립니다.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 콤보 상자 테두리의 경계 사각형입니다.

*bDisabled*<br/>
진행 콤보 상자 테두리를 사용할 수 없는지 여부를 지정 합니다.

*bIsDropped*<br/>
진행 콤보 상자 테두리를 삭제할지 여부를 지정 합니다.

*bIsHighlighted*<br/>
진행 콤보 상자 테두리를 강조 표시할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

테마 API를 사용 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a> CMFCBaseVisualManager::D rawComboDropButton

현재 Windows 테마를 사용 하 여 콤보 상자 드롭다운 단추를 그립니다.

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*\
진행 장치 컨텍스트에 대 한 포인터입니다.

*직교*\
진행 콤보 상자 드롭다운 단추의 경계 사각형입니다.

*bDisabled*\
진행 콤보 상자 드롭다운 단추를 사용할 수 없는지 여부를 지정 합니다.

*bIsDropped*\
진행 콤보 상자 드롭다운 단추를 삭제할지 여부를 지정 합니다.

*bIsHighlighted*\
진행 콤보 상자 드롭다운 단추가 강조 표시 되는지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

테마 API를 사용 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a> CMFCBaseVisualManager::D rawPushButton

현재 Windows 테마를 사용 하 여 누름 단추를 그립니다.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 누름 단추의 경계 사각형입니다.

*pButton*<br/>
진행 그릴 [Cmfcbutton 클래스](../../mfc/reference/cmfcbutton-class.md) 개체에 대 한 포인터입니다.

*uiState*<br/>
진행 무시. *Pbutton* 에서 상태를 가져옵니다.

### <a name="return-value"></a>반환 값

테마 API를 사용 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a> CMFCBaseVisualManager::D rawRadioButton

현재 Windows 테마를 사용 하 여 라디오 단추 컨트롤을 그립니다.

```
virtual BOOL DrawRadioButton(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    BOOL bChecked,
    BOOL bEnabled,
    BOOL bPressed);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 라디오 단추의 경계 사각형입니다.

*bHighlighted 표시*<br/>
진행 라디오 단추가 강조 표시 되는지 여부를 지정 합니다.

*bChecked*<br/>
진행 라디오 단추가 선택 되어 있는지 여부를 지정 합니다.

*bEnabled*<br/>
진행 라디오 단추를 사용할 수 있는지 여부를 지정 합니다.

*bPressed*<br/>
진행 라디오 단추를 눌렀는지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

테마 API를 사용 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a> CMFCBaseVisualManager::D rawStatusBarProgress

현재 Windows 테마를 사용 하 여 상태 표시줄 컨트롤 ( [Cmfcstatusbar 클래스](../../mfc/reference/cmfcstatusbar-class.md))에 진행률 표시줄을 그립니다.

```
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,
    CMFCStatusBar* pStatusBar,
    CRect rectProgress,
    int nProgressTotal,
    int nProgressCurr,
    COLORREF clrBar,
    COLORREF clrProgressBarDest,
    COLORREF clrProgressText,
    BOOL bProgressText);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*pStatusBar*<br/>
진행 상태 표시줄에 대 한 포인터입니다. 이 값은 무시됩니다.

*rectProgress*<br/>
진행 *PDC* 좌표에 있는 진행률 표시줄의 경계 사각형입니다.

*nProgressTotal*<br/>
진행 총 진행률 값입니다.

*nProgressCurr*<br/>
진행 현재 진행 값입니다.

*clrBar*<br/>
진행 시작 색입니다. `CMFCBaseVisualManager` 는이를 무시 합니다. 파생 클래스에서 색 그라데이션과 함께 사용할 수 있습니다.

*clrProgressBarDest*<br/>
진행 마지막 색입니다. `CMFCBaseVisualManager` 는이를 무시 합니다. 파생 클래스에서 색 그라데이션과 함께 사용할 수 있습니다.

*clrProgressText*<br/>
진행 진행률 텍스트 색입니다. `CMFCBaseVisualManager` 는이를 무시 합니다. 텍스트 색은에 의해 정의 됩니다 `afxGlobalData.clrBtnText` .

*bProgressText*<br/>
진행 진행률 텍스트를 표시할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

테마 API를 사용 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a> CMFCBaseVisualManager:: Fillre바 창

현재 Windows 테마를 사용 하 여 rebar 컨트롤의 배경을 채웁니다.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*pBar*<br/>
진행 배경을 그려야 하는 창에 대 한 포인터입니다.

*rectClient*<br/>
진행 채워질 영역의 경계 사각형입니다.

### <a name="return-value"></a>반환 값

테마 API를 사용 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a> CMFCBaseVisualManager:: GetStandardWindowsTheme

현재 Windows 테마를 가져옵니다.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>반환 값

현재 선택 된 Windows 테마 색입니다. 다음 열거형 값 중 하나일 수 있습니다.

- `WinXpTheme_None` -테마를 사용할 수 없습니다.

- `WinXpTheme_NonStandard` -비표준 테마가 선택 됩니다 (테마를 선택 하 고 아래 목록에서 없음).

- `WinXpTheme_Blue` -파란색 테마 (Luna).

- `WinXpTheme_Olive` -올리브 테마.

- `WinXpTheme_Silver` -은색 테마.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a> CMFCBaseVisualManager:: UpdateSystemColors

`OpenThemeData`을 호출 하 여 다양 한 컨트롤을 그리기 위한 핸들을 가져옵니다. 창, 도구 모음, 단추 등

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>설명

내부 전용입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
