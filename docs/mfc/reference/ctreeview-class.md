---
description: '자세히 알아보기: CTreeView 클래스'
title: CTreeView 클래스
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: 3e50f912f03d5214e8ec238844b3288691a4f326
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318522"
---
# <a name="ctreeview-class"></a>CTreeView 클래스

MFC의 문서 뷰 아키텍처를 사용 하 여 트리 컨트롤 및 트리 컨트롤 기능을 캡슐화 하는 클래스인 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)의 사용을 간소화 합니다.

## <a name="syntax"></a>구문

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CTreeView:: CTreeView](#ctreeview)|`CTreeView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTreeView:: GetTreeCtrl](#gettreectrl)|뷰와 연결 된 트리 컨트롤을 반환 합니다.|

## <a name="remarks"></a>설명

이 아키텍처에 대 한 자세한 내용은 [CView](../../mfc/reference/cview-class.md) 클래스에 대 한 개요 및 여기에 언급 된 상호 참조를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>요구 사항

**헤더:** afxcview

## <a name="ctreeviewctreeview"></a><a name="ctreeview"></a> CTreeView:: CTreeView

`CTreeView` 개체를 생성합니다.

```
CTreeView();
```

## <a name="ctreeviewgettreectrl"></a><a name="gettreectrl"></a> CTreeView:: GetTreeCtrl

뷰와 연결 된 트리 컨트롤에 대 한 참조를 반환 합니다.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>참고 항목

[CCtrlView 클래스](../../mfc/reference/cctrlview-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CCtrlView 클래스](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl 클래스](../../mfc/reference/ctreectrl-class.md)
