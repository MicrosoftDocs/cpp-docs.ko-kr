---
description: '자세히 알아보기: IViewObjectExImpl 클래스'
title: IViewObjectExImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 16b6f4a94635410f777e5c34e794ca425d38c466
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139102"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 클래스

이 클래스 `IUnknown` 는을 구현 하 고 [Iviewobject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)및 [iviewobjectex](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) 인터페이스의 기본 구현을 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IViewObjectExImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IViewObjectExImpl::D raw](#draw)|컨트롤의 표현을 장치 컨텍스트에 그립니다.|
|[IViewObjectExImpl:: Freeze](#freeze)|가 될 때까지 변경 되지 않도록 컨트롤의 그리기 표현을 고정 합니다 `Unfreeze` . ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IViewObjectExImpl:: GetAdvise](#getadvise)|컨트롤의 기존 advise 싱크 연결 (있는 경우)을 검색 합니다.|
|[IViewObjectExImpl:: GetColorSet](#getcolorset)|컨트롤에서 그리기에 사용 하는 논리 색상표를 반환 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IViewObjectExImpl:: GetExtent](#getextent)|컨트롤 클래스 데이터 멤버 [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)에서 컨트롤의 표시 크기 (단위당 0.01 밀리미터)를 검색 합니다.|
|[IViewObjectExImpl:: GetNaturalExtent](#getnaturalextent)|사용자가 크기를 조정할 때 사용할 개체의 컨테이너에서 크기 조정 힌트를 제공 합니다.|
|[IViewObjectExImpl:: GetRect](#getrect)|요청한 그리기 모양을 설명 하는 사각형을 반환 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IViewObjectExImpl:: GetViewStatus](#getviewstatus)|개체의 불투명도와 지원 되는 그리기 요소에 대 한 정보를 반환 합니다.|
|[IViewObjectExImpl:: QueryHitPoint](#queryhitpoint)|지정 된 점이 지정 된 사각형에 있는지 확인 하 고에서 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 값을 반환 `pHitResult` 합니다.|
|[IViewObjectExImpl:: QueryHitRect](#queryhitrect)|컨트롤의 표시 사각형이 지정 된 위치 사각형의 모든 지점과 겹치면에서 HITRESULT 값을 반환 하는지 여부를 확인 `pHitResult` 합니다.|
|[IViewObjectExImpl:: SetAdvise](#setadvise)|컨트롤과 advise 싱크 간의 연결을 설정 하 여 싱크에 컨트롤 뷰의 변경 내용에 대 한 정보를 알릴 수 있도록 합니다.|
|[IViewObjectExImpl:: 고정 취소](#unfreeze)|컨트롤의 그려진 표시를 중지 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|

## <a name="remarks"></a>설명

[Iviewobject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)및 [iviewobjectex](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) 인터페이스를 사용 하면 컨트롤이 자신을 직접 표시 하 고 advise 싱크를 만들고 관리 하 여 컨트롤 표시의 변경 내용을 컨테이너에 알릴 수 있습니다. `IViewObjectEx`인터페이스는 깜박임 없는 그리기, 사각형이 아닌 투명 한 컨트롤 및 적중 테스트와 같은 확장 컨트롤 기능을 지원 합니다 (예: 컨트롤에서 마우스 클릭을 닫기 위해 고려해 야 하는 방법). 클래스는 `IViewObjectExImpl` 이러한 인터페이스의 기본 구현을 제공 하 고 `IUnknown` 디버그 빌드에서 덤프 장치로 정보를 전송 하 여를 구현 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a> IViewObjectExImpl::D raw

컨트롤의 표현을 장치 컨텍스트에 그립니다.

```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```

### <a name="remarks"></a>설명

이 메서드는를 호출 `CComControl::OnDrawAdvanced` 하 여 컨트롤 클래스의 메서드를 호출 `OnDraw` 합니다. `OnDraw`ATL 컨트롤 마법사를 사용 하 여 컨트롤을 만들 때 메서드는 컨트롤 클래스에 자동으로 추가 됩니다. 마법사의 기본값은 `OnDraw` "ATL 3.0" 라는 레이블이 있는 사각형을 그립니다.

Windows SDK에서 [Iviewobject: raw:D](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) 를 참조 하세요.

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a> IViewObjectExImpl:: Freeze

가 될 때까지 변경 되지 않도록 컨트롤의 그리기 표현을 고정 합니다 `Unfreeze` . ATL 구현은 E_NOTIMPL 반환 합니다.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>설명

Windows SDK [Iviewobject:: Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) 를 참조 하세요.

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a> IViewObjectExImpl:: GetAdvise

컨트롤의 기존 advise 싱크 연결 (있는 경우)을 검색 합니다.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>설명

Advise 싱크는 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)에 저장 됩니다.

Windows SDK에서 [Iviewobject:: GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) 를 참조 하세요.

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a> IViewObjectExImpl:: GetColorSet

컨트롤에서 그리기에 사용 하는 논리 색상표를 반환 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.

```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```

### <a name="remarks"></a>설명

Windows SDK에서 [Iviewobject:: GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) 를 참조 하세요.

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a> IViewObjectExImpl:: GetExtent

컨트롤 클래스 데이터 멤버 [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)에서 컨트롤의 표시 크기 (단위당 0.01 밀리미터)를 검색 합니다.

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>설명

Windows SDK에서 [IViewObject2:: GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) 를 참조 하세요.

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a> IViewObjectExImpl:: GetNaturalExtent

사용자가 크기를 조정할 때 사용할 개체의 컨테이너에서 크기 조정 힌트를 제공 합니다.

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>설명

`dwAspect`가 DVASPECT_CONTENT이 고 *>pExtentInfo dwExtentMode* 이 DVEXTENT_CONTENT 인 경우는 *를 `psizel` 컨트롤 클래스의 데이터 멤버 [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)로 설정 합니다. 그렇지 않으면 오류 HRESULT를 반환 합니다.

Windows SDK에서 [Iviewobjectex:: GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) 를 참조 하세요.

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a> IViewObjectExImpl:: GetRect

요청한 그리기 모양을 설명 하는 사각형을 반환 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>설명

Windows SDK에서 [Iviewobjectex:: GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) 를 참조 하세요.

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a> IViewObjectExImpl:: GetViewStatus

개체의 불투명도와 지원 되는 그리기 요소에 대 한 정보를 반환 합니다.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>설명

기본적으로 ATL `pdwStatus` 은 컨트롤이 VIEWSTATUS_OPAQUE 지원함을 나타내기 위해를 설정 합니다 (가능한 값은 [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) 열거형에 있음).

Windows SDK에서 [Iviewobjectex:: GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) 를 참조 하세요.

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a> IViewObjectExImpl:: QueryHitPoint

지정 된 점이 지정 된 사각형에 있는지 확인 하 고에서 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 값을 반환 `pHitResult` 합니다.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>설명

값은 HITRESULT_HIT 또는 HITRESULT_OUTSIDE 일 수 있습니다.

`dwAspect`가 [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)와 같으면이 메서드는 S_OK 반환 합니다. 그렇지 않으면 메서드는 E_FAIL 반환 합니다.

Windows SDK에서 [Iviewobjectex:: QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) 를 참조 하세요.

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a> IViewObjectExImpl:: QueryHitRect

컨트롤의 표시 사각형이 지정 된 위치 사각형의 모든 지점과 겹치면에서 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 값을 반환 하는지 여부를 확인 `pHitResult` 합니다.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>설명

값은 HITRESULT_HIT 또는 HITRESULT_OUTSIDE 일 수 있습니다.

`dwAspect`가 [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)와 같으면이 메서드는 S_OK 반환 합니다. 그렇지 않으면 메서드는 E_FAIL 반환 합니다.

Windows SDK에서 [Iviewobjectex:: QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) 를 참조 하세요.

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a> IViewObjectExImpl:: SetAdvise

컨트롤과 advise 싱크 간의 연결을 설정 하 여 싱크에 컨트롤 뷰의 변경 내용에 대 한 정보를 알릴 수 있도록 합니다.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>설명

Advise 싱크에 있는 [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) 인터페이스에 대 한 포인터는 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)에 저장 됩니다.

Windows SDK에서 [Iviewobject:: SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) 를 참조 하세요.

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a> IViewObjectExImpl:: 고정 취소

컨트롤의 그려진 표시를 중지 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>설명

Windows SDK [Iviewobject:: 고정](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) 해제를 참조 하세요.

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a> IWorkerThreadClient:: CloseHandle

이 개체와 연결 된 핸들을 닫으려면이 메서드를 구현 합니다.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>매개 변수

*hHandle*<br/>
닫을 핸들입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 반환 하거나 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드에 전달 된 핸들은 이전에 [C이상 스레드:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)을 호출 하 여이 개체와 연결 되었습니다.

### <a name="example"></a>예제

다음 코드에서는의 간단한 구현을 보여 줍니다 `IWorkerThreadClient::CloseHandle` .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a> IWorkerThreadClient:: Execute

이 개체와 연결 된 핸들이 신호를 받을 때 코드를 실행 하려면이 메서드를 구현 합니다.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>매개 변수

*dwParam*<br/>
사용자 매개 변수입니다.

*hObject*<br/>
신호를 받은 핸들입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 반환 하거나 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드에 전달 된 핸들 및 DWORD/포인터는 이전에 [C이상 thread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)을 호출 하 여이 개체와 연결 되었습니다.

### <a name="example"></a>예제

다음 코드에서는의 간단한 구현을 보여 줍니다 `IWorkerThreadClient::Execute` .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 컨트롤 인터페이스](/windows/win32/com/activex-controls-interfaces)<br/>
[자습서](../../atl/active-template-library-atl-tutorial.md)<br/>
[ATL 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
