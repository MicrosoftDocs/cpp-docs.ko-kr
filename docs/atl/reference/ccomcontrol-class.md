---
description: '자세히 알아보기: CComControl 클래스'
title: CComControl 클래스
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: 3fbd0f3483c61993a575b0817538f759b06c11d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146746"
---
# <a name="ccomcontrol-class"></a>CComControl 클래스

이 클래스는 ATL 컨트롤을 만들고 관리 하기 위한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컨트롤을 구현 하는 클래스입니다.

*Winbase.h*<br/>
창 고 함수를 구현 하는 기본 클래스입니다. 기본값은 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComControl:: ControlQueryInterface](#controlqueryinterface)|요청된 인터페이스에 대한 포인터를 검색합니다.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|컨트롤의 창을 만듭니다.|
|[CComControl::FireOnChanged](#fireonchanged)|컨트롤 속성이 변경 되었음을 컨테이너 싱크에 알립니다.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|컨트롤 속성이 변경 될 것 이며 개체가 싱크에 요청 하 고 있는지를 컨테이너 싱크에 알립니다.|
|[CComControl:: MessageBox](#messagebox)|이 메서드를 호출 하 여 메시지 상자를 만들고 표시 하 고 작동할 수 있습니다.|

## <a name="remarks"></a>설명

`CComControl` 는 ATL 컨트롤의 유용한 컨트롤 도우미 함수 및 필수 데이터 멤버 집합입니다. ATL 컨트롤 마법사를 사용 하 여 표준 컨트롤이 나 DHTML 컨트롤을 만들면 마법사가에서 자동으로 클래스를 파생 시킵니다 `CComControl` . `CComControl`[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)에서 대부분의 메서드를 파생 합니다.

컨트롤을 만드는 방법에 대 한 자세한 내용은 [ATL 자습서](../../atl/active-template-library-atl-tutorial.md)를 참조 하십시오. ATL 프로젝트 마법사에 대 한 자세한 내용은 [Atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)문서를 참조 하세요.

메서드 및 데이터 멤버에 대 한 데모는 `CComControl` [CIRC](../../overview/visual-cpp-samples.md) 샘플을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a> CComControl::CComControl

생성자입니다.

```
CComControl();
```

### <a name="remarks"></a>설명

[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) 생성자를 호출 하 여 `m_hWnd` [CWindowImpl](../../atl/reference/cwindowimpl-class.md)를 통해 상속 된 데이터 멤버를 전달 합니다.

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a> CComControl:: ControlQueryInterface

요청된 인터페이스에 대한 포인터를 검색합니다.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 요청 되는 인터페이스의 GUID입니다.

*ppv*<br/>
제한이 *Iid* 로 식별 되는 인터페이스 포인터에 대 한 포인터 이거나, 인터페이스를 찾을 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

는 COM 맵 테이블의 인터페이스만 처리 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a> CComControl::CreateControlWindow

기본적으로는를 호출 하 여 컨트롤에 대 한 창을 만듭니다 `CWindowImpl::Create` .

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
진행 부모 또는 소유자 창에 대 한 핸들입니다. 올바른 창 핸들을 제공 해야 합니다. 컨트롤 창은 부모 창의 영역으로 한정 됩니다.

*rcPos*<br/>
진행 만들 창의 초기 크기와 위치입니다.

### <a name="remarks"></a>설명

단일 창 만들기 외에 다른 작업을 수행 하려는 경우이 메서드를 재정의 합니다. 예를 들어 두 개의 창을 만들면이 중 하나가 컨트롤의 도구 모음이 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a> CComControl::FireOnChanged

컨트롤 속성이 변경 되었음을 컨테이너 싱크에 알립니다.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>매개 변수

*dispID*<br/>
진행 변경 된 속성의 식별자입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

컨트롤 클래스가 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)에서 파생 되는 경우이 메서드는 [CFirePropNotifyEvent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) 를 호출 하 여 `IPropertyNotifySink` 지정 된 컨트롤 속성이 변경 되었음을 연결 된 모든 인터페이스에 알립니다. 컨트롤 클래스가에서 파생 되지 않은 경우 `IPropertyNotifySink` 이 메서드는 S_OK 반환 합니다.

컨트롤에서 연결 지점이 지원 되지 않는 경우에도이 메서드는를 호출 하는 것이 안전 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a> CComControl::FireOnRequestEdit

컨트롤 속성이 변경 될 것 이며 개체가 싱크에 요청 하 고 있는지를 컨테이너 싱크에 알립니다.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>매개 변수

*dispID*<br/>
진행 변경할 속성의 식별자입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

컨트롤 클래스가 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)에서 파생 되는 경우이 메서드는 [CFirePropNotifyEvent:: FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) 를 호출 하 여 `IPropertyNotifySink` 지정 된 컨트롤 속성이 변경 될 것으로 연결 된 모든 인터페이스를 알립니다. 컨트롤 클래스가에서 파생 되지 않은 경우 `IPropertyNotifySink` 이 메서드는 S_OK 반환 합니다.

컨트롤에서 연결 지점이 지원 되지 않는 경우에도이 메서드는를 호출 하는 것이 안전 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a> CComControl:: MessageBox

이 메서드를 호출 하 여 메시지 상자를 만들고 표시 하 고 작동할 수 있습니다.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
메시지 상자에 표시할 텍스트입니다.

*lpszCaption*<br/>
대화 상자 제목입니다. NULL (기본값) 이면 "Error" 라는 제목이 사용 됩니다.

*nType*<br/>
대화 상자의 내용과 동작을 지정 합니다. 사용 가능한 여러 메시지 상자의 목록은 Windows SDK 설명서의 [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) 항목을 참조 하세요. 기본값은 간단한 **확인** 단추를 제공 합니다.

### <a name="return-value"></a>반환 값

Windows SDK 설명서에서 [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) 에 나열 된 메뉴 항목 값 중 하나를 지정 하는 정수 값을 반환 합니다.

### <a name="remarks"></a>설명

`MessageBox` 는 개발 중에 그리고 사용자에 게 오류 또는 경고 메시지를 표시 하는 쉬운 방법으로 유용 합니다.

## <a name="see-also"></a>참고 항목

[CWindowImpl 클래스](../../atl/reference/cwindowimpl-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComControlBase 클래스](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl 클래스](../../atl/reference/ccomcompositecontrol-class.md)
