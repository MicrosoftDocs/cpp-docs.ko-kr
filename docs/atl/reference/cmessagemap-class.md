---
description: '자세한 정보: CMessageMap 클래스'
title: CMessageMap 클래스
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: 90ecdc101071b84362d328558ff2e74cb9bbeb6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141442"
---
# <a name="cmessagemap-class"></a>CMessageMap 클래스

이 클래스를 사용 하 여 개체의 메시지 맵을 다른 개체에서 액세스할 수 있습니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMessageMap::P](#processwindowmessage)|파생 클래스의 메시지 맵에 액세스 `CMessageMap` 합니다.|

## <a name="remarks"></a>설명

`CMessageMap` 는 다른 개체에서 개체의 메시지 맵을 액세스할 수 있도록 하는 추상 기본 클래스입니다. 개체가 메시지 맵을 노출 하도록 하려면 해당 클래스가에서 파생 되어야 합니다 `CMessageMap` .

ATL은를 사용 하 여 `CMessageMap` 포함 된 windows 및 동적 메시지 맵 체인을 지원 합니다. 예를 들어 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 개체를 포함 하는 모든 클래스는에서 파생 되어야 합니다 `CMessageMap` . 다음 코드는 [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) 샘플에서 가져온 것입니다. [CComControl](../../atl/reference/ccomcontrol-class.md)를 통해 `CAtlEdit` 클래스는에서 자동으로 파생 `CMessageMap` 됩니다.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

포함 된 창는 `m_EditCtrl` 포함 하는 클래스의 메시지 맵을 사용 하므로 `CAtlEdit` 에서 파생 됩니다 `CMessageMap` .

메시지 맵에 대 한 자세한 내용은 "ATL 창 클래스" 문서의 [메시지 맵](../../atl/message-maps-atl.md) 을 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a> CMessageMap::P

파생 클래스에서 *Dwmsgmapid* 로 식별 되는 메시지 맵에 액세스 합니다 `CMessageMap` .

```
virtual BOOL ProcessWindowMessage(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```

### <a name="parameters"></a>매개 변수

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

*dwMsgMapID*<br/>
진행 메시지를 처리 하는 메시지 맵의 식별자입니다. [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)로 선언 된 기본 메시지 맵은 0으로 식별 됩니다. [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)로 선언 된 대체 메시지 맵은로 식별 됩니다 `msgMapID` .

### <a name="return-value"></a>반환 값

메시지가 완전히 처리 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 개체의 창 프로시저나 메시지 맵에 동적으로 연결 되는 개체에 의해 호출 됩니다.

## <a name="see-also"></a>참고 항목

[CDynamicChain 클래스](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
