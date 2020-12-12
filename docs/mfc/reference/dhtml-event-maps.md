---
description: '자세한 정보: DHTML 이벤트 맵'
title: DHTML 이벤트 맵
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: b9df8f1aa59472de033943efd28f5c688c61e706
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220125"
---
# <a name="dhtml-event-maps"></a>DHTML 이벤트 맵

다음 매크로는 DHTML 이벤트를 처리 하는 데 사용할 수 있습니다.

## <a name="dhtml-event-map-macros"></a>DHTML 이벤트 맵 매크로

다음 매크로를 사용 하 여 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)파생 클래스에서 DHTML 이벤트를 처리할 수 있습니다.

|Name|설명|
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|DHTML 이벤트 맵의 시작을 표시 합니다.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|DHTML 이벤트 맵의 시작을 표시 합니다.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|DHTML 이벤트 맵을 선언 합니다.|
|[DHTML_EVENT](#dhtml_event)|단일 HTML 요소에 대 한 문서 수준에서 이벤트를 처리 하는 데 사용 됩니다.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|ActiveX 컨트롤에서 발생 한 이벤트를 처리 하는 데 사용 됩니다.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|특정 CSS 클래스를 사용 하 여 모든 HTML 요소의 문서 수준에서 이벤트를 처리 하는 데 사용 됩니다.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|요소 수준에서 이벤트를 처리 하는 데 사용 됩니다.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|HTML 요소의 이벤트를 처리 하는 데 사용 `onafterupdate` 됩니다.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|HTML 요소의 이벤트를 처리 하는 데 사용 `onbeforeupdate` 됩니다.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|HTML 요소의 이벤트를 처리 하는 데 사용 `onblur` 됩니다.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|HTML 요소의 이벤트를 처리 하는 데 사용 `onchange` 됩니다.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|HTML 요소의 이벤트를 처리 하는 데 사용 `onclick` 됩니다.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|HTML 요소의 이벤트를 처리 하는 데 사용 `ondataavailable` 됩니다.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|HTML 요소의 이벤트를 처리 하는 데 사용 `ondatasetchanged` 됩니다.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|HTML 요소의 이벤트를 처리 하는 데 사용 `ondatasetcomplete` 됩니다.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|HTML 요소의 이벤트를 처리 하는 데 사용 `ondblclick` 됩니다.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|HTML 요소의 이벤트를 처리 하는 데 사용 `ondragstart` 됩니다.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|HTML 요소의 이벤트를 처리 하는 데 사용 `onerrorupdate` 됩니다.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|HTML 요소의 이벤트를 처리 하는 데 사용 `onfilterchange` 됩니다.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|HTML 요소의 이벤트를 처리 하는 데 사용 `onfocus` 됩니다.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|HTML 요소의 이벤트를 처리 하는 데 사용 `onhelp` 됩니다.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|HTML 요소의 이벤트를 처리 하는 데 사용 `onkeydown` 됩니다.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|HTML 요소의 이벤트를 처리 하는 데 사용 `onkeypress` 됩니다.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|HTML 요소의 이벤트를 처리 하는 데 사용 `onkeyup` 됩니다.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|HTML 요소의 이벤트를 처리 하는 데 사용 `onmousedown` 됩니다.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|HTML 요소의 이벤트를 처리 하는 데 사용 `onmousemove` 됩니다.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|HTML 요소의 이벤트를 처리 하는 데 사용 `onmouseout` 됩니다.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|HTML 요소의 이벤트를 처리 하는 데 사용 `onmouseover` 됩니다.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|HTML 요소의 이벤트를 처리 하는 데 사용 `onmouseup` 됩니다.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|HTML 요소의 이벤트를 처리 하는 데 사용 `onresize` 됩니다.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|HTML 요소의 이벤트를 처리 하는 데 사용 `onrowenter` 됩니다.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|HTML 요소의 이벤트를 처리 하는 데 사용 `onrowexit` 됩니다.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|HTML 요소의 이벤트를 처리 하는 데 사용 `onselectstart` 됩니다.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|특정 HTML 태그를 사용 하는 모든 요소에 대해 문서 수준에서 이벤트를 처리 하는 데 사용 됩니다.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|DHTML 이벤트 맵의 끝을 표시 합니다.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|DHTML 이벤트 맵의 끝을 표시 합니다. |

## <a name="url-event-map-macros"></a>URL 이벤트 맵 매크로

다음 매크로를 사용 하 여 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)파생 클래스에서 DHTML 이벤트를 처리할 수 있습니다.

|Name|설명|
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|다중 페이지 DHTML 및 URL 이벤트 맵의 시작을 표시 합니다.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|포함 된 DHTML 이벤트 맵의 시작을 표시 합니다.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|URL 이벤트 항목 맵의 시작을 표시 합니다.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|다중 페이지 DHTML 및 URL 이벤트 맵을 선언 합니다.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|다중 페이지 DHTML 및 URL 이벤트 맵의 끝을 표시 합니다.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|포함 된 DHTML 이벤트 맵의 끝을 표시 합니다.|
|[END_URL_ENTRIES](#end_url_entries)|URL 이벤트 항목 맵의 끝을 표시 합니다.|
|[URL_EVENT_ENTRY](#url_event_entry)|URL 또는 HTML 리소스를 다중 페이지 대화 상자에 있는 페이지에 매핑합니다.|

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a> BEGIN_DHTML_EVENT_MAP

로 식별 된 클래스에 대 한 소스 파일에 배치 될 때 DHTML 이벤트 맵의 시작을 표시 합니다 `className` .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
DHTML 이벤트 맵을 포함 하는 클래스의 이름입니다. 이 클래스는 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) 에서 직접 또는 간접적으로 파생 되 고 해당 클래스 정의 내에 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) 매크로를 포함 해야 합니다.

### <a name="remarks"></a>설명

`CDHtmlDialog`HTML 요소나 웹 페이지의 ActiveX 컨트롤에서 발생 한 이벤트를 클래스의 처리기 함수로 라우팅하는 데 사용할 수 있는에 대 한 정보를 제공 하기 위해 클래스에 DHTML 이벤트 맵을 추가 합니다.

클래스의 구현 파일 (.cpp)에 BEGIN_DHTML_EVENT_MAP 매크로를 배치한 다음 클래스에서 처리할 이벤트 (예: mouseover 이벤트의 경우 DHTML_EVENT_ONMOUSEOVER)에 대해 매크로를 DHTML_EVENT 합니다. [END_DHTML_EVENT_MAP](#end_dhtml_event_map) 매크로를 사용 하 여 이벤트 맵의 끝을 표시 합니다. 이러한 매크로는 다음 함수를 구현 합니다.

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a> BEGIN_DHTML_EVENT_MAP_INLINE

*ClassName* 의 클래스 정의 내에서 DHTML 이벤트 맵의 시작을 표시 합니다.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
DHTML 이벤트 맵을 포함 하는 클래스의 이름입니다. 이 클래스는 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) 에서 직접 또는 간접적으로 파생 되 고 해당 클래스 정의 내에 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) 매크로를 포함 해야 합니다.

### <a name="remarks"></a>설명

`CDHtmlDialog`HTML 요소나 웹 페이지의 ActiveX 컨트롤에서 발생 한 이벤트를 클래스의 처리기 함수로 라우팅하는 데 사용할 수 있는에 대 한 정보를 제공 하기 위해 클래스에 DHTML 이벤트 맵을 추가 합니다.

클래스의 정의 (.h) 파일에 BEGIN_DHTML_EVENT_MAP 매크로를 놓고 클래스에서 처리할 이벤트 (예: mouseover 이벤트의 경우 DHTML_EVENT_ONMOUSEOVER)에 대해 매크로를 DHTML_EVENT 합니다. [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) 매크로를 사용 하 여 이벤트 맵의 끝을 표시 합니다. 이러한 매크로는 다음 함수를 구현 합니다.

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a> DECLARE_DHTML_EVENT_MAP

클래스 정의에서 DHTML 이벤트 맵을 선언 합니다.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>설명

이 매크로는 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)파생 클래스의 정의에 사용 됩니다.

[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) 또는 [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) 를 사용 하 여 맵을 구현 합니다.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) 는 다음 함수를 선언 합니다.

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event"></a><a name="dhtml_event"></a> DHTML_EVENT

*ElemName* 로 식별 되는 HTML 요소에 의해 시작 되는 *dispid* 에 의해 식별 되는 이벤트를 처리 합니다 (문서 수준).

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
처리할 이벤트의 DISPID입니다.

*elemName*<br/>
HTML 요소의 ID를 포함 하는 LPCWSTR는 이벤트를 소싱 하거나 NULL 인 문서 이벤트를 처리 합니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a> DHTML_EVENT_AXCONTROL

*Controlname* 으로 식별 되는 ActiveX 컨트롤에서 발생 한 *dispid* 로 식별 되는 이벤트를 처리 합니다.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
처리할 이벤트의 디스패치 ID입니다.

*controlName*<br/>
이벤트를 발생 시키는 컨트롤의 HTML ID를 보유 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a> DHTML_EVENT_CLASS

*ElemName* 로 식별 되는 CSS 클래스를 사용 하 여 *dispid* 에서 식별 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
처리할 이벤트의 디스패치 ID입니다.

*elemName*<br/>
HTML 요소의 CSS 클래스를 포함 하는 LPCWSTR는 이벤트를 소싱 합니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a> DHTML_EVENT_ELEMENT

*ElemName* 로 식별 되는 요소에서 *dispid* 로 식별 되는 이벤트를 처리 합니다.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
처리할 이벤트의 디스패치 ID입니다.

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

이 매크로를 사용 하 여 비 버블링 이벤트를 처리 하는 경우 이벤트의 소스는 *elemName* 으로 식별 되는 요소가 됩니다.

이 매크로를 사용 하 여 버블링 이벤트를 처리 하는 경우 *elemName* 에 의해 식별 되는 요소가 이벤트의 소스가 아닐 수 있습니다. 소스는 *elemName* 에 포함 된 모든 요소가 될 수 있습니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a> DHTML_EVENT_ONAFTERUPDATE

`onafterupdate` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a> DHTML_EVENT_ONBEFOREUPDATE

`onbeforeupdate` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a> DHTML_EVENT_ONBLUR

요소 수준에서 이벤트를 처리 `onblur` 합니다. 비 버블링 이벤트입니다.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a> DHTML_EVENT_ONCHANGE

요소 수준에서 이벤트를 처리 `onchange` 합니다. 비 버블링 이벤트입니다.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a> DHTML_EVENT_ONCLICK

`onclick` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a> DHTML_EVENT_ONDATAAVAILABLE

`ondataavailable` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a> DHTML_EVENT_ONDATASETCHANGED

`ondatasetchanged` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a> DHTML_EVENT_ONDATASETCOMPLETE

`ondatasetcomplete`로 식별 된 HTML 요소가 발생 시킨 이벤트를 문서 수준에서 처리 `elemName` 합니다.

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a> DHTML_EVENT_ONDBLCLICK

`ondblclick` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a> DHTML_EVENT_ONDRAGSTART

`ondragstart` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a> DHTML_EVENT_ONERRORUPDATE

`onerrorupdate` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a> DHTML_EVENT_ONFILTERCHANGE

`onfilterchange` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a> DHTML_EVENT_ONFOCUS

요소 수준에서 이벤트를 처리 `onfocus` 합니다. 비 버블링 이벤트입니다.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a> DHTML_EVENT_ONHELP

`onhelp` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a> DHTML_EVENT_ONKEYDOWN

`onkeydown` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a> DHTML_EVENT_ONKEYPRESS

`onkeypress` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a> DHTML_EVENT_ONKEYUP

`onkeyup` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a> DHTML_EVENT_ONMOUSEDOWN

`onmousedown` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a> DHTML_EVENT_ONMOUSEMOVE

`onmousemove` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a> DHTML_EVENT_ONMOUSEOUT

`onmouseout` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a> DHTML_EVENT_ONMOUSEOVER

`onmouseover` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a> DHTML_EVENT_ONMOUSEUP

`onmouseup` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a> DHTML_EVENT_ONRESIZE

요소 수준에서 이벤트를 처리 `onresize` 합니다. 비 버블링 이벤트입니다.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a> DHTML_EVENT_ONROWENTER

`onrowenter` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a> DHTML_EVENT_ONROWEXIT

`onrowexit` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a> DHTML_EVENT_ONSELECTSTART

`onselectstart` *ElemName* 로 식별 되는 HTML 요소에서 발생 한 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>매개 변수

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 ID를 포함 하는 LPCWSTR입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a> DHTML_EVENT_TAG

`dispid` *ElemName* 로 식별 되는 html 태그를 사용 하 여에서 가져온 이벤트를 문서 수준에서 처리 합니다.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
처리할 이벤트의 디스패치 ID입니다.

*elemName*<br/>
이벤트를 소싱 하는 HTML 요소의 HTML 태그입니다.

*memberFxn*<br/>
이벤트에 대 한 처리기 함수입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 클래스의 [DHTML 이벤트 맵에](#begin_dhtml_event_map_inline) 항목을 추가 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a> END_DHTML_EVENT_MAP

DHTML 이벤트 맵의 끝을 표시 합니다.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>설명

[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)와 함께 사용 해야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a> BEGIN_DHTML_URL_EVENT_MAP

다중 페이지 대화 상자에서 DHTML 및 URL 이벤트 맵의 정의를 시작 합니다.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>설명

[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)파생 클래스의 구현 파일에 BEGIN_DHTML_URL_EVENT_MAP을 배치 합니다. [포함 된 DHTML 이벤트 맵과](#begin_embed_dhtml_event_map) [URL 항목](#begin_url_entries)을 사용 하 여이를 따른 후 [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)를 사용 하 여 닫습니다. 클래스 정의에 [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) 매크로를 포함 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a> BEGIN_EMBED_DHTML_EVENT_MAP

다중 페이지 대화 상자에서 포함 된 DHTML 이벤트 맵의 정의를 시작 합니다.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
이벤트 맵을 포함 하는 클래스의 이름입니다. 이 클래스는 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)에서 직접 또는 간접적으로 파생 되어야 합니다. 포함 된 DHTML 이벤트 맵은 [dhtml 및 URL 이벤트 맵](#begin_dhtml_url_event_map)내에 있어야 합니다.

*mapName*<br/>
이에 해당 하는 이벤트 맵이 있는 페이지를 지정 합니다. 이는 [URL_EVENT_ENTRY](#url_event_entry) 매크로에서 실제로 URL 또는 HTML 리소스를 정의 하는 *mapName* 와 일치 합니다.

### <a name="remarks"></a>설명

다중 페이지 DHTML 대화 상자는 각각 DHTML 이벤트를 발생 시킬 수 있는 여러 HTML 페이지로 구성 되기 때문에, 포함 된 이벤트 맵은 페이지 별로 이벤트를 처리기에 매핑하는 데 사용 됩니다.

DHTML 및 URL 이벤트 맵 내의 포함 이벤트 맵은 BEGIN_EMBED_DHTML_EVENT_MAP 매크로와 [DHTML_EVENT](#dhtml_event) 매크로 및 [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) 매크로로 구성 됩니다.

포함 된 각 이벤트 맵에는 url 또는 HTML 리소스에 *mapName* (BEGIN_EMBED_DHTML_EVENT_MAP 지정)를 매핑하기 위해 해당 [url 이벤트 항목이](#url_event_entry) 필요 합니다.

### <a name="example"></a>예제

[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a> BEGIN_URL_ENTRIES

다중 페이지 대화 상자에서 URL 이벤트 항목 맵 정의를 시작합니다.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
URL 이벤트 항목 맵을 포함하는 클래스의 이름입니다. 이 클래스는 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)에서 직접 또는 간접적으로 파생 되어야 합니다. URL 이벤트 항목 맵은 [DHTML 및 url 이벤트 맵](#begin_dhtml_url_event_map)내에 있어야 합니다.

### <a name="remarks"></a>설명

다중 페이지 DHTML 대화 상자는 여러 HTML 페이지로 구성 되므로 URL 또는 HTML 리소스를 해당 [포함 된 DHTML 이벤트 맵에](#begin_embed_dhtml_event_map)매핑하는 데 url 이벤트 항목이 사용 됩니다. BEGIN_URL_ENTRIES와 [END_URL_ENTRIES](#end_url_entries) 매크로 사이에 URL_EVENT_ENTRY 매크로를 추가 합니다.

### <a name="example"></a>예제

[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a> DECLARE_DHTML_URL_EVENT_MAP

클래스 정의에서 DHTML 및 URL 이벤트 맵을 선언 합니다.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>설명

이 매크로는 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)파생 클래스의 정의에 사용 됩니다.

DHTML 및 URL 이벤트 맵은 포함 된 [dhtml 이벤트 맵과](#begin_embed_dhtml_event_map) [url 이벤트 항목](#begin_url_entries) 을 포함 하 여 페이지 별로 dhtml 이벤트를 처리기에 매핑합니다. [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) 를 사용 하 여 맵을 구현 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a> END_DHTML_URL_EVENT_MAP

DHTML 및 URL 이벤트 맵의 끝을 표시 합니다.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
이벤트 맵을 포함 하는 클래스의 이름입니다. 이 클래스는 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)에서 직접 또는 간접적으로 파생 되어야 합니다. 해당 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) 매크로의 *className* 과 일치 해야 합니다.

### <a name="example"></a>예제

[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a> END_EMBED_DHTML_EVENT_MAP

포함 된 DHTML 이벤트 맵의 끝을 표시 합니다.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>예제

[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="end_url_entries"></a><a name="end_url_entries"></a> END_URL_ENTRIES

URL 이벤트 항목 맵의 끝을 표시 합니다.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>예제

[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="url_event_entry"></a><a name="url_event_entry"></a> URL_EVENT_ENTRY

URL 또는 HTML 리소스를 다중 페이지 대화 상자에 있는 페이지에 매핑합니다.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
URL 이벤트 항목 맵을 포함하는 클래스의 이름입니다. 이 클래스는 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)에서 직접 또는 간접적으로 파생 되어야 합니다. URL 이벤트 항목 맵은 [DHTML 및 url 이벤트 맵](#begin_dhtml_url_event_map)내에 있어야 합니다.

*url*<br/>
페이지의 URL 또는 HTML 리소스입니다.

*mapName*<br/>
Url이 *url* 인 페이지를 지정 합니다. 이는이 페이지의 이벤트를 매핑하는 [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) 매크로의 *mapName* 와 일치 합니다.

### <a name="remarks"></a>설명

페이지가 HTML 리소스인 경우 *url* 은 리소스 ID 번호 (123 또는 ID_HTMLRES1이 아닌 "123")의 문자열 표현 이어야 합니다.

페이지 식별자 *mapName* 는 포함 된 DHTML 이벤트 맵을 URL 이벤트 항목 맵에 연결 하는 데 사용 되는 임의의 기호입니다. DHTML 및 URL 이벤트 맵으로 범위가 제한 됩니다.

### <a name="example"></a>예제

[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdhtml

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a> END_DHTML_EVENT_MAP_INLINE

DHTML 이벤트 맵의 끝을 표시 합니다.

### <a name="syntax"></a>구문

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>설명

[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)와 함께 사용 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdhtml

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)
