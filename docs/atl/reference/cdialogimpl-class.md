---
description: '자세한 정보: CDialogImpl 클래스'
title: CDialogImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: 228a63edde7eb66960a0acad5d60088d909946a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141858"
---
# <a name="cdialogimpl-class"></a>CDialogImpl 클래스

이 클래스는 모달 또는 모덜리스 대화 상자를 만드는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CDialogImpl` 입니다.

*TBase*<br/>
새 클래스의 기본 클래스입니다. 기본 클래스는 [CWindow](../../atl/reference/cwindow-class.md)입니다.

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|함수|Description|
|-|-|
|[만들기](#create)|모덜리스 대화 상자를 만듭니다.|
|[DestroyWindow](#destroywindow)|모덜리스 대화 상자를 소멸 시킵니다.|
|[DoModal](#domodal)|모달 대화 상자를 만듭니다.|
|[EndDialog](#enddialog)|모달 대화 상자를 소멸 시킵니다.|

### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT 메서드

|함수|설명|
|-|-|
|[GetDialogProc](#getdialogproc)|현재 대화 상자 프로시저를 반환 합니다.|
|[MapDialogRect](#mapdialogrect)|지정 된 사각형의 대화 상자 단위를 화면 단위 (픽셀)에 매핑합니다.|
|[OnFinalMessage](#onfinalmessage)|마지막 메시지를 받은 후 호출 됩니다. 일반적으로 WM_NCDESTROY입니다.|

### <a name="static-functions"></a>정적 함수

|함수|설명|
|-|-|
|[DialogProc](#dialogproc)|대화 상자에 전송 된 메시지를 처리 합니다.|
|[StartDialogProc](#startdialogproc)|대화 상자로 보낸 메시지를 처리 하기 위해 첫 번째 메시지를 받을 때 호출 됩니다.|

## <a name="remarks"></a>설명

를 사용 `CDialogImpl` 하 여 모달 또는 모덜리스 대화 상자를 만들 수 있습니다. `CDialogImpl` 기본 메시지 맵을 사용 하 여 메시지를 적절 한 처리기에 전달 하는 대화 상자 프로시저를 제공 합니다.

기본 클래스 소멸자는 `~CWindowImplRoot` 개체를 삭제 하기 전에 창이 사라졌는지 확인 합니다.

`CDialogImpl` 는에서 파생 `CDialogImplBaseT` 되 고이는에서 파생 `CWindowImplRoot` 됩니다.

> [!NOTE]
> 클래스는 `IDD` 대화 상자 템플릿 리소스 ID를 지정 하는 멤버를 정의 해야 합니다. 예를 들어, ATL 프로젝트 마법사는 클래스에 다음 줄을 자동으로 추가 합니다.

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

여기서 `MyDlg` 는 마법사의 **이름** 페이지에 입력 한 **짧은 이름** 입니다.

|항목|참조 항목|
|--------------------------------|---------|
|컨트롤 만들기|[ATL 자습서](../../atl/active-template-library-atl-tutorial.md)|
|ATL에서 대화 상자 사용|[ATL 창 클래스](../../atl/atl-window-classes.md)|
|ATL 프로젝트 마법사|[ATL 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)|
|대화 상자|Windows SDK [대화 상자](/windows/win32/dlgbox/dialog-boxes) 및 후속 항목|

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cdialogimplcreate"></a><a name="create"></a> CDialogImpl:: Create

모덜리스 대화 상자를 만듭니다.

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
진행 소유자 창에 대 한 핸들입니다.

**Rect&** *rect* [in] 대화 상자의 크기와 위치를 지정 하는 [rect](/windows/win32/api/windef/ns-windef-rect) 구조체입니다.

*dwInitParam*<br/>
진행 WM_INITDIALOG 메시지의 *lParam* 매개 변수에서 대화 상자에 전달할 값을 지정 합니다.

### <a name="return-value"></a>반환 값

새로 만든 대화 상자에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 대화 상자는 개체에 자동으로 연결 됩니다 `CDialogImpl` . 모달 대화 상자를 만들려면 [DoModal](#domodal)를 호출 합니다. 위의 두 번째 재정의는 [CComControl](../../atl/reference/ccomcontrol-class.md)사용 되는 경우에만 사용 됩니다.

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a> CDialogImpl::D estroyWindow

모덜리스 대화 상자를 소멸 시킵니다.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>반환 값

대화 상자가 성공적으로 제거 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

대화 상자가 성공적으로 제거 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a> CDialogImpl::D ialogProc

이 정적 함수는 대화 상자 프로시저를 구현 합니다.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
진행 대화 상자에 대 한 핸들입니다.

*uMsg*<br/>
진행 대화 상자로 보낸 메시지입니다.

*wParam*<br/>
진행 추가 메시지 관련 정보입니다.

*lParam*<br/>
진행 추가 메시지 관련 정보입니다.

### <a name="return-value"></a>반환 값

메시지가 처리 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`DialogProc` 기본 메시지 맵을 사용 하 여 메시지를 적절 한 처리기로 보냅니다.

`DialogProc`를 재정의 하 여 메시지를 처리 하는 다른 메커니즘을 제공할 수 있습니다.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a> CDialogImpl::D oModal

모달 대화 상자를 만듭니다.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
진행 소유자 창에 대 한 핸들입니다. 기본값은 [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 함수의 반환 값입니다.

*dwInitParam*<br/>
진행 WM_INITDIALOG 메시지의 *lParam* 매개 변수에서 대화 상자에 전달할 값을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 [EndDialog](#enddialog)호출에 지정 된 *nRetCode* 매개 변수의 값입니다. 그렇지 않으면 -1입니다.

### <a name="remarks"></a>설명

이 대화 상자는 개체에 자동으로 연결 됩니다 `CDialogImpl` .

모덜리스 대화 상자를 만들려면 [create](#create)를 호출 합니다.

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a> CDialogImpl:: EndDialog

모달 대화 상자를 소멸 시킵니다.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>매개 변수

*nRetCode*<br/>
진행 [Cdialogimpl:D oModal](#domodal)에서 반환 될 값입니다.

### <a name="return-value"></a>반환 값

대화 상자가 소멸 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`EndDialog` 는 대화 상자 프로시저를 통해 호출 해야 합니다. 대화 상자가 제거 되 면 Windows에서는 대화 상자를 만든의 반환 값으로 *nRetCode* 의 값을 사용 합니다 `DoModal` .

> [!NOTE]
> `EndDialog`모덜리스 대화 상자를 삭제 하려면를 호출 하지 마세요. 대신 [CWindow::D estroyWindow](../../atl/reference/cwindow-class.md#destroywindow) 를 호출 합니다.

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a> CDialogImpl:: GetDialogProc

`DialogProc`현재 대화 상자 프로시저인를 반환 합니다.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>반환 값

현재 대화 상자 프로시저입니다.

### <a name="remarks"></a>설명

이 메서드를 재정의 하 여 대화 상자 프로시저를 고유한 것으로 바꿉니다.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a> CDialogImpl:: MapDialogRect

지정 된 사각형의 대화 상자 단위를 화면 단위 (픽셀)로 변환 (maps) 합니다.

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`CRect`업데이트 영역을 포함 하는 업데이트의 클라이언트 좌표를 수신 하는 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조를 가리킵니다.

### <a name="return-value"></a>반환 값

업데이트에 성공 하면 0이 아닌 값입니다. 업데이트가 실패 하는 경우 0입니다. 확장 오류 정보를 가져오려면 `GetLastError`를 호출합니다.

### <a name="remarks"></a>설명

함수는 지정 된 구조체의 좌표를 `RECT` 변환 된 좌표로 대체 합니다. 그러면 구조를 사용 하 여 대화 상자를 만들거나 대화 상자에 컨트롤을 배치할 수 있습니다.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a> CDialogImpl:: On% 메시지

마지막 메시지를 받은 후 호출 됩니다 (일반적으로 `WM_NCDESTROY` ).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
진행 소멸 되는 창에 대 한 핸들입니다.

### <a name="remarks"></a>설명

창 소멸 시 개체를 자동으로 삭제 하려면 여기에서 **삭제** 를 호출 하면 됩니다.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a> CDialogImpl:: StartDialogProc

대화 상자에 전송 된 메시지를 처리 하기 위해 첫 번째 메시지를 받을 때 한 번만 호출 됩니다.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
진행 대화 상자에 대 한 핸들입니다.

*uMsg*<br/>
진행 대화 상자로 보낸 메시지입니다.

*wParam*<br/>
진행 추가 메시지 관련 정보입니다.

*lParam*<br/>
진행 추가 메시지 관련 정보입니다.

### <a name="return-value"></a>반환 값

창 프로시저입니다.

### <a name="remarks"></a>설명

에 대 한 초기 호출 후에 `StartDialogProc` `DialogProc` 는 대화 상자로 설정 되 고 추가 호출이 수행 됩니다.

## <a name="see-also"></a>참고 항목

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
