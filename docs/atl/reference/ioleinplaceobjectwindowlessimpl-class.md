---
description: '자세히 알아보기: IOleInPlaceObjectWindowlessImpl 클래스'
title: IOleInPlaceObjectWindowlessImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: 927a973565949bbfc6331e4b4e62d7cb270c2107
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139388"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 클래스

이 클래스는 `IUnknown` 창 없는 컨트롤에서 창 메시지를 받고 끌어서 놓기 작업에 참여할 수 있도록 하는 메서드를 구현 하 고 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IOleInPlaceObjectWindowlessImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|상황에 맞는 도움말을 사용 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleInPlaceObjectWindowlessImpl:: GetDropTarget](#getdroptarget)|`IDropTarget`끌어서 놓기를 지 원하는 내부 활성 창 없는 개체에 대 한 인터페이스를 제공 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleInPlaceObjectWindowlessImpl:: GetWindow](#getwindow)|창 핸들을 가져옵니다.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|활성 내부 컨트롤을 비활성화 합니다.|
|[IOleInPlaceObjectWindowlessImpl:: OnWindowMessage](#onwindowmessage)|컨테이너의 메시지를 내부 활성 상태의 창 없는 컨트롤로 디스패치합니다.|
|[IOleInPlaceObjectWindowlessImpl:: ReactivateAndUndo](#reactivateandundo)|이전에 비활성화 된 컨트롤을 다시 활성화 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleInPlaceObjectWindowlessImpl:: SetObjectRects](#setobjectrects)|현재 위치의 컨트롤이 표시 되는 부분을 나타냅니다.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|내부 활성화를 지 원하는 사용자 인터페이스를 비활성화 하 고 제거 합니다.|

## <a name="remarks"></a>설명

[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) 인터페이스는 내부 컨트롤의 다시 활성화 및 비활성화를 관리 하 고 표시 되는 컨트롤의 양을 결정 합니다. [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) 인터페이스를 사용 하면 창 없는 컨트롤에서 창 메시지를 받고 끌어서 놓기 작업에 참여할 수 있습니다. 클래스는 `IOleInPlaceObjectWindowlessImpl` 및의 기본 구현을 `IOleInPlaceObject` 제공 `IOleInPlaceObjectWindowless` 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a> IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

E_NOTIMPL을 반환합니다.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) 를 참조 하세요.

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a> IOleInPlaceObjectWindowlessImpl:: GetDropTarget

E_NOTIMPL을 반환합니다.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) 을 참조 하세요.

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a> IOleInPlaceObjectWindowlessImpl:: GetWindow

컨테이너는이 함수를 호출 하 여 컨트롤의 창 핸들을 가져옵니다.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>설명

일부 컨테이너는 현재 기간 이동 중인 경우에도 창 없는 컨트롤과 함께 작동 하지 않습니다. ATL의 구현에서 컨트롤 클래스의 데이터 멤버가 `m_bWasOnceWindowless` TRUE 이면 함수는 E_FAIL을 반환 합니다. 그렇지 않고 *phwnd* 가 NULL이 아닌 경우 `GetWindow` \* *phwnd* 을 컨트롤 클래스의 데이터 멤버로 설정 하 `m_hWnd` 고 S_OK을 반환 합니다.

Windows SDK [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) 을 참조 하세요.

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a> IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

내부 활성 컨트롤을 비활성화 하기 위해 컨테이너에 의해 호출 됩니다.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>설명

이 메서드는 컨트롤의 상태에 따라 전체 또는 부분 비활성화를 수행 합니다. 필요한 경우 컨트롤의 사용자 인터페이스는 비활성화 되 고 컨트롤의 창 (있는 경우)은 소멸 됩니다. 컨테이너는 컨트롤이 현재 활성화 되어 있지 않음을 알립니다. `IOleInPlaceUIWindow`컨테이너에서 메뉴와 테두리 공간을 협상 하는 데 사용 하는 인터페이스가 릴리스됩니다.

Windows SDK에서 [IOleInPlaceObject:: InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) 를 참조 하세요.

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a> IOleInPlaceObjectWindowlessImpl:: OnWindowMessage

컨테이너의 메시지를 내부 활성 상태의 창 없는 컨트롤로 디스패치합니다.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>설명

Windows SDK [IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) 를 참조 하세요.

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a> IOleInPlaceObjectWindowlessImpl:: ReactivateAndUndo

E_NOTIMPL을 반환합니다.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>설명

Windows SDK에서 [IOleInPlaceObject:: ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) 를 참조 하세요.

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a> IOleInPlaceObjectWindowlessImpl:: SetObjectRects

컨트롤의 크기 및/또는 위치가 변경 되었음을 컨트롤에 알리기 위해 컨테이너에 의해 호출 됩니다.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>설명

컨트롤의 `m_rcPos` 데이터 멤버와 컨트롤 표시를 업데이트 합니다. 클립 영역과 교차 하는 컨트롤 부분만 표시 됩니다. 컨트롤의 디스플레이가 이전에 클리핑되지는 했지만 클리핑이 제거 된 경우에는이 함수를 호출 하 여 컨트롤의 전체 뷰를 다시 그릴 수 있습니다.

Windows SDK [IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) 를 참조 하세요.

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a> IOleInPlaceObjectWindowlessImpl::UIDeactivate

내부 활성화를 지 원하는 컨트롤의 사용자 인터페이스를 비활성화 하 고 제거 합니다.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>설명

컨트롤 클래스의 데이터 멤버를 `m_bUIActive` FALSE로 설정 합니다. 이 함수의 ATL 구현은 항상 S_OK을 반환 합니다.

Windows SDK에서 [IOleInPlaceObject:: UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
