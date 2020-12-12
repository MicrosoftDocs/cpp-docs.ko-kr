---
description: '자세히 알아보기: COleDropTarget 클래스'
title: COleDropTarget 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
ms.openlocfilehash: ff911caa98031899ab018434d87d813d3c45362e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227106"
---
# <a name="coledroptarget-class"></a>COleDropTarget 클래스

창과 OLE 라이브러리 사이의 통신 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDropTarget:: COleDropTarget](#coledroptarget)|`COleDropTarget` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDropTarget:: System.windows.uielement.ondragenter](#ondragenter)|커서를 창으로 처음 가져가면 호출 됩니다.|
|[COleDropTarget:: System.windows.uielement.ondragleave](#ondragleave)|커서를 창 밖으로 끌 때 호출 됩니다.|
|[COleDropTarget:: System.windows.uielement.ondragover](#ondragover)|커서를 창 위로 끌 때 반복적으로 호출 됩니다.|
|[COleDropTarget:: OnDragScroll](#ondragscroll)|커서를 창의 스크롤 영역으로 끌 지 여부를 결정 하기 위해 호출 됩니다.|
|[COleDropTarget:: OnDrop](#ondrop)|창, 기본 처리기에 데이터를 놓을 때 호출 됩니다.|
|[COleDropTarget:: OnDropEx](#ondropex)|창의 초기 처리기에 데이터를 놓을 때 호출 됩니다.|
|[COleDropTarget:: Register](#register)|창을 유효한 놓기 대상으로 등록 합니다.|
|[COleDropTarget:: Revoke](#revoke)|창이 올바른 놓기 대상으로 중단 되도록 합니다.|

## <a name="remarks"></a>설명

이 클래스의 개체를 만들면 창에서 OLE 끌어서 놓기 메커니즘을 통해 데이터를 허용할 수 있습니다.

Drop 명령을 허용 하는 창을 가져오려면 먼저 클래스의 개체 `COleDropTarget` 를 만든 다음 원하는 개체에 대 한 포인터를 사용 하 여 [Register](#register) 함수를 `CWnd` 유일한 매개 변수로 호출 해야 합니다.

OLE를 사용 하는 끌어서 놓기 작업에 대 한 자세한 내용은 [ole 끌어서 놓기](../../mfc/drag-and-drop-ole.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a> COleDropTarget:: COleDropTarget

클래스의 개체를 생성 `COleDropTarget` 합니다.

```
COleDropTarget();
```

### <a name="remarks"></a>설명

[Register](#register) 를 호출 하 여이 개체를 창과 연결 합니다.

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a> COleDropTarget:: System.windows.uielement.ondragenter

커서를 창으로 처음 끌 때 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
커서가 입력 하는 창을 가리킵니다.

*pDataObject*<br/>
삭제할 수 있는 데이터를 포함 하는 데이터 개체를 가리킵니다.

*dwKeyState*<br/>
보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.

*까지*<br/>
클라이언트 좌표에서 커서의 현재 위치를 포함 합니다.

### <a name="return-value"></a>반환 값

*Point* 로 지정 된 위치에서 놓기를 시도 했을 때 발생 하는 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- Drop을 사용할 수 DROPEFFECT_NONE.

- DROPEFFECT_COPY 복사 작업이 수행 됩니다.

- DROPEFFECT_MOVE 이동 작업이 수행 됩니다.

- 끌어 놓은 데이터에서 원래 데이터로의 링크를 설정 DROPEFFECT_LINK 합니다.

- 끌기 스크롤 작업이 발생 하거나 대상에서 발생 하는 DROPEFFECT_SCROLL입니다.

### <a name="remarks"></a>설명

창에서 drop 작업을 수행할 수 있도록 하려면이 함수를 재정의 합니다. 기본 구현에서는 기본적으로 DROPEFFECT_NONE을 반환 하는 [CView:: system.windows.uielement.ondragenter](../../mfc/reference/cview-class.md#ondragenter)를 호출 합니다.

자세한 내용은 [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) in the Windows SDK을 참조 하세요.

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a> COleDropTarget:: System.windows.uielement.ondragleave

끌기 작업이 적용 되는 동안 커서가 창을 벗어나면 프레임 워크에서 호출 됩니다.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
커서가 있는 창을 가리킵니다.

### <a name="remarks"></a>설명

끌기 작업이 지정 된 창을 벗어나면 특수 동작을 수행 하려면이 함수를 재정의 합니다. 이 함수의 기본 구현에서는 [CView:: system.windows.uielement.ondragleave](../../mfc/reference/cview-class.md#ondragleave)를 호출 합니다.

자세한 내용은 [IDropTarget::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) in the Windows SDK을 참조 하세요.

## <a name="coledroptargetondragover"></a><a name="ondragover"></a> COleDropTarget:: System.windows.uielement.ondragover

커서를 창 위로 끌 때 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
커서가 있는 창을 가리킵니다.

*pDataObject*<br/>
삭제할 데이터를 포함 하는 데이터 개체를 가리킵니다.

*dwKeyState*<br/>
보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.

*까지*<br/>
클라이언트 좌표에서 커서의 현재 위치를 포함 합니다.

### <a name="return-value"></a>반환 값

*Point* 로 지정 된 위치에서 놓기를 시도 했을 때 발생 하는 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- Drop을 사용할 수 DROPEFFECT_NONE.

- DROPEFFECT_COPY 복사 작업이 수행 됩니다.

- DROPEFFECT_MOVE 이동 작업이 수행 됩니다.

- 끌어 놓은 데이터에서 원래 데이터로의 링크를 설정 DROPEFFECT_LINK 합니다.

- DROPEFFECT_SCROLL는 끌기 스크롤 작업이 대상에서 발생 하거나 발생 하려고 함을 나타냅니다.

### <a name="remarks"></a>설명

창에서 drop 작업을 수행할 수 있도록이 함수를 재정의 해야 합니다. 이 함수의 기본 구현에서는 기본적으로 DROPEFFECT_NONE을 반환 하는 [CView:: system.windows.uielement.ondragover](../../mfc/reference/cview-class.md#ondragover)를 호출 합니다. 이 함수는 끌어서 놓기 작업 중에 자주 호출 되기 때문에 최대한 최적화 해야 합니다.

자세한 내용은 [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) in the Windows SDK을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a> COleDropTarget:: OnDragScroll

[System.windows.uielement.ondragenter](#ondragenter) 또는 [system.windows.uielement.ondragover](#ondragover) 를 호출 하 여 *요소가* 스크롤 영역에 있는지 여부를 확인 하기 전에 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
커서가 현재 있는 창을 가리킵니다.

*dwKeyState*<br/>
보조키의 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.

*까지*<br/>
화면에 상대적인 커서 위치 (픽셀)를 포함 합니다.

### <a name="return-value"></a>반환 값

*Point* 로 지정 된 위치에서 놓기를 시도 했을 때 발생 하는 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- Drop을 사용할 수 DROPEFFECT_NONE.

- DROPEFFECT_COPY 복사 작업이 수행 됩니다.

- DROPEFFECT_MOVE 이동 작업이 수행 됩니다.

- 끌어 놓은 데이터에서 원래 데이터로의 링크를 설정 DROPEFFECT_LINK 합니다.

- DROPEFFECT_SCROLL는 끌기 스크롤 작업이 대상에서 발생 하거나 발생 하려고 함을 나타냅니다.

### <a name="remarks"></a>설명

이 이벤트에 특별 한 동작을 제공 하려는 경우이 함수를 재정의 합니다. 이 함수의 기본 구현은 [CView:: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)을 호출 합니다 .이는 DROPEFFECT_NONE을 반환 하 고 창의 테두리 안쪽에 있는 기본 스크롤 영역으로 커서를 끌 때 창을 스크롤합니다.

## <a name="coledroptargetondrop"></a><a name="ondrop"></a> COleDropTarget:: OnDrop

놓기 작업이 발생 하는 경우 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
커서가 현재 있는 창을 가리킵니다.

*pDataObject*<br/>
삭제할 데이터를 포함 하는 데이터 개체를 가리킵니다.

*dropEffect*<br/>
사용자가 삭제 작업에 대해 선택한 효과입니다. 다음 중 하나 이상이 될 수 있습니다.

- DROPEFFECT_COPY 복사 작업이 수행 됩니다.

- DROPEFFECT_MOVE 이동 작업이 수행 됩니다.

- 끌어 놓은 데이터에서 원래 데이터로의 링크를 설정 DROPEFFECT_LINK 합니다.

*까지*<br/>
화면에 상대적인 커서 위치 (픽셀)를 포함 합니다.

### <a name="return-value"></a>반환 값

삭제에 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

프레임 워크는 먼저 [Ondropex](#ondropex)를 호출 합니다. 함수에서 `OnDropEx` drop을 처리 하지 않는 경우 프레임 워크는이 멤버 함수를 호출 `OnDrop` 합니다. 일반적으로 응용 프로그램은 뷰 클래스의 [Ondropex](../../mfc/reference/cview-class.md#ondropex) 를 재정의 하 여 마우스 오른쪽 단추 끌어서 놓기를 처리 합니다. 일반적으로 뷰 클래스 [Ondrop](../../mfc/reference/cview-class.md#ondrop) 은 간단한 끌어서 놓기를 처리 하는 데 사용 됩니다.

의 기본 구현은 `COleDropTarget::OnDrop` [CView:: ondrop](../../mfc/reference/cview-class.md#ondrop)을 호출 하며,이는 기본적으로 FALSE를 반환 합니다.

자세한 내용은 [IDropTarget::D rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) in Windows SDK을 참조 하세요.

## <a name="coledroptargetondropex"></a><a name="ondropex"></a> COleDropTarget:: OnDropEx

놓기 작업이 발생 하는 경우 프레임 워크에서 호출 됩니다.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
커서가 현재 있는 창을 가리킵니다.

*pDataObject*<br/>
삭제할 데이터를 포함 하는 데이터 개체를 가리킵니다.

*dropDefault*<br/>
사용자가 현재 키 상태를 기준으로 기본 drop 작업에 대해 선택한 효과입니다. DROPEFFECT_NONE 수 있습니다. Drop 효과는 설명 섹션에 설명 되어 있습니다.

*dropList*<br/>
Drop 소스가 지 원하는 drop 효과 목록입니다. 놓기 효과 값은 비트 OR (**&#124;**) 연산을 사용 하 여 결합할 수 있습니다. Drop 효과는 설명 섹션에 설명 되어 있습니다.

*까지*<br/>
화면에 상대적인 커서 위치 (픽셀)를 포함 합니다.

### <a name="return-value"></a>반환 값

*Point* 로 지정 된 위치에서 삭제 시도로 인해 발생 하는 낙하 효과입니다. Drop 효과는 설명 섹션에 설명 되어 있습니다.

### <a name="remarks"></a>설명

프레임 워크는 먼저이 함수를 호출 합니다. 삭제를 처리 하지 않는 경우 프레임 워크는 [Ondrop](#ondrop)을 호출 합니다. 일반적으로 마우스 오른쪽 단추 끌어서 놓기를 지원 하기 위해 view 클래스에서 [Ondropex](../../mfc/reference/cview-class.md#ondropex) 를 재정의 합니다. 일반적으로 뷰 클래스 [Ondrop](../../mfc/reference/cview-class.md#ondrop) 은 간단한 끌어서 놓기를 지 원하는 사례를 처리 하는 데 사용 됩니다.

의 기본 구현에서는 `COleDropTarget::OnDropEx` [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex)를 호출 합니다. 기본적으로 [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex) 는 [ondrop](#ondrop) 멤버 함수를 호출 해야 함을 나타내는 더미 값을 반환 합니다.

Drop effects는 drop 작업과 관련 된 동작을 설명 합니다. 다음 drop effects 목록을 참조 하십시오.

- Drop을 사용할 수 DROPEFFECT_NONE.

- DROPEFFECT_COPY 복사 작업이 수행 됩니다.

- DROPEFFECT_MOVE 이동 작업이 수행 됩니다.

- 끌어 놓은 데이터에서 원래 데이터로의 링크를 설정 DROPEFFECT_LINK 합니다.

- DROPEFFECT_SCROLL는 끌기 스크롤 작업이 대상에서 발생 하거나 발생 하려고 함을 나타냅니다.

자세한 내용은 [IDropTarget::D rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) in Windows SDK을 참조 하세요.

## <a name="coledroptargetregister"></a><a name="register"></a> COleDropTarget:: Register

이 함수를 호출 하 여 창을 OLE Dll에 유효한 놓기 대상으로 등록 합니다.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
놓기 대상으로 등록할 창을 가리킵니다.

### <a name="return-value"></a>반환 값

등록이 성공 하면 0이 아닌 값이 됩니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Drop 작업을 수락 하려면이 함수를 호출 해야 합니다.

자세한 내용은 Windows SDK에서 [Registerdragdrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) 을 참조 하세요.

## <a name="coledroptargetrevoke"></a><a name="revoke"></a> COleDropTarget:: Revoke

놓기 대상 목록에서 제거 하기 위해 [Register](#register) 를 호출 하 여 놓기 대상으로 등록 된 모든 창을 소멸 하기 전에이 함수를 호출 합니다.

```
virtual void Revoke();
```

### <a name="remarks"></a>설명

이 함수는 등록 된 창에 대 한 [Ondestroy](../../mfc/reference/cwnd-class.md#ondestroy) 처리기에서 자동으로 호출 되므로 일반적으로 명시적으로이 함수를 호출할 필요가 없습니다.

자세한 내용은 Windows SDK에서 [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource 클래스](../../mfc/reference/coledropsource-class.md)
