---
description: '자세히 알아보기: CListView 클래스'
title: CListView 클래스
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: 5576a0997c84e8f5639911a1120a6645e720a7cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259567"
---
# <a name="clistview-class"></a>CListView 클래스

MFC의 문서 뷰 아키텍처를 사용 하 여 목록 컨트롤 및 목록 컨트롤 기능을 캡슐화 하는 클래스인 [CListCtrl](../../mfc/reference/clistctrl-class.md)의 사용을 간소화 합니다.

## <a name="syntax"></a>구문

```
class CListView : public CCtrlView
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CListView:: CListView](#clistview)|`CListView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CListView:: GetListCtrl](#getlistctrl)|뷰와 연결 된 목록 컨트롤을 반환 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CListView:: RemoveImageList](#removeimagelist)|지정 된 이미지 목록을 목록 뷰에서 제거 합니다.|

## <a name="remarks"></a>설명

이 아키텍처에 대 한 자세한 내용은 [CView](../../mfc/reference/cview-class.md) 클래스에 대 한 개요 및 여기에 언급 된 상호 참조를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>요구 사항

**헤더:** afxcview

## <a name="clistviewclistview"></a><a name="clistview"></a> CListView:: CListView

`CListView` 개체를 생성합니다.

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a> CListView:: GetListCtrl

뷰와 연결 된 목록 컨트롤에 대 한 참조를 가져오려면이 멤버 함수를 호출 합니다.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>반환 값

뷰와 연결 된 목록 컨트롤에 대 한 참조입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a> CListView:: RemoveImageList

지정 된 이미지 목록을 목록 뷰에서 제거 합니다.

```cpp
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>매개 변수

*nImageList*<br/>
제거할 이미지의 인덱스 (0부터 시작)입니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 클래스](../../mfc/reference/cctrlview-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView 클래스](../../mfc/reference/cctrlview-class.md)
