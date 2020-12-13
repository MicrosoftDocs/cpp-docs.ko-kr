---
description: '자세히 알아보기: CContainedWindowT 클래스'
title: CContainedWindowT 클래스
ms.date: 11/04/2016
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 68135ec6d8dc43623ec2a827bbe075e24eef8d42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142079"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 클래스

이 클래스는 다른 개체 내에 포함 된 창을 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>매개 변수

*TBase*<br/>
새 클래스의 기본 클래스입니다. 기본 클래스는 `CWindow` 입니다.

*TWinTraits*<br/>
창 스타일을 정의하는 특성 클래스입니다. 기본값은 `CControlWinTraits`입니다.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) 는의 특수화입니다 `CContainedWindowT` . 기본 클래스 또는 특성을 변경 하려면 직접를 사용 `CContainedWindowT` 합니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|생성자입니다. 포함 된 창의 메시지를 처리할 메시지 맵을 지정 하는 데이터 멤버를 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CContainedWindowT:: Create](#create)|창을 만듭니다.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|기본 메시지 처리를 제공합니다.|
|[CContainedWindowT:: GetCurrentMessage](#getcurrentmessage)|현재 메시지를 반환합니다.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|포함 된 창의 창 클래스를 등록 합니다.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|창을 서브클래싱합니다.|
|[CContainedWindowT:: SwitchMessageMap](#switchmessagemap)|포함 된 창의 메시지를 처리 하는 데 사용 되는 메시지 맵을 변경 합니다.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|이전에 서브클래싱된 창을 복원합니다.|
|[CContainedWindowT::WindowProc](#windowproc)|정적인 포함 된 창에 전송 된 메시지를 처리 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|포함 된 창의 메시지를 처리 하는 메시지 맵을 식별 합니다.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|새 창 클래스의 기반이 되는 기존 창 클래스의 이름을 지정 합니다.|
|[CContainedWindowT:: m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|창 클래스의 원본 창 프로시저를 가리킵니다.|
|[CContainedWindowT:: m_pObject](#m_pobject)|포함 하는 개체를 가리킵니다.|

## <a name="remarks"></a>설명

`CContainedWindowT` 다른 개체 내에 포함 된 창을 구현 합니다. `CContainedWindowT`의 창 프로시저는 포함 하는 개체의 메시지 맵을 사용 하 여 메시지를 적절 한 처리기로 보냅니다. 개체를 생성할 때 `CContainedWindowT` 사용할 메시지 맵을 지정 합니다.

`CContainedWindowT` 기존 창 클래스를 superclassing 하 여 새 창을 만들 수 있습니다. `Create`메서드는 먼저 기존 클래스를 기반으로 하는 창 클래스를 등록 하지만를 사용 `CContainedWindowT::WindowProc` 합니다. `Create` 그런 다음이 새 창 클래스를 기반으로 창을 만듭니다. 의 각 인스턴스 `CContainedWindowT` 는 다른 창 클래스의 슈퍼 클래스를 사용할 수 있습니다.

`CContainedWindowT`은 또한 창 서브클래싱도 지원합니다. `SubclassWindow` 메서드는 기존 창을 `CContainedWindowT` 개체에 연결하고 창 프로시저를 `CContainedWindowT::WindowProc`로 변경합니다. `CContainedWindowT`의 각 인스턴스는 다른 창을 서브클래싱할 수 있습니다.

> [!NOTE]
> 지정 된 개체에 대해 `CContainedWindowT` 또는를 `Create` 호출 `SubclassWindow` 합니다. 동일한 개체에서 두 메서드를 모두 호출 하면 안 됩니다.

ATL 프로젝트 마법사에서 **컨트롤에 따라 추가** 옵션을 사용 하면 마법사가 자동으로 `CContainedWindowT` 컨트롤을 구현 하는 클래스에 데이터 멤버를 추가 합니다. 다음 예제에서는 포함 된 창을 선언 하는 방법을 보여 줍니다.

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|항목|참조 항목|
|--------------------------------|---------|
|컨트롤 만들기|[ATL 자습서](../../atl/active-template-library-atl-tutorial.md)|
|ATL에서 창 사용하기|[ATL 창 클래스](../../atl/atl-window-classes.md)|
|ATL 프로젝트 마법사|[ATL 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)|
|Windows|Windows SDK의 [Windows](/windows/win32/winmsg/windows) 및 후속 항목|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a> CContainedWindowT::CContainedWindowT

생성자는 데이터 멤버를 초기화 합니다.

```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>
진행 포함 된 창의 기반이 되는 기존 창 클래스의 이름입니다.

*pObject*<br/>
진행 메시지 맵을 선언 하는 포함 하는 개체에 대 한 포인터입니다. 이 개체의 클래스는 [Cmessagemap](../../atl/reference/cmessagemap-class.md)클래스에서 파생 되어야 합니다.

*dwMsgMapID*<br/>
진행 포함 된 창의 메시지를 처리 하는 메시지 맵을 식별 합니다. 기본값 0은 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)로 선언 된 기본 메시지 맵을 지정 합니다. [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)로 선언 된 대체 메시지 맵을 사용 하려면을 전달 `msgMapID` 합니다.

### <a name="remarks"></a>설명

[만들기](#create)를 통해 새 창을 만들려면 *lpszClassName* 매개 변수에 대 한 기존 창 클래스의 이름을 전달 해야 합니다. 예는 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 개요를 참조 하세요.

세 가지 생성자가 있습니다.

- 세 개의 인수를 사용 하는 생성자가 일반적으로 호출 됩니다.

- 인수가 두 개인 생성자는의 클래스 이름을 사용 합니다 `TBase::GetWndClassName` .

- 인수를 사용 하지 않는 생성자는 나중에 인수를 제공 하려는 경우에 사용 됩니다. 나중에를 호출할 때 창 클래스 이름, 메시지 맵 개체 및 메시지 맵 ID를 제공 해야 합니다 `Create` .

[SubclassWindow](#subclasswindow)를 통해 기존 창을 서브클래싱하는 경우에는 *lpszClassName* 값이 사용 되지 않습니다. 따라서이 매개 변수에 NULL을 전달할 수 있습니다.

## <a name="ccontainedwindowtcreate"></a><a name="create"></a> CContainedWindowT:: Create

[RegisterWndSuperclass](#registerwndsuperclass) 를 호출 하 여 기존 클래스를 기반으로 하는 창 클래스를 등록 하지만 [CContainedWindowT:: WindowProc](#windowproc)를 사용 합니다.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>
진행 포함 된 창의 기반이 되는 기존 창 클래스의 이름입니다.

*pObject*<br/>
진행 메시지 맵을 선언 하는 포함 하는 개체에 대 한 포인터입니다. 이 개체의 클래스는 [Cmessagemap](../../atl/reference/cmessagemap-class.md)클래스에서 파생 되어야 합니다.

*dwMsgMapID*<br/>
진행 포함 된 창의 메시지를 처리 하는 메시지 맵을 식별 합니다. 기본값 0은 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)로 선언 된 기본 메시지 맵을 지정 합니다. [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)로 선언 된 대체 메시지 맵을 사용 하려면을 전달 `msgMapID` 합니다.

*hWndParent*<br/>
진행 부모 또는 소유자 창에 대 한 핸들입니다.

*rect*<br/>
진행 창의 위치를 지정 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체입니다. 는 `RECT` 포인터 또는 참조로 전달 될 수 있습니다.

*szWindowName*<br/>
진행 창의 이름을 지정 합니다. 기본값은 NULL입니다.

*dwStyle*<br/>
진행 창의 스타일입니다. 기본값은 WS_CHILD &#124; WS_VISIBLE입니다. 가능한 값 목록은 Windows SDK의 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 를 참조 하세요.

*dwExStyle*<br/>
진행 확장 창 스타일입니다. 기본값은 확장 스타일이 없음을 의미 하는 0입니다. 가능한 값 목록은 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 를 참조 하세요.

*MenuOrID*<br/>
진행 자식 창의 경우 창 식별자입니다. 최상위 창의 경우 창의 메뉴 핸들입니다. 기본값은 **0u** 입니다.

*lpCreateParam*<br/>
진행 창 생성 데이터에 대 한 포인터입니다. 전체 설명은 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)에 대 한 final 매개 변수에 대 한 설명을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 새로 만든 창에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

기존 창 클래스 이름은 [m_lpszClassName](#m_lpszclassname)에 저장 됩니다. `Create` 그런 다음이 새 클래스를 기반으로 창을 만듭니다. 새로 만든 창이 개체에 자동으로 연결 됩니다 `CContainedWindowT` .

> [!NOTE]
> 이미 [SubclassWindow](#subclasswindow)를 호출한 경우에는 `Create`를 호출하지 마세요.

> [!NOTE]
> *MenuOrID* 매개 변수에 대 한 값으로 0을 사용 하는 경우 컴파일러 오류를 방지 하려면 해당 값을 0u (기본값)로 지정 해야 합니다.

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a> CContainedWindowT::D efWindowProc

메시지 맵에서 처리 되지 않은 메시지를 처리 하기 위해 [WindowProc](#windowproc) 에서 호출 됩니다.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a> CContainedWindowT:: GetCurrentMessage

현재 메시지 ()를 반환 합니다 `m_pCurrentMsg` .

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>반환 값

구조에 패키지 된 현재 메시지 `MSG` 입니다.

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a> CContainedWindowT:: m_dwMsgMapID

포함 된 창에 현재 사용 되 고 있는 메시지 맵의 식별자를 포함 합니다.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>설명

이 메시지 맵은 포함 하는 개체에서 선언 해야 합니다.

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)로 선언 된 기본 메시지 맵은 항상 0으로 식별 됩니다. [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)로 선언 된 대체 메시지 맵은로 식별 됩니다 `msgMapID` .

`m_dwMsgMapID` 는 생성자에 의해 처음 초기화 되며 [Switchmessagemap](#switchmessagemap)을 호출 하 여 변경할 수 있습니다. 예는 [CContainedWindowT 개요](../../atl/reference/ccontainedwindowt-class.md)를 참조 하세요.

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a> CContainedWindowT:: m_lpszClassName

기존 창 클래스의 이름을 지정 합니다.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>설명

창을 만들 때 [create](#create) 는이 기존 클래스를 기반으로 하지만 [CContainedWindowT:: WindowProc](#windowproc)를 사용 하는 새 창 클래스를 등록 합니다.

`m_lpszClassName` 는 생성자에 의해 초기화 됩니다. 예는 [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) 개요를 참조 하세요.

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a> CContainedWindowT:: m_pfnSuperWindowProc

포함 된 창이 서브클래싱된 경우는 `m_pfnSuperWindowProc` window 클래스의 원래 창 프로시저를 가리킵니다.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>설명

포함 된 창이 superclassed 경우 기존 클래스를 수정 하는 창 클래스를 기반으로 하 여 `m_pfnSuperWindowProc` 기존 창 클래스의 창 프로시저를 가리킵니다.

[DefWindowProc](#defwindowproc) 메서드는에 저장 된 창 프로시저로 메시지 정보를 보냅니다 `m_pfnSuperWindowProc` .

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a> CContainedWindowT:: m_pObject

개체를 포함 하는 개체를 가리킵니다 `CContainedWindowT` .

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>설명

클래스가 [Cmessagval에서](../../atl/reference/cmessagemap-class.md)파생 되어야 하는이 컨테이너는 포함 된 창에서 사용 하는 메시지 맵을 선언 합니다.

`m_pObject` 는 생성자에 의해 초기화 됩니다. 예는 [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) 개요를 참조 하세요.

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a> CContainedWindowT::RegisterWndSuperclass

포함 된 창의 창 클래스를 등록 하기 위해 [Create](#create) 에 의해 호출 됩니다.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>반환 값

성공 하면 등록 되는 창 클래스를 고유 하 게 식별 하는 atom입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 창 클래스는 기존 클래스를 기반으로 하지만 [CContainedWindowT:: WindowProc](#windowproc)를 사용 합니다. 기존 창 클래스의 이름 및 창 프로시저는 각각 [m_lpszClassName](#m_lpszclassname) 및 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)에 저장 됩니다.

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a> CContainedWindowT::SubclassWindow

*HWnd* 로 식별 되는 창을 서브클래싱하 고 개체에 연결 `CContainedWindowT` 합니다.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
진행 서브클래싱 되는 창에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

창이 서브클래싱된 경우 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이제 서브클래싱된 창에서 [CContainedWindowT:: WindowProc](#windowproc)를 사용 합니다. 원래 창 프로시저는 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)에 저장 됩니다.

> [!NOTE]
> 이미 [Create](#create)를 호출한 경우에는 `SubclassWindow`를 호출하지 마세요.

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a> CContainedWindowT:: SwitchMessageMap

포함 된 창의 메시지를 처리 하는 데 사용할 메시지 맵을 변경 합니다.

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>매개 변수

*dwMsgMapID*<br/>
진행 메시지 맵 식별자입니다. [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)로 선언 된 기본 메시지 맵을 사용 하려면 0을 전달 합니다. [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)로 선언 된 대체 메시지 맵을 사용 하려면을 전달 `msgMapID` 합니다.

### <a name="remarks"></a>설명

메시지 맵은 포함 하는 개체에 정의 되어야 합니다.

처음에는 생성자에서 메시지 맵 식별자를 지정 합니다.

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a> CContainedWindowT::UnsubclassWindow

개체에서 서브클래싱된 창을 분리 `CContainedWindowT` 하 고 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)에 저장 된 원래 창 프로시저를 복원 합니다.

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>매개 변수

*bForce*<br/>
진행 이 개체에 대 한 창 프로시저가 `CContainedWindowT` 현재 활성화 되어 있지 않은 경우에도 원래 창 프로시저를 강제로 복원 하려면 TRUE로 설정 합니다. *Bforce* 가 FALSE로 설정 되어 있고이 개체에 대 한 창 프로시저가 `CContainedWindowT` 현재 활성화 되어 있지 않은 경우 원래 창 프로시저는 복원 되지 않습니다.

### <a name="return-value"></a>반환 값

이전에 서브클래싱된 창에 대 한 핸들입니다. *Bforce* 가 FALSE로 설정 되어 있고이 개체에 대 한 창 프로시저가 `CContainedWindowT` 현재 활성화 되어 있지 않으면 NULL을 반환 합니다.

### <a name="remarks"></a>설명

창이 제거 되기 전에 원래 창 프로시저를 복원 하려는 경우에만이 메서드를 사용 합니다. 그렇지 않으면 창이 소멸 될 때 [WindowProc](#windowproc) 가 자동으로이 작업을 수행 합니다.

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a> CContainedWindowT:: WindowProc

이 정적 메서드는 창 프로시저를 구현 합니다.

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

`WindowProc` 메시지를 [m_dwMsgMapID](#m_dwmsgmapid)으로 식별 되는 메시지 맵으로 보냅니다. 필요한 경우 `WindowProc` 추가 메시지 처리를 위해 [DefWindowProc](#defwindowproc) 를 호출 합니다.

## <a name="see-also"></a>참고 항목

[CWindow 클래스](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl 클래스](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap 클래스](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
