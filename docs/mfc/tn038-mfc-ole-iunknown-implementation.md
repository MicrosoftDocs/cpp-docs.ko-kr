---
description: 'TN038: MFC/OLE IUnknown 구현에 대해 자세히 알아보세요.'
title: 'TN038: MFC-OLE IUnknown 구현'
ms.date: 06/28/2018
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 64a921fec560c375440f0430d4804aa78e533c6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215406"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: MFC/OLE IUnknown 구현

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

OLE 2의 핵심에는 "OLE 구성 요소 개체 모델" 즉, COM이 있습니다. COM은 협동 개체가 서로 통신하는 방법에 대한 표준을 정의합니다. 여기에는 메서드가 개체에서 디스패치되는 방법을 포함하여 “개체"의 모양에 대한 세부 정보가 포함됩니다. 또한 COM은 모든 COM 호환 클래스가 파생되는 기본 클래스를 정의합니다. 이 기본 클래스는 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)입니다. [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 인터페이스는 c + + 클래스 라고 하지만 com은 한 언어에 국한 되지 않습니다. c, 파스칼 또는 com 개체의 이진 레이아웃을 지원할 수 있는 다른 언어로 구현할 수 있습니다.

OLE는 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 에서 파생 된 모든 클래스를 "인터페이스"로 나타냅니다. [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 과 같은 "인터페이스"는 구현과 함께 전달 되지 않으므로이는 중요 한 차이점입니다. 해당 구현에서 수행하는 구체적인 작업이 아니라 개체가 통신하는 데 필요한 프로토콜만 정의하면 됩니다. 따라서 최대 유연성을 허용하는 시스템에 적합합니다. MFC의 역할은 MFC/C++ 프로그램의 기본 동작을 구현하는 것입니다.

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 의 MFC 구현을 이해 하려면 먼저이 인터페이스를 이해 해야 합니다. [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 의 간소화 된 버전은 다음과 같이 정의 됩니다.

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> 과 같은 필요한 특정 호출 규칙 세부 정보 **`__stdcall`** 는이 그림에 대해 남아 있습니다.

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 멤버 함수는 개체의 메모리 관리를 제어 합니다. COM은 참조 개수 계산 스키마를 사용하여 개체를 추적합니다. C++에서처럼 개체가 직접 참조되지 않습니다. 대신 COM 개체는 항상 포인터를 통해 참조됩니다. 소유자가이 개체를 사용 하 여 작업을 완료할 때 개체를 해제 하려면 기존 c + + 개체에 대해 수행 되는 operator delete를 사용 하는 대신 개체의 [릴리스](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 멤버를 호출 합니다. 참조 개수 계산 메커니즘에서는 단일 개체에 대한 여러 참조를 관리할 수 있습니다. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 의 구현에서 개체에 대 한 참조 횟수를 유지 관리 합니다. 개체는 참조 횟수가 0에 도달할 때까지 삭제 되지 않습니다.

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 는 구현 관점에서 매우 간단 합니다. 다음은 간단한 구현입니다.

```cpp
ULONG CMyObj::AddRef()
{
    return ++m_dwRef;
}

ULONG CMyObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}
```

[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 멤버 함수는 좀 더 흥미롭습니다. 멤버 함수만 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 인 개체를 갖는 것은 매우 흥미롭습니다. 개체가 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 에서 제공 하는 것 보다 더 많은 작업을 수행 하도록 지시 하는 것이 좋습니다. 여기에는 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 가 유용 합니다. 동일한 개체에서 다른 "인터페이스"를 가져올 수 있습니다. 이러한 인터페이스는 일반적으로 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 에서 파생 되며 새 멤버 함수를 추가 하 여 추가 기능을 추가 합니다. COM 인터페이스는 인터페이스에 선언된 멤버 변수를 사용하지 않으며, 모든 멤버 함수가 pure-virtual로 선언됩니다. 예를 들면 다음과 같습니다.

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)만 있는 경우 IPrintInterface를 가져오려면의를 사용 하 여 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 를 호출 합니다 `IID` `IPrintInterface` . `IID`는 인터페이스를 고유하게 식별하는 128비트 숫자입니다. 사용자나 OLE에서 정의하는 각 인터페이스에 대해 `IID`가 있습니다. *PUnk* 가 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 개체에 대 한 포인터인 경우 iprintinterface를 검색 하는 코드는 다음과 같을 수 있습니다.

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

이는 매우 쉽지만 iprintinterface와 [iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 인터페이스를 모두 지 원하는 개체를 구현 하는 방법은 간단 합니다. IPrintInterface는 iprintinterface를 구현 하 여 iprintinterface를 구현 하면 [iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 이 자동으로 지원 됩니다. [](/windows/win32/api/unknwn/nn-unknwn-iunknown) 예를 들어:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 의 구현은 위에 구현 된 것과 정확 하 게 동일 합니다. `CPrintObj::QueryInterface` 다음과 같이 표시 됩니다.

```cpp
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}
```

IID(인터페이스 식별자)가 인식되면 포인터가 개체에 반환되고, 그렇지 않으면 오류가 발생합니다. 또한 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 가 성공적으로 수행 되 면 묵시적 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)이 발생 합니다. 물론 CEditObj::Print도 구현해야 합니다. IPrintInterface가 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 인터페이스에서 직접 파생 되었기 때문에 간단 합니다. 그러나 둘 다 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)에서 파생 된 두 가지 인터페이스를 지원 하려는 경우 다음 사항을 고려 하세요.

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

C++ 다중 상속 사용을 포함하여 다양한 방법으로 IEditInterface와 IPrintInterface를 모두 지원하는 클래스를 구현할 수 있지만 여기서는 중첩 클래스를 사용하여 이 기능을 구현하는 데 집중합니다.

```cpp
class CEditPrintObj
{
public:
    CEditPrintObj();

    HRESULT QueryInterface(REFIID iid, void**);
    ULONG AddRef();
    ULONG Release();
    DWORD m_dwRef;

    class CPrintObj : public IPrintInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_printObj;

    class CEditObj : public IEditInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_editObj;
};
```

다음은 전체 구현입니다.

```cpp
CEditPrintObj::CEditPrintObj()
{
    m_editObj.m_pParent = this;
    m_printObj.m_pParent = this;
}

ULONG CEditPrintObj::AddRef()
{
    return ++m_dwRef;
}

CEditPrintObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}

HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = &m_printObj;
        AddRef();
        return NOERROR;
    }
    else if (iid == IID_IEditInterface)
    {
        *ppvObj = &m_editObj;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

ULONG CEditPrintObj::CEditObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CEditObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}

ULONG CEditPrintObj::CPrintObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CPrintObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

대부분의 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 구현은 ceditprintobj:: ceditobj 및 ceditprintobj:: cprintobj의 코드를 복제 하는 대신 ceditprintobj 클래스에 배치 됩니다. 따라서 코드의 양을 줄이고 버그를 방지할 수 있습니다. 여기서의 핵심은 IUnknown 인터페이스에서 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 를 호출 하 여 개체가 지원할 수 있는 인터페이스를 검색할 수 있다는 점입니다. 이러한 각 인터페이스에서 동일한 작업을 수행할 수 있습니다. 즉, 각 인터페이스에서 사용할 수 있는 모든 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 함수는 정확히 동일한 방식으로 동작 해야 합니다. 이러한 포함된 개체가 "외부 개체"에서 구현을 호출할 수 있도록 하려면 후방 포인터(m_pParent)를 사용합니다. m_pParent 포인터는 CEditPrintObj 생성자 중 초기화됩니다. 그런 다음 CEditPrintObj::CPrintObj::PrintObject 및 CEditPrintObj::CEditObj::EditObject도 구현합니다. 개체를 편집하는 한 가지 기능을 추가하기 위해 약간의 코드가 추가되었습니다. 다행히 인터페이스에서 단일 멤버 함수만 사용하는 것은 매우 특수하지만 발생하는 경우이며, 이런 경우 EditObject 및 PrintObject가 일반적으로 단일 인터페이스로 결합됩니다.

따라서 이러한 간단한 시나리오에 대해서도 설명과 코드가 많습니다. MFC/OLE 클래스는 보다 간단한 대안을 제공합니다. MFC 구현에서는 Windows 메시지가 메시지 맵을 사용하여 래핑되는 방식과 유사한 기술을 사용합니다. 이 기능을 *인터페이스 맵* 이라고 하며 다음 섹션에서 설명 합니다.

## <a name="mfc-interface-maps"></a>MFC 인터페이스 맵

MFC/OLE에는 개념과 실행 측면에서 MFC의 "메시지 맵" 및 “디스패치 맵"과 유사한 “인터페이스 맵"의 구현이 포함됩니다. MFC 인터페이스 맵의 핵심 기능은 다음과 같습니다.

- 클래스에 기본 제공 되는 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)의 표준 구현입니다 `CCmdTarget` .

- [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 로 수정 된 참조 횟수의 유지 관리

- [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 의 데이터 기반 구현

또한 인터페이스 맵은 다음과 같은 고급 기능을 지원합니다.

- 집계할 수 있는 COM 개체 만들기 지원

- COM 개체의 구현에서 집계 개체 사용 지원

- 연결 및 확장 가능한 구현

집계에 대 한 자세한 내용은 [집계](/windows/win32/com/aggregation) 항목을 참조 하세요.

MFC의 인터페이스 맵 지원은 `CCmdTarget` 클래스를 기반으로 합니다. `CCmdTarget` "*있음*" 참조 수와 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 구현과 관련 된 모든 멤버 함수 (예를 들어 참조 횟수는에 있음 `CCmdTarget` ). OLE COM을 지원하는 클래스를 만들려면 `CCmdTarget`에서 클래스를 파생시키고 다양한 매크로 및 `CCmdTarget`의 멤버 함수를 사용하여 원하는 인터페이스를 구현합니다. MFC의 구현에서는 중첩 클래스를 사용하여 위의 예제와 매우 유사하게 각 인터페이스 구현을 정의합니다. IUnknown의 표준 구현 및 반복되는 코드 일부를 제거하는 다양한 매크로를 사용하면 더 간단해집니다.

## <a name="interface-map-basics"></a>인터페이스 맵 기본 사항

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>MFC의 인터페이스 맵을 사용하는 클래스를 구현하려면

1. `CCmdTarget`에서 직접적으로나 간접적으로 클래스를 파생시킵니다.

2. 파생 클래스 정의에서 `DECLARE_INTERFACE_MAP` 함수를 사용합니다.

3. 지원 하려는 각 인터페이스에 대해 BEGIN_INTERFACE_PART를 사용 하 고 클래스 정의에서 매크로를 END_INTERFACE_PART 합니다.

4. 구현 파일에서 BEGIN_INTERFACE_MAP 및 END_INTERFACE_MAP 매크로를 사용 하 여 클래스의 인터페이스 맵을 정의 합니다.

5. 지원 되는 각 IID에 대해 BEGIN_INTERFACE_MAP와 END_INTERFACE_MAP 매크로 사이에 INTERFACE_PART 매크로를 사용 하 여 해당 IID를 클래스의 특정 "파트"에 매핑합니다.

6. 지원하는 인터페이스를 나타내는 각 중첩 클래스를 구현합니다.

7. METHOD_PROLOGUE 매크로를 사용 하 여 부모, `CCmdTarget` 파생 개체에 액세스 합니다.

8. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)및 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 는 `CCmdTarget` 이러한 함수 ( `ExternalAddRef` , 및)의 구현에 위임할 수 있습니다 `ExternalRelease` `ExternalQueryInterface` .

위의 CPrintEditObj 예제는 다음과 같이 구현할 수 있습니다.

```cpp
class CPrintEditObj : public CCmdTarget
{
public:
    // member data and member functions for CPrintEditObj go here

// Interface Maps
protected:
    DECLARE_INTERFACE_MAP()

    BEGIN_INTERFACE_PART(EditObj, IEditInterface)
        STDMETHOD_(void, EditObject)();
    END_INTERFACE_PART(EditObj)

    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)
        STDMETHOD_(void, PrintObject)();
    END_INTERFACE_PART(PrintObj)
};
```

위의 선언은 `CCmdTarget`에서 파생 클래스를 만듭니다. DECLARE_INTERFACE_MAP 매크로는이 클래스에 사용자 지정 인터페이스 맵이 있음을 프레임 워크에 알립니다. 또한 BEGIN_INTERFACE_PART 및 END_INTERFACE_PART 매크로는 중첩 클래스 (이 경우 CEditObj 및 Ceditobj)를 정의 합니다. X는 "C"로 시작 하는 전역 클래스와 "I"로 시작 하는 인터페이스 클래스에서 중첩 된 클래스를 구분 하는 데만 사용 됩니다. 이러한 클래스의 두 중첩 멤버, 각각 m_CEditObj와 m_CPrintObj가 만들어집니다. 매크로는 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)및 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 함수를 자동으로 선언 합니다. 따라서이 인터페이스와 관련 된 함수만 선언 합니다. EditObject 및 PrintObject (OLE 매크로 STDMETHOD를 사용 하 여 대상 플랫폼에 적절 한 **_stdcall** 및 가상 키워드를 제공 합니다.

이 클래스에 대해 인터페이스 맵을 구현하려면

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

각각 IID_IPrintInterface IID는 m_CPrintObj와 연결하고 IID_IEditInterface는 m_CEditObj와 연결합니다. `CCmdTarget` [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ()의 구현은 `CCmdTarget::ExternalQueryInterface` 이 맵을 사용 하 여 m_CPrintObj에 대 한 포인터를 반환 하 고 요청 시 m_CEditObj 합니다. `IID_IUnknown`에 대한 항목은 포함할 필요가 없습니다. `IID_IUnknown`을 요청하는 경우 프레임워크는 맵의 첫 번째 인터페이스(이 경우 m_CPrintObj)를 사용합니다.

BEGIN_INTERFACE_PART 매크로가 자동으로 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 및 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 함수를 선언 했더라도 이러한 함수를 구현 해야 합니다.

```cpp
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalAddRef();
}

ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalRelease();
}

HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);
}

void FAR EXPORT CEditPrintObj::XEditObj::EditObject()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    // code to "Edit" the object, whatever that means...
}
```

CEditPrintObj::CPrintObj에 대한 구현은 CEditPrintObj::CEditObj에 대한 위의 정의와 유사합니다. 이러한 함수를 자동으로 생성하는 데 사용할 수 있는 매크로를 만들 수 있었지만(MFC/OLE 개발 초기에 해당) 매크로에서 두 줄 이상의 코드를 생성하는 경우 중단점을 설정하기가 어려워집니다. 따라서 이 코드를 수동으로 확장합니다.

메시지 맵의 프레임워크 구현을 사용하면 다음과 같은 많은 작업을 수행할 필요가 없습니다.

- QueryInterface 구현

- AddRef 및 Release 구현

- 두 인터페이스 모두에서 이러한 기본 제공 메서드 중 하나 선언

또한 프레임워크는 메시지 맵을 내부적으로 사용합니다. 따라서 이미 특정 인터페이스를 지원하고 프레임워크에서 제공하는 인터페이스에 대체 또는 추가 작업을 제공하는 프레임워크 클래스 `COleServerDoc`에서 파생시킬 수 있습니다. 프레임워크는 기본 클래스에서 인터페이스 맵 상속을 완벽하게 지원하기 때문에 가능합니다. 이것은 BEGIN_INTERFACE_MAP가 기본 클래스의 이름을 두 번째 매개 변수로 사용 하는 이유입니다.

> [!NOTE]
> 일반적으로 MFC 버전에서 해당 인터페이스의 포함된 특수화를 상속하는 것만으로는 MFC의 OLE 인터페이스 기본 제공 구현의 구현을 다시 사용할 수 없습니다. 이는 METHOD_PROLOGUE 매크로를 사용 하 여 포함 된 파생 개체에 대 한 액세스 권한을 얻는 것이 `CCmdTarget` 파생 개체에서 포함 된 개체의 *고정 오프셋* 을 의미 하기 때문에 불가능 합니다 `CCmdTarget` . 예를 들어 `COleClientItem::XAdviseSink`의 MFC 구현에서 포함된 XMyAdviseSink를 파생시킬 수 없는데, XAdviseSink는 `COleClientItem` 개체의 맨 위로부터 특정 오프셋에 있기 때문입니다.

> [!NOTE]
> 그러나 MFC의 기본 동작을 원하는 모든 함수에 대한 MFC 구현에 위임할 수 있습니다. 이 작업은 `COleFrameHook` 클래스(많은 함수에서 m_xOleInPlaceUIWindow에 위임)에서 `IOleInPlaceFrame`(XOleInPlaceFrame)의 MFC 구현으로 수행합니다. 이 디자인은 여러 인터페이스를 구현하는 개체의 런타임 크기를 줄이기 위해 선택되었으며, 이전 섹션에서 사용된 m_pParent 같은 후방 포인터가 필요하지 않습니다.

### <a name="aggregation-and-interface-maps"></a>집계 및 인터페이스 맵

MFC는 독립 실행형 COM 개체뿐만 아니라 집계도 지원합니다. 집계 자체는 여기에 설명 하기에 너무 복잡 한 주제입니다. 집계에 대 한 자세한 내용은 [집계](/windows/win32/com/aggregation) 항목을 참조 하세요. 여기서는 프레임워크 및 인터페이스 맵에 기본 제공되는 집계에 대한 지원에 대해 간략하게 설명합니다.

집계는 (1) 집계를 지원하는 COM 개체 사용, (2) 다른 개체에서 집계할 수 있는 개체 구현과 같은 두 가지 방법으로 사용할 수 있습니다. 이러한 기능을 "집계 개체 사용" 및 “개체를 집계할 수 있도록 만들기"라고 합니다. MFC는 둘 다를 지원합니다.

### <a name="using-an-aggregate-object"></a>집계 개체 사용

집계 개체를 사용하려면 집계를 QueryInterface 메커니즘에 연결할 수 있는 몇 가지 방법이 있어야 합니다. 즉, 집계 개체는 개체의 네이티브 요소인 것처럼 동작해야 합니다. 이렇게 하면 중첩 된 개체가 IID에 매핑되는 INTERFACE_PART 매크로 외에도이를 MFC의 인터페이스 맵 메커니즘에 연결 하는 방법이 파생 클래스의 일부로 집계 개체를 선언할 수 있습니다 `CCmdTarget` . 이렇게 하려면 INTERFACE_AGGREGATE 매크로가 사용 됩니다. 이를 통해 인터페이스 맵 메커니즘에 통합 될 멤버 변수 ( [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 또는 파생 클래스에 대 한 포인터 여야 함)를 지정할 수 있습니다. `CCmdTarget::ExternalQueryInterface`가 호출 될 때 포인터가 NULL이 아닌 경우 프레임워크는 집계 개체의 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 멤버함수를 자동으로 호출하고, .요청된 `IID`가 `CCmdTarget`개체 자체에 의해 지원되는 네이티브 `IID`중 하나가 아닌 경우.

#### <a name="to-use-the-interface_aggregate-macro"></a>INTERFACE_AGGREGATE 매크로를 사용하려면

1. 집계 개체에 대한 포인터를 포함할 멤버 변수(`IUnknown*`)를 선언합니다.

2. 이름으로 멤버 변수를 참조 하는 인터페이스 맵에 INTERFACE_AGGREGATE 매크로를 포함 합니다.

3. 특정 지점(일반적으로 `CCmdTarget::OnCreateAggregates` 중)에서 멤버 변수를 NULL이 아닌 다른 값으로 초기화합니다.

예를 들어:

```cpp
class CAggrExample : public CCmdTarget
{
public:
    CAggrExample();

protected:
    LPUNKNOWN m_lpAggrInner;
    virtual BOOL OnCreateAggregates();

    DECLARE_INTERFACE_MAP()
    // "native" interface part macros may be used here
};

CAggrExample::CAggrExample()
{
    m_lpAggrInner = NULL;
}

BOOL CAggrExample::OnCreateAggregates()
{
    // wire up aggregate with correct controlling unknown
    m_lpAggrInner = CoCreateInstance(CLSID_Example,
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)
        return FALSE;
    // optionally, create other aggregate objects here
    return TRUE;
}

BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)
    // native "INTERFACE_PART" entries go here
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)
END_INTERFACE_MAP()
```

m_lpAggrInner 변수는 생성자에서 NULL로 초기화됩니다. 프레임 워크는 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))의 기본 구현에서 NULL 멤버 변수를 무시 합니다. `OnCreateAggregates`는 실제로 집계 개체를 만들 수 있는 좋은 위치입니다. `COleObjectFactory`의 MFC 구현 외부에서 개체를 만드는 경우 명시적으로 호출해야 합니다. `CCmdTarget::GetControllingUnknown`의 사용뿐만 아니라 `CCmdTarget::OnCreateAggregates`에서 집계를 만드는 이유는 집계할 수 있는 개체 만들기에 대해 설명할 때 명확해집니다.

이 기술은 집계 개체가 지원하는 모든 인터페이스와 네이티브 인터페이스에 개체에 제공합니다. 집계에서 지원하는 인터페이스의 하위 집합만 원하는 경우 `CCmdTarget::GetInterfaceHook`을 재정의할 수 있습니다. 이를 통해 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))와 유사한 매우 낮은 수준의 hookability를 사용할 수 있습니다. 일반적으로 집계에서 지원하는 모든 인터페이스를 원합니다.

### <a name="making-an-object-implementation-aggregatable"></a>개체 구현을 집계할 수 있도록 만들기

집계할 수 있는 개체의 경우 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)및 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 의 구현은 "제어 알 수 없음"에 위임 해야 합니다. 즉, 개체의 일부가 되려면 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)및 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 를 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)에서 파생 된 다른 개체에 위임 해야 합니다. 이 "제어 알 수 없음"은 개체가 생성될 때 개체에 제공됩니다. 즉, `COleObjectFactory`의 구현에 제공됩니다. 이 구현에는 약간의 오버헤드가 수반되므로 경우에 따라 바람직하지 않으므로 MFC에서는 선택 사항으로 만듭니다. 개체를 집계할 수 있도록 하려면 개체의 생성자에서 `CCmdTarget::EnableAggregation`을 호출합니다.

개체도 집계를 사용하는 경우 올바른 “제어 알 수 없음"을 집계 개체에도 전달해야 합니다. 일반적으로이 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 포인터는 집계가 생성 될 때 개체에 전달 됩니다. 예를 들어 pUnkOuter 매개 변수는 `CoCreateInstance`를 사용하여 만든 개체에 대한 “제어 알 수 없음"입니다. 올바른 “제어 알 수 없음" 포인터는 `CCmdTarget::GetControllingUnknown`을 호출하여 검색할 수 있습니다. 그러나 해당 함수에서 반환된 값은 생성자 중 올바르지 않습니다. 따라서 `CCmdTarget::OnCreateAggregates`의 재정의에서만 집계를 만드는 것이 좋습니다. 여기서 `GetControllingUnknown`의 반환 값은 `COleObjectFactory` 구현에서 만들어진 경우에도 신뢰할 수 있습니다.

또한 개체는 인공 참조 개수를 추가하거나 해제하는 경우 올바른 참조 개수를 조작해야 합니다. 이렇게 하려면 항상 `InternalRelease` 및 `InternalAddRef` 대신 `ExternalAddRef` 및 `ExternalRelease`를 호출합니다. 집계를 지원하는 클래스에서는 `InternalRelease` 또는 `InternalAddRef`를 거의 호출하지 않습니다.

## <a name="reference-material"></a>참조 자료

고유한 인터페이스 정의 또는 프레임워크의 OLE 인터페이스 구현 재정의 같은 고급 OLE 사용에서는 기본 인터페이스 맵 메커니즘을 사용해야 합니다.

이 섹션에서는 이러한 고급 기능을 구현하는 데 사용되는 각 매크로 및 API에 대해 설명합니다.

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation — 함수 설명

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>설명

이 형식의 개체에 대해 OLE 집계를 지원하려면 파생 클래스의 생성자에서 이 함수를 호출합니다. 이 함수는 집계할 수 있는 개체에 필요한 특수 IUnknown 구현을 준비합니다.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface — 함수 설명

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>매개 변수

*lpIID*<br/>
IID(QueryInterface 첫 번째 인수)에 대한 far 포인터

*ppvObj*<br/>
IUnknown*(QueryInterface의 두 번째 인수)에 대한 포인터

#### <a name="remarks"></a>설명

클래스가 구현하는 각 인터페이스에 대해 IUnknown 구현에서 이 함수를 호출합니다. 이 함수는 개체의 인터페이스 맵에 기반을 둔 QueryInterface의 표준 데이터 기반 구현을 제공합니다. 반환 값을 HRESULT에 캐스팅해야 합니다. 개체가 집계되는 경우 이 함수는 로컬 인터페이스 맵을 사용하는 대신 "controlling IUnknown"을 호출합니다.

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef — 함수 설명

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>설명

클래스가 구현하는 각 인터페이스에 대해 IUnknown::AddRef 구현에서 이 함수를 호출합니다. 반환 값은 CCmdTarget 개체에 대한 새 참조 개수입니다. 개체가 집계되는 경우 이 함수는 로컬 참조 개수를 조작하는 대신 "controlling IUnknown"을 호출합니다.

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease — 함수 설명

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>설명

클래스가 구현하는 각 인터페이스에 대해 IUnknown::Release 구현에서 이 함수를 호출합니다. 반환 값은 개체에 대한 새 참조 개수를 나타냅니다. 개체가 집계되는 경우 이 함수는 로컬 참조 개수를 조작하는 대신 "controlling IUnknown"을 호출합니다.

### <a name="declare_interface_map--macro-description"></a>DECLARE_INTERFACE_MAP — 매크로 설명

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>설명

이 매크로는 인터페이스 맵이 포함될 `CCmdTarget`에서 파생 클래스에서 사용합니다. DECLARE_MESSAGE_MAP와 거의 동일한 방식으로 사용 됩니다. 이 매크로 호출은 일반적으로 헤더(.H) 파일에 있는 클래스 정의에 배치해야 합니다. DECLARE_INTERFACE_MAP 있는 클래스는 구현 파일 ()에서 인터페이스 맵을 정의 해야 합니다. CPP)를 사용 하 여 BEGIN_INTERFACE_MAP 및 END_INTERFACE_MAP 매크로를 사용 합니다.

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>BEGIN_INTERFACE_PART 및 END_INTERFACE_PART — 매크로 설명

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>매개 변수

*localClass*<br/>
인터페이스를 구현하는 클래스의 이름

*iface*<br/>
이 클래스에서 구현하는 인터페이스의 이름

#### <a name="remarks"></a>설명

클래스가 구현 하는 각 인터페이스에 대해 BEGIN_INTERFACE_PART 및 END_INTERFACE_PART 쌍이 있어야 합니다. 이러한 매크로는 정의하는 OLE 인터페이스에서 파생된 로컬 클래스뿐만 아니라 해당 클래스의 포함된 멤버 변수를 정의합니다. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)및 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 멤버는 자동으로 선언 됩니다. 구현 되는 인터페이스의 일부인 다른 멤버 함수에 대 한 선언을 포함 해야 합니다. 이러한 선언은 BEGIN_INTERFACE_PART와 END_INTERFACE_PART 매크로 사이에 배치 됩니다.

*Iface* 인수는 `IAdviseSink` , 또는 `IPersistStorage` 사용자 지정 인터페이스와 같이 구현 하려는 OLE 인터페이스입니다.

*Localclass* 인수는 정의 되는 로컬 클래스의 이름입니다. 'X'는 이름 앞에 자동으로 추가됩니다. 이 명명 규칙은 이름이 동일한 전역 클래스와의 충돌을 방지하는 데 사용됩니다. 또한 포함 된 멤버의 이름에는 ' m_x ' 접두사가 접두사로 붙은 *Localclass* 이름과 동일 합니다.

예를 들어:

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

IAdviseSink에서 파생된 XMyAdviseSink라는 로컬 클래스와 이 로컬 클래스가 선언되는 클래스의 멤버인 m_xMyAdviseSink.Note를 정의합니다.

> [!NOTE]
> _로 시작 하는 줄은 `STDMETHOD` 기본적으로 OLE2에서 복사 됩니다. H 및가 약간 수정 되었습니다. OLE2에서 복사하면 해결하기 어려운 오류를 줄일 수 있습니다.

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>BEGIN_INTERFACE_MAP 및 END_INTERFACE_MAP — 매크로 설명

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>매개 변수

*theClass*<br/>
인터페이스 맵을 정의할 클래스

*baseClass*<br/>
*Theclass* 가 파생 되는 클래스입니다.

#### <a name="remarks"></a>설명

BEGIN_INTERFACE_MAP 및 END_INTERFACE_MAP 매크로는 구현 파일에서 실제로 인터페이스 맵을 정의 하는 데 사용 됩니다. 구현 된 각 인터페이스에 대해 하나 이상의 INTERFACE_PART 매크로 호출이 있습니다. 클래스에서 사용 하는 각 집계에 대해 하나의 매크로 호출 INTERFACE_AGGREGATE 있습니다.

### <a name="interface_part--macro-description"></a>INTERFACE_PART — 매크로 설명

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>매개 변수

*theClass*<br/>
인터페이스 맵을 포함하는 클래스의 이름

*iid*<br/>
포함된 클래스에 매핑될 `IID`

*localClass*<br/>
로컬 클래스의 이름('X' 제외)

#### <a name="remarks"></a>설명

이 매크로는 BEGIN_INTERFACE_MAP 매크로와 개체가 지 원하는 각 인터페이스에 대 한 END_INTERFACE_MAP 매크로 사이에 사용 됩니다. 이를 통해 IID를 *Theclass* 및 *localclass* 로 표시 되는 클래스의 멤버에 매핑할 수 있습니다. ' M_x '는 *Localclass* 에 자동으로 추가 됩니다. 단일 멤버에 둘 이상의 `IID`를 연결할 수 있습니다. 이 기능은 "최다 파생" 인터페이스만 구현하고 모든 중간 인터페이스도 제공하려는 경우에 매우 유용합니다. 좋은 예로 `IOleInPlaceFrameWindow` 인터페이스가 있습니다. 해당 계층 구조는 다음과 같습니다.

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

개체가를 구현 하는 경우 `IOleInPlaceFrameWindow` 클라이언트는 `QueryInterface` `IOleUIWindow` `IOleWindow` "가장 많이 파생 된" 인터페이스 [](/windows/win32/api/unknwn/nn-unknwn-iunknown) `IOleInPlaceFrameWindow` (실제로 구현 하는 인터페이스) 외에, 또는 IUnknown 인터페이스 중 하나에 있을 수 있습니다. 이를 처리 하기 위해 두 개 이상의 INTERFACE_PART 매크로를 사용 하 여 각 및 모든 기본 인터페이스를 인터페이스에 매핑할 수 있습니다 `IOleInPlaceFrameWindow` .

클래스 정의 파일:

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

클래스 구현 파일:

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

프레임워크는 항상 필요한 IUnknown을 관리합니다.

### <a name="interface_part--macro-description"></a>INTERFACE_PART — 매크로 설명

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>매개 변수

*theClass*<br/>
인터페이스 맵을 포함하는 클래스의 이름

*theAggr*<br/>
집계될 멤버 변수의 이름

#### <a name="remarks"></a>설명

이 매크로는 클래스에서 집계 개체를 사용하고 있음을 프레임워크에 알리는 데 사용됩니다. BEGIN_INTERFACE_PART와 END_INTERFACE_PART 매크로 사이에 나타나야 합니다. 집계 개체는 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)에서 파생 된 별도의 개체입니다. 집계 및 INTERFACE_AGGREGATE 매크로를 사용 하 여 집계에서 지 원하는 모든 인터페이스가 개체에서 직접 지원 되는 것으로 표시 되도록 할 수 있습니다. *TheAggr* 인수는 단순히 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 에서 (직접 또는 간접적으로) 파생 된 클래스의 멤버 변수 이름입니다. 모든 INTERFACE_AGGREGATE 매크로는 인터페이스 맵에 배치 될 때 INTERFACE_PART 매크로를 따라야 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
