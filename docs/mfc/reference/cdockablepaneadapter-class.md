---
description: '자세히 알아보기: CDockablePaneAdapter 클래스'
title: CDockablePaneAdapter 클래스
ms.date: 11/04/2016
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
ms.openlocfilehash: 0a46ef15d35194203d6e5c035555de0d80b63c72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185039"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter 클래스

`CWnd`파생 창에 대해 도킹 지원을 제공합니다.

## <a name="syntax"></a>구문

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDockablePaneAdapter:: GetWrappedWnd](#getwrappedwnd)|래핑된 창을 반환합니다.|
|[CDockablePaneAdapter::LoadState](#loadstate)|[CDockablePane:: LoadState](cdockablepane-class.md#loadstate)를 재정의 합니다.|
|[CDockablePaneAdapter::SaveState](#savestate)|[CDockablePane:: SaveState](cdockablepane-class.md)를 재정의 합니다.|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>설명

일반적으로 프레임 워크는 [CMFCBaseTabCtrl:: addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) 또는 [CMFCBaseTabCtrl:: inserttab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) 메서드를 사용할 때이 클래스의 개체를 인스턴스화합니다.

동작을 사용자 지정 하려는 경우 `CDockablePaneAdapter` [CMFCBaseTabCtrl:: SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc)를 사용 하 여 해당 클래스에서 새 클래스를 파생 하 고 런타임 클래스 정보를 탭 창으로 설정 하면 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Cpane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxDockablePaneAdapter

## <a name="cdockablepaneadaptergetwrappedwnd"></a><a name="getwrappedwnd"></a> CDockablePaneAdapter:: GetWrappedWnd

도킹 가능한 창 어댑터에 대 한 내부 창을 반환 합니다.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>반환 값

래핑된 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

래핑된 창에 액세스 하려면이 함수를 사용 합니다.

## <a name="cdockablepaneadapterloadstate"></a><a name="loadstate"></a> CDockablePaneAdapter:: LoadState

레지스트리에서 창의 상태를 로드 합니다.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 프로필 이름입니다.

*nIndex*<br/>
진행 프로필 인덱스입니다.

*uiID*<br/>
진행 창 ID입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockablepaneadaptersavestate"></a><a name="savestate"></a> CDockablePaneAdapter:: SaveState

창 상태를 레지스트리에 저장 합니다.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 프로필 이름입니다.

*nIndex*<br/>
진행 프로필 인덱스 (기본값은 창의 컨트롤 ID)입니다.

*uiID*<br/>
진행 창 ID입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockablepaneadaptersetwrappedwnd"></a><a name="setwrappedwnd"></a> CDockablePaneAdapter:: SetWrappedWnd

도킹 가능한 창 어댑터에 대 한 내부 창을 설정 합니다.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 래핑할 창 어댑터에 대 한 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)
