---
description: '자세히 알아보기: CMFCDropDownFrame 클래스'
title: CMFCDropDownFrame 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: 9ab5cbaf600fe7970bdff229b43d34fd04c8fbb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294043"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 클래스

드롭다운 도구 모음 및 드롭다운 도구 모음 단추에 드롭다운 프레임 창 기능을 제공 합니다.

## <a name="syntax"></a>구문

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|`CMFCDropDownFrame::CMFCDropDownFrame`|기본 생성자입니다.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCDropDownFrame:: Create](#create)|`CMFCDropDownFrame` 개체를 만듭니다.|
|`CMFCDropDownFrame::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|드롭다운 프레임의 부모 메뉴 모음을 검색 합니다.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|드롭다운 프레임의 부모 팝업 메뉴를 검색 합니다.|
|`CMFCDropDownFrame::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCDropDownFrame:: RecalcLayout](#recalclayout)|드롭다운 프레임의 위치를 이동 합니다.|
|[CMFCDropDownFrame:: SetAutoDestroy](#setautodestroy)|자식 드롭다운 도구 모음 창이 자동으로 소멸 되는지 여부를 설정 합니다.|

### <a name="remarks"></a>설명

이 클래스는 사용자 코드에서 직접 사용할 수 없습니다.

프레임 워크는이 클래스를 사용 하 여 및 클래스에 프레임 동작을 제공 합니다 `CMFCDropDownToolbar` `CMFCDropDownToolbarButton` . 이러한 클래스에 대 한 자세한 내용은 [CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md) 및 [CMFCDropDownToolbarButton 클래스](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 개체에 대 한 포인터를 검색 하는 방법과 `CMFCDropDownFrame` `CFrameWnd` 자식 드롭다운 도구 모음 창이 자동으로 소멸 되도록 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a> CMFCDropDownFrame:: Create

`CMFCDropDownFrame` 개체를 만듭니다.

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>매개 변수

*pWndParent*\
진행 드롭다운 프레임의 부모 창입니다.

*.x*\
진행 아래쪽 프레임 위치의 가로 화면 좌표입니다.

*x.y*\
진행 아래쪽 프레임 위치의 세로 화면 좌표입니다.

*pWndOriginToolbar*\
진행 이 메서드가 새 드롭다운 프레임 개체를 채우는 데 사용 하는 드롭다운 단추가 있는 도구 모음입니다.

### <a name="return-value"></a>반환 값

드롭다운 프레임이 성공적으로 생성 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 기본 [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) 메서드를 호출 하 여 WS_POPUP 스타일이 있는 드롭다운 프레임 창을 만듭니다. 지정 된 화면 좌표에 드롭다운 프레임 창이 표시 됩니다. [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) 메서드가 FALSE를 반환 하는 경우이 메서드는 실패 합니다.

`CMFCDropDownFrame`클래스는 제공 된 매개 변수의 복사본을 만듭니다 `CMFCDropDownToolBar` . 이 메서드는 매개 변수에서 데이터 멤버로 단추 이미지 및 단추 상태를 복사 `pWndOriginToolbar` `m_pWndOriginToolbar` 합니다.

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a> CMFCDropDownFrame::GetParentMenuBar

드롭다운 프레임의 부모 메뉴 모음을 검색 합니다.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>반환 값

드롭다운 프레임의 부모 메뉴 모음에 대 한 포인터 이거나, 프레임에 부모가 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 부모 단추에서 부모 메뉴 모음을 검색 합니다. 이 메서드는 드롭다운 프레임에 부모 단추가 없거나 부모 단추에 부모 메뉴 모음이 없는 경우 NULL을 반환 합니다.

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a> CMFCDropDownFrame::GetParentPopupMenu

드롭다운 프레임의 부모 팝업 메뉴를 검색 합니다.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>반환 값

드롭다운 프레임의 부모 드롭다운 메뉴에 대 한 포인터 이거나, 프레임에 부모가 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 부모 단추에서 부모 메뉴를 검색 합니다. 드롭다운 프레임에 부모 단추가 없거나 부모 단추에 부모 메뉴가 없으면이 메서드는 NULL을 반환 합니다.

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a> CMFCDropDownFrame:: RecalcLayout

드롭다운 프레임의 위치를 이동 합니다.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>매개 변수

*bNotify*\
진행 사용 되지 않는.

### <a name="remarks"></a>설명

프레임 워크는 드롭다운 프레임이 만들어지거나 부모 창의 크기가 조정 될 때이 메서드를 호출 합니다. 이 메서드는 부모 창의 위치와 크기를 사용 하 여 드롭다운 프레임의 위치와 크기를 계산 합니다.

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a> CMFCDropDownFrame:: SetAutoDestroy

자식 드롭다운 도구 모음 창이 자동으로 소멸 되는지 여부를 설정 합니다.

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*bAutoDestroy*<br/>
진행 연결 된 드롭다운 도구 모음 창을 자동으로 삭제 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*Bautodestroy* TRUE 이면 `CMFCDropDownFrame` 소멸자가 연결 된 드롭다운 도구 모음 창을 소멸 시킵니다. 기본값은 TRUE입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton 클래스](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
