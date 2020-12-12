---
description: '자세한 정보: Cmfc리본 Linkctrl 클래스'
title: Cmfc리본 Linkctrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 19b10643fa1af25dae4a5dc888f61d1c9ecaaee7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321789"
---
# <a name="cmfcribbonlinkctrl-class"></a>Cmfc리본 Linkctrl 클래스

리본에 배치되는 하이퍼링크를 구현합니다. 하이퍼링크를 클릭하면 웹 페이지가 열립니다.
자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|`CMFCRibbonLinkCtrl` 개체를 생성하고 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|( `CMFCRibbonButton::CopyFrom`을 재정의합니다.)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|[Cmfc리본 단추:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)를 재정의 합니다.|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|하이퍼링크의 값을 반환합니다.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|[Cmfc리본 단추:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)를 재정의 합니다.|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|[Cmfc리본 단추:: GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)를 재정의 합니다.|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|( `CMFCRibbonButton::IsDrawTooltipImage`을 재정의합니다.)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|[Cmfc리본 단추:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)를 재정의 합니다.|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|[Cmfc리본 Baseelement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)를 재정의 합니다.|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|( `CMFCRibbonButton::OnMouseMove`을 재정의합니다.)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|하이퍼링크에 지정된 웹 페이지를 엽니다.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|하이퍼링크의 값을 설정합니다.|

## <a name="remarks"></a>설명

하이퍼링크를 만든 후 [Cmfc리본 패널:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)를 호출 하 여 패널에 추가 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [Cmfc리본 baseelement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Cmfc리본 단추](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Cmfc리본 링크 ctrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxRibbonLinkCtrl

## <a name="cmfcribbonlinkctrlcmfcribbonlinkctrl"></a><a name="cmfcribbonlinkctrl"></a> Cmfc리본 Linkctrl:: Cmfc리본 링크 Ctrl

[Cmfc리본 Linkctrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) 개체를 생성 하 고 초기화 합니다.

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 링크 컨트롤을 클릭할 때 실행 되는 명령의 명령 ID를 지정 합니다.

*lpszText*<br/>
진행 링크 컨트롤에 표시할 레이블을 지정 합니다.

*lpszLink*<br/>
진행 링크 컨트롤과 연결 된 하이퍼링크를 지정 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 생성자를 사용 하는 방법을 보여 줍니다 `CMFCRibbonLinkCtrl` . 이 코드 조각은 [리본 가젯 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

## <a name="cmfcribbonlinkctrlcopyfrom"></a><a name="copyfrom"></a> Cmfc리본 Linkctrl:: CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>매개 변수

진행 *src*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlgetcompactsize"></a><a name="getcompactsize"></a> Cmfc리본 Linkctrl:: GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlgetlink"></a><a name="getlink"></a> Cmfc리본 Linkctrl:: GetLink

하이퍼링크의 값을 반환합니다.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>반환 값

하이퍼링크의 현재 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlgetregularsize"></a><a name="getregularsize"></a> Cmfc리본 Linkctrl:: GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlgettooltiptext"></a><a name="gettooltiptext"></a> Cmfc리본 Linkctrl:: GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlondrawmenuimage"></a><a name="ondrawmenuimage"></a> Cmfc리본 Linkctrl:: OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>매개 변수

진행 *CDC&#42;*<br/>
진행 *Crect*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a> Cmfc리본 Linkctrl:: IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlondraw"></a><a name="ondraw"></a> Cmfc리본 Linkctrl:: OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlonmousemove"></a><a name="onmousemove"></a> Cmfc리본 Linkctrl:: OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>매개 변수

진행 *point*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlonseticon"></a><a name="onseticon"></a> Cmfc리본 Linkctrl:: OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>설명

## <a name="cmfcribbonlinkctrlopenlink"></a><a name="openlink"></a> Cmfc리본 Linkctrl:: OpenLink

하이퍼링크에 지정된 웹 페이지를 엽니다.

```
BOOL OpenLink();
```

### <a name="return-value"></a>반환 값

연결 된 웹 페이지가 성공적으로 열리면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

개체와 연결 된 하이퍼링크를 사용 하 여 웹 페이지를 엽니다 `CMFCRibbonLinkCtrl` .

## <a name="cmfcribbonlinkctrlsetlink"></a><a name="setlink"></a> Cmfc리본 Linkctrl:: SetLink

하이퍼링크의 값을 설정합니다.

```cpp
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>매개 변수

*lpszLink*<br/>
진행 하이퍼링크 텍스트를 지정 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 단추 클래스](../../mfc/reference/cmfcribbonbutton-class.md)
