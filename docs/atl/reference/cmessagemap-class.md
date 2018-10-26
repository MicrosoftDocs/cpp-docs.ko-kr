---
title: CMessageMap 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fcbb20ac27eea7999c634f78b14e85a6221b11b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053456"
---
# <a name="cmessagemap-class"></a>CMessageMap 클래스

이 클래스는 개체의 메시지 맵 다른 개체에 의해 액세스를 허용 합니다.

> [!IMPORTANT]
>  이 클래스 및 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|메시지 맵을 액세스는 `CMessageMap`-클래스를 파생 합니다.|

## <a name="remarks"></a>설명

`CMessageMap` 개체의 메시지를 허용 하는 추상 기본 클래스를 다른 개체에 의해 액세스할 수 매핑되는입니다. 메시지 맵을 노출 하는 개체에 대 한 순서로 해당 클래스에서 파생 되어야 `CMessageMap`합니다.

ATL 사용 `CMessageMap` 지원이 포함 된 windows 및 동적 메시지 맵 체 이닝 합니다. 예를 들어, 모든 클래스를 포함 하는 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 개체에서 파생 되어야 합니다 `CMessageMap`합니다. 다음 코드에서 가져온 것은 [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) 샘플입니다. 통해 [CComControl](../../atl/reference/ccomcontrol-class.md)서 `CAtlEdit` 클래스에서 자동으로 파생 됩니다 `CMessageMap`합니다.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

때문에 포함 된 창을 `m_EditCtrl`, 메시지 맵을 포함 하는 클래스에서 사용할 `CAtlEdit` 에서 파생 `CMessageMap`합니다.

메시지 맵에 대 한 자세한 내용은 참조 하세요. [메시지 맵](../../atl/message-maps-atl.md) 문서의 "ATL 창 클래스입니다."

## <a name="requirements"></a>요구 사항

**헤더:** atlwin.h

##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage

액세스로 식별 되는 메시지 맵을 *dwMsgMapID* 에 `CMessageMap`-클래스를 파생 합니다.

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
[in] 메시지를 받는 창에 대 한 핸들입니다.

*uMsg*<br/>
[in] 창으로 전송 하는 메시지입니다.

*wParam*<br/>
[in] 추가 메시지 관련 정보입니다.

*lParam*<br/>
[in] 추가 메시지 관련 정보입니다.

*lResult*<br/>
[out] 메시지 처리의 결과입니다.

*dwMsgMapID*<br/>
[in] 메시지를 처리 하는 메시지 맵의 식별자입니다. 기본 메시지 맵을 사용 하 여 선언 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)를 0으로 식별 됩니다. 대체 메시지 지도 사용 하 여 선언 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map),으로 식별 되 `msgMapID`합니다.

### <a name="return-value"></a>반환 값

TRUE 이면 메시지 처리. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

창 프로시저에 의해 호출 된 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 개체 또는 개체는 동적으로 연결을 메시지 맵에 있습니다.

## <a name="see-also"></a>참고 항목

[CDynamicChain 클래스](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
