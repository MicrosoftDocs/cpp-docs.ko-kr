---
description: '자세히 알아보기: CScrollView 클래스'
title: CScrollView 클래스
ms.date: 11/04/2016
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
ms.openlocfilehash: 76045f640cf74b650fbbf48dead7ee44c57fbd87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342906"
---
# <a name="cscrollview-class"></a>CScrollView 클래스

스크롤 기능이 있는 [CView](../../mfc/reference/cview-class.md)

## <a name="syntax"></a>구문

```
class CScrollView : public CView
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CScrollView:: CScrollView](#cscrollview)|`CScrollView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CScrollView:: CheckScrollBars](#checkscrollbars)|스크롤 보기에 가로 및 세로 스크롤 막대가 있는지 여부를 나타냅니다.|
|[CScrollView:: FillOutsideRect](#filloutsiderect)|스크롤 영역 외부에 있는 뷰의 영역을 채웁니다.|
|[CScrollView:: GetDeviceScrollPosition](#getdevicescrollposition)|장치 단위의 현재 스크롤 위치를 가져옵니다.|
|[CScrollView:: GetDeviceScrollSizes](#getdevicescrollsizes)|스크롤 가능한 뷰의 현재 매핑 모드, 전체 크기 및 줄 및 페이지 크기를 가져옵니다. 크기는 장치 단위입니다.|
|[CScrollView:: GetScrollPosition](#getscrollposition)|논리 단위의 현재 스크롤 위치를 가져옵니다.|
|[CScrollView:: GetTotalSize](#gettotalsize)|스크롤 뷰의 전체 크기 (논리 단위)를 가져옵니다.|
|[CScrollView:: ResizeParentToFit](#resizeparenttofit)|뷰의 크기를 조정 하 여 프레임의 크기를 지시 합니다.|
|[CScrollView:: ScrollToPosition](#scrolltoposition)|논리 단위로 지정 된 지정 된 지점으로 뷰를 스크롤합니다.|
|[CScrollView:: SetScaleToFitSize](#setscaletofitsize)|스크롤 뷰를 배율 조정 모드로 전환 합니다.|
|[CScrollView:: SetScrollSizes](#setscrollsizes)|스크롤 뷰의 매핑 모드, 전체 크기 및 가로 및 세로 스크롤 크기를 설정 합니다.|

## <a name="remarks"></a>설명

`CView`메시지 매핑된 [onhscroll](../../mfc/reference/cwnd-class.md#onhscroll) 및 [onhscroll](../../mfc/reference/cwnd-class.md#onvscroll) 멤버 함수를 재정의 하 여에서 파생 된 클래스에서 직접 표준 스크롤을 처리할 수 있습니다. 는 `CScrollView` 다음과 같은 기능을 해당 기능에 추가 합니다 `CView` .

- 창 및 뷰포트 크기와 매핑 모드를 관리 합니다.

- 스크롤 막대 메시지에 응답 하 여 자동으로 스크롤됩니다.

- 키보드의 메시지에 대 한 응답으로 자동으로 스크롤됩니다. 스크롤 하지 않는 마우스나 IntelliMouse 휠입니다.

키보드의 메시지에 대 한 응답으로 자동으로 스크롤하려면 WM_KEYDOWN 메시지를 추가 하 고 VK_DOWN VK_PREV를 테스트 하 고 [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos)를 호출 합니다.

메시지 매핑된 [Onmousewheel](../../mfc/reference/cwnd-class.md#onmousewheel) 및 [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) 멤버 함수를 재정의 하 여 마우스 휠 스크롤을 직접 처리할 수 있습니다. 이러한 멤버 함수는에 대 한 것 처럼 `CScrollView` 휠 회전 메시지 [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel)에 대해 권장 되는 동작을 지원 합니다.

자동 스크롤 기능을 활용 하려면 대신에서 뷰 클래스를 파생 시킵니다 `CScrollView` `CView` . 뷰를 처음 만들 때 문서 크기에 따라 스크롤할 수 있는 뷰의 크기를 계산 하려면 `SetScrollSizes` [cview:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) 또는 [cview:: OnUpdate](../../mfc/reference/cview-class.md#onupdate)의 재정의에서 멤버 함수를 호출 합니다. (문서 크기를 쿼리하려면 사용자 고유의 코드를 작성 해야 합니다. 예제를 보려면 [Scribble 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

멤버 함수에 대 한 호출은 `SetScrollSizes` 뷰의 매핑 모드, 스크롤 뷰의 전체 크기 및 가로 및 세로로 스크롤할 크기를 설정 합니다. 모든 크기는 논리적 단위입니다. 뷰의 논리적 크기는 일반적으로 문서에 저장 된 데이터에서 계산 되지만 경우에 따라 고정 크기를 지정할 수 있습니다. 두 방법의 예제는 [CScrollView:: SetScrollSizes](#setscrollsizes)를 참조 하세요.

논리적 단위에서 가로 및 세로 방향으로 스크롤할 크기를 지정 합니다. 기본적으로 사용자가 스크롤 상자 외부에서 스크롤 막대 샤프트를 클릭 하면 `CScrollView` "페이지"를 스크롤합니다. 사용자가 스크롤 막대의 한쪽 끝에 있는 스크롤 화살표를 클릭 하면 `CScrollView` "줄"을 스크롤합니다. 기본적으로 페이지의 총 크기는 1/10입니다. 줄은 페이지 크기의 1/10입니다. 멤버 함수에서 사용자 지정 크기를 전달 하 여 이러한 기본값을 재정의 `SetScrollSizes` 합니다. 예를 들어 가로 크기를 전체 크기의 너비와 세로 크기를 현재 글꼴의 줄 높이로 설정할 수 있습니다.

스크롤 하는 대신에서 `CScrollView` 뷰를 현재 창 크기로 자동으로 조정할 수 있습니다. 이 모드에서 뷰는 스크롤 막대를 포함 하지 않으며 논리적 보기가 창의 클라이언트 영역에 정확히 맞게 확대 또는 축소 됩니다. 이 크기 조정 기능을 사용 하려면 [CScrollView:: SetScaleToFitSize](#setscaletofitsize)를 호출 합니다. 또는 중 하나만 `SetScaleToFitSize` 호출 `SetScrollSizes` 합니다.

파생 된 `OnDraw` 뷰 클래스의 멤버 함수를 호출 하기 전에은 `CScrollView` `CPaintDC` 전달 되는 장치 컨텍스트 개체의 뷰포트 원본을 자동으로 조정 `OnDraw` 합니다.

스크롤 창에 대 한 뷰포트 원본을 조정 하기 위해 `CScrollView` 는 [CView:: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)를 재정의 합니다. 이 조정은 `CPaintDC` 에 전달 되는 장치 컨텍스트에 대해 자동 `CScrollView` `OnDraw` 이지만 `CScrollView::OnPrepareDC` 와 같이 사용 하는 다른 장치 컨텍스트를 위해 직접 호출 해야 합니다 `CClientDC` . 를 재정의 `CScrollView::OnPrepareDC` 하 여 펜, 배경색 및 기타 그리기 특성을 설정할 수 있지만, 기본 클래스를 호출 하 여 크기 조정을 수행할 수 있습니다.

스크롤 막대는 다음과 같은 경우에 표시 된 것 처럼 보기에 상대적인 세 위치에 표시 될 수 있습니다.

- WS_HSCROLL 및 WS_VSCROLL[Windows 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 사용 하 여 뷰에 대 한 표준 창 스타일 스크롤 막대를 설정할 수 있습니다.

- 스크롤 막대 컨트롤은 뷰가 포함 된 프레임에 추가 될 수도 있습니다 .이 경우 프레임 워크는 WM_HSCROLL를 전달 하 고 프레임 창에서 현재 활성 뷰로 메시지 WM_VSCROLL 메시지를 전달 합니다.

- 프레임 워크는 또한 `CSplitterWnd` splitter 컨트롤에서 현재 활성 분할자 창 (뷰)으로 스크롤 메시지를 전달 합니다. 공유 스크롤 막대가 있는 [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) 에 배치 되 면 개체는 `CScrollView` 자체를 만드는 대신 공유 된 스크롤 막대가 사용 됩니다.

사용에 대 한 자세한 내용은 `CScrollView` [MFC에서 사용할 수 있는](../../mfc/derived-view-classes-available-in-mfc.md) [문서/뷰 아키텍처](../../mfc/document-view-architecture.md) 및 파생 뷰 클래스를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a> CScrollView:: CheckScrollBars

스크롤 뷰에 가로 및 세로 막대가 있는지 확인 하려면이 멤버 함수를 호출 합니다.

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>매개 변수

*bHasHorzBar*<br/>
응용 프로그램에 가로 스크롤 막대가 있음을 나타냅니다.

*bHasVertBar*<br/>
응용 프로그램에 세로 스크롤 막대가 있음을 나타냅니다.

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a> CScrollView:: CScrollView

`CScrollView` 개체를 생성합니다.

```
CScrollView();
```

### <a name="remarks"></a>설명

`SetScrollSizes`스크롤 뷰를 사용 하려면 또는 중 하나를 호출 해야 합니다 `SetScaleToFitSize` .

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a> CScrollView:: FillOutsideRect

`FillOutsideRect`을 호출 하 여 스크롤 영역 외부에 나타나는 뷰의 영역을 채웁니다.

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
채우기를 수행할 장치 컨텍스트입니다.

*pBrush*<br/>
영역을 채울 브러시입니다.

### <a name="remarks"></a>설명

`FillOutsideRect`스크롤 뷰의 `OnEraseBkgnd` 처리기 함수에서를 사용 하 여 과도 한 배경 다시 그리기를 방지 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a> CScrollView:: GetDeviceScrollPosition

`GetDeviceScrollPosition`스크롤 막대에서 스크롤 상자의 현재 가로 및 세로 위치가 필요한 경우를 호출 합니다.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>반환 값

개체에 해당 하는 스크롤 상자의 가로 및 세로 위치 (장치 단위)입니다 `CPoint` .

### <a name="remarks"></a>설명

이 좌표 쌍은 뷰의 왼쪽 위 모퉁이가 스크롤되는 문서의 위치에 해당 합니다. 이는 마우스 장치 위치를 스크롤 보기 장치 위치로 오프셋 하는 데 유용 합니다.

`GetDeviceScrollPosition` 장치 단위의 값을 반환 합니다. 논리 단위를 사용 하려면 대신를 사용 `GetScrollPosition` 합니다.

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a> CScrollView:: GetDeviceScrollSizes

`GetDeviceScrollSizes` 스크롤 가능한 뷰의 현재 매핑 모드, 전체 크기 및 줄 및 페이지 크기를 가져옵니다.

```cpp
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>매개 변수

*nMapMode*<br/>
이 뷰의 현재 매핑 모드를 반환 합니다. 사용 가능한 값 목록을 보려면 `SetScrollSizes`을 참조하십시오.

*sizeTotal*<br/>
장치 단위에서 스크롤 뷰의 현재 총 크기를 반환 합니다.

*sizePage*<br/>
스크롤 막대 샤프트에서 마우스 클릭에 대 한 응답으로 각 방향으로 스크롤할 현재 가로 및 세로 크기를 반환 합니다. `cx`멤버는 가로 크기를 포함 합니다. `cy`멤버는 세로 크기를 포함 합니다.

*sizeLine*<br/>
스크롤 화살표에서 마우스 클릭에 대 한 응답으로 각 방향으로 스크롤할 현재 가로 및 세로 크기를 반환 합니다. `cx`멤버는 가로 크기를 포함 합니다. `cy`멤버는 세로 크기를 포함 합니다.

### <a name="remarks"></a>설명

크기는 장치 단위입니다. 이 멤버 함수는 거의 호출 되지 않습니다.

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a> CScrollView:: GetScrollPosition

`GetScrollPosition`스크롤 막대에서 스크롤 상자의 현재 가로 및 세로 위치가 필요한 경우를 호출 합니다.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>반환 값

개체에 해당 하는 스크롤 상자의 가로 및 세로 위치 (논리 단위)입니다 `CPoint` .

### <a name="remarks"></a>설명

이 좌표 쌍은 뷰의 왼쪽 위 모퉁이가 스크롤되는 문서의 위치에 해당 합니다.

`GetScrollPosition` 논리 단위로 값을 반환 합니다. 장치 단위를 사용 하려면 대신을 사용 `GetDeviceScrollPosition` 합니다.

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a> CScrollView:: GetTotalSize

`GetTotalSize`을 호출 하 여 스크롤 뷰의 현재 가로 및 세로 크기를 검색 합니다.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>반환 값

논리 단위로 표시 되는 스크롤 뷰의 전체 크기입니다. 가로 크기는 `cx` 반환 값의 멤버에 `CSize` 있습니다. 세로 크기는 `cy` 멤버입니다.

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a> CScrollView:: ResizeParentToFit

`ResizeParentToFit`를 호출 하 여 뷰의 크기가 프레임 창의 크기를 받아쓸 수 있도록 합니다.

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>매개 변수

*bShrinkOnly*<br/>
수행할 크기 조정의 종류입니다. 기본값인 TRUE 이면 프레임 창이 축소 됩니다 (해당 하는 경우). 스크롤 막대는 크게 보기 또는 작은 프레임 창에 계속 표시 됩니다. FALSE 값을 설정 하면 뷰는 항상 프레임 창의 크기를 정확 하 게 조정 합니다. 이는 프레임 창이 MDI (다중 문서 인터페이스) 프레임 창이 나 화면에 맞게 너무 커질 수 있으므로 약간 위험할 수 있습니다.

### <a name="remarks"></a>설명

MDI 자식 프레임 창의 뷰에서만 권장 됩니다. `ResizeParentToFit` `OnInitialUpdate` 파생 클래스의 처리기 함수에서를 사용 `CScrollView` 합니다. 이 멤버 함수에 대 한 예제는 [CScrollView:: SetScrollSizes](#setscrollsizes)를 참조 하세요.

`ResizeParentToFit` 보기 창의 크기가 설정 된 것으로 가정 합니다. 가 호출 될 때 보기 창 크기가 설정 되지 않은 경우에는 `ResizeParentToFit` 어설션이 발생 합니다. 이 문제가 발생 하지 않도록 하려면를 호출 하기 전에 다음을 호출 합니다 `ResizeParentToFit` .

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a> CScrollView:: ScrollToPosition

`ScrollToPosition`를 호출 하 여 뷰의 지정 된 지점으로 스크롤합니다.

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
논리 단위로 스크롤할 점입니다. `x`멤버는 0 보다 크거나 같고 뷰의 전체 크기에 해당 하는 양수 값 이어야 합니다. `y`매핑 모드가 MM_TEXT 경우에도 마찬가지입니다. `y`멤버가 MM_TEXT 아닌 매핑 모드에서 음수입니다.

### <a name="remarks"></a>설명

이 점이 창의 왼쪽 위 모퉁이에 오도록 뷰가 스크롤됩니다. 뷰가 크기에 맞게 조정 되는 경우이 멤버 함수를 호출 하면 안 됩니다.

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a> CScrollView:: SetScaleToFitSize

`SetScaleToFitSize`뷰포트 크기를 현재 창 크기에 맞게 자동으로 조정 하려는 경우를 호출 합니다.

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>매개 변수

*sizeTotal*<br/>
뷰의 크기를 조정할 가로 및 세로 크기입니다. 스크롤 뷰의 크기는 논리 단위로 측정 됩니다. 가로 크기는 멤버에 포함 되어 `cx` 있습니다. 세로 크기는 멤버에 포함 되어 `cy` 있습니다. 및 둘 다 `cx` `cy` 0 보다 크거나 같아야 합니다.

### <a name="remarks"></a>설명

스크롤 막대를 사용 하면 언제 든 지 논리 뷰의 일부만 표시 될 수 있습니다. 그러나 크기 조정 기능을 사용 하는 경우 보기에 스크롤 막대가 없고 논리적 보기가 창의 클라이언트 영역에 정확히 맞게 확대 또는 축소 됩니다. 창의 크기를 조정 하면 뷰는 창의 크기에 따라 새 크기로 데이터를 그립니다.

일반적으로에 대 한 호출을 `SetScaleToFitSize` 뷰의 멤버 함수 재정의에 추가 `OnInitialUpdate` 합니다. 자동 크기 조정을 원하지 않는 경우 `SetScrollSizes` 대신 멤버 함수를 호출 합니다.

`SetScaleToFitSize` "크기에 맞게 확대" 작업을 구현 하는 데 사용할 수 있습니다. `SetScrollSizes`스크롤을 다시 초기화 하는 데 사용 합니다.

`SetScaleToFitSize` 보기 창의 크기가 설정 된 것으로 가정 합니다. 가 호출 될 때 보기 창 크기가 설정 되지 않은 경우에는 `SetScaleToFitSize` 어설션이 발생 합니다. 이 문제가 발생 하지 않도록 하려면를 호출 하기 전에 다음을 호출 합니다 `SetScaleToFitSize` .

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a> CScrollView:: SetScrollSizes

`SetScrollSizes`뷰가 업데이트 될 때 호출 됩니다.

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>매개 변수

*nMapMode*<br/>
이 뷰에 대해 설정할 매핑 모드입니다. 가능한 값은 다음과 같습니다.

|매핑 모드|논리 단위|Y 축 양의 확장 ...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 픽셀|방향|
|MM_HIMETRIC|0.01 mm|위나|
|MM_TWIPS|1/1440 in|위나|
|MM_HIENGLISH|0.001 in|위나|
|MM_LOMETRIC|0.1 mm|위나|
|MM_LOENGLISH|0.01 in|위나|

이러한 모드는 모두 Windows에서 정의 됩니다. 에는 두 개의 표준 매핑 모드 MM_ISOTROPIC 및 MM_ANISOTROPIC가 사용 되지 않습니다 `CScrollView` . 클래스 라이브러리는 뷰를 `SetScaleToFitSize` 창 크기로 확장 하기 위한 멤버 함수를 제공 합니다. 위의 표에서 열 3은 좌표 방향에 대해 설명 합니다.

*sizeTotal*<br/>
스크롤 뷰의 전체 크기입니다. `cx`멤버는 가로 범위를 포함 합니다. `cy`멤버에 세로 범위가 포함 되어 있습니다. 크기는 논리적 단위입니다. 및 둘 다 `cx` `cy` 0 보다 크거나 같아야 합니다.

*sizePage*<br/>
스크롤 막대 샤프트에서 마우스 클릭에 대 한 응답으로 각 방향으로 스크롤할 가로 및 세로 거리입니다. `cx`멤버는 가로 크기를 포함 합니다. `cy`멤버는 세로 크기를 포함 합니다.

*sizeLine*<br/>
스크롤 화살표를 마우스 클릭에 대 한 응답으로 각 방향으로 스크롤할 가로 및 세로 거리입니다. `cx`멤버는 가로 크기를 포함 합니다. `cy`멤버는 세로 크기를 포함 합니다.

### <a name="remarks"></a>설명

예를 들어 문서를 처음에 `OnUpdate` 표시 하거나 크기를 변경할 때 스크롤 특성을 조정 하기 위해 멤버 함수 재정의에서 호출 합니다.

일반적으로 `GetMyDocSize` 파생 문서 클래스와 함께 제공 되는 문서 멤버 함수를 호출 하 여 뷰의 연결 된 문서에서 크기 정보를 가져옵니다. 다음 코드에서는이 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

또는 다음 코드와 같이 고정 크기를 설정 해야 하는 경우도 있습니다.

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

매핑 모드는 MM_ISOTROPIC 또는 MM_ANISOTROPIC를 제외 하 고 Windows 매핑 모드를 설정 해야 합니다. 제한 되지 않은 매핑 모드를 사용 하려는 경우 `SetScaleToFitSize` 대신 멤버 함수를 호출 `SetScrollSizes` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd 클래스](../../mfc/reference/csplitterwnd-class.md)
