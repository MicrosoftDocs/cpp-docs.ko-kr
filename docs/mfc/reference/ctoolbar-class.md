---
title: "CToolBar 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
dev_langs:
- C++
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dec2dac93dae9860dfadd347584fbdf465d15838
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="ctoolbar-class"></a>CToolBar 클래스
비트맵 단추의 행과 구분 기호(선택 사항)가 있는 컨트롤 막대입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CToolBar : public CControlBar  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CToolBar::CToolBar](#ctoolbar)|`CToolBar` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](#commandtoindex)|지정한 명령 id는 단추의 인덱스를 반환합니다.|  
|[CToolBar::Create](#create)|Windows 도구 모음을 만들고에 연결 된 `CToolBar` 개체입니다.|  
|[CToolBar::CreateEx](#createex)|만듭니다는 `CToolBar` 개체는 포함 된 항목에 대 한 추가 스타일으로 `CToolBarCtrl` 개체입니다.|  
|[CToolBar::GetButtonInfo](#getbuttoninfo)|ID, 스타일 및 단추의 이미지 수를 검색합니다.|  
|[CToolBar::GetButtonStyle](#getbuttonstyle)|단추에 대 한 스타일을 검색합니다.|  
|[CToolBar::GetButtonText](#getbuttontext)|단추에 표시 될 텍스트를 검색 합니다.|  
|[CToolBar::GetItemID](#getitemid)|단추를 클릭 하거나 지정된 된 인덱스에서 구분 기호의 명령 ID를 반환합니다.|  
|[CToolBar::GetItemRect](#getitemrect)|지정된 된 인덱스에서 항목에 대 한 표시 사각형을 검색합니다.|  
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|기본 공용 컨트롤에 직접 액세스할을 수 있습니다.|  
|[CToolBar::LoadBitmap](#loadbitmap)|비트맵 단추 이미지를 포함 하는 비트맵을 로드 합니다.|  
|[CToolBar::LoadToolBar](#loadtoolbar)|리소스 편집기를 사용 하 여 만든 도구 모음 리소스를 로드 합니다.|  
|[CToolBar::SetBitmap](#setbitmap)|비트맵 이미지를 설정합니다.|  
|[CToolBar::SetButtonInfo](#setbuttoninfo)|ID, 스타일 및 단추의 이미지 수를 설정합니다.|  
|[CToolBar::SetButtons](#setbuttons)|단추 스타일과의 비트맵 단추 이미지 인덱스를 설정 합니다.|  
|[CToolBar::SetButtonStyle](#setbuttonstyle)|단추에 대 한 스타일을 설정합니다.|  
|[CToolBar::SetButtonText](#setbuttontext)|단추에 표시 될 텍스트를 설정 합니다.|  
|[CToolBar::SetHeight](#setheight)|도구 모음의 높이 설정합니다.|  
|[CToolBar::SetSizes](#setsizes)|단추와 해당 비트맵의 크기를 설정합니다.|  
  
## <a name="remarks"></a>설명  
 단추는 누름 단추, 확인란 단추 또는 라디오 단추 처럼 작동할 수 있습니다. `CToolBar`개체는 일반적으로 포함 된 클래스에서 파생 되는 프레임 창 개체 멤버 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 또는 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)합니다.  
  
 [CToolBar::GetToolBarCtrl](#gettoolbarctrl), 멤버 함수 새 MFC 4.0 허용 도구 모음 사용자 지정 및 추가 기능에 대 한 Windows 공용 컨트롤 지원 기능을 사용할 수 있습니다. `CToolBar`멤버 함수는 대부분의 Windows 공용 컨트롤; 기능 제공. 그러나 호출 하는 경우 `GetToolBarCtrl`, 도구 모음을 Windows 95/98 도구 모음의 특징 중 이상용으로 지정할 수 있습니다. 호출 하는 경우 `GetToolBarCtrl`에 대 한 참조를 반환 합니다는 `CToolBarCtrl` 개체입니다. 참조 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) Windows 공용 컨트롤을 사용 하 여 도구 모음을 디자인 하는 방법에 대 한 자세한 내용은 합니다. 공용 컨트롤에 대 한 자세한 내용은 참조 하십시오. [공용 컨트롤](http://msdn.microsoft.com/library/windows/desktop/bb775493) Windows sdk에서입니다.  
  
 Visual c + + 도구 모음을 만들려면 두 가지 방법을 제공 합니다. 리소스 편집기를 사용 하 여 도구 모음 리소스를 만들려면 다음이 단계를 수행 합니다.  
  
1.  도구 모음 리소스를 만듭니다.  
  
2.  `CToolBar` 개체를 생성합니다.  
  
3.  호출 된 [만들기](#create) (또는 [CreateEx](#createex)) Windows 도구 모음을 만들고에 연결 하는 함수는 `CToolBar` 개체입니다.  
  
4.  호출 [LoadToolBar](#loadtoolbar) 도구 모음 리소스를 로드할 수 있습니다.  
  
 그렇지 않으면 다음이 단계를 따르십시오.  
  
1.  `CToolBar` 개체를 생성합니다.  
  
2.  호출 된 [만들기](#create) (또는 [CreateEx](#createex)) Windows 도구 모음을 만들고에 연결 하는 함수는 `CToolBar` 개체입니다.  
  
3.  호출 [LoadBitmap](#loadbitmap) 도구 모음 단추 이미지를 포함 하는 비트맵을 로드 합니다.  
  
4.  호출 [SetButtons](#setbuttons) 단추 스타일을 설정 하는 비트맵의 이미지와 함께 각 단추를 연결 합니다.  
  
 도구 모음에서 모든 단추 이미지 각 단추에 대 한 이미지를 포함 해야 하는 하나의 비트맵에서 가져옵니다. 모든 이미지 크기가; 같아야 함 기본값이 16 픽셀 너비 및 높이가 15 픽셀입니다. 이미지는 비트맵에서 나란히 여야 합니다.  
  
 `SetButtons` 함수는 배열의 요소 수를 지정 하는 정수 및 컨트롤 Id의 배열에 대 한 포인터를 사용 합니다. 각 단추의 ID를 배열에는 해당 요소의 값으로 설정 하 고 각 단추 비트맵에서 단추의 이미지의 위치를 지정 하는 이미지 인덱스를 지정 하는 합니다. 배열 요소 값이 경우 **ID_SEPARATOR**, 이미지 인덱스가 없는 할당 됩니다.  
  
 비트맵에서 이미지의 순서는 일반적으로 순서는 화면에서 그릴 하지만 사용할 수 있습니다는 [SetButtonInfo](#setbuttoninfo) 함수 그리기 순서 이미지 order 간의 관계를 변경할 수 있습니다.  
  
 모든 단추는 도구 모음에는 크기가 동일 합니다. 기본값에 따라 24x22 픽셀은 *소프트웨어 디자인에 대 한 Windows 인터페이스 지침*합니다. 이미지 및 단추 차원 사이의 모든 추가 공간이 이미지 주위에 테두리를 만드는 데 사용 됩니다.  
  
 각 단추에는 하나의 이미지를 있습니다. 여러 단추 상태 및 스타일이 (누름된 up, 위로, 사용 안 함, 아래쪽, 사용 안 함 및 확인할 수 없는) 하나의 해당 이미지에서 생성 됩니다. 비트맵에서 색을 사용할 수 있지만 흑백 회색 음영 인 이미지와 함께 최상의 결과 얻을 수 있습니다.  
  
> [!WARNING]
> `CToolBar`최대 16 개의 색 비트맵을 지원합니다. 도구 모음 편집기에 이미지를 로드 Visual Studio가 자동으로 필요한 경우 이미지는 16 색 비트맵에 변환 및 이미지 변환 된 경우 경고 메시지를 표시 합니다. 이미지 (이미지를 편집 하는 외부 편집기 사용) 하는 16 개 색을 사용 하면 응용 프로그램이 예기치 않게 동작할 수 있습니다.  
  
 도구 모음 단추는 기본적으로 누름 단추를 모방 합니다. 그러나 확인란 단추 또는 라디오 단추 도구 모음 단추 모방 수도 있습니다. 확인란 단추는 세 가지 상태: 확인 된 지워지고 비활성화 상태입니다. 라디오 단추 두 가지 상태: 되 고 비활성화 합니다.  
  
 배열을 가리키는 없이 개별 단추 또는 구분 기호 스타일을 설정 하려면 호출 [GetButtonStyle](#getbuttonstyle) 스타일을 검색 한 다음 호출 하 [SetButtonStyle](#setbuttonstyle) 대신 `SetButtons`합니다. `SetButtonStyle`런타임 시 단추의 스타일을 변경 하려는 경우 가장 유용 합니다.  
  
 단추에 표시할 텍스트를 할당 하려면 호출 [GetButtonText](#getbuttontext) 을 단추에 다음 텍스트를 검색할 [SetButtonText](#setbuttontext) 텍스트를 설정 합니다.  
  
 확인란 단추를 만들려면 할당 스타일 **TBBS_CHECKBOX** 하거나 사용 하 여는 `CCmdUI` 개체의 `SetCheck` 에서 멤버 함수는 `ON_UPDATE_COMMAND_UI` 처리기입니다. 호출 `SetCheck` 확인란 단추 누름 단추로 바뀝니다. 전달 `SetCheck` 인수가 0 선택 또는 2에 대 한 옵션을 선택 취소 1에 대 한에 대 한 비활성화 상태입니다.  
  
 라디오 단추를 만들려면 호출는 [CCmdUI](../../mfc/reference/ccmdui-class.md) 개체의 [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) 에서 멤버 함수는 `ON_UPDATE_COMMAND_UI` 처리기입니다. 전달 `SetRadio` 선택 되지 않은 또는 검사에 대 한 0이 아닌 인수를 0입니다. 라디오 그룹의 상호 배타적인 동작을 제공 하기 위해 있어야 `ON_UPDATE_COMMAND_UI` 모든 그룹의 단추에 대 한 처리기입니다.  
  
 사용 하 여 대 한 자세한 내용은 `CToolBar`, 문서를 참조 [MFC 도구 모음 구현](../../mfc/mfc-toolbar-implementation.md) 및 [Technical Note 31: 컨트롤 막대](../../mfc/tn031-control-bars.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxext.h  
  
##  <a name="commandtoindex"></a>CToolBar::CommandToIndex  
 이 멤버 함수는 첫 번째 도구 모음 단추를 위치 0에서 시작 명령 ID를 가진 일치 인덱스를 반환 합니다. `nIDFind`합니다.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `nIDFind`  
 도구 모음 단추의 명령 ID입니다.  
  
### <a name="return-value"></a>반환 값  
 단추나 없는 단추에 지정 된 명령 id입니다.-1의 인덱스  
  
##  <a name="create"></a>CToolBar::Create  
 이 멤버 함수 Windows 도구 모음 (자식 창)을 만들고 사용 하 여 연결 된 `CToolBar` 개체입니다.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>매개 변수  
 `pParentWnd`  
 도구 모음의 부모 창에 대 한 포인터입니다.  
  
 `dwStyle`  
 도구 모음 스타일입니다. 지원 되는 추가 도구 모음 스타일은  
  
- `CBRS_TOP`컨트롤 막대 프레임 창의 위쪽에입니다.  
  
- `CBRS_BOTTOM`컨트롤 막대 프레임 창 맨 아래에입니다.  
  
- `CBRS_NOALIGN`부모 크기를 조정할 때 컨트롤 막대 위치가 변경 되지 않습니다.  
  
- `CBRS_TOOLTIPS`컨트롤 막대에는 도구 설명을 표시합니다.  
  
- **CBRS_SIZE_DYNAMIC** 동적 컨트롤 막대입니다.  
  
- **CBRS_SIZE_FIXED** 컨트롤 막대 고정 됩니다.  
  
- **CBRS_FLOATING** 컨트롤 막대 부동 합니다.  
  
- `CBRS_FLYBY`상태 표시줄 단추에 대 한 정보를 표시합니다.  
  
- **CBRS_HIDE_INPLACE** 컨트롤 막대 사용자에 게 표시 되지 않습니다.  
  
 `nID`  
 도구 모음의 자식 창 id입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 또한 도구 모음 높이 기본값으로 설정합니다.  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]  
  
##  <a name="createex"></a>CToolBar::CreateEx  
 Windows 도구 모음 (자식 창)을 만들고 사용 하 여 연결 하려면이 함수를 호출 하 여 `CToolBar` 개체입니다.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = TBSTYLE_FLAT,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,  
    CRect rcBorders = CRect(
    0, 
    0, 
    0, 
    0), 
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>매개 변수  
 `pParentWnd`  
 도구 모음의 부모 창에 대 한 포인터입니다.  
  
 `dwCtrlStyle`  
 포함된 된 생성에 대 한 추가 스타일 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 개체입니다. 기본적으로이 값 설정 **TBSTYLE_FLAT**합니다. 도구 모음 스타일의 전체 목록은 참조 하십시오. `dwStyle`합니다.  
  
 `dwStyle`  
 도구 모음 스타일입니다. 참조 [도구 모음 컨트롤과 단추 스타일](http://msdn.microsoft.com/library/windows/desktop/bb760439) 적절 한 스타일의 목록을 Windows sdk입니다.  
  
 *rcBorders*  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) 도구 모음 창 테두리의 너비를 정의 하는 개체입니다. 이러한 테두리는 기본적으로 테두리가 없는 도구 모음 창에 그 결과로 0,0,0,0으로 설정 됩니다.  
  
 `nID`  
 도구 모음의 자식 창 id입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 또한 도구 모음 높이 기본값으로 설정합니다.  
  
 사용 하 여 `CreateEx`, 대신 [만들기](#create)포함 된 도구 모음 컨트롤을 만들 때 특정 스타일 있어야 하는 경우. 예를 들어 설정 `dwCtrlStyle` 를 **TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT** Internet Explorer 4 도구 모음 유사한 도구 모음을 만들려면 합니다.  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]  
  
##  <a name="ctoolbar"></a>CToolBar::CToolBar  
 이 멤버 함수를 생성 한 `CToolBar` 개체를 기본 크기를 설정 합니다.  
  
```  
CToolBar();
```  
  
### <a name="remarks"></a>설명  
 호출 된 [만들기](#create) 멤버 함수를 만드는 도구 모음 창.  
  
##  <a name="getbuttoninfo"></a>CToolBar::GetButtonInfo  
 이 멤버 함수는 컨트롤 ID, 스타일 및 도구 모음 단추 또는 지정 된 위치에 구분의 이미지 인덱스 검색 *nIndex 합니다.*  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 도구 모음 단추 또는 구분 기호 정보를 검색할 수는 인덱스입니다.  
  
 `nID`  
 에 대 한 참조는 **UINT** 단추의 명령 ID로 설정 되어 있는 합니다.  
  
 `nStyle`  
 에 대 한 참조는 **UINT** 단추의 스타일으로 설정 되어 있는 합니다.  
  
 `iImage`  
 비트맵 내 단추의 이미지의 인덱스를 설정 하는 정수에 대 한 참조입니다.  
  
### <a name="remarks"></a>설명  
 해당 값에서 참조 변수에 할당 된 `nID`, `nStyle`, 및 `iImage`합니다. 이미지 인덱스는 모든 도구 모음 단추에 대 한 이미지를 포함 하는 비트맵 내 이미지의 위치입니다. 첫 번째 이미지는 0 위치에 있습니다.  
  
 경우 `nIndex` 는 구분 기호를 지정 `iImage` 구분 기호 너비 (픽셀)에서로 설정 됩니다.  
  
##  <a name="getbuttonstyle"></a>CToolBar::GetButtonStyle  
 단추 또는 도구 모음에서 구분 기호 스타일을 검색 하려면이 멤버 함수를 호출 합니다.  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 인덱스를 검색할 도구 모음 단추 또는 구분 기호 스타일입니다.  
  
### <a name="return-value"></a>반환 값  
 단추 또는 지정 된 구분 기호 스타일 `nIndex`합니다.  
  
### <a name="remarks"></a>설명  
 단추의 스타일 사용자 입력에 응답 하 고 단추가 표시 되는 방식을 결정 합니다. 참조 [SetButtonStyle](#setbuttonstyle) 단추 스타일에 대 한 예제입니다.  
  
##  <a name="getbuttontext"></a>CToolBar::GetButtonText  
 단추에 표시 되는 텍스트를 검색 하려면이 멤버 함수를 호출 합니다.  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 검색할 텍스트의 인덱스입니다.  
  
 `rString`  
 에 대 한 참조는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 검색할 텍스트를 포함 하는 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 A `CString` 단추 텍스트를 포함 하는 개체입니다.  
  
### <a name="remarks"></a>설명  
 이 멤버에 두 번째 형태 채우기 함수는 `CString` 문자열 텍스트와 함께 개체입니다.  
  
##  <a name="getitemid"></a>CToolBar::GetItemID  
 이 멤버 함수 단추를 클릭 하거나 지정 된 구분 기호 명령 ID를 반환 합니다. `nIndex`합니다.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 ID가 검색할 항목의 인덱스입니다.  
  
### <a name="return-value"></a>반환 값  
 단추 명령 ID로 지정 된 구분 기호 `nIndex`합니다.  
  
### <a name="remarks"></a>설명  
 구분 기호 반환 **ID_SEPARATOR**합니다.  
  
##  <a name="getitemrect"></a>CToolBar::GetItemRect  
 이 멤버 함수는 채웁니다는 `RECT` 에 주소가 포함 된 구조 `lpRect` 단추 또는 지정 된 구분 기호 좌표로 `nIndex`합니다.  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 인덱스를 검색할 수 있는 사각형 좌표는 항목 (단추 또는 구분 기호)입니다.  
  
 `lpRect`  
 주소는 [RECT](../../mfc/reference/rect-structure1.md) 항목의 좌표를 포함 하는 구조입니다.  
  
### <a name="remarks"></a>설명  
 좌표는 도구 모음의 왼쪽 위 모퉁이 기준으로 픽셀입니다.  
  
 사용 하 여 `GetItemRect` 콤보 상자나 기타 컨트롤으로 교체 하려면 구분의 좌표를 얻으려고 합니다.  
  
### <a name="example"></a>예  
  예를 참조 [CToolBar::SetSizes](#setsizes)합니다.  
  
##  <a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl  
 이 멤버 함수에는 기본 공용 컨트롤에 직접 액세스할을 수 있습니다.  
  
```  
CToolBarCtrl& GetToolBarCtrl() const;  
```  
  
### <a name="return-value"></a>반환 값  
 `CToolBarCtrl` 개체에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 사용 하 여 `GetToolBarCtrl` Windows 도구 모음 공용 컨트롤의 기능을 활용 하 고는 지원의 이용 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 도구 모음 사용자 지정에 대 한 제공 합니다.  
  
 공용 컨트롤을 사용 하는 방법에 대 한 자세한 내용은 문서 참조 [컨트롤](../../mfc/controls-mfc.md) 및 [공용 컨트롤](http://msdn.microsoft.com/library/windows/desktop/bb775493) Windows sdk에서입니다.  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]  
  
##  <a name="loadbitmap"></a>CToolBar::LoadBitmap  
 로 지정 된 비트맵을 로드 하려면이 함수를 호출 `lpszResourceName` 또는 `nIDResource`합니다.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszResourceName`  
 로드할 비트맵의 리소스 이름에 대 한 포인터입니다.  
  
 `nIDResource`  
 로드할 비트맵의 리소스 ID입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 비트맵 각 도구 모음 단추에 대 한 이미지를 포함 해야 합니다. 이미지 없는 경우 표준 크기 (16 픽셀 너비 및 높이가 15 픽셀)의 호출 [SetSizes](#setsizes) 단추 크기 및 해당 이미지를 설정할 수 있습니다.  
  
> [!WARNING]
> `CToolBar`최대 16 개의 색 비트맵을 지원합니다. 도구 모음 편집기에 이미지를 로드 Visual Studio가 자동으로 필요한 경우 이미지는 16 색 비트맵에 변환 및 이미지 변환 된 경우 경고 메시지를 표시 합니다. 이미지 (이미지를 편집 하는 외부 편집기 사용) 하는 16 개 색을 사용 하면 응용 프로그램이 예기치 않게 동작할 수 있습니다.  
  
##  <a name="loadtoolbar"></a>CToolBar::LoadToolBar  
 이 멤버 함수를 로드 하 여 지정 된 도구 모음 호출 `lpszResourceName` 또는 `nIDResource`합니다.  
  
```  
BOOL LoadToolBar(LPCTSTR lpszResourceName);  
BOOL LoadToolBar(UINT nIDResource);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszResourceName`  
 도구 모음의 로드할 리소스 이름에 대 한 포인터입니다.  
  
 `nIDResource`  
 로드할 도구 모음의 리소스 ID입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 참조 [도구 모음 편집기](../../windows/toolbar-editor.md) 에서 도구 모음 리소스를 만들기에 대 한 자세한 내용은 합니다.  
  
### <a name="example"></a>예  
  예를 참조 [CToolBar::CreateEx](#createex)합니다.  
  
##  <a name="setbitmap"></a>CToolBar::SetBitmap  
 도구 모음에 대 한 비트맵 이미지를 설정 하려면이 함수를 호출 합니다.  
  
```  
BOOL SetBitmap(HBITMAP hbmImageWell);
```  
  
### <a name="parameters"></a>매개 변수  
 *hbmImageWell*  
 연결 된 도구 모음 비트맵 이미지의 핸들입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 예를 들어 호출 `SetBitmap` 단추의 동작을 변경 하는 문서에 작업을 수행 하는 사용자 한 다음 비트맵 이미지를 변경 하려면.  
  
##  <a name="setbuttoninfo"></a>CToolBar::SetButtonInfo  
 단추의 명령 ID, 스타일 및 이미지 수를 설정 하려면이 함수를 호출 합니다.  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 단추 또는 구분 기호 정보를 설정할 수는 0부터 시작 인덱스입니다.  
  
 `nID`  
 단추의 명령 ID에 설정 된 값입니다.  
  
 `nStyle`  
 새 단추 스타일입니다. 다음 단추 스타일 지원 됩니다.  
  
- **TBBS_BUTTON** 표준 누름 단추입니다 (기본값)  
  
- **TBBS_SEPARATOR** 구분 기호  
  
- **TBBS_CHECKBOX** 자동 확인란 단추  
  
- **TBBS_GROUP** 단추 그룹의 시작을 표시  
  
- **TBBS_CHECKGROUP** 확인란 단추 그룹의 시작을 표시  
  
- **TBBS_DROPDOWN** 드롭다운 목록에서 단추를 만듭니다.  
  
- **TBBS_AUTOSIZE** 단추의 너비는 이미지의 크기가 아니라 단추의 텍스트를 기반으로 계산 됩니다.  
  
- **TBBS_NOPREFIX** 단추 텍스트 연관는 액셀러레이터 키 접두사는 없습니다.  
  
 `iImage`  
 비트맵 내 단추의 이미지에 대 한 새 인덱스입니다.  
  
### <a name="remarks"></a>설명  
 스타일 충족 하는 구분 기호, **TBBS_SEPARATOR**,이 함수에 저장 된 값 (픽셀)에서의 구분 기호 너비 설정 `iImage`합니다.  
  
> [!NOTE]
>  사용 하 여 단추 상태를 설정할 수도 있습니다는 `nStyle` 매개 변수 이지만 단추 상태에 의해 제어 되므로 [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) 사용 하 여 설정 상태 처리기를 모든 `SetButtonInfo` 다음 동안 손실 됩니다 유휴 처리 중입니다. 참조 [사용자 인터페이스 개체 업데이트 하는 방법을](../../mfc/how-to-update-user-interface-objects.md) 및 [TN031: 컨트롤 막대](../../mfc/tn031-control-bars.md) 자세한 정보에 대 한 합니다.  
  
 비트맵 이미지 및 단추에 대 한 내용은 참조는 [CToolBar](../../mfc/reference/ctoolbar-class.md) 개요 및 [CToolBar::LoadBitmap](#loadbitmap)합니다.  
  
##  <a name="setbuttons"></a>CToolBar::SetButtons  
 각 도구 모음 단추의 명령 ID 배열의 해당 요소에 지정 된 값으로 설정 하는이 멤버 함수 `lpIDArray`합니다.  
  
```  
BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpIDArray`  
 명령 Id의 배열에 대 한 포인터입니다. 것이 **NULL** 빈 단추를 할당할 수 있습니다.  
  
 `nIDCount`  
 가 가리키는 배열의 요소 수가 `lpIDArray`합니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 배열의 요소 값이 경우 **ID_SEPARATOR**, 구분 기호는 도구 모음의 해당 위치에 만들어집니다. 이 함수는 또한 각 단추 스타일을 설정 **TBBS_BUTTON** 과 각 구분 기호 스타일을 **TBBS_SEPARATOR**, 되며 각 단추 이미지 인덱스를 지정 합니다. 이미지 인덱스 비트맵 내 단추의 이미지의 위치를 지정합니다.  
  
 이 함수는 구분 기호에 대 한 이미지 인덱스를 할당 하지 않는 경우 비트맵의 구분 기호에 대해 설명 하기 위해 필요가 없습니다. 도구 모음에 위치 0에 단추가 경우 1, 3 및 위치 2, 비트맵에 위치 0, 1 및 2의 이미지에 대 한 구분 기호에 위치 0, 1, 3에 있는 단추 각각 할당 합니다.  
  
 경우 `lpIDArray` 은 **NULL**, 지정 된 항목 수에 대 한 공간을 할당 하는이 함수 `nIDCount`합니다. 사용 하 여 [SetButtonInfo](#setbuttoninfo) 각 항목의 특성을 설정 합니다.  
  
##  <a name="setbuttonstyle"></a>CToolBar::SetButtonStyle  
 단추 또는 구분 기호 또는 단추를 그룹 스타일을 설정 하려면이 멤버 함수를 호출 합니다.  
  
```  
void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 단추를 클릭 하거나 해당 정보를 설정 하는 구분 기호의 인덱스입니다.  
  
 `nStyle`  
 단추 스타일입니다. 다음 단추 스타일 지원 됩니다.  
  
- **TBBS_BUTTON** 표준 누름 단추입니다 (기본값)  
  
- **TBBS_SEPARATOR** 구분 기호  
  
- **TBBS_CHECKBOX** 자동 확인란 단추  
  
- **TBBS_GROUP** 단추 그룹의 시작을 표시  
  
- **TBBS_CHECKGROUP** 확인란 단추 그룹의 시작을 표시  
  
- **TBBS_DROPDOWN** 드롭다운 목록에서 단추를 만듭니다.  
  
- **TBBS_AUTOSIZE** 단추의 너비는 이미지의 크기가 아니라 단추의 텍스트를 기반으로 계산 됩니다  
  
- **TBBS_NOPREFIX** 단추 텍스트를 연결 된 액셀러레이터 키 접두사는 갖습니다.  
  
### <a name="remarks"></a>설명  
 단추의 스타일 사용자 입력에 응답 하 고 단추가 표시 되는 방식을 결정 합니다.  
  
 호출 하기 전에 `SetButtonStyle`, 호출 된 [GetButtonStyle](#getbuttonstyle) 멤버 함수를 단추 또는 구분 기호 스타일을 검색 합니다.  
  
> [!NOTE]
>  사용 하 여 단추 상태를 설정할 수도 있습니다는 `nStyle` 매개 변수 이지만 단추 상태에 의해 제어 되므로 [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) 사용 하 여 설정 상태 처리기를 모든 `SetButtonStyle` 다음 동안 손실 됩니다 유휴 처리 중입니다. 참조 [사용자 인터페이스 개체 업데이트 하는 방법을](../../mfc/how-to-update-user-interface-objects.md) 및 [TN031: 컨트롤 막대](../../mfc/tn031-control-bars.md) 자세한 정보에 대 한 합니다.  
  
##  <a name="setbuttontext"></a>CToolBar::SetButtonText  
 단추 텍스트를 설정 하려면이 함수를 호출 합니다.  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>매개 변수  
 `nIndex`  
 텍스트가 설정 되어야 하는 단추의 인덱스입니다.  
  
 `lpszText`  
 단추에 설정 될 텍스트를 가리킵니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="example"></a>예  
  예를 참조 [CToolBar::GetToolBarCtrl](#gettoolbarctrl)합니다.  
  
##  <a name="setheight"></a>CToolBar::SetHeight  
 도구 모음의 높이 (픽셀)에 지정 된 값으로 설정 하는이 멤버 함수 `cyHeight`합니다.  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>매개 변수  
 `cyHeight`  
 도구 모음의 픽셀 단위 높이입니다.  
  
### <a name="remarks"></a>설명  
 호출한 후 [SetSizes](#setsizes), 표준 도구 모음의 높이 재정의 하려면이 멤버 함수를 사용 합니다. 높이 너무 작은 경우 맨 아래에 있는 단추가 클리핑됩니다.  
  
 이 함수를 호출 하지 않은 경우 프레임 워크를 사용 하 여 단추의 크기 도구 모음의 높이 결정 합니다.  
  
##  <a name="setsizes"></a>CToolBar::SetSizes  
 도구 모음 단추에 지정 된 픽셀 단위로 크기를 설정 하려면이 함수를 호출 *sizeButton*합니다.  
  
```  
void SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>매개 변수  
 *sizeButton*  
 각 단추의 픽셀 크기입니다.  
  
 `sizeImage`  
 각 이미지의 픽셀 크기입니다.  
  
### <a name="remarks"></a>설명  
 `sizeImage` 매개 변수는 도구 모음 비트맵의 이미지를 픽셀 단위로 크기를 포함 해야 합니다. 차원 *sizeButton* 를 더한 이미지 너비에 추가 7 픽셀이 고 높이가 추가 6 픽셀 이어야 합니다. 또한이 함수에 맞게 단추 도구 모음의 높이 설정 합니다.  
  
 준수 하지 않는 도구 모음에 대해서만이 함수를 호출 *소프트웨어 디자인에 대 한 Windows 인터페이스 지침* 단추와 이미지 크기에 대 한 권장 사항입니다.  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]  
  
## <a name="see-also"></a>참고 항목  
 [MFC 샘플 CTRLBARS](../../visual-cpp-samples.md)   
 [MFC 샘플 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 샘플 DOCKTOOL](../../visual-cpp-samples.md)   
 [CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 클래스](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)
