---
description: '자세한 정보: 이벤트 싱크 맵'
title: 이벤트 싱크 맵
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: df18cdbba849ff0c8d7be5b038f997b6cc5df849
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219839"
---
# <a name="event-sink-maps"></a>이벤트 싱크 맵

포함 된 OLE 컨트롤이 이벤트를 발생 시키면 컨트롤의 컨테이너는 MFC에서 제공 하는 "이벤트 싱크 맵" 이라는 메커니즘을 사용 하 여 이벤트를 수신 합니다. 이 이벤트 싱크 맵은 해당 이벤트의 매개 변수 뿐만 아니라 각 특정 이벤트에 대 한 처리기 함수를 지정 합니다. 이벤트 싱크 맵에 대 한 자세한 내용은 [ActiveX 컨트롤 컨테이너](../../mfc/activex-control-containers.md)문서를 참조 하세요.

### <a name="event-sink-maps"></a>이벤트 싱크 맵

|Name|설명|
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|이벤트 싱크 맵의 정의를 시작 합니다.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|이벤트 싱크 맵을 선언 합니다.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|이벤트 싱크 맵의 정의를 종료 합니다.|
|[ON_EVENT](#on_event)|특정 이벤트에 대 한 이벤트 처리기를 정의 합니다.|
|[ON_EVENT_RANGE](#on_event_range)|OLE 컨트롤 집합에서 발생 한 특정 이벤트에 대 한 이벤트 처리기를 정의 합니다.|
|[ON_EVENT_REFLECT](#on_event_reflect)|컨트롤의 컨테이너에서 처리 되기 전에 컨트롤에서 발생 한 이벤트를 수신 합니다.|
|[ON_PROPNOTIFY](#on_propnotify)|OLE 컨트롤에서 속성 알림을 처리 하기 위한 처리기를 정의 합니다.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|OLE 컨트롤 집합에서 속성 알림을 처리 하기 위한 처리기를 정의 합니다.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|컨트롤의 컨테이너에서 처리 되기 전에 컨트롤에서 보낸 속성 알림을 받습니다.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a> BEGIN_EVENTSINK_MAP

이벤트 싱크 맵의 정의를 시작 합니다.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이벤트 싱크가이를 매핑하는 컨트롤 클래스의 이름을 지정 합니다.

*baseClass*<br/>
*Theclass* 의 기본 클래스 이름을 지정 합니다.

### <a name="remarks"></a>설명

클래스의 멤버 함수를 정의 하는 구현 파일 (.cpp)에서 BEGIN_EVENTSINK_MAP 매크로를 사용 하 여 이벤트 싱크 맵을 시작한 다음에 대 한 알림이 될 각 이벤트에 대 한 매크로 항목을 추가 하 고 END_EVENTSINK_MAP 매크로를 사용 하 여 이벤트 싱크 맵을 완료 합니다.

이벤트 싱크 맵 및 OLE 컨트롤 컨테이너에 대 한 자세한 내용은 [ActiveX 컨트롤 컨테이너](../../mfc/activex-control-containers.md)문서를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a> DECLARE_EVENTSINK_MAP

OLE 컨테이너는 이벤트 싱크 맵을 제공 하 여 컨테이너에서 알릴 이벤트를 지정할 수 있습니다.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>설명

클래스 선언 끝에 DECLARE_EVENTSINK_MAP 매크로를 사용 합니다. 그런 다음에서를 클릭 합니다. 클래스에 대 한 멤버 함수를 정의 하 고, BEGIN_EVENTSINK_MAP 매크로를 사용 하 고, 알림이 제공 되는 각 이벤트에 대 한 매크로 항목을 사용 하 고, END_EVENTSINK_MAP 매크로를 사용 하 여 이벤트 싱크 목록의 끝을 선언 하는 .CPP 파일입니다.

이벤트 싱크 맵에 대 한 자세한 내용은 [ActiveX 컨트롤 컨테이너](../../mfc/activex-control-containers.md)문서를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a> END_EVENTSINK_MAP

이벤트 싱크 맵의 정의를 종료 합니다.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="on_event"></a><a name="on_event"></a> ON_EVENT

ON_EVENT 매크로를 사용 하 여 OLE 컨트롤에 의해 발생 하는 이벤트에 대 한 이벤트 처리기 함수를 정의 합니다.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 이벤트 싱크 맵이 속한 클래스입니다.

*id*<br/>
OLE 컨트롤의 컨트롤 ID입니다.

*dispid*<br/>
컨트롤에서 발생 한 이벤트의 디스패치 ID입니다.

*pfnHandler*<br/>
이벤트를 처리 하는 멤버 함수에 대 한 포인터입니다. 이 함수에는 BOOL 반환 형식 및 이벤트의 매개 변수와 일치 하는 매개 변수 형식이 있어야 합니다 ( *vtsParams* 참조). 이벤트를 처리 했음을 나타내려면 함수에서 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

*vtsParams*<br/>
이벤트에 대 한 매개 변수의 형식을 지정 하는 **VTS_** 상수 시퀀스입니다. 이러한 상수는 DISP_FUNCTION와 같은 디스패치 맵 항목에서 사용 되는 상수와 동일 합니다.

### <a name="remarks"></a>설명

*VtsParams* 인수는 **VTS_** 상수에서 공백으로 구분 된 값 목록입니다. 공백으로 구분 된 이러한 값 중 하나 이상 (쉼표 아님)은 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

short 정수를 포함 하는 목록을 지정 하 고 BOOL을 지정 합니다.

**VTS_** 상수 목록은 [EVENT_CUSTOM](event-maps.md#event_custom)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a> ON_EVENT_RANGE

ON_EVENT_RANGE 매크로를 사용 하 여 연속 된 Id 범위 내에서 컨트롤 ID가 있는 OLE 컨트롤에 의해 발생 하는 이벤트에 대 한 이벤트 처리기 함수를 정의 합니다.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 이벤트 싱크 맵이 속한 클래스입니다.

*idFirst*<br/>
범위에 있는 첫 번째 OLE 컨트롤의 컨트롤 ID입니다.

*idLast*<br/>
범위에 있는 마지막 OLE 컨트롤의 컨트롤 ID입니다.

*dispid*<br/>
컨트롤에서 발생 한 이벤트의 디스패치 ID입니다.

*pfnHandler*<br/>
이벤트를 처리 하는 멤버 함수에 대 한 포인터입니다. 이 함수에는 BOOL 반환 형식, UINT 형식의 첫 번째 매개 변수 (컨트롤 ID의 경우) 및 이벤트의 매개 변수와 일치 하는 추가 매개 변수 형식이 있어야 합니다 ( *vtsParams* 참조). 이벤트를 처리 했음을 나타내려면 함수에서 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

*vtsParams*<br/>
이벤트에 대 한 매개 변수의 형식을 지정 하는 **VTS_** 상수 시퀀스입니다. 첫 번째 상수는 컨트롤 ID의 VTS_I4 형식 이어야 합니다. 이러한 상수는 DISP_FUNCTION와 같은 디스패치 맵 항목에서 사용 되는 상수와 동일 합니다.

### <a name="remarks"></a>설명

*VtsParams* 인수는 **VTS_** 상수에서 공백으로 구분 된 값 목록입니다. 공백으로 구분 된 이러한 값 중 하나 이상 (쉼표 아님)은 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

short 정수를 포함 하는 목록을 지정 하 고 BOOL을 지정 합니다.

**VTS_** 상수 목록은 [EVENT_CUSTOM](event-maps.md#event_custom)를 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 세 개의 컨트롤 (IDC_MYCTRL3를 통해 IDC_MYCTRL1)에 대해 구현 된 MouseDown 이벤트에 대 한 이벤트 처리기를 보여 줍니다. 이벤트 처리기 함수인는 `OnRangeMouseDown` 대화 상자 클래스의 헤더 파일 ()에 다음과 같이 선언 됩니다 `CMyDlg` .

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

아래 코드는 대화 상자 클래스의 구현 파일에 정의 되어 있습니다.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a> ON_EVENT_REFLECT

ON_EVENT_REFLECT 매크로는 OLE 컨트롤의 래퍼 클래스의 이벤트 싱크 맵에 사용 되는 경우 컨트롤의 컨테이너에서 처리 되기 전에 컨트롤에서 발생 한 이벤트를 수신 합니다.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 이벤트 싱크 맵이 속한 클래스입니다.

*dispid*<br/>
컨트롤에서 발생 한 이벤트의 디스패치 ID입니다.

*pfnHandler*<br/>
이벤트를 처리 하는 멤버 함수에 대 한 포인터입니다. 이 함수에는 이벤트의 매개 변수와 일치 하는 부울 반환 형식 및 매개 변수 형식이 있어야 합니다 ( *vtsParams* 참조). 이벤트를 처리 했음을 나타내려면 함수에서 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

*vtsParams*<br/>
이벤트에 대 한 매개 변수의 형식을 지정 하는 **VTS_** 상수 시퀀스입니다. 이러한 상수는 DISP_FUNCTION와 같은 디스패치 맵 항목에서 사용 되는 상수와 동일 합니다.

### <a name="remarks"></a>설명

*VtsParams* 인수는 **VTS_** 상수에서 공백으로 구분 된 값 목록입니다.

공백으로 구분 된 이러한 값 중 하나 이상 (쉼표 아님)은 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

short 정수를 포함 하는 목록을 지정 하 고 BOOL을 지정 합니다.

**VTS_** 상수 목록은 [EVENT_CUSTOM](event-maps.md#event_custom)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a> ON_PROPNOTIFY

ON_PROPNOTIFY 매크로를 사용 하 여 OLE 컨트롤에서 속성 알림을 처리 하기 위한 이벤트 싱크 맵 항목을 정의 합니다.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 이벤트 싱크 맵이 속한 클래스입니다.

*id*<br/>
OLE 컨트롤의 컨트롤 ID입니다.

*dispid*<br/>
알림과 관련 된 속성의 디스패치 ID입니다.

*pfnRequest*<br/>
`OnRequestEdit`이 속성에 대 한 알림을 처리 하는 멤버 함수에 대 한 포인터입니다. 이 함수에는 BOOL 반환 형식과 **bool** <strong>\*</strong> 매개 변수가 있어야 합니다. 이 함수는 속성을 변경할 수 있도록 매개 변수를 TRUE로 설정 하 고, 허용 하지 않으려면 FALSE로 설정 해야 합니다. 이 함수는 알림이 처리 되었음을 나타내기 위해 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

*pfnChanged*<br/>
`OnChanged`이 속성에 대 한 알림을 처리 하는 멤버 함수에 대 한 포인터입니다. 함수는 BOOL 반환 형식 및 UINT 매개 변수를 포함 해야 합니다. 이 함수는 알림이 처리 되었음을 나타내기 위해 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*VtsParams* 인수는 **VTS_** 상수에서 공백으로 구분 된 값 목록입니다. 공백으로 구분 된 이러한 값 중 하나 이상 (쉼표 아님)은 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

short 정수를 포함 하는 목록을 지정 하 고 BOOL을 지정 합니다.

**VTS_** 상수 목록은 [EVENT_CUSTOM](event-maps.md#event_custom)를 참조 하세요.

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a> ON_PROPNOTIFY_RANGE

ON_PROPNOTIFY_RANGE 매크로를 사용 하 여 인접 한 Id 범위 내에서 컨트롤 ID가 있는 OLE 컨트롤의 속성 알림을 처리 하기 위한 이벤트 싱크 맵 항목을 정의할 수 있습니다.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 이벤트 싱크 맵이 속한 클래스입니다.

*idFirst*<br/>
범위에 있는 첫 번째 OLE 컨트롤의 컨트롤 ID입니다.

*idLast*<br/>
범위에 있는 마지막 OLE 컨트롤의 컨트롤 ID입니다.

*dispid*<br/>
알림과 관련 된 속성의 디스패치 ID입니다.

*pfnRequest*<br/>
`OnRequestEdit`이 속성에 대 한 알림을 처리 하는 멤버 함수에 대 한 포인터입니다. 이 함수에는 `BOOL` 반환 형식 및 `UINT` 및 `BOOL*` 매개 변수가 있어야 합니다. 함수는 매개 변수를 TRUE로 설정 하 여 속성을 변경할 수 있도록 하 고 FALSE를 허용 하지 않도록 설정 해야 합니다. 이 함수는 알림이 처리 되었음을 나타내기 위해 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

*pfnChanged*<br/>
`OnChanged`이 속성에 대 한 알림을 처리 하는 멤버 함수에 대 한 포인터입니다. 함수는 `BOOL` 반환 형식 및 매개 변수를 포함 해야 합니다 `UINT` . 이 함수는 알림이 처리 되었음을 나타내기 위해 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a> ON_PROPNOTIFY_REFLECT

ON_PROPNOTIFY_REFLECT 매크로는 OLE 컨트롤의 래퍼 클래스의 이벤트 싱크 맵에 사용 되는 경우 컨트롤의 컨테이너에서 처리 되기 전에 컨트롤에서 보낸 속성 알림을 받습니다.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 이벤트 싱크 맵이 속한 클래스입니다.

*dispid*<br/>
알림과 관련 된 속성의 디스패치 ID입니다.

*pfnRequest*<br/>
`OnRequestEdit`이 속성에 대 한 알림을 처리 하는 멤버 함수에 대 한 포인터입니다. 이 함수에는 BOOL 반환 형식과 **bool** <strong>\*</strong> 매개 변수가 있어야 합니다. 이 함수는 속성을 변경할 수 있도록 매개 변수를 TRUE로 설정 하 고, 허용 하지 않으려면 FALSE로 설정 해야 합니다. 이 함수는 알림이 처리 되었음을 나타내기 위해 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

*pfnChanged*<br/>
`OnChanged`이 속성에 대 한 알림을 처리 하는 멤버 함수에 대 한 포인터입니다. 함수는 부울 반환 형식 및 매개 변수를 포함 하지 않아야 합니다. 이 함수는 알림이 처리 되었음을 나타내기 위해 TRUE를 반환 해야 합니다. 그렇지 않으면 FALSE입니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
