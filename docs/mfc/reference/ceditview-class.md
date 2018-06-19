---
title: CEditView 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
dev_langs:
- C++
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b15d604670ec1c458c6ca8db5b3b4eab51fb8f65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371545"
---
# <a name="ceditview-class"></a>CEditView 클래스
Windows 편집 컨트롤의 기능을 제공하고 간단한 텍스트 편집기 기능을 구현하는 데 사용할 수 있는 뷰 클래스의 유형입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CEditView : public CCtrlView  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CEditView::CEditView](#ceditview)|`CEditView` 형식의 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CEditView::FindText](#findtext)|텍스트 내에서 문자열을 검색 합니다.|  
|[CEditView::GetBufferLength](#getbufferlength)|문자 버퍼의 길이 가져옵니다.|  
|[CEditView::GetEditCtrl](#geteditctrl)|에 대 한 액세스를 제공 된 `CEdit` 부분의 `CEditView` 개체 (Windows 편집 컨트롤).|  
|[CEditView::GetPrinterFont](#getprinterfont)|현재 프린터 글꼴을 검색합니다.|  
|[CEditView::GetSelectedText](#getselectedtext)|현재 선택 된 텍스트를 검색합니다.|  
|[CEditView::LockBuffer](#lockbuffer)|버퍼를 잠급니다.|  
|[CEditView::PrintInsideRect](#printinsiderect)|지정 된 사각형 내에 텍스트를 렌더링합니다.|  
|[CEditView::SerializeRaw](#serializeraw)|직렬화는 `CEditView` 원시 텍스트도 디스크에는 개체입니다.|  
|[CEditView::SetPrinterFont](#setprinterfont)|새 프린터 글꼴을 설정합니다.|  
|[CEditView::SetTabStops](#settabstops)|설정 탭 인쇄와 화면 표시에 대 한 위치입니다.|  
|[CEditView::UnlockBuffer](#unlockbuffer)|버퍼의 잠금을 해제 합니다.|  
  
### <a name="protected-methods"></a>Protected 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|텍스트 문자열의 다음 항목을 찾습니다.|  
|[CEditView::OnReplaceAll](#onreplaceall)|지정된 된 문자열의 모든 항목을 새 문자열을 바꿉니다.|  
|[CEditView::OnReplaceSel](#onreplacesel)|현재 선택 영역을 바꿉니다.|  
|[CEditView::OnTextNotFound](#ontextnotfound)|모든 추가 텍스트와 일치 하도록 찾기 작업이 실패 하면 호출 됩니다.|  
  
### <a name="public-data-members"></a>공용 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|기본 형식의 개체에 대 한 스타일 **CEditView 합니다.**|  
  
## <a name="remarks"></a>설명  
 `CEditView` 클래스는 다음과 같은 추가 기능을 제공 합니다.  
  
-   인쇄 합니다.  
  
-   찾기 및 바꾸기.  
  
 때문에 클래스 `CEditView` 클래스 파생 `CView`, 클래스의 개체 `CEditView` 문서 및 문서 템플릿을 사용할 수 있습니다.  
  
 각 `CEditView` 자체 글로벌 메모리 개체에 유지 되는 컨트롤의 텍스트입니다. 응용 프로그램에 개수에 관계 없이 점이 `CEditView` 개체입니다.  
  
 형식의 개체를 만들 `CEditView` 편집 창 위에 나열 된 기능을 추가 하려는 경우 또는 간단한 텍스트 편집기 기능을 사용 하려는 경우. A `CEditView` 개체 창의 전체 클라이언트 영역을 차지할 수 있습니다. 사용자 고유의 클래스를 파생 `CEditView` 추가 하거나 기본 기능을 수정 하거나 문서 서식 파일에 추가할 수 있는 클래스를 선언 합니다.  
  
 클래스의 기본 구현은 `CEditView` 다음 명령 처리: **ID_EDIT_SELECT_ALL**, **ID_EDIT_FIND**, **ID_EDIT_REPLACE**, **ID_EDIT_REPEAT**, 및 **ID_FILE_PRINT**합니다.  
  
 기본 문자 제한을 `CEditView` 됩니다 (1024 \* 1024-1 = 1048575). 이 호출 하 여 변경할 수 있습니다는 **EM_LIMITTEXT** 함수는 기본 컨트롤을 편집 합니다. 그러나 한 제한은 운영 체제에 따라 다른 하 고 유형의 컨트롤 (단일 또는 여러 줄)를 편집 합니다. 이러한 제한에 대 한 자세한 내용은 참조 하십시오. [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)합니다.  
  
 컨트롤에서이 제한을 변경 하려면 재정의 `OnCreate()` 함수에 대 한 프로그램 `CEditView` 클래스 및 코드의 다음 줄을 삽입 합니다.  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 형식의 개체 `CEditView` (또는에서 파생 된 유형의 `CEditView`) 다음과 같은 제한 사항이 있습니다.  
  
- `CEditView` true를 구현 하지 않는 나타나는 며 (WYSIWYG)을 편집 합니다. 선택 하는 화면에 가독성 및 일치 하는 인쇄 출력 간에 `CEditView` 화면 가독성을 높이기 위해 opts 합니다.  
  
- `CEditView` 단일 글꼴로 텍스트를 표시할 수 있습니다. 서식이 없는 특수 문자 지원 됩니다. 클래스 참조 [CRichEditView](../../mfc/reference/cricheditview-class.md) 큰 기능에 대 한 합니다.  
  
-   텍스트의 크기는 `CEditView` 포함 될 수 있습니다는 제한 됩니다. 에 대 한 동일한 제한은 `CEdit` 제어 합니다.  
  
 대 한 자세한 내용은 `CEditView`, 참조 [파생 된 뷰 클래스에서에서 사용할 수 있는 MFC](../../mfc/derived-view-classes-available-in-mfc.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxext.h  
  
##  <a name="ceditview"></a>  CEditView::CEditView  
 `CEditView` 형식의 개체를 생성합니다.  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>설명  
 호출 해야 개체를 생성 한 후의 [CWnd::Create](../../mfc/reference/cwnd-class.md#create) 편집 컨트롤을 사용 하기 전에 작동 합니다. 클래스를 파생 하는 경우 `CEditView` 사용 하 여 서식 파일에 추가 하려면 `CWinApp::AddDocTemplate`, 모두이 생성자를 호출 하는 프레임 워크 및 **만들기** 함수입니다.  
  
##  <a name="dwstyledefault"></a>  CEditView::dwStyleDefault  
 기본 스타일 포함는 `CEditView` 개체입니다.  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>설명  
 전달로이 정적 멤버는 `dwStyle` 의 매개 변수는 **만들기** 함수에 대 한 기본 스타일입니다.는 `CEditView` 개체입니다.  
  
##  <a name="findtext"></a>  CEditView::FindText  
 호출 된 `FindText` 함수가 검색할는 `CEditView` 개체의 텍스트 버퍼입니다.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszFind`  
 찾으려는 텍스트입니다.  
  
 `bNext`  
 검색의 방향을 지정합니다. 경우 **TRUE**, 검색 방향이 버퍼의 끝이 있습니다. 경우 **FALSE**, 버퍼의 시작 부분을 향해 검색 방향이 됩니다.  
  
 `bCase`  
 검색은 대/소문자 구분 여부를 지정 합니다. 경우 **TRUE**, 검색은 대/소문자 구분 합니다. 경우 **FALSE**, 검색은 대/소문자 구분 하지 않습니다.  
  
### <a name="return-value"></a>반환 값  
 검색 텍스트; 없으면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 함수는 지정 된 텍스트에 대 한 버퍼에서 텍스트를 검색 `lpszFind`에서 지정 된 방향에서 현재 선택 영역에서 시작 하는 `bNext`와로 지정 된 대/소문자 구분 `bCase`합니다. 텍스트가 검색 되는 경우 발견된 된 텍스트에는 선택 항목을 설정 하 고 0이 아닌 값을 반환 합니다. 텍스트 없으면 함수가 0을 반환 합니다.  
  
 일반적으로 않아도 호출 하 여 `FindText` 재정의 하지 않는 한 작동 `OnFindNext`, 되는 호출 `FindText`합니다.  
  
##  <a name="getbufferlength"></a>  CEditView::GetBufferLength  
 편집 컨트롤의 버퍼에 null 종결자를 포함 하지 않고 현재 있는 문자 수를 가져오려면이 함수를 호출 합니다.  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>반환 값  
 버퍼에 있는 문자열의 길이입니다.  
  
##  <a name="geteditctrl"></a>  CEditView::GetEditCtrl  
 호출 `GetEditCtrl` 편집 보기에서 사용 하는 편집 컨트롤에 대 한 참조를 얻으려고 합니다.  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>반환 값  
 `CEdit` 개체에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 이 컨트롤은 형식의 [CEdit](../../mfc/reference/cedit-class.md)사용 하 여 직접 Windows 편집 컨트롤을 조작할 수 있도록는 `CEdit` 멤버 함수입니다.  
  
> [!CAUTION]
>  사용 하는 `CEdit` 개체의 기본 창 상태를 변경 컨트롤을 편집할 수 있습니다. 사용 하 여 탭 설정을 변경 하면 안 되는 예를 들어는 [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) 때문에 작동 `CEditView` 편집 컨트롤 및 인쇄에 사용 하기 위해 이러한 설정을 캐시 합니다. 대신를 사용 하 여 [CEditView::SetTabStops](#settabstops)합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>  CEditView::GetPrinterFont  
 호출 `GetPrinterFont` 에 포인터를 얻으려면는 [CFont](../../mfc/reference/cfont-class.md) 현재 프린터 글꼴을 설명 하는 개체입니다.  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 `CFont` 현재 프린터 글꼴;를 지정 하는 개체 **NULL** 프린터 글꼴을 설정 하지 않은 경우. 해당 포인터는 임시적이며, 나중에 사용하려고 저장하면 안됩니다.  
  
### <a name="remarks"></a>설명  
 경우 프린터 글꼴 설정 되지 않았습니다, 기본 동작을 인쇄는 `CEditView` 클래스 표시 하기 위해 사용 되는 동일한 글꼴을 사용 하 여 인쇄 하는 것입니다.  
  
 이 함수를 사용 하 여 현재 프린터 글꼴을 결정 합니다. 사용 하 여 원하는 프린터 글꼴 아니라면 [CEditView::SetPrinterFont](#setprinterfont) 변경할 수 있습니다.  
  
##  <a name="getselectedtext"></a>  CEditView::GetSelectedText  
 호출 `GetSelectedText` 선택한 텍스트를 복사 하는 `CString` 선택 또는 선택 영역에 첫 번째 캐리지 리턴 문자 앞에 있는 문자의 끝까지 개체입니다.  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `strResult`  
 에 대 한 참조는 `CString` 선택한 텍스트를 수신 하는 개체입니다.  
  
##  <a name="lockbuffer"></a>  CEditView::LockBuffer  
 버퍼에 대 한 포인터를 가져오려면이 함수를 호출 합니다. 버퍼를 수정 하지 않아야 합니다.  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>반환 값  
 편집 컨트롤의 버퍼에 대 한 포인터입니다.  
  
##  <a name="onfindnext"></a>  CEditView::OnFindNext  
 로 지정 된 텍스트에 대 한 버퍼에서 텍스트를 검색 `lpszFind`로 지정 된 방향의 `bNext`, 대/소문자 구분 하 여 지정 된 `bCase`합니다.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszFind`  
 찾으려는 텍스트입니다.  
  
 `bNext`  
 검색의 방향을 지정합니다. 경우 **TRUE**, 검색 방향이 버퍼의 끝이 있습니다. 경우 **FALSE**, 버퍼의 시작 부분을 향해 검색 방향이 됩니다.  
  
 `bCase`  
 검색은 대/소문자 구분 여부를 지정 합니다. 경우 **TRUE**, 검색은 대/소문자 구분 합니다. 경우 **FALSE**, 검색은 대/소문자 구분 하지 않습니다.  
  
### <a name="remarks"></a>설명  
 검색이 현재 선택 영역의 시작 부분에서 시작 되며 호출을 통해 수행 됩니다 [FindText](#findtext)합니다. 기본 구현에서 `OnFindNext` 호출 [OnTextNotFound](#ontextnotfound) 텍스트를 찾을 수 없는 경우.  
  
 재정의 `OnFindNext` 방식을 변경 하는 한 `CEditView`-파생 된 개체 텍스트를 검색 합니다. `CEditView` 호출 `OnFindNext` 표준 찾기 대화 상자에서 다음 찾기 단추를 선택 하면 됩니다.  
  
##  <a name="onreplaceall"></a>  CEditView::OnReplaceAll  
 `CEditView` 호출 `OnReplaceAll` 사용자가 모두 바꾸기 단추 표준 바꾸기 대화 상자에서 선택 합니다.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszFind`  
 찾으려는 텍스트입니다.  
  
 `lpszReplace`  
 검색 텍스트를 바꿀 텍스트입니다.  
  
 `bCase`  
 검색은 대/소문자 구분 여부를 지정 합니다. 경우 **TRUE**, 검색은 대/소문자 구분 합니다. 경우 **FALSE**, 검색은 대/소문자 구분 하지 않습니다.  
  
### <a name="remarks"></a>설명  
 `OnReplaceAll` 로 지정 된 텍스트에 대 한 버퍼에서 텍스트를 검색 `lpszFind`, 대/소문자 구분 하 여 지정 된 `bCase`합니다. 현재 선택의 시작 부분에서 검색이 시작 합니다. 검색 텍스트를 찾을 때마다가이 함수는로 지정 된 텍스트와 텍스트의 해당 항목을 대체 `lpszReplace`합니다. 검색에 대 한 호출을 통해 수행 됩니다 [FindText](#findtext)합니다. 기본 구현에서 [OnTextNotFound](#ontextnotfound) 텍스트를 찾을 수 없는 경우 호출 됩니다.  
  
 현재 선택 영역이 일치 하지 않는 경우 `lpszFind`, 선택 항목으로 지정 된 텍스트의 첫 번째 항목으로 업데이트 됩니다 `lpszFind` 및 대체 수행 되지 않습니다. 이렇게 하면 사용자 선택 바꿀 텍스트를 일치 하지 않을 때 수행 하려는 작업이 무엇 인지 확인 합니다.  
  
 재정의 `OnReplaceAll` 방식을 변경 하는 한 `CEditView`-파생 된 개체는 텍스트 문자열로 바꿉니다.  
  
##  <a name="onreplacesel"></a>  CEditView::OnReplaceSel  
 `CEditView` 호출 `OnReplaceSel` 표준 바꾸기 대화 상자에서 바꾸기 단추를 선택 하면 됩니다.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszFind`  
 찾으려는 텍스트입니다.  
  
 `bNext`  
 검색의 방향을 지정합니다. 경우 **TRUE**, 검색 방향이 버퍼의 끝이 있습니다. 경우 **FALSE**, 버퍼의 시작 부분을 향해 검색 방향이 됩니다.  
  
 `bCase`  
 검색은 대/소문자 구분 여부를 지정 합니다. 경우 **TRUE**, 검색은 대/소문자 구분 합니다. 경우 **FALSE**, 검색은 대/소문자 구분 하지 않습니다.  
  
 `lpszReplace`  
 검색된 텍스트를 바꿀 텍스트입니다.  
  
### <a name="remarks"></a>설명  
 선택 영역을 바꾼 후이 함수에 지정한 텍스트의 다음 위치에 대 한 버퍼에서 텍스트를 검색 `lpszFind`로 지정 된 방향의 `bNext`, 대/소문자 구분 하 여 지정 된 `bCase`합니다. 검색에 대 한 호출을 통해 수행 됩니다 [FindText](#findtext)합니다. 텍스트 없으면 [OnTextNotFound](#ontextnotfound) 호출 됩니다.  
  
 재정의 `OnReplaceSel` 방식을 변경 하는 한 `CEditView`-선택한 텍스트를 대체 하는 파생 된 개체입니다.  
  
##  <a name="ontextnotfound"></a>  CEditView::OnTextNotFound  
 Windows 함수를 호출 하는 기본 구현을 변경 하려면이 함수를 재정의 **MessageBeep**합니다.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszFind`  
 찾으려는 텍스트입니다.  
  
##  <a name="printinsiderect"></a>  CEditView::PrintInsideRect  
 호출 `PrintInsideRect` 으로 지정 된 사각형에 텍스트를 인쇄 하려면 *rectLayout*합니다.  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDC`  
 프린터 장치 컨텍스트에 대 한 포인터입니다.  
  
 *rectLayout*  
 에 대 한 참조는 [CRect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT 구조체](../../mfc/reference/rect-structure1.md) 텍스트를 렌더링할 인 사각형을 지정 합니다.  
  
 `nIndexStart`  
 첫 번째 문자를 렌더링할 수 버퍼 내의 인덱스입니다.  
  
 `nIndexStop`  
 마지막 문자 다음에 렌더링 되어야 하는 문자 버퍼 내의 인덱스입니다.  
  
### <a name="return-value"></a>반환 값  
 인쇄할 다음 문자 인덱스로 (즉, 마지막 문자 다음에 렌더링 하는 문자)입니다.  
  
### <a name="remarks"></a>설명  
 경우는 `CEditView` 컨트롤에는 스타일 **ES_AUTOHSCROLL**, 렌더링 사각형 내에서 텍스트가 줄 바꿈됩니다. 컨트롤에 스타일을 되어 **ES_AUTOHSCROLL**, 텍스트는 사각형의 오른쪽 가장자리에 맞게 잘립니다.  
  
 **rect.bottom** 의 요소는 *rectLayout* 개체가 되는 텍스트에 사용 되는 원래 사각형의 부분을 정의 하는 사각형의 크기를 변경 합니다.  
  
##  <a name="serializeraw"></a>  CEditView::SerializeRaw  
 호출 `SerializeRaw` 있어야는 `CArchive` 텍스트 쓰기 또는 읽기 개체의 `CEditView` 개체를 텍스트 파일입니다.  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>매개 변수  
 `ar`  
 에 대 한 참조는 `CArchive` 직렬화 된 텍스트를 저장 하는 개체입니다.  
  
### <a name="remarks"></a>설명  
 `SerializeRaw` 와 다른 `CEditView`의의 내부 구현 `Serialize` 한다는 점에서 읽고 없이 개체 설명 데이터 앞에 텍스트를 씁니다.  
  
##  <a name="setprinterfont"></a>  CEditView::SetPrinterFont  
 호출 `SetPrinterFont` 프린터 글꼴에 지정 된 글꼴을 설정 하려면 `pFont`합니다.  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>매개 변수  
 `pFont`  
 형식의 개체에 대 한 포인터 `CFont`합니다. 경우 **NULL**, 글꼴에 따라 인쇄에 사용 되는 글꼴입니다.  
  
### <a name="remarks"></a>설명  
 항상 인쇄를 위해 특정 글꼴을 사용 하 여 보기에 대 한 호출을 포함, `SetPrinterFont` 클래스의에서 `OnPreparePrinting` 함수입니다. 인쇄 발생 하기 전에이 가상 함수 호출 됩니다 글꼴 변경 되기 전에 발생 보기의 내용은 인쇄 됩니다.  
  
##  <a name="settabstops"></a>  CEditView::SetTabStops  
 표시 및 인쇄를 위해 사용 되는 탭 정지를 설정 하려면이 함수를 호출 합니다.  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>매개 변수  
 `nTabStops`  
 대화 상자 단위에서 각 탭 정지의 너비입니다.  
  
### <a name="remarks"></a>설명  
 탭 정지 너비만 지원 됩니다. ( `CEdit` 개체는 여러 탭 너비를 지원 합니다.) 너비는 인쇄 하거나 표시의 시간에 사용 되는 글꼴 (대문자 및 소문자 알파벳 문자만에 기반) 평균 문자 너비의 1 / 4 같은 대화 상자 단위 됩니다. 사용 하지 않아야 `CEdit::SetTabStops` 때문에 `CEditView` 탭 정지 값을 캐시 해야 합니다.  
  
 이 함수를 호출 하는 개체의 탭만 수정 합니다. 탭을 변경 하려면 각각에 대 한 중지 `CEditView` 응용 프로그램에서 개체를 호출 하는 각 개체의 `SetTabStops` 함수입니다.  
  
### <a name="example"></a>예제  
 이 코드 조각은 컨트롤이 차지 하는 글꼴을 신중 하 게 측정 하 여 모든 4 번째 문자를 컨트롤의 탭 정지를 설정 합니다.  
  
 [!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>  CEditView::UnlockBuffer  
 버퍼의 잠금을 해제 하려면이 함수를 호출 합니다.  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>설명  
 호출 `UnlockBuffer` 에서 반환 된 포인터를 사용 하 여 완료 한 후 [LockBuffer](#lockbuffer)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [MFC 샘플 SUPERPAD](../../visual-cpp-samples.md)   
 [CCtrlView 클래스](../../mfc/reference/cctrlview-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CEdit 클래스](../../mfc/reference/cedit-class.md)   
 [CDocument 클래스](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)   
 [CCtrlView 클래스](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView 클래스](../../mfc/reference/cricheditview-class.md)
