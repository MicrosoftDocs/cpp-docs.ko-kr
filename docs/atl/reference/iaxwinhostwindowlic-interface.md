---
title: IAxWinHostWindowLic 인터페이스
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: d7a63fc63b8abcf8574ea9a2fed2556635dba045
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352949"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic 인터페이스

이 인터페이스는 사용이 허가 된 컨트롤과 해당 호스트 개체를 조작 하기 위한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|Description|
|-|-|
|[CreateControlLic](#createcontrollic)|라이선스가 있는 컨트롤을 만들어 호스트 개체에 연결 합니다.|
|[CreateControlLicEx](#createcontrollicex)|라이선스가 있는 컨트롤을 만들어 호스트 개체에 연결 하 고 필요에 따라 이벤트 처리기를 설정 합니다.|

## <a name="remarks"></a>설명

`IAxWinHostWindowLic`[Iaxwinhostwindow](../../atl/reference/iaxwinhostwindow-interface.md) 에서 상속 하 고 사용이 허가 된 컨트롤 만들기를 지 원하는 메서드를 추가 합니다.

이 인터페이스의 멤버를 사용 하는 샘플은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요.

## <a name="requirements"></a>요구 사항

이 인터페이스의 정의는 아래와 같이 IDL 또는 c + +로 사용할 수 있습니다.

|정의 유형|파일|
|---------------------|----------|
|IDL|ATLIFace. idl|
|C++|ATLIFace. .h (설명서에도 포함 됨)|

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a> IAxWinHostWindowLic:: CreateControlLic

라이선스가 있는 컨트롤을 만들어 초기화 하 고로 식별 되는 창에 호스트 `hWnd` 합니다.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>매개 변수

*bstrLic*<br/>
진행 컨트롤의 라이선스 키를 포함 하는 BSTR입니다.

### <a name="remarks"></a>설명

나머지 매개 변수 및 반환 값에 대 한 설명은 [Iaxwinhostwindow:: CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) 을 참조 하세요.

이 메서드 호출은 [Iaxwinhostwindowlic:: CreateControlLicEx](#createcontrollicex) 를 호출 하는 것과 같습니다.

### <a name="example"></a>예제

을 사용 하는 샘플은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요 `IAxWinHostWindowLic::CreateControlLic` .

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a> IAxWinHostWindowLic:: CreateControlLicEx

사용이 허가 된 ActiveX 컨트롤을 만들고 초기화 하며 지정한 창에 호스팅합니다. [Iaxwinhostwindow:: CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)과 비슷합니다.

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>매개 변수

*bstrLic*<br/>
진행 컨트롤의 라이선스 키를 포함 하는 BSTR입니다.

### <a name="remarks"></a>설명

나머지 매개 변수 및 반환 값에 대 한 설명은 [Iaxwinhostwindow:: CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) 를 참조 하세요.

### <a name="example"></a>예제

을 사용 하는 샘플은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요 `IAxWinHostWindowLic::CreateControlLicEx` .
