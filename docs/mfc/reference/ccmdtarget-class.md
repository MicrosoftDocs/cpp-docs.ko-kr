---
description: '자세한 정보: CCmdTarget 클래스'
title: CCmdTarget 클래스
ms.date: 11/04/2016
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
ms.openlocfilehash: c4a579c0f224913cf47f332382fb71c12bdac755
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133018"
---
# <a name="ccmdtarget-class"></a>CCmdTarget 클래스

MFC 라이브러리 메시지 맵 아키텍처의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CCmdTarget : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|`CCmdTarget` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|커서를 모래 시계 커서로 표시 합니다.|
|[CCmdTarget::DoOleVerb](#dooleverb)|OLE 동사로 지정 된 작업을 수행 합니다.|
|[CCmdTarget::EnableAutomation](#enableautomation)|개체에 대 한 OLE 자동화를 허용 `CCmdTarget` 합니다.|
|[CCmdTarget::EnableConnections](#enableconnections)|연결 지점의 이벤트 발생을 사용 하도록 설정 합니다.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|개체의 형식 라이브러리를 사용 하도록 설정 합니다.|
|[CCmdTarget:: EndWaitCursor](#endwaitcursor)|이전 커서로 돌아갑니다.|
|[CCmdTarget:: EnumOleVerbs](#enumoleverbs)|개체의 OLE 동사를 열거 합니다.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|포인터와 연결 된 개체에 대 한 포인터를 반환 합니다 `CCmdTarget` `IDispatch` .|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|기본 디스패치 인터페이스 ID를 가져옵니다.|
|[CCmdTarget::GetIDispatch](#getidispatch)|개체와 연결 된 개체에 대 한 포인터를 반환 합니다 `IDispatch` `CCmdTarget` .|
|[CCmdTarget:: GetTypeInfoCount](#gettypeinfocount)|개체에서 제공 하는 형식 정보 인터페이스의 수를 검색 합니다.|
|[CCmdTarget:: GetTypeInfoOfGuid](#gettypeinfoofguid)|지정된 된 GUID에 해당 하는 형식 설명을 검색 합니다.|
|[CCmdTarget:: GetTypeLib](#gettypelib)|형식 라이브러리에 대 한 포인터를 가져옵니다.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|형식 라이브러리 캐시를 가져옵니다.|
|[CCmdTarget:: IsInvokeAllowed](#isinvokeallowed)|자동화 메서드 호출을 사용 합니다.|
|[CCmdTarget:: IsResultExpected](#isresultexpected)|자동화 함수에서 값을 반환 해야 하는 경우 0이 아닌 값을 반환 합니다.|
|[CCmdTarget:: OnCmdMsg](#oncmdmsg)|명령 메시지를 라우팅하고 디스패치합니다.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|마지막 OLE 참조가 해제 된 후 정리 합니다.|
|[CCmdTarget:: RestoreWaitCursor](#restorewaitcursor)|모래 시계 커서를 복원 합니다.|

## <a name="remarks"></a>설명

메시지 맵은 명령 또는 메시지를 처리 하기 위해 작성 하는 멤버 함수로 라우팅합니다. 명령은 메뉴 항목, 명령 단추 또는 액셀러레이터 키의 메시지입니다.

에서 파생 된 키 프레임 워크 클래스에 `CCmdTarget` 는 [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)및 [CFrameWnd](../../mfc/reference/cframewnd-class.md)가 포함 됩니다. 새 클래스에서 메시지를 처리 하려는 경우 이러한 파생 클래스 중 하나에서 클래스를 파생 시킵니다 `CCmdTarget` . 에서 직접 클래스를 파생 시키는 경우는 거의 `CCmdTarget` 없습니다.

명령 대상 및 라우팅에 대 한 개요는 `OnCmdMsg` [명령 대상](../../mfc/command-targets.md), [명령 라우팅](../../mfc/command-routing.md)및 [매핑 메시지](../../mfc/mapping-messages.md)를 참조 하세요.

`CCmdTarget` 모래 시계 커서의 표시를 처리 하는 멤버 함수를 포함 합니다. 명령을 실행 하는 데 눈에 띄는 시간 간격을 사용 하는 경우 모래 시계 커서를 표시 합니다.

메시지 맵과 마찬가지로 디스패치 맵은 OLE 자동화 기능을 노출 하는 데 사용 됩니다 `IDispatch` . 이 인터페이스를 노출 하면 다른 응용 프로그램 (예: Visual Basic)이 응용 프로그램을 호출할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a> CCmdTarget:: BeginWaitCursor

명령을 실행 하는 데 눈에 띄는 시간 간격을 사용 하는 경우 커서를 모래 시계 모양으로 표시 하려면이 함수를 호출 합니다.

```cpp
void BeginWaitCursor();
```

### <a name="remarks"></a>설명

프레임 워크는이 함수를 호출 하 여 `CDocument` 개체가 파일에 로드 또는 저장 되는 경우와 같이 사용 중인 사용자를 표시 합니다.

`BeginWaitCursor`처리와 같은 다른 동작이 커서를 변경할 수 있으므로의 작업은 단일 메시지 처리기 외부에서 항상 적용 되는 것은 아닙니다 `OnSetCursor` .

`EndWaitCursor`을 호출 하 여 이전 커서를 복원 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a> CCmdTarget:: CCmdTarget

`CCmdTarget` 개체를 생성합니다.

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a> CCmdTarget::D oOleVerb

OLE 동사로 지정 된 작업을 수행 합니다.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*iVerb*<br/>
동사의 숫자 식별자입니다.

*lpMsg*<br/>
동사를 호출한 이벤트를 설명 하는 [메시지](/windows/win32/api/winuser/ns-winuser-msg) 구조 (예: 두 번 클릭)에 대 한 포인터입니다.

*hWndParent*<br/>
개체가 포함된 문서 창의 핸들입니다.

*lpRect*<br/>
*HwndParent* 에서 개체의 경계 사각형을 정의 하는 좌표 (픽셀)를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 기본적으로 [:D IOleObject](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)의 구현입니다. 가능한 동작은 [Ccmdtarget:: EnumOleVerbs](#enumoleverbs)에 의해 열거 됩니다.

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a> CCmdTarget:: EnableAutomation

개체에 대해 OLE 자동화를 사용 하도록 설정 하려면이 함수를 호출 합니다.

```cpp
void EnableAutomation();
```

### <a name="remarks"></a>설명

이 함수는 일반적으로 개체의 생성자에서 호출 되며 디스패치 맵이 클래스에 대해 선언 된 경우에만 호출 해야 합니다. 자동화에 대 한 자세한 내용은 [자동화 클라이언트](../../mfc/automation-clients.md) 및 [자동화 서버](../../mfc/automation-servers.md)문서를 참조 하세요.

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a> CCmdTarget:: EnableConnections

연결 지점의 이벤트 발생을 사용 하도록 설정 합니다.

```cpp
void EnableConnections();
```

### <a name="remarks"></a>설명

연결 요소를 사용 하도록 설정 하려면 파생 클래스의 생성자에서이 멤버 함수를 호출 합니다.

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a> CCmdTarget:: EnableTypeLib

개체의 형식 라이브러리를 사용 하도록 설정 합니다.

```cpp
void EnableTypeLib();
```

### <a name="remarks"></a>설명

`CCmdTarget`형식 정보를 제공 하는 경우 파생 개체의 생성자에서이 멤버 함수를 호출 합니다.

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a> CCmdTarget:: EndWaitCursor

`BeginWaitCursor`모래 시계 커서에서 이전 커서로 돌아가려면 멤버 함수를 호출한 후이 함수를 호출 합니다.

```cpp
void EndWaitCursor();
```

### <a name="remarks"></a>설명

프레임 워크는 모래 시계 커서를 호출한 후에도이 멤버 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a> CCmdTarget:: EnumOleVerbs

개체의 OLE 동사를 열거 합니다.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>매개 변수

*ppenumOleVerb*<br/>
[IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb) 인터페이스에 대 한 포인터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

개체가 하나 이상의 OLE 동사를 지원 하면 TRUE이 고 (이 경우 \* *ppenumOleVerb* 은 `IEnumOLEVERB` 열거자 인터페이스를 가리킴), 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 기본적으로 [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs)의 구현입니다.

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a> CCmdTarget:: FromIDispatch

`IDispatch`클래스의 자동화 멤버 함수에서 받은 포인터를 `CCmdTarget` 개체의 인터페이스를 구현 하는 개체로 매핑하려면이 함수를 호출 `IDispatch` 합니다.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>매개 변수

*lpDispatch*<br/>
`IDispatch` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

`CCmdTarget` *Lpdispatch* 와 연결 된 개체에 대 한 포인터입니다. 이 함수는 `IDispatch` 개체가 Microsoft Foundation Class 개체로 인식 되지 않는 경우 NULL을 반환 합니다 `IDispatch` .

### <a name="remarks"></a>설명

이 함수의 결과는 멤버 함수에 대 한 호출의 역함수입니다 `GetIDispatch` .

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a> CCmdTarget:: GetDispatchIID

기본 디스패치 인터페이스 ID를 가져옵니다.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>매개 변수

*pIID*<br/>
인터페이스 ID ([GUID] (/windows/win32/api/guiddef/ns-guiddef-guid.)에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다. 성공 하면 \* *piid* 가 기본 디스패치 인터페이스 ID로 설정 됩니다.

### <a name="remarks"></a>설명

파생 된 클래스는이 멤버 함수를 재정의 해야 합니다. 재정의 되지 않으면 `GetDispatchIID` FALSE를 반환 합니다. [COleControl](../../mfc/reference/colecontrol-class.md)을 참조 하세요.

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a> CCmdTarget:: GetIDispatch

`IDispatch`포인터를 반환 `IDispatch` 하거나 참조로 포인터를 사용 하는 자동화 메서드에서 포인터를 검색 하려면이 멤버 함수를 호출 `IDispatch` 합니다.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>매개 변수

*bAddRef*<br/>
개체의 참조 횟수를 증가 시킬 것인지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

`IDispatch`개체와 연결 된 포인터입니다.

### <a name="remarks"></a>설명

생성자에서를 호출 하는 개체의 경우 `EnableAutomation` 자동화를 사용 하도록 설정 하면이 함수는 인터페이스를 통해 통신 하는 `IDispatch` 클라이언트에서 사용 하는의 Foundation 클래스 구현에 대 한 포인터를 반환 합니다 `IDispatch` . 이 함수를 호출 하면 포인터에 대 한 참조가 자동으로 추가 되므로 [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)에 대 한 호출을 만들 필요가 없습니다.

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a> CCmdTarget:: GetTypeInfoCount

개체에서 제공 하는 형식 정보 인터페이스의 수를 검색 합니다.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>반환 값

형식 정보 인터페이스의 수입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 기본적으로 [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)을 구현 합니다.

파생 클래스는 제공 된 형식 정보 인터페이스의 수 (0 또는 1)를 반환 하도록이 함수를 재정의 해야 합니다. 재정의 되지 않으면 `GetTypeInfoCount` 0을 반환 합니다. 재정의 하려면 `GetTypeLib` 및 `GetTypeLibCache`도 구현 하는 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) 매크로를 사용 합니다.

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a> CCmdTarget:: GetTypeInfoOfGuid

지정된 된 GUID에 해당 하는 형식 설명을 검색 합니다.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>매개 변수

*lcid*<br/>
로캘 식별자 ( `LCID` )입니다.

*guid*<br/>
유형 설명의 [GUID] (/windows/win32/api/guiddef/ns-guiddef-guid)입니다.

*ppTypeInfo*<br/>
인터페이스에 대 한 포인터에 대 한 포인터 `ITypeInfo` 입니다.

### <a name="return-value"></a>반환 값

호출의 성공 또는 실패를 나타내는 HRESULT입니다. 성공 하면 \* *pptypeinfo* 가 유형 정보 인터페이스를 가리킵니다.

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a> CCmdTarget:: GetTypeLib

형식 라이브러리에 대 한 포인터를 가져옵니다.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>매개 변수

*lcid*<br/>
LCID(로캘 식별자)입니다.

*ppTypeLib*<br/>
인터페이스에 대 한 포인터에 대 한 포인터 `ITypeLib` 입니다.

### <a name="return-value"></a>반환 값

호출의 성공 또는 실패를 나타내는 HRESULT입니다. 성공 하면 \* *pptypelib* 가 형식 라이브러리 인터페이스를 가리킵니다.

### <a name="remarks"></a>설명

파생 클래스는이 멤버 함수를 재정의 해야 합니다. 재정의 되지 않으면 `GetTypeLib` TYPE_E_CANTLOADLIBRARY 반환 됩니다. `GetTypeInfoCount` 및 `GetTypeLibCache`도 구현하는 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) 매크로를 사용합니다.

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a> CCmdTarget:: GetTypeLibCache

형식 라이브러리 캐시를 가져옵니다.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>반환 값

`CTypeLibCache` 개체에 대한 포인터입니다.

### <a name="remarks"></a>설명

파생 된 클래스는이 멤버 함수를 재정의 해야 합니다. 재정의 되지 않으면 `GetTypeLibCache` NULL이 반환 됩니다. `GetTypeInfoCount` 및 `GetTypeLib`도 구현하는 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) 매크로를 사용합니다.

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a> CCmdTarget:: IsInvokeAllowed

이 함수는 `IDispatch::Invoke` 지정 된 자동화 메서드 ( *dispid* 로 식별)를 호출할 수 있는지 여부를 확인 하기 위해의 MFC 구현에 의해 호출 됩니다.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>매개 변수

*dispid*<br/>
디스패치 ID입니다.

### <a name="return-value"></a>반환 값

메서드를 호출할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 `IsInvokeAllowed` TRUE를 반환 하면 `Invoke` 는 메서드를 호출 합니다. 그렇지 않으면가 `Invoke` 실패 하 고 E_UNEXPECTED 반환 됩니다.

파생 클래스는이 함수를 재정의 하 여 적절 한 값을 반환할 수 있습니다 (재정의 되지 않은 경우 `IsInvokeAllowed` TRUE를 반환 함). 자세한 내용은 특정 [COleControl:: IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)를 참조 하세요.

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a> CCmdTarget:: IsResultExpected

`IsResultExpected`클라이언트에서 자동화 함수 호출의 반환 값을 예상 하는지 여부를 확인 하는 데 사용 합니다.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>반환 값

자동화 함수에서 값을 반환 해야 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

OLE 인터페이스는 클라이언트에서 함수 호출 결과를 사용 하 고 있는지 여부에 대 한 정보를 MFC에 제공 하며, MFC는이 정보를 사용 하 여에 대 한 호출의 결과를 확인 `IsResultExpected` 합니다. 반환 값의 프로덕션이 시간 또는 리소스를 많이 사용 하는 경우 반환 값을 계산 하기 전에이 함수를 호출 하 여 효율성을 높일 수 있습니다.

이 함수는 클라이언트에서 호출한 자동화 함수에서 호출 하는 경우 다른 자동화 함수에서 유효한 반환 값을 얻을 수 있도록 0을 한 번만 반환 합니다.

`IsResultExpected` 는 자동화 함수 호출이 진행 되 고 있지 않을 때 호출 되는 경우 0이 아닌 값을 반환 합니다.

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a> CCmdTarget:: OnCmdMsg

명령 메시지를 라우팅하고 발송 하 고 명령 사용자 인터페이스 개체의 업데이트를 처리 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
명령 ID를 포함 합니다.

*nCode*<br/>
명령 알림 코드를 식별 합니다. *Ncode* 의 값에 대 한 자세한 내용은 **설명 부분** 을 참조 하십시오.

*pExtra*<br/>
*Ncode* 의 값에 따라 사용 됩니다. *Pextra* 에 대 한 자세한 내용은 **설명** 을 참조 하세요.

*pHandlerInfo*<br/>
NULL이 아닌 경우는 `OnCmdMsg` 명령을 발송 하는 대신 *Phandlerinfo* 구조의 *ptarget* 및 *pmf* 멤버를 채웁니다. 일반적으로이 매개 변수는 NULL 이어야 합니다.

### <a name="return-value"></a>반환 값

메시지가 처리 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이는 프레임 워크 명령 아키텍처의 기본 구현 루틴입니다.

런타임에는 `OnCmdMsg` 다른 개체에 명령을 디스패치 하거나 `CCmdTarget::OnCmdMsg` 실제 메시지 매핑 조회를 수행 하는 루트 클래스를 호출 하 여 명령 자체를 처리 합니다. 기본 명령 라우팅에 대 한 자세한 내용은 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요.

드문 경우 지만이 멤버 함수를 재정의 하 여 프레임 워크의 표준 명령 라우팅을 확장할 수 있습니다. 명령 라우팅 아키텍처에 대 한 자세한 내용은 [기술 정보 21](../../mfc/tn021-command-and-message-routing.md) 을 참조 하세요.

을 재정의 하는 경우 ncode `OnCmdMsg` 의 값에 따라 *ncode*, 명령 알림 코드 및 *pextra* 에 적절 한 값을 제공 해야 합니다.  다음 표에서는 해당 값을 보여 줍니다.

|*Ncode* 값|*Pextra* 값|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a> CCmdTarget:: OnFinalRelease

개체에 대 한 마지막 OLE 참조가 해제 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>설명

이 상황에 대 한 특별 한 처리를 제공 하려면이 함수를 재정의 합니다. 기본 구현에서는 개체를 삭제 합니다.

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a> CCmdTarget:: RestoreWaitCursor

시스템 커서가 변경 된 후에 적절 한 모래 시계 커서를 복원 하려면이 함수를 호출 합니다 (예: 긴 작업 중에 메시지 상자를 연 후 닫은 후).

```cpp
void RestoreWaitCursor();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI 클래스](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument 클래스](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp 클래스](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver 클래스](../../mfc/reference/coledispatchdriver-class.md)
