---
description: '자세한 정보: 메시지 맵 매크로 (ATL)'
title: 메시지 맵 매크로 (ATL)
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 5efe2a6b5aaeb2fbbf3cb5b54ce376ebf00c3b75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139076"
---
# <a name="message-map-macros-atl"></a>메시지 맵 매크로 (ATL)

이러한 매크로는 메시지 맵과 항목을 정의 합니다.

|Name|설명|
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|대체 메시지 맵의 시작을 표시 합니다.|
|[BEGIN_MSG_MAP](#begin_msg_map)|기본 메시지 맵의 시작을 표시 합니다.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|기본 클래스의 대체 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|클래스의 데이터 멤버에 있는 대체 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP](#chain_msg_map)|기본 클래스의 기본 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|런타임에 다른 클래스의 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|클래스의 데이터 멤버에 있는 기본 메시지 맵에 연결 합니다.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|알림 코드에 따라 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[COMMAND_HANDLER](#command_handler)|알림 코드 및 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[COMMAND_ID_HANDLER](#command_id_handler)|메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|알림 코드 및 인접 한 컨트롤 식별자 범위에 따라 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|연속 되는 컨트롤 식별자 범위에 따라 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|빈 메시지 맵을 구현 합니다.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|달리 처리 되지 않은 반영 된 메시지에 대 한 기본 처리기를 제공 합니다.|
|[END_MSG_MAP](#end_msg_map)|메시지 맵의 끝을 표시 합니다.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|부모 창에 알림 메시지를 전달 합니다.|
|[MESSAGE_HANDLER](#message_handler)|Windows 메시지를 처리기 함수에 매핑합니다.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|연속 되는 Windows 메시지 범위를 처리기 함수에 매핑합니다.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|알림 코드에 따라 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[NOTIFY_HANDLER](#notify_handler)|알림 코드 및 컨트롤 식별자를 기반으로 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|컨트롤 식별자를 기반으로 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|알림 코드 및 인접 한 컨트롤 식별자 범위에 따라 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|연속 되는 컨트롤 식별자 범위에 따라 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|알림 메시지를 보낸 창으로 다시 반영 합니다.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|반영 된 WM_COMMAND 메시지를 알림 코드에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|알림 코드 및 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 리플렉션된 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 리플렉션된 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|반영 된 WM_COMMAND 메시지를 알림 코드 및 인접 한 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|반영 된 WM_COMMAND 메시지를 연속 된 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|반영 된 WM_NOTIFY 메시지를 알림 코드에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|반영 된 WM_NOTIFY 메시지를 알림 코드 및 컨트롤 식별자를 기반으로 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|컨트롤 식별자를 기반으로 리플렉션된 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|반영 된 WM_NOTIFY 메시지를 알림 코드 및 인접 한 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|반영 된 WM_NOTIFY 메시지를 연속 된 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a> ALT_MSG_MAP

대체 메시지 맵의 시작을 표시 합니다.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>매개 변수

*msgMapID*<br/>
진행 메시지 맵 식별자입니다.

### <a name="remarks"></a>설명

ATL은 각 메시지 맵을 숫자로 식별 합니다. BEGIN_MSG_MAP 매크로를 사용 하 여 선언 된 기본 메시지 맵은 0으로 식별 됩니다. 대체 메시지 맵은 *Msgmapid* 로 식별 됩니다.

메시지 맵은 창에 전송 된 메시지를 처리 하는 데 사용 됩니다. 예를 들어 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 를 사용 하면 포함 하는 개체에서 메시지 맵의 식별자를 지정할 수 있습니다. [CContainedWindow:: WindowProc](ccontainedwindowt-class.md#windowproc) 는이 메시지 맵을 사용 하 여 포함 된 창의 메시지를 적절 한 처리기 함수 또는 다른 메시지 맵으로 보냅니다. 처리기 함수를 선언 하는 매크로 목록은 [BEGIN_MSG_MAP](#begin_msg_map)를 참조 하세요.

항상 BEGIN_MSG_MAP를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 후속 대체 메시지 맵을 선언할 수 있습니다.

[END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 항상 정확히 하나씩 있습니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 기본 메시지 맵과 각각 하나의 처리기 함수를 포함 하는 하나의 대체 메시지 맵을 보여 줍니다.

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

다음 예제에서는 두 개의 대체 메시지 맵을 보여 줍니다. 기본 메시지 맵은 비어 있습니다.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a> BEGIN_MSG_MAP

기본 메시지 맵의 시작을 표시 합니다.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
진행 메시지 맵을 포함 하는 클래스의 이름입니다.

### <a name="remarks"></a>설명

[CWindowImpl:: WindowProc](cwindowimpl-class.md#windowproc) 는 기본 메시지 맵을 사용 하 여 창에 전송 된 메시지를 처리 합니다. 메시지 맵은 메시지를 적절 한 처리기 함수 또는 다른 메시지 맵으로 보냅니다.

다음 매크로는 메시지를 처리기 함수에 매핑합니다. 이 함수는 *Theclass* 에서 정의 해야 합니다.

|매크로|설명|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Windows 메시지를 처리기 함수에 매핑합니다.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|연속 되는 Windows 메시지 범위를 처리기 함수에 매핑합니다.|
|[COMMAND_HANDLER](#command_handler)|알림 코드 및 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[COMMAND_ID_HANDLER](#command_id_handler)|메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[COMMAND_CODE_HANDLER](#command_handler)|알림 코드에 따라 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 하 여 WM_COMMAND 메시지의 연속 범위를 처리기 함수에 매핑합니다.|
|[NOTIFY_HANDLER](#notify_handler)|알림 코드 및 컨트롤 식별자를 기반으로 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|컨트롤 식별자를 기반으로 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|알림 코드에 따라 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|컨트롤 식별자를 기반으로 WM_NOTIFY 메시지의 연속 범위를 처리기 함수에 매핑합니다.|

다음 매크로는 메시지를 다른 메시지 맵으로 보냅니다. 이 프로세스를 "연결" 이라고 합니다.

|매크로|설명|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|기본 클래스의 기본 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|클래스의 데이터 멤버에 있는 기본 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|기본 클래스의 대체 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|클래스의 데이터 멤버에 있는 대체 메시지 맵에 연결 합니다.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|런타임에 다른 클래스의 기본 메시지 맵에 연결 합니다.|

다음 매크로는 부모 창에서 "리플렉션된" 메시지를 전달 합니다. 예를 들어, 컨트롤은 일반적으로 처리를 위해 해당 부모 창에 알림 메시지를 보내지만 부모 창에는 메시지를 컨트롤에 다시 반영할 수 있습니다.

|매크로|설명|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|알림 코드 및 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 리플렉션된 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자를 기반으로 리플렉션된 WM_COMMAND 메시지를 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|반영 된 WM_COMMAND 메시지를 알림 코드에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|반영 된 WM_COMMAND 메시지를 연속 된 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|반영 된 WM_COMMAND 메시지를 알림 코드 및 인접 한 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|반영 된 WM_NOTIFY 메시지를 알림 코드 및 컨트롤 식별자를 기반으로 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|컨트롤 식별자를 기반으로 리플렉션된 WM_NOTIFY 메시지를 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|반영 된 WM_NOTIFY 메시지를 알림 코드에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|반영 된 WM_NOTIFY 메시지를 연속 된 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|반영 된 WM_NOTIFY 메시지를 알림 코드 및 인접 한 컨트롤 식별자 범위에 따라 처리기 함수에 매핑합니다.|

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

`CMyExtWindow`개체가 WM_PAINT 메시지를 받으면 실제 처리를 위해 메시지를 전송 합니다 `CMyExtWindow::OnPaint` . `OnPaint`에서 메시지에 추가 처리가 필요 함을 나타내는 경우 메시지가의 기본 메시지 맵으로 전달 됩니다 `CMyBaseWindow` .

기본 메시지 맵 외에도 [ALT_MSG_MAP](#alt_msg_map)를 사용 하 여 대체 메시지 맵을 정의할 수 있습니다. 항상 BEGIN_MSG_MAP를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 후속 대체 메시지 맵을 선언할 수 있습니다. 다음 예제에서는 기본 메시지 맵과 각각 하나의 처리기 함수를 포함 하는 하나의 대체 메시지 맵을 보여 줍니다.

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

다음 예제에서는 두 개의 대체 메시지 맵을 보여 줍니다. 기본 메시지 맵은 비어 있습니다.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 항상 정확히 하나씩 있습니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a> CHAIN_MSG_MAP_ALT

메시지 맵에 항목을 정의 합니다.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>매개 변수

*theChainClass*<br/>
진행 메시지 맵을 포함 하는 기본 클래스의 이름입니다.

*msgMapID*<br/>
진행 메시지 맵 식별자입니다.

### <a name="remarks"></a>설명

CHAIN_MSG_MAP_ALT는 메시지를 기본 클래스의 대체 메시지 맵으로 보냅니다. [ALT_MSG_MAP (msgMapID)](#alt_msg_map)를 사용 하 여이 대체 메시지 맵을 선언 해야 합니다. [BEGIN_MSG_MAP](#begin_msg_map)를 사용 하 여 선언 된 기본 클래스의 기본 메시지 맵으로 메시지를 전달 하려면 CHAIN_MSG_MAP를 사용 합니다. 예제를 보려면 [CHAIN_MSG_MAP](#chain_msg_map)를 참조 하세요.

> [!NOTE]
> 항상 BEGIN_MSG_MAP를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 ALT_MSG_MAP를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a> CHAIN_MSG_MAP_ALT_MEMBER

메시지 맵에 항목을 정의 합니다.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>매개 변수

*theChainMember*<br/>
진행 메시지 맵을 포함 하는 데이터 멤버의 이름입니다.

*msgMapID*<br/>
진행 메시지 맵 식별자입니다.

### <a name="remarks"></a>설명

CHAIN_MSG_MAP_ALT_MEMBER는 메시지를 데이터 멤버의 대체 메시지 맵으로 보냅니다. [ALT_MSG_MAP (msgMapID)](#alt_msg_map)를 사용 하 여이 대체 메시지 맵을 선언 해야 합니다. [BEGIN_MSG_MAP](#begin_msg_map)를 사용 하 여 선언 된 데이터 멤버의 기본 메시지 맵으로 메시지를 전달 하려면 CHAIN_MSG_MAP_MEMBER를 사용 합니다. 예제를 보려면 [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)를 참조 하세요.

> [!NOTE]
> 항상 BEGIN_MSG_MAP를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 ALT_MSG_MAP를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a> CHAIN_MSG_MAP

메시지 맵에 항목을 정의 합니다.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>매개 변수

*theChainClass*<br/>
진행 메시지 맵을 포함 하는 기본 클래스의 이름입니다.

### <a name="remarks"></a>설명

CHAIN_MSG_MAP는 메시지를 기본 클래스의 기본 메시지 맵으로 전달 합니다 ( [BEGIN_MSG_MAP](#begin_msg_map)로 선언 됨). [ALT_MSG_MAP](#alt_msg_map)를 사용 하 여 선언 된 기본 클래스의 대체 메시지 맵으로 메시지를 전달 하려면 [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)를 사용 합니다.

> [!NOTE]
> 항상 BEGIN_MSG_MAP를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 ALT_MSG_MAP를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

이 예제에서는 다음을 보여 줍니다.

- 창 프로시저에서 `CMyClass` 의 기본 메시지 맵을 사용 하 고 `OnPaint` 메시지를 처리 하지 않는 경우 메시지를 `CMyBaseClass` 처리 하기 위해 기본 메시지 맵으로 전송 합니다.

- 창 프로시저에서의 첫 번째 대체 메시지 맵을 사용 하는 경우 `CMyClass` 모든 메시지는 `CMyBaseClass` 기본 메시지 맵으로 전달 됩니다.

- 창 프로시저가 `CMyClass` 의 두 번째 대체 메시지 맵을 사용 하 고 `OnChar` 메시지를 처리 하지 않는 경우의 지정 된 대체 메시지 맵으로 메시지가 전송 됩니다 `CMyBaseClass` . `CMyBaseClass` ALT_MSG_MAP (1)를 사용 하 여이 메시지 맵을 선언 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a> CHAIN_MSG_MAP_DYNAMIC

메시지 맵에 항목을 정의 합니다.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>매개 변수

*dynaChainID*<br/>
진행 개체의 메시지 맵에 대 한 고유 식별자입니다.

### <a name="remarks"></a>설명

CHAIN_MSG_MAP_DYNAMIC는 런타임에 메시지를 다른 개체의 기본 메시지 맵으로 보냅니다. 개체와 해당 메시지 맵은 [Cdynamicchain:: SetChainEntry](cdynamicchain-class.md#setchainentry)를 통해 정의 하는 *dynaChainID* 와 연결 됩니다. CHAIN_MSG_MAP_DYNAMIC를 사용 하려면에서 클래스를 파생 해야 합니다 `CDynamicChain` . 예제는 [Cdynamicchain](../../atl/reference/cdynamicchain-class.md) 개요를 참조 하세요.

> [!NOTE]
> 항상 [BEGIN_MSG_MAP](#begin_msg_map)를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 ALT_MSG_MAP를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a> CHAIN_MSG_MAP_MEMBER

메시지 맵에 항목을 정의 합니다.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>매개 변수

*theChainMember*<br/>
진행 메시지 맵을 포함 하는 데이터 멤버의 이름입니다.

### <a name="remarks"></a>설명

CHAIN_MSG_MAP_MEMBER은 [BEGIN_MSG_MAP](#begin_msg_map)으로 선언 된 데이터 멤버의 기본 메시지 맵으로 메시지를 보냅니다. [ALT_MSG_MAP](#alt_msg_map)로 선언 된 데이터 멤버의 대체 메시지 맵으로 메시지를 전달 하려면 [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)를 사용 합니다.

> [!NOTE]
> 항상 BEGIN_MSG_MAP를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 ALT_MSG_MAP를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

이 예제에서는 다음을 보여 줍니다.

- 창 프로시저에서 `CMyClass` 의 기본 메시지 맵을 사용 하 고 `OnPaint` 메시지를 처리 하지 않는 경우 메시지를 `m_obj` 처리 하기 위해 기본 메시지 맵으로 전송 합니다.

- 창 프로시저에서의 첫 번째 대체 메시지 맵을 사용 하는 경우 `CMyClass` 모든 메시지는 `m_obj` 기본 메시지 맵으로 전달 됩니다.

- 창 프로시저가 `CMyClass` 의 두 번째 대체 메시지 맵을 사용 하 고 `OnChar` 메시지를 처리 하지 않는 경우 메시지는의 지정 된 대체 메시지 맵으로 전달 됩니다 `m_obj` . 클래스가 `CMyContainedClass` ALT_MSG_MAP (1)를 사용 하 여이 메시지 맵을 선언 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="command_code_handler"></a><a name="command_code_handler"></a> COMMAND_CODE_HANDLER

[COMMAND_HANDLER](#command_handler)와 비슷하지만 알림 코드만을 기반으로 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 매핑합니다.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>매개 변수

*code*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="command_handler"></a><a name="command_handler"></a> COMMAND_HANDLER

메시지 맵에 항목을 정의 합니다.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자입니다.

*code*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

COMMAND_HANDLER는 알림 코드 및 컨트롤 식별자를 기반으로 하 여 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 지정 된 처리기 함수에 매핑합니다. 예를 들어:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

COMMAND_HANDLER 매크로에 지정 된 함수는 다음과 같이 정의 해야 합니다.

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

메시지 맵은 `bHandled` 가 호출 되기 전에를 TRUE로 설정 합니다 `CommandHandler` . `CommandHandler`에서 메시지를 완전히 처리 하지 않는 경우에는 `bHandled` 메시지에 추가 처리가 필요 함을 나타내기 위해를 FALSE로 설정 해야 합니다.

> [!NOTE]
> 항상 [BEGIN_MSG_MAP](#begin_msg_map)를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 [ALT_MSG_MAP](#alt_msg_map)를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

COMMAND_HANDLER 외에도 [MESSAGE_HANDLER](#message_handler) 를 사용 하 여 식별자 나 코드에 관계 없이 WM_COMMAND 메시지를 매핑할 수 있습니다. 이 경우 `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` 는 모든 WM_COMMAND 메시지를로 보냅니다 `OnHandlerFunction` .

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="command_id_handler"></a><a name="command_id_handler"></a> COMMAND_ID_HANDLER

[COMMAND_HANDLER](#command_handler)와 비슷하지만 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자만 기반으로 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 매핑합니다.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메시지를 보내는 메뉴 항목, 컨트롤 또는 액셀러레이터의 식별자입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a> COMMAND_RANGE_CODE_HANDLER

[COMMAND_RANGE_HANDLER](#command_range_handler)와 유사 하지만 컨트롤 범위에서 특정 알림 코드를 포함 하는 메시지 [WM_COMMAND](/windows/win32/menurc/wm-command) 단일 처리기 함수로 매핑합니다.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*code*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

이 범위는 메시지를 보내는 메뉴 항목, 컨트롤 또는 액셀러레이터의 식별자를 기반으로 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="command_range_handler"></a><a name="command_range_handler"></a> COMMAND_RANGE_HANDLER

[COMMAND_HANDLER](#command_handler)와 비슷하지만 컨트롤 범위에 있는 메시지 [WM_COMMAND](/windows/win32/menurc/wm-command) 단일 처리기 함수에 매핑합니다.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

이 범위는 메시지를 보내는 메뉴 항목, 컨트롤 또는 액셀러레이터의 식별자를 기반으로 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a> DECLARE_EMPTY_MSG_MAP

빈 메시지 맵을 선언 합니다.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>설명

DECLARE_EMPTY_MSG_MAP는 매크로 [BEGIN_MSG_MAP](#begin_msg_map) 를 호출 하는 편리한 매크로 이며 [END_MSG_MAP](#end_msg_map) 빈 메시지 맵을 만듭니다.

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a> DEFAULT_REFLECTION_HANDLER

반영 된 메시지를 수신 하는 자식 창 (컨트롤)에 대 한 기본 처리기를 제공 합니다. 처리기가 처리 되지 않은 메시지를에 올바르게 전달 `DefWindowProc` 합니다.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="end_msg_map"></a><a name="end_msg_map"></a> END_MSG_MAP

메시지 맵의 끝을 표시 합니다.

```
END_MSG_MAP()
```

### <a name="remarks"></a>설명

항상 [BEGIN_MSG_MAP](#begin_msg_map) 매크로를 사용 하 여 메시지 맵의 시작을 표시 합니다. 후속 대체 메시지 맵을 선언 하려면 [ALT_MSG_MAP](#alt_msg_map) 을 사용 합니다.

BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 항상 정확히 하나씩 있습니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 기본 메시지 맵과 각각 하나의 처리기 함수를 포함 하는 하나의 대체 메시지 맵을 보여 줍니다.

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

다음 예제에서는 두 개의 대체 메시지 맵을 보여 줍니다. 기본 메시지 맵은 비어 있습니다.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="forward_notifications"></a><a name="forward_notifications"></a> FORWARD_NOTIFICATIONS

부모 창에 알림 메시지를 전달 합니다.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>설명

이 매크로를 메시지 맵의 일부로 지정 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="message_handler"></a><a name="message_handler"></a> MESSAGE_HANDLER

메시지 맵에 항목을 정의 합니다.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>매개 변수

*msg*<br/>
진행 Windows 메시지입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

MESSAGE_HANDLER는 Windows 메시지를 지정 된 처리기 함수에 매핑합니다.

MESSAGE_HANDLER 매크로에 지정 된 함수는 다음과 같이 정의 해야 합니다.

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

메시지 맵은 `bHandled` 가 호출 되기 전에를 TRUE로 설정 합니다 `MessageHandler` . `MessageHandler`에서 메시지를 완전히 처리 하지 않는 경우에는 `bHandled` 메시지에 추가 처리가 필요 함을 나타내기 위해를 FALSE로 설정 해야 합니다.

> [!NOTE]
> 항상 [BEGIN_MSG_MAP](#begin_msg_map)를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 [ALT_MSG_MAP](#alt_msg_map)를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

MESSAGE_HANDLER 외에도 [COMMAND_HANDLER](#command_handler) 및 [NOTIFY_HANDLER](#notify_handler) 를 사용 하 여 [WM_COMMAND](/windows/win32/menurc/wm-command) 및 [WM_NOTIFY](/windows/win32/controls/wm-notify) 메시지를 각각 매핑할 수 있습니다.

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="message_range_handler"></a><a name="message_range_handler"></a> MESSAGE_RANGE_HANDLER

[MESSAGE_HANDLER](#message_handler)와 비슷하지만 Windows 메시지 범위를 단일 처리기 함수에 매핑합니다.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>매개 변수

*msgFirst*<br/>
진행 연속 된 메시지 범위의 시작을 표시 합니다.

*msgLast*<br/>
진행 연속 된 메시지 범위의 끝을 표시 합니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a> NOTIFY_CODE_HANDLER

[NOTIFY_HANDLER](#notify_handler)와 비슷하지만 알림 코드만을 기반으로 [WM_NOTIFY](/windows/win32/controls/wm-notify) 메시지를 매핑합니다.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>매개 변수

*cd*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="notify_handler"></a><a name="notify_handler"></a> NOTIFY_HANDLER

메시지 맵에 항목을 정의 합니다.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메시지를 보내는 컨트롤의 식별자입니다.

*cd*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

NOTIFY_HANDLER는 알림 코드 및 컨트롤 식별자를 기반으로 하 여 [WM_NOTIFY](/windows/win32/controls/wm-notify) 메시지를 지정 된 처리기 함수에 매핑합니다.

NOTIFY_HANDLER 매크로에 지정 된 함수는 다음과 같이 정의 해야 합니다.

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

메시지 맵은 `bHandled` 가 호출 되기 전에를 TRUE로 설정 합니다 `NotifyHandler` . `NotifyHandler`에서 메시지를 완전히 처리 하지 않는 경우에는 `bHandled` 메시지에 추가 처리가 필요 함을 나타내기 위해를 FALSE로 설정 해야 합니다.

> [!NOTE]
> 항상 [BEGIN_MSG_MAP](#begin_msg_map)를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 [ALT_MSG_MAP](#alt_msg_map)를 사용 하 여 후속 대체 메시지 맵을 선언할 수 있습니다. [END_MSG_MAP](#end_msg_map) 매크로는 메시지 맵의 끝을 표시 합니다. 모든 메시지 맵에는 정확히 하나의 BEGIN_MSG_MAP와 END_MSG_MAP 인스턴스가 있어야 합니다.

NOTIFY_HANDLER 외에도 [MESSAGE_HANDLER](#message_handler) 를 사용 하 여 식별자 나 코드에 관계 없이 WM_NOTIFY 메시지를 매핑할 수 있습니다. 이 경우 `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` 는 모든 WM_NOTIFY 메시지를로 보냅니다 `OnHandlerFunction` .

ATL에서 메시지 맵을 사용 하는 방법에 대 한 자세한 내용은 [메시지 맵](../../atl/message-maps-atl.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a> NOTIFY_ID_HANDLER

[NOTIFY_HANDLER](#notify_handler)와 비슷하지만 컨트롤 식별자를 기반으로 [WM_NOTIFY](/windows/win32/controls/wm-notify) 메시지를 매핑합니다.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메시지를 보내는 컨트롤의 식별자입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a> NOTIFY_RANGE_CODE_HANDLER

[NOTIFY_RANGE_HANDLER](#notify_range_handler)와 유사 하지만 컨트롤 범위에서 특정 알림 코드를 포함 하는 메시지 [WM_NOTIFY](/windows/win32/controls/wm-notify) 단일 처리기 함수로 매핑합니다.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*cd*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

이 범위는 메시지를 보내는 컨트롤의 식별자를 기반으로 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a> NOTIFY_RANGE_HANDLER

[NOTIFY_HANDLER](#notify_handler)와 비슷하지만 컨트롤 범위에 있는 메시지 [WM_NOTIFY](/windows/win32/controls/wm-notify) 단일 처리기 함수에 매핑합니다.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

이 범위는 메시지를 보내는 컨트롤의 식별자를 기반으로 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a> REFLECT_NOTIFICATIONS

알림 메시지를 보낸 자식 창 (컨트롤)으로 다시 반영 합니다.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>설명

이 매크로를 부모 창의 메시지 맵의 일부로 지정 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a> REFLECTED_COMMAND_CODE_HANDLER

[COMMAND_CODE_HANDLER](#command_code_handler)와 비슷하지만 부모 창에서 리플렉션된 명령을 매핑합니다.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>매개 변수

*code*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a> REFLECTED_COMMAND_HANDLER

[COMMAND_HANDLER](#command_handler)와 비슷하지만 부모 창에서 리플렉션된 명령을 매핑합니다.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자입니다.

*code*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a> REFLECTED_COMMAND_ID_HANDLER

[COMMAND_ID_HANDLER](#command_id_handler)와 비슷하지만 부모 창에서 리플렉션된 명령을 매핑합니다.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a> REFLECTED_COMMAND_RANGE_CODE_HANDLER

[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)와 비슷하지만 부모 창에서 리플렉션된 명령을 매핑합니다.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*code*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a> REFLECTED_COMMAND_RANGE_HANDLER

[COMMAND_RANGE_HANDLER](#command_range_handler)와 비슷하지만 부모 창에서 리플렉션된 명령을 매핑합니다.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a> REFLECTED_NOTIFY_CODE_HANDLER

[NOTIFY_CODE_HANDLER](#notify_code_handler)와 비슷하지만 부모 창에서 리플렉션된 알림이 매핑됩니다.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>매개 변수

*cd*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a> REFLECTED_NOTIFY_HANDLER

[NOTIFY_HANDLER](#notify_handler)와 비슷하지만 부모 창에서 리플렉션된 알림이 매핑됩니다.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자입니다.

*cd*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a> REFLECTED_NOTIFY_ID_HANDLER

[NOTIFY_ID_HANDLER](#notify_id_handler)와 비슷하지만 부모 창에서 리플렉션된 알림이 매핑됩니다.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 메뉴 항목, 컨트롤 또는 액셀러레이터 키의 식별자입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a> REFLECTED_NOTIFY_RANGE_CODE_HANDLER

[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)와 비슷하지만 부모 창에서 리플렉션된 알림이 매핑됩니다.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*cd*<br/>
진행 알림 코드입니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a> REFLECTED_NOTIFY_RANGE_HANDLER

[NOTIFY_RANGE_HANDLER](#notify_range_handler)와 비슷하지만 부모 창에서 리플렉션된 알림이 매핑됩니다.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>매개 변수

*idFirst*<br/>
진행 연속 된 컨트롤 식별자 범위의 시작을 표시 합니다.

*idLast*<br/>
진행 연속 된 범위에 있는 컨트롤 식별자의 끝을 표시 합니다.

*func*<br/>
진행 메시지 처리기 함수의 이름입니다.

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
