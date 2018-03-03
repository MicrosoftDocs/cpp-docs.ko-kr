---
title: "CWinFormsView 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb68e906a06d18b41d97851d8d91717ac3dd78b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="cwinformsview-class"></a>CWinFormsView 클래스
Windows Forms 컨트롤을 MFC 뷰로 호스팅하기 위한 일반 기능을 제공합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CWinFormsView : public CView;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CWinFormsView::CWinFormsView](#cwinformsview)|`CWinFormsView` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CWinFormsView::GetControl](#getcontrol)|Windows Forms 컨트롤에 대 한 포인터를 검색합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|name||  
|----------|-|  
|[CWinFormsView::operator 제어 ^](#operator_control)|Windows Forms 컨트롤에 대 한 포인터로 형식을 캐스팅합니다.|  
  
## <a name="remarks"></a>설명  
 MFC 사용 하 여는 `CWinFormsView` MFC 뷰로 내에서.NET Framework Windows Forms 컨트롤을 호스트 하는 클래스입니다. 기본 보기의 자식인 컨트롤과 MFC 뷰의 전체 클라이언트 영역을 차지 합니다. 결과 비슷합니다는 `CFormView` 보기, 양식 기반 다양 한 보기를 만드는 시간을 실행 및 Windows Forms 디자이너의 사용할 수 있습니다.  
  
 Windows Forms를 사용 하 여에 대 한 자세한 내용은 참조 하십시오. [MFC의 Windows Form 사용자 정의 컨트롤을 사용 하 여](../../dotnet/using-a-windows-form-user-control-in-mfc.md)합니다.  
  
> [!NOTE]
>  동적으로 MFC에 링크 되는 프로젝트 에서만에서 작동 하는 MFC Windows Forms 통합 (프로젝트의 AFXDLL 정의 되어 있는 경우).  
  
> [!NOTE]
>  CWinFormsView MFC 분할 창을 지원 하지 않습니다 ( [CSplitterWnd 클래스](../../mfc/reference/csplitterwnd-class.md)). 현재만 Windows Forms 분할자 컨트롤은 지원 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxwinforms.h  
  
##  <a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 `CWinFormsView` 개체를 생성합니다.  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pManagedViewType`  
 Windows Forms 사용자 정의 컨트롤의 데이터 형식에 대 한 포인터입니다.   
  
### <a name="example"></a>예  
 다음 예제에서는 `CUserView` 클래스에서 상속 `CWinFormsView` 유형을 전달 하 고 `UserControl1` 에 `CWinFormsView` 생성자입니다. `UserControl1`ControlLibrary1.dll에 사용자가 작성 한 컨트롤이입니다.  
  
 [!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>CWinFormsView::GetControl  
 Windows Forms 컨트롤에 대 한 포인터를 검색합니다.  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 `System.Windows.Forms.Control` 개체입니다.  
  
### <a name="remarks"></a>설명  
 Windows Forms을 사용 하는 방법의 예제를 보려면 [MFC의 Windows Form 사용자 정의 컨트롤을 사용 하 여](../../dotnet/using-a-windows-form-user-control-in-mfc.md)합니다.  
  
##  <a name="operator_control"></a>CWinFormsView::operator 제어 ^  
 Windows Forms 컨트롤에 대 한 포인터로 형식을 캐스팅합니다.  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>설명  
 이 연산자를 사용 하면 전달할 수는 `CWinFormsView` 뷰 형식의 Windows Forms 컨트롤에 대 한 포인터를 허용 하는 함수를 <xref:System.Windows.Forms.Control>합니다.  
  
### <a name="example"></a>예  
  참조 [CWinFormsView::GetControl](#getcontrol)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl 클래스](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog 클래스](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView 클래스](../../mfc/reference/cformview-class.md)
