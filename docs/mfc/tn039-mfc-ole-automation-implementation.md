---
description: 'TN039: MFC/OLE 자동화 구현에 대해 자세히 알아보세요.'
title: 'TN039: MFC-OLE 자동화 구현'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
ms.openlocfilehash: caabd3719a467e534e47ca61ed8f9a9f1f0d2eb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215419"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039: MFC/OLE 자동화 구현

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

## <a name="overview-of-ole-idispatch-interface"></a>OLE IDispatch 인터페이스 개요

`IDispatch`인터페이스는 VISUAL BASIC 등의 다른 응용 프로그램에서 응용 프로그램의 기능을 활용할 수 있도록 응용 프로그램에서 메서드 및 속성을 노출 하는 방법입니다. 이 인터페이스의 가장 중요 한 부분은 `IDispatch::Invoke` 함수입니다. MFC는 "디스패치 맵"을 사용 하 여를 구현 `IDispatch::Invoke` 합니다. 디스패치 맵은 `CCmdTarget` 개체의 속성을 직접 조작 하거나 개체 내에서 멤버 함수를 호출 하 여 요청을 처리할 수 있도록 파생 클래스의 레이아웃 또는 "모양"에 대 한 MFC 구현 정보를 제공 합니다 `IDispatch::Invoke` .

대부분의 경우 클래스 마법사와 MFC는 응용 프로그램 프로그래머의 OLE 자동화에 대 한 대부분의 세부 정보를 숨깁니다. 프로그래머는 응용 프로그램에서 노출 하는 실제 기능을 집중적으로 소개 하 고 내부에 대해 걱정 하지 않아도 됩니다.

그러나 MFC가 백그라운드에서 수행 하는 작업을 이해 해야 하는 경우도 있습니다. 이 메모는 프레임 워크가 멤버 함수 및 속성에 **DISPID** 를 할당 하는 방법을 설명 합니다. MFC에서 **DISPID** 를 할당 하는 데 사용 하는 알고리즘에 대 한 지식은 응용 프로그램의 개체에 대 한 "형식 라이브러리"를 만들 때와 같이 id를 알아야 하는 경우에만 필요 합니다.

## <a name="mfc-dispid-assignment"></a>MFC DISPID 할당

자동화의 최종 사용자 (예: Visual Basic 사용자)는 코드에서 자동화가 설정 된 속성 및 메서드의 실제 이름을 표시 합니다 (예: obj). ShowWindow)의 구현은 `IDispatch::Invoke` 실제 이름을 받지 않습니다. 최적화를 위해이 속성은 액세스할 메서드나 속성을 설명 하는 32 비트 "매직 cookie" 인 **DISPID** 를 수신 합니다. 이러한 **DISPID** 값은 `IDispatch` 라는 다른 메서드를 통해 구현에서 반환 됩니다 `IDispatch::GetIDsOfNames` . 자동화 클라이언트 응용 프로그램은 `GetIDsOfNames` 액세스 하려는 각 멤버나 속성에 대해 한 번 호출 하 고 나중에에 대 한 호출을 위해 캐시 `IDispatch::Invoke` 합니다. 이러한 방식으로 비용이 많이 드는 문자열 조회는 각 호출에 한 번이 아니라 개체 사용 당 한 번만 수행 됩니다 `IDispatch::Invoke` .

MFC는 다음 두 가지를 기준으로 각 메서드와 속성에 대 한 **DISPID** 를 결정 합니다.

- 디스패치 지도의 위쪽에서의 거리입니다 (상대 1 개).

- 가장 많이 파생 된 클래스에서 디스패치 맵의 거리 (0 상대)입니다.

**DISPID** 는 두 부분으로 나뉩니다. **DISPID** 의 **loword** 에는 첫 번째 구성 요소, 디스패치 지도의 위쪽 으로부터의 거리가 포함 됩니다. 이 **단어** 는 가장 많이 파생 된 클래스의 거리를 포함 합니다. 예를 들어:

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

여기에서 볼 수 있듯이 두 가지 클래스가 있습니다. 둘 다 OLE 자동화 인터페이스를 노출 합니다. 이러한 클래스 중 하나는 다른 클래스에서 파생 되므로 OLE 자동화 부분 (이 경우 "x" 및 "y" 속성 포함)을 포함 하 여 기본 클래스의 기능을 활용 합니다.

MFC는 다음과 같이 CDispPoint 클래스에 대 한 **DISPID** s를 생성 합니다.

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

속성은 기본 클래스에 없기 때문에 **DISPID** 의 기본 **단어** 는 항상 0입니다. 즉, CDispPoint에 대해 가장 많이 파생 된 클래스의 거리가 0입니다.

MFC는 다음과 같이 CDisp3DPoint 클래스에 대 한 **DISPID** s를 생성 합니다.

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Z 속성에는 CDisp3DPoint 속성을 노출 하는 클래스에 정의 되어 있으므로 0으로 지정 된 **단어가** 있는 **DISPID** 가 제공 됩니다. X 및 Y 속성은 기본 클래스에서 정의 되기 때문에이 속성을 정의 하는 클래스가 가장 많이 파생 된 클래스에서 파생 되는 거리에 있기 때문에 **DISPID** 의 다른 **단어** 는 1입니다.

> [!NOTE]
> 지도에 명시적 **DISPID** 가 있는 항목이 있는 경우에도 **loword** 는 항상 지도의 위치에 의해 결정 됩니다 ( **_ID** 버전의 및 매크로에 대 한 자세한 내용은 다음 섹션 참조 `DISP_PROPERTY` `DISP_FUNCTION` ).

## <a name="advanced-mfc-dispatch-map-features"></a>고급 MFC 디스패치 맵 기능

이 Visual C++ 릴리스에서는 클래스 마법사가 지원 하지 않는 추가 기능이 많이 있습니다. 클래스 마법사 `DISP_FUNCTION` 는 `DISP_PROPERTY` `DISP_PROPERTY_EX` 메서드, 멤버 변수 속성 및 get/set 멤버 함수 속성을 각각 정의 하는, 및를 지원 합니다. 이러한 기능은 일반적으로 대부분의 자동화 서버를 만드는 데 필요 합니다.

클래스 마법사에서 지원 되는 매크로가 적절 하지 않은 경우 다음과 같은 추가 매크로를 사용할 수 있습니다. `DISP_PROPERTY_NOTIFY` 및 `DISP_PROPERTY_PARAM` .

## <a name="disp_property_notify--macro-description"></a>DISP_PROPERTY_NOTIFY — 매크로 설명

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*pszName*<br/>
속성의 외부 이름입니다.

*memberName*<br/>
속성이 저장 된 멤버 변수의 이름입니다.

*pfnAfterSet*<br/>
속성이 변경 될 때 호출할 멤버 함수의 이름입니다.

*vtPropType*<br/>
속성의 형식을 지정 하는 값입니다.

### <a name="remarks"></a>설명

이 매크로는 추가 인수를 허용 한다는 점을 제외 하 고 DISP_PROPERTY와 매우 비슷합니다. 추가 인수인 *pfnAfterSet* 은 아무 것도 반환 하지 않고 ' Void OnPropertyNotify () ' 매개 변수를 사용 하지 않는 멤버 함수 여야 합니다. 멤버 변수가 수정 된 **후** 에 호출 됩니다.

## <a name="disp_property_param--macro-description"></a>DISP_PROPERTY_PARAM — 매크로 설명

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
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

*vtsParams*<br/>
각 매개 변수에 대해 VTS_ 공백으로 구분 된 문자열입니다.

### <a name="remarks"></a>설명

DISP_PROPERTY_EX 매크로와 매우 유사 하 게이 매크로는 별도의 Get 및 Set 멤버 함수를 사용 하 여 액세스 되는 속성을 정의 합니다. 그러나이 매크로를 사용 하면 속성에 대 한 매개 변수 목록을 지정할 수 있습니다. 이는 다른 방식으로 인덱싱되는 속성 또는 매개 변수화 된 속성을 구현 하는 데 유용 합니다. 매개 변수는 항상 먼저 배치 된 다음 속성의 새 값이 됩니다. 예를 들어:

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

는 멤버 함수 가져오기 및 설정에 해당 합니다.

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="disp_xxxx_id--macro-descriptions"></a>DISP_XXXX_ID — 매크로 설명

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
클래스의 이름입니다.

*pszName*<br/>
속성의 외부 이름입니다.

*dispid*<br/>
속성 또는 메서드에 대 한 고정 DISPID입니다.

*pfnGet*<br/>
속성을 가져오는 데 사용 되는 멤버 함수의 이름입니다.

*pfnSet*<br/>
속성을 설정 하는 데 사용 되는 멤버 함수의 이름입니다.

*memberName*<br/>
속성에 매핑할 멤버 변수의 이름입니다.

*vtPropType*<br/>
속성의 형식을 지정 하는 값입니다.

*vtsParams*<br/>
각 매개 변수에 대해 VTS_ 공백으로 구분 된 문자열입니다.

### <a name="remarks"></a>설명

이러한 매크로를 사용 하면 MFC에서 자동으로 하나를 할당 하는 대신 **DISPID** 를 지정할 수 있습니다. 이러한 고급 매크로는 이름이 매크로 이름에 추가 된다는 점을 제외 하 고 (예: **DISP_PROPERTY_ID**) id가 같으며 *pszName* 매개 변수 바로 뒤에 지정 된 매개 변수에 의해 id가 결정 됩니다. AFXDISP.H를 참조 하세요. 이러한 매크로에 대 한 자세한 내용은 H. **_ID** 항목은 디스패치 맵의 끝에 배치 해야 합니다. 자동 Dispid 생성에 영향을 주는 것과 같은 **_ID** 방법으로 자동 **dispid** 생성에 영향을 줍니다. 즉, **dispid** 는 위치에 따라 결정 됩니다. 예를 들어:

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC는 다음과 같이 CDisp3DPoint 클래스에 대 한 Dispid를 생성 합니다.

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

고정 **DISPID** 를 지정 하는 것은 이전에 기존 디스패치 인터페이스와의 호환성을 유지 하거나 특정 시스템 정의 메서드 또는 속성을 구현 하는 데 유용 합니다 (일반적으로 **DISPID_NEWENUM** 컬렉션과 같이 음수 **DISPID** 로 표시 됨).

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>COleClientItem에 대 한 IDispatch 인터페이스를 검색 하는 중

많은 서버는 OLE 서버 기능과 함께 문서 개체 내에서 자동화를 지원 합니다. 이 자동화 인터페이스에 대 한 액세스 권한을 얻으려면 멤버 변수에 직접 액세스 해야 `COleClientItem::m_lpObject` 합니다. 아래 코드에서는 `IDispatch` 에서 파생 된 개체에 대 한 인터페이스를 검색 `COleClientItem` 합니다. 이 기능이 필요한 경우 응용 프로그램에 아래 코드를 포함할 수 있습니다.

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

이 함수에서 반환 된 디스패치 인터페이스는 형식이 안전한 액세스를 위해 직접 사용 하거나에 연결할 수 있습니다 `COleDispatchDriver` . 이를 직접 사용 하는 경우 포인터를 사용 하 여를 호출할 때 해당 멤버를 호출 해야 합니다 `Release` `COleDispatchDriver` . 소멸자는 기본적으로이 작업을 수행 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
