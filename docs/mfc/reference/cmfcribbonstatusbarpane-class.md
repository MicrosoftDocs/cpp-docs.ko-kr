---
description: '자세히 알아보기: CMFCRibbonStatusBarPane 클래스'
title: CMFCRibbonStatusBarPane 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
ms.openlocfilehash: 4ddbee5a6c44411ef2ac34bff3e07b47c3d950a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264988"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane 클래스

`CMFCRibbonStatusBarPane`클래스는 리본 상태 표시줄에 추가할 수 있는 리본 요소를 구현 합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCRibbonStatusBarPane:: CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|`CMFCRibbonStatusBarPane` 개체를 생성하고 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCRibbonStatusBarPane:: GetAlmostLargeText](#getalmostlargetext)|잘림 없이 창에 표시할 수 있는 가장 긴 텍스트 문자열을 정의 하는 문자열을 반환 합니다.|
|[CMFCRibbonStatusBarPane:: GetTextAlign](#gettextalign)|텍스트 맞춤의 현재 설정을 반환 합니다.|
|[CMFCRibbonStatusBarPane:: IsAnimation](#isanimation)|애니메이션이 진행 중인지 여부를 확인 합니다.|
|[CMFCRibbonStatusBarPane:: IsExtended](#isextended)|창이 리본 상태 표시줄의 확장 영역에 있는지 여부를 확인 합니다.|
|[CMFCRibbonStatusBarPane:: OnDrawBorder](#ondrawborder)|[Cmfc리본 단추:: OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder)를 재정의 합니다.|
|[CMFCRibbonStatusBarPane:: OnFillBackground](#onfillbackground)|[Cmfc리본 단추:: OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)를 재정의 합니다.|
|[CMFCRibbonStatusBarPane:: SetAlmostLargeText](#setalmostlargetext)|잘림 없이 창에 표시할 수 있는 가장 긴 텍스트 문자열을 정의 합니다.|
|[CMFCRibbonStatusBarPane:: Set애니메이션 목록](#setanimationlist)|애니메이션에 사용할 수 있는 이미지 목록을 창에 할당 합니다.|
|[CMFCRibbonStatusBarPane:: SetTextAlign](#settextalign)|텍스트 맞춤을 설정 합니다.|
|[CMFCRibbonStatusBarPane:: StartAnimation](#startanimation)|창에 할당 된 애니메이션을 시작 합니다.|
|[CMFCRibbonStatusBarPane:: StopAnimation](#stopanimation)|창에 할당 된 애니메이션을 중지 합니다. .|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCRibbonStatusBarPane:: Onation 애니메이션](#onfinishanimation)|창에 할당 된 애니메이션이 중지 될 때 프레임 워크에서 호출 됩니다.|

## <a name="example"></a>예제

다음 예제에서는 `CMFCRibbonStatusBarPane` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 개체를 생성 하 고 `CMFCRibbonStatusBarPane` , 상태 표시줄 창 레이블의 텍스트 맞춤을 설정 하 고, 상태 표시줄 창에 잘림 없이 표시할 수 있는 가장 긴 텍스트를 정의 하 고, 상태 표시줄 창에 연결 하 여 애니메이션을 시작 하 고, 애니메이션을 시작 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonstatusbarpane

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a> CMFCRibbonStatusBarPane:: CMFCRibbonStatusBarPane

상태 표시줄에 창 개체를 생성 합니다.

```
CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    BOOL bIsStatic=FALSE,
    HICON hIcon=NULL,
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);
```

### <a name="parameters"></a>매개 변수

*nCmdID*<br/>
진행 창의 명령 ID를 지정 합니다.

*lpszText*<br/>
진행 창에 표시할 텍스트 문자열을 지정 합니다.

*bIsStatic*<br/>
진행 TRUE 이면 상태 창을 강조 표시 하거나 클릭 하 여 선택할 수 없습니다.

*hIcon*<br/>
진행 창에 표시 되는 아이콘에 대 한 핸들을 지정 합니다.

*lpszAlmostLargeText*<br/>
진행 창에 표시할 수 있는 가장 긴 텍스트 문자열을 지정 합니다.

*hBmpAnimationList*<br/>
진행 애니메이션에 사용 되는 이미지 목록에 대 한 핸들을 지정 합니다.

*cxAnimation*<br/>
진행 애니메이션에 사용 되는 이미지 목록에 있는 아이콘의 너비 (픽셀)를 지정 합니다.

*clrTrnsp*<br/>
진행 애니메이션에 사용 되는 이미지 목록에 있는 이미지의 투명 한 색을 지정 합니다.

*uiAnimationListResID*<br/>
진행 애니메이션에 사용 되는 이미지 목록의 리소스 ID를 지정 합니다.

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a> CMFCRibbonStatusBarPane:: GetAlmostLargeText

상태 표시줄 창에 표시할 수 있는 가장 긴 텍스트 문자열을 가져옵니다.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>반환 값

상태 표시줄 창에 표시할 수 있는 가장 긴 텍스트 문자열입니다.

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a> CMFCRibbonStatusBarPane:: GetTextAlign

상태 표시줄 창에 있는 레이블의 텍스트 맞춤에 대 한 현재 설정을 가져옵니다.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>반환 값

다음 중 하나일 수 있는 현재 텍스트 맞춤입니다.

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a> CMFCRibbonStatusBarPane:: IsAnimation

애니메이션이 진행 중인지 여부를 확인 합니다.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>반환 값

애니메이션이 진행 중인 경우 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a> CMFCRibbonStatusBarPane:: IsExtended

창이 리본 상태 표시줄의 확장 영역에 있는지 여부를 확인 합니다.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>반환 값

창이 상태 표시줄 확장 영역에 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a> CMFCRibbonStatusBarPane:: OnDrawBorder

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>매개 변수

진행 *CDC&#42;*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a> CMFCRibbonStatusBarPane:: OnFillBackground

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a> CMFCRibbonStatusBarPane:: Onation 애니메이션

프레임 워크는 창에 할당 된 애니메이션이 종료 될 때이 메서드를 호출 합니다.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>설명

`StopAnimation` 메서드는 메서드를 호출 합니다 `OnFinishAnimation` .이 메서드는 애니메이션이 종료 될 때 데이터를 정리 하는 데 사용할 수 있습니다.

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a> CMFCRibbonStatusBarPane:: SetAlmostLargeText

상태 표시줄 창에 잘림 없이 표시할 수 있는 가장 긴 텍스트를 정의 합니다.

```cpp
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>매개 변수

*lpszAlmostLargeText*<br/>
진행 상태 표시줄 창에 잘림 없이 표시할 수 있는 가장 긴 문자열을 지정 합니다.

### <a name="remarks"></a>설명

라이브러리는 *lpszAlmostLargeText* 에서 지정 하는 텍스트의 크기를 계산 하 고 그에 따라 창 크기를 조정 합니다. 텍스트는 여전히 창에 들어가지 않을 경우 잘립니다.

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a> CMFCRibbonStatusBarPane:: Set애니메이션 목록

애니메이션에 사용할 수 있는 이미지 목록을 상태 표시줄 창에 연결 합니다.

```cpp
void SetAnimationList(
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```

### <a name="parameters"></a>매개 변수

*hBmpAnimationList*<br/>
진행 이미지 목록에 대 한 핸들을 지정 합니다.

*cxAnimation*<br/>
진행 이미지 목록에 있는 프레임의 너비를 픽셀 단위로 지정 합니다.

*clrTransp*<br/>
진행 이미지 목록의 투명 한 색을 지정 합니다.

*uiAnimationListResID*<br/>
진행 이미지 목록의 리소스 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

이미지 목록이 상태 표시줄 창에 성공적으로 연결 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a> CMFCRibbonStatusBarPane:: SetTextAlign

상태 표시줄 창 레이블의 텍스트 맞춤을 설정 합니다.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>매개 변수

*nAlign*<br/>
진행 텍스트 맞춤을 지정 합니다.

### <a name="remarks"></a>설명

*n align* 은 다음 값 중 하나를 사용할 수 있습니다.

- TA_LEFT: 왼쪽 맞춤

- TA_CENTER: 가운데 맞춤

- TA_RIGHT: 오른쪽 맞춤

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a> CMFCRibbonStatusBarPane:: StartAnimation

창에 할당 하는 애니메이션을 시작 합니다.

```cpp
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>매개 변수

*N프레임 지연*<br/>
진행 애니메이션 프레임 주기 (밀리초)를 지정 합니다.

*n 기간*<br/>
진행 애니메이션을 재생 하는 시간 (밀리초)을 지정 합니다. 무한 루프의 경우-1을 사용 합니다.

### <a name="remarks"></a>설명

를 사용 하 여를 호출 하기 전에 이미지 목록에 대 한 핸들을 지정 해야 합니다 `StartAnimation` `SetAnimationList` .

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a> CMFCRibbonStatusBarPane:: StopAnimation

상태 표시줄 창에 할당 한 애니메이션을 중지 합니다.

```cpp
void StopAnimation();
```

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 단추 클래스](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Cmfc리본 Statusbar 클래스](../../mfc/reference/cmfcribbonstatusbar-class.md)
