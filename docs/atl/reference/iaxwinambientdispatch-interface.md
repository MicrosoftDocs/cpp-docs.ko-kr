---
title: IAxWinAmbientDispatch 인터페이스
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: dbd682451ca5499aef4b16b3b51feba8411bdd12
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352962"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch 인터페이스

이 인터페이스는 호스트 된 컨트롤 또는 컨테이너의 특성을 지정 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|Description|
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|`AllowContextMenu`속성은 호스팅된 컨트롤이 자체 상황에 맞는 메뉴를 표시할 수 있는지 여부를 지정 합니다.|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI`속성은 호스팅된 컨트롤이 자체 사용자 인터페이스를 표시할 수 있는지 여부를 지정 합니다.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation`속성은 컨테이너가 창 없는 활성화를 허용할지 여부를 지정 합니다.|
|[get_BackColor](#get_backcolor)|`BackColor`속성은 컨테이너의 앰비언트 배경색을 지정 합니다.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` 는 컨트롤이 기본 컨트롤 인지 여부를 확인할 수 있도록 하는 앰비언트 속성입니다.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags`속성은 두 번 클릭에 대 한 응답으로 수행 해야 하는 작업을 지정 합니다.|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags`속성은 호스트 개체의 사용자 인터페이스 기능을 지정 합니다.|
|[get_Font](#get_font)|`Font`속성은 컨테이너의 앰비언트 글꼴을 지정 합니다.|
|[get_ForeColor](#get_forecolor)|`ForeColor`속성은 컨테이너의 앰비언트 전경색을 지정 합니다.|
|[get_LocaleID](#get_localeid)|`LocaleID`속성은 컨테이너의 앰비언트 로캘 ID를 지정 합니다.|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect`앰비언트 속성은 컨테이너가 호스팅된 컨트롤에 메시지를 반영 하는지 여부를 지정 합니다.|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath`속성은 사용자 설정에 대 한 레지스트리 키 경로를 지정 합니다.|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles`앰비언트 속성을 사용 하면 컨트롤에서 잡기 핸들을 사용 하 여 자체적으로 그려야 하는지 여부를 확인할 수 있습니다.|
|[get_ShowHatching](#get_showhatching)|`ShowHatching`앰비언트 속성을 사용 하면 컨트롤에서 자동으로 해치를 그릴지 여부를 확인할 수 있습니다.|
|[get_UserMode](#get_usermode)|`UserMode`속성은 컨테이너의 앰비언트 사용자 모드를 지정 합니다.|
|[put_AllowContextMenu](#put_allowcontextmenu)|`AllowContextMenu`속성은 호스팅된 컨트롤이 자체 상황에 맞는 메뉴를 표시할 수 있는지 여부를 지정 합니다.|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI`속성은 호스팅된 컨트롤이 자체 사용자 인터페이스를 표시할 수 있는지 여부를 지정 합니다.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation`속성은 컨테이너가 창 없는 활성화를 허용할지 여부를 지정 합니다.|
|[put_BackColor](#put_backcolor)|`BackColor`속성은 컨테이너의 앰비언트 배경색을 지정 합니다.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` 는 컨트롤이 기본 컨트롤 인지 여부를 확인할 수 있도록 하는 앰비언트 속성입니다.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags`속성은 두 번 클릭에 대 한 응답으로 수행 해야 하는 작업을 지정 합니다.|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags`속성은 호스트 개체의 사용자 인터페이스 기능을 지정 합니다.|
|[put_Font](#put_font)|`Font`속성은 컨테이너의 앰비언트 글꼴을 지정 합니다.|
|[put_ForeColor](#put_forecolor)|`ForeColor`속성은 컨테이너의 앰비언트 전경색을 지정 합니다.|
|[put_LocaleID](#put_localeid)|`LocaleID`속성은 컨테이너의 앰비언트 로캘 ID를 지정 합니다.|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect`앰비언트 속성은 컨테이너가 호스팅된 컨트롤에 메시지를 반영 하는지 여부를 지정 합니다.|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath`속성은 사용자 설정에 대 한 레지스트리 키 경로를 지정 합니다.|
|[put_UserMode](#put_usermode)|`UserMode`속성은 컨테이너의 앰비언트 사용자 모드를 지정 합니다.|

## <a name="remarks"></a>설명

이 인터페이스는 ATL의 ActiveX 컨트롤 호스팅 개체에 의해 노출 됩니다. 이 인터페이스의 메서드를 호출 하 여 호스팅된 컨트롤에서 사용할 수 있는 앰비언트 속성을 설정 하거나 컨테이너 동작의 다른 측면을 지정할 수 있습니다. 에서 제공 하는 속성을 보완 하려면 `IAxWinAmbientDispatch` [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)를 사용 합니다.

<xref:System.Windows.Forms.AxHost> 는 `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` 코드를 포함 하는 typelib와 관련 된 형식 정보를 로드 하려고 합니다.

ATL90.dll에 연결 하는 경우 **Axhost** 는 DLL의 typelib에서 형식 정보를 로드 합니다.

자세한 내용은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요.

## <a name="requirements"></a>요구 사항

이 인터페이스의 정의는 아래 표에 나와 있는 것 처럼 다양 한 형식으로 제공 됩니다.

|정의 형식|파일|
|---------------------|----------|
|IDL|atliface. idl|
|형식 라이브러리|ATL.dll|
|C++|atliface. .h (설명서에도 포함 됨)|

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a> IAxWinAmbientDispatch:: get_AllowContextMenu

`AllowContextMenu`속성은 호스팅된 컨트롤이 자체 상황에 맞는 메뉴를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>매개 변수

*pbAllowContextMenu*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a> IAxWinAmbientDispatch:: get_AllowShowUI

`AllowShowUI`속성은 호스팅된 컨트롤이 자체 사용자 인터페이스를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>매개 변수

*pbAllowShowUI*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a> IAxWinAmbientDispatch:: get_AllowWindowlessActivation

`AllowWindowlessActivation`속성은 컨테이너가 창 없는 활성화를 허용할지 여부를 지정 합니다.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>매개 변수

*pbAllowWindowless 없음*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a> IAxWinAmbientDispatch:: get_BackColor

`BackColor`속성은 컨테이너의 앰비언트 배경색을 지정 합니다.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>매개 변수

*pclrBackground*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 호스트 창의 부모가 대화 인지 여부에 따라 COLOR_BTNFACE 또는 COLOR_WINDOW를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a> IAxWinAmbientDispatch:: get_DisplayAsDefault

`DisplayAsDefault` 는 컨트롤이 기본 컨트롤 인지 여부를 확인할 수 있도록 하는 앰비언트 속성입니다.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>매개 변수

*pbDisplayAsDefault*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a> IAxWinAmbientDispatch:: get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`속성은 두 번 클릭에 대 한 응답으로 수행 해야 하는 작업을 지정 합니다.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>매개 변수

*pdwDocHostDoubleClickFlags*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIDBLCLK_DEFAULT를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a> IAxWinAmbientDispatch:: get_DocHostFlags

`DocHostFlags`속성은 호스트 개체의 사용자 인터페이스 기능을 지정 합니다.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>매개 변수

*pdwDocHostFlags*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIFLAG_NO3DBORDER를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a> IAxWinAmbientDispatch:: get_Font

`Font`속성은 컨테이너의 앰비언트 글꼴을 지정 합니다.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>매개 변수

*pFont*<br/>
제한이 `IFontDisp` 이 속성의 현재 값을 받는 데 사용 되는 인터페이스 포인터의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현에서는 기본 GUI 글꼴이 나 시스템 글꼴을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a> IAxWinAmbientDispatch:: get_ForeColor

`ForeColor`속성은 컨테이너의 앰비언트 전경색을 지정 합니다.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>매개 변수

*pclrForeground*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 시스템 창 텍스트 색을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a> IAxWinAmbientDispatch:: get_LocaleID

`LocaleID`속성은 컨테이너의 앰비언트 로캘 ID를 지정 합니다.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>매개 변수

*plcidLocaleID*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 사용자의 기본 로캘을이 속성의 기본값으로 사용 합니다.

이 메서드를 사용 하 여 앰비언트 LocalID (컨트롤이 사용 되는 프로그램의 LocaleID)를 검색할 수 있습니다. LocaleID를 알고 있으면 코드를 호출 하 여 리소스 파일이 나 위성 DLL에서 로캘별 캡션, 오류 메시지 텍스트 등을 로드할 수 있습니다.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a> IAxWinAmbientDispatch:: get_MessageReflect

`MessageReflect`앰비언트 속성은 컨테이너가 호스팅된 컨트롤에 메시지를 반영 하는지 여부를 지정 합니다.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>매개 변수

*pbMessageReflect*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a> IAxWinAmbientDispatch:: get_OptionKeyPath

`OptionKeyPath`속성은 사용자 설정에 대 한 레지스트리 키 경로를 지정 합니다.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>매개 변수

*pbstrOptionKeyPath*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a> IAxWinAmbientDispatch:: get_ShowGrabHandles

`ShowGrabHandles`앰비언트 속성을 사용 하면 컨트롤에서 잡기 핸들을 사용 하 여 자체적으로 그려야 하는지 여부를 확인할 수 있습니다.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>매개 변수

*pbShowGrabHandles*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 항상이 속성의 값으로 VARIANT_FALSE을 반환 합니다.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a> IAxWinAmbientDispatch:: get_ShowHatching

`ShowHatching`앰비언트 속성을 사용 하면 컨트롤에서 자동으로 해치를 그릴지 여부를 확인할 수 있습니다.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>매개 변수

*pbShowHatching*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 항상이 속성의 값으로 VARIANT_FALSE을 반환 합니다.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a> IAxWinAmbientDispatch:: get_UserMode

`UserMode`속성은 컨테이너의 앰비언트 사용자 모드를 지정 합니다.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>매개 변수

*pbUserMode*<br/>
제한이 이 속성의 현재 값을 받을 변수의 주소입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a> IAxWinAmbientDispatch::p ut_AllowContextMenu

`AllowContextMenu`속성은 호스팅된 컨트롤이 자체 상황에 맞는 메뉴를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>매개 변수

*bAllowContextMenu*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a> IAxWinAmbientDispatch::p ut_AllowShowUI

`AllowShowUI`속성은 호스팅된 컨트롤이 자체 사용자 인터페이스를 표시할 수 있는지 여부를 지정 합니다.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>매개 변수

*bAllowShowUI*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a> IAxWinAmbientDispatch::p ut_AllowWindowlessActivation

`AllowWindowlessActivation`속성은 컨테이너가 창 없는 활성화를 허용할지 여부를 지정 합니다.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>매개 변수

*bAllowWindowless 없는*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a> IAxWinAmbientDispatch::p ut_BackColor

`BackColor`속성은 컨테이너의 앰비언트 배경색을 지정 합니다.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>매개 변수

*clrBackground*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 호스트 창의 부모가 대화 인지 여부에 따라 COLOR_BTNFACE 또는 COLOR_WINDOW를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a> IAxWinAmbientDispatch::p ut_DisplayAsDefault

`DisplayAsDefault` 는 컨트롤이 기본 컨트롤 인지 여부를 확인할 수 있도록 하는 앰비언트 속성입니다.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>매개 변수

*bDisplayAsDefault*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_FALSE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a> IAxWinAmbientDispatch::p ut_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`속성은 두 번 클릭에 대 한 응답으로 수행 해야 하는 작업을 지정 합니다.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>매개 변수

*dwDocHostDoubleClickFlags*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIDBLCLK_DEFAULT를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a> IAxWinAmbientDispatch::p ut_DocHostFlags

`DocHostFlags`속성은 호스트 개체의 사용자 인터페이스 기능을 지정 합니다.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>매개 변수

*dwDocHostFlags*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 DOCHOSTUIFLAG_NO3DBORDER를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a> IAxWinAmbientDispatch::p ut_Font

`Font`속성은 컨테이너의 앰비언트 글꼴을 지정 합니다.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>매개 변수

*pFont*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현에서는 기본 GUI 글꼴이 나 시스템 글꼴을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a> IAxWinAmbientDispatch::p ut_ForeColor

`ForeColor`속성은 컨테이너의 앰비언트 전경색을 지정 합니다.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>매개 변수

*clrForeground*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 시스템 창 텍스트 색을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a> IAxWinAmbientDispatch::p ut_LocaleID

`LocaleID`속성은 컨테이너의 앰비언트 로캘 ID를 지정 합니다.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>매개 변수

*lcidLocaleID*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 사용자의 기본 로캘을이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a> IAxWinAmbientDispatch::p ut_MessageReflect

`MessageReflect`앰비언트 속성은 컨테이너가 호스팅된 컨트롤에 메시지를 반영 하는지 여부를 지정 합니다.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>매개 변수

*bMessageReflect*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a> IAxWinAmbientDispatch::p ut_OptionKeyPath

`OptionKeyPath`속성은 사용자 설정에 대 한 레지스트리 키 경로를 지정 합니다.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>매개 변수

*bstrOptionKeyPath*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a> IAxWinAmbientDispatch::p ut_UserMode

`UserMode`속성은 컨테이너의 앰비언트 사용자 모드를 지정 합니다.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>매개 변수

*bUserMode*<br/>
진행 이 속성의 새 값입니다.

### <a name="return-value"></a>Return Value

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

ATL 호스트 개체 구현은 VARIANT_TRUE를이 속성의 기본값으로 사용 합니다.

## <a name="see-also"></a>참고 항목

[IAxWinAmbientDispatchEx 인터페이스](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow 인터페이스](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
