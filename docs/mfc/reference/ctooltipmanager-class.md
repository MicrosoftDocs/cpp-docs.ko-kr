---
description: '자세히 알아보기: CTooltipManager 클래스'
title: CTooltipManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: 0ec6d691abbceb7026fe9656c17ff899f1d07759
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318548"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager 클래스

도구 설명에 대한 런타임 정보를 유지합니다. `CTooltipManager` 클래스는 애플리케이션당 한 번씩 인스턴스화됩니다.

## <a name="syntax"></a>구문

```
class CTooltipManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|지정된 Windows 컨트롤 형식에 대한 도구 설명 컨트롤을 만듭니다.|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|도구 설명 컨트롤을 삭제합니다.|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|지정된 Windows 컨트롤 형식에 대한 도구 설명 컨트롤의 시각적 모양을 사용자 지정합니다.|
|[CTooltipManager::SetTooltipText](#settooltiptext)|도구 설명 컨트롤에 대한 텍스트 및 설명을 설정합니다.|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>설명

[CMFCToolTipCtrl 클래스](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo` 및를 함께 사용 하 여 `CTooltipManager` 응용 프로그램에 사용자 지정 도구 설명을 구현 합니다. 이러한 도구 설명 클래스를 사용 하는 방법에 대 한 예제는 [CMFCToolTipCtrl 클래스](../../mfc/reference/cmfctooltipctrl-class.md) 항목을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtooltipmanager

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a> CTooltipManager:: CreateToolTip

Tooltip 컨트롤을 만듭니다.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>매개 변수

*pToolTip*<br/>
제한이 도구 설명 포인터에 대 한 참조입니다. 함수가 반환 될 때 새로 만든 도구 설명을 가리키도록 설정 됩니다.

*pWndParent*<br/>
진행 도구 설명의 부모입니다.

*nType*<br/>
진행 도구 설명의 유형입니다.

### <a name="return-value"></a>반환 값

도구 설명이 성공적으로 만들어진 경우 0이 아닙니다.

### <a name="remarks"></a>설명

[CTooltipManager::D eletetooltip](#deletetooltip) 를 호출 하 여 *ptooltip* 에서 다시 전달 되는 도구 설명 컨트롤을 삭제 해야 합니다.

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) 는 *nType* 가 지정 하는 도구 설명 유형에 따라 생성 되는 각 도구 설명의 시각적 표시 매개 변수를 설정 합니다. 하나 이상의 도구 설명 형식에 대 한 매개 변수를 변경 하려면 [CTooltipManager:: SetTooltipParams](#settooltipparams)를 호출 합니다.

다음 표에는 유효한 도구 설명 형식이 나와 있습니다.

|도구 설명 형식|컨트롤 범주|예제 형식|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|단추입니다.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|캡션 표시줄입니다.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|다른 범주에 맞지 않는 컨트롤입니다.|없음|
|AFX_TOOLTIP_TYPE_DOCKBAR|도킹 가능한 창.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|텍스트 상자입니다.|없음|
|AFX_TOOLTIP_TYPE_MINIFRAME|미니 프레임입니다.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Planner.|없음|
|AFX_TOOLTIP_TYPE_RIBBON|리본 표시줄입니다.|Cmfc리본 표시줄, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|탭 컨트롤입니다.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|도구 모음입니다.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|도구 상자입니다.|없음|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a> CTooltipManager::D eleteToolTip

도구 설명 컨트롤을 삭제합니다.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>매개 변수

*pToolTip*<br/>
[in, out] 제거할 도구 설명에 대 한 포인터에 대 한 참조입니다.

### <a name="remarks"></a>설명

[CTooltipManager:: CreateToolTip](#createtooltip)에서 만든 각 [CToolTipCtrl 클래스](../../mfc/reference/ctooltipctrl-class.md) 에 대해이 메서드를 호출 합니다. 부모 컨트롤이 처리기에서이 메서드를 호출 해야 합니다 `OnDestroy` . 이는 프레임 워크에서 도구 설명을 올바르게 제거 하는 데 필요 합니다. 이 메서드는 반환 되기 전에 *Ptooltip* 을 NULL로 설정 합니다.

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a> CTooltipManager:: SetTooltipParams

지정 된 Windows 컨트롤 형식에 대 한 도구 설명 컨트롤의 모양을 사용자 지정 합니다.

```cpp
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>매개 변수

*nTypes*<br/>
진행 컨트롤 형식을 지정 합니다.

*pRTC*<br/>
진행 사용자 지정 도구 설명의 런타임 클래스입니다.

*pParams*<br/>
진행 Tooltip 매개 변수.

### <a name="remarks"></a>설명

이 메서드는 도구 설명을 만들 때 [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) 에서 사용 하는 런타임 클래스 및 초기 매개 변수를 설정 합니다. 컨트롤이 [CTooltipManager:: CreateToolTip](#createtooltip) 를 호출 하 고 *ntypes* 가 나타내는 형식 중 하나인 도구 설명 형식을 전달 하는 경우 도구 설명 관리자는 *prtc* 에서 지정한 런타임 클래스의 인스턴스인 도구 설명 컨트롤을 만들고 *pparams* 로 지정 된 매개 변수를 새 도구 설명에 전달 합니다.

이 메서드를 호출 하면 기존 도구 설명 소유자는 모두 AFX_WM_UPDATETOOLTIPS 메시지를 수신 하 고 [CTooltipManager:: CreateToolTip](#createtooltip)를 사용 하 여 해당 도구 설명을 다시 만들어야 합니다.

*n 형식은* [CTooltipManager:: CreateToolTip](#createtooltip) 에서 사용 하는 유효한 도구 설명 형식의 조합 이거나 AFX_TOOLTIP_TYPE_ALL 수 있습니다. AFX_TOOLTIP_TYPE_ALL를 전달 하는 경우 모든 도구 설명 형식이 영향을 받습니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `SetTooltipParams` `CTooltipManager` . 이 코드 조각은 [클라이언트 그리기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a> CTooltipManager:: SetTooltipText

도구 설명에 대 한 텍스트 및 설명을 설정 합니다.

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>매개 변수

*pTI*<br/>
진행 TOOLINFO 개체에 대 한 포인터입니다.

*pToolTip*<br/>
[in, out] 텍스트와 설명을 설정할 도구 설명 컨트롤에 대 한 포인터입니다.

*nType*<br/>
진행 이 도구 설명이 연결 된 컨트롤의 유형을 지정 합니다.

*strText*<br/>
진행 도구 설명 텍스트로 설정할 텍스트입니다.

*lpszDescr*<br/>
진행 도구 설명에 대 한 포인터입니다. NULL일 수 있습니다.

### <a name="remarks"></a>설명

*NType* 의 값은 도구 설명을 만들 때 [CTooltipManager:: CreateToolTip](#createtooltip) 의 *nType* 매개 변수와 동일한 값 이어야 합니다.

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a> CTooltipManager:: UpdateTooltips

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```cpp
void UpdateTooltips();
```

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl 클래스](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo 클래스](../../mfc/reference/cmfctooltipinfo-class.md)
