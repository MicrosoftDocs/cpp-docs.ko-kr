---
title: CMFCDragFrameImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f743c074bc956181e8b62a02062ac2f22cdfb6e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl 클래스
`CMFCDragFrameImpl` 클래스는 사용자가 표준 도킹 모드의 창을 끌 때 나타나는 끌기 사각형을 그립니다.  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
## <a name="syntax"></a>구문  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>설명  
 이 클래스의 개체가 각각에 포함 된 [CPane 클래스](../../mfc/reference/cpane-class.md) 개체입니다. 따라서 사용 하는 각 창에서 `CanFloat` 메서드는 사용자가 끌어올 때 끌기 사각형을 표시 합니다.  
  
 사용 하 여 끌기 사각형의 두께 제어할 수 있습니다 [afx_global_data:: m_ndragframethicknessfloat](afx-global-data-structure.md#m_ndragframethicknessfloat) 및 [afx_global_data:: m_ndragframethicknessdock](afx-global-data-structure.md#m_ndragframethicknessdock)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame  

  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `bClearInternalRects`  
  
### <a name="remarks"></a>설명  
  
##  <a name="init"></a>  CMFCDragFrameImpl::Init  

  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pDraggedWnd`  
  
### <a name="remarks"></a>설명  
  
##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame  

  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `bForceMove`  
  
### <a name="remarks"></a>설명  
  
##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking  

  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pTabbedBar`  
 [in] `bFirstTime`  
 [in] `pCBarToPlaceOn`  
  
### <a name="remarks"></a>설명  
  
##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking  

  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pOldTargetBar`  
  
### <a name="remarks"></a>설명  
  
##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState  

  
```  
void ResetState();
```  
  
### <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CPane 클래스](../../mfc/reference/cpane-class.md)