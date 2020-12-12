---
description: '자세한 정보: CMFCCaptionButton 클래스'
title: CMFCCaptionButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: 6c3c1cbeea4a548f2951276b3ad43cb598cf22a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327757"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton 클래스

`CMFCCaptionButton`클래스는 도킹 창이 나 미니 프레임 창의 캡션 표시줄에 표시 되는 단추를 구현 합니다. 일반적으로 프레임워크는 캡션 단추를 자동으로 만듭니다.

## <a name="syntax"></a>구문

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|----------|-----------------|
|[CMFCCaptionButton:: CMFCCaptionButton](#cmfccaptionbutton)|CMFCCaptionButton 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCCaptionButton:: GetHit](#gethit)|단추로 표시 되는 명령을 반환 합니다.|
|[CMFCCaptionButton:: GetIconID](#geticonid)|단추와 연결 된 이미지 ID를 반환 합니다.|
|[CMFCCaptionButton:: GetRect](#getrect)|단추가 차지 하는 사각형을 반환 합니다.|
|[CMFCCaptionButton:: GetSize](#getsize)|단추의 너비와 높이를 반환 합니다.|
|[CMFCCaptionButton:: Is미니 프레임 단추](#isminiframebutton)|제목 표시줄 높이가 미니 크기로 설정 되어 있는지 여부를 나타냅니다.|
|[CMFCCaptionButton:: Move](#move)|단추 그리기 위치 및 창 표시 상태를 설정 합니다.|
|[CMFCCaptionButton:: OnDraw](#ondraw)|캡션 단추를 그립니다.|
|[CMFCCaptionButton:: Set미니 프레임 단추](#setminiframebutton)|제목 표시줄의 미니 크기를 설정 합니다.|

## <a name="remarks"></a>설명

[CPaneFrameWnd 클래스](../../mfc/reference/cpaneframewnd-class.md) 에서 클래스를 파생 시키고 protected 메서드인를 사용 `AddButton` 하 여 미니 프레임 창에 캡션 단추를 추가할 수 있습니다.

CPaneFrameWnd는 두 가지 유형의 캡션 단추에 대 한 명령 Id를 정의 합니다.

- 도킹 창에서 자동 숨기기 모드를 지원할 때 핀 단추를 표시 하는 AFX_CAPTION_BTN_PIN.

- AFX_CAPTION_BTN_CLOSE 창을 닫거나 숨길 수 있는 **닫기** 단추를 표시 합니다.

## <a name="example"></a>예제

다음 예제에서는 개체를 생성 하 `CMFCCaptionButton` 고 제목 표시줄의 미니 크기를 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcaptionbutton

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a> CMFCCaptionButton:: CMFCCaptionButton

`CMFCCaptionButton` 개체를 생성합니다.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>매개 변수

*n 적중*<br/>
진행 단추와 연결 된 명령입니다.

*B왼쪽 맞춤*<br/>
진행 단추를 왼쪽에 맞출지 여부를 지정 합니다.

다음 표에서는 *Nhit* 매개 변수에 사용할 수 있는 값을 보여 줍니다.

|값|명령|
|-----------|-------------|
|AFX_HTCLOSE|닫기 단추|
|HTMINBUTTON|최소화 단추.|
|HTMAXBUTTON|최대화 단추.|
|AFX_HTLEFTBUTTON|왼쪽 화살표 단추입니다.|
|AFX_HTRIGHTBUTTON|오른쪽 화살표 단추입니다.|
|AFX_HTMENU|아래쪽 화살표 메뉴 단추입니다.|
|HTNOWHERE|기본값은입니다. 명령을 표시 하지 않습니다.|

### <a name="remarks"></a>설명

기본적으로 캡션 단추는 명령과 연결 되지 않습니다.

캡션 단추는 오른쪽 이나 왼쪽에 정렬 됩니다.

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a> CMFCCaptionButton:: GetHit

단추로 표시 되는 명령을 반환 합니다.

```
UINT GetHit() const;
```

### <a name="return-value"></a>반환 값

단추가 나타내는 명령입니다.

다음 표에서는 가능한 반환 값을 보여 줍니다.

|값|명령|
|-----------|-------------|
|AFX_HTCLOSE|닫기 단추|
|HTMINBUTTON|최소화 단추.|
|HTMAXBUTTON|최대화 단추.|
|AFX_HTLEFTBUTTON|왼쪽 화살표 단추입니다.|
|AFX_HTRIGHTBUTTON|오른쪽 화살표 단추입니다.|
|AFX_HTMENU|아래쪽 화살표 메뉴 단추입니다.|
|HTNOWHERE|기본값은입니다. 명령을 표시 하지 않습니다.|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a> CMFCCaptionButton:: GetIconID

단추와 연결 된 이미지 ID를 반환 합니다.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>매개 변수

*bHorz*<br/>
진행 왼쪽 또는 오른쪽 화살표 이미지 Id의 경우 TRUE입니다. 위쪽 또는 아래쪽 화살표 이미지 Id의 경우 FALSE입니다.

*bMaximized*<br/>
진행 이미지 ID 최대화의 경우 TRUE입니다. 이미지 ID 최소화의 경우 FALSE입니다.

### <a name="return-value"></a>반환 값

이미지 ID입니다.

### <a name="remarks"></a>설명

매개 변수는 캡션 단추를 최소화 하거나 최대화 하기 위한 이미지 Id를 지정 합니다.

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a> CMFCCaptionButton:: GetRect

단추가 차지 하는 사각형을 반환 합니다.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>반환 값

단추의 위치를 나타내는 사각형입니다.

### <a name="remarks"></a>설명

단추를 볼 수 없는 경우 반환 되는 크기는 0입니다.

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a> CMFCCaptionButton:: GetSize

단추의 너비와 높이를 반환 합니다.

```
static CSize GetSize();
```

### <a name="return-value"></a>반환 값

단추의 외부 크기입니다.

### <a name="remarks"></a>설명

반환 되는 크기는 단추 여백 및 테두리를 포함 합니다.

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a> CMFCCaptionButton:: Is미니 프레임 단추

제목 표시줄 높이가 미니 크기로 설정 되어 있는지 여부를 나타냅니다.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>반환 값

캡션이 미니 크기로 설정 된 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a> CMFCCaptionButton:: Move

단추 그리기 위치 및 창 표시 상태를 설정 합니다.

```cpp
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>매개 변수

*ptTo*<br/>
진행 새 위치입니다.

*bHide*<br/>
진행 단추를 표시할지 여부를 지정 합니다.

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a> CMFCCaptionButton:: OnDraw

캡션 단추를 그립니다.

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추의 장치 컨텍스트에 대 한 포인터입니다.

*bActive*<br/>
진행 활성 단추 이미지를 그릴지 여부를 나타냅니다.

*bHorz*<br/>
진행 파생 클래스에서 사용 하도록 예약 되어 있습니다.

*bMaximized*<br/>
진행 최대화 된 단추 이미지를 그릴지 여부를 나타냅니다.

*bDisabled*<br/>
진행 활성화 된 단추 이미지를 그릴지 여부를 지정 합니다.

### <a name="remarks"></a>설명

*Bmaximized* 된 매개 변수는 단추가 최대화 또는 최소화 단추인 경우 사용 됩니다.

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a> CMFCCaptionButton:: Set미니 프레임 단추

제목 표시줄의 미니 크기를 설정 합니다.

```cpp
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>매개 변수

*bSet*<br/>
진행 미니 제목 표시줄 높이의 경우 TRUE입니다. 기본 제목 표시줄 높이의 경우 FALSE입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd 클래스](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)
