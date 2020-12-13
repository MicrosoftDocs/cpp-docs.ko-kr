---
description: '자세한 정보: CDynamicChain 클래스'
title: CDynamicChain 클래스
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 5ada99b519900150afa2143fb1527245797fed98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141819"
---
# <a name="cdynamicchain-class"></a>CDynamicChain 클래스

이 클래스는 메시지 맵의 동적 체인을 지 원하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CDynamicChain
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDynamicChain:: CDynamicChain](#cdynamicchain)|생성자입니다.|
|[CDynamicChain:: ~ CDynamicChain](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDynamicChain:: CallChain](#callchain)|Windows 메시지를 다른 개체의 메시지 맵으로 보냅니다.|
|[CDynamicChain:: RemoveChainEntry](#removechainentry)|컬렉션에서 메시지 맵 항목을 제거 합니다.|
|[CDynamicChain:: SetChainEntry](#setchainentry)|컬렉션에 메시지 맵 항목을 추가 하거나 기존 항목을 수정 합니다.|

## <a name="remarks"></a>설명

`CDynamicChain` 런타임에 Windows 메시지를 다른 개체의 메시지 맵으로 리디렉션할 수 있도록 하는 메시지 맵의 컬렉션을 관리 합니다.

메시지 맵의 동적 체인에 대 한 지원을 추가 하려면 다음을 수행 합니다.

- 에서 클래스를 파생 시킵니다 `CDynamicChain` . 메시지 맵에서 다른 개체의 기본 메시지 맵에 연결할 [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) 매크로를 지정 합니다.

- [Cmessagemap](../../atl/reference/cmessagemap-class.md)에서 연결 하려는 모든 클래스를 파생 합니다. `CMessageMap` 개체가 메시지 맵을 다른 개체에 노출할 수 있도록 합니다.

- `CDynamicChain::SetChainEntry`을 호출 하 여 연결 하려는 개체와 메시지 맵을 식별 합니다.

예를 들어 클래스가 다음과 같이 정의 되어 있다고 가정 합니다.

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

클라이언트는 다음을 호출 합니다 `CMyWindow::SetChainEntry` .

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

여기서 `chainedObj` 는 연결 된 개체이 고는에서 파생 된 클래스의 인스턴스입니다 `CMessageMap` . 이제가 `myCtl` 또는에서 처리 하지 않는 메시지를 수신 하면 `OnPaint` `OnSetFocus` 창 프로시저는 메시지를 `chainedObj` 기본 메시지 맵으로 보냅니다.

메시지 맵 연결에 대 한 자세한 내용은 "ATL 창 클래스" 문서의 [메시지 맵](../../atl/message-maps-atl.md) 을 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a> CDynamicChain:: CallChain

Windows 메시지를 다른 개체의 메시지 맵으로 보냅니다.

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>매개 변수

*dwChainID*<br/>
진행 연결 된 개체 및 해당 메시지 맵에 연결 된 고유 식별자입니다.

*hWnd*<br/>
진행 메시지를 수신 하는 창에 대 한 핸들입니다.

*uMsg*<br/>
진행 창에 전송 된 메시지입니다.

*wParam*<br/>
진행 추가 메시지 관련 정보입니다.

*lParam*<br/>
진행 추가 메시지 관련 정보입니다.

*lResult*<br/>
제한이 메시지 처리의 결과입니다.

### <a name="return-value"></a>반환 값

메시지가 완전히 처리 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

호출 하는 창 프로시저의 경우 `CallChain` 메시지 맵에 [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) 매크로를 지정 해야 합니다. 예제는 [Cdynamicchain](../../atl/reference/cdynamicchain-class.md) 개요를 참조 하세요.

`CallChain`*dwChainID* 값을 개체 및 해당 메시지 맵과 연결 하려면 [SetChainEntry](#setchainentry) 에 대 한 이전 호출이 필요 합니다.

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a> CDynamicChain:: CDynamicChain

생성자입니다.

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a> CDynamicChain:: ~ CDynamicChain

소멸자입니다.

```
~CDynamicChain();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a> CDynamicChain:: RemoveChainEntry

컬렉션에서 지정 된 메시지 맵을 제거 합니다.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>매개 변수

*dwChainID*<br/>
진행 연결 된 개체 및 해당 메시지 맵에 연결 된 고유 식별자입니다. [SetChainEntry](#setchainentry)에 대 한 호출을 통해 원래이 값을 정의 합니다.

### <a name="return-value"></a>반환 값

메시지 맵이 컬렉션에서 성공적으로 제거 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a> CDynamicChain:: SetChainEntry

지정 된 메시지 맵을 컬렉션에 추가 합니다.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>매개 변수

*dwChainID*<br/>
진행 연결 된 개체 및 해당 메시지 맵에 연결 된 고유 식별자입니다.

*pObject*<br/>
진행 메시지 맵을 선언 하는 연결 된 개체에 대 한 포인터입니다. 이 개체는 [Cmessagemap](../../atl/reference/cmessagemap-class.md)에서 파생 되어야 합니다.

*dwMsgMapID*<br/>
진행 연결 된 개체에 있는 메시지 맵의 식별자입니다. 기본값은 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)로 선언 된 기본 메시지 맵을 식별 하는 0입니다. [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)를 사용 하 여 선언 된 대체 메시지 맵을 지정 하려면를 전달 `msgMapID` 합니다.

### <a name="return-value"></a>반환 값

메시지 맵이 컬렉션에 성공적으로 추가 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*DwChainID* 값이 이미 컬렉션에 있는 경우 연결 된 개체 및 메시지 맵은 각각 *PObject* 및 *dwmsgmapid* 로 바뀝니다. 그렇지 않으면 새 항목이 추가 됩니다.

## <a name="see-also"></a>참고 항목

[CWindowImpl 클래스](../../atl/reference/cwindowimpl-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
