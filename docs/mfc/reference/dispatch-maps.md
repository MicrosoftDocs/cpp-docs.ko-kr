---
description: '자세한 정보: 디스패치 맵'
title: 디스패치 맵
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 3b160040af52e8346cbcbb09cc05c301f607052b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219969"
---
# <a name="dispatch-maps"></a>디스패치 맵

OLE Automation은 메서드를 호출 하 고 응용 프로그램에서 속성에 액세스 하는 방법을 제공 합니다. 이러한 요청을 디스패치 하는 MFC 라이브러리에서 제공 하는 메커니즘은 "디스패치 맵" 이며,이는 개체 함수 및 속성의 내부 및 외부 이름과 함수 인수의 데이터 형식을 지정 합니다.

|디스패치 맵 매크로|설명|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|클래스의 메서드 및 속성을 노출 하는 데 디스패치 맵이 사용 됨을 선언 합니다 (클래스 선언에서 사용 되어야 함).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|디스패치 맵의 정의를 시작 합니다.|
|[END_DISPATCH_MAP](#end_dispatch_map)|디스패치 맵의 정의를 종료 합니다.|
|[DISP_FUNCTION](#disp_function)|디스패치 맵에서 OLE 자동화 함수를 정의 하는 데 사용 됩니다.|
|[DISP_PROPERTY](#disp_property)|OLE automation 속성을 정의 합니다.|
|[DISP_PROPERTY_EX](#disp_property_ex)|OLE automation 속성을 정의 하 고 Get 및 Set 함수의 이름을로 설정 합니다.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|알림을 사용 하 여 OLE 자동화 속성을 정의 합니다.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|매개 변수를 사용 하 고 Get 및 Set 함수의 이름을로 설정 하는 OLE 자동화 속성을 정의 합니다.|
|[DISP_DEFVALUE](#disp_defvalue)|기존 속성을 개체의 기본값으로 만듭니다.|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a> DECLARE_DISPATCH_MAP

`CCmdTarget`프로그램의 파생 클래스가 OLE 자동화를 지 원하는 경우 해당 클래스는 해당 메서드 및 속성을 노출 하는 디스패치 맵을 제공 해야 합니다.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>설명

클래스 선언 끝에 DECLARE_DISPATCH_MAP 매크로를 사용 합니다. 그런 다음에서를 클릭 합니다. 클래스의 멤버 함수를 정의 하는 .CPP 파일 BEGIN_DISPATCH_MAP 매크로를 사용 합니다. 그런 다음 클래스의 노출 된 메서드 및 속성 (DISP_FUNCTION, DISP_PROPERTY 등)에 대 한 매크로 항목을 포함 합니다. 마지막으로 END_DISPATCH_MAP 매크로를 사용 합니다.

> [!NOTE]
> DECLARE_DISPATCH_MAP 후 멤버를 선언 하는 경우 **`public`** **`private`** 해당 멤버에 대 한 새 액세스 형식 (, 또는)을 지정 해야 합니다 **`protected`** .

응용 프로그램 마법사 및 코드 마법사는 자동화 클래스를 만들고 디스패치 맵을 유지 관리 하는 데 도움이 됩니다. 디스패치 맵에 대 한 자세한 내용은 [자동화 서버](../../mfc/automation-servers.md)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a> BEGIN_DISPATCH_MAP

디스패치 맵의 정의를 선언 합니다.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
이 디스패치 맵을 소유 하는 클래스의 이름을 지정 합니다.

*baseClass*<br/>
*Theclass* 의 기본 클래스 이름을 지정 합니다.

### <a name="remarks"></a>설명

클래스의 멤버 함수를 정의 하는 구현 파일 (.cpp)에서 BEGIN_DISPATCH_MAP 매크로를 사용 하 여 디스패치 맵을 시작 하 고, 각 디스패치 함수 및 속성에 대 한 매크로 항목을 추가 하 고, END_DISPATCH_MAP 매크로를 사용 하 여 디스패치 맵을 완성 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a> END_DISPATCH_MAP

디스패치 맵의 정의를 종료 합니다.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>설명

BEGIN_DISPATCH_MAP와 함께 사용 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a> DISP_FUNCTION

디스패치 맵에 OLE 자동화 함수를 정의 합니다.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*pszName*<br/>
함수의 외부 이름입니다.

*pfnMember*<br/>
멤버 함수의 이름입니다.

*vtRetVal*<br/>
함수의 반환 형식을 지정 하는 값입니다.

*vtsParams*<br/>
함수의 매개 변수 목록을 지정 하는 하나 이상의 상수에 대 한 공백으로 구분 된 목록입니다.

### <a name="remarks"></a>설명

*VtRetVal* 인수는 VARTYPE 유형입니다. 이 인수에 대 한 가능한 다음 값은 열거형에서 가져옵니다 `VARENUM` .

|기호|반환 형식|
|------------|-----------------|
|VT_EMPTY|**`void`**|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*VtsParams* 인수는 상수에서 공백으로 구분 된 값 목록입니다 `VTS_*` . 공백으로 구분 된 이러한 값 중 하나 이상 (쉼표 아님)은 함수의 매개 변수 목록을 지정 합니다. 예를 들면 다음과 같습니다.

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

short 정수를 포함 하는 목록 및 short 정수에 대 한 포인터를 지정 합니다.

`VTS_`상수 및 해당 의미는 다음과 같습니다.

|기호|매개 변수 형식|
|------------|--------------------|
|VTS_I2|**`short`**|
|VTS_I4|**`long`**|
|VTS_R4|**`float`**|
|VTS_R8|**`double`**|
|VTS_CY|`const CY` 또는 `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` 또는 `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__short\*__|
|VTS_PI4|__long\*__|
|VTS_PR4|__f\*__|
|VTS_PR8|__차례로\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|매개 변수 없음|

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="disp_property"></a><a name="disp_property"></a> DISP_PROPERTY

디스패치 맵에서 OLE automation 속성을 정의 합니다.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*pszName*<br/>
속성의 외부 이름입니다.

*memberName*<br/>
속성이 저장 된 멤버 변수의 이름입니다.

*vtPropType*<br/>
속성의 형식을 지정 하는 값입니다.

### <a name="remarks"></a>설명

*VtPropType* 인수는 **VARTYPE** 유형입니다. 이 인수에 사용할 수 있는 값은 VARENUM 열거형에서 가져옵니다.

|기호|속성 형식|
|------------|-----------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

외부 클라이언트가 속성을 변경 하는 경우 *memberName* 로 지정 된 멤버 변수의 값이 변경 됩니다. 변경에 대 한 알림이 없습니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a> DISP_PROPERTY_EX

OLE automation 속성을 정의 하 고 디스패치 맵에서 속성의 값을 가져오고 설정 하는 데 사용 되는 함수의 이름을로 설정 합니다.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*pszName*<br/>
속성의 외부 이름입니다.

*memberGet*<br/>
속성을 가져오는 데 사용 되는 멤버 함수의 이름입니다.

*집합*<br/>
속성을 설정 하는 데 사용 되는 멤버 함수의 이름입니다.

*vtPropType*<br/>
속성의 형식을 지정 하는 값입니다.

### <a name="remarks"></a>설명

*Memberget* 및 *MemberSet* 함수는 *vtPropType* 인수에 의해 결정 된 시그니처를 포함 합니다. *Memberget* 함수는 인수를 사용 하지 않고 *vtPropType* 에서 지정한 형식의 값을 반환 합니다. *MemberSet* 함수는 *vtPropType* 에 의해 지정 된 형식의 인수를 사용 하 고 아무 것도 반환 하지 않습니다.

*VtPropType* 인수는 VARTYPE 유형입니다. 이 인수에 사용할 수 있는 값은 VARENUM 열거형에서 가져옵니다. 이러한 값의 목록은 [DISP_FUNCTION](#disp_function)의 *vtRetVal* 매개 변수에 대 한 설명을 참조 하십시오. DISP_FUNCTION 설명에 나열 된 VT_EMPTY는 속성 데이터 형식으로 허용 되지 않습니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a> DISP_PROPERTY_NOTIFY

디스패치 맵에 알림을 사용 하 여 OLE automation 속성을 정의 합니다.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*szExternalName*<br/>
속성의 외부 이름입니다.

*memberName*<br/>
속성이 저장 된 멤버 변수의 이름입니다.

*pfnAfterSet*<br/>
*Szexternalname* 에 대 한 알림 함수의 이름입니다.

*vtPropType*<br/>
속성의 형식을 지정 하는 값입니다.

### <a name="remarks"></a>설명

DISP_PROPERTY으로 정의 된 속성과 달리 DISP_PROPERTY_NOTIFY으로 정의 된 속성은 속성이 변경 될 때 *pfnAfterSet* 에 지정 된 함수를 자동으로 호출 합니다.

*VtPropType* 인수는 VARTYPE 유형입니다. 이 인수에 사용할 수 있는 값은 VARENUM 열거형에서 가져옵니다.

|기호|속성 형식|
|------------|-----------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="disp_property_param"></a><a name="disp_property_param"></a> DISP_PROPERTY_PARAM

별도의 및 멤버 함수를 사용 하 여 액세스 되는 속성을 정의 `Get` `Set` 합니다.

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*pszExternalName*<br/>
속성의 외부 이름입니다.

*pfnGet*<br/>
속성을 가져오는 데 사용 되는 멤버 함수의 이름입니다.

*pfnSet*<br/>
속성을 설정 하는 데 사용 되는 멤버 함수의 이름입니다.

*vtPropType*<br/>
속성의 형식을 지정 하는 값입니다.

*vtsParams*<br/>
`VTS_*`각 매개 변수에 대해 하나씩, 공백으로 구분 된 variant 매개 변수 형식의 문자열입니다.

### <a name="remarks"></a>설명

DISP_PROPERTY_EX 매크로와 달리이 매크로를 사용 하면 속성에 대 한 매개 변수 목록을 지정할 수 있습니다. 이는 인덱싱된 속성 또는 매개 변수화 된 속성을 구현 하는 데 유용 합니다.

### <a name="example"></a>예제

사용자가 속성에 액세스할 때 특정 행과 열을 요청할 수 있게 해 주는 get 및 set 멤버 함수의 다음 선언을 고려 하십시오.

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

이러한 구문은 컨트롤 디스패치 맵의 다음 DISP_PROPERTY_PARAM 매크로에 해당 합니다.

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

또 다른 예로 다음 get 및 set 멤버 함수를 살펴보겠습니다.

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

이러한 구문은 컨트롤 디스패치 맵의 다음 DISP_PROPERTY_PARAM 매크로에 해당 합니다.

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a> DISP_DEFVALUE

기존 속성을 개체의 기본값으로 만듭니다.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*pszName*<br/>
개체의 "값"을 나타내는 속성의 외부 이름입니다.

### <a name="remarks"></a>설명

기본값을 사용하면 Visual Basic 애플리케이션에 대한 자동화 개체 프로그래밍을 더 간소화할 수 있습니다.

개체의 "기본값"은 개체에 대한 참조가 속성 또는 멤버 함수를 지정하지 않을 때 검색 또는 설정되는 속성입니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
