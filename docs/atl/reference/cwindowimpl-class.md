---
description: '자세히 알아보기: CWindowImpl 클래스'
title: CWindowImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: c0736f0c963016fe5f65982c90903bfdce7c382e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140116"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 클래스

창을 만들거나 서브클래싱하기 위한 메서드를 제공합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
`CWindowImpl`에서 파생된 새 클래스입니다.

*TBase*<br/>
클래스의 기본 클래스입니다. 기본적으로 기본 클래스는 [CWindow](../../atl/reference/cwindow-class.md)입니다.

*TWinTraits*<br/>
창에 대 한 스타일을 정의 하는 [특성 클래스](../../atl/understanding-window-traits.md) 입니다. 기본값은 `CControlWinTraits`입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWindowImpl:: Create](#create)|창을 만듭니다.|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 메서드

|Name|설명|
|-|-|
|[DefWindowProc](#defwindowproc)|기본 메시지 처리를 제공합니다.|
|[GetCurrentMessage](#getcurrentmessage)|현재 메시지를 반환합니다.|
|[GetWindowProc](#getwindowproc)|현재 창 프로시저를 반환합니다.|
|[OnFinalMessage](#onfinalmessage)|마지막 메시지를 받은 후에 호출 됩니다 (일반적으로 WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|창을 서브클래싱합니다.|
|[UnsubclassWindow](#unsubclasswindow)|이전에 서브클래싱된 창을 복원합니다.|

### <a name="static-methods"></a>정적 메서드

|Name|설명|
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|창 클래스 정보를 관리 하는 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)의 정적 인스턴스를 반환 합니다.|
|[WindowProc](#windowproc)|창으로 보내는 메시지를 처리합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|창 클래스의 원본 창 프로시저를 가리킵니다.|

## <a name="remarks"></a>설명

`CWindowImpl`를 사용 하 여 창 또는 기존 창을 만들 수 있습니다. `CWindowImpl`창 프로시저는 메시지 맵을 사용 하 여 메시지를 적절 한 처리기로 보냅니다.

`CWindowImpl::Create`[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)에서 관리 하는 창 클래스 정보를 기반으로 창을 만듭니다. `CWindowImpl`[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) 매크로를 포함 합니다. 즉, `CWndClassInfo` 새 창 클래스를 등록 합니다. 기존 창 클래스의 슈퍼 클래스를 만들려면에서 클래스를 파생 하 `CWindowImpl` 고 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 포함 합니다. 이 경우 `CWndClassInfo`는 기존 클래스를 기반으로 하는 창 클래스 등록하지만 `CWindowImpl::WindowProc`를 사용합니다. 예를 들어:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> `CWndClassInfo`는 한 윈도우 클래스의 정보만 관리하기 때문에, `CWindowImpl`의 인스턴스를 통해 생성된 각 창은 동일한 창 클래스를 기반으로 합니다.

`CWindowImpl`은 또한 창 서브클래싱도 지원합니다. `SubclassWindow` 메서드는 기존 창을 `CWindowImpl` 개체에 연결하고 창 프로시저를 `CWindowImpl::WindowProc`로 변경합니다. `CWindowImpl`의 각 인스턴스는 다른 창을 서브클래싱할 수 있습니다.

> [!NOTE]
> 지정 된 개체에 대해 `CWindowImpl` 또는를 `Create` 호출 `SubclassWindow` 합니다. 동일한 개체에서 두 메서드를 모두 호출하지는 마십시오.

뿐만 아니라 `CWindowImpl` ATL은 다른 개체에 포함 된 창을 만드는 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 제공 합니다.

기본 클래스 소멸자 (~ `CWindowImplRoot` )는 개체가 제거 되기 전에 창이 사라졌는지 확인 합니다.

`CWindowImpl`에서 파생 되는에서 파생 되는에서 파생 `CWindowImplBaseT` `CWindowImplRoot` `TBase` 됩니다 [](../../atl/reference/cmessagemap-class.md).

|항목|참조 항목|
|--------------------------------|---------|
|컨트롤 만들기|[ATL 자습서](../../atl/active-template-library-atl-tutorial.md)|
|ATL에서 창 사용하기|[ATL 창 클래스](../../atl/atl-window-classes.md)|
|ATL 프로젝트 마법사|[ATL 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cwindowimplcreate"></a><a name="create"></a> CWindowImpl:: Create

새 창 클래스를 기반으로 창을 만듭니다.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
진행 부모 또는 소유자 창에 대 한 핸들입니다.

*rect*<br/>
진행 창의 위치를 지정 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체입니다. 는 `RECT` 포인터 또는 참조로 전달 될 수 있습니다.

*szWindowName*<br/>
진행 창의 이름을 지정 합니다. 기본값은 NULL입니다.

*dwStyle*<br/>
진행 창의 스타일입니다. 이 값은 창의 특성 클래스에서 제공 하는 스타일과 결합 됩니다. 기본값은 특성 클래스에 스타일에 대 한 모든 권한을 부여 합니다. 가능한 값 목록은 Windows SDK의 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 를 참조 하세요.

*dwExStyle*<br/>
진행 확장 창 스타일입니다. 이 값은 창의 특성 클래스에서 제공 하는 스타일과 결합 됩니다. 기본값은 특성 클래스에 스타일에 대 한 모든 권한을 부여 합니다. 가능한 값 목록은 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 를 참조 하세요.

*MenuOrID*<br/>
진행 자식 창의 경우 창 식별자입니다. 최상위 창의 경우 창의 메뉴 핸들입니다. 기본값은 **0u** 입니다.

*lpCreateParam*<br/>
진행 창 생성 데이터에 대 한 포인터입니다. 전체 설명은 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)에 대 한 final 매개 변수에 대 한 설명을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 새로 만든 창에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`Create` 는 아직 등록 되지 않은 경우 먼저 창 클래스를 등록 합니다. 새로 만든 창이 개체에 자동으로 연결 됩니다 `CWindowImpl` .

> [!NOTE]
> 이미 [SubclassWindow](#subclasswindow)를 호출한 경우에는 `Create`를 호출하지 마세요.

기존 창 클래스를 기반으로 하는 창 클래스를 사용 하려면에서 클래스를 파생 하 `CWindowImpl` 고 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 포함 합니다. 기존 창 클래스의 창 프로시저는 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)에 저장 됩니다. 자세한 내용은 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 개요를 참조 하세요.

> [!NOTE]
> *MenuOrID* 매개 변수에 대 한 값으로 0을 사용 하는 경우 컴파일러 오류를 방지 하려면 해당 값을 0u (기본값)로 지정 해야 합니다.

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a> CWindowImpl::D efWindowProc

메시지 맵에서 처리 되지 않은 메시지를 처리 하기 위해 [WindowProc](#windowproc) 에서 호출 됩니다.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>매개 변수

*uMsg*<br/>
진행 창에 전송 된 메시지입니다.

*wParam*<br/>
진행 추가 메시지 관련 정보입니다.

*lParam*<br/>
진행 추가 메시지 관련 정보입니다.

### <a name="return-value"></a>반환 값

메시지 처리의 결과입니다.

### <a name="remarks"></a>설명

기본적으로에서는 `DefWindowProc` [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 함수를 호출 하 여 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)에 지정 된 창 프로시저로 메시지 정보를 보냅니다.

매개 변수가 없는 함수는 현재 메시지에서 필요한 매개 변수를 자동으로 검색 합니다.

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a> CWindowImpl:: GetCurrentMessage

구조에 패키지 된 현재 메시지를 반환 합니다 `MSG` .

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>반환 값

현재 메시지입니다.

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a> CWindowImpl:: GetWindowProc

`WindowProc`현재 창 프로시저를 반환 합니다.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>반환 값

현재 창 프로시저입니다.

### <a name="remarks"></a>설명

이 메서드를 재정의 하 여 창 프로시저를 고유한 창으로 바꿉니다.

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a> CWindowImpl:: GetWndClassInfo

창 클래스 정보에 액세스 하기 위해 [Create](#create) 에서 호출 됩니다.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>반환 값

[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)의 정적 인스턴스입니다.

### <a name="remarks"></a>설명

기본적으로는 `CWindowImpl` 새 창 클래스를 지정 하는 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) 매크로를 통해이 메서드를 가져옵니다.

기존 창 클래스의 슈퍼 클래스를 만들려면에서 클래스를 파생 하 `CWindowImpl` 고 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 포함 하 여를 재정의 `GetWndClassInfo` 합니다. 자세한 내용은 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 개요를 참조 하세요.

DECLARE_WND_CLASS 및 DECLARE_WND_SUPERCLASS 매크로를 사용 하는 것 외에도 `GetWndClassInfo` 고유한 구현으로 재정의할 수 있습니다.

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a> CWindowImpl:: m_pfnSuperWindowProc

창에 따라는 다음 창 프로시저 중 하나를 가리킵니다.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>설명

|창 유형|창 프로시저|
|--------------------|----------------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) 매크로를 통해 지정 된 새 창 클래스를 기반으로 하는 창입니다.|[DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32 함수입니다.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 매크로를 통해 지정 된 기존 클래스를 수정 하는 창 클래스를 기반으로 하는 창입니다.|기존 창 클래스의 창 프로시저입니다.|
|서브클래싱된 창입니다.|서브클래싱된 창의 원래 창 프로시저입니다.|

[CWindowImpl::D efwindowproc](#defwindowproc) 는에 저장 된 창 프로시저로 메시지 정보를 보냅니다 `m_pfnSuperWindowProc` .

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a> CWindowImpl:: On% 메시지

마지막 메시지를 받은 후 호출 됩니다 (일반적으로 WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
진행 소멸 되는 창에 대 한 핸들입니다.

### <a name="remarks"></a>설명

의 기본 구현은 `OnFinalMessage` 아무 작업도 수행 하지 않지만 창을 소멸 하기 전에 정리를 처리 하도록이 함수를 재정의할 수 있습니다. 창 소멸 시 개체를 자동으로 삭제 하려면이 함수에서 **delete this** 를 호출 하면 됩니다.

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a> CWindowImpl:: SubclassWindow

*HWnd* 로 식별 되는 창을 서브클래싱하 고 개체에 연결 `CWindowImpl` 합니다.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
진행 서브클래싱 되는 창에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

창이 서브클래싱된 경우 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이제 서브클래싱된 창에서 [CWindowImpl:: WindowProc](#windowproc)를 사용 합니다. 원래 창 프로시저는 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)에 저장 됩니다.

> [!NOTE]
> 이미 [Create](#create)를 호출한 경우에는 `SubclassWindow`를 호출하지 마세요.

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a> CWindowImpl:: UnsubclassWindow

개체에서 서브클래싱된 창을 분리 `CWindowImpl` 하 고 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)에 저장 된 원래 창 프로시저를 복원 합니다.

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>반환 값

이전에 서브클래싱된 창에 대 한 핸들입니다.

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a> CWindowImpl:: WindowProc

이 정적 함수는 창 프로시저를 구현 합니다.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
진행 창에 대 한 핸들입니다.

*uMsg*<br/>
진행 창에 전송 된 메시지입니다.

*wParam*<br/>
진행 추가 메시지 관련 정보입니다.

*lParam*<br/>
진행 추가 메시지 관련 정보입니다.

### <a name="return-value"></a>반환 값

메시지 처리의 결과입니다.

### <a name="remarks"></a>설명

`WindowProc` 는 기본 메시지 맵 ( [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)로 선언 됨)을 사용 하 여 메시지를 적절 한 처리기로 보냅니다. 필요한 경우 `WindowProc` 추가 메시지 처리를 위해 [DefWindowProc](#defwindowproc) 를 호출 합니다. 최종 메시지가 처리 되지 않은 경우는 `WindowProc` 다음을 수행 합니다.

- 창이 서브클래싱된 경우 하위 클래스를 수행 하지 않습니다.

- `m_hWnd`을 지웁니다.

- 창이 소멸 되기 전에 [Onto 메시지](#onfinalmessage) 를 호출 합니다.

`WindowProc`를 재정의 하 여 메시지를 처리 하는 다른 메커니즘을 제공할 수 있습니다.

## <a name="see-also"></a>참고 항목

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
