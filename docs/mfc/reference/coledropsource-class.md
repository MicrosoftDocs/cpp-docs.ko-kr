---
description: '자세히 알아보기: COleDropSource 클래스'
title: COleDropSource 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: 069c1b2a3cb46f0824da55bca8e97041e9b0b2e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227145"
---
# <a name="coledropsource-class"></a>COleDropSource 클래스

데이터를 놓기 대상으로 끌 수 있습니다.

## <a name="syntax"></a>구문

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDropSource:: COleDropSource](#coledropsource)|`COleDropSource` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDropSource:: System.windows.dragdrop.givefeedback>](#givefeedback)|끌어서 놓기 작업을 수행 하는 동안 커서를 변경 합니다.|
|[COleDropSource:: OnBeginDrag](#onbegindrag)|끌어서 놓기 작업 중에 마우스 캡처를 처리 합니다.|
|[COleDropSource:: System.windows.dragdrop.querycontinuedrag>](#querycontinuedrag)|끌기를 계속 해야 하는지 여부를 확인 합니다.|

## <a name="remarks"></a>설명

[Coledroptarget](../../mfc/reference/coledroptarget-class.md) 클래스는 끌어서 놓기 작업의 수신 부분을 처리 합니다. 개체는 끌기 작업이 `COleDropSource` 시작 되는 시기를 결정 하 고 끌기 작업 중에 피드백을 제공 하며 끌기 작업이 종료 되는 시점을 결정 합니다.

개체를 사용 하려면 `COleDropSource` 생성자를 호출 하기만 하면 됩니다. 이렇게 하면 마우스 클릭과 같은 이벤트를 결정 하는 프로세스를 간소화 하 고 Coledatasource를 사용 하 여 끌기 작업을 시작 합니다 [.:D oDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::D Odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)또는 [COleServerItem::D odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) 함수. 이러한 함수는 개체를 만듭니다 `COleDropSource` . 재정의 가능한 함수의 기본 동작을 수정할 수 있습니다 `COleDropSource` . 이러한 멤버 함수는 프레임 워크에서 적절 한 시간에 호출 됩니다.

OLE를 사용 하는 끌어서 놓기 작업에 대 한 자세한 내용은 [ole 끌어서 놓기](../../mfc/drag-and-drop-ole.md)문서를 참조 하세요.

자세한 내용은 Windows SDK에서 [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) 을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a> COleDropSource:: COleDropSource

`COleDropSource` 개체를 생성합니다.

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a> COleDropSource:: System.windows.dragdrop.givefeedback>

[Coledroptarget:: system.windows.uielement.ondragover](../../mfc/reference/coledroptarget-class.md#ondragover) 또는 [coledroptarget::D ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter)를 호출한 후 프레임 워크에서 호출 됩니다.

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>매개 변수

*dropEffect*<br/>
사용자에 게 표시 하려는 효과 이며,이 시점에서 선택한 데이터를 사용 하 여 놓기가 발생 한 경우 발생 하는 결과를 나타냅니다. 일반적으로이 값은 [cview:: system.windows.uielement.ondragenter](../../mfc/reference/cview-class.md#ondragenter) 또는 [Cview:: system.windows.uielement.ondragover](../../mfc/reference/cview-class.md#ondragover)에 대 한 가장 최근의 호출에서 반환 된 값입니다. 다음 중 하나 이상이 될 수 있습니다.

- Drop을 사용할 수 DROPEFFECT_NONE.

- DROPEFFECT_COPY 복사 작업이 수행 됩니다.

- DROPEFFECT_MOVE 이동 작업이 수행 됩니다.

- 끌어 놓은 데이터에서 원래 데이터로의 링크를 설정 DROPEFFECT_LINK 합니다.

- 끌기 스크롤 작업이 발생 하거나 대상에서 발생 하는 DROPEFFECT_SCROLL입니다.

### <a name="return-value"></a>반환 값

끌기를 진행 중인 경우 DRAGDROP_S_USEDEFAULTCURSORS을 반환 하 고, 그렇지 않으면 NOERROR를 반환 합니다.

### <a name="remarks"></a>설명

이 시점에서 drop이 발생 한 경우 발생 하는 상황에 대 한 피드백을 사용자에 게 제공 하려면이 함수를 재정의 합니다. 기본 구현에서는 OLE 기본 커서를 사용 합니다. OLE를 사용 하는 끌어서 놓기 작업에 대 한 자세한 내용은 [ole 끌어서 놓기](../../mfc/drag-and-drop-ole.md)문서를 참조 하세요.

자세한 내용은 Windows SDK에서 [IDropSource:: system.windows.dragdrop.givefeedback>](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::D Ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover), And [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) 를 참조 하세요.

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a> COleDropSource:: OnBeginDrag

왼쪽 마우스 단추를 누르는 등의 끌기 작업을 시작할 수 있는 이벤트가 발생할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
선택한 데이터를 포함 하는 창을 가리킵니다.

### <a name="return-value"></a>반환 값

끌기가 허용 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

끌기 프로세스가 시작 되는 방식을 수정 하려면이 함수를 재정의 합니다. 기본 구현은 마우스를 캡처하고 마우스 왼쪽 또는 오른쪽 단추를 클릭 하거나 ESC 키를 누를 때까지 마우스를 눌렀다 놓습니다.

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a> COleDropSource:: System.windows.dragdrop.querycontinuedrag>

끌기를 시작한 후에는 끌기 작업이 취소 되거나 완료 될 때까지 프레임 워크에서이 함수를 반복적으로 호출 합니다.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>매개 변수

*bEscapePressed*<br/>
에 대 한 마지막 호출 이후 ESC 키를 눌렀는지 여부를 나타냅니다 `COleDropSource::QueryContinueDrag` .

*dwKeyState*<br/>
키보드의 보조키 상태를 포함 합니다. MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON 및 MK_RBUTTON의 조합입니다.

### <a name="return-value"></a>반환 값

ESC 키 또는 오른쪽 단추를 누르면 DRAGDROP_S_CANCEL 하 고, 끌기를 시작 하기 전에 왼쪽 단추를 발생 시킵니다. DROP 작업을 수행 해야 하는지 여부를 DRAGDROP_S_DROP 합니다. 그렇지 않으면 S_OK 합니다.

### <a name="remarks"></a>설명

끌기가 취소 되거나 놓기가 발생 하는 지점을 변경 하려면이 함수를 재정의 합니다.

기본 구현에서는 놓기를 시작 하거나 다음과 같이 끌기를 취소 합니다. ESC 키 또는 마우스 오른쪽 단추를 누르면 끌기 작업이 취소 됩니다. 끌기를 시작한 후 마우스 왼쪽 단추를 누르면 놓기 작업을 시작 합니다. 그렇지 않으면 S_OK을 반환 하 고 추가 작업을 수행 하지 않습니다.

이 함수는 자주 호출 되기 때문에 최대한 최적화 해야 합니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
