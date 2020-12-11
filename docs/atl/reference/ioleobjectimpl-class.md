---
description: '자세히 알아보기: IOleObjectImpl 클래스'
title: IOleObjectImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: a8e9fd7dc370ee3f0861ab152061e4a0b96465ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158181"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 클래스

이 클래스는를 구현 `IUnknown` 하며 컨테이너에서 컨트롤과 통신 하는 데 사용 되는 주 인터페이스입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IOleObjectImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IOleObjectImpl:: Advise](#advise)|컨트롤과의 advise 연결을 설정 합니다.|
|[IOleObjectImpl:: Close](#close)|컨트롤 상태를 실행 중에서 로드 됨으로 변경 합니다.|
|[IOleObjectImpl::D 초과 b](#doverb)|열거 된 작업 중 하나를 수행 하도록 컨트롤에 지시 합니다.|
|[IOleObjectImpl::D oVerbDiscardUndo](#doverbdiscardundo)|유지 관리 하 고 있는 실행 취소 상태를 삭제 하도록 컨트롤에 지시 합니다.|
|[IOleObjectImpl::D 과잉 Bhide](#doverbhide)|뷰에서 사용자 인터페이스를 제거 하도록 컨트롤에 지시 합니다.|
|[IOleObjectImpl::D oVerbInPlaceActivate](#doverbinplaceactivate)|컨트롤을 실행 하 고 해당 창을 설치 하지만 컨트롤의 사용자 인터페이스를 설치 하지는 않습니다.|
|[IOleObjectImpl::D 오버 열기](#doverbopen)|별도의 창에서 컨트롤이 열려 편집 되도록 합니다.|
|[IOleObjectImpl::D 과잉 Bprimary](#doverbprimary)|사용자가 컨트롤을 두 번 클릭할 때 지정 된 작업을 수행 합니다. 컨트롤은 일반적으로 컨트롤을 내부에서 활성화 하는 작업을 정의 합니다.|
|[IOleObjectImpl::D 과다 Bshow](#doverbshow)|사용자에 게 새로 삽입 된 컨트롤을 표시 합니다.|
|[IOleObjectImpl::D 오버 활성화](#doverbuiactivate)|컨트롤을 내부에서 활성화 하 고 메뉴 및 도구 모음과 같은 컨트롤의 사용자 인터페이스를 표시 합니다.|
|[IOleObjectImpl:: EnumAdvise](#enumadvise)|컨트롤의 advise 연결을 열거 합니다.|
|[IOleObjectImpl:: EnumVerbs](#enumverbs)|컨트롤에 대 한 동작을 열거 합니다.|
|[IOleObjectImpl:: GetClientSite](#getclientsite)|컨트롤의 클라이언트 사이트를 검색 합니다.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|클립보드에서 데이터를 검색 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleObjectImpl:: GetExtent](#getextent)|컨트롤의 표시 영역 범위를 검색 합니다.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|컨트롤의 상태를 검색 합니다.|
|[IOleObjectImpl:: GetMoniker](#getmoniker)|컨트롤의 모니커를 검색 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|컨트롤의 클래스 식별자를 검색 합니다.|
|[IOleObjectImpl::GetUserType](#getusertype)|컨트롤의 사용자 형식 이름을 검색 합니다.|
|[IOleObjectImpl:: InitFromData](#initfromdata)|선택한 데이터에서 컨트롤을 초기화 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleObjectImpl:: IsUpToDate](#isuptodate)|컨트롤이 최신 상태 인지 확인 합니다. ATL 구현은 S_OK 반환 합니다.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|실행 취소 상태를 삭제 한 후 [DoVerbDiscardUndo](#doverbdiscardundo) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|컨트롤이 숨겨진 후 [DoVerbHide](#doverbhide) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|컨트롤이 현재 활성화 된 후 [DoVerbInPlaceActivate](#doverbinplaceactivate) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|별도의 창에서 편집 하기 위해 컨트롤이 열린 후 [DoVerbOpen](#doverbopen) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|컨트롤이 표시 된 후 [DoVerbShow](#doverbshow) 에서 호출 됩니다.|
|[IOleObjectImpl:: OnPostVerbUIActivate](#onpostverbuiactivate)|컨트롤의 사용자 인터페이스가 활성화 된 후 [Doverstactivate](#doverbuiactivate) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|실행 취소 상태를 삭제 하기 전에 [DoVerbDiscardUndo](#doverbdiscardundo) 에 의해 호출 됩니다.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|컨트롤이 숨겨지도록 [DoVerbHide](#doverbhide) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|컨트롤이 현재 활성화 되기 전에 [DoVerbInPlaceActivate](#doverbinplaceactivate) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|별도의 창에서 편집 하기 위해 컨트롤이 열리기 전에 [DoVerbOpen](#doverbopen) 에서 호출 됩니다.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|컨트롤이 표시 되기 전에 [DoVerbShow](#doverbshow) 에 의해 호출 됩니다.|
|[IOleObjectImpl:: OnPreVerbUIActivate](#onpreverbuiactivate)|컨트롤의 사용자 인터페이스가 활성화 되기 전에 [Doverbuiactivate](#doverbuiactivate) 에서 호출 됩니다.|
|[IOleObjectImpl:: SetClientSite](#setclientsite)|컨테이너의 클라이언트 사이트에 대해 컨트롤에 지시 합니다.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|컨트롤의 응용 프로그램에 색 구성표를 권장 합니다 (있는 경우). ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleObjectImpl:: SetExtent](#setextent)|컨트롤의 표시 영역 범위를 설정 합니다.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|컨테이너 응용 프로그램 및 컨테이너 문서의 이름을 컨트롤에 알립니다.|
|[IOleObjectImpl:: SetMoniker](#setmoniker)|컨트롤의 모니커가 무엇 인지를 컨트롤에 알립니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleObjectImpl:: Unadvise](#unadvise)|컨트롤과의 advise 연결을 삭제 합니다.|
|[IOleObjectImpl:: Update](#update)|컨트롤을 업데이트 합니다. ATL 구현은 S_OK 반환 합니다.|

## <a name="remarks"></a>설명

[IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) 인터페이스는 컨테이너가 컨트롤과 통신 하는 데 사용 하는 주 인터페이스입니다. 클래스는 `IOleObjectImpl` 이 인터페이스의 기본 구현을 제공 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a> IOleObjectImpl:: Advise

컨트롤과의 advise 연결을 설정 합니다.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>설명

Windows SDK [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) 를 참조 하세요.

## <a name="ioleobjectimplclose"></a><a name="close"></a> IOleObjectImpl:: Close

컨트롤 상태를 실행 중에서 로드 됨으로 변경 합니다.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>설명

컨트롤을 비활성화 하 고 컨트롤 창이 있으면 소멸 시킵니다. 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) 이 TRUE이 고 *dwsaveoption* 매개 변수가 OLECLOSE_SAVEIFDIRTY 또는 OLECLOSE_PROMPTSAVE 인 경우 닫기 전에 컨트롤 속성이 저장 됩니다.

컨트롤 클래스 데이터 멤버 [CComControlBase:: m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) 및 [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) 에 있는 포인터가 해제 되 고 데이터 멤버 [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase:: M_BWNDLESS](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)및 [CComControlBase:: m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) 가 FALSE로 설정 됩니다.

Windows SDK [IOleObject:: Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) 를 참조 하세요.

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a> IOleObjectImpl::D 초과 b

열거 된 작업 중 하나를 수행 하도록 컨트롤에 지시 합니다.

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>설명

의 값에 따라 다음과 `iVerb` `DoVerb` 같이 ATL 도우미 함수 중 하나가 호출 됩니다.

|*Iverb* 기본값|DoVerb 도우미 함수가 호출 되었습니다.|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Windows SDK에서 [IOleObject::D 초과 b](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 를 참조 하세요.

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a> IOleObjectImpl::D oVerbDiscardUndo

유지 관리 하 고 있는 실행 취소 상태를 삭제 하도록 컨트롤에 지시 합니다.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
진행 컨테이너에서 컨트롤이 그리기를 원하는 사각형에 대 한 포인터입니다.

*hwndParent*<br/>
진행 컨트롤을 포함 하는 창의 핸들입니다.

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a> IOleObjectImpl::D 과잉 Bhide

컨트롤의 사용자 인터페이스를 비활성화 하 고 제거 하 고 컨트롤을 숨깁니다.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
진행 컨테이너에서 컨트롤이 그리기를 원하는 사각형에 대 한 포인터입니다.

*hwndParent*<br/>
진행 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a> IOleObjectImpl::D oVerbInPlaceActivate

컨트롤을 실행 하 고 해당 창을 설치 하지만 컨트롤의 사용자 인터페이스를 설치 하지는 않습니다.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
진행 컨테이너에서 컨트롤이 그리기를 원하는 사각형에 대 한 포인터입니다.

*hwndParent*<br/>
진행 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

[CComControlBase:: InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)를 호출 하 여 컨트롤을 활성화 합니다. 컨트롤 클래스의 데이터 멤버가 `m_bWindowOnly` TRUE가 아니면 `DoVerbInPlaceActivate` 먼저 컨트롤을 창 없는 컨트롤로 활성화 하려고 시도 합니다 (컨테이너가 [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)을 지 원하는 경우에만 가능). 이 작업이 실패 하면 함수는 확장 된 기능을 사용 하 여 컨트롤을 활성화 하려고 시도 합니다 (컨테이너가 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)을 지 원하는 경우에만 가능). 이 작업이 실패 하면 함수는 확장 된 기능 없이 컨트롤을 활성화 하려고 시도 합니다 (컨테이너가 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)을 지 원하는 경우에만 가능). 활성화가 성공 하면 함수는 컨트롤이 활성화 되었음을 컨테이너에 알립니다.

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a> IOleObjectImpl::D 오버 열기

별도의 창에서 컨트롤이 열려 편집 되도록 합니다.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
진행 컨테이너에서 컨트롤이 그리기를 원하는 사각형에 대 한 포인터입니다.

*hwndParent*<br/>
진행 컨트롤을 포함 하는 창의 핸들입니다.

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a> IOleObjectImpl::D 과잉 Bprimary

사용자가 컨트롤을 두 번 클릭할 때 수행 되는 동작을 정의 합니다.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
진행 컨테이너에서 컨트롤이 그리기를 원하는 사각형에 대 한 포인터입니다.

*hwndParent*<br/>
진행 컨트롤을 포함 하는 창의 핸들입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

기본적으로 속성 페이지를 표시 하려면를 설정 합니다. 두 번 클릭 시 다른 동작을 호출 하도록 컨트롤 클래스에서이를 재정의할 수 있습니다. 예를 들어 비디오를 재생 하거나 내부 활성 상태로 전환 합니다.

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a> IOleObjectImpl::D 과다 Bshow

컨테이너에 컨트롤을 표시 하도록 지시 합니다.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
진행 컨테이너에서 컨트롤이 그리기를 원하는 사각형에 대 한 포인터입니다.

*hwndParent*<br/>
진행 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a> IOleObjectImpl::D 오버 활성화

컨트롤의 사용자 인터페이스를 활성화 하 고 해당 메뉴가 복합 메뉴로 대체 중임을 컨테이너에 알립니다.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
진행 컨테이너에서 컨트롤이 그리기를 원하는 사각형에 대 한 포인터입니다.

*hwndParent*<br/>
진행 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a> IOleObjectImpl:: EnumAdvise

이 컨트롤에 대해 등록 된 advise 연결의 열거형을 제공 합니다.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>설명

Windows SDK [IOleObject:: EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) 를 참조 하세요.

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a> IOleObjectImpl:: EnumVerbs

을 호출 하 여이 컨트롤에 대해 등록 된 작업 (동사)의 열거형을 제공 `OleRegEnumVerbs` 합니다.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>설명

프로젝트의 .rgs 파일에 동사를 추가할 수 있습니다. 예를 들어 CIRCCTL를 참조 하세요. [CIRC](../../overview/visual-cpp-samples.md) 샘플의 RGS

Windows SDK [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) 를 참조 하세요.

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a> IOleObjectImpl:: GetClientSite

컨트롤 클래스 데이터 멤버 [CComControlBase:: m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) 의 포인터를 *ppclientsite* 에 넣고 포인터의 참조 횟수를 증가 시킵니다.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>설명

Windows SDK [IOleObject:: GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) 를 참조 하세요.

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a> IOleObjectImpl::GetClipboardData

클립보드에서 데이터를 검색 합니다.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleObject:: GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) 를 참조 하세요.

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a> IOleObjectImpl:: GetExtent

실행 중인 컨트롤의 표시 크기를 HIMETRIC unit (단위당 0.01 밀리미터)으로 검색 합니다.

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>설명

크기는 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)에 저장 됩니다.

Windows SDK에서 [IOleObject:: GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) 를 참조 하세요.

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a> IOleObjectImpl::GetMiscStatus

을 호출 하 여 컨트롤에 대 한 등록 된 상태 정보에 대 한 포인터를 반환 `OleRegGetMiscStatus` 합니다.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>설명

상태 정보에는 컨트롤 및 프레젠테이션 데이터에서 지 원하는 동작이 포함 됩니다. 프로젝트의 .rgs 파일에 상태 정보를 추가할 수 있습니다.

Windows SDK에서 [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) 를 참조 하세요.

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a> IOleObjectImpl:: GetMoniker

컨트롤의 모니커를 검색 합니다.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleObject:: GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) 를 참조 하세요.

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a> IOleObjectImpl::GetUserClassID

컨트롤의 클래스 식별자를 반환 합니다.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IOleObject:: GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) 를 참조 하세요.

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a> IOleObjectImpl::GetUserType

을 호출 하 여 컨트롤의 사용자 형식 이름을 반환 합니다 `OleRegGetUserType` .

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>설명

사용자 형식 이름은 메뉴 및 대화 상자와 같은 사용자 인터페이스 요소에 표시 하는 데 사용 됩니다. 프로젝트의 .rgs 파일에서 사용자 형식 이름을 변경할 수 있습니다.

Windows SDK에서 [IOleObject:: GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) 를 참조 하세요.

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a> IOleObjectImpl:: InitFromData

선택한 데이터에서 컨트롤을 초기화 합니다.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) 를 참조 하세요.

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a> IOleObjectImpl:: IsUpToDate

컨트롤이 최신 상태 인지 확인 합니다.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleObject:: IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) 를 참조 하세요.

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a> IOleObjectImpl::OnPostVerbDiscardUndo

실행 취소 상태를 삭제 한 후 [DoVerbDiscardUndo](#doverbdiscardundo) 에서 호출 됩니다.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

실행 취소 상태를 삭제 한 후에 실행 하려는 코드를 사용 하 여이 메서드를 재정의 합니다.

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a> IOleObjectImpl::OnPostVerbHide

컨트롤이 숨겨진 후 [DoVerbHide](#doverbhide) 에서 호출 됩니다.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 숨겨진 후에 실행 하려는 코드를 사용 하 여이 메서드를 재정의 합니다.

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a> IOleObjectImpl::OnPostVerbInPlaceActivate

컨트롤이 현재 활성화 된 후 [DoVerbInPlaceActivate](#doverbinplaceactivate) 에서 호출 됩니다.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 현재 활성화 된 후에 실행 하려는 코드를 사용 하 여이 메서드를 재정의 합니다.

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a> IOleObjectImpl::OnPostVerbOpen

별도의 창에서 편집 하기 위해 컨트롤이 열린 후 [DoVerbOpen](#doverbopen) 에서 호출 됩니다.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

별도의 창에서 편집 하기 위해 컨트롤이 열린 후에 실행 하려는 코드를 사용 하 여이 메서드를 재정의 합니다.

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a> IOleObjectImpl::OnPostVerbShow

컨트롤이 표시 된 후 [DoVerbShow](#doverbshow) 에서 호출 됩니다.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 표시 된 후에 실행 하려는 코드를 사용 하 여이 메서드를 재정의 합니다.

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a> IOleObjectImpl:: OnPostVerbUIActivate

컨트롤의 사용자 인터페이스가 활성화 된 후 [Doverstactivate](#doverbuiactivate) 에서 호출 됩니다.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤의 사용자 인터페이스가 활성화 된 후에 실행 하려는 코드를 사용 하 여이 메서드를 재정의 합니다.

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a> IOleObjectImpl::OnPreVerbDiscardUndo

실행 취소 상태를 삭제 하기 전에 [DoVerbDiscardUndo](#doverbdiscardundo) 에 의해 호출 됩니다.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

실행 취소 상태가 삭제 되지 않도록 하려면이 메서드를 재정의 하 여 오류 HRESULT를 반환 합니다.

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a> IOleObjectImpl::OnPreVerbHide

컨트롤이 숨겨지도록 [DoVerbHide](#doverbhide) 에서 호출 됩니다.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 숨겨지지 않도록 하려면이 메서드를 재정의 하 여 오류 HRESULT를 반환 합니다.

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a> IOleObjectImpl::OnPreVerbInPlaceActivate

컨트롤이 현재 활성화 되기 전에 [DoVerbInPlaceActivate](#doverbinplaceactivate) 에서 호출 됩니다.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 현재 활성화 되지 않도록 하려면이 메서드를 재정의 하 여 오류 HRESULT를 반환 합니다.

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a> IOleObjectImpl::OnPreVerbOpen

별도의 창에서 편집 하기 위해 컨트롤이 열리기 전에 [DoVerbOpen](#doverbopen) 에서 호출 됩니다.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

별도의 창에서 편집 하기 위해 컨트롤이 열리지 않도록 하려면이 메서드를 재정의 하 여 오류 HRESULT를 반환 합니다.

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a> IOleObjectImpl::OnPreVerbShow

컨트롤이 표시 되기 전에 [DoVerbShow](#doverbshow) 에 의해 호출 됩니다.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 표시 되지 않도록 하려면이 메서드를 재정의 하 여 오류 HRESULT를 반환 합니다.

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a> IOleObjectImpl:: OnPreVerbUIActivate

컨트롤의 사용자 인터페이스가 활성화 되기 전에 [Doverbuiactivate](#doverbuiactivate) 에서 호출 됩니다.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤의 사용자 인터페이스가 활성화 되지 않도록 하려면이 메서드를 재정의 하 여 오류 HRESULT를 반환 합니다.

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a> IOleObjectImpl:: SetClientSite

컨테이너의 클라이언트 사이트에 대해 컨트롤에 지시 합니다.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>설명

그런 다음 메서드는 S_OK 반환 합니다.

Windows SDK [IOleObject:: SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) 를 참조 하세요.

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a> IOleObjectImpl::SetColorScheme

컨트롤의 응용 프로그램에 색 구성표를 권장 합니다 (있는 경우).

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 를 참조 하세요.

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a> IOleObjectImpl:: SetExtent

컨트롤의 표시 영역 범위를 설정 합니다.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>설명

그렇지 않으면는 `SetExtent` `psizel` 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)에 의해 가리키는 값을 저장 합니다. 이 값은 HIMETRIC 단위 (0.01 밀리미터/단위)로 되어 있습니다.

컨트롤 클래스 데이터 멤버 [CComControlBase:: m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) 이 TRUE 이면에서 `SetExtent` 가리키는 값을 `psizel` 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)에도 저장 합니다.

컨트롤 클래스 데이터 멤버 [CComControlBase:: m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) 이 TRUE 이면 및를 `SetExtent` 호출 `SendOnDataChange` `SendOnViewChange` 하 여 컨트롤 크기가 변경 된 advise 소유자에 등록 된 모든 advise 싱크에 알립니다.

Windows SDK [IOleObject:: SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) 를 참조 하세요.

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a> IOleObjectImpl::SetHostNames

컨테이너 응용 프로그램 및 컨테이너 문서의 이름을 컨트롤에 알립니다.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleObject:: SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) 를 참조 하세요.

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a> IOleObjectImpl:: SetMoniker

컨트롤의 모니커가 무엇 인지를 컨트롤에 알립니다.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK [IOleObject:: SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) 를 참조 하세요.

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a> IOleObjectImpl:: Unadvise

컨트롤 클래스의 데이터 멤버에 저장 된 advise 연결을 삭제 합니다 `m_spOleAdviseHolder` .

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) 를 참조 하세요.

## <a name="ioleobjectimplupdate"></a><a name="update"></a> IOleObjectImpl:: Update

컨트롤을 업데이트 합니다.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK [IOleObject:: Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) 를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 컨트롤 인터페이스](/windows/win32/com/activex-controls-interfaces)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
