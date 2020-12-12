---
description: '자세히 알아보기: CHtmlEditView 클래스'
title: CHtmlEditView 클래스
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 9ab998ca16a26fd4ef7a23e4dc58c6542ec330b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261322"
---
# <a name="chtmleditview-class"></a>CHtmlEditView 클래스

MFC의 문서/뷰 아키텍처 컨텍스트 내에서 WebBrowser 편집 플랫폼의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|`CHtmlEditView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHtmlEditView:: Create](#create)|새 창 개체를 만듭니다.|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|`IHTMLDocument2`현재 문서에 대 한 인터페이스를 반환 합니다.|
|[CHtmlEditView:: GetStartDocument](#getstartdocument)|이 뷰에 대 한 기본 문서의 이름을 검색 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CHtmlView](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>요구 사항

**헤더:** afxhtml.h

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a> CHtmlEditView::CHtmlEditView

`CHtmlEditView` 개체를 생성합니다.

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a> CHtmlEditView:: Create

새 창 개체를 만듭니다.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>
Windows 클래스의 이름을 나타내는 null로 끝나는 문자열을 가리킵니다. 클래스 이름은 [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) global 함수 또는 Windows 함수에 등록 된 모든 이름일 수 있습니다 `RegisterClass` . NULL 인 경우 미리 정의 된 기본 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 특성을 사용 합니다.

*lpszWindowName*<br/>
창 이름을 나타내는 null로 끝나는 문자열을 가리킵니다.

*dwStyle*<br/>
창 스타일 특성을 지정 합니다. 기본적으로 WS_VISIBLE 및 WS_CHILD Windows 스타일은 설정 되어 있습니다.

*rect*<br/>
창의 크기와 위치를 지정 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다. *RectDefault* 값을 사용 하면 창에서 새 창의 크기와 위치를 지정할 수 있습니다.

*pParentWnd*<br/>
컨트롤의 부모 창에 대 한 포인터입니다.

*nID*<br/>
뷰의 ID 번호입니다. 기본적으로 AFX_IDW_PANE_FIRST로 설정 됩니다.

*pContext*<br/>
[Ccreatecontext](../../mfc/reference/ccreatecontext-structure.md)에 대 한 포인터입니다. 기본값은 NULL입니다.

### <a name="remarks"></a>설명

또한이 메서드는 포함 된 WebBrowser의 메서드를 호출 `Navigate` 하 여 기본 문서를 로드 합니다 ( [CHtmlEditView:: GetStartDocument](#getstartdocument)참조).

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a> CHtmlEditView::GetDHtmlDocument

`IHTMLDocument2`현재 문서에 대 한 인터페이스를 반환 합니다.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>매개 변수

*ppDocument*<br/>
[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) 인터페이스입니다.

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a> CHtmlEditView:: GetStartDocument

이 뷰에 대 한 기본 문서의 이름을 검색 합니다.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>참고 항목

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
