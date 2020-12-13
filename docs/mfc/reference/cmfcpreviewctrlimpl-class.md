---
description: '자세히 알아보기: CMFCPreviewCtrlImpl 클래스'
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
ms.openlocfilehash: 09e4b8e023a55110986aafccfd2646d8e7775c31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334736"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 클래스

이 클래스는 풍부한 미리 보기를 위해 셸에서 제공 하는 호스트 창에 배치 되는 창을 구현 합니다.

## <a name="syntax"></a>구문

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destructs 미리 보기 컨트롤 개체입니다.|
|[CMFCPreviewCtrlImpl:: CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|미리 보기 컨트롤 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCPreviewCtrlImpl:: Create](#create)|오버로드됨. Windows 창을 만들기 위해 풍부한 미리 보기 처리기에서 호출 됩니다.|
|[CMFCPreviewCtrlImpl::D estroy](#destroy)|이 컨트롤을 제거 해야 할 때 풍부한 미리 보기 처리기에서 호출 됩니다.|
|[CMFCPreviewCtrlImpl:: Focus](#focus)|이 컨트롤에 입력 포커스를 설정합니다.|
|[CMFCPreviewCtrlImpl:: GetDocument](#getdocument)|이 미리 보기 컨트롤에 연결 된 문서를 반환 합니다.|
|[CMFCPreviewCtrlImpl:: 다시 그리기](#redraw)|이 컨트롤에 다시 그리도록 지시 합니다.|
|[CMFCPreviewCtrlImpl:: SetDocument](#setdocument)|문서 구현과 미리 보기 컨트롤 간의 관계를 만들기 위해 미리 보기 처리기에서 호출 됩니다.|
|[CMFCPreviewCtrlImpl:: SetHost](#sethost)|이 컨트롤에 대 한 새 부모를 설정 합니다.|
|[CMFCPreviewCtrlImpl:: SetPreviewVisuals](#setpreviewvisuals)|풍부한 미리 보기 콘텐츠의 시각적 개체를 설정 해야 하는 경우 풍부한 미리 보기 처리기에서 호출 됩니다.|
|[CMFCPreviewCtrlImpl:: SetRect](#setrect)|이 컨트롤에 대 한 새 경계 사각형을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::D oPaint](#dopaint)|미리 보기를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCPreviewCtrlImpl:: m_clrBackColor](#m_clrbackcolor)|미리 보기 창의 배경색입니다.|
|[CMFCPreviewCtrlImpl:: m_clrTextColor](#m_clrtextcolor)|미리 보기 창의 텍스트 색입니다.|
|[CMFCPreviewCtrlImpl:: m_font](#m_font)|미리 보기 창에 텍스트를 표시 하는 데 사용 되는 글꼴입니다.|
|[CMFCPreviewCtrlImpl:: m_pDocument](#m_pdocument)|컨트롤에서 콘텐츠를 미리 볼 수 있는 문서에 대 한 포인터입니다.|

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl:: CMFCPreviewCtrlImpl

미리 보기 컨트롤 개체를 생성 합니다.

### <a name="syntax"></a>Syntax

CMFCPreviewCtrlImpl ();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a> CMFCPreviewCtrlImpl:: Create

오버로드됨. Windows 창을 만들기 위해 풍부한 미리 보기 처리기에서 호출 됩니다.

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

*hWndParent*<br/>
셸에서 리치 미리 보기에 대해 제공 하는 호스트 창에 대 한 핸들입니다.

*prc*<br/>
창의 초기 크기와 위치를 지정 합니다.

*pContext*<br/>
생성 컨텍스트에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

생성에 성공하면 TRUE이고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a> CMFCPreviewCtrlImpl::D estroy

이 컨트롤을 제거 해야 할 때 풍부한 미리 보기 처리기에서 호출 됩니다.

### <a name="syntax"></a>Syntax

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a> CMFCPreviewCtrlImpl::D oPaint

미리 보기를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

### <a name="syntax"></a>구문

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
그리기를 위한 장치 컨텍스트에 대 한 포인터입니다.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a> CMFCPreviewCtrlImpl:: Focus

이 컨트롤에 입력 포커스를 설정합니다.

### <a name="syntax"></a>Syntax

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a> CMFCPreviewCtrlImpl:: GetDocument

이 미리 보기 컨트롤에 연결 된 문서를 반환 합니다.

### <a name="syntax"></a>구문

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Return Value

컨트롤에서 콘텐츠를 미리 볼 수 있는 문서에 대 한 포인터입니다.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl:: m_clrBackColor

미리 보기 창의 배경색입니다.

### <a name="syntax"></a>Syntax

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl:: m_clrTextColor

미리 보기 창의 텍스트 색입니다.

### <a name="syntax"></a>Syntax

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a> CMFCPreviewCtrlImpl:: m_font 미리 보기 창에 텍스트를 표시 하는 데 사용 되는 글꼴입니다.

### <a name="syntax"></a>Syntax

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a> CMFCPreviewCtrlImpl:: m_pDocument

컨트롤에서 콘텐츠를 미리 볼 수 있는 문서에 대 한 포인터입니다.

### <a name="syntax"></a>Syntax

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a> CMFCPreviewCtrlImpl:: 다시 그리기

이 컨트롤에 다시 그리도록 지시 합니다.

### <a name="syntax"></a>Syntax

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a> CMFCPreviewCtrlImpl:: SetDocument

문서 구현과 미리 보기 컨트롤 간의 관계를 만들기 위해 미리 보기 처리기에서 호출 됩니다.

### <a name="syntax"></a>구문

```cpp
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>매개 변수

*pDocument*<br/>
문서 구현에 대 한 포인터입니다.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a> CMFCPreviewCtrlImpl:: SetHost

이 컨트롤에 대 한 새 부모를 설정 합니다.

### <a name="syntax"></a>구문

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
새 부모 창에 대 한 핸들입니다.

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl:: SetPreviewVisuals

풍부한 미리 보기 콘텐츠의 시각적 개체를 설정 해야 하는 경우 풍부한 미리 보기 처리기에서 호출 됩니다.

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
미리 보기 창의 배경색입니다.

*clrText*<br/>
미리 보기 창의 텍스트 색입니다.

*plf*<br/>
미리 보기 창에 텍스트를 표시 하는 데 사용 되는 글꼴입니다.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a> CMFCPreviewCtrlImpl:: SetRect

이 컨트롤에 대 한 새 경계 사각형을 설정 합니다.

### <a name="syntax"></a>구문

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>매개 변수

*prc*<br/>
미리 보기 컨트롤의 새 크기와 위치를 지정 합니다.

*bRedraw*<br/>
컨트롤을 다시 그려야 하는지 여부를 지정 합니다.

### <a name="remarks"></a>설명

일반적으로 새 경계 사각형은 호스트 컨트롤의 크기를 조정할 때 설정 됩니다.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a> CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl

Destructs 미리 보기 컨트롤 개체입니다.

### <a name="syntax"></a>구문

```
virtual ~CMFCPreviewCtrlImpl();
```
