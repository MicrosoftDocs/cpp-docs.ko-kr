---
description: '자세히 알아보기: IAxWinAmbientDispatchEx 인터페이스'
title: IAxWinAmbientDispatchEx 인터페이스
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: c26ce7fb4f41273a498e3b28e9d6e15d4c89f9ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139726"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 인터페이스

이 인터페이스는 호스트 된 컨트롤에 대 한 보완 앰비언트 속성을 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|이 메서드는 사용자 정의 인터페이스를 사용 하 여 기본 앰비언트 속성 인터페이스를 보완 하기 위해 호출 됩니다.|

## <a name="remarks"></a>설명

ATL에 정적으로 링크 되 고 ActiveX 컨트롤, 특히 앰비언트 속성이 있는 ActiveX 컨트롤을 호스트 하는 ATL 응용 프로그램에이 인터페이스를 포함 합니다. 이 인터페이스를 포함 하지 않으면 다음 어설션이 생성 됩니다. "LIBID를 CComModule:: Init에 전달 해야 합니다."

이 인터페이스는 ATL의 ActiveX 컨트롤 호스팅 개체에 의해 노출 됩니다. [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)에서 파생 되 고, 사용자 `IAxWinAmbientDispatchEx` 고유의를 사용 하 여 ATL에서 제공 하는 앰비언트 속성 인터페이스를 보완할 수 있도록 하는 메서드를 추가 합니다.

<xref:System.Windows.Forms.AxHost> 는 `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` 코드를 포함 하는 형식 라이브러리에 대 한 형식 정보를 로드 하려고 합니다.

ATL90.dll에 연결 하는 경우 **Axhost** 는 DLL의 형식 라이브러리에서 형식 정보를 로드 합니다.

자세한 내용은 [ATL AXHost를 사용 하 여 ActiveX 컨트롤 호스팅](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 을 참조 하세요.

## <a name="requirements"></a>요구 사항

이 인터페이스의 정의는 다음 표에 나와 있는 것 처럼 다양 한 형식으로 제공 됩니다.

|정의 형식|파일|
|---------------------|----------|
|IDL|atliface. idl|
|형식 라이브러리|ATL.dll|
|C++|atliface. .h (설명서에도 포함 됨)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> IAxWinAmbientDispatchEx::SetAmbientDispatch

이 메서드는 사용자 정의 인터페이스를 사용 하 여 기본 앰비언트 속성 인터페이스를 보완 하기 위해 호출 됩니다.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>매개 변수

*pDispatch*<br/>
새 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`SetAmbientDispatch`새 인터페이스에 대 한 포인터를 사용 하 여를 호출 하면이 새 인터페이스를 사용 하 여 호스트 된 컨트롤에 의해 요청 된 속성 또는 메서드를 호출 합니다. 이러한 속성은 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)에서 아직 제공 되지 않은 경우에 사용 됩니다.

## <a name="see-also"></a>참고 항목

[IAxWinAmbientDispatch 인터페이스](../../atl/reference/iaxwinambientdispatch-interface.md)
