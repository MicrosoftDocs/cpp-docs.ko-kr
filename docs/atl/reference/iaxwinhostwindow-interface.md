---
description: '자세히 알아보기: IAxWinHostWindow 인터페이스'
title: IAxWinHostWindow 인터페이스
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: 86cccd2b9ae19d5020cd1cf7ff2f0aff8759060e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139713"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 인터페이스

이 인터페이스는 컨트롤과 해당 호스트 개체를 조작 하기 위한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[AttachControl](#attachcontrol)|기존 컨트롤을 호스트 개체에 연결 합니다.|
|[CreateControl](#createcontrol)|컨트롤을 만들어 호스트 개체에 연결 합니다.|
|[CreateControlEx](#createcontrolex)|컨트롤을 만들어 호스트 개체에 연결 하 고 필요에 따라 이벤트 처리기를 설정 합니다.|
|[QueryControl](#querycontrol)|호스팅된 컨트롤에 대 한 인터페이스 포인터를 반환 합니다.|
|[SetExternalDispatch](#setexternaldispatch)|외부 인터페이스를 설정 `IDispatch` 합니다.|
|[SetExternalUIHandler](#setexternaluihandler)|외부 인터페이스를 설정 `IDocHostUIHandlerDispatch` 합니다.|

## <a name="remarks"></a>설명

이 인터페이스는 ATL의 ActiveX 컨트롤 호스팅 개체에 의해 노출 됩니다. 이 인터페이스의 메서드를 호출 하 여 호스트 개체에 컨트롤을 만들거나 연결 하거나, 호스트 된 컨트롤에서 인터페이스를 가져오거나, 웹 브라우저를 호스팅할 때 사용할 외부 인터페이스 또는 UI 처리기를 설정 합니다.

## <a name="requirements"></a>요구 사항

이 인터페이스의 정의는 아래와 같이 IDL 또는 c + +로 사용할 수 있습니다.

|정의 유형|파일|
|---------------------|----------|
|IDL|ATLIFace. idl|
|C++|ATLIFace. .h (설명서에도 포함 됨)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow:: AttachControl

*HWnd* 로 식별 된 창을 사용 하 여 기존 (및 이전에 초기화 된) 컨트롤을 호스트 개체에 연결 합니다.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*pUnkControl*<br/>
진행 `IUnknown` 호스트 개체에 연결할 컨트롤의 인터페이스에 대 한 포인터입니다.

*hWnd*<br/>
진행 호스팅을 위해 사용할 창에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow:: CreateControl

컨트롤을 만들어 초기화 하 고 *hWnd* 로 식별 되는 창에 호스팅합니다.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>매개 변수

*lpTricsData*<br/>
진행 만들 컨트롤을 식별 하는 문자열입니다. 에는 CLSID (중괄호를 포함 해야 함), ProgID, URL 또는 원시 HTML ( **MSHTML:**)이 있을 수 있습니다.

*hWnd*<br/>
진행 호스팅을 위해 사용할 창에 대 한 핸들입니다.

*pStream*<br/>
진행 컨트롤의 초기화 데이터를 포함 하는 스트림에 대 한 인터페이스 포인터입니다. NULL일 수 있습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 창은 메시지를 컨트롤에 반영 하 고 다른 컨테이너 기능을 사용할 수 있도록이 인터페이스를 노출 하는 호스트 개체에 의해 서브클래싱된 것입니다.

이 메서드 호출은 [Iaxwinhostwindow:: CreateControlEx](#createcontrolex)를 호출 하는 것과 같습니다.

사용이 허가 된 ActiveX 컨트롤을 만들려면 [Iaxwinhostwindowlic:: CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)를 참조 하세요.

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow:: CreateControlEx

ActiveX 컨트롤을 만들고 초기화 하며 지정한 창에 호스팅합니다. [Iaxwinhostwindow:: CreateControl](#createcontrol)과 비슷합니다.

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>매개 변수

*lpTricsData*<br/>
진행 만들 컨트롤을 식별 하는 문자열입니다. 는 CLSID (는 중괄호를 포함 해야 함), ProgID, URL 또는 원시 HTML ( **MSHTML:**)이 될 수 있습니다.

*hWnd*<br/>
진행 호스팅을 위해 사용할 창에 대 한 핸들입니다.

*pStream*<br/>
진행 컨트롤의 초기화 데이터를 포함 하는 스트림에 대 한 인터페이스 포인터입니다. NULL일 수 있습니다.

*ppUnk*<br/>
제한이 만든 컨트롤의 인터페이스를 받는 포인터의 주소입니다 `IUnknown` . NULL일 수 있습니다.

*riidAdvise*<br/>
진행 포함 된 개체의 송신 인터페이스에 대 한 인터페이스 식별자입니다. IID_NULL 수 있습니다.

*punkAdvise*<br/>
진행 `IUnknown` 로 지정 된 포함 된 개체의 연결 지점에 연결할 싱크 개체의 인터페이스에 대 한 포인터입니다 `iidSink` .

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

메서드와 달리 `CreateControl` 를 `CreateControlEx` 사용 하면 새로 만든 컨트롤에 대 한 인터페이스 포인터를 받고 컨트롤에서 발생 한 이벤트를 수신 하도록 이벤트 싱크를 설정할 수도 있습니다.

사용이 허가 된 ActiveX 컨트롤을 만들려면 [Iaxwinhostwindowlic:: CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)를 참조 하세요.

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow:: QueryControl

호스팅된 컨트롤에서 제공 하는 지정 된 인터페이스 포인터를 반환 합니다.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
진행 요청 된 컨트롤의 인터페이스 ID입니다.

*ppvObject*<br/>
제한이 만든 컨트롤의 지정 된 인터페이스를 받는 포인터의 주소입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow:: SetExternalDispatch

[IDocHostUIHandlerDispatch:: getexternal](../../atl/reference/idochostuihandlerdispatch-interface.md) 메서드를 통해 포함 된 컨트롤에 사용할 수 있는 외부 컨트롤을 설정 합니다.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
진행 인터페이스에 대 한 포인터 `IDispatch` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow:: SetExternalUIHandler

개체에 대 한 외부 [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) 인터페이스를 설정 하려면이 함수를 호출 `CAxWindow` 합니다.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>매개 변수

*pDisp*<br/>
진행 인터페이스에 대 한 포인터 `IDocHostUIHandlerDispatch` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 함수는 호스트의 사이트에서 인터페이스를 쿼리 하는 컨트롤 (예: 웹 브라우저 컨트롤)에 사용 됩니다 `IDocHostUIHandlerDispatch` .

## <a name="see-also"></a>참고 항목

[IAxWinAmbientDispatch 인터페이스](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
