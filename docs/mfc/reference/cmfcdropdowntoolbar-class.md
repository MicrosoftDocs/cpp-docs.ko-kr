---
title: CMFCDropDownToolBar 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b227f9d2fdd43b576f89b74f43e4cdce8476bf9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692385"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar 클래스
사용자가 최상위 도구 모음 단추를 누르고 있을 때 나타나는 도구 모음입니다.  
  
   자세한 세부 정보에 대 한 참조에 있는 소스 코드를 **VC\\atlmfc\\src\\mfc** Visual Studio 설치의 폴더입니다.  
## <a name="syntax"></a>구문  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(`CPane::AllowShowOnPaneMenu`를 재정의합니다.)|  
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(재정의 [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|  
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(재정의 [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|  
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||  
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||  
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(`CMFCToolBar::OnSendCommand`를 재정의합니다.)|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(재정의 [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md)합니다.|  
  
### <a name="remarks"></a>설명  
 `CMFCDropDownToolBar` 팝업 메뉴의 동작을 사용 하 여 도구 모음의 시각적 모양을 결합 하는 개체입니다. 때 사용자를 누르고 드롭다운 도구 모음 단추 (참조 [CMFCDropDownToolbarButton 클래스](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), 드롭다운 도구 모음이 나타나고 사용자에 스크롤 및 마우스를 해제 하 여 드롭다운 도구 모음에서 단추에 선택할 수 단추입니다. 사용자가 드롭다운 도구 모음에서 단추를 선택, 최상위 도구 모음에서 현재 단추와 해당 단추가 표시 됩니다.  
  
 드롭다운 도구 모음 사용자 지정 하거나 창을 도킹 하면 없습니다 및 분리 상태 없습니다.  
  
 다음 그림에 표시 된 `CMFCDropDownToolBar` 개체:  
  
 ![CMFCDropDownToolbar의 예제](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 만든를 `CMFCDropDownToolBar` 는 일반 도구 모음을 만든 동일한 방식으로 개체 (참조 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)).  
  
 드롭다운 도구 모음에 부모 도구 모음 삽입할:  
  
 1. 부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다.  
  
 2. 만들기는 `CMFCDropDownToolBarButton` 드롭다운 도구 모음을 포함 하는 개체 (자세한 내용은 참조 하십시오 [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).  
  
 3. 사용 하 여 더미 단추 바꾸기 합니다 `CMFCDropDownToolBarButton` 개체를 사용 하 여 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)합니다.  
  
 도구 모음 단추에 대 한 자세한 내용은 참조 하세요. [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)합니다. 드롭다운 도구 모음의 예로, VisualStudioDemo 샘플 프로젝트를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 예제에서는 사용 하는 방법에 설명 합니다 `Create` 의 메서드는 `CMFCDropDownToolBar` 클래스입니다. 이 코드 조각은의 일부인 합니다 [Visual Studio 데모 샘플](../../visual-cpp-samples.md)합니다.  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>반환 값  
  
### <a name="remarks"></a>설명  
  
##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap  
 응용 프로그램 리소스에서 도구 모음 이미지를 로드합니다.  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *uiResID*  
 핫 도구 모음 이미지를 참조하는 비트맵의 리소스 ID입니다.  
  
 [in] *uiColdResID*  
 콜드 도구 모음 이미지를 참조하는 비트맵의 리소스 ID입니다.  
  
 [in] *uiMenuResID*  
 일반 메뉴 이미지를 참조하는 비트맵의 리소스 ID입니다.  
  
 [in] *차단*  
 도구 모음을 잠그려면 그렇지 않으면 FALSE입니다.  
  
 [in] *uiDisabledResID*  
 비활성화된 도구 모음 이미지를 참조하는 비트맵의 리소스 ID입니다.  
  
 [in] *uiMenuDisabledResID*  
 비활성화된 메뉴 이미지를 참조하는 비트맵의 리소스 ID입니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공하면 0이 아니고, 실패하면 0입니다.  
  
### <a name="remarks"></a>설명  
 합니다 [cmfctoolbar:: Loadtoolbarex](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) 도구 모음을 사용 하 여 연결 된 이미지를 로드 하려면이 메서드를 호출 합니다. 이미지 리소스의 사용자 지정 로드를 수행하려면 이 메서드를 재정의합니다.  
  
 `LoadBitmapEx` 메서드를 호출하여 도구 모음을 만든 후 추가 이미지를 로드합니다.  
  
##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar  

  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID = 0,  
    UINT uiMenuResID = 0,
    BOOL = FALSE,  
    UINT uiDisabledResID = 0,  
    UINT uiMenuDisabledResID = 0,  
    UINT uiHotResID = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *uiResID*  
 [in] *uiColdResID*  
 [in] *uiMenuResID*  
 [in] *BOOL*  
 [in] *uiDisabledResID*  
 [in] *uiMenuDisabledResID*  
 [in] *uiHotResID*  
  
### <a name="return-value"></a>반환 값  
  
### <a name="remarks"></a>설명  
  
##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp  

  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *nFlags*  
 [in] *지점*  
  
### <a name="remarks"></a>설명  
  
##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove  

  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *nFlags*  
 [in] *지점*  
  
### <a name="remarks"></a>설명  
  
##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *pButton*  
  
### <a name="return-value"></a>반환 값  
  
### <a name="remarks"></a>설명  
  
##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *pTarget*  
 [in] *bDisableIfNoHndler*  
  
### <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [CMFCDropDownToolbarButton 클래스](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)



