---
description: '자세한 정보: Cmfc리본 Statusbar 클래스'
title: Cmfc리본 Statusbar 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: 01436d535b410fd4a6c70f52760908e3547b7af8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265001"
---
# <a name="cmfcribbonstatusbar-class"></a>Cmfc리본 Statusbar 클래스

`CMFCRibbonStatusBar`클래스는 리본 요소를 표시할 수 있는 상태 표시줄 컨트롤을 구현 합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Statusbar:: AddDynamicElement](#adddynamicelement)|리본 상태 표시줄에 동적 요소를 추가 합니다.|
|[Cmfc리본 Statusbar:: AddElement](#addelement)|리본 상태 표시줄에 새 리본 요소를 추가 합니다.|
|[Cmfc리본 Statusbar:: AddExtendedElement](#addextendedelement)|리본 상태 표시줄의 확장 된 영역에 리본 요소를 추가 합니다.|
|[Cmfc리본 Statusbar:: AddSeparator](#addseparator)|리본 상태 표시줄에 구분 기호를 추가 합니다.|
|[Cmfc리본 Statusbar:: Create](#create)|리본 상태 표시줄을 만듭니다.|
|[Cmfc리본 Statusbar:: CreateEx](#createex)|확장 스타일을 사용 하 여 리본 상태 표시줄을 만듭니다.|
|[Cmfc리본 Statusbar:: FindByID](#findbyid)||
|[Cmfc리본 Statusbar:: FindElement](#findelement)|지정 된 명령 ID를 가진 요소에 대 한 포인터를 반환 합니다.|
|[Cmfc리본 Statusbar:: GetCount](#getcount)|리본 상태 표시줄의 기본 영역에 있는 요소 수를 반환 합니다.|
|[Cmfc리본 Statusbar:: GetElement](#getelement)|지정 된 인덱스에 있는 요소에 대 한 포인터를 반환 합니다.|
|[Cmfc리본 Statusbar:: GetExCount](#getexcount)|리본 상태 표시줄의 확장 된 영역에 있는 요소 수를 반환 합니다.|
|[Cmfc리본 Statusbar:: GetExElement](#getexelement)|리본 메뉴 상태 표시줄에서 확장된 영역의 지정한 인덱스에 있는 요소에 대한 포인터를 반환합니다.|
|[Cmfc리본 Statusbar:: GetExtendedArea](#getextendedarea)||
|[Cmfc리본 Statusbar:: GetSpace](#getspace)||
|[Cmfc리본 Statusbar:: IsBottomFrame](#isbottomframe)||
|[Cmfc리본 Statusbar:: IsExtendedElement](#isextendedelement)||
|[Cmfc리본 Statusbar:: IsInformationMode](#isinformationmode)|리본 상태 표시줄에 대해 정보 모드를 사용 하도록 설정할지 여부를 결정 합니다.|
|[Cmfc리본 Statusbar:: RecalcLayout](#recalclayout)|[Cmfc리본 표시줄:: RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout)를 재정의 합니다.|
|[Cmfc리본 Statusbar:: RemoveAll](#removeall)|리본 상태 표시줄에서 모든 요소를 제거 합니다.|
|[Cmfc리본 Statusbar:: RemoveElement](#removeelement)|리본 상태 표시줄에서 지정 된 명령 ID를 가진 요소를 제거 합니다.|
|[Cmfc리본 Statusbar:: SetInformation](#setinformation)|리본 상태 표시줄에 대 한 정보 모드를 사용 하거나 사용 하지 않도록 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[Cmfc리본 Statusbar:: OnDrawInformation](#ondrawinformation)|정보 모드를 사용 하는 경우 리본 상태 표시줄에 나타나는 정보 문자열을 표시 합니다.|

## <a name="remarks"></a>설명

사용자는 리본 상태 표시줄의 기본 제공 상황에 맞는 메뉴를 사용 하 여 리본 상태 표시줄에서 리본 요소의 표시 여부를 변경할 수 있습니다. 요소를 동적으로 추가 하거나 제거할 수 있습니다.

리본 상태 표시줄에는 주 영역과 확장 영역 이라는 두 가지 영역이 있습니다. 확장 영역이 리본 상태 표시줄의 오른쪽에 표시 되 고 주 영역과 다른 색으로 표시 됩니다.

일반적으로 상태 표시줄의 기본 영역에는 상태 알림이 표시 되 고 확장 영역에는 보기 컨트롤이 표시 됩니다. 확장 영역은 사용자가 리본 상태 표시줄의 크기를 조정할 때 가능한 한 오랫동안 표시 됩니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCRibbonStatusBar` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 리본 상태 표시줄에 새 리본 요소를 추가 하 고 리본 상태 표시줄의 확장 영역에 리본 요소를 추가 하 고 구분 기호를 추가 하 고 리본 상태 표시줄에 대 한 일반 모드를 사용 하도록 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonstatusbar

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a> Cmfc리본 Statusbar:: AddDynamicElement

리본 상태 표시줄에 동적 요소를 추가 합니다.

```cpp
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>매개 변수

*pElement*<br/>
진행 동적 요소에 대 한 포인터입니다.

### <a name="remarks"></a>설명

일반 요소와 달리 동적 요소는 사용자 지정할 수 없으며 상태 표시줄의 사용자 지정 메뉴에 표시 되지 않습니다.

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a> Cmfc리본 Statusbar:: AddElement

리본 상태 표시줄에 새 리본 요소를 추가 합니다.

```cpp
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>매개 변수

*pElement*<br/>
진행 추가 된 요소에 대 한 포인터입니다.

*lpszLabel*<br/>
진행 요소의 텍스트 레이블입니다.

*bIsVisible*<br/>
진행 요소를 표시 된 대로 추가 하려면 TRUE이 고, 요소를 숨김으로 추가 하려면 FALSE입니다.

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a> Cmfc리본 Statusbar:: AddExtendedElement

리본 상태 표시줄의 확장 된 영역에 리본 요소를 추가 합니다.

```cpp
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>매개 변수

*pElement*<br/>
진행 추가 된 요소에 대 한 포인터입니다.

*lpszLabel*<br/>
진행 요소의 텍스트 레이블입니다.

*bIsVisible*<br/>
진행 요소를 표시 된 대로 추가 하려면 TRUE이 고, 요소를 숨김으로 추가 하려면 FALSE입니다.

### <a name="remarks"></a>설명

확장된 영역은 상태 표시줄 컨트롤의 오른쪽에 있습니다.

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a> Cmfc리본 Statusbar:: AddSeparator

리본 상태 표시줄에 구분 기호를 추가 합니다.

```cpp
void AddSeparator();
```

### <a name="remarks"></a>설명

프레임 워크는 [Cmfc리본 statusbar:: AddElement](#addelement)메서드 뒤에 구분 기호를 추가 합니다. 마지막 요소를 삽입 합니다.

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a> Cmfc리본 Statusbar:: Create

리본 상태 표시줄을 만듭니다.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
진행 부모 창에 대 한 포인터입니다.

*dwStyle*<br/>
진행 컨트롤 스타일의 논리적 또는 조합입니다.

*nID*<br/>
진행 상태 표시줄의 컨트롤 ID입니다.

### <a name="return-value"></a>반환 값

상태 표시줄이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a> Cmfc리본 Statusbar:: CreateEx

확장 스타일을 포함 하는 리본 상태 표시줄을 만듭니다.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
부모 창에 대 한 포인터입니다.

*dwCtrlStyle*<br/>
상태 표시줄 개체 만들기에 대 한 추가 스타일의 논리적 또는 조합입니다.

*dwStyle*<br/>
상태 표시줄의 컨트롤 스타일입니다.

*nID*<br/>
상태 표시줄의 컨트롤 ID입니다.

### <a name="return-value"></a>반환 값

상태 표시줄이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a> Cmfc리본 Statusbar:: FindByID

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *Uicmdid*<br/>
진행 *BOOL*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a> Cmfc리본 Statusbar:: FindElement

지정 된 명령 ID를 가진 요소에 대 한 포인터를 반환 합니다.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 요소의 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 명령 ID를 가진 요소에 대 한 포인터입니다. 이러한 요소가 없는 경우 NULL입니다.

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a> Cmfc리본 Statusbar:: GetCount

리본 상태 표시줄의 기본 영역에 있는 요소 수를 반환 합니다.

```
int GetCount() const;
```

### <a name="return-value"></a>반환 값

리본 상태 표시줄의 기본 영역에 있는 요소 수입니다.

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a> Cmfc리본 Statusbar:: GetElement

지정 된 인덱스에 있는 요소에 대 한 포인터를 반환 합니다.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 상태 표시줄 컨트롤의 주 영역에 있는 요소의 인덱스 (0부터 시작)를 지정 합니다.

### <a name="return-value"></a>반환 값

지정 된 인덱스에 있는 요소에 대 한 포인터입니다. 인덱스가 음수 이거나 상태 표시줄의 요소 수를 초과 하면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a> Cmfc리본 Statusbar:: GetExCount

리본 상태 표시줄의 확장 된 영역에 있는 요소 수를 반환 합니다.

```
int GetExCount() const;
```

### <a name="return-value"></a>반환 값

리본 상태 표시줄의 확장 된 영역에 있는 요소 수입니다.

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a> Cmfc리본 Statusbar:: GetExElement

리본 메뉴 상태 표시줄에서 확장된 영역의 지정한 인덱스에 있는 요소에 대한 포인터를 반환합니다. 확장된 영역은 상태 표시줄 컨트롤의 오른쪽에 있습니다.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 상태 표시줄 컨트롤의 확장 된 영역에 있는 요소의 인덱스 (0부터 시작)를 지정 합니다.

### <a name="return-value"></a>반환 값

리본 메뉴 상태 표시줄에서 확장된 영역의 지정한 인덱스에 있는 요소에 대한 포인터입니다. *Nindex* 가 음수 이거나 리본 상태 표시줄의 확장 된 영역에 있는 요소 수를 초과 하는 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a> Cmfc리본 Statusbar:: GetExtendedArea

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>매개 변수

[in] *rect*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a> Cmfc리본 Statusbar:: GetSpace

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
int GetSpace() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a> Cmfc리본 Statusbar:: IsBottomFrame

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a> Cmfc리본 Statusbar:: IsExtendedElement

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>매개 변수

진행 *Pelement*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a> Cmfc리본 Statusbar:: IsInformationMode

리본 상태 표시줄에 대해 정보 모드를 사용 하도록 설정할지 여부를 결정 합니다.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>반환 값

상태 표시줄을 정보 모드에서 사용할 수 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

정보 모드에서 상태 표시줄은 모든 일반 창을 숨기고 메시지 문자열을 표시 합니다.

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a> Cmfc리본 Statusbar:: OnDrawInformation

정보 모드를 사용 하는 경우 리본 상태 표시줄에 표시 되는 문자열을 표시 합니다.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*strInfo*<br/>
진행 정보 문자열입니다.

*rectInfo*<br/>
진행 경계 사각형입니다.

### <a name="remarks"></a>설명

상태 표시줄에서 정보 문자열의 모양을 사용자 지정 하려면 파생 클래스에서이 메서드를 재정의 합니다. [Cmfc리본 statusbar:: setinformation](#setinformation) 메서드를 사용 하 여 상태 표시줄을 정보 모드로 전환 합니다. 이 모드에서 상태 표시줄은 모든 창을 숨기고 *Strinfo* 에 지정 된 정보 문자열을 표시 합니다.

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a> Cmfc리본 Statusbar:: RecalcLayout

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a> Cmfc리본 Statusbar:: RemoveAll

리본 상태 표시줄에서 모든 요소를 제거 합니다.

```cpp
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a> Cmfc리본 Statusbar:: RemoveElement

리본 상태 표시줄에서 지정 된 명령 ID를 가진 요소를 제거 합니다.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 상태 표시줄에서 제거할 요소의 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 *Uiid* 의 요소가 제거 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a> Cmfc리본 Statusbar:: SetInformation

리본 상태 표시줄에 대 한 정보 모드를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>매개 변수

*lpszInfo*<br/>
진행 정보 문자열입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 상태 표시줄을 정보 모드로 전환 합니다. 이 모드에서 상태 표시줄은 모든 창을 숨기고 *lpszInfo* 에 지정 된 정보 문자열을 표시 합니다.

LpszInfo가 NULL 인 경우 상태 표시줄은 일반 모드로 돌아갑니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 표시줄 클래스](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[Cmfc리본 Baseelement 클래스](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Cmfc리본 표시줄 클래스](../../mfc/reference/cmfcribbonbar-class.md)
