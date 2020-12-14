---
description: '자세히 알아보기: COleIPFrameWnd 클래스'
title: COleIPFrameWnd 클래스
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: d89cfa9b3f6d610276c3c972ee48c943f753e36a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227015"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd 클래스

애플리케이션의 내부 편집 창의 기준입니다.

## <a name="syntax"></a>구문

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleIPFrameWnd:: COleIPFrameWnd](#coleipframewnd)|`COleIPFrameWnd` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleIPFrameWnd:: OnCreateControlBars](#oncreatecontrolbars)|내부 편집을 위해 항목이 활성화 될 때 프레임 워크에서 호출 됩니다.|
|[COleIPFrameWnd:: RepositionFrame](#repositionframe)|내부 편집 창의 위치를 변경 하기 위해 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

이 클래스는 컨테이너 응용 프로그램의 문서 창에 컨트롤 막대를 만들고 배치 합니다. 또한 사용자가 내부 편집 창의 크기를 조정할 때 포함 된 [COleResizeBar](../../mfc/reference/coleresizebar-class.md) 개체에 의해 생성 된 알림도 처리 합니다.

사용에 대 한 자세한 내용은 `COleIPFrameWnd` [활성화](../../mfc/activation-cpp.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a> COleIPFrameWnd:: COleIPFrameWnd

개체를 생성 `COleIPFrameWnd` 하 고 OLEINPLACEFRAMEINFO 형식의 구조에 저장 되는 내부 상태 정보를 초기화 합니다.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK에서 [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) 을 참조 하세요.

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a> COleIPFrameWnd:: OnCreateControlBars

`OnCreateControlBars`항목이 내부 편집을 위해 활성화 된 경우 프레임 워크는 함수를 호출 합니다.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>매개 변수

*pWndFrame*<br/>
컨테이너 응용 프로그램의 프레임 창에 대 한 포인터입니다.

*pWndDoc*<br/>
컨테이너의 문서 수준 창에 대 한 포인터입니다. 컨테이너가 SDI 응용 프로그램 일 경우 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

성공 시 0이 아닌 경우 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 구현은 아무 작업도 수행하지 않습니다. 컨트롤 막대를 만들 때 필요한 특별 한 처리 작업을 수행 하려면이 함수를 재정의 합니다.

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a> COleIPFrameWnd:: RepositionFrame

프레임 워크는 `RepositionFrame` 멤버 함수를 호출 하 여 컨트롤 막대를 배치 하 고 내부 편집 창의 위치를 변경 하 여 모든 컨트롤이 표시 되도록 합니다.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>매개 변수

*lpPosRect*<br/>
`RECT` `CRect` 클라이언트 영역을 기준으로 하는 내부 프레임 창의 현재 위치 좌표 (픽셀)를 포함 하는 구조체 또는 개체에 대 한 포인터입니다.

*lpClipRect*<br/>
`RECT` `CRect` 클라이언트 영역을 기준으로 하는 내부 프레임 창의 현재 클리핑 사각형 좌표 (픽셀)를 포함 하는 구조체 또는 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

컨테이너 창에서 컨트롤 막대의 레이아웃은 비 OLE 프레임 창에서 수행 하는 것과 다릅니다. 비 OLE 프레임 창에서는 [CFrameWnd:: RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)를 호출 하는 것 처럼 지정 된 프레임 창 크기에서 컨트롤 막대와 기타 개체의 위치를 계산 합니다. 클라이언트 영역은 컨트롤 막대에 대 한 공간 이후에 남아 있는 개체를 뺀 것입니다. 반면에 `COleIPFrameWnd` 창은 지정 된 클라이언트 영역에 따라 도구 모음을 배치 합니다. 즉,는 "의 외부에서" 실행 되 `CFrameWnd::RecalcLayout` 는 반면 " `COleIPFrameWnd::RepositionFrame` 는 내부에서"로 작동 합니다. "

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)
