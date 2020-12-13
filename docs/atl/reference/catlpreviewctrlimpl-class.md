---
description: '자세히 알아보기: CAtlPreviewCtrlImpl 클래스'
title: CAtlPreviewCtrlImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: 52263a4c65af1b791ca5da64eff235e93006ab52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147214"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl 클래스

이 클래스는 풍부한 미리 보기를 위해 셸에서 제공 하는 호스트 창에 배치 되는 창의 ATL 구현입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destructs 미리 보기 컨트롤 개체입니다.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|미리 보기 컨트롤 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: Create](#create)|Windows 창을 만들기 위해 풍부한 미리 보기 처리기에서 호출 됩니다.|
|[CAtlPreviewCtrlImpl::D estroy](#destroy)|이 컨트롤을 제거 해야 할 때 풍부한 미리 보기 처리기에서 호출 됩니다.|
|[CAtlPreviewCtrlImpl:: Focus](#focus)|이 컨트롤에 입력 포커스를 설정합니다.|
|[CAtlPreviewCtrlImpl:: OnPaint](#onpaint)|WM_PAINT 메시지를 처리 합니다.|
|[CAtlPreviewCtrlImpl:: 다시 그리기](#redraw)|이 컨트롤에 다시 그리도록 지시 합니다.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|이 컨트롤에 대 한 새 부모를 설정 합니다.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|풍부한 미리 보기 콘텐츠의 시각적 개체를 설정 해야 하는 경우 풍부한 미리 보기 처리기에서 호출 됩니다.|
|[CAtlPreviewCtrlImpl:: SetRect](#setrect)|이 컨트롤에 대 한 새 경계 사각형을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::D oPaint](#dopaint)|미리 보기를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.|

### <a name="protected-constants"></a>Protected 상수

|Name|설명|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: m_plf](#m_plf)|미리 보기 창에 텍스트를 표시 하는 데 사용 되는 글꼴입니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: m_clrBack](#m_clrback)|미리 보기 창의 배경색입니다.|
|[CAtlPreviewCtrlImpl:: m_clrText](#m_clrtext)|미리 보기 창의 텍스트 색입니다.|

## <a name="remarks"></a>설명

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL:: CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>요구 사항

**헤더:** atlpreviewctrlimpl

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a> CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

미리 보기 컨트롤 개체를 생성 합니다.

```cpp
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a> CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl

Destructs 미리 보기 컨트롤 개체입니다.

```cpp
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a> CAtlPreviewCtrlImpl:: Create

Windows 창을 만들기 위해 풍부한 미리 보기 처리기에서 호출 됩니다.

```cpp
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
셸에서 리치 미리 보기에 대해 제공 하는 호스트 창에 대 한 핸들입니다.

*prc*<br/>
창의 초기 크기와 위치를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a> CAtlPreviewCtrlImpl::D estroy

이 컨트롤을 제거 해야 할 때 풍부한 미리 보기 처리기에서 호출 됩니다.

```cpp
virtual void Destroy();
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a> CAtlPreviewCtrlImpl::D oPaint

미리 보기를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

```cpp
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>매개 변수

*hdc*<br/>
그리기를 위한 장치 컨텍스트에 대 한 핸들입니다.

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a> CAtlPreviewCtrlImpl:: Focus

이 컨트롤에 입력 포커스를 설정합니다.

```cpp
virtual void Focus();
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a> CAtlPreviewCtrlImpl:: m_clrBack

미리 보기 창의 배경색입니다.

```cpp
COLORREF m_clrBack;
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a> CAtlPreviewCtrlImpl:: m_clrText

미리 보기 창의 텍스트 색입니다.

```cpp
COLORREF m_clrText;
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a> CAtlPreviewCtrlImpl:: m_plf

미리 보기 창에 텍스트를 표시 하는 데 사용 되는 글꼴입니다.

```cpp
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a> CAtlPreviewCtrlImpl:: OnPaint

WM_PAINT 메시지를 처리 합니다.

```cpp
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>매개 변수

*nMsg*<br/>
WM_PAINT로 설정 합니다.

*wParam*<br/>
이 매개 변수는 사용되지 않습니다.

*lParam*<br/>
이 매개 변수는 사용되지 않습니다.

*bHandled*<br/>
이 함수는 반환 될 때 TRUE를 포함 합니다.

### <a name="return-value"></a>반환 값

항상 0을 반환합니다.

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a> CAtlPreviewCtrlImpl:: 다시 그리기

이 컨트롤에 다시 그리도록 지시 합니다.

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a> CAtlPreviewCtrlImpl::SetHost

이 컨트롤에 대 한 새 부모를 설정 합니다.

```cpp
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
새 부모 창에 대 한 핸들입니다.

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a> CAtlPreviewCtrlImpl::SetPreviewVisuals

풍부한 미리 보기 콘텐츠의 시각적 개체를 설정 해야 하는 경우 풍부한 미리 보기 처리기에서 호출 됩니다.

```cpp
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>매개 변수

*clrBack*<br/>
미리 보기 창의 배경색입니다.

*clrText*<br/>
미리 보기 창의 텍스트 색입니다.

*plf*<br/>
미리 보기 창에 텍스트를 표시 하는 데 사용 되는 글꼴입니다.

### <a name="remarks"></a>설명

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a> CAtlPreviewCtrlImpl:: SetRect

이 컨트롤에 대 한 새 경계 사각형을 설정 합니다.

```cpp
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>매개 변수

*prc*<br/>
미리 보기 컨트롤의 새 크기와 위치를 지정 합니다.

*bRedraw*<br/>
컨트롤을 다시 그려야 하는지 여부를 지정 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[ATL COM 데스크톱 구성 요소](../../atl/atl-com-desktop-components.md)
