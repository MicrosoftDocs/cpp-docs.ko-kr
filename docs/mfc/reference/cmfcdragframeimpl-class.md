---
description: '자세한 정보: Cmfcdrag프레임 하 클래스'
title: Cmfcdrag프레임의 구현이 클래스
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 9885b750ace86d11ca573f23c7ee1c03d8926921
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294056"
---
# <a name="cmfcdragframeimpl-class"></a>Cmfcdrag프레임의 구현이 클래스

`CMFCDragFrameImpl`클래스는 사용자가 창을 표준 도킹 모드로 끌 때 나타나는 끌기 사각형을 그립니다.
자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>설명

이 클래스의 개체는 각 [Cpane 클래스](../../mfc/reference/cpane-class.md) 개체에 포함 되어 있습니다. 따라서 메서드를 사용 하는 각 창은 `CanFloat` 사용자가 끌 때 끌기 사각형을 표시 합니다.

[AFX_GLOBAL_DATA:: m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) 및 [AFX_GLOBAL_DATA:: m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock)를 사용 하 여 끌기 사각형의 두께를 제어할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxdragframeimpl

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a> Cmfcdrag프레임 하:: EndDrawDragFrame

```cpp
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *Bclearinternalrects*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdragframeimplinit"></a><a name="init"></a> Cmfcdrag프레임 하:: Init

```cpp
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>매개 변수

진행 *pDraggedWnd*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a> Cmfcdrag프레임 하:: MoveDragFrame

```cpp
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>매개 변수

진행 *bForceMove*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a> Cmfcdrag프레임 laceTabPreDocking::P

```cpp
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>매개 변수

진행 *pTabbedBar*<br/>

진행 *Bfirsttime*<br/>

진행 *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a> Cmfcdrag프레임 하:: RemoveTabPreDocking

```cpp
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>매개 변수

진행 *정책 모음*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a> Cmfcdrag프레임 하:: ResetState

```cpp
void ResetState();
```

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CPane 클래스](../../mfc/reference/cpane-class.md)
