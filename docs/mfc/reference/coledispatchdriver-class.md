---
description: '자세히 알아보기: COleDispatchDriver 클래스'
title: COleDispatchDriver 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
ms.openlocfilehash: 0006f7922820602dd7a4a927b8064fc9e75f76f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227249"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver 클래스

OLE 자동화의 클라이언트 쪽을 구현합니다.

## <a name="syntax"></a>구문

```
class COleDispatchDriver
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDispatchDriver:: COleDispatchDriver](#coledispatchdriver)|`COleDispatchDriver` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDispatchDriver:: AttachDispatch](#attachdispatch)|`IDispatch`개체에 대 한 연결을 연결 `COleDispatchDriver` 합니다.|
|[COleDispatchDriver:: CreateDispatch](#createdispatch)|연결을 만들고 `IDispatch` 이를 개체에 연결 `COleDispatchDriver` 합니다.|
|[COleDispatchDriver::D etachDispatch](#detachdispatch)|`IDispatch`연결을 해제 하지 않고 분리 합니다.|
|[COleDispatchDriver::GetProperty](#getproperty)|자동화 속성을 가져옵니다.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|자동화 메서드를 호출 하는 도우미입니다.|
|[COleDispatchDriver:: ReleaseDispatch](#releasedispatch)|연결을 해제 `IDispatch` 합니다.|
|[COleDispatchDriver:: SetProperty](#setproperty)|자동화 속성을 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[COleDispatchDriver:: operator =](#operator_eq)|원본 값을 개체에 복사 `COleDispatchDriver` 합니다.|
|[COleDispatchDriver:: operator LPDISPATCH](#operator_lpdispatch)|기본 포인터에 액세스 `IDispatch` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleDispatchDriver:: m_bAutoRelease](#m_bautorelease)|`IDispatch`또는 개체 소멸 중에를 해제할 것인지 여부를 지정 합니다 `ReleaseDispatch` .|
|[COleDispatchDriver:: m_lpDispatch](#m_lpdispatch)|이에 연결 된 인터페이스에 대 한 포인터를 나타냅니다 `IDispatch` `COleDispatchDriver` .|

## <a name="remarks"></a>설명

`COleDispatchDriver` 에 기본 클래스가 없습니다.

OLE 디스패치 인터페이스는 개체의 메서드 및 속성에 대 한 액세스를 제공 합니다. `COleDispatchDriver`형식의 디스패치 연결을 연결, 분리, 만들기 및 해제 하는 멤버 함수입니다 `IDispatch` . 다른 멤버 함수는 가변 인수 목록을 사용 하 여 호출을 단순화 `IDispatch::Invoke` 합니다.

이 클래스는 직접 사용할 수 있지만 일반적으로 클래스 추가 마법사에서 만든 클래스 에서만 사용 됩니다. 형식 라이브러리를 가져와 새 c + + 클래스를 만드는 경우 새 클래스는에서 파생 됩니다 `COleDispatchDriver` .

사용에 대 한 자세한 내용은 `COleDispatchDriver` 다음 문서를 참조 하세요.

- [자동화 클라이언트](../../mfc/automation-clients.md)

- [자동화 서버](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`COleDispatchDriver`

## <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a> COleDispatchDriver:: AttachDispatch

`AttachDispatch` 멤버 함수를 호출하여 `IDispatch` 개체에 대한 `COleDispatchDriver` 포인터를 연결합니다. 자세한 내용은 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)을 참조하십시오.

```cpp
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpDispatch*<br/>
`IDispatch` 개체에 연결될 OLE `COleDispatchDriver` 개체에 대한 포인터입니다.

*bAutoRelease*<br/>
이 개체가 범위를 벗어날 때 디스패치를 해제할지 여부를 지정합니다.

### <a name="remarks"></a>설명

이 함수는 `IDispatch` 개체에 이미 연결된 모든 `COleDispatchDriver` 포인터를 해제합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a> COleDispatchDriver:: COleDispatchDriver

`COleDispatchDriver` 개체를 생성합니다.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>매개 변수

*lpDispatch*<br/>
`IDispatch` 개체에 연결될 OLE `COleDispatchDriver` 개체에 대한 포인터입니다.

*bAutoRelease*<br/>
이 개체가 범위를 벗어날 때 디스패치를 해제할지 여부를 지정합니다.

*dispatchSrc*<br/>
기존 개체에 대 한 참조 `COleDispatchDriver` 입니다.

### <a name="remarks"></a>설명

양식은 `COleDispatchDriver( LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE )` [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 인터페이스에 연결 됩니다.

양식은 `COleDispatchDriver( const COleDispatchDriver& dispatchSrc )` 기존 개체를 복사 `COleDispatchDriver` 하 고 참조 횟수를 증가 시킵니다.

폼에서 `COleDispatchDriver( )` 개체를 만들지만 `COleDispatchDriver` 인터페이스를 연결 하지는 않습니다 `IDispatch` . 인수 없이를 사용 하려면 먼저 `COleDispatchDriver( )` `IDispatch` [Coledispatchdriver:: Createdispatch](#createdispatch) 또는 [Coledispatchdriver:: AttachDispatch](#attachdispatch)를 사용 하 여를 연결 해야 합니다. 자세한 내용은 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)을 참조하십시오.

### <a name="example"></a>예제

  [COleDispatchDriver::CreateDispatch](#createdispatch)에 대한 예제를 참조하세요.

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a> COleDispatchDriver:: CreateDispatch

[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 인터페이스 개체를 만들고 `COleDispatchDriver` 개체에 연결합니다.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
만들려는 `IDispatch` 연결 개체의 클래스 ID입니다.

*pError*<br/>
만들기에서 발생하는 상태 코드를 포함할, OLE 예외 개체에 대한 포인터입니다.

*lpszProgID*<br/>
디스패치 개체를 만들려는 자동화 개체의 프로그래밍 ID(예: "Excel.Document.5")에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아닌 값이고, 실패하면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a> COleDispatchDriver::D etachDispatch

`IDispatch`이 개체에서 현재 연결을 분리 합니다.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>반환 값

이전에 연결 된 OLE 개체에 대 한 포인터 `IDispatch` 입니다.

### <a name="remarks"></a>설명

는 `IDispatch` 해제 되지 않습니다.

LPDISPATCH 유형에 대 한 자세한 내용은 Windows SDK에서 [IDispatch 인터페이스 구현](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a> COleDispatchDriver:: GetProperty

*Dwdispid* 로 지정 된 개체 속성을 가져옵니다.

```cpp
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
검색할 속성을 식별 합니다.

*vtProp*<br/>
검색할 속성을 지정 합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](#invokehelper)의 설명 섹션을 참조하세요.

*pvProp*<br/>
속성 값을 받을 변수의 주소입니다. *VtProp* 에 지정 된 형식과 일치 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a> COleDispatchDriver:: InvokeHelper

*Wflags* 로 지정 된 컨텍스트에서 *dwdispid* 로 지정 된 개체 메서드 또는 속성을 호출 합니다.

```cpp
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
호출할 메서드 또는 속성을 식별합니다.

*wFlags*<br/>
호출의 컨텍스트를 설명 하는 플래그 `IDispatch::Invoke` 입니다. . 가능한 값 목록은 Windows SDK에서 [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 의 *wflags* 매개 변수를 참조 하세요.

*vtRet*<br/>
반환 값 형식을 지정합니다. 가능한 값은 설명 섹션을 참조하세요.

*pvRet*<br/>
속성 값이나 반환 값을 받을 변수의 주소입니다. *Vtret* 에 지정 된 형식과 일치 해야 합니다.

*pbParamInfo*<br/>
*Pbparaminfo* 다음에 매개 변수의 형식을 지정 하는 null로 끝나는 바이트 문자열에 대 한 포인터입니다.

*...*<br/>
*Pbparaminfo* 에 지정 된 형식의 매개 변수 목록입니다.

### <a name="remarks"></a>설명

*Pbparaminfo* 매개 변수는 메서드나 속성에 전달 되는 매개 변수의 형식을 지정 합니다. 인수의 변수 목록은 구문 선언에서 **...** 로 표시됩니다.

*Vtret* 인수의 가능한 값은 varenum 열거형에서 가져옵니다. 가능한 값은 다음과 같습니다.

|기호|반환 형식|
|------------|-----------------|
|VT_EMPTY|**`void`**|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|**CY**|
|VT_DATE|**DATE**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**BOOL**|
|VT_VARIANT|**변형은**|
|VT_UNKNOWN|LPUNKNOWN|

*Pbparaminfo* 인수는 공백으로 구분 된 **VTS_** 상수 목록입니다. 공백(쉼표가 아님)으로 구분된 이러한 값 중 하나 이상이 함수의 매개 변수 목록을 지정합니다. 가능한 값은 [EVENT_CUSTOM](event-maps.md#event_custom) 매크로를 통해 나열됩니다.

이 함수는 매개 변수를 VARIANTARG 값으로 변환하고 나서 [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 메서드를 호출합니다. `Invoke` 호출에 실패하면 이 함수가 예외를 throw합니다. 에서 반환 된 (상태 코드)가 `IDispatch::Invoke` DISP_E_EXCEPTION 경우이 함수는 [coleexception](../../mfc/reference/coleexception-class.md) 개체를 throw 하 고, 그렇지 않으면 [coledispatchexception](../../mfc/reference/coledispatchexception-class.md)을 throw 합니다.

자세한 내용은 Windows SDK에서 [Idispatch 인터페이스 구현](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [Idispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)및 [COM 오류 코드 구조](/windows/win32/com/structure-of-com-error-codes) [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant)를 참조 하세요.

### <a name="example"></a>예제

  [COleDispatchDriver::CreateDispatch](#createdispatch)에 대한 예제를 참조하세요.

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a> COleDispatchDriver:: m_bAutoRelease

TRUE 이면 [Releasedispatch](#releasedispatch) 를 호출할 때 또는이 개체가 제거 될 때 [m_lpDispatch](#m_lpdispatch) 에서 액세스 하는 COM 개체가 자동으로 해제 됩니다 `COleDispatchDriver` .

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>설명

기본적으로 `m_bAutoRelease` 생성자에서는 TRUE로 설정 됩니다.

COM 개체를 해제 하는 방법에 대 한 자세한 내용은 Windows SDK [참조 계산](/windows/win32/com/implementing-reference-counting) 및 [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 구현을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a> COleDispatchDriver:: m_lpDispatch

이에 연결 된 인터페이스에 대 한 포인터 `IDispatch` `COleDispatchDriver` 입니다.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>설명

`m_lpDispatch`데이터 멤버는 LPDISPATCH 형식의 공용 변수입니다.

자세한 내용은 Windows SDK에서 [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 를 참조 하세요.

### <a name="example"></a>예제

  [Coledispatchdriver:: AttachDispatch](#attachdispatch)에 대 한 예제를 참조 하세요.

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a> COleDispatchDriver:: operator =

원본 값을 개체에 복사 `COleDispatchDriver` 합니다.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>매개 변수

*dispatchSrc*<br/>
기존 개체에 대 한 포인터 `COleDispatchDriver` 입니다.

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a> COleDispatchDriver:: operator LPDISPATCH

`IDispatch`개체의 기본 포인터에 액세스 `COleDispatchDriver` 합니다.

```
operator LPDISPATCH();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a> COleDispatchDriver:: ReleaseDispatch

연결을 해제 `IDispatch` 합니다. 자세한 내용은 [IDispatch 인터페이스 구현](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 을 참조 하세요.

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>설명

이 연결에 대해 자동 릴리스가 설정 된 경우이 함수는 `IDispatch::Release` 인터페이스를 해제 하기 전에를 호출 합니다.

### <a name="example"></a>예제

  [Coledispatchdriver:: AttachDispatch](#attachdispatch)에 대 한 예제를 참조 하세요.

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a> COleDispatchDriver:: SetProperty

*Dwdispid* 로 지정 된 OLE 개체 속성을 설정 합니다.

```cpp
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>매개 변수

*dwDispID*<br/>
설정할 속성을 확인합니다.

*vtProp*<br/>
설정할 속성의 유형을 지정합니다. 가능한 값에 대해서는 [COleDispatchDriver::InvokeHelper](#invokehelper)의 설명 섹션을 참조하세요.

*...*<br/>
*VtProp* 에 의해 지정 된 형식의 단일 매개 변수입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)
