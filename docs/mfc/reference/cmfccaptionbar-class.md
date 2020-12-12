---
description: '자세한 정보: CMFCCaptionBar 클래스'
title: CMFCCaptionBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: a5dd5f968c52268935b6176115e8723a9d82e8a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327734"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar 클래스

`CMFCCaptionBar`개체는 단추, 텍스트 레이블, 비트맵의 세 가지 요소를 표시할 수 있는 컨트롤 막대입니다. 각 형식의 요소를 한 번에 하나만 표시할 수 있습니다. 각 요소를 컨트롤의 왼쪽 또는 오른쪽 가장자리나 가운데에 맞출 수 있습니다. 평면 또는 3D 스타일을 캡션 표시줄의 위쪽 및 아래쪽 테두리에 적용할 수도 있습니다.

## <a name="syntax"></a>구문

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCCaptionBar:: Create](#create)|캡션 표시줄 컨트롤을 만들고 개체에 연결 `CMFCCaptionBar` 합니다.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|다른 창이 캡션 표시줄과 부모 프레임 사이에서 동적으로 삽입 될 수 있는지 여부를 나타냅니다. [Cbasepane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)를 재정의 합니다.|
|[CMFCCaptionBar:: EnableButton](#enablebutton)|캡션 표시줄에서 단추를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CMFCCaptionBar:: GetAlignment](#getalignment)|지정 된 요소의 맞춤을 반환 합니다.|
|[CMFCCaptionBar:: GetBorderSize](#getbordersize)|캡션 표시줄의 테두리 크기를 반환 합니다.|
|[CMFCCaptionBar:: GetButtonRect](#getbuttonrect)|캡션 표시줄에서 단추의 경계 사각형을 검색 합니다.|
|[CMFCCaptionBar:: GetMargin](#getmargin)|캡션 표시줄 요소와 캡션 표시줄 컨트롤의 가장자리 사이의 거리를 반환 합니다.|
|[CMFCCaptionBar:: Ismessagebar 모드](#ismessagebarmode)|캡션 표시줄이 메시지 표시줄 모드에 있는지 여부를 지정 합니다.|
|[CMFCCaptionBar:: RemoveBitmap](#removebitmap)|캡션 표시줄에서 비트맵 이미지를 제거 합니다.|
|[CMFCCaptionBar:: RemoveButton](#removebutton)|캡션 표시줄에서 단추를 제거 합니다.|
|[CMFCCaptionBar:: RemoveIcon](#removeicon)|캡션 표시줄에서 아이콘을 제거 합니다.|
|[CMFCCaptionBar:: RemoveText](#removetext)|캡션 표시줄에서 텍스트 레이블을 제거 합니다.|
|[CMFCCaptionBar:: SetBitmap](#setbitmap)|캡션 표시줄의 비트맵 이미지를 설정 합니다.|
|[CMFCCaptionBar:: SetBorderSize](#setbordersize)|캡션 표시줄의 테두리 크기를 설정 합니다.|
|[CMFCCaptionBar:: SetButton](#setbutton)|캡션 표시줄의 단추를 설정 합니다.|
|[CMFCCaptionBar:: SetButtonPressed](#setbuttonpressed)|단추를 눌렀는지 여부를 지정 합니다.|
|[CMFCCaptionBar:: SetButtonToolTip](#setbuttontooltip)|단추에 대 한 도구 설명을 설정 합니다.|
|[CMFCCaptionBar:: SetFlatBorder](#setflatborder)|캡션 표시줄의 테두리 스타일을 설정 합니다.|
|[CMFCCaptionBar:: SetIcon](#seticon)|캡션 표시줄의 아이콘을 설정 합니다.|
|[CMFCCaptionBar:: SetImageToolTip](#setimagetooltip)|캡션 표시줄의 이미지에 대 한 도구 설명을 설정 합니다.|
|[CMFCCaptionBar:: SetMargin](#setmargin)|캡션 표시줄 요소와 캡션 표시줄 컨트롤의 가장자리 사이의 거리를 설정 합니다.|
|[CMFCCaptionBar:: SetText](#settext)|캡션 표시줄의 텍스트 레이블을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCCaptionBar:: OnDrawBackground](#ondrawbackground)|캡션 표시줄의 배경을 채우기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCCaptionBar:: OnDrawBorder](#ondrawborder)|캡션 표시줄의 테두리를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCCaptionBar:: OnDrawButton](#ondrawbutton)|캡션 표시줄 단추를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCCaptionBar:: OnDrawImage](#ondrawimage)|캡션 표시줄 이미지를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCCaptionBar:: OnDrawText](#ondrawtext)|캡션 표시줄 텍스트를 그리기 위해 프레임 워크에서 호출 됩니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCCaptionBar:: m_clrBarBackground](#m_clrbarbackground)|캡션 표시줄의 배경색입니다.|
|[CMFCCaptionBar:: m_clrBarBorder](#m_clrbarborder)|캡션 표시줄 테두리의 색입니다.|
|[CMFCCaptionBar:: m_clrBarText](#m_clrbartext)|캡션 표시줄 텍스트의 색입니다.|

## <a name="remarks"></a>설명

캡션 표시줄을 만들려면 다음 단계를 수행 합니다.

1. `CMFCCaptionBar` 개체를 생성합니다. 일반적으로는 프레임 창 클래스에 캡션 표시줄을 추가 합니다.

1. [Cmfccaptionbar:: Create](#create) 메서드를 호출 하 여 캡션 표시줄 컨트롤을 만들고 개체에 연결 `CMFCCaptionBar` 합니다.

1. [Cmfccaptionbar:: SetButton](#setbutton), [Cmfccaptionbar](#settext):: SetText, Cmfccaptionbar:: [Setbutton](#seticon)및 [Cmfccaptionbar:: setbutton](#setbitmap) 을 호출 하 여 캡션 표시줄 요소를 설정 합니다.

Button 요소를 설정 하는 경우 단추에 명령 ID를 할당 해야 합니다. 사용자가 단추를 클릭 하면 캡션 표시줄에서이 ID를 가진 WM_COMMAND 메시지를 부모 프레임 창으로 라우팅합니다.

Microsoft Office 2007 응용 프로그램에 표시 되는 메시지 표시줄을 에뮬레이트하는 메시지 표시줄 모드 에서도 캡션 표시줄을 사용할 수 있습니다. 메시지 표시줄 모드에서 캡션 표시줄에는 비트맵, 메시지 및 단추가 표시 됩니다 (일반적으로 대화 상자를 열림). 도구 설명을 비트맵에 할당할 수 있습니다.

메시지 표시줄 모드를 사용 하도록 설정 하려면 [Cmfccaptionbar:: Create](#create) 를 호출 하 고 네 번째 매개 변수 (bIsMessageBarMode)를 TRUE로 설정 합니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCCaptionBar` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 캡션 표시줄 컨트롤을 만들고, 캡션 표시줄의 3D 테두리를 설정 하 고, 캡션 표시줄 요소와 캡션 표시줄 컨트롤의 가장자리 사이의 거리를 픽셀 단위로 설정 하 고, 캡션 표시줄의 단추를 설정 하 고, 캡션 표시줄의 텍스트 레이블을 설정 하 고, 캡션 표시줄의 비트맵 이미지를 설정 하는 방법을 보여 줍니다. 를 선택한 다음 캡션 표시줄에서 이미지에 대 한 도구 설명을 설정 합니다. 이 코드 조각은 [MS Office 2007 Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcaptionbar

## <a name="cmfccaptionbarcreate"></a><a name="create"></a> CMFCCaptionBar:: Create

캡션 표시줄 컨트롤을 만들고 개체에 연결 `CMFCCaptionBar` 합니다.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
캡션 표시줄 스타일의 논리적 또는 조합입니다.

*pParentWnd*<br/>
캡션 표시줄 컨트롤의 부모 창입니다.

*uID*<br/>
캡션 표시줄 컨트롤의 ID입니다.

*nHeight*<br/>
캡션 표시줄 컨트롤의 높이 (픽셀)입니다. -1 인 경우에는 캡션 표시줄 컨트롤이 표시 하는 아이콘의 높이, 텍스트 및 단추에 따라 높이가 계산 됩니다.

*bIsMessageBarMode*<br/>
캡션 표시줄이 메시지 표시줄 모드에 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

캡션 표시줄 컨트롤이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`CMFCCaptionBar`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음 `Create` Windows 컨트롤을 만들고이를 개체에 연결 하는 메서드를 호출 합니다 `CMFCCaptionBar` .

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCCaptionBar::D oesAllowDynInsertBefore

다른 창이 캡션 표시줄과 부모 프레임 사이에서 동적으로 삽입 될 수 있는지 여부를 나타냅니다.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>반환 값

재정의 되지 않는 경우 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a> CMFCCaptionBar:: EnableButton

캡션 표시줄에서 단추를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 단추를 사용 하려면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a> CMFCCaptionBar:: GetAlignment

지정 된 요소의 맞춤을 반환 합니다.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>매개 변수

*e*<br/>
진행 맞춤을 검색할 캡션 표시줄 요소입니다.

### <a name="return-value"></a>반환 값

단추, 비트맵, 텍스트 또는 아이콘과 같은 요소의 맞춤입니다.

### <a name="remarks"></a>설명

요소의 맞춤은 다음 값 중 하나일 수 있습니다.

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a> CMFCCaptionBar:: GetBorderSize

캡션 표시줄의 테두리 크기를 반환 합니다.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>반환 값

테두리의 크기 (픽셀)입니다.

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a> CMFCCaptionBar:: GetButtonRect

캡션 표시줄에서 단추의 경계 사각형을 검색 합니다.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>반환 값

`CRect`캡션 표시줄에 있는 단추의 경계 사각형 좌표를 포함 하는 개체입니다.

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a> CMFCCaptionBar:: GetMargin

캡션 표시줄 요소와 캡션 표시줄 컨트롤의 가장자리 사이의 거리를 반환 합니다.

```
int GetMargin() const;
```

### <a name="return-value"></a>반환 값

캡션 표시줄 요소와 캡션 표시줄 컨트롤의 가장자리 사이의 거리 (픽셀)입니다.

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a> CMFCCaptionBar:: Ismessagebar 모드

캡션 표시줄이 메시지 표시줄 모드에 있는지 여부를 지정 합니다.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>반환 값

캡션 표시줄이 메시지 표시줄 모드에 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

메시지 표시줄 모드에서 캡션 표시줄에는 도구 설명, 메시지 텍스트 및 단추가 있는 이미지가 표시 됩니다.

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a> CMFCCaptionBar:: m_clrBarBackground

캡션 표시줄의 배경색입니다.

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a> CMFCCaptionBar:: m_clrBarBorder

캡션 표시줄 테두리의 색입니다.

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a> CMFCCaptionBar:: m_clrBarText

캡션 표시줄 텍스트의 색입니다.

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a> CMFCCaptionBar:: OnDrawBackground

캡션 표시줄의 배경을 채우기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 캡션 표시줄의 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 채울 경계 사각형입니다.

### <a name="remarks"></a>설명

`OnDrawBackground`메서드는 캡션 표시줄의 배경이 채워질 때 호출 됩니다. 기본 구현은 [Cmfccaptionbar:: m_clrBarBackground](#m_clrbarbackground) 색을 사용 하 여 배경을 채웁니다.

파생 클래스에서이 메서드 `CMFCCaptionBar` 를 재정의 하 여 캡션 표시줄의 모양을 사용자 지정 합니다.

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a> CMFCCaptionBar:: OnDrawBorder

캡션 표시줄의 테두리를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 테두리를 표시 하는 데 사용 되는 장치 컨텍스트입니다.

*rect*<br/>
진행 경계 사각형입니다.

### <a name="remarks"></a>설명

기본적으로 테두리에는 평면 스타일이 있습니다.

파생 클래스에서이 메서드 `CMFCCaptionBar` 를 재정의 하 여 캡션 표시줄 테두리의 모양을 사용자 지정 합니다.

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a> CMFCCaptionBar:: OnDrawButton

캡션 표시줄 단추를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 데 사용 되는 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 단추의 경계 사각형입니다.

*strButton*<br/>
진행 단추의 텍스트 레이블입니다.

*bEnabled*<br/>
진행 단추를 사용할 수 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

파생 클래스에서이 메서드 `CMFCCaptionBar` 를 재정의 하 여 캡션 표시줄 단추의 모양을 사용자 지정 합니다.

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a> CMFCCaptionBar:: OnDrawImage

캡션 표시줄 이미지를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 이미지를 표시 하는 데 사용 되는 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 이미지의 경계 사각형을 지정 합니다.

### <a name="remarks"></a>설명

파생 클래스에서이 메서드 `CMFCCaptionBar` 를 재정의 하 여 이미지 모양을 사용자 지정 합니다.

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a> CMFCCaptionBar:: OnDrawText

캡션 표시줄 텍스트를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 데 사용 되는 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 텍스트의 경계 사각형입니다.

*strText*<br/>
진행 표시할 텍스트 문자열입니다.

### <a name="remarks"></a>설명

기본 구현에서는 `CDC::DrawText` 및 [Cmfccaptionbar:: m_clrBarText](#m_clrbartext) 색을 사용 하 여 텍스트를 표시 합니다.

`CMFCCaptionBar`캡션 표시줄의 텍스트 모양을 사용자 지정 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a> CMFCCaptionBar:: RemoveBitmap

캡션 표시줄에서 비트맵 이미지를 제거 합니다.

```cpp
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a> CMFCCaptionBar:: RemoveButton

캡션 표시줄에서 단추를 제거 합니다.

```cpp
void RemoveButton();
```

### <a name="remarks"></a>설명

캡션 표시줄 요소의 레이아웃이 자동으로 조정 됩니다.

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a> CMFCCaptionBar:: RemoveIcon

캡션 표시줄에서 아이콘을 제거 합니다.

```cpp
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a> CMFCCaptionBar:: RemoveText

캡션 표시줄에서 텍스트 레이블을 제거 합니다.

```cpp
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a> CMFCCaptionBar:: SetBitmap

캡션 표시줄의 비트맵 이미지를 설정 합니다.

```cpp
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>매개 변수

*hBitmap*<br/>
진행 설정할 비트맵에 대 한 핸들입니다.

*clrTransparent*<br/>
진행 비트맵의 투명 한 색을 지정 하는 RGB 값입니다.

*bStretch*<br/>
진행 TRUE 이면 이미지 경계 사각형에 맞지 않는 비트맵이 늘어납니다. 그렇지 않으면 비트맵이 확장 되지 않습니다.

*bmpAlignment*<br/>
진행 비트맵의 맞춤입니다.

### <a name="remarks"></a>설명

캡션 표시줄에 비트맵을 설정 하려면이 메서드를 사용 합니다.

이전 비트맵이 자동으로 삭제 됩니다. [Cmfccaptionbar:: seticon](#seticon) 메서드를 호출 하 여 캡션 표시줄에 아이콘이 표시 되는 경우 [Cmfccaptionbar:: removeicon](#removeicon)을 호출 하 여 아이콘을 제거 하지 않으면 비트맵이 표시 되지 않습니다.

*Bmpalignment* 매개 변수에 지정 된 대로 비트맵이 정렬 됩니다.  이 매개 변수는 다음 `BarElementAlignment` 값 중 하나일 수 있습니다.

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a> CMFCCaptionBar:: SetBorderSize

캡션 표시줄의 테두리 크기를 설정 합니다.

```cpp
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>매개 변수

*nSize*<br/>
진행 캡션 표시줄 테두리의 새 크기 (픽셀)입니다.

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a> CMFCCaptionBar:: SetButton

캡션 표시줄의 단추를 설정 합니다.

```cpp
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
단추의 명령 레이블입니다.

*uiCmdUI*<br/>
단추의 명령 ID입니다.

*btnAlignmnet*<br/>
단추의 맞춤입니다.

*bHasDropDownArrow*<br/>
단추에 드롭다운 화살표가 표시 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a> CMFCCaptionBar:: SetButtonPressed

단추를 눌렀는지 여부를 지정 합니다.

```cpp
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>매개 변수

*B보도*<br/>
단추가 눌러진 상태를 유지 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a> CMFCCaptionBar:: SetButtonToolTip

단추에 대 한 도구 설명을 설정 합니다.

```cpp
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszToolTip*<br/>
진행 도구 설명 캡션입니다.

*lpszDescription*<br/>
진행 도구 설명에 대 한 설명입니다.

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a> CMFCCaptionBar:: SetFlatBorder

캡션 표시줄의 테두리 스타일을 설정 합니다.

```cpp
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>매개 변수

*bFlat*<br/>
진행 캡션 표시줄의 테두리가 플랫 이면 TRUE입니다. 테두리가 3D 이면 FALSE입니다.

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a> CMFCCaptionBar:: SetIcon

캡션 표시줄의 아이콘을 설정 합니다.

```cpp
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>매개 변수

*hIcon*<br/>
진행 설정할 아이콘에 대 한 핸들입니다.

*iconAlignment*<br/>
진행 아이콘의 맞춤입니다.

### <a name="remarks"></a>설명

캡션 표시줄에 아이콘이 나 비트맵 중 하나가 표시 될 수 있습니다. 비트맵을 표시 하는 방법을 알아보려면 [Cmfccaptionbar:: SetBitmap](#setbitmap) 을 참조 하세요. 아이콘과 비트맵을 모두 설정 하면 아이콘이 항상 표시 됩니다. [Cmfccaptionbar:: RemoveIcon](#removeicon) 을 호출 하 여 캡션 표시줄에서 아이콘을 제거 합니다.

아이콘은 *Iconalignment* 매개 변수에 따라 정렬 됩니다. 다음 값 중 하나일 수 있습니다 `BarElementAlignment` .

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a> CMFCCaptionBar:: SetImageToolTip

캡션 표시줄의 이미지에 대 한 도구 설명을 설정 합니다.

```cpp
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszToolTip*<br/>
진행 도구 설명의 텍스트입니다.

*lpszDescription*<br/>
진행 도구 설명에 대 한 설명입니다.

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a> CMFCCaptionBar:: SetMargin

캡션 표시줄 요소와 캡션 표시줄 컨트롤의 가장자리 사이의 거리를 설정 합니다.

```cpp
void SetMargin(int nMargin);
```

### <a name="parameters"></a>매개 변수

*nMargin*<br/>
진행 캡션 표시줄 요소와 캡션 표시줄 컨트롤의 가장자리 사이의 거리 (픽셀)입니다.

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a> CMFCCaptionBar:: SetText

캡션 표시줄의 텍스트 레이블을 설정 합니다.

```cpp
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>매개 변수

*strText*<br/>
진행 설정할 텍스트 문자열입니다.

*textAlignment*<br/>
진행 텍스트 맞춤입니다.

### <a name="remarks"></a>설명

텍스트 레이블이 *Textalignment* 매개 변수에 의해 지정 된 대로 정렬 됩니다. 다음 값 중 하나일 수 있습니다 `BarElementAlignment` .

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
