---
title: IOleObjectImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a98d3e0ad75d2eaa0325699369bfe4473182049
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366197"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 클래스
이 클래스는 구현 **IUnknown** 컨트롤과 컨테이너 통신 하는 주 인터페이스입니다.  
  
> [!IMPORTANT]
>  이 클래스 및 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 파생 된 클래스에 `IOleObjectImpl`합니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|컨트롤에서 권장 된 연결을 설정합니다.|  
|[IOleObjectImpl::Close](#close)|실행을 로드 컨트롤 상태를 변경 합니다.|  
|[IOleObjectImpl::DoVerb](#doverb)|열거 작업 중 하나를 수행 하려면 컨트롤에 알립니다.|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|컨트롤 여전히 활성 상태가 유지 관리 하는 것을 지시 합니다.|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|보기에서 해당 사용자 인터페이스를 제거 하려면 컨트롤에 알립니다.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|컨트롤을 실행 하 고 해당 창을 설치 되지만 컨트롤의 사용자 인터페이스를 설치 하지 않습니다.|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|사용 하면 오픈 편집 별도 창에서 수를 제어 합니다.|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|컨트롤을 두 번 클릭할 때 지정된 된 작업을 수행 합니다. 컨트롤의 컨트롤 내부 활성화를 일반적으로 작업을 정의 합니다.|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|사용자에 게 새로 삽입된 된 컨트롤을 보여줍니다.|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|컨트롤의 내부에서 활성화 되 고 같은 메뉴 및 도구 모음 컨트롤의 사용자 인터페이스를 보여 줍니다.|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|컨트롤의 자문 연결을 열거합니다.|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|컨트롤에 대 한 작업을 열거합니다.|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|컨트롤의 클라이언트 사이트를 검색합니다.|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|클립보드의 데이터를 검색합니다. ATL 구현은 **E_NOTIMPL**합니다.|  
|[IOleObjectImpl::GetExtent](#getextent)|컨트롤의 표시 영역 범위를 검색합니다.|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|컨트롤의 상태를 검색 합니다.|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|컨트롤의 모니커를 검색합니다. ATL 구현은 **E_NOTIMPL**합니다.|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|컨트롤의 클래스 식별자를 검색합니다.|  
|[IOleObjectImpl::GetUserType](#getusertype)|컨트롤의 사용자 형식 이름을 검색합니다.|  
|[IOleObjectImpl::InitFromData](#initfromdata)|선택한 데이터에서 컨트롤을 초기화합니다. ATL 구현은 **E_NOTIMPL**합니다.|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|컨트롤 최신 상태 인지 확인 합니다. ATL 구현은 `S_OK`합니다.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|에 의해 호출 [DoVerbDiscardUndo](#doverbdiscardundo) 후 실행 취소 상태는 삭제 됩니다.|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|에 의해 호출 [DoVerbHide](#doverbhide) 후 컨트롤을 숨깁니다.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|에 의해 호출 [DoVerbInPlaceActivate](#doverbinplaceactivate) 컨트롤 위치에 활성화 된 후입니다.|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|에 의해 호출 [DoVerbOpen](#doverbopen) 컨트롤을 연 후에 별도 창에서 편집 합니다.|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|에 의해 호출 [DoVerbShow](#doverbshow) 만들어지면 컨트롤 표시 합니다.|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|에 의해 호출 [DoVerbUIActivate](#doverbuiactivate) 컨트롤의 사용자 인터페이스를 활성화 합니다.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|에 의해 호출 [DoVerbDiscardUndo](#doverbdiscardundo) 실행 취소 하기 전에 상태는 삭제 됩니다.|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|에 의해 호출 [DoVerbHide](#doverbhide) 전에 컨트롤을 숨깁니다.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|에 의해 호출 [DoVerbInPlaceActivate](#doverbinplaceactivate) 컨트롤 위치에서 활성화 되기 전에 합니다.|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|에 의해 호출 [DoVerbOpen](#doverbopen) 전에 컨트롤 별도 창에서 편집을 위해 열려 있습니다.|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|에 의해 호출 [DoVerbShow](#doverbshow) 컨트롤이 되기 전에 표시 합니다.|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|에 의해 호출 [DoVerbUIActivate](#doverbuiactivate) 전에 컨트롤의 사용자 인터페이스를 활성화 합니다.|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|컨테이너에서의 클라이언트 사이트에 대 한 컨트롤에 알립니다.|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|있는 경우에 컨트롤의 응용 프로그램에 색 구성표를 권장 합니다. ATL 구현은 **E_NOTIMPL**합니다.|  
|[IOleObjectImpl::SetExtent](#setextent)|컨트롤의 표시 영역 범위를 설정합니다.|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|컨테이너 문서 컨테이너 응용 프로그램의 이름과 컨트롤에 알립니다.|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|해당 모니커 란 컨트롤에 알립니다. ATL 구현은 **E_NOTIMPL**합니다.|  
|[IOleObjectImpl::Unadvise](#unadvise)|컨트롤에서 권장 된 연결을 삭제합니다.|  
|[IOleObjectImpl::Update](#update)|컨트롤을 업데이트합니다. ATL 구현은 `S_OK`합니다.|  
  
## <a name="remarks"></a>설명  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) 인터페이스는 컨트롤과 컨테이너 통신 하는 주 인터페이스입니다. 클래스 `IOleObjectImpl` 이 인터페이스의 기본 구현을 제공 하 고 구현 **IUnknown** 디버그에서 장치 정보 덤프를 전송 하 여 빌드합니다.  
  
 **관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [ATL 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlctl.h  
  
##  <a name="advise"></a>  IOleObjectImpl::Advise  
 컨트롤에서 권장 된 연결을 설정합니다.  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) in the Windows SDK입니다.  
  
##  <a name="close"></a>  IOleObjectImpl::Close  
 실행을 로드 컨트롤 상태를 변경 합니다.  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>설명  
 컨트롤을 비활성화 하 고 있는 경우 제어 창을 제거 합니다. 컨트롤 클래스 데이터 멤버 경우 [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) 은 **TRUE** 및 `dwSaveOption` 매개 변수가 `OLECLOSE_SAVEIFDIRTY` 또는 `OLECLOSE_PROMPTSAVE`, 컨트롤 속성이 저장 됩니다 닫아야 합니다.  
  
 컨트롤 클래스 데이터 멤버에 대 한 포인터 보유할 [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) 및 [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) 출시 되 면 데이터 멤버 및 [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), 및 [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) 로 설정 **FALSE**합니다.  
  
 참조 [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) in the Windows SDK입니다.  
  
##  <a name="doverb"></a>  IOleObjectImpl::DoVerb  
 열거 작업 중 하나를 수행 하려면 컨트롤에 알립니다.  
  
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
 값에 따라 `iVerb`, ATL 중 하나 `DoVerb` 도우미 함수를 다음과 같이 호출 됩니다.  
  
|*iVerb* 값|라는 DoVerb 도우미 함수|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 참조 [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) in the Windows SDK입니다.  
  
##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo  
 컨트롤 여전히 활성 상태가 유지 관리 하는 것을 지시 합니다.  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>매개 변수  
 `prcPosRec`  
 [in] 사각형 컨테이너에 대 한 포인터에 제어를 하려고 합니다.  
  
 *hwndParent*  
 [in] 컨트롤을 포함 하는 창의 핸들입니다.  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide  
 비활성화 하 고 컨트롤의 사용자 인터페이스를 제거 하 고 컨트롤을 숨깁니다.  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>매개 변수  
 `prcPosRec`  
 [in] 사각형 컨테이너에 대 한 포인터에 제어를 하려고 합니다.  
  
 *hwndParent*  
 [in] 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate  
 컨트롤을 실행 하 고 해당 창을 설치 되지만 컨트롤의 사용자 인터페이스를 설치 하지 않습니다.  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>매개 변수  
 `prcPosRec`  
 [in] 사각형 컨테이너에 대 한 포인터에 제어를 하려고 합니다.  
  
 *hwndParent*  
 [in] 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.  
  
### <a name="return-value"></a>반환 값  
 표준 중 하나 `HRESULT` 값입니다.  
  
### <a name="remarks"></a>설명  
 호출 하 여 위치에 컨트롤을 활성화 [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)합니다. 하지 않는 한 컨트롤 클래스의 데이터 멤버 `m_bWindowOnly` 은 **TRUE**, `DoVerbInPlaceActivate` 창 없는 컨트롤로 컨트롤을 활성화 하려면 먼저 시도 (컨테이너에서 지 원하는 경우에 가능한 [IOleInPlaceSiteWindowless ](http://msdn.microsoft.com/library/windows/desktop/ms682300)). 함수 확장된 기능을 사용 하 여 컨트롤을 활성화 하려고 실패할 경우 (컨테이너에서 지 원하는 경우에 가능한 [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)). 함수 확장 기능이 없는 컨트롤을 활성화 하려고 실패할 경우 (컨테이너에서 지 원하는 경우에 가능한 [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)). 정품 인증에 성공 하는 경우 함수가 알립니다 컨테이너 컨트롤 활성화 되었습니다.  
  
##  <a name="doverbopen"></a>  IOleObjectImpl::DoVerbOpen  
 사용 하면 오픈 편집 별도 창에서 수를 제어 합니다.  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>매개 변수  
 `prcPosRec`  
 [in] 사각형 컨테이너에 대 한 포인터에 제어를 하려고 합니다.  
  
 *hwndParent*  
 [in] 컨트롤을 포함 하는 창의 핸들입니다.  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
##  <a name="doverbprimary"></a>  IOleObjectImpl::DoVerbPrimary  
 컨트롤을 두 번 클릭할 때 수행할 동작을 정의 합니다.  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>매개 변수  
 `prcPosRec`  
 [in] 사각형 컨테이너에 대 한 포인터에 제어를 하려고 합니다.  
  
 *hwndParent*  
 [in] 컨트롤을 포함 하는 창의 핸들입니다.  
  
### <a name="return-value"></a>반환 값  
 표준 중 하나 `HRESULT` 값입니다.  
  
### <a name="remarks"></a>설명  
 기본적으로 속성 페이지를 표시 하도록 설정 합니다. 이 두 번 클릭;에 다른 동작을 호출 하려면 컨트롤 클래스에서 재정의할 수 있습니다. 예를 들어, 비디오를 재생 하거나 내부 활성화를 이동 합니다.  
  
##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow  
 컨트롤을 표시 하려면 컨테이너에 지시 합니다.  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>매개 변수  
 `prcPosRec`  
 [in] 사각형 컨테이너에 대 한 포인터에 제어를 하려고 합니다.  
  
 *hwndParent*  
 [in] 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.  
  
### <a name="return-value"></a>반환 값  
 표준 중 하나 `HRESULT` 값입니다.  
  
##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate  
 컨트롤의 사용자 인터페이스를 활성화 하 고 복합 메뉴가 해당 메뉴를 대체 되 고는 컨테이너에 알립니다.  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>매개 변수  
 `prcPosRec`  
 [in] 사각형 컨테이너에 대 한 포인터에 제어를 하려고 합니다.  
  
 *hwndParent*  
 [in] 컨트롤을 포함 하는 창의 핸들입니다. ATL 구현에서 사용 되지 않습니다.  
  
### <a name="return-value"></a>반환 값  
 표준 중 하나 `HRESULT` 값입니다.  
  
##  <a name="enumadvise"></a>  IOleObjectImpl::EnumAdvise  
 이 컨트롤에 대 한 등록된 자문 연결의 열거형을 제공합니다.  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) in the Windows SDK입니다.  
  
##  <a name="enumverbs"></a>  IOleObjectImpl::EnumVerbs  
 호출 하 여이 컨트롤에 대 한 등록된 작업 (동사) 열거 제공 **OleRegEnumVerbs**합니다.  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>설명  
 프로젝트의.rgs 파일에 동사를 추가할 수 있습니다. 예를 들어 CIRCCTL를 참조 하십시오. 에 대 한 RGS는 [CIRC](../../visual-cpp-samples.md) 샘플.  
  
 참조 [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) in the Windows SDK입니다.  
  
##  <a name="getclientsite"></a>  IOleObjectImpl::GetClientSite  
 컨트롤 클래스 데이터 멤버에 포인터를 놓습니다 [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) 에 *ppClientSite* 포인터의 참조 횟수를 증가 시킵니다.  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) in the Windows SDK입니다.  
  
##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData  
 클립보드의 데이터를 검색합니다.  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>반환 값  
 반환 **E_NOTIMPL**합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) in the Windows SDK입니다.  
  
##  <a name="getextent"></a>  IOleObjectImpl::GetExtent  
 HIMETRIC 단위 (단위당 0.01 m m)에서 실행 중인 컨트롤의 표시 크기를 검색합니다.  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>설명  
 크기에서 컨트롤 클래스 데이터 멤버에 저장 된 [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)합니다.  
  
 참조 [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) in the Windows SDK입니다.  
  
##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus  
 호출 하 여 컨트롤에 대 한 등록 된 상태 정보에 대 한 포인터를 반환 **OleRegGetMiscStatus**합니다.  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>설명  
 상태 정보에는 제어 및 프레젠테이션 데이터에서 지 원하는 동작 포함 됩니다. 프로젝트의.rgs 파일에 상태 정보를 추가할 수 있습니다.  
  
 참조 [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) in the Windows SDK입니다.  
  
##  <a name="getmoniker"></a>  IOleObjectImpl::GetMoniker  
 컨트롤의 모니커를 검색합니다.  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>반환 값  
 반환 **E_NOTIMPL**합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) in the Windows SDK입니다.  
  
##  <a name="getuserclassid"></a>  IOleObjectImpl::GetUserClassID  
 컨트롤의 클래스 식별자를 반환합니다.  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) in the Windows SDK입니다.  
  
##  <a name="getusertype"></a>  IOleObjectImpl::GetUserType  
 호출 하 여 컨트롤의 사용자 형식 이름을 반환 **OleRegGetUserType**합니다.  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>설명  
 사용자 형식 이름은 메뉴 및 대화 상자와 같은 사용자 인터페이스 요소에 표시 하기 위해 사용 됩니다. 프로젝트의.rgs 파일의 사용자 형식 이름은 변경할 수 있습니다.  
  
 참조 [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) in the Windows SDK입니다.  
  
##  <a name="initfromdata"></a>  IOleObjectImpl::InitFromData  
 선택한 데이터에서 컨트롤을 초기화합니다.  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>반환 값  
 반환 **E_NOTIMPL**합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) in the Windows SDK입니다.  
  
##  <a name="isuptodate"></a>  IOleObjectImpl::IsUpToDate  
 컨트롤 최신 상태 인지 확인 합니다.  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) in the Windows SDK입니다.  
  
##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo  
 에 의해 호출 [DoVerbDiscardUndo](#doverbdiscardundo) 후 실행 취소 상태는 삭제 됩니다.  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 실행 취소 상태는 삭제 후에 실행 하려는 코드로이 메서드를 재정의 합니다.  
  
##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide  
 에 의해 호출 [DoVerbHide](#doverbhide) 후 컨트롤을 숨깁니다.  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤이 숨겨지는지 후에 실행 하려는 코드로이 메서드를 재정의 합니다.  
  
##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate  
 에 의해 호출 [DoVerbInPlaceActivate](#doverbinplaceactivate) 컨트롤 위치에 활성화 된 후입니다.  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤은 내부에서 활성화 한 후에 실행 하려는 코드로이 메서드를 재정의 합니다.  
  
##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen  
 에 의해 호출 [DoVerbOpen](#doverbopen) 컨트롤을 연 후에 별도 창에서 편집 합니다.  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤을 별도 창에서 편집을 위해 열린 후에 실행 하려는 코드로이 메서드를 재정의 합니다.  
  
##  <a name="onpostverbshow"></a>  IOleObjectImpl::OnPostVerbShow  
 에 의해 호출 [DoVerbShow](#doverbshow) 만들어지면 컨트롤 표시 합니다.  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤 표시 수행 된 후 실행을 원하는 코드로이 메서드를 재정의 합니다.  
  
##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate  
 에 의해 호출 [DoVerbUIActivate](#doverbuiactivate) 컨트롤의 사용자 인터페이스를 활성화 합니다.  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤의 사용자 인터페이스를 활성화 한 후 실행을 원하는 코드로이 메서드를 재정의 합니다.  
  
##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo  
 에 의해 호출 [DoVerbDiscardUndo](#doverbdiscardundo) 실행 취소 하기 전에 상태는 삭제 됩니다.  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 실행 취소 상태를 삭제 하지 않도록 하려면 오류 HRESULT를 반환 하려면이 메서드를 재정의 합니다.  
  
##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide  
 에 의해 호출 [DoVerbHide](#doverbhide) 전에 컨트롤을 숨깁니다.  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤이 숨겨진 되지 않도록 하려면 오류 HRESULT를 반환 하려면이 메서드를 재정의 합니다.  
  
##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate  
 에 의해 호출 [DoVerbInPlaceActivate](#doverbinplaceactivate) 컨트롤 위치에서 활성화 되기 전에 합니다.  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤에에서 활성화를 방지 하려면 오류 HRESULT를 반환 하려면이 메서드를 재정의 합니다.  
  
##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen  
 에 의해 호출 [DoVerbOpen](#doverbopen) 전에 컨트롤 별도 창에서 편집을 위해 열려 있습니다.  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤을 별도 창에서 편집을 위해 열을 방지 하려면 오류 HRESULT를 반환 하려면이 메서드를 재정의 합니다.  
  
##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow  
 에 의해 호출 [DoVerbShow](#doverbshow) 컨트롤이 되기 전에 표시 합니다.  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤 표시를 수정할를 방지 하려면 오류 HRESULT를 반환 하려면이 메서드를 재정의 합니다.  
  
##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate  
 에 의해 호출 [DoVerbUIActivate](#doverbuiactivate) 전에 컨트롤의 사용자 인터페이스를 활성화 합니다.  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 컨트롤의 사용자 인터페이스를 활성화할를 방지 하려면 오류 HRESULT를 반환 하려면이 메서드를 재정의 합니다.  
  
##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite  
 컨테이너에서의 클라이언트 사이트에 대 한 컨트롤에 알립니다.  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>설명  
 그런 다음 반환 `S_OK`합니다.  
  
 참조 [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) in the Windows SDK입니다.  
  
##  <a name="setcolorscheme"></a>  IOleObjectImpl::SetColorScheme  
 있는 경우에 컨트롤의 응용 프로그램에 색 구성표를 권장 합니다.  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>반환 값  
 반환 **E_NOTIMPL**합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) in the Windows SDK입니다.  
  
##  <a name="setextent"></a>  IOleObjectImpl::SetExtent  
 컨트롤의 표시 영역 범위를 설정합니다.  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>설명  
 그렇지 않으면 `SetExtent` 가 가리키는 값을 저장 `psizel` 컨트롤 클래스 데이터 멤버에 [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)합니다. 이 값은 HIMETRIC 단위 (단위당 0.01 m m).  
  
 컨트롤 클래스 데이터 멤버 경우 [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) 은 **TRUE**, `SetExtent` 또한 가리키는 값을 저장 `psizel` 컨트롤클래스데이터멤버에[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)합니다.  
  
 컨트롤 클래스 데이터 멤버 경우 [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) 은 **TRUE**, `SetExtent` 호출 `SendOnDataChange` 및 `SendOnViewChange` 에 등록 된 모든 자문 싱크를 알리기 위해는 컨트롤 크기가 변경 된 소유자에 게 설명 합니다.  
  
 참조 [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) in the Windows SDK입니다.  
  
##  <a name="sethostnames"></a>  IOleObjectImpl::SetHostNames  
 컨테이너 문서 컨테이너 응용 프로그램의 이름과 컨트롤에 알립니다.  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) in the Windows SDK입니다.  
  
##  <a name="setmoniker"></a>  IOleObjectImpl::SetMoniker  
 해당 모니커 란 컨트롤에 알립니다.  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>반환 값  
 반환 **E_NOTIMPL**합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) in the Windows SDK입니다.  
  
##  <a name="unadvise"></a>  IOleObjectImpl::Unadvise  
 컨트롤 클래스에 저장 된 권장 연결 삭제 `m_spOleAdviseHolder` 데이터 멤버입니다.  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) in the Windows SDK입니다.  
  
##  <a name="update"></a>  IOleObjectImpl::Update  
 컨트롤을 업데이트합니다.  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>반환 값  
 `S_OK`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 참조 [IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) in the Windows SDK입니다.  
  
## <a name="see-also"></a>참고 항목  
 [CComControl 클래스](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 컨트롤 인터페이스](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [클래스 개요](../../atl/atl-class-overview.md)
