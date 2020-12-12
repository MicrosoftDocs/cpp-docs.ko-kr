---
description: '자세히 알아보기: CMFCPropertyGridToolTipCtrl 클래스'
title: CMFCPropertyGridToolTipCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 5e560d09756be99c00257c351b58223b37a6b5da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289883"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 클래스

[Cmfcpropertygridctrl 클래스](../../mfc/reference/cmfcpropertygridctrl-class.md) 에서 도구 설명을 표시 하는 데 사용 하는 도구 설명 컨트롤을 구현 합니다.

## <a name="syntax"></a>구문

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|`CMFCPropertyGridToolTipCtrl` 개체를 생성합니다.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCPropertyGridToolTipCtrl:: Create](#create)|Tooltip 컨트롤의 창을 만듭니다.|
|[CMFCPropertyGridToolTipCtrl::D eactivate](#deactivate)|도구 설명 컨트롤을 비활성화 하 고 숨깁니다.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Tooltip 컨트롤의 마지막 위치 좌표를 반환 합니다.|
|[CMFCPropertyGridToolTipCtrl:: Hide](#hide)|Tooltip 컨트롤을 숨깁니다.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|창 메시지가 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 및 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) Windows 함수로 디스패치되기 전에 [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) 클래스가 이 메시지를 해석하는 데 사용됩니다. ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 재정의합니다.)|
|[CMFCPropertyGridToolTipCtrl:: SetTextMargin](#settextmargin)|도구 설명 텍스트와 도구 설명 창의 테두리 사이의 간격을 설정 합니다.|
|[CMFCPropertyGridToolTipCtrl:: Track](#track)|Tooltip 컨트롤을 표시 합니다.|

## <a name="remarks"></a>설명

포인터가 속성 이름 위에 있을 때 도구 설명이 표시 됩니다. [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) 클래스는 사용자가 쉽게 읽을 수 있도록 도구 설명을 표시 합니다. 일반적으로 도구 설명의 위치는 포인터의 위치에 따라 결정 됩니다. 이 클래스를 사용 하 여 속성 이름 위에 도구 설명을 표시 하 고 속성 이름이 완전히 표시 되도록 자연 속성 확장과 유사 합니다.

MFC는이 컨트롤을 자동으로 만들고 [Cmfcpropertygridctrl 클래스](../../mfc/reference/cmfcpropertygridctrl-class.md)에서 사용 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법과 도구 설명 컨트롤을 표시 하는 방법을 보여 줍니다 `CMFCPropertyGridToolTipCtrl` .

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpropertygridtooltipctrl

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a> CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

`CMFCPropertyGridToolTipCtrl` 개체를 생성합니다.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a> CMFCPropertyGridToolTipCtrl:: Create

Tooltip 컨트롤의 창을 만듭니다.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 부모 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

창이 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a> CMFCPropertyGridToolTipCtrl::D eactivate

도구 설명 컨트롤을 비활성화 하 고 숨깁니다.

```cpp
void Deactivate();
```

### <a name="remarks"></a>설명

이 메서드는 마지막 위치와 텍스트를 빈 값으로 설정 하므로 나중에 [CMFCPropertyGridToolTipCtrl:: Track](#track) 을 호출 하면 도구 설명이 표시 됩니다.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a> CMFCPropertyGridToolTipCtrl::GetLastRect

Tooltip 컨트롤의 마지막 위치 좌표를 반환 합니다.

```cpp
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
제한이 Tooltip 컨트롤의 마지막 위치를 포함 합니다.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a> CMFCPropertyGridToolTipCtrl:: Hide

Tooltip 컨트롤을 숨깁니다.

```cpp
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a> CMFCPropertyGridToolTipCtrl:: SetTextMargin

도구 설명 텍스트와 도구 설명 창의 테두리 사이의 간격을 설정 합니다.

```cpp
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>매개 변수

*nTextMargin*<br/>
진행 도구 설명 컨트롤 텍스트와 도구 설명 창의 테두리 사이의 간격을 지정 합니다. 기본값은 10 픽셀입니다.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a> CMFCPropertyGridToolTipCtrl:: Track

Tooltip 컨트롤을 표시 합니다.

```cpp
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
진행 Tooltip 컨트롤의 위치와 크기를 지정 합니다.

*strText*<br/>
진행 도구 설명에 표시할 텍스트를 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 *rect* 에 의해 지정 된 위치와 크기에 대 한 도구 설명 컨트롤을 표시 합니다. 이 메서드가 마지막으로 호출 된 이후 위치, 크기 및 텍스트가 변경 되지 않은 경우이 메서드는 영향을 주지 않습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
