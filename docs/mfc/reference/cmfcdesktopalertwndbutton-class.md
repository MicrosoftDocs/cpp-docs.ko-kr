---
title: CMFCDesktopAlertWndButton 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efabaabdcc3f08a58cb7dc0a7845a56e5238548d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 클래스
바탕 화면 경고 대화 상자에 추가 하는 단추를 허용 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|||  
|-|-|  
|이름|설명|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|기본 생성자입니다.|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|소멸자|  
  
### <a name="public-methods"></a>Public 메서드  
  
|||  
|-|-|  
|이름|설명|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|캡션 영역의 경고 대화 상자에는 단추가 표시 되는지를 있는지 여부를 결정 합니다.|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|단추 경고 대화 상자를 닫고 있는지 여부를 결정 합니다.|  
  
### <a name="data-members"></a>데이터 멤버  
  
|||  
|-|-|  
|이름|설명|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|단추 캡션 영역 경고 대화 상자에에서 표시 되는지 여부를 지정 하는 부울 값입니다.|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|단추 경고 대화 상자를 닫고 있는지 여부를 지정 하는 부울 값입니다.|  
  
### <a name="remarks"></a>설명  
 생성자는 기본적으로 설정 된 `m_bIsCaptionButton` 및 `m_bIsCloseButton` 데이터 멤버를 `FALSE`합니다. 부모 `CMFCDesktopAlertDialog` 개체 집합이 `m_bIsCaptionButton` 를 `TRUE` 단추가 경고 대화 상자 캡션 영역에 위치 합니다. `CMFCDesktopAlertDialog` 클래스 만듭니다는 `CMFCDesktopAlertWndButton` 경고 대화 상자를 닫습니다는 단추와은 상자 응용 프로그램을 설정 하는 개체 `m_bIsCloseButton` 를 `TRUE`합니다.  
  
 추가 `CMFCDesktopAlertWndButton` 개체를 한 `CMFCDesktopAlertDialog` 개체 모든 단추를 추가 합니다. 에 대 한 자세한 내용은 `CMFCDesktopAlertDialog`, 참조 [CMFCDesktopAlertDialog 클래스](../../mfc/reference/cmfcdesktopalertdialog-class.md)합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 사용 하는 `SetImage` 에서 메서드는 `CMFCDesktopAlertWndButton` 클래스. 이 코드 조각은의 일부인는 [바탕 화면 경고 데모 샘플](../../visual-cpp-samples.md)합니다.  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton  
 캡션 영역의 경고 대화 상자에는 단추가 표시 되는지를 있는지 여부를 결정 합니다.  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>반환 값  
 단추 경고 대화 상자; 캡션 영역에 표시 되 면 0이 아닌 그렇지 않으면 0입니다.  
  
##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton  
 단추 경고 대화 상자를 닫고 있는지 여부를 결정 합니다.  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>반환 값  
 단추 경고 대화 상자가; 종료 하면 0이 아니고 그렇지 않으면 0입니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog 클래스](../../mfc/reference/cmfcdesktopalertdialog-class.md)
