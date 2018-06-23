---
title: 이벤트 맵 | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce997441c11287626e9681a661f858e33ccdde24
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322214"
---
# <a name="event-maps"></a>이벤트 맵

컨트롤 (컨트롤 개발자가 결정) 일부 동작 (예: 키, 마우스 클릭 또는 컨트롤의 상태에 대 한 변경) 발생 하는 해당 컨테이너에 알리기 위해 하지 않고자 한다면 때마다 이벤트 발생 함수를 호출 합니다. 이 함수는 관련 된 이벤트를 발생 시켜 서 몇 가지 중요 한 작업을 수행한 컨트롤 컨테이너를 알립니다.

Microsoft Foundation Class 라이브러리는 발생 하는 이벤트에 대 한 액세스에 최적화 된 프로그래밍 모델을 제공 합니다. 이 모델에서 "이벤트 맵"가 특정 컨트롤에 대 한 이벤트를 실행 하는 함수를 지정 하는 데 사용 됩니다. 이벤트 맵 각 이벤트에 대 한 매크로 포함합니다. 예를 들어는 event 맵이 있는 발생 재고 클릭 이벤트 다음과 같을 수 있습니다.

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK` 매크로 컨트롤은 재고 클릭 이벤트는 마우스를 발견할 때마다 한 번씩 클릭을 발생을 나타냅니다. 다른 스톡 이벤트 목록이 더 자세한 문서를 참조 하십시오. [ActiveX 컨트롤: 이벤트](../../mfc/mfc-activex-controls-events.md)합니다. 매크로 사용자 지정 이벤트를 나타내는 데 사용할 수 있습니다.

이벤트 맵 매크로 중요 하지만, 일반적으로 삽입 하지 않으면 이러한 직접 합니다. 즉, 속성 창을 사용 하면 이벤트와 이벤트 발생 함수를 연결할 때 소스 파일에서 이벤트 맵 항목 자동으로 만들어집니다. 이벤트 맵 항목을 추가 하거나 편집 하려면 언제 든 지 속성 창을 사용할 수 있습니다.

이벤트 맵을 지원 하기 위해 MFC는 다음과 같은 매크로 제공 합니다.

## <a name="event-map-macros"></a>이벤트 맵 매크로

### <a name="event-map-declaration-and-demarcation"></a>이벤트 맵 선언 및 구분

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|이벤트 맵 (클래스 선언에 사용 해야 합니다) 이벤트 발생 함수에 이벤트를 매핑할 수는 클래스에 사용될지를 선언 합니다.|
|[BEGIN_EVENT_MAP](#begin_event_map)|이벤트 맵 (클래스 구현에 사용 해야 합니다) 정의 시작 합니다.|
|[END_EVENT_MAP](#end_event_map)|이벤트 맵 (클래스 구현에 사용 해야 합니다) 정의 종료 합니다.|

### <a name="event-mapping-macros"></a>이벤트 매핑 매크로

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|이벤트 발생 함수는 지정된 된 이벤트 발생을 나타냅니다.|
|[EVENT_CUSTOM_ID](#event_custom_id)|이벤트 발생 함수는 지정 된 디스패치 id, 지정된 된 이벤트 발생을 나타냅니다.|

### <a name="message-mapping-macros"></a>메시지 매핑 매크로

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|OLE 컨트롤에서 처리 한 사용자 지정 동사를 나타냅니다.|
|[ON_STDOLEVERB](#on_stdoleverb)|OLE 컨트롤의 표준 동사 매핑이 무시 됩니다.|

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

각 `COleControl`-프로그램의 파생된 클래스에서 컨트롤은 발생 이벤트를 지정 하는 event 맵이 제공할 수 있습니다.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>설명

사용 하 여는 `DECLARE_EVENT_MAP` 끝 클래스 선언에는 매크로입니다. 그런 다음 클래스에 대 한 멤버 함수를 정의 하는.cpp 파일에서 사용 하는 `BEGIN_EVENT_MAP` 매크로, 각 컨트롤의 이벤트에 대해 매크로 항목 및 `END_EVENT_MAP` 이벤트 목록의 끝을 선언 하는 매크로입니다.

이벤트 맵에 대 한 자세한 내용은 문서 참조 [ActiveX 컨트롤: 이벤트](../../mfc/mfc-activex-controls-events.md)합니다.

### <a name="requirements"></a>요구 사항

**헤더** afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

이벤트 맵 정의 시작 합니다.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>매개 변수

*theClass*  
이 이벤트 매핑할 컨트롤 클래스의 이름을 지정 합니다.

*baseClass*  
기본 클래스의 이름을 지정 *theClass*합니다.

### <a name="remarks"></a>설명

클래스 멤버 함수를 정의 하는 구현 (.cpp) 파일에서로 이벤트 맵 시작는 `BEGIN_EVENT_MAP` 매크로, 그런 다음 각 사용자 이벤트에 대해 매크로 항목을 추가 하 고 있는 이벤트 맵을 완료는 `END_EVENT_MAP` 매크로입니다.

이벤트에 대 한 자세한 내용은 매핑합니다 및 `BEGIN_EVENT_MAP` 매크로 문서 참조 [ActiveX 컨트롤: 이벤트](../../mfc/mfc-activex-controls-events.md)합니다.

### <a name="requirements"></a>요구 사항

**헤더** afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP

사용 된 `END_EVENT_MAP` 이벤트 맵의 정의를 끝내는 매크로입니다.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>요구 사항

**헤더** afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM

사용자 지정 이벤트에 대 한 이벤트 맵 항목을 정의합니다.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>매개 변수

*pszName*  
이벤트의 이름입니다.

*pfnFire*  
이벤트 발생 함수의 이름입니다.

*vtsParams*  
함수의 매개 변수 목록을 지정 하는 하나 이상의 상수의 공백으로 구분 된 목록.

### <a name="remarks"></a>설명

*vtsParams* 매개 변수는 공백으로 구분 된 목록에서 값의 `VTS_` 상수입니다. 공백 (쉼표가 아님)으로 구분 된 이러한 값 중 하나 이상이 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

RGB를 나타내는 32 비트 정수를 포함 하는 목록에 대 한 포인터 뒤 값 색 지정는 `IFontDisp` OLE 글꼴 개체의 인터페이스입니다.

`VTS_` 상수 및 해당 의미는 다음과 같습니다.

|기호|매개 변수 형식|
|------------|--------------------|
|`VTS_I2`|**short**|
|`VTS_I4`|**long**|
|`VTS_R4`|**float**|
|`VTS_R8`|**double**|
|`VTS_COLOR`|`OLE_COLOR`|
|`VTS_CY`|`CURRENCY`|
|`VTS_DATE`|`DATE`|
|`VTS_BSTR`|**const** __char\*__|
|`VTS_DISPATCH`|`LPDISPATCH`|
|`VTS_FONT`|`IFontDispatch*`|
|`VTS_HANDLE`|`HANDLE`|
|`VTS_SCODE`|`SCODE`|
|`VTS_BOOL`|`BOOL`|
|`VTS_VARIANT`|`const VARIANT*`|
|`VTS_PVARIANT`|`VARIANT*`|
|`VTS_UNKNOWN`|`LPUNKNOWN`|
|`VTS_OPTEXCLUSIVE`|`OLE_OPTEXCLUSIVE`|
|`VTS_PICTURE`|`IPictureDisp*`|
|`VTS_TRISTATE`|`OLE_TRISTATE`|
|`VTS_XPOS_PIXELS`|`OLE_XPOS_PIXELS`|
|`VTS_YPOS_PIXELS`|`OLE_YPOS_PIXELS`|
|`VTS_XSIZE_PIXELS`|`OLE_XSIZE_PIXELS`|
|`VTS_YSIZE_PIXELS`|`OLE_YSIZE_PIXELS`|
|`VTS_XPOS_HIMETRIC`|`OLE_XPOS_HIMETRIC`|
|`VTS_YPOS_HIMETRIC`|`OLE_YPOS_HIMETRIC`|
|`VTS_XSIZE_HIMETRIC`|`OLE_XSIZE_HIMETRIC`|
|`VTS_YSIZE_HIMETRIC`|`OLE_YSIZE_HIMETRIC`|

> [!NOTE]
> 추가 variant 상수를 모든 variant 형식에 대해 정의 된 `VTS_FONT` 및 `VTS_PICTURE`, 가변 데이터 상수에 대 한 포인터를 제공 하는 합니다. 이러한 상수를 사용 하 여 라고는 `VTS_Pconstantname` 규칙입니다. 예를 들어 `VTS_PCOLOR` 에 대 한 포인터는 `VTS_COLOR` 상수입니다.

### <a name="requirements"></a>요구 사항

**헤더** afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID

이벤트 발생 하 여 지정 된 디스패치 ID에 속하는 사용자 지정 이벤트에 대 한 함수 정의 *dispid*합니다.

```cpp
EVENT_CUSTOM_ID(
  pszName,
  dispid,
  pfnFire,
  vtsParams)
```

### <a name="parameters"></a>매개 변수

*pszName*  
이벤트의 이름입니다.

*dispid*  
이벤트를 발생 하는 경우 컨트롤에서 사용 하는 디스패치 ID입니다.

*pfnFire*  
이벤트 발생 함수의 이름입니다.

*vtsParams*  
이벤트가 발생 하는 경우 컨트롤 컨테이너에 가변 매개 변수 목록을 전달.

### <a name="remarks"></a>설명

*vtsParams* 인수는 공백으로 구분 된 목록에서 값의 `VTS_` 상수입니다. 쉼표가 아닌 공백으로 구분 된 다음이 값 중 하나 이상을 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

RGB를 나타내는 32 비트 정수를 포함 하는 목록에 대 한 포인터 뒤 값 색 지정는 `IFontDisp` OLE 글꼴 개체의 인터페이스입니다.

목록은 `VTS_` 상수 참조 [EVENT_CUSTOM](#event_custom)합니다.

### <a name="requirements"></a>요구 사항

**헤더** afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB

이 매크로 사용자 지정 동사 컨트롤의 특정 멤버 함수에 매핑되는 메시지 맵 항목을 정의 합니다.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>매개 변수

*idsVerbName* 는 동사 이름의 문자열 리소스 ID입니다.

*memberFxn*  
동사를 호출할 때 프레임 워크에서 호출 하는 함수입니다.

### <a name="remarks"></a>설명

리소스 편집기는 문자열 테이블에 추가 된 사용자 지정 동사 이름을 만드는 데 사용할 수 있습니다.

함수 프로토타입에 *memberFxn* 됩니다.

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

값은 *lpMsg*, *창은*, 및 *lpRect* 의 해당 매개 변수에서 가져온 매개 변수는 **IOleObject::DoVerb** 멤버 함수입니다.

### <a name="requirements"></a>요구 사항

**헤더** afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

이 매크로 사용 하 여 표준 동사 기본 동작을 재정의 합니다.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>매개 변수

*iVerb*  
재정의 되는 동사에 대 한 표준 동사 인덱스입니다.

*memberFxn*  
동사를 호출할 때 프레임 워크에서 호출 하는 함수입니다.

### <a name="remarks"></a>설명

폼의 표준 동사 인덱스는 `OLEIVERB_`동작 이어집니다. `OLEIVERB_SHOW``OLEIVERB_HIDE`, 및 `OLEIVERB_UIACTIVATE` 표준 동사의 일부의 예입니다.

참조 [ON_OLEVERB](#on_oleverb) 에 대 한 설명은로 사용할 함수 프로토타입에 *memberFxn* 매개 변수입니다.


### <a name="requirements"></a>요구 사항

**헤더** afxole.h

## <a name="see-also"></a>참고자료

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
