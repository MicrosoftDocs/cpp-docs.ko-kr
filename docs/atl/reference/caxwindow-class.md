---
description: '자세히 알아보기: CAxWindow 클래스'
title: CAxWindow 클래스
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 0b1cdabbce4fd6a36f6f3e9fb15b3f28249065c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146993"
---
# <a name="caxwindow-class"></a>CAxWindow 클래스

이 클래스는 ActiveX 컨트롤을 호스트 하는 창을 조작 하기 위한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CAxWindow : public CWindow
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|함수|설명|
|-|-|
|[AttachControl](#attachcontrol)|기존 ActiveX 컨트롤을 개체에 연결 `CAxWindow` 합니다.|
|[CAxWindow](#caxwindow)|`CAxWindow` 개체를 생성합니다.|
|[CreateControl](#createcontrol)|ActiveX 컨트롤을 만들어 초기화 하 고 창에서 호스팅합니다 `CAxWindow` .|
|[CreateControlEx](#createcontrolex)|ActiveX 컨트롤을 만들고 컨트롤에서 인터페이스 포인터 (또는 포인터)를 검색 합니다.|
|[GetWndClassName](#getwndclassname)|정적인 개체의 미리 정의 된 클래스 이름을 검색 `CAxWindow` 합니다.|
|[QueryControl](#querycontrol)|`IUnknown`호스팅된 ActiveX 컨트롤의를 검색 합니다.|
|[QueryHost](#queryhost)|`IUnknown`개체의 포인터를 검색 `CAxWindow` 합니다.|
|[SetExternalDispatch](#setexternaldispatch)|개체에서 사용 하는 외부 디스패치 인터페이스를 설정 합니다 `CAxWindow` .|
|[SetExternalUIHandler](#setexternaluihandler)|개체에서 사용 하는 외부 인터페이스를 설정 `IDocHostUIHandler` `CAxWindow` 합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 =](#operator_eq)|기존 개체에 HWND를 할당 `CAxWindow` 합니다.|

## <a name="remarks"></a>설명

이 클래스는 ActiveX 컨트롤을 호스트 하는 창을 조작 하기 위한 메서드를 제공 합니다. 호스트는로 래핑된 " **AtlAxWin80"** 에서 제공 됩니다 `CAxWindow` .

클래스는 `CAxWindow` 클래스의 특수화로 구현 됩니다 `CAxWindowT` . 이 특수화는 다음과 같이 선언 됩니다.

`typedef CAxWindowT<CWindow> CAxWindow;`

기본 클래스를 변경 해야 하는 경우를 사용 하 `CAxWindowT` 고 새 기본 클래스를 템플릿 인수로 지정할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a> CAxWindow:: AttachControl

새 호스트 개체가 아직 없는 경우 새로 만들고 지정 된 컨트롤을 호스트에 연결 합니다.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>매개 변수

*pControl*<br/>
진행 컨트롤의에 대 한 포인터 `IUnknown` 입니다.

*ppUnkContainer*<br/>
제한이 호스트의에 대 한 포인터 `IUnknown` `AxWin` 입니다 (개체).

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

연결 중인 컨트롤 개체는를 호출 하기 전에 올바르게 초기화 되어야 합니다 `AttachControl` .

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a> CAxWindow:: CAxWindow

`CAxWindow`기존 창 개체 핸들을 사용 하 여 개체를 생성 합니다.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
기존 창 개체에 대 한 핸들입니다.

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a> CAxWindow:: CreateControl

ActiveX 컨트롤을 만들고 초기화하며 지정한 창에 호스팅합니다.

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
컨트롤을 만들 문자열에 대 한 포인터입니다. 다음 방법 중 하나로 형식을 지정 해야 합니다.

- 와 같은 ProgID `"MSCAL.Calendar.7"`

- 와 같은 CLSID `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL (예:) `"<https://www.microsoft.com>"`

- 과 같은 활성 문서에 대 한 참조입니다. `"file://\\\Documents\MyDoc.doc"`

- 와 같은 HTML의 조각 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 는 MSHTML 스트림으로 지정 되도록 HTML 조각 앞에와 야 합니다. Windows Mobile platform에서는 ProgID와 CLSID만 지원 됩니다. CE IE를 지 원하는 Windows Mobile이 아닌 임베디드 플랫폼 Windows CE ProgID, CLSID, URL, 활성 문서에 대 한 참조 및 HTML 조각을 비롯 한 모든 형식을 지원 합니다.

*pStream*<br/>
진행 컨트롤의 속성을 초기화 하는 데 사용 되는 스트림에 대 한 포인터입니다. NULL일 수 있습니다.

*ppUnkContainer*<br/>
제한이 컨테이너의를 받는 포인터의 주소입니다 `IUnknown` . NULL일 수 있습니다.

*dwResID*<br/>
HTML 리소스의 리소스 ID입니다. 지정 된 리소스를 사용 하 여 WebBrowser 컨트롤이 만들어지고 로드 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 메서드의 두 번째 버전을 사용 하는 경우 HTML 컨트롤이 만들어지고 *dwResID* 으로 식별 되는 리소스에 바인딩됩니다.

이 메서드는를 호출 하는 것과 동일한 결과를 제공 합니다.

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

사용이 허가 된 ActiveX 컨트롤을 만들고, 초기화 하 고, 호스트 하려면 [CAxWindow2T:: CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) 를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 샘플은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요 `CreateControl` .

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a> CAxWindow:: CreateControlEx

ActiveX 컨트롤을 만들고 초기화하며 지정한 창에 호스팅합니다.

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
컨트롤을 만들 문자열에 대 한 포인터입니다. 다음 방법 중 하나로 형식을 지정 해야 합니다.

- 와 같은 ProgID `"MSCAL.Calendar.7"`

- 와 같은 CLSID `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL (예:) `"<https://www.microsoft.com>"`

- 과 같은 활성 문서에 대 한 참조입니다. `"file://\\\Documents\MyDoc.doc"`

- 와 같은 HTML의 조각 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 는 MSHTML 스트림으로 지정 되도록 HTML 조각 앞에와 야 합니다. Windows Mobile platform에서는 ProgID와 CLSID만 지원 됩니다. CE IE를 지 원하는 Windows Mobile이 아닌 임베디드 플랫폼 Windows CE ProgID, CLSID, URL, 활성 문서에 대 한 참조 및 HTML 조각을 비롯 한 모든 형식을 지원 합니다.

*pStream*<br/>
진행 컨트롤의 속성을 초기화 하는 데 사용 되는 스트림에 대 한 포인터입니다. NULL일 수 있습니다.

*ppUnkContainer*<br/>
제한이 컨테이너의를 받는 포인터의 주소입니다 `IUnknown` . NULL일 수 있습니다.

*ppUnkControl*<br/>
제한이 컨트롤의를 받는 포인터의 주소입니다 `IUnknown` . NULL일 수 있습니다.

*iidSink*<br/>
진행 포함 된 개체의 송신 인터페이스에 대 한 인터페이스 식별자입니다. IID_NULL 수 있습니다.

*punkSink*<br/>
진행 `IUnknown` *Iidsink* 에서 지정한 포함 된 개체의 연결 지점에 연결할 싱크 개체의 인터페이스에 대 한 포인터입니다.

*dwResID*<br/>
진행 HTML 리소스의 리소스 ID입니다. 지정 된 리소스를 사용 하 여 WebBrowser 컨트롤이 만들어지고 로드 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 메서드는 [Caxwindow:: CreateControl](#createcontrol)과 비슷하지만,이 메서드와 달리 `CreateControlEx` 새로 만든 컨트롤에 대 한 인터페이스 포인터를 받고 컨트롤에서 발생 한 이벤트를 수신 하도록 이벤트 싱크를 설정할 수도 있습니다.

사용이 허가 된 ActiveX 컨트롤을 만들고, 초기화 하 고, 호스트 하려면 [CAxWindow2T:: CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) 를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 샘플은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요 `CreateControlEx` .

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a> CAxWindow:: GetWndClassName

창 클래스의 이름을 검색 합니다.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>반환 값

사용이 허가 되지 않은 ActiveX 컨트롤을 호스팅할 수 있는 창 클래스의 이름을 포함 하는 문자열에 대 한 포인터입니다.

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a> CAxWindow:: operator =

기존 개체에 HWND를 할당 `CAxWindow` 합니다.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
기존 창에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

현재 개체에 대 한 참조를 반환 합니다 `CAxWindow` .

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a> CAxWindow:: QueryControl

호스팅된 컨트롤의 지정 된 인터페이스를 검색 합니다.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 컨트롤 인터페이스의 IID를 지정 합니다.

*ppUnk*<br/>
제한이 컨트롤의 인터페이스에 대 한 포인터입니다. 이 메서드의 템플릿 버전에서는 연결 된 UUID를 사용 하는 형식화 된 인터페이스가 전달 되는 한 참조 ID가 필요 하지 않습니다.

*Q*<br/>
진행 쿼리 되는 인터페이스입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a> CAxWindow:: QueryHost

호스트의 지정 된 인터페이스를 반환 합니다.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 컨트롤 인터페이스의 IID를 지정 합니다.

*ppUnk*<br/>
제한이 호스트의 인터페이스에 대 한 포인터입니다. 이 메서드의 템플릿 버전에서는 연결 된 UUID를 사용 하는 형식화 된 인터페이스가 전달 되는 한 참조 ID가 필요 하지 않습니다.

*Q*<br/>
진행 쿼리 되는 인터페이스입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

호스트의 인터페이스를 사용 하면에 의해 구현 되는 창 호스팅 코드의 기본 기능에 액세스할 수 있습니다 `AxWin` .

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> CAxWindow:: SetExternalDispatch

개체에 대 한 외부 디스패치 인터페이스를 설정 `CAxWindow` 합니다.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
진행 인터페이스에 대 한 포인터 `IDispatch` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> CAxWindow:: SetExternalUIHandler

개체에 대 한 외부 [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) 인터페이스를 설정 `CAxWindow` 합니다.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>매개 변수

*pUIHandler*<br/>
진행 인터페이스에 대 한 포인터 `IDocHostUIHandlerDispatch` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

외부 `IDocHostUIHandlerDispatch` 인터페이스는 호스트의 사이트에서 인터페이스를 쿼리 하는 컨트롤에 사용 됩니다 `IDocHostUIHandlerDispatch` . WebBrowser 컨트롤은이를 수행 하는 한 가지 컨트롤입니다.

## <a name="see-also"></a>참고 항목

[ATLCON 샘플](../../overview/visual-cpp-samples.md)<br/>
[CWindow 클래스](../../atl/reference/cwindow-class.md)<br/>
[복합 컨트롤 기본 사항](../../atl/atl-composite-control-fundamentals.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[컨트롤 포함 FAQ](../../atl/atl-control-containment-faq.md)
