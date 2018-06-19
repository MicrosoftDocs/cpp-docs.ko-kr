---
title: CMFCDropDownToolbarButton 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c65cf3070f199b013a0e85c1ae56764174fdc33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372536"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 클래스
클릭할 때 일반 단추처럼 동작하는 도구 모음 단추의 한 종류입니다. 그러나 드롭다운 도구 모음이 열립니다 ( [CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md) 경우 사용자 번 클릭 하 고 도구 모음 단추를 누르고 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|`CMFCDropDownToolbarButton` 개체를 생성합니다.|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|소멸자|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|도구 모음 단추 속성은 현재 단추에 복사합니다. (재정의 [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCDropDownToolbarButton::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|  
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|드롭다운 도구 모음이 열립니다.|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|도구 모음 단추에서 메뉴에 텍스트를 복사 합니다. (재정의 [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|단추와 연결 된 드롭다운 도구 모음을 검색 합니다.|  
|`CMFCDropDownToolbarButton::GetThisClass`|에 대 한 포인터를 가져오는 데 프레임 워크에서는 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 이 클래스 형식과 연결 된 개체입니다.|  
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|드롭다운 도구 모음이 현재 열려 있는지 여부를 결정 합니다.|  
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|단추가 확장된 테두리 함께 표시 될 수 있는지 여부를 결정 합니다. (재정의 [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|지정 된 장치 컨텍스트와 도킹 상태에 대 한 단추 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다. (재정의 [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|처리 하기 위해 프레임 워크에서 호출 된 [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) 메시지입니다. (`CMCToolBarButton::OnCancelMode`를 재정의합니다.)|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|새 도구 모음에 단추를 삽입할 때 프레임 워크에서 호출 됩니다. (재정의 [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCDropDownToolbarButton::OnClick](#onclick)|사용자가 마우스 단추를 클릭할 때 프레임 워크에서 호출 됩니다. (재정의 [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|사용자가 마우스 단추를 놓을 때 프레임 워크에서 호출 됩니다. (재정의 [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|  
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|부모 도구 모음에서 처리 될 때 프레임 워크에서 호출 된 `WM_HELPHITTEST` 메시지입니다. (재정의 [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|부모 도구 모음 바로 가기 메뉴를 표시 하는 응용 프로그램 때 제공 된 메뉴를 수정 합니다. (재정의 [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|  
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|지정 된 스타일 및 옵션을 사용 하 여 단추를 그리기 위해 프레임 워크에서 호출 됩니다. (재정의 [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|단추를 그리기 위해 프레임 워크에서 호출 된 **명령을** 의 창은 **사용자 지정** 대화 상자. (재정의 [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCDropDownToolbarButton::Serialize](#serialize)|보관 파일에서이 개체를 읽거나 보관 파일에 씁니다. (재정의 [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|단추를 클릭할 때 프레임 워크를 사용 하는 기본 명령을 설정 합니다.|  
  
### <a name="data-members"></a>데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|드롭다운 도구 모음이 표시 될 때까지 사용자를 마우스 단추를 누른 해야 하는 시간의 길이 지정 합니다.|  
  
## <a name="remarks"></a>설명  
 A `CMFCDropDownToolBarButton` 일반 단추 점에서 다릅니다 단추의 오른쪽 아래 모서리 작은 화살표를 포함 합니다. 사용자가 드롭다운 목록 도구 모음에서 단추를 선택한 후 프레임 워크 최상위 도구 모음 단추 (오른쪽 아래 모서리에 있는 작은 화살표가 있는 단추)에 해당 아이콘을 표시 합니다.  
  
 드롭 다운 도구 모음을 구현 하는 방법에 대 한 정보를 참조 하십시오. [CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md)합니다.  
  
 `CMFCDropDownToolBarButton` 에 개체를 내보낼 수는 [CMFCToolBarMenuButton 클래스](../../mfc/reference/cmfctoolbarmenubutton-class.md) 개체 및 팝업 메뉴가 있는 메뉴 단추를 표시 합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxdropdowntoolbar.h  
  
##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom  
 도구 모음 단추 속성은 현재 단추에 복사합니다.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `src`  
 복사할 소스 단추에 대 한 참조입니다.  
  
### <a name="remarks"></a>설명  
 이 도구 모음 단추를 도구 모음 단추 복사 하려면이 메서드를 호출 합니다. `src` 형식 이어야 합니다 `CMFCDropDownToolbarButton`합니다.  
  
##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton  
 `CMFCDropDownToolbarButton` 개체를 생성합니다.  
  
```  
CMFCDropDownToolbarButton();

 
CMFCDropDownToolbarButton(
    LPCTSTR lpszName,  
    CMFCDropDownToolBar* pToolBar);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `lpszName`  
 단추의 기본 텍스트입니다.  
  
 [in] `pToolBar`  
 에 대 한 포인터는 `CMFCDropDownToolBar` 단추를 누를 때 표시 되는 개체입니다.  
  
### <a name="remarks"></a>설명  
 도구 모음에서 첫 번째 단추에서 드롭다운 단추에 복사 생성자의 두 번째 오버 로드는 `pToolBar` 지정 합니다.  
  
 일반적으로 드롭 다운 도구 모음 단추를 도구 모음에서 가장 최근에 사용한 단추에서 텍스트를 사용 하는 `pToolBar` 지정 합니다. 로 지정 된 텍스트를 사용 하 여 `lpszName` 때 단추는 메뉴 단추 또는 변환에 표시 되는 **명령을** 탭은 **사용자 지정** 대화 상자. 에 대 한 자세한 내용은 **사용자 지정** 대화 상자, 참조 [CMFCToolBarsCustomizeDialog 클래스](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)합니다.  
  
### <a name="example"></a>예제  
 다음 예제에서는의 개체를 생성 하는 `CMFCDropDownToolbarButton` 클래스입니다. 이 코드 조각은의 일부인는 [Visual Studio 데모 샘플](../../visual-cpp-samples.md)합니다.  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]  
  
##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar  
 드롭다운 도구 모음이 열립니다.  
  
```  
BOOL DropDownToolbar(CWnd* pWnd);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pWnd`  
 드롭 다운 프레임의 부모 창 또는 `NULL` 드롭 다운 도구 모음 단추의 부모 창을 사용 하 여 합니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공 하면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 [CMFCDropDownToolbarButton::OnClick](#onclick) 메서드를 누르고 있을 때 사용자 도구 모음 단추 드롭 다운 도구 모음을 열려면이 메서드를 호출 합니다.  
  
 이 메서드를 사용 하 여 드롭다운 목록 도구 모음을 만듭니다는 [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) 메서드. 부모 도구 모음에서 세로로 도킹 되는 경우이 메서드는 배치 드롭 다운 도구 모음 왼쪽 또는 오른쪽 맞춤에 따라 부모 도구 모음 옆에 있습니다. 그렇지 않으면이 메서드는 부모 도구 모음 아래 드롭다운 목록 도구 모음을 배치 합니다.  
  
 이 메서드는 실패 하는 경우 `pWnd` 은 `NULL` 드롭 다운 도구 모음 단추에 부모 창 없는 합니다.  
  
##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton  
 도구 모음 단추에서 메뉴에 텍스트를 복사 합니다.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `menuButton`  
 대상 메뉴 단추에 대 한 참조입니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공하면 0이 아니고, 실패하면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 기본 클래스 구현을 호출 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) 하 고 대상 메뉴 단추에 추가 된 다음이 단추에 각 도구 모음 메뉴 항목이 포함 된 팝업 메뉴입니다. 이 메서드는 하위 메뉴 팝업 메뉴에 추가 하지 않습니다.  
  
 이 메서드는 실패 하는 경우 부모 도구 모음 `m_pToolBar`은 `NULL` 하거나 기본 클래스 구현을 반환 `FALSE`합니다.  
  
##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar  
 단추와 연결 된 드롭다운 도구 모음을 검색 합니다.  
  
```  
CMFCToolBar* GetDropDownToolBar() const;  
```  
  
### <a name="return-value"></a>반환 값  
 드롭 다운 도구 모음 단추와 연결 된입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 반환 된 `m_pToolBar` 데이터 멤버입니다.  
  
##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown  
 드롭다운 도구 모음이 현재 열려 있는지 여부를 결정 합니다.  
  
```  
BOOL IsDropDown() const;  
```  
  
### <a name="return-value"></a>반환 값  
 드롭다운 도구 모음이 현재 열려 있습니다. 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 프레임 워크를 사용 하 여 드롭다운 도구 모음이 열립니다는 [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) 메서드. 사용자가 드롭다운 도구 모음이의 비클라이언트 영역에서 마우스 왼쪽 단추를 누를 때 프레임 워크 드롭다운 도구 모음이 닫습니다.  
  
##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize  
 단추가 확장된 테두리 함께 표시 될 수 있는지 여부를 결정 합니다.  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>반환 값  
 확장 된 테두리가; 도구 모음 단추를 표시할 수 있으면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 확장 된 테두리에 대 한 자세한 내용은 참조 [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)합니다.  
  
##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay  
 드롭다운 도구 모음이 표시 될 때까지 사용자를 마우스 단추를 누른 해야 하는 시간의 길이 지정 합니다.  
  
```  
static UINT m_uiShowBarDelay;  
```  
  
### <a name="remarks"></a>설명  
 지연 시간은 밀리초 단위로 측정 됩니다. 기본값은 500입니다. 이 공유 데이터 멤버의 값을 변경 하 여 다른 지연을 설정할 수 있습니다.  
  
##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize  
 지정 된 장치 컨텍스트와 도킹 상태에 대 한 단추 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pDC`  
 단추를 표시 하는 장치 컨텍스트.  
  
 [in] `sizeDefault`  
 단추의 기본 크기입니다.  
  
 [in] `bHorz`  
 부모 도구 모음 도킹 상태입니다. 이 매개 변수는 `TRUE` 경우 도구 모음에서 가로로 도킹 되어 있거나 부동 창인 경우 또는 `FALSE` 도구 모음 세로로 도킹 되는 경우.  
  
### <a name="return-value"></a>반환 값  
 A `SIZE` 픽셀 단위로 단추의 크기를 포함 하는 구조입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 기본 클래스 구현을 확장 ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) 드롭 다운 화살표 너비 단추 크기의 가로 크기를 추가 하 여 합니다.  
  
##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd  
 새 도구 모음에 단추를 삽입할 때 프레임 워크에서 호출 됩니다.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pWndParent`  
 새 부모 창입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 기본 클래스 구현을 재정의 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 텍스트 레이블의 선택을 취소 하 여 ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) 설정의 [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) 및 [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) 데이터 멤버를 `FALSE`합니다.  
  
##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick  
 사용자가 마우스 단추를 클릭할 때 프레임 워크에서 호출 됩니다.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pWnd`  
 도구 모음 단추의 부모 창입니다.  
  
 [in] `bDelay`  
 `TRUE` 경우 메시지는 지연으로 처리 되어야 합니다.  
  
### <a name="return-value"></a>반환 값  
 단추 클릭 하 여 메시지를 처리 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드가 기본 클래스 구현을 확장 [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), 드롭 다운 도구 모음 상태를 업데이트 하 여 합니다.  
  
 이 메서드가 만드는 길이에 지정 된 시간을 대기 하는 타이머를 사용자가 도구 모음 단추를 클릭 하면는 [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) 데이터 멤버와는 를사용하여도구모음열립니다드롭다운[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) 메서드. 이 메서드는 사용자가 도구 모음 단추를 클릭 한 번 드롭다운 도구 모음이 닫습니다.  
  
##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp  
 사용자가 마우스 단추를 놓을 때 프레임 워크에서 호출 됩니다.  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>반환 값  
 단추 클릭 하 여 메시지를 처리 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드가 기본 클래스 구현을 확장 [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), 드롭 다운 도구 모음 상태를 업데이트 하 여 합니다.  
  
 이 메서드는 활성 상태 이면 드롭다운 도구 모음이 타이머를 중지 합니다. 열려 있는 경우에 드롭다운 도구 모음을 닫습니다.  
  
 도구 모음 드롭다운 목록 및 드롭다운 도구 모음이 타이머에 대 한 자세한 내용은 참조 [CMFCDropDownToolbarButton::OnClick](#onclick)합니다.  
  
##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp  
 부모 도구 모음에서 처리 될 때 프레임 워크에서 호출 된 `WM_HELPHITTEST` 메시지입니다.  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pWnd`  
 도구 모음 단추의 부모 창입니다.  
  
### <a name="return-value"></a>반환 값  
 단추 도움말 메시지를 처리 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 기본 클래스 구현을 확장 ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp))를 호출 하 여는 [CMFCDropDownToolbarButton::OnClick](#onclick) 메서드 `bDelay` 로 설정 `FALSE` . 이 메서드가 반환 하 여 반환 되는 값 [CMFCDropDownToolbarButton::OnClick](#onclick)합니다.  
  
 에 대 한 자세한 내용은 `WM_HELPHITTEST message, see` [TN028: 상황에 맞는 도움말 지원](../../mfc/tn028-context-sensitive-help-support.md)합니다.  
  
##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu  
 부모 도구 모음 바로 가기 메뉴를 표시 하는 응용 프로그램 때 제공 된 메뉴를 수정 합니다.  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pMenu`  
 사용자 지정 하는 메뉴.  
  
### <a name="return-value"></a>반환 값  
 이 메서드는 `TRUE`을 반환합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 기본 클래스 구현을 확장 ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) 다음과 같은 메뉴 항목이 비활성화 하 여:  
  
- **단추 이미지 복사**  
  
- **단추 모양**  
  
- **Image**  
  
- **텍스트**  
  
- **이미지 및 텍스트**  
  
 사용자 지정 모드에는 프레임 워크가 표시 하는 바로 가기 메뉴를 수정 하려면이 메서드를 재정의 합니다.  
  
##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw  
 지정 된 스타일 및 옵션을 사용 하 여 단추를 그리기 위해 프레임 워크에서 호출 됩니다.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pDC`  
 단추를 표시 하는 장치 컨텍스트.  
  
 [in] `rect`  
 단추의 경계 사각형입니다.  
  
 [in] `pImages`  
 단추와 연결 된 도구 모음 이미지의 컬렉션입니다.  
  
 [in] `bHorz`  
 부모 도구 모음 도킹 상태입니다. 이 매개 변수는 `TRUE` 단추를 가로로 도킹 되어 및 `FALSE` 단추 세로로 도킹 된 경우.  
  
 [in] `bCustomizeMode`  
 도구 모음 사용자 지정 모드에 있는지 여부를 지정 합니다. 이 매개 변수는 `TRUE` 도구 모음 사용자 지정 모드 중인 하는 경우 및 `FALSE` 는 도구 모음이 사용자 지정 모드 없는 합니다.  
  
 [in] `bHighlight`  
 단추가 강조 표시 하는지 여부를 지정 합니다. 이 매개 변수는 `TRUE` 단추가 강조 표시 된 및 `FALSE` 때 단추가 강조 표시 되지 않습니다.  
  
 [in] `bDrawBorder`  
 단추 테두리를 표시할지 여부를 지정 합니다. 이 매개 변수는 `TRUE` 때 단추 테두리를 표시할지 및 `FALSE` 단추 테두리를 표시 하지 않아야 합니다.  
  
 [in] `bGrayDisabledButtons`  
 비활성화 된 단추 지정 하거나 비활성화 된 이미지 컬렉션을 사용할 것인지 지정 합니다. 이 매개 변수는 `TRUE` 때 비활성화 된 단추가 회색으로 표시 됩니다 및 `FALSE` 이 메서드는 비활성화 된 이미지 컬렉션을 사용 해야 합니다.  
  
### <a name="remarks"></a>설명  
 도구 모음 단추 그리기를 사용자 지정 하려면이 메서드를 재정의 합니다.  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList  
 단추를 그리기 위해 프레임 워크에서 호출 된 **명령을** 의 창은 **사용자 지정** 대화 상자.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pDC`  
 단추를 표시 하는 장치 컨텍스트.  
  
 [in] `rect`  
 단추의 경계 사각형입니다.  
  
 [in] `bSelected`  
 단추가 선택 되었는지 여부를 나타냅니다. 이 매개 변수가 `TRUE`, 단추가 선택 되어 있습니다. 이 매개 변수가 `FALSE`, 단추를 선택 하지 않으면 합니다.  
  
### <a name="return-value"></a>반환 값  
 지정된 된 디바이스 컨텍스트에서 단추의 픽셀 너비입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 사용자 지정 대화 상자 ( **명령을** 탭) 소유자 그리기 목록 상자에 표시 되도록 하는 단추가 필요한 경우.  
  
 이 메서드는 기본 클래스 구현을 확장 ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) 단추의 텍스트 레이블을 단추의 이름을 변경 하 여 (즉, 값에는 `lpszName` 전달 된 매개 변수 생성자).  
  
##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize  
 보관 파일에서이 개체를 읽거나 보관 파일에 씁니다.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `ar`  
 `CArchive` 개체를 serialize 또는입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 기본 클래스 구현을 확장 ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) 부모 도구 모음에서의 리소스 ID를 직렬화 하 여 합니다. 보관 파일을 로드 하는 경우 ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) 0이 아닌 값을 반환)를 설정 하는이 메서드는 `m_pToolBar` 직렬화 된 리소스 ID를 포함 하는 도구 모음에 데이터 멤버  
  
##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand  
 단추를 클릭할 때 프레임 워크를 사용 하는 기본 명령을 설정 합니다.  
  
```  
void SetDefaultCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `uiCmd`  
 기본 명령의 ID입니다.  
  
### <a name="remarks"></a>설명  
 사용자가 단추를 클릭할 때 프레임 워크가 실행 하는 기본 명령을 지정 하려면이 메서드를 호출 합니다. 지정한 명령 ID 가진 항목이 `uiCmd` 부모 드롭 다운 도구 모음에 있어야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar 클래스](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarMenuButton 클래스](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)



