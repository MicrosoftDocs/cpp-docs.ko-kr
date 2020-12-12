---
description: 'TN065: OLE 자동화 서버에 대 한 Dual-Interface 지원에 대해 자세히 알아보세요.'
title: 'TN065: OLE 자동화 서버에 대한 이중 인터페이스 지원'
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 9add7b42c832944c10b4b607f26b6ca8f23ae300
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214574"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: OLE 자동화 서버에 대한 이중 인터페이스 지원

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 MFC 기반 OLE 자동화 서버 응용 프로그램에 이중 인터페이스 지원을 추가 하는 방법에 대해 설명 합니다. [Acdual](../overview/visual-cpp-samples.md) 샘플은 이중 인터페이스 지원을 보여 주고,이 메모의 예제 코드는 ACDUAL에서 가져옵니다. DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART 및 IMPLEMENT_DUAL_ERRORINFO와 같이이 메모에 설명 된 매크로는 ACDUAL 샘플의 일부 이며 있는 MFCDUAL.H에서 찾을 수 있습니다.

## <a name="dual-interfaces"></a>이중 인터페이스

OLE 자동화를 사용 하 여 `IDispatch` 인터페이스, VTBL 인터페이스 또는 이중 인터페이스 (둘 다 포함)를 구현할 수 있지만, 모든 노출 된 OLE 자동화 개체에 대해 이중 인터페이스를 구현 하는 것이 좋습니다. 이중 인터페이스에는 오버 `IDispatch` 전용 또는 VTBL 전용 인터페이스의 매우 많은 장점이 있습니다.

- 바인딩은 VTBL 인터페이스를 통해 컴파일 타임에 발생 하거나 런타임에를 통해 수행할 수 있습니다 `IDispatch` .

- VTBL 인터페이스를 사용할 수 있는 OLE 자동화 컨트롤러는 성능 향상의 이점을 누릴 수 있습니다.

- 인터페이스를 사용 하는 기존 OLE 자동화 컨트롤러는 `IDispatch` 계속 작동 합니다.

- VTBL 인터페이스는 c + +에서 보다 쉽게 호출할 수 있습니다.

- 이중 인터페이스는 Visual Basic 개체 지원 기능과의 호환성을 위해 필요 합니다.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>CCmdTarget-Based 클래스에 Dual-Interface 지원 추가

이중 인터페이스는 실제에서 파생 된 사용자 지정 인터페이스입니다 `IDispatch` . 기반 클래스에서 이중 인터페이스 지원을 구현 하는 가장 간단한 방법은 `CCmdTarget` 먼저 MFC와 클래스 마법사를 사용 하 여 클래스에서 일반 디스패치 인터페이스를 구현한 후 나중에 사용자 지정 인터페이스를 추가 하는 것입니다. 대부분의 경우 사용자 지정 인터페이스 구현은 단순히 MFC 구현에 다시 위임 됩니다 `IDispatch` .

먼저, 개체에 대 한 이중 인터페이스를 정의 하도록 서버에 대 한 ODL 파일을 수정 합니다. 이중 인터페이스를 정의 하려면 `DISPINTERFACE` Visual C++ 마법사가 생성 하는 문 대신 interface 문을 사용 해야 합니다. 기존 문을 제거 하는 대신 `DISPINTERFACE` 새 interface 문을 추가 합니다. `DISPINTERFACE`폼을 유지 하면 클래스 마법사를 사용 하 여 속성 및 메서드를 개체에 추가할 수 있지만 해당 속성 및 메서드를 인터페이스 문에 추가 해야 합니다.

이중 인터페이스에 대 한 인터페이스 문에는 *OLEAUTOMATION* 및 *이중* 특성이 있어야 하며,이 인터페이스는에서 파생 되어야 합니다 `IDispatch` . [Guidgen.exe](../overview/visual-cpp-samples.md) 샘플을 사용 하 여 이중 인터페이스용 **IID** 를 만들 수 있습니다.

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

인터페이스 문을 배치한 후에는 메서드 및 속성에 대 한 항목을 추가 하기 시작 합니다. 이중 인터페이스의 경우 이중 인터페이스의 메서드 및 속성 접근자 함수가 **HRESULT** 를 반환 하 고 특성을 사용 하 여 반환 값을 매개 변수로 전달 하도록 매개 변수 목록을 다시 정렬 해야 합니다 `[retval,out]` . 속성의 경우 `propget` 동일한 id를 사용 하 여 읽기 () 및 쓰기 () 액세스 함수를 모두 추가 해야 합니다 `propput` . 예를 들어:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

메서드 및 속성을 정의한 후에는 coclass 문에 있는 interface 문에 대 한 참조를 추가 해야 합니다. 예를 들어:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

ODL 파일이 업데이트 되 면 MFC의 인터페이스 맵 메커니즘을 사용 하 여 개체 클래스의 이중 인터페이스에 대 한 구현 클래스를 정의 하 고 MFC의 메커니즘에서 해당 항목을 만듭니다 `QueryInterface` . `INTERFACE_PART`ODL의 interface 문에 있는 각 항목에 대 한 블록에는 하나의 항목이 필요 하 고 디스패치 인터페이스에 대 한 항목을 포함 해야 합니다. *Propput* 특성을 사용 하는 각 ODL 항목에는 라는 함수가 필요 `put_propertyname` 합니다. *Propget* 특성을 포함 하는 각 항목에는 라는 함수가 필요 `get_propertyname` 합니다.

이중 인터페이스에 대 한 구현 클래스를 정의 하려면 `DUAL_INTERFACE_PART` 개체 클래스 정의에 블록을 추가 합니다. 예를 들어:

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

이중 인터페이스를 MFC의 [QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object) 메커니즘에 연결 하려면 `INTERFACE_PART` 인터페이스 맵에 항목을 추가 합니다.

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

다음에는 인터페이스의 구현을 채워야 합니다. 대부분의 경우에는 기존 MFC 구현에 위임할 수 있습니다 `IDispatch` . 예를 들어:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

개체의 메서드 및 속성 접근자 함수에는 구현을 채워야 합니다. 메서드 및 속성 함수는 일반적으로 클래스 마법사를 사용 하 여 생성 된 메서드로 다시 위임할 수 있습니다. 그러나 변수에 직접 액세스 하기 위한 속성을 설정 하는 경우 변수에 값을 가져오거나 설정 하는 코드를 작성 해야 합니다. 예를 들어:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>Dual-Interface 포인터 전달

특히를 호출 해야 하는 경우 이중 인터페이스 포인터를 전달 하는 것은 간단 하지 않습니다 `CCmdTarget::FromIDispatch` . `FromIDispatch` 는 MFC의 포인터 에서만 작동 `IDispatch` 합니다. 이 문제를 해결 하는 한 가지 방법은 MFC에 의해 설정 된 원래 포인터를 쿼리하고이를 `IDispatch` 필요로 하는 함수에 해당 포인터를 전달 하는 것입니다. 예를 들어:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

이중 인터페이스 메서드를 통해 포인터를 다시 전달 하기 전에 MFC `IDispatch` 포인터에서 이중 인터페이스 포인터로 변환 해야 할 수 있습니다. 예를 들어:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>응용 프로그램의 형식 라이브러리 등록

응용 프로그램 마법사는 시스템에 OLE 자동화 서버 응용 프로그램의 형식 라이브러리를 등록 하는 코드를 생성 하지 않습니다. 형식 라이브러리를 등록 하는 다른 방법이 있지만 응용 프로그램이 독립 실행형으로 실행 될 때마다 해당 OLE 형식 정보를 업데이트할 때 형식 라이브러리를 등록 하는 것이 편리 합니다.

응용 프로그램이 독립적으로 실행 될 때마다 응용 프로그램의 형식 라이브러리를 등록 하려면:

- AFXCTL를 포함 합니다. 표준에는 헤더 파일 (STDAFX.H)이 포함 됩니다. H는 함수 정의에 액세스 `AfxOleRegisterTypeLib` 합니다.

- 응용 프로그램의 `InitInstance` 함수에서에 대 한 호출을 찾습니다 `COleObjectFactory::UpdateRegistryAll` . 이 호출을 수행 하 고 형식 라이브러리 `AfxOleRegisterTypeLib` 의 이름과 함께 형식 라이브러리에 해당 하는 **LIBID** 를 지정 하 여에 대 한 호출을 추가 합니다.

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>형식 라이브러리 변경 내용에 맞게 프로젝트 빌드 설정 수정

형식 라이브러리가 다시 빌드될 때마다 MkTypLib에서 **UUID** 정의가 포함 된 헤더 파일을 생성 하도록 프로젝트의 빌드 설정을 수정 하려면 다음을 수행 합니다.

1. **빌드** 메뉴에서 **설정** 을 클릭 한 후 각 구성에 대 한 파일 목록에서 ODL 파일을 선택 합니다.

2. **OLE 유형** 탭을 클릭 하 고 **출력 헤더** 파일 이름 필드에 파일 이름을 지정 합니다. MkTypLib가 기존 파일을 덮어쓰기 때문에 프로젝트에서 아직 사용 하지 않은 파일 이름을 사용 합니다. **확인** 을 클릭 하 여 **빌드 설정** 대화 상자를 닫습니다.

MkTypLib에서 생성 된 헤더 파일의 **UUID** 정의를 프로젝트에 추가 하려면 다음을 수행 합니다.

1. 표준에 포함 된 MkTypLib 헤더 *파일을 포함 합니다.*

2. 새 파일인 INITIIDS를 만듭니다. CPP를 추가 하 고 프로젝트에 추가 합니다. 이 파일에는 OLE2를 포함 한 후 MkTypLib에서 생성 된 헤더 파일을 포함 합니다. H 및 INITGUID입니다. 넣기

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. **빌드** 메뉴에서 **설정** 을 클릭 한 다음 INITIIDS를 선택 합니다. 각 구성에 대 한 파일 목록에서 .CPP를 표시 합니다.

4. **C + +** 탭을 클릭 하 고, **미리 컴파일된** 헤더 범주를 클릭 하 고, **미리 컴파일된 헤더 사용 안 함** 라디오 단추를 선택 합니다. 확인을 클릭 하 여 **빌드 설정** 대화 상자를 닫습니다.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>형식 라이브러리에 올바른 개체 클래스 이름 지정

와 Visual C++ 함께 제공 되는 마법사는 구현 클래스 이름을 잘못 사용 하 여 OLE에서 만들 수 있는 클래스에 대 한 서버의 ODL 파일에 coclass를 지정 합니다. 이는 작동 하지만 구현 클래스 이름은 개체의 사용자가 사용 하려는 클래스 이름이 아닐 수 있습니다. 올바른 이름을 지정 하려면 ODL 파일을 열고 각 coclass 문을 찾은 다음 구현 클래스 이름을 올바른 외부 이름으로 바꿉니다.

Coclass 문을 변경 하면 MkTypLib 생성 헤더 파일에 있는 **CLSID** 의 변수 이름이 그에 따라 변경 됩니다. 새 변수 이름을 사용 하도록 코드를 업데이트 해야 합니다.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>예외 및 자동화 오류 인터페이스 처리

자동화 개체의 메서드 및 속성 접근자 함수에서 예외를 throw 할 수 있습니다. 그렇다면 이중 인터페이스 구현에서이를 처리 하 고 OLE 자동화 오류 처리 인터페이스인를 통해 해당 예외에 대 한 정보를 컨트롤러에 다시 전달 해야 합니다 `IErrorInfo` . 이 인터페이스는 및 VTBL 인터페이스를 통해 자세한 컨텍스트 오류 정보를 제공 `IDispatch` 합니다. 오류 처리기를 사용할 수 있음을 나타내려면 인터페이스를 구현 해야 합니다 `ISupportErrorInfo` .

오류 처리 메커니즘을 설명 하기 위해 표준 디스패치를 구현 하는 데 사용 되는 클래스 마법사 생성 함수가 예외를 throw 한다고 가정 합니다. MFC의 구현은 `IDispatch::Invoke` 일반적으로 이러한 예외를 catch 하 고 호출을 통해 반환 되는 EXCEPTINFO 구조체로 변환 합니다 `Invoke` . 그러나 VTBL 인터페이스를 사용 하는 경우 예외를 직접 catch 해야 합니다. 이중 인터페이스 메서드를 보호 하는 예제는 다음과 같습니다.

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL` 예외가 발생 하는 경우 올바른 오류 코드를 반환 합니다. `CATCH_ALL_DUAL` 인터페이스를 사용 하 여 MFC 예외를 OLE 자동화 오류 처리 정보로 변환 합니다 `ICreateErrorInfo` . 예를 들어 `CATCH_ALL_DUAL` 매크로는 있는 mfcdual.h 파일에 있습니다. . [ACDUAL](../overview/visual-cpp-samples.md) 샘플에서 H. 예외를 처리 하기 위해 호출 하는 함수는 `DualHandleException` 있는 mfcdual.h 파일에 있습니다. .CPP) `CATCH_ALL_DUAL` 발생 한 예외 유형에 따라 반환할 오류 코드를 결정 합니다.

- [Coledispatchexception](../mfc/reference/coledispatchexception-class.md) -이 경우 `HRESULT` 는 다음 코드를 사용 하 여 생성 됩니다.

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   이렇게 하면 `HRESULT` 예외를 발생 시킨 인터페이스에 대 한 특정가 만들어집니다. `HRESULT`표준 OLE 인터페이스에 대 한 시스템 정의와 충돌 하지 않도록 오류 코드는 0x200에 의해 오프셋 됩니다.

- [Cmemoryexception](../mfc/reference/cmemoryexception-class.md) -이 경우이 `E_OUTOFMEMORY` 반환 됩니다.

- 이 경우 다른 모든 예외가 `E_UNEXPECTED` 반환 됩니다.

OLE 자동화 오류 처리기가 사용 됨을 나타내려면 인터페이스도 구현 해야 합니다 `ISupportErrorInfo` .

먼저 자동화 클래스 정의에 코드를 추가 하 여 지원 하도록 표시 `ISupportErrorInfo` 합니다.

두 번째로, 자동화 클래스의 인터페이스 맵에 코드를 추가 하 여 `ISupportErrorInfo` 구현 클래스를 MFC의 `QueryInterface` 메커니즘과 연결 합니다. `INTERFACE_PART`문은에 대해 정의 된 클래스와 일치 합니다 `ISupportErrorInfo` .

마지막으로,를 지원 하도록 정의 된 클래스를 구현 `ISupportErrorInfo` 합니다.

( [ACDUAL](../overview/visual-cpp-samples.md) 샘플에는 `DECLARE_DUAL_ERRORINFO` `DUAL_ERRORINFO_PART` 있는 mfcdual.h에 포함 된 세 가지 단계,, 및를 수행 하는 데 도움이 되는 세 개의 매크로가 포함 되어 있습니다 `IMPLEMENT_DUAL_ERRORINFO` .)

다음 예제에서는을 지원 하도록 정의 된 클래스를 구현 합니다 `ISupportErrorInfo` . `CAutoClickDoc` 은 (는) automation 클래스의 이름이 고,는 `IID_IDualAClick` OLE automation error 개체를 통해 보고 되는 오류의 원본인 인터페이스에 대 한 **IID** 입니다.

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
