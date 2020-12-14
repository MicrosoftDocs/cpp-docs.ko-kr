---
description: '자세히 알아보기: CTabView 클래스'
title: CTabView 클래스
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: 59d4169bae108575fcf4844ec7c5c6e1e6681e28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345058"
---
# <a name="ctabview-class"></a>CTabView 클래스

`CTabView`클래스는 MFC의 문서/뷰 아키텍처를 사용 하는 응용 프로그램에서 탭 컨트롤 클래스 ( [Cmfctabctrl](../../mfc/reference/ctabview-class.md))를 사용 하는 것을 간소화 합니다.

## <a name="syntax"></a>구문

```
class CTabbedView : public CView
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTabView:: AddView](#addview)|탭 컨트롤에 새 뷰를 추가 합니다.|
|[CTabView:: FindTab](#findtab)|탭 컨트롤에서 지정 된 뷰의 인덱스를 반환 합니다.|
|[CTabView:: GetActiveView](#getactiveview)|현재 활성화 된 뷰에 대 한 포인터를 반환 합니다.|
|[CTabView:: GetTabControl](#gettabcontrol)|뷰와 연결 된 tab 컨트롤에 대 한 참조를 반환 합니다.|
|[CTabView:: RemoveView](#removeview)|탭 컨트롤에서 뷰를 제거 합니다.|
|[CTabView:: SetActiveView](#setactiveview)|뷰를 활성 상태로 만듭니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CTabView:: IsScrollBar](#isscrollbar)|탭 뷰에 공유 가로 스크롤 막대가 있는지 여부를 확인 하기 위해 탭 뷰를 만들 때 프레임 워크에서 호출 됩니다.|
|[CTabView:: OnActivateView](#onactivateview)|탭 뷰가 활성 또는 비활성 상태가 될 때 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

이 클래스를 사용 하면 문서/뷰 응용 프로그램에 탭 뷰를 쉽게 배치할 수 있습니다. `CTabView` 는 `CView` 포함 된 개체를 포함 하는 파생 클래스입니다 `CMFCTabCtrl` . `CTabView` 개체를 지 원하는 데 필요한 모든 메시지를 처리 `CMFCTabCtrl` 합니다. 에서 클래스를 파생 하 `CTabView` 고 응용 프로그램에 연결한 다음 `CView` 메서드를 사용 하 여 파생 클래스를 추가 하기만 하면 됩니다 `AddView` . 탭 컨트롤은 해당 뷰를 탭으로 표시 합니다.

예를 들어 스프레드시트, 차트, 편집 가능 폼 등의 여러 가지 방법으로 문서를 표시할 수 있습니다. 필요에 따라 데이터를 그리거나, `CTabView` 파생 개체에 삽입 하 고, 추가 코딩 없이 탭 하도록 개별 뷰를 만들 수 있습니다.

[TabbedView 샘플: MFC 탭 뷰 응용 프로그램](../../overview/visual-cpp-samples.md) 은 사용법을 보여 줍니다 `CTabView` .

## <a name="example"></a>예제

다음 예제에서는 `CTabView` TabbedView 샘플에서를 사용 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>요구 사항

**헤더:** afxTabView

## <a name="ctabviewaddview"></a><a name="addview"></a> CTabView:: AddView

탭 컨트롤에 뷰를 추가 합니다.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>매개 변수

*pViewClass*<br/>
진행 삽입 된 뷰의 런타임 클래스에 대 한 포인터입니다.

*strViewLabel*<br/>
진행 탭의 텍스트를 지정 합니다.

*iIndex*<br/>
진행 뷰를 삽입할 위치 (0부터 시작)를 지정 합니다. 위치가-1 인 경우 새 탭은 끝에 삽입 됩니다.

*pContext*<br/>
진행 뷰의에 대 한 포인터 `CCreateContext` 입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하는 경우 뷰 인덱스입니다. 그렇지 않으면 -1입니다.

### <a name="remarks"></a>설명

프레임에 포함 된 탭 컨트롤에 뷰를 추가 하려면이 함수를 호출 합니다.

## <a name="ctabviewfindtab"></a><a name="findtab"></a> CTabView:: FindTab

탭 컨트롤에서 지정 된 뷰의 인덱스를 반환 합니다.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>매개 변수

*hWndView*<br/>
진행 뷰의 핸들입니다.

### <a name="return-value"></a>반환 값

있는 경우 뷰의 인덱스이 고, 그렇지 않으면입니다. 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

지정 된 핸들이 있는 뷰의 인덱스를 검색 하려면이 함수를 호출 합니다.

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a> CTabView:: GetActiveView

현재 활성화 된 뷰에 대 한 포인터를 반환 합니다.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>반환 값

활성 뷰에 대 한 유효한 포인터 이거나 활성 뷰가 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a> CTabView:: GetTabControl

뷰와 연결 된 tab 컨트롤에 대 한 참조를 반환 합니다.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>반환 값

뷰와 연결 된 tab 컨트롤에 대 한 참조입니다.

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a> CTabView:: IsScrollBar

탭 뷰에 공유 가로 스크롤 막대가 있는지 여부를 확인 하기 위해 탭 뷰를 만들 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>반환 값

탭 뷰를 공유 스크롤 막대와 함께 만들어야 하는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*Ctabview* 개체를 만들 때 프레임 워크에서이 메서드를 호출 합니다.

*Ctabview* 파생 클래스에서 *isscrollbar* 메서드를 재정의 하 고 공유 가로 스크롤 막대가 있는 뷰를 만들려면 TRUE를 반환 합니다.

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a> CTabView:: OnActivateView

탭 뷰가 활성 또는 비활성 상태가 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>매개 변수

*view*<br/>
진행 뷰에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행하지 않습니다. `CTabView`이 알림을 처리 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctabviewremoveview"></a><a name="removeview"></a> CTabView:: RemoveView

탭 컨트롤에서 뷰를 제거 합니다.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>매개 변수

*iTabNum*<br/>
진행 제거할 뷰의 인덱스입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하는 경우 제거 된 뷰의 인덱스입니다. 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a> CTabView:: SetActiveView

뷰를 활성 상태로 만듭니다.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>매개 변수

*iTabNum*<br/>
진행 탭 뷰의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 뷰가 활성 상태 이면 TRUE이 고, 뷰의 인덱스가 유효 하지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

자세한 내용은 [Cmfctabctrl:: SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)
