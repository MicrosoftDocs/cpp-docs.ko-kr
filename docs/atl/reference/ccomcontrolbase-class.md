---
description: '자세히 알아보기: CComControlBase 클래스'
title: CComControlBase 클래스
ms.date: 11/04/2016
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 5ea232ac84ede33f7faa2a04e75b1ef65073ae9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152167"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 클래스

이 클래스는 ATL 컨트롤을 만들고 관리 하기 위한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|`m_nAppearance`스톡 속성이 형식이 아닌 경우를 재정의 **`short`** 합니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|생성자입니다.|
|[CComControlBase:: ~ CComControlBase](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|요청된 인터페이스에 대한 포인터를 검색합니다.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|에서 사용 하는 *iverb* 매개 변수가 `IOleObjectImpl::DoVerb` 컨트롤의 사용자 인터페이스 (*iverb* equals OLEIVERB_UIACTIVATE)를 활성화 하는지 확인 하 고, 사용자가 컨트롤을 두 번 클릭할 때 수행 되는 동작을 정의 *합니다 (* iverb equals OLEIVERB_PRIMARY). 컨트롤을 표시 하거나 *(iverb* Equals OLEIVERB_SHOW) 컨트롤을 활성화 합니다 (*iverb* equals OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::D oesVerbUIActivate](#doesverbuiactivate)|에서 사용 하는 *Iverb* 매개 변수가 `IOleObjectImpl::DoVerb` 컨트롤의 사용자 인터페이스를 활성화 하 고 TRUE를 반환 하는지 확인 합니다.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|컨트롤의 속성 페이지를 표시 합니다.|
|[CComControlBase::FireViewChange](#fireviewchange)|컨테이너에 컨트롤을 다시 그리도록 지시 하거나, 컨트롤의 뷰가 변경 되었음을 등록 된 advise 싱크에 알리도록 하려면이 메서드를 호출 합니다.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|컨트롤에 대 한 현재 모양 설정인 DISPID_AMBIENT_APPEARANCE를 검색 합니다. 즉, 평면에 대해 0을, 3D의 경우 1을 검색 합니다.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|컨테이너가 컨트롤 표시 영역의 자동 클리핑을 지원 하는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_AUTOCLIP를 검색 합니다.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|컨테이너에 의해 정의 되는 모든 컨트롤의 앰비언트 배경색 인 DISPID_AMBIENT_BACKCOLOR를 검색 합니다.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|컨테이너에 의해 정의 되는 모든 컨트롤에 대 한 앰비언트 문자 집합인 DISPID_AMBIENT_CHARSET를 검색 합니다.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|컨테이너에 의해 정의 되는 모든 컨트롤에 대 한 앰비언트 문자 집합인 DISPID_AMBIENT_CODEPAGE를 검색 합니다.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|컨테이너에서이 사이트의 컨트롤을 기본 단추로 표시 한 경우 TRUE 인 플래그 인 DISPID_AMBIENT_DISPLAYASDEFAULT를 검색 하므로 단추 컨트롤이 더 두꺼운 프레임을 사용 하 여 자체적으로 그려야 합니다.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|컨테이너가 컨트롤에 제공한 이름인 DISPID_AMBIENT_DISPLAYNAME를 검색 합니다.|
|[CComControlBase::GetAmbientFont](#getambientfont)|컨테이너의 앰비언트 인터페이스에 대 한 포인터를 검색 `IFont` 합니다.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|컨테이너의 앰비언트 디스패치 인터페이스에 대 한 포인터를 검색 `IFontDisp` 합니다.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|컨테이너에 의해 정의 되는 모든 컨트롤의 앰비언트 전경색 인 DISPID_AMBIENT_FORECOLOR를 검색 합니다.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|컨테이너에서 사용 하는 언어의 식별자 인 DISPID_AMBIENT_LOCALEID를 검색 합니다.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|컨테이너가 이벤트로 창 메시지 (예: WM_DRAWITEM)를 받을지 여부를 나타내는 플래그 DISPID_AMBIENT_MESSAGEREFLECT를 검색 합니다.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|컨테이너의 HPALETTE에 액세스 하는 데 사용 되는 DISPID_AMBIENT_PALETTE를 검색 합니다.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|*Id* 로 지정 된 컨테이너 속성을 검색 합니다.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|컨테이너에서 콘텐츠를 표시 하는 방향으로 DISPID_AMBIENT_RIGHTTOLEFT를 검색 합니다.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|레이블 표시를 위해 컨테이너의 주변 단위 (예: 인치 또는 센티미터)를 DISPID_AMBIENT_SCALEUNITS 검색 합니다.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|컨테이너에서 컨트롤이 활성화 될 때 자체에 대 한 잡기 핸들을 표시할 수 있는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_SHOWGRABHANDLES를 검색 합니다.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|UI가 활성 상태일 때 컨테이너를 사용 하 여 컨트롤을 해치 패턴으로 표시할 수 있는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_SHOWHATCHING를 검색 합니다.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|컨테이너에서 키보드 니모닉이 지원 되는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_SUPPORTSMNEMONICS를 검색 합니다.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|컨테이너에서 선호 하는 텍스트 맞춤 인 DISPID_AMBIENT_TEXTALIGN를 검색 합니다. 즉, 일반 맞춤의 경우 0, 왼쪽에는 텍스트, 왼쪽 맞춤의 경우 1, 가운데 맞춤의 경우 2, 오른쪽 맞춤의 경우 3입니다.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|컨테이너에서 콘텐츠를 표시 하는 방향으로 DISPID_AMBIENT_TOPTOBOTTOM를 검색 합니다.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|컨테이너에서 컨트롤을 사용자 인터페이스 작업에 응답할지 여부를 나타내는 플래그 인 DISPID_AMBIENT_UIDEAD를 검색 합니다.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|컨테이너가 실행 모드 (TRUE) 인지, 아니면 디자인 모드 (FALSE) 인지를 나타내는 플래그를 DISPID_AMBIENT_USERMODE를 검색 합니다.|
|[CComControlBase:: GetDirty](#getdirty)|데이터 멤버의 값을 반환 합니다 `m_bRequiresSave` .|
|[CComControlBase::GetZoomInfo](#getzoominfo)|내부 편집을 위해 활성화 된 컨트롤에 대 한 확대/축소 비율의 분자 및 분모의 x 및 y 값을 검색 합니다.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|컨트롤이 비활성 상태에서 *Iverb* 의 동사가 나타내는 상태로 전환 되도록 합니다.|
|[CComControlBase:: InternalGetSite](#internalgetsite)|컨트롤 사이트에서 식별 된 인터페이스에 대 한 포인터를 쿼리하려면이 메서드를 호출 합니다.|
|[CComControlBase:: OnDraw](#ondraw)|컨트롤을 그리려면이 메서드를 재정의 합니다.|
|[CComControlBase:: OnDrawAdvanced](#ondrawadvanced)|기본값은 `OnDrawAdvanced` 그리기를 위해 정규화 된 장치 컨텍스트를 준비한 다음 컨트롤 클래스의 메서드를 호출 `OnDraw` 합니다.|
|[CComControlBase::OnKillFocus](#onkillfocus)|컨트롤이 내부 활성 상태이 고 유효한 컨트롤 사이트가 있는지 확인 한 다음 컨트롤이 포커스를 잃었을 수 있음을 컨테이너에 알립니다.|
|[CComControlBase:: OnMouseActivate](#onmouseactivate)|UI가 사용자 모드에 있는지 확인 한 다음 컨트롤을 활성화 합니다.|
|[CComControlBase:: OnPaint](#onpaint)|컨테이너를 그리기 위해 준비 하 고, 컨트롤의 클라이언트 영역을 가져온 다음, 컨트롤 클래스의 메서드를 호출 합니다 `OnDraw` .|
|[CComControlBase:: OnSetFocus](#onsetfocus)|컨트롤이 내부 활성 상태이 고 유효한 컨트롤 사이트가 있는지 확인 한 다음 컨트롤이 포커스를 획득 했음을 컨테이너에 알립니다.|
|[CComControlBase::P reTranslateAccelerator](#pretranslateaccelerator)|사용자 고유의 키보드 액셀러레이터 처리기를 제공 하려면이 메서드를 재정의 합니다.|
|[CComControlBase::SendOnClose](#sendonclose)|컨트롤이 닫 혔 음을 advise 표시자에 등록 하 여 모든 advise 싱크에 알립니다.|
|[CComControlBase:: SendOnDataChange](#sendondatachange)|컨트롤 데이터가 변경 되었음을 advise 표시자에 등록 하 여 모든 advise 싱크에 알립니다.|
|[CComControlBase:: SendOnRename](#sendonrename)|컨트롤에 새 모니커가 있음을 advise 표시자에 등록 한 모든 advise 싱크에 알립니다.|
|[CComControlBase::SendOnSave](#sendonsave)|컨트롤이 저장 되었음을 알리는 advise 표시자에 등록 된 모든 advise 싱크에 알립니다.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|등록 된 모든 advise 싱크에 컨트롤의 뷰가 변경 되었음을 알립니다.|
|[CComControlBase:: SetControlFocus](#setcontrolfocus)|컨트롤에서 키보드 포커스를 설정 하거나 제거 합니다.|
|[CComControlBase:: SetDirty](#setdirty)|데이터 멤버를 `m_bRequiresSave` *bdirty* 의 값으로 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComControlBase:: m_bAutoSize](#m_bautosize)|컨트롤에 다른 크기를 지정할 수 없음을 나타내는 플래그입니다.|
|[CComControlBase:: m_bDrawFromNatural](#m_bdrawfromnatural)|`IDataObjectImpl::GetData`및가가 아닌 `CComControlBase::GetZoomInfo` 에서 컨트롤 크기를 설정 해야 함을 나타내는 플래그입니다 `m_sizeNatural` `m_sizeExtent` .|
|[CComControlBase:: m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|`IDataObjectImpl::GetData`그릴 때 픽셀이 아닌 HIMETRIC 단위를 사용 해야 함을 나타내는 플래그입니다.|
|[CComControlBase:: m_bInPlaceActive](#m_binplaceactive)|컨트롤이 내부 활성화 되었음을 나타내는 플래그입니다.|
|[CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex)|컨테이너에서 `IOleInPlaceSiteEx` 인터페이스 및 OCX96 컨트롤 기능 (예: 창 없는 및 깜빡임 없는 컨트롤)을 지원함을 나타내는 플래그입니다.|
|[CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd)|컨트롤이 OCX96 컨트롤 기능 (예: 깜빡임 없는 컨트롤 및 창 없는 컨트롤)에 대 한 지원 및 컨트롤이 창에 있는지 또는 창 없는 컨트롤 인지 여부를 나타내는 플래그입니다.|
|[CComControlBase:: m_bRecomposeOnResize](#m_brecomposeonresize)|컨테이너가 컨트롤의 표시 크기를 변경 하는 경우 컨트롤에서 프레젠테이션을 재구성 함을 나타내는 플래그입니다.|
|[CComControlBase:: m_bRequiresSave](#m_brequiressave)|컨트롤이 마지막으로 저장 된 이후 변경 되었음을 나타내는 플래그입니다.|
|[CComControlBase:: m_bResizeNatural](#m_bresizenatural)|컨테이너가 컨트롤의 표시 크기를 변경 하는 경우 컨트롤에서 해당 자연 익스텐트의 크기를 조정 하려고 함을 나타내는 플래그입니다.|
|[CComControlBase:: m_bUIActive](#m_buiactive)|메뉴 및 도구 모음과 같은 컨트롤의 사용자 인터페이스가 활성 상태를 나타내는 플래그입니다.|
|[CComControlBase:: m_bUsingWindowRgn](#m_busingwindowrgn)|컨테이너가 컨테이너에서 제공 하는 창 영역을 사용 중임을 나타내는 플래그입니다.|
|[CComControlBase:: m_bWasOnceWindowless](#m_bwasoncewindowless)|컨트롤이 창 없는 컨트롤이 었는 지를 나타내는 플래그입니다. 현재는 창이 표시 되지 않을 수도 있습니다.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|컨테이너에서 창 없는 컨트롤을 지 원하는 경우에도 컨트롤이 창에 있어야 함을 나타내는 플래그입니다.|
|[CComControlBase:: m_bWndLess](#m_bwndless)|컨트롤을 창 없는 컨트롤로 나타내는 플래그입니다.|
|[CComControlBase:: m_hWndCD](#m_hwndcd)|컨트롤과 연결 된 창 핸들에 대 한 참조를 포함 합니다.|
|[CComControlBase:: m_nFreezeEvents](#m_nfreezeevents)|이벤트를 중단 (이벤트 허용) 하지 않고 컨테이너가 고정 된 이벤트 (이벤트를 허용 하지 않음)가 발생 한 횟수입니다.|
|[CComControlBase:: m_rcPos](#m_rcpos)|컨테이너의 좌표로 표현 되는 컨트롤의 픽셀 위치입니다.|
|[CComControlBase:: m_sizeExtent](#m_sizeextent)|특정 표시에 대 한 HIMETRIC unit (각 단위는 0.01 밀리미터)에 있는 컨트롤의 범위입니다.|
|[CComControlBase:: m_sizeNatural](#m_sizenatural)|HIMETRIC unit에 있는 컨트롤의 실제 크기 (각 단위는 0.01 밀리미터)입니다.|
|[CComControlBase:: m_spAdviseSink](#m_spadvisesink)|컨테이너의 advise 연결에 대 한 직접 포인터 (컨테이너의 [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink))입니다.|
|[CComControlBase:: m_spAmbientDispatch](#m_spambientdispatch)|`CComDispatchDriver`포인터를 통해 컨테이너의 속성을 검색 하 고 설정할 수 있는 개체입니다 `IDispatch` .|
|[CComControlBase:: m_spClientSite](#m_spclientsite)|컨테이너 내에 있는 컨트롤의 클라이언트 사이트에 대 한 포인터입니다.|
|[CComControlBase:: m_spDataAdviseHolder](#m_spdataadviseholder)|데이터 개체와 advise 싱크 간의 advise 연결을 보유 하는 표준 수단을 제공 합니다.|
|[CComControlBase:: m_spInPlaceSite](#m_spinplacesite)|컨테이너의 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)또는 [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) 인터페이스 포인터에 대 한 포인터입니다.|
|[CComControlBase:: m_spOleAdviseHolder](#m_spoleadviseholder)|Advise 연결을 보유 하는 방법의 표준 구현을 제공 합니다.|

## <a name="remarks"></a>설명

이 클래스는 ATL 컨트롤을 만들고 관리 하기 위한 메서드를 제공 합니다. [CComControl 클래스](../../atl/reference/ccomcontrol-class.md) 는에서 파생 `CComControlBase` 됩니다. ATL 컨트롤 마법사를 사용 하 여 표준 컨트롤 또는 DHTML 컨트롤을 만들면 마법사가에서 자동으로 클래스를 파생 시킵니다 `CComControlBase` .

컨트롤을 만드는 방법에 대 한 자세한 내용은 [ATL 자습서](../../atl/active-template-library-atl-tutorial.md)를 참조 하십시오. ATL 프로젝트 마법사에 대 한 자세한 내용은 [Atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)문서를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a> CComControlBase::AppearanceType

`m_nAppearance`스톡 속성이 형식이 아닌 경우를 재정의 **`short`** 합니다.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>설명

ATL 컨트롤 마법사는 `m_nAppearance` short 형식의 스톡 속성을 추가 합니다. `AppearanceType`다른 데이터 형식을 사용 하는 경우를 재정의 합니다.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a> CComControlBase::CComControlBase

생성자입니다.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
컨트롤과 연결 된 창에 대 한 핸들입니다.

### <a name="remarks"></a>설명

컨트롤 크기를 5080X5080 HIMETRIC units (2 "X2")로 초기화 하 고 `CComControlBase` 데이터 멤버 값을 NULL 또는 FALSE로 초기화 합니다.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a> CComControlBase:: ~ CComControlBase

소멸자입니다.

```
~CComControlBase();
```

### <a name="remarks"></a>설명

컨트롤이 창에 있는 경우 `~CComControlBase` [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow)를 호출 하 여이를 소멸 시킵니다.

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a> CComControlBase:: ControlQueryInterface

요청된 인터페이스에 대한 포인터를 검색합니다.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
요청 되는 인터페이스의 GUID입니다.

*ppv*<br/>
*Iid* 로 식별 되는 인터페이스 포인터에 대 한 포인터 이거나, 인터페이스를 찾을 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

는 COM 맵 테이블의 인터페이스만 처리 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a> CComControlBase::D oesVerbActivate

에서 사용 하는 *iverb* 매개 변수가 `IOleObjectImpl::DoVerb` 컨트롤의 사용자 인터페이스 (*iverb* equals OLEIVERB_UIACTIVATE)를 활성화 하는지 확인 하 고, 사용자가 컨트롤을 두 번 클릭할 때 수행 되는 동작을 정의 *합니다 (* iverb equals OLEIVERB_PRIMARY). 컨트롤을 표시 하거나 *(iverb* Equals OLEIVERB_SHOW) 컨트롤을 활성화 합니다 (*iverb* equals OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>매개 변수

*iVerb*<br/>
에서 수행할 동작을 나타내는 값 `DoVerb` 입니다.

### <a name="return-value"></a>반환 값

*Iverb* 가 OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW 또는 OLEIVERB_INPLACEACTIVATE 인 경우 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드를 재정의 하 여 사용자 고유의 활성화 동사를 정의할 수 있습니다.

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a> CComControlBase::D oesVerbUIActivate

에서 사용 하는 *Iverb* 매개 변수가 `IOleObjectImpl::DoVerb` 컨트롤의 사용자 인터페이스를 활성화 하 고 TRUE를 반환 하는지 확인 합니다.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>매개 변수

*iVerb*<br/>
에서 수행할 동작을 나타내는 값 `DoVerb` 입니다.

### <a name="return-value"></a>반환 값

*Iverb* 가 OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW 또는 OLEIVERB_INPLACEACTIVATE 인 경우 TRUE를 반환 합니다. 그렇지 않으면이 메서드는 FALSE를 반환 합니다.

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a> CComControlBase::D 오버:

컨트롤의 속성 페이지를 표시 합니다.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>매개 변수

*prcPosRec*<br/>
예약되어 있습니다.

*hwndParent*<br/>
컨트롤을 포함 하는 창의 핸들입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a> CComControlBase::FireViewChange

컨테이너에 컨트롤을 다시 그리도록 지시 하거나, 컨트롤의 뷰가 변경 되었음을 등록 된 advise 싱크에 알리도록 하려면이 메서드를 호출 합니다.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

컨트롤이 활성화 되어 있으면 (컨트롤 클래스 데이터 멤버 [CComControlBase:: M_BINPLACEACTIVE](#m_binplaceactive) TRUE 임)는 전체 컨트롤을 다시 그리도록 컨테이너에 알립니다. 컨트롤이 비활성화 되어 있는 경우 컨트롤의 뷰가 변경 된 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_spAdviseSink](#m_spadvisesink)를 통해 컨트롤의 등록 된 advise 싱크에 알립니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a> CComControlBase::GetAmbientAppearance

컨트롤에 대 한 현재 모양 설정인 DISPID_AMBIENT_APPEARANCE를 검색 합니다. 즉, 평면에 대해 0을, 3D의 경우 1을 검색 합니다.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>매개 변수

*nAppearance*<br/>
속성 DISPID_AMBIENT_APPEARANCE입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a> CComControlBase::GetAmbientAutoClip

컨테이너가 컨트롤 표시 영역의 자동 클리핑을 지원 하는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_AUTOCLIP를 검색 합니다.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>매개 변수

*bAutoClip*<br/>
속성 DISPID_AMBIENT_AUTOCLIP입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a> CComControlBase::GetAmbientBackColor

컨테이너에 의해 정의 되는 모든 컨트롤의 앰비언트 배경색 인 DISPID_AMBIENT_BACKCOLOR를 검색 합니다.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>매개 변수

*배경색*<br/>
속성 DISPID_AMBIENT_BACKCOLOR입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a> CComControlBase::GetAmbientCharSet

컨테이너에 의해 정의 되는 모든 컨트롤에 대 한 앰비언트 문자 집합인 DISPID_AMBIENT_CHARSET를 검색 합니다.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>매개 변수

*bstrCharSet*<br/>
속성 DISPID_AMBIENT_CHARSET입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a> CComControlBase::GetAmbientCodePage

컨테이너에 의해 정의 되는 모든 컨트롤에 대 한 앰비언트 코드 페이지인 DISPID_AMBIENT_CODEPAGE를 검색 합니다.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>매개 변수

*ulCodePage*<br/>
속성 DISPID_AMBIENT_CODEPAGE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a> CComControlBase::GetAmbientDisplayAsDefault

컨테이너에서이 사이트의 컨트롤을 기본 단추로 표시 한 경우 TRUE 인 플래그 인 DISPID_AMBIENT_DISPLAYASDEFAULT를 검색 하므로 단추 컨트롤이 더 두꺼운 프레임을 사용 하 여 자체적으로 그려야 합니다.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>매개 변수

*bDisplayAsDefault*<br/>
속성 DISPID_AMBIENT_DISPLAYASDEFAULT입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a> CComControlBase::GetAmbientDisplayName

컨테이너가 컨트롤에 제공한 이름인 DISPID_AMBIENT_DISPLAYNAME를 검색 합니다.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>매개 변수

*bstrDisplayName*<br/>
속성 DISPID_AMBIENT_DISPLAYNAME입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a> CComControlBase::GetAmbientFont

컨테이너의 앰비언트 인터페이스에 대 한 포인터를 검색 `IFont` 합니다.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>매개 변수

*ppFont*<br/>
컨테이너의 앰비언트 [Ifont](/windows/win32/api/ocidl/nn-ocidl-ifont) 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

속성이 NULL 이면 포인터가 NULL입니다. 포인터가 NULL이 아니면 호출자는 포인터를 해제 해야 합니다.

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a> CComControlBase::GetAmbientFontDisp

컨테이너의 앰비언트 디스패치 인터페이스에 대 한 포인터를 검색 `IFontDisp` 합니다.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>매개 변수

*ppFont*<br/>
컨테이너의 앰비언트 [Ifontdisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) 디스패치 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

속성이 NULL 이면 포인터가 NULL입니다. 포인터가 NULL이 아니면 호출자는 포인터를 해제 해야 합니다.

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a> CComControlBase::GetAmbientForeColor

컨테이너에 의해 정의 되는 모든 컨트롤의 앰비언트 전경색 인 DISPID_AMBIENT_FORECOLOR를 검색 합니다.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>매개 변수

*ForeColor*<br/>
속성 DISPID_AMBIENT_FORECOLOR입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a> CComControlBase::GetAmbientLocaleID

컨테이너에서 사용 하는 언어의 식별자 인 DISPID_AMBIENT_LOCALEID를 검색 합니다.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>매개 변수

*lcid*<br/>
속성 DISPID_AMBIENT_LOCALEID입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

컨트롤은이 식별자를 사용 하 여 사용자 인터페이스를 다양 한 언어로 조정할 수 있습니다.

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a> CComControlBase::GetAmbientMessageReflect

컨테이너가 이벤트로 창 메시지 (예:)를 받을지 여부를 나타내는 플래그 DISPID_AMBIENT_MESSAGEREFLECT를 검색 합니다 `WM_DRAWITEM` .

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>매개 변수

*bMessageReflect*<br/>
속성 DISPID_AMBIENT_MESSAGEREFLECT입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a> CComControlBase::GetAmbientPalette

컨테이너의 HPALETTE에 액세스 하는 데 사용 되는 DISPID_AMBIENT_PALETTE를 검색 합니다.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>매개 변수

*hPalette*<br/>
속성 DISPID_AMBIENT_PALETTE입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a> CComControlBase::GetAmbientProperty

*Dispid* 로 지정 된 컨테이너 속성을 검색 합니다.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
검색할 컨테이너 속성의 식별자입니다.

*var*<br/>
속성을 받는 변수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

ATL은 특정 속성을 검색 하는 도우미 함수 집합을 제공 합니다 (예 [: CComControlBase:: GetAmbientBackColor](#getambientbackcolor)). 사용할 수 있는 적절 한 메서드가 없으면를 사용 `GetAmbientProperty` 합니다.

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a> CComControlBase::GetAmbientRightToLeft

컨테이너에서 콘텐츠를 표시 하는 방향으로 DISPID_AMBIENT_RIGHTTOLEFT를 검색 합니다.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>매개 변수

*bRightToLeft*<br/>
속성 DISPID_AMBIENT_RIGHTTOLEFT입니다. 내용이 오른쪽에서 왼쪽으로 표시 되 면 TRUE로 설정 하 고 왼쪽에서 오른쪽으로 표시 되는 경우 FALSE로 설정 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a> CComControlBase::GetAmbientScaleUnits

레이블 표시를 위해 컨테이너의 주변 단위 (예: 인치 또는 센티미터)를 DISPID_AMBIENT_SCALEUNITS 검색 합니다.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>매개 변수

*bstrScaleUnits*<br/>
속성 DISPID_AMBIENT_SCALEUNITS입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a> CComControlBase::GetAmbientShowGrabHandles

컨테이너에서 컨트롤이 활성화 될 때 자체에 대 한 잡기 핸들을 표시할 수 있는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_SHOWGRABHANDLES를 검색 합니다.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>매개 변수

*bShowGrabHandles*<br/>
속성 DISPID_AMBIENT_SHOWGRABHANDLES입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a> CComControlBase::GetAmbientShowHatching

컨트롤의 사용자 인터페이스가 활성화 된 경우 컨테이너를 사용 하 여 컨트롤을 해치 패턴으로 표시할 수 있는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_SHOWHATCHING를 검색 합니다.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>매개 변수

*bShowHatching*<br/>
속성 DISPID_AMBIENT_SHOWHATCHING입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a> CComControlBase::GetAmbientSupportsMnemonics

컨테이너에서 키보드 니모닉이 지원 되는지 여부를 나타내는 플래그 인 DISPID_AMBIENT_SUPPORTSMNEMONICS를 검색 합니다.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>매개 변수

*bSupportsMnemonics*<br/>
속성 DISPID_AMBIENT_SUPPORTSMNEMONICS입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a> CComControlBase::GetAmbientTextAlign

컨테이너에서 선호 하는 텍스트 맞춤 인 DISPID_AMBIENT_TEXTALIGN를 검색 합니다. 즉, 일반 맞춤의 경우 0, 왼쪽에는 텍스트, 왼쪽 맞춤의 경우 1, 가운데 맞춤의 경우 2, 오른쪽 맞춤의 경우 3입니다.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>매개 변수

*nTextAlign*<br/>
속성 DISPID_AMBIENT_TEXTALIGN입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a> CComControlBase::GetAmbientTopToBottom

컨테이너에서 콘텐츠를 표시 하는 방향으로 DISPID_AMBIENT_TOPTOBOTTOM를 검색 합니다.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>매개 변수

*bTopToBottom*<br/>
속성 DISPID_AMBIENT_TOPTOBOTTOM입니다. 텍스트가 위쪽에서 아래쪽으로 표시 되 면 TRUE로 설정 하 고, 위쪽에서 아래쪽으로 표시 되 면 FALSE로 설정 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a> CComControlBase::GetAmbientUIDead

컨테이너에서 컨트롤을 사용자 인터페이스 작업에 응답할지 여부를 나타내는 플래그 인 DISPID_AMBIENT_UIDEAD를 검색 합니다.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>매개 변수

*bUIDead*<br/>
속성 DISPID_AMBIENT_UIDEAD입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

TRUE 이면 컨트롤이 응답 하지 않습니다. 이 플래그는 DISPID_AMBIENT_USERMODE 플래그에 관계 없이 적용 됩니다. [CComControlBase:: GetAmbientUserMode](#getambientusermode)를 참조 하세요.

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a> CComControlBase::GetAmbientUserMode

컨테이너가 실행 모드 (TRUE) 인지, 아니면 디자인 모드 (FALSE) 인지를 나타내는 플래그를 DISPID_AMBIENT_USERMODE를 검색 합니다.

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>매개 변수

*bUserMode*<br/>
속성 DISPID_AMBIENT_USERMODE입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a> CComControlBase:: GetDirty

데이터 멤버의 값을 반환 합니다 `m_bRequiresSave` .

```
BOOL GetDirty();
```

### <a name="return-value"></a>반환 값

데이터 멤버 [m_bRequiresSave](#m_brequiressave)의 값을 반환 합니다.

### <a name="remarks"></a>설명

이 값은 [CComControlBase:: SetDirty](#setdirty)를 사용 하 여 설정 됩니다.

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a> CComControlBase::GetZoomInfo

내부 편집을 위해 활성화 된 컨트롤에 대 한 확대/축소 비율의 분자 및 분모의 x 및 y 값을 검색 합니다.

```cpp
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>매개 변수

*di*<br/>
확대/축소 비율의 분자와 분모를 포함 하는 구조체입니다. 자세한 내용은 [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)를 참조 하세요.

### <a name="remarks"></a>설명

확대/축소 비율은 현재 범위에 대 한 컨트롤의 기본 크기에 대 한 비율입니다.

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a> CComControlBase::InPlaceActivate

컨트롤이 비활성 상태에서 *Iverb* 의 동사가 나타내는 상태로 전환 되도록 합니다.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>매개 변수

*iVerb*<br/>
[IOleObjectImpl::D 초과 b](../../atl/reference/ioleobjectimpl-class.md#doverb)에서 수행할 동작을 나타내는 값입니다.

*prcPosRect*<br/>
내부 컨트롤의 위치에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

활성화 하기 전에이 메서드는 컨트롤에 클라이언트 사이트가 있는지 확인 하 고, 표시 되는 컨트롤의 크기를 확인 하 고, 부모 창에서 컨트롤의 위치를 가져옵니다. 컨트롤이 활성화 되 면이 메서드는 컨트롤의 사용자 인터페이스를 활성화 하 고 컨테이너에 컨트롤을 표시 하도록 지시 합니다.

또한이 메서드는 `IOleInPlaceSite` `IOleInPlaceSiteEx` `IOleInPlaceSiteWindowless` 컨트롤에 대 한, 또는 인터페이스 포인터를 검색 하 여 컨트롤 클래스의 데이터 멤버 [CComControlBase:: m_spInPlaceSite](#m_spinplacesite)에 저장 합니다. 컨트롤 클래스 데이터 멤버 [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase:: m_bWndLess](#m_bwndless), [CComControlBase:: m_bWasOnceWindowless](#m_bwasoncewindowless)및 [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) 은 적절 하 게 true로 설정 됩니다.

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a> CComControlBase:: InternalGetSite

컨트롤 사이트에서 식별 된 인터페이스에 대 한 포인터를 쿼리하려면이 메서드를 호출 합니다.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
*PpUnkSite* 에 반환 되어야 하는 인터페이스 포인터의 IID입니다.

*ppUnkSite*<br/>
*Riid* 에서 요청 된 인터페이스 포인터를 받는 포인터 변수의 주소입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

사이트가 *riid* 에서 요청 된 인터페이스를 지 원하는 경우 *ppUnkSite* 를 통해 포인터가 반환 됩니다. 그렇지 않으면 *ppUnkSite* 가 NULL로 설정 됩니다.

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a> CComControlBase:: m_bAutoSize

컨트롤에 다른 크기를 지정할 수 없음을 나타내는 플래그입니다.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>설명

이 플래그는에 의해 확인 되며 `IOleObjectImpl::SetExtent` TRUE 이면 함수가 E_FAIL을 반환 합니다.

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

ATL 컨트롤 마법사의 [스톡 속성](../../atl/reference/stock-properties-atl-control-wizard.md) 탭에서 **자동 크기** 옵션을 추가 하는 경우 마법사는이 데이터 멤버를 컨트롤 클래스에 자동으로 만들고, 속성에 대 한 put 및 get 메서드를 만들며, [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)을 지원 합니다. 속성이 변경 될 때 컨테이너에 자동으로 알리려면입니다.

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a> CComControlBase:: m_bDrawFromNatural

`IDataObjectImpl::GetData`및가가 아닌 `CComControlBase::GetZoomInfo` 에서 컨트롤 크기를 설정 해야 함을 나타내는 플래그입니다 `m_sizeNatural` `m_sizeExtent` .

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a> CComControlBase:: m_bDrawGetDataInHimetric

`IDataObjectImpl::GetData`그릴 때 픽셀이 아닌 HIMETRIC 단위를 사용 해야 함을 나타내는 플래그입니다.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>설명

각 논리적 HIMETRIC 단위는 0.01 밀리미터입니다.

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a> CComControlBase:: m_bInPlaceActive

컨트롤이 내부 활성화 되었음을 나타내는 플래그입니다.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>설명

즉, 컨트롤이 표시 되 고 창 (있는 경우)은 표시 되지만 메뉴와 도구 모음은 활성화 되지 않을 수 있습니다. `m_bUIActive`플래그는 메뉴와 같은 컨트롤의 사용자 인터페이스도 활성 상태임을 나타냅니다.

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a> CComControlBase:: m_bInPlaceSiteEx

컨테이너에서 `IOleInPlaceSiteEx` 인터페이스 및 OCX96 컨트롤 기능 (예: 창 없는 및 깜빡임 없는 컨트롤)을 지원함을 나타내는 플래그입니다.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

데이터 멤버 `m_spInPlaceSite`는 `m_bWndLess` 및 `m_bInPlaceSiteEx` 플래그의 값에 따라 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex) 또는 [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) 인터페이스를 가리킵니다. ( `m_bNegotiatedWnd` 포인터가 유효 하려면 데이터 멤버가 TRUE 여야 합니다 `m_spInPlaceSite` .)

`m_bWndLess`가 FALSE이 고 `m_bInPlaceSiteEx` 가 TRUE 이면 `m_spInPlaceSite` 는 `IOleInPlaceSiteEx` 인터페이스 포인터입니다. 이러한 세 데이터 멤버 간의 관계를 보여 주는 테이블은 [m_spInPlaceSite](#m_spinplacesite) 를 참조 하세요.

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a> CComControlBase:: m_bNegotiatedWnd

컨트롤이 OCX96 컨트롤 기능 (예: 깜빡임 없는 컨트롤 및 창 없는 컨트롤)에 대 한 지원 및 컨트롤이 창에 있는지 또는 창 없는 컨트롤 인지 여부를 나타내는 플래그입니다.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

`m_bNegotiatedWnd`포인터가 유효 하려면 플래그가 TRUE 여야 합니다 `m_spInPlaceSite` .

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a> CComControlBase:: m_bRecomposeOnResize

컨테이너가 컨트롤의 표시 크기를 변경 하는 경우 컨트롤에서 프레젠테이션을 재구성 함을 나타내는 플래그입니다.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

이 플래그는 [IOleObjectImpl:: SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) 확인 하 고 TRUE 인 경우 `SetExtent` 뷰 변경 내용에 대 한 컨테이너를 알립니다. 이 플래그가 설정 되 면 [Olemisc](/windows/win32/api/oleidl/ne-oleidl-olemisc) 열거의 OLEMISC_RECOMPOSEONRESIZE 비트가 설정 되어야 합니다.

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a> CComControlBase:: m_bRequiresSave

컨트롤이 마지막으로 저장 된 이후 변경 되었음을 나타내는 플래그입니다.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>설명

값은 `m_bRequiresSave` [CComControlBase:: setdirty](#setdirty) 를 사용 하 여 설정 하 고 [CComControlBase:: getdirty](#getdirty)로 검색할 수 있습니다.

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a> CComControlBase:: m_bResizeNatural

컨테이너가 컨트롤의 표시 크기를 변경 하는 경우 컨트롤에서 해당 자연 익스텐트의 크기를 조정 하려고 함을 나타내는 플래그입니다.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>설명

이 플래그는에 의해 확인 되며 TRUE 이면에 `IOleObjectImpl::SetExtent` 전달 된 크기가 `SetExtent` 에 할당 됩니다 `m_sizeNatural` .

에 전달 되는 크기는 `SetExtent` `m_sizeExtent` 의 값에 관계 없이 항상에 할당 됩니다 `m_bResizeNatural` .

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a> CComControlBase:: m_bUIActive

메뉴 및 도구 모음과 같은 컨트롤의 사용자 인터페이스가 활성 상태를 나타내는 플래그입니다.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>설명

`m_bInPlaceActive`플래그는 컨트롤이 활성화 되어 있지만 해당 사용자 인터페이스가 활성 상태임을 나타냅니다.

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a> CComControlBase:: m_bUsingWindowRgn

컨테이너가 컨테이너에서 제공 하는 창 영역을 사용 중임을 나타내는 플래그입니다.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a> CComControlBase:: m_bWasOnceWindowless

컨트롤이 창 없는 컨트롤이 었는 지를 나타내는 플래그입니다. 현재는 창이 표시 되지 않을 수도 있습니다.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a> CComControlBase:: m_bWindowOnly

컨테이너에서 창 없는 컨트롤을 지 원하는 경우에도 컨트롤이 창에 있어야 함을 나타내는 플래그입니다.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a> CComControlBase:: m_bWndLess

컨트롤을 창 없는 컨트롤로 나타내는 플래그입니다.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

데이터 멤버는 `m_spInPlaceSite` [](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)및 [](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex) [](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess` [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex) 플래그의 값에 따라 IOleInPlaceSite, IOleInPlaceSiteEx 또는 IOleInPlaceSiteWindowless 인터페이스를 가리킵니다. [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) 포인터가 유효 하려면 [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) 데이터 멤버를 TRUE로 설정 해야 합니다.

`m_bWndLess`이 TRUE 이면 `m_spInPlaceSite` 는 `IOleInPlaceSiteWindowless` 인터페이스 포인터입니다. 이러한 데이터 멤버 간의 전체 관계를 보여 주는 테이블은 [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) 를 참조 하세요.

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a> CComControlBase:: m_hWndCD

컨트롤과 연결 된 창 핸들에 대 한 참조를 포함 합니다.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a> CComControlBase:: m_nFreezeEvents

이벤트를 중단 (이벤트 허용) 하지 않고 컨테이너가 고정 된 이벤트 (이벤트를 허용 하지 않음)가 발생 한 횟수입니다.

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a> CComControlBase:: m_rcPos

컨테이너의 좌표로 표현 되는 컨트롤의 픽셀 위치입니다.

```
RECT m_rcPos;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a> CComControlBase:: m_sizeExtent

특정 표시에 대 한 HIMETRIC unit (각 단위는 0.01 밀리미터)에 있는 컨트롤의 범위입니다.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

이 크기는 표시의 크기를 조정 합니다. 컨트롤의 실제 크기가 데이터 멤버에 지정 되어 `m_sizeNatural` 있고 고정 되어 있습니다.

전역 함수 [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)를 사용 하 여 크기를 픽셀로 변환할 수 있습니다.

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a> CComControlBase:: m_sizeNatural

HIMETRIC unit에 있는 컨트롤의 실제 크기 (각 단위는 0.01 밀리미터)입니다.

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

이 크기는 고정 되어 있지만의 크기는 `m_sizeExtent` 표시에 의해 조정 됩니다.

전역 함수 [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)를 사용 하 여 크기를 픽셀로 변환할 수 있습니다.

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a> CComControlBase:: m_spAdviseSink

컨테이너의 advise 연결에 대 한 직접 포인터 (컨테이너의 [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink))입니다.

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a> CComControlBase:: m_spAmbientDispatch

`CComDispatchDriver`포인터를 통해 개체의 속성을 검색 하 고 설정할 수 있는 개체입니다 `IDispatch` .

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a> CComControlBase:: m_spClientSite

컨테이너 내에 있는 컨트롤의 클라이언트 사이트에 대 한 포인터입니다.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a> CComControlBase:: m_spDataAdviseHolder

데이터 개체와 advise 싱크 간의 advise 연결을 보유 하는 표준 수단을 제공 합니다.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

데이터 개체는 데이터를 전송할 수 있는 컨트롤이 며, 해당 메서드가 데이터의 형식 및 전송 미디어를 지정 하는 [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)를 구현 합니다.

이 인터페이스는 `m_spDataAdviseHolder` [IDataObject::D Advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) 및 [IDataObject::D unadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) 메서드를 구현 하 여 컨테이너에 대 한 advise 연결을 설정 하 고 삭제 합니다. 컨트롤의 컨테이너는 [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) 인터페이스를 지원 하 여 advise 싱크를 구현 해야 합니다.

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a> CComControlBase:: m_spInPlaceSite

컨테이너의 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)또는 [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) 인터페이스 포인터에 대 한 포인터입니다.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

`m_spInPlaceSite`포인터는 [M_BNEGOTIATEDWND](#m_bnegotiatedwnd) 플래그가 TRUE 인 경우에만 유효 합니다.

다음 표에서는 `m_spInPlaceSite` [m_bWndLess](#m_bwndless) 및 [m_bInPlaceSiteEx](#m_binplacesiteex) 데이터 멤버 플래그에 포인터 형식이 어떻게 달라 지는 지를 보여 줍니다.

|m_spInPlaceSite 형식|m_bWndLess 값|m_bInPlaceSiteEx 값|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|TRUE 또는 FALSE|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a> CComControlBase:: m_spOleAdviseHolder

Advise 연결을 보유 하는 방법의 표준 구현을 제공 합니다.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤 클래스 내에서이 데이터 멤버를 사용 하려면 컨트롤 클래스에서이 데이터 멤버를 데이터 멤버로 선언 해야 합니다. 컨트롤 클래스는 기본 클래스의 공용 구조체 내에서 선언 되기 때문에 기본 클래스에서이 데이터 멤버를 상속 하지 않습니다.

이 인터페이스는 `m_spOleAdviseHolder` [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) 및 [IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) 메서드를 구현 하 여 컨테이너에 대 한 advise 연결을 설정 하 고 삭제 합니다. 컨트롤의 컨테이너는 [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) 인터페이스를 지원 하 여 advise 싱크를 구현 해야 합니다.

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a> CComControlBase:: OnDraw

컨트롤을 그리려면이 메서드를 재정의 합니다.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>매개 변수

*di*<br/>
그리기 측면, 컨트롤 범위, 그리기의 최적화 여부와 같은 그리기 정보를 포함 하는 [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) 구조에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

기본값은 `OnDraw` [CComControlBase:: OnDrawAdvanced](#ondrawadvanced)에 설정 된 플래그에 따라 장치 컨텍스트를 삭제 또는 복원 하거나 아무 작업도 수행 하지 않습니다.

`OnDraw`ATL 컨트롤 마법사를 사용 하 여 컨트롤을 만들 때 메서드는 컨트롤 클래스에 자동으로 추가 됩니다. 마법사의 기본값은 `OnDraw` "ATL 8.0" 라는 레이블이 있는 사각형을 그립니다.

### <a name="example"></a>예제

[CComControlBase:: GetAmbientAppearance](#getambientappearance)의 예제를 참조 하세요.

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a> CComControlBase:: OnDrawAdvanced

기본값은 `OnDrawAdvanced` 그리기를 위해 정규화 된 장치 컨텍스트를 준비한 다음 컨트롤 클래스의 메서드를 호출 `OnDraw` 합니다.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>매개 변수

*di*<br/>
그리기 측면, 컨트롤 범위, 그리기의 최적화 여부와 같은 그리기 정보를 포함 하는 [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) 구조에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

정규화 하지 않고 컨테이너에 의해 전달 된 장치 컨텍스트를 허용 하려면이 메서드를 재정의 합니다.

자세한 내용은 [CComControlBase:: OnDraw](#ondraw) 를 참조 하세요.

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a> CComControlBase::OnKillFocus

컨트롤이 내부 활성 상태이 고 유효한 컨트롤 사이트가 있는지 확인 한 다음 컨트롤이 포커스를 잃었을 수 있음을 컨테이너에 알립니다.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>매개 변수

*nMsg*<br/>
예약되어 있습니다.

*wParam*<br/>
예약되어 있습니다.

*lParam*<br/>
예약되어 있습니다.

*bHandled*<br/>
창 메시지가 성공적으로 처리 되었는지 여부를 나타내는 플래그입니다. 기본값은 FALSE입니다.

### <a name="return-value"></a>반환 값

항상 1을 반환 합니다.

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a> CComControlBase:: OnMouseActivate

UI가 사용자 모드에 있는지 확인 한 다음 컨트롤을 활성화 합니다.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>매개 변수

*nMsg*<br/>
예약되어 있습니다.

*wParam*<br/>
예약되어 있습니다.

*lParam*<br/>
예약되어 있습니다.

*bHandled*<br/>
창 메시지가 성공적으로 처리 되었는지 여부를 나타내는 플래그입니다. 기본값은 FALSE입니다.

### <a name="return-value"></a>반환 값

항상 1을 반환 합니다.

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a> CComControlBase:: OnPaint

컨테이너를 그리기 위해 준비 하 고, 컨트롤의 클라이언트 영역을 가져온 다음, 컨트롤 클래스의 메서드를 호출 합니다 `OnDrawAdvanced` .

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>매개 변수

*nMsg*<br/>
예약되어 있습니다.

*wParam*<br/>
기존 HDC입니다.

*lParam*<br/>
예약되어 있습니다.

*lResult*<br/>
예약되어 있습니다.

### <a name="return-value"></a>반환 값

항상 0을 반환합니다.

### <a name="remarks"></a>설명

*WParam* 이 NULL이 아닌 경우는 `OnPaint` 유효한 HDC를 포함 하 고 [CComControlBase:: m_hWndCD](#m_hwndcd)대신이를 사용 한다고 가정 합니다.

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a> CComControlBase:: OnSetFocus

컨트롤이 내부 활성 상태이 고 유효한 컨트롤 사이트가 있는지 확인 한 다음 컨트롤이 포커스를 획득 했음을 컨테이너에 알립니다.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>매개 변수

*nMsg*<br/>
예약되어 있습니다.

*wParam*<br/>
예약되어 있습니다.

*lParam*<br/>
예약되어 있습니다.

*bHandled*<br/>
창 메시지가 성공적으로 처리 되었는지 여부를 나타내는 플래그입니다. 기본값은 FALSE입니다.

### <a name="return-value"></a>반환 값

항상 1을 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 포커스를 받은 컨테이너에 알림을 보냅니다.

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a> CComControlBase::P reTranslateAccelerator

사용자 고유의 키보드 액셀러레이터 처리기를 제공 하려면이 메서드를 재정의 합니다.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>매개 변수

*pMsg*<br/>
예약되어 있습니다.

*hRet*<br/>
예약되어 있습니다.

### <a name="return-value"></a>반환 값

기본적으로는 FALSE를 반환 합니다.

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a> CComControlBase::SendOnClose

컨트롤이 닫 혔 음을 advise 표시자에 등록 하 여 모든 advise 싱크에 알립니다.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤이 해당 advise 싱크를 닫 혔 음을 알려 주는 알림을 보냅니다.

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a> CComControlBase:: SendOnDataChange

컨트롤 데이터가 변경 되었음을 advise 표시자에 등록 하 여 모든 advise 싱크에 알립니다.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>매개 변수

*advf*<br/>
[IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) 를 호출 하는 방법을 지정 하는 Advise 플래그입니다. 값은 [ADVF](/windows/win32/api/objidl/ne-objidl-advf) 열거형에서 가져온 값입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a> CComControlBase:: SendOnRename

컨트롤에 새 모니커가 있음을 advise 표시자에 등록 한 모든 advise 싱크에 알립니다.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>매개 변수

*pmk*<br/>
컨트롤의 새 모니커에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤의 모니커가 변경 되었다는 알림을 보냅니다.

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a> CComControlBase::SendOnSave

컨트롤이 저장 되었음을 알리는 advise 표시자에 등록 된 모든 advise 싱크에 알립니다.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

컨트롤에서 데이터를 방금 저장 한 알림을 보냅니다.

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a> CComControlBase::SendOnViewChange

등록 된 모든 advise 싱크에 컨트롤의 뷰가 변경 되었음을 알립니다.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>매개 변수

*dwAspect*<br/>
컨트롤의 측면이 나 뷰입니다.

*lindex*<br/>
변경 된 보기의 일부입니다. -1만 유효 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`SendOnViewChange`[IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange)를 호출 합니다. 현재 지원 되는 *lindex* 의 유일한 값은-1 이며이는 전체 뷰가 관심 임을 나타냅니다.

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a> CComControlBase:: SetControlFocus

컨트롤에서 키보드 포커스를 설정 하거나 제거 합니다.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>매개 변수

*bGrab*<br/>
TRUE 이면 호출 하는 컨트롤에 키보드 포커스를 설정 합니다. FALSE 이면 포커스를가지고 있는 경우 호출 하는 컨트롤에서 키보드 포커스를 제거 합니다.

### <a name="return-value"></a>반환 값

컨트롤이 포커스를 받으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

창 컨트롤의 경우 Windows API 함수 [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) 가 호출 됩니다. 창 없는 컨트롤의 경우 [IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) 가 호출 됩니다. 이 호출을 통해 창 없는 컨트롤은 키보드 포커스를 가져오고 창 메시지에 응답할 수 있습니다.

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a> CComControlBase:: SetDirty

데이터 멤버를 `m_bRequiresSave` *bdirty* 의 값으로 설정 합니다.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>매개 변수

*bDirty*<br/>
데이터 멤버 [CComControlBase:: m_bRequiresSave](#m_brequiressave)의 값입니다.

### <a name="remarks"></a>설명

`SetDirty(TRUE)` 컨트롤이 마지막으로 저장 된 이후 변경 되었음을 플래그를 지정 하기 위해 호출 해야 합니다. 의 값은 `m_bRequiresSave` [CComControlBase:: getdirty](#getdirty)를 사용 하 여 검색 됩니다.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
