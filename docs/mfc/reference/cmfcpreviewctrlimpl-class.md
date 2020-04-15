---
title: CMFCPreviewCtrlImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
ms.openlocfilehash: 060e601901fa5725d7ca62f244f66784af3dc11d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375332"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 클래스

이 클래스는 [리치 미리 보기용 셸]에서 제공하는 호스트 창에 배치되는 창을 구현합니다.

## <a name="syntax"></a>구문

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|[CMFC프리뷰CtrlImpl:::~CMFC프리뷰CtrlImpl](#dtor)|미리 보기 컨트롤 개체를 소멸합니다.|
|[CMFC 프리뷰CtrlImpl:::CMFC 프리뷰CtrlImpl](#cmfcpreviewctrlimpl)|미리 보기 컨트롤 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[CMFC프리뷰CtrlImpl::만들기](#create)|오버로드되었습니다. 리치 미리 보기 처리기에 의해 호출되어 Windows 창을 만듭니다.|
|[CMFC프리뷰CtrlImpl::D에스트로이](#destroy)|이 컨트롤을 삭제해야 할 때 리치 미리 보기 처리기에 의해 호출됩니다.|
|[CMFC프리뷰CtrlImpl::초점](#focus)|이 컨트롤에 입력 포커스를 설정합니다.|
|[CMFC프리뷰CtrlImpl::GetDocument](#getdocument)|이 미리 보기 컨트롤에 연결된 문서를 반환합니다.|
|[CMFC프리뷰CtrlImpl::다시 그리기](#redraw)|이 컨트롤을 다시 그리도록 지시합니다.|
|[CMFC프리뷰CtrlImpl:::세트문서](#setdocument)|미리 보기 처리기에서 호출하여 문서 구현과 미리 보기 컨트롤 간의 관계를 만듭니다.|
|[CMFC 프리뷰CtrlImpl:::세트호스트](#sethost)|이 컨트롤에 대한 새 부모를 설정합니다.|
|[CMFC프리뷰CtrlImpl:::세트프리뷰비주얼](#setpreviewvisuals)|리치 미리 보기 콘텐츠의 시각적 개체를 설정해야 하는 경우 리치 미리 보기 처리기에 의해 호출됩니다.|
|[CMFC프리뷰CtrlImpl:::세트렉트](#setrect)|이 컨트롤에 대한 새 경계 사각형을 설정합니다.|

### <a name="protected-methods"></a>Protected 메서드

|속성|Description|
|----------|-----------------|
|[CMFC프리뷰CtrlImpl::Do페인트](#dopaint)|미리 보기를 렌더링하는 프레임워크에서 호출됩니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|속성|Description|
|----------|-----------------|
|[CMFC프리뷰CtrlImpl::m_clrBackColor](#m_clrbackcolor)|미리 보기 창의 배경 색입니다.|
|[CMFC프리뷰CtrlImpl::m_clrTextColor](#m_clrtextcolor)|미리 보기 창의 텍스트 색상입니다.|
|[CMFC프리뷰CtrlImpl::m_font](#m_font)|미리 보기 창에 텍스트를 표시하는 데 사용되는 글꼴입니다.|
|[CMFC프리뷰CtrlImpl::m_pDocument](#m_pdocument)|컨트롤에서 콘텐츠를 미리 볼 수 있는 문서에 대한 포인터입니다.|

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFC 프리뷰CtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFC 프리뷰CtrlImpl:::CMFC 프리뷰CtrlImpl

미리 보기 컨트롤 개체를 생성합니다.

### <a name="syntax"></a>구문

CMFC프리뷰CtrlImpl();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFC프리뷰CtrlImpl::만들기

오버로드되었습니다. 리치 미리 보기 처리기에 의해 호출되어 Windows 창을 만듭니다.

### <a name="syntax"></a>구문

```
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc
);
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc,
   CCreateContext* pContext
);
```

### <a name="parameters"></a>매개 변수

*hWnd부모*<br/>
리치 미리 보기에 대해 셸에서 제공하는 호스트 창에 대한 핸들입니다.

*Prc*<br/>
창의 초기 크기와 위치를 지정합니다.

*pContext*<br/>
생성 컨텍스트에 대한 포인터입니다.

### <a name="return-value"></a>Return Value

생성에 성공하면 TRUE이고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFC프리뷰CtrlImpl::D에스트로이

이 컨트롤을 삭제해야 할 때 리치 미리 보기 처리기에 의해 호출됩니다.

### <a name="syntax"></a>구문

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFC프리뷰CtrlImpl::Do페인트

미리 보기를 렌더링하는 프레임워크에서 호출됩니다.

### <a name="syntax"></a>구문

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>매개 변수

*pDC*<br/>
페인팅을 위한 장치 컨텍스트에 대한 포인터입니다.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFC프리뷰CtrlImpl::초점

이 컨트롤에 입력 포커스를 설정합니다.

### <a name="syntax"></a>구문

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFC프리뷰CtrlImpl::GetDocument

이 미리 보기 컨트롤에 연결된 문서를 반환합니다.

### <a name="syntax"></a>구문

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Return Value

컨트롤에서 콘텐츠를 미리 볼 수 있는 문서에 대한 포인터입니다.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFC프리뷰CtrlImpl::m_clrBackColor

미리 보기 창의 배경 색입니다.

### <a name="syntax"></a>구문

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFC프리뷰CtrlImpl::m_clrTextColor

미리 보기 창의 텍스트 색상입니다.

### <a name="syntax"></a>구문

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFCPreviewCtrlImpl::m_font 글꼴은 미리 보기 창에 텍스트를 표시하는 데 사용됩니다.

### <a name="syntax"></a>구문

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFC프리뷰CtrlImpl::m_pDocument

컨트롤에서 콘텐츠를 미리 볼 수 있는 문서에 대한 포인터입니다.

### <a name="syntax"></a>구문

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFC프리뷰CtrlImpl::다시 그리기

이 컨트롤을 다시 그리도록 지시합니다.

### <a name="syntax"></a>구문

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFC프리뷰CtrlImpl:::세트문서

미리 보기 처리기에서 호출하여 문서 구현과 미리 보기 컨트롤 간의 관계를 만듭니다.

### <a name="syntax"></a>구문

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>매개 변수

*p문서*<br/>
문서 구현에 대한 포인터입니다.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFC 프리뷰CtrlImpl:::세트호스트

이 컨트롤에 대한 새 부모를 설정합니다.

### <a name="syntax"></a>구문

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>매개 변수

*hWnd부모*<br/>
새 상위 창에 대한 핸들입니다.

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFC프리뷰CtrlImpl:::세트프리뷰비주얼

리치 미리 보기 콘텐츠의 시각적 개체를 설정해야 하는 경우 리치 미리 보기 처리기에 의해 호출됩니다.

### <a name="syntax"></a>구문

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>매개 변수

*clrBack*<br/>
미리 보기 창의 배경 색입니다.

*clrText*<br/>
미리 보기 창의 텍스트 색상입니다.

*Plf*<br/>
미리 보기 창에 텍스트를 표시하는 데 사용되는 글꼴입니다.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFC프리뷰CtrlImpl:::세트렉트

이 컨트롤에 대한 새 경계 사각형을 설정합니다.

### <a name="syntax"></a>구문

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>매개 변수

*Prc*<br/>
미리 보기 컨트롤의 새 크기와 위치를 지정합니다.

*bRedraw*<br/>
컨트롤을 다시 그려야 하는지 여부를 지정합니다.

### <a name="remarks"></a>설명

일반적으로 호스트 컨트롤의 크기를 조정하면 새 경계 사각형이 설정됩니다.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFC프리뷰CtrlImpl:::~CMFC프리뷰CtrlImpl

미리 보기 컨트롤 개체를 소멸합니다.

### <a name="syntax"></a>구문

```
virtual ~CMFCPreviewCtrlImpl();
```
