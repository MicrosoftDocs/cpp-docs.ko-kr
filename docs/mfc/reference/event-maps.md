---
description: '자세한 정보: 이벤트 맵'
title: 이벤트 맵
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: f3a6e949a4dc40927fc8946610707fbb404a400b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219852"
---
# <a name="event-maps"></a>이벤트 맵

컨트롤에서 컨트롤 개발자가 결정 한 일부 작업 (예: 키 입력, 마우스 클릭 또는 컨트롤 상태 변경)이 발생 했음을 컨테이너에 알릴 때마다 이벤트 발생 함수를 호출 합니다. 이 함수는 관련 이벤트를 발생 시켜 컨트롤 컨테이너에 몇 가지 중요 한 작업이 발생 했음을 알립니다.

MFC 라이브러리는 이벤트를 발생 시키는 데 최적화 된 프로그래밍 모델을 제공 합니다. 이 모델에서 "이벤트 맵"은 특정 컨트롤에 대 한 이벤트를 발생 시키는 함수를 지정 하는 데 사용 됩니다. 이벤트 맵은 각 이벤트에 대해 하나의 매크로를 포함 합니다. 예를 들어, 주식 클릭 이벤트를 발생 시키는 이벤트 맵은 다음과 같습니다.

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK`매크로는 컨트롤에서 마우스 클릭을 검색할 때마다 스톡 click 이벤트를 발생 시 고 함을 나타냅니다. 다른 스톡 이벤트의 자세한 목록은 [ActiveX 컨트롤: 이벤트](../../mfc/mfc-activex-controls-events.md)문서를 참조 하세요. 매크로를 사용 하 여 사용자 지정 이벤트를 나타낼 수도 있습니다.

이벤트 맵 매크로는 중요 하지만 일반적으로 직접 삽입 하지는 않습니다. 이는 이벤트 발생 함수를 이벤트에 연결 하는 데 사용 하는 경우 **속성** 창 ( **클래스 뷰**)이 자동으로 소스 파일에 이벤트 맵 항목을 만들기 때문입니다. 언제 든 지 이벤트 맵 항목을 편집 하거나 추가 하려면 **속성** 창을 사용할 수 있습니다.

이벤트 맵을 지원 하기 위해 MFC는 다음 매크로를 제공 합니다.

## <a name="event-map-macros"></a>이벤트 맵 매크로

### <a name="event-map-declaration-and-demarcation"></a>이벤트 맵 선언 및 경계

|Name|설명|
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|이벤트 맵이 이벤트를 이벤트 발생 함수에 매핑하기 위해 클래스에서 사용 됨을 선언 합니다 (클래스 선언에서 사용 되어야 함).|
|[BEGIN_EVENT_MAP](#begin_event_map)|이벤트 맵의 정의를 시작 합니다 (클래스 구현에서 사용 되어야 함).|
|[END_EVENT_MAP](#end_event_map)|이벤트 맵의 정의를 끝냅니다 (클래스 구현에서 사용 되어야 함).|

### <a name="event-mapping-macros"></a>이벤트 매핑 매크로

|Name|설명|
|-|-|
|[EVENT_CUSTOM](#event_custom)|지정 된 이벤트를 발생 시킬 이벤트 발생 함수를 나타냅니다.|
|[EVENT_CUSTOM_ID](#event_custom_id)|지정 된 디스패치 ID를 사용 하 여 지정 된 이벤트를 발생 시킬 이벤트 발생 함수를 나타냅니다.|

### <a name="message-mapping-macros"></a>메시지 매핑 매크로

|Name|설명|
|-|-|
|[ON_OLEVERB](#on_oleverb)|OLE 컨트롤에서 처리 하는 사용자 지정 동사를 나타냅니다.|
|[ON_STDOLEVERB](#on_stdoleverb)|OLE 컨트롤의 표준 동사 매핑을 재정의 합니다.|

## <a name="declare_event_map"></a><a name="declare_event_map"></a> DECLARE_EVENT_MAP

`COleControl`프로그램의 각 파생 클래스는 이벤트 맵을 제공 하 여 컨트롤에서 발생 하는 이벤트를 지정할 수 있습니다.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>설명

클래스 선언 끝에 DECLARE_EVENT_MAP 매크로를 사용 합니다. 그런 다음 클래스의 멤버 함수를 정의 하는 .cpp 파일에서 BEGIN_EVENT_MAP 매크로, 각 컨트롤의 이벤트에 대 한 매크로 항목, END_EVENT_MAP 매크로를 사용 하 여 이벤트 목록의 끝을 선언 합니다.

이벤트 맵에 대 한 자세한 내용은 [ActiveX 컨트롤: 이벤트](../../mfc/mfc-activex-controls-events.md)문서를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더** afxctl

## <a name="begin_event_map"></a><a name="begin_event_map"></a> BEGIN_EVENT_MAP

이벤트 맵의 정의를 시작 합니다.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이벤트 맵이 있는 컨트롤 클래스의 이름을 지정 합니다.

*baseClass*<br/>
*Theclass* 의 기본 클래스 이름을 지정 합니다.

### <a name="remarks"></a>설명

클래스의 멤버 함수를 정의 하는 구현 파일 (.cpp)에서 BEGIN_EVENT_MAP 매크로를 사용 하 여 이벤트 맵을 시작한 다음 각 이벤트에 대 한 매크로 항목을 추가 하 고 END_EVENT_MAP 매크로를 사용 하 여 이벤트 맵을 완료 합니다.

이벤트 맵과 BEGIN_EVENT_MAP 매크로에 대 한 자세한 내용은 [ActiveX 컨트롤: 이벤트](../../mfc/mfc-activex-controls-events.md)문서를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더** afxctl

## <a name="end_event_map"></a><a name="end_event_map"></a> END_EVENT_MAP

END_EVENT_MAP 매크로를 사용 하 여 이벤트 맵의 정의를 종료 합니다.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>요구 사항

**헤더** afxctl

## <a name="event_custom"></a><a name="event_custom"></a> EVENT_CUSTOM

사용자 지정 이벤트에 대 한 이벤트 맵 항목을 정의 합니다.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>매개 변수

*pszName*<br/>
이벤트의 이름입니다.

*pfnFire*<br/>
이벤트 발생 함수의 이름입니다.

*vtsParams*<br/>
함수의 매개 변수 목록을 지정 하는 하나 이상의 상수에 대 한 공백으로 구분 된 목록입니다.

### <a name="remarks"></a>설명

*VtsParams* 매개 변수는 상수에서 공백으로 구분 된 값 목록입니다 `VTS_` . 공백으로 구분 된 이러한 값 중 하나 이상 (쉼표 아님)은 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

RGB 색 값을 나타내는 32 비트 정수를 포함 하 고 `IFontDisp` OLE 글꼴 개체의 인터페이스에 대 한 포인터를 포함 하는 목록을 지정 합니다.

`VTS_`상수 및 해당 의미는 다음과 같습니다.

|기호|매개 변수 형식|
|------------|--------------------|
|VTS_I2|**`short`**|
|VTS_I4|**`long`**|
|VTS_R4|**`float`**|
|VTS_R8|**`double`**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|통화|
|VTS_DATE|DATE|
|VTS_BSTR|**`const`**__char \*__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|HANDLE|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Variant 데이터 상수에 대 한 포인터를 제공 하는 VTS_FONT 및 VTS_PICTURE를 제외 하 고 모든 variant 형식에 대해 추가 변형 상수가 정의 되었습니다. 이러한 상수는 규칙을 사용 하 여 명명 됩니다 `VTS_Pconstantname` . 예를 들어 VTS_PCOLOR은 VTS_COLOR 상수에 대 한 포인터입니다.

### <a name="requirements"></a>요구 사항

**헤더** afxctl

## <a name="event_custom_id"></a><a name="event_custom_id"></a> EVENT_CUSTOM_ID

*Dispid* 로 지정 된 디스패치 ID에 속하는 사용자 지정 이벤트에 대 한 이벤트 발생 함수를 정의 합니다.

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>매개 변수

*pszName*<br/>
이벤트의 이름입니다.

*dispid*<br/>
이벤트를 발생 시킬 때 컨트롤에서 사용 하는 디스패치 ID입니다.

*pfnFire*<br/>
이벤트 발생 함수의 이름입니다.

*vtsParams*<br/>
이벤트가 발생 했을 때 컨트롤 컨테이너에 전달 되는 매개 변수의 변수 목록입니다.

### <a name="remarks"></a>설명

*VtsParams* 인수는 상수에서 공백으로 구분 된 값 목록입니다 `VTS_` . 공백이 아닌 공백으로 구분 된 이러한 값 중 하나 이상이 함수의 매개 변수 목록을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

RGB 색 값을 나타내는 32 비트 정수를 포함 하 고 `IFontDisp` OLE 글꼴 개체의 인터페이스에 대 한 포인터를 포함 하는 목록을 지정 합니다.

`VTS_`상수 목록은 [EVENT_CUSTOM](#event_custom)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더** afxctl

## <a name="on_oleverb"></a><a name="on_oleverb"></a> ON_OLEVERB

이 매크로는 사용자 지정 동사를 컨트롤의 특정 멤버 함수에 매핑하는 메시지 맵 항목을 정의 합니다.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>매개 변수

*idsVerbName*<br/>
동사 이름에 대 한 문자열 리소스 ID입니다.

*memberFxn*<br/>
동사가 호출 될 때 프레임 워크에서 호출 하는 함수입니다.

### <a name="remarks"></a>설명

리소스 편집기를 사용 하 여 문자열 테이블에 추가 되는 사용자 지정 동사 이름을 만들 수 있습니다.

*MemberFxn* 에 대 한 함수 프로토타입은 다음과 같습니다.

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

*Lpmsg*, *hWndParent* 및 *lpRect* 매개 변수의 값은 멤버 함수의 해당 매개 변수에서 가져옵니다 `IOleObject::DoVerb` .

### <a name="requirements"></a>요구 사항

**헤더** afxole

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a> ON_STDOLEVERB

이 매크로를 사용 하 여 표준 동사의 기본 동작을 재정의할 수 있습니다.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>매개 변수

*iVerb*<br/>
재정의 되는 동사의 표준 동사 인덱스입니다.

*memberFxn*<br/>
동사가 호출 될 때 프레임 워크에서 호출 하는 함수입니다.

### <a name="remarks"></a>설명

표준 동사 인덱스는 폼 이며 `OLEIVERB_` 그 다음에는 작업을 수행 합니다. OLEIVERB_SHOW, OLEIVERB_HIDE 및 OLEIVERB_UIACTIVATE은 표준 동사의 몇 가지 예입니다.

*MemberFxn* 매개 변수로 사용할 함수 프로토타입에 대 한 설명은 [ON_OLEVERB](#on_oleverb) 를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더** afxole

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
