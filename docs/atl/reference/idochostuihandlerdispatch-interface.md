---
description: '자세히 알아보기: IDocHostUIHandlerDispatch 인터페이스'
title: IDocHostUIHandlerDispatch 인터페이스
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 59f9975f48a7ae63d5820a9c05f9baa49b8a5f25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158376"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 인터페이스

Microsoft HTML 구문 분석 및 렌더링 엔진에 대 한 인터페이스입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

> [!NOTE]
> 다음 표에서는 [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) 인터페이스 멤버에 대 한 INet SDK 참조 항목에 대 한 링크를 제공 합니다. `IDocHostUIHandlerDispatch` 는와 동일한 기능을 포함 `IDocUIHostHandler` 하며, `IDocHostUIHandlerDispatch` 이는 `IDocUIHostHandler` 사용자 지정 인터페이스입니다.

|Name|설명|
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|[IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)의 MSHTML 구현에서 호출 됩니다. MSHTML이 모달 UI를 표시 하는 경우에도 호출 됩니다.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|호스트가 MSHTML의 데이터 개체를 바꿀 수 있도록 MSHTML에 의해 호스트에서 호출 됩니다.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|호스트가 대체 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)을 제공할 수 있도록 놓기 대상으로 사용 되는 경우 MSHTML에 의해 호출 됩니다.|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|호스트의 IDispatch 인터페이스를 가져오기 위해 MSHTML에 의해 호출 됩니다.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|MSHTML 호스트의 UI 기능을 검색 합니다.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|MSHTML이 사용자 기본 설정을 저장 하는 레지스트리 키를 반환 합니다.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|MSHTML에서 메뉴와 도구 모음을 제거 하면 호출 됩니다.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|[IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)의 MSHTML 구현에서 호출 됩니다.|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|[IOleInPlaceActiveObject:: On Windowactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)의 MSHTML 구현에서 호출 됩니다.|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|[IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)의 MSHTML 구현에서 호출 됩니다.|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|상황에 맞는 메뉴를 표시 하기 위해 MSHTML에서 호출 됩니다.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|호스트가 MSHTML 메뉴와 도구 모음을 대체할 수 있습니다.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|[IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) 또는 [IOleControlSite:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) 가 호출 될 때 MSHTML에 의해 호출 됩니다.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|호스트가 로드할 URL을 수정할 수 있도록 MSHTML에서 호출 됩니다.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|명령 상태가 변경되었음을 호스트에 알립니다.|

## <a name="remarks"></a>설명

호스트는이 인터페이스를 구현 하 여 Microsoft HTML 구문 분석 및 MSHTML (구문 분석 및 렌더링 엔진)에서 사용 하는 메뉴, 도구 모음 및 상황에 맞는 메뉴를 바꿀 수 있습니다.

## <a name="requirements"></a>요구 사항

이 인터페이스의 정의는 아래와 같이 IDL 또는 c + +로 사용할 수 있습니다.

|정의 유형|파일|
|---------------------|----------|
|IDL|ATLIFace. idl|
|C++|ATLIFace. .h (설명서에도 포함 됨)|

## <a name="see-also"></a>참고 항목

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
