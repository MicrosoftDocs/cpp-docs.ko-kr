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
ms.openlocfilehash: d0090386b1ebb4d89b9a7613a0b2a28529decbe5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127432"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 클래스

탭 컨트롤과 OLE 라이브러리 사이의 통신 메커니즘을 제공 합니다.

## <a name="syntax"></a>구문

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|||
|-|-|
|name|설명|
|`CMFCTabDropTarget::CMFCTabDropTarget`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|||
|-|-|
|name|설명|
|[CMFCTabDropTarget:: System.windows.uielement.ondragenter](#ondragenter)|사용자가 개체를 탭 창으로 끌 때 프레임 워크에서 호출 됩니다. ( [Coledroptarget:: system.windows.uielement.ondragenter](../../mfc/reference/coledroptarget-class.md#ondragenter)를 재정의 합니다.)|
|[CMFCTabDropTarget:: System.windows.uielement.ondragleave](#ondragleave)|사용자가 포커스가 있는 탭 창 밖으로 개체를 끌 때 프레임 워크에서 호출 됩니다. ( [Coledroptarget:: system.windows.uielement.ondragleave](../../mfc/reference/coledroptarget-class.md#ondragleave)를 재정의 합니다.)|
|[CMFCTabDropTarget:: System.windows.uielement.ondragover](#ondragover)|사용자가 포커스를 가진 탭 창으로 개체를 끌 때 프레임 워크에서 호출 됩니다. ( [Coledroptarget:: system.windows.uielement.ondragover](../../mfc/reference/coledroptarget-class.md#ondragover)를 재정의 합니다.)|
|[CMFCTabDropTarget:: OnDropEx](#ondropex)|사용자가 끌기 작업 끝에서 마우스 단추를 놓을 때 프레임 워크에서 호출 됩니다. ( [Coledroptarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)를 재정의 합니다.)|
|[CMFCTabDropTarget:: Register](#register)|컨트롤을 OLE 끌어서 놓기 작업의 대상이 될 수 있는 컨트롤로 등록 합니다.|

### <a name="remarks"></a>설명

이 클래스는 `CMFCBaseTabCtrl` 클래스에 끌어서 놓기 지원을 제공 합니다. 응용 프로그램이 [AfxOleInit](ole-initialization.md#afxoleinit) 함수를 사용 하 여 OLE 라이브러리를 초기화 하는 경우 `CMFCBaseTabCtrl` 개체는 끌어서 놓기 작업을 위해 자체적으로 등록 됩니다.

`CMFCTabDropTarget` 클래스는 끌기 작업이 활성 상태로 나타날 때 커서 아래에 있는 탭을 만들어 기본 클래스를 확장 합니다. 끌어서 놓기 작업에 대 한 자세한 내용은 [OLE 끌어서 놓기](../../mfc/drag-and-drop-ole.md)를 참조 하십시오.

## <a name="example"></a>예제

다음 예제에서는 `CMFCTabDropTarget` 개체를 생성하고 해당 `Register` 메서드를 사용하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxbasetabctrl.h

##  <a name="ondragenter"></a>CMFCTabDropTarget:: System.windows.uielement.ondragenter

사용자가 개체를 탭 창으로 끌 때 프레임 워크에서 호출 됩니다.

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
|*pWnd*|진행 사용 되지 않는.|
|*pDataObject*|진행 사용자가 끌어 온 개체에 대 한 포인터입니다.|
|*dwKeyState*|진행 보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.|
|*point*|진행 클라이언트 좌표에서 커서의 위치입니다.|

### <a name="return-value"></a>Return Value

놓기가 *point*로 지정 된 위치에서 발생 하는 경우 발생 하는 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>설명

이 메서드는 도구 모음 프레임 워크가 사용자 지정 모드가 아니거나 클립보드 데이터 형식을 사용할 수 없는 경우 DROPEFFECT_NONE를 반환 합니다. 그렇지 않은 경우에는 제공 된 매개 변수를 사용 하 여 `CMFCBaseTabCtrl::OnDragEnter` 호출 결과를 반환 합니다.

사용자 지정 모드에 대 한 자세한 내용은 [Cmfctoolbar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)를 참조 하세요. 클립보드 데이터 형식에 대 한 자세한 내용은 [Coledataobject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)를 참조 하세요.

##  <a name="ondragleave"></a>CMFCTabDropTarget:: System.windows.uielement.ondragleave

사용자가 포커스가 있는 탭 창 밖으로 개체를 끌 때 프레임 워크에서 호출 됩니다.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

|||
|-|-|
|매개 변수|설명|
|*pWnd*|진행 사용 되지 않는.|

### <a name="remarks"></a>설명

이 메서드는 `CMFCBaseTabCtrl::OnDragLeave` 메서드를 호출 하 여 끌기 작업을 수행 합니다.

##  <a name="ondragover"></a>CMFCTabDropTarget:: System.windows.uielement.ondragover

사용자가 포커스를 가진 탭 창으로 개체를 끌 때 프레임 워크에서 호출 됩니다.

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
|*pWnd*|진행 사용 되지 않는.|
|*pDataObject*|진행 사용자가 끌어 온 개체에 대 한 포인터입니다.|
|*dwKeyState*|진행 보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.|
|*point*|진행 클라이언트 좌표로 나타낸 마우스 포인터의 위치입니다.|

### <a name="return-value"></a>Return Value

놓기가 *point*로 지정 된 위치에서 발생 하는 경우 발생 하는 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>설명

이 메서드는 끌기 작업이 활성 상태로 나타날 때 커서 아래에 있는 탭을 만듭니다. 도구 모음 프레임 워크가 사용자 지정 모드가 아니거나 클립보드 데이터 형식을 사용할 수 없는 경우 DROPEFFECT_NONE를 반환 합니다. 그렇지 않은 경우에는 제공 된 매개 변수를 사용 하 여 `CMFCBaseTabCtrl::OnDragOver` 호출 결과를 반환 합니다.

사용자 지정 모드에 대 한 자세한 내용은 [Cmfctoolbar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)를 참조 하세요. 클립보드 데이터 형식에 대 한 자세한 내용은 [Coledataobject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)를 참조 하세요.

##  <a name="ondropex"></a>CMFCTabDropTarget:: OnDropEx

사용자가 끌기 작업 끝에서 마우스 단추를 놓을 때 프레임 워크에서 호출 됩니다.

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
|*pWnd*|진행 사용 되지 않는.|
|*pDataObject*|진행 사용자가 끌어 온 개체에 대 한 포인터입니다.|
|*dropEffect*|진행 기본 삭제 작업입니다.|
|*dropList*|진행 사용 되지 않는.|
|*point*|진행 클라이언트 좌표로 나타낸 마우스 포인터의 위치입니다.|

### <a name="return-value"></a>Return Value

결과 삭제 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>설명

이 메서드는 도구 모음 프레임 워크가 사용자 지정 모드에 있고 클립보드 데이터 형식을 사용할 수 있는 경우 `CMFCBaseTabCtrl::OnDrop`를 호출 합니다. `CMFCBaseTabCtrl::OnDrop`에 대 한 호출이 0이 아닌 값을 반환 하는 경우이 메서드는 *dropEffect*에 지정 된 기본 놓기 효과를 반환 합니다. 그렇지 않으면이 메서드는 DROPEFFECT_NONE 반환 합니다. 드롭 효과에 대 한 자세한 내용은 [Coledroptarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)를 참조 하세요.

사용자 지정 모드에 대 한 자세한 내용은 [Cmfctoolbar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)를 참조 하세요. 클립보드 데이터 형식에 대 한 자세한 내용은 [Coledataobject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)를 참조 하세요.

##  <a name="register"></a>CMFCTabDropTarget:: Register

컨트롤을 OLE 끌어서 놓기 작업의 대상이 될 수 있는 컨트롤로 등록 합니다.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>매개 변수

|||
|-|-|
|매개 변수|설명|
|*pOwner*|진행 놓기 대상으로 등록할 tab 컨트롤입니다.|

### <a name="return-value"></a>Return Value

등록이 성공 하면 0이 아닌 값이 됩니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 [Coledroptarget:: Register](../../mfc/reference/coledroptarget-class.md#register) 를 호출 하 여 끌어서 놓기 작업에 대 한 컨트롤을 등록 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[OLE 끌어서 놓기](../../mfc/drag-and-drop-ole.md)
