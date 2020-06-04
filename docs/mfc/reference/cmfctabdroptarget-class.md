---
title: CMFCTabDropTarget 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367351"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 클래스

탭 컨트롤과 OLE 라이브러리 간의 통신 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|||
|-|-|
|속성|Description|
|`CMFCTabDropTarget::CMFCTabDropTarget`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|||
|-|-|
|속성|Description|
|[CMFC탭드롭타겟::온드래그엔터](#ondragenter)|사용자가 개체를 탭 창으로 드래그할 때 프레임워크에서 호출합니다. (오버라이드 [콜레드롭타겟::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFC탭드롭타겟::온드래그리브](#ondragleave)|사용자가 포커스가 있는 탭 창 외부로 개체를 끌 때 프레임워크에서 호출됩니다. (오버라이드 [콜레드롭타겟::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFC탭드롭타겟::온드래그오버](#ondragover)|사용자가 포커스가 있는 탭 창에 개체를 드래그할 때 프레임워크에서 호출됩니다. (오버라이드 [콜레드롭Target::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFC탭드롭타겟::온드롭엑스](#ondropex)|사용자가 끌기 작업이 끝날 때 마우스 단추를 해제할 때 프레임워크에서 호출됩니다. (오버라이드 [COleDropTarget::OnDropEx.)](../../mfc/reference/coledroptarget-class.md#ondropex)|
|[CMFC탭드롭대상::레지스터](#register)|컨트롤을 OLE 끌어서 놓기 작업의 대상이 될 수 있는 컨트롤으로 등록합니다.|

### <a name="remarks"></a>설명

이 클래스는 `CMFCBaseTabCtrl` 클래스에 끌어서 놓기 지원을 제공합니다. 응용 프로그램이 [AfxOleInit](ole-initialization.md#afxoleinit) 함수를 사용하여 OLE 라이브러리를 `CMFCBaseTabCtrl` 초기화하는 경우 개체는 끌어서 놓기 작업에 자신을 등록합니다.

클래스는 `CMFCTabDropTarget` 끌기 작업이 활성화될 때 커서 아래에 있는 탭을 만들어 기본 클래스를 확장합니다. 끌어서 놓기 작업에 대한 자세한 내용은 [OLE 드래그 앤 드롭](../../mfc/drag-and-drop-ole.md)을 참조하십시오.

## <a name="example"></a>예제

다음 예제에서는 `CMFCTabDropTarget` 개체를 생성하고 해당 `Register` 메서드를 사용하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFC탭드롭타겟](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFC탭드롭타겟::온드래그엔터

사용자가 개체를 탭 창으로 드래그할 때 프레임워크에서 호출합니다.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

|||
|-|-|
|매개 변수|설명|
|*pWnd*|【인】 하지 않는.|
|*pDataObject*|【인】 사용자가 드래그하는 개체에 대한 포인터입니다.|
|*dwKeyState*|【인】 수정자 키의 상태를 포함합니다. 이는 MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON 여러 가지 조합입니다.|
|*지점*|【인】 클라이언트 좌표에서 커서의 위치입니다.|

### <a name="return-value"></a>Return Value

*점에*의해 지정된 위치에서 드롭이 발생하는 경우 발생하는 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>설명

이 메서드는 도구 모음 프레임워크가 사용자 지정 모드에 없거나 Clipboard 데이터 형식을 사용할 수 없는 경우 DROPEFFECT_NONE 반환합니다. 그렇지 않으면 제공된 매개 `CMFCBaseTabCtrl::OnDragEnter` 변수를 호출한 결과를 반환합니다.

사용자 지정 모드에 대한 자세한 내용은 [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)을 참조하십시오. 클립보드 데이터 형식에 대한 자세한 내용은 [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)을 참조하십시오.

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFC탭드롭타겟::온드래그리브

사용자가 포커스가 있는 탭 창 외부로 개체를 끌 때 프레임워크에서 호출됩니다.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

|||
|-|-|
|매개 변수|설명|
|*pWnd*|【인】 하지 않는.|

### <a name="remarks"></a>설명

이 메서드는 `CMFCBaseTabCtrl::OnDragLeave` 끌기 작업을 수행 하는 메서드를 호출 합니다.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFC탭드롭타겟::온드래그오버

사용자가 포커스가 있는 탭 창에 개체를 드래그할 때 프레임워크에서 호출됩니다.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

|||
|-|-|
|매개 변수|설명|
|*pWnd*|【인】 하지 않는.|
|*pDataObject*|【인】 사용자가 드래그하는 개체에 대한 포인터입니다.|
|*dwKeyState*|【인】 수정자 키의 상태를 포함합니다. 이는 MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON 여러 가지 조합입니다.|
|*지점*|【인】 클라이언트 좌표에서 마우스 포인터의 위치입니다.|

### <a name="return-value"></a>Return Value

*점에*의해 지정된 위치에서 드롭이 발생하는 경우 발생하는 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>설명

이 메서드는 끌기 작업이 활성화될 때 커서 아래에 있는 탭을 만듭니다. 도구 모음 프레임워크가 사용자 지정 모드에 없거나 클립보드 데이터 형식을 사용할 수 없는 경우 DROPEFFECT_NONE 반환됩니다. 그렇지 않으면 제공된 매개 `CMFCBaseTabCtrl::OnDragOver` 변수를 호출한 결과를 반환합니다.

사용자 지정 모드에 대한 자세한 내용은 [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)을 참조하십시오. 클립보드 데이터 형식에 대한 자세한 내용은 [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)을 참조하십시오.

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFC탭드롭타겟::온드롭엑스

사용자가 끌기 작업이 끝날 때 마우스 단추를 해제할 때 프레임워크에서 호출됩니다.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

|||
|-|-|
|매개 변수|설명|
|*pWnd*|【인】 하지 않는.|
|*pDataObject*|【인】 사용자가 드래그하는 개체에 대한 포인터입니다.|
|*드롭 이펙트*|【인】 기본 드롭 작업입니다.|
|*드롭리스트*|【인】 하지 않는.|
|*지점*|【인】 클라이언트 좌표에서 마우스 포인터의 위치입니다.|

### <a name="return-value"></a>Return Value

결과 드롭 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>설명

이 메서드는 도구 모음 프레임워크가 사용자 지정 모드에 있고 클립보드 데이터 형식을 사용할 수 있는 경우 호출합니다. `CMFCBaseTabCtrl::OnDrop` 호출이 `CMFCBaseTabCtrl::OnDrop` zero가 아닌 값을 반환하는 경우 이 메서드는 *dropEffect*에 의해 지정된 기본 놓기 효과를 반환합니다. 그렇지 않으면 이 메서드는 DROPEFFECT_NONE 반환합니다. 드롭 효과에 대한 자세한 내용은 [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)을 참조하십시오.

사용자 지정 모드에 대한 자세한 내용은 [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)을 참조하십시오. 클립보드 데이터 형식에 대한 자세한 내용은 [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)을 참조하십시오.

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFC탭드롭대상::레지스터

컨트롤을 OLE 끌어서 놓기 작업의 대상이 될 수 있는 컨트롤으로 등록합니다.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>매개 변수

|||
|-|-|
|매개 변수|설명|
|*p 소유자*|【인】 드롭 대상으로 등록하는 탭 컨트롤입니다.|

### <a name="return-value"></a>Return Value

등록에 성공한 경우 비영; 그렇지 않으면 0.

### <a name="remarks"></a>설명

이 메서드는 [COleDropTarget::등록을](../../mfc/reference/coledroptarget-class.md#register) 호출하여 끌어서 놓기 작업에 대한 컨트롤을 등록합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[OLE 끌어서 놓기](../../mfc/drag-and-drop-ole.md)
