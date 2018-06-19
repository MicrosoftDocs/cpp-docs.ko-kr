---
title: CKeyboardManager 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
dev_langs:
- C++
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b9d4aace502310836429ec8f8f9db74d7cf17ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369104"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager 클래스
주 프레임 창 및 자식 프레임 창에 대한 바로 가기 키 테이블을 관리합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CKeyboardManager : public CObject  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|||  
|-|-|  
|이름|설명|  
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|`CKeyboardManager` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|||  
|-|-|  
|이름|설명|  
|[CKeyboardManager::CleanUp](#cleanup)|바로 가기 키 테이블을 지웁니다.|  
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|지정 된 명령 및 창에 대 한 기본 바로 가기 키를 검색합니다.|  
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|액셀러레이터 키 테이블에서 키를 처리할지 여부를 결정 합니다.|  
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|인쇄 가능한 문자 인지를 나타냅니다.|  
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|메뉴 명령에 대 한 모든 바로 가기 키 또는 기본 바로 가기 키만 표시할지 여부를 나타냅니다.|  
|[CKeyboardManager::LoadState](#loadstate)|Windows 레지스트리에서 바로 가기 키 테이블을 로드합니다.|  
|[CKeyboardManager::ResetAll](#resetall)|응용 프로그램 리소스에서 바로 가기 키 테이블을 다시 로드합니다.|  
|[CKeyboardManager::SaveState](#savestate)|Windows 레지스트리에 바로 가기 키 테이블을 저장합니다.|  
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|모든 명령에 대 한 모든 바로 가기 키 또는 각 명령에 대 한 단일 바로 가기 키 프레임 워크가 표시 여부를 지정 합니다. 이 메서드는 하나의 연결 된 바로 가기 키가 있는 명령이 적용 되지 않습니다.|  
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|문자 위쪽 해당 레지스터를 변환 합니다.|  
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|새 바로 가기 키 테이블으로 바로 가기 키 테이블을 업데이트합니다.|  
  
## <a name="remarks"></a>설명  
 이 클래스의 멤버를 저장 및 Windows 레지스트리를 바로 가기 키 테이블을 로드 하 고, 템플릿을 사용 하 여 바로 가기 키 테이블을 업데이트할 수 있으며 프레임 창에는 명령에 대 한 기본 바로 가기 키를 찾을 있습니다. 또한는 `CKeyboardManager` 개체를 사용 하면 사용자에 게 바로 가기 키 표시 되는 방식을 제어할 수 있습니다.  
  
 만들지 마십시오는 `CKeyboardManager` 수동으로 개체입니다. 응용 프로그램의 프레임 워크에서 자동으로 생성 될 됩니다. 하지만 호출 해야 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) 응용 프로그램의 초기화 프로세스 동안 합니다. 응용 프로그램에 대 한 키보드 관리자에 대 한 포인터를 가져오려면, 호출 [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)합니다.  
  
## <a name="example"></a>예제  
 다음 예제에 대 한 포인터를 검색 하는 방법을 보여 줍니다는 `CKeyboardManager` 에서 개체는 `CWinAppEx` 클래스 및 메뉴 명령과 연결 된 모든 바로 가기 키를 표시 하는 방법입니다. 이 코드 조각은의 일부인는 [사용자 지정 페이지 샘플](../../visual-cpp-samples.md)합니다.  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxkeyboardmanager.h  
  
##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager  
 `CKeyboardManager` 개체를 생성합니다.  
  
```  
CKeyboardManager();
```  
  
### <a name="remarks"></a>설명  
 대부분의 경우에서 않아도 만들려는 `CKeyboardManager` 직접 합니다. 프레임 워크는 기본적으로 구독을 하나 만듭니다. 에 포인터를 얻으려면는 `CKeyboardManager`, 호출 [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)합니다. 하나 수동으로 만들면 경우 방법으로 초기화 해야 하면 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)합니다.  
  
##  <a name="cleanup"></a>  CKeyboardManager::CleanUp  
 해제 된 `CKeyboardManager` 리소스 모든 바로 가기 키 매핑을 지웁니다.  
  
```  
static void CleanUp();
```  
  
### <a name="remarks"></a>설명  
 바로 가기 키에 대 한 자세한 내용은 참조 [키보드 및 마우스 사용자 지정](../../mfc/keyboard-and-mouse-customization.md)합니다.  
  
 응용 프로그램 프레임 워크 중 응용 프로그램을 종료할 것을 자동으로 호출 하기 때문에 종료 될 때이 함수를 호출할 필요가 없습니다.  
  
##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator  
 지정 된 명령 및 창에 대 한 기본 바로 가기 키를 검색합니다.  
  
```  
static BOOL FindDefaultAccelerator(
    UINT uiCmd,  
    CString& str,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `uiCmd`  
 명령 ID입니다.  
  
 [out] `str`  
 `CString` 개체에 대한 참조입니다.  
  
 [in] `pWndFrame`  
 프레임 창에 대 한 포인터입니다.  
  
 [in] `bIsDefaultFrame`  
 프레임 창의 기본 프레임 창인지 여부를 지정 합니다.  
  
### <a name="return-value"></a>반환 값  
 바로 가기; 없으면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 지정 된 명령을 찾습니다 `uiCmd` 기본 바로 가기 키를 검색 합니다. 메서드는이 바로 가기 키와 연결 된 문자열을 사용 하 고 값을 씁니다는 `str` 매개 변수입니다.  
  
##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled  
 지정된 된 키가 처리 여부를 결정은 [CKeyboardManager 클래스](../../mfc/reference/ckeyboardmanager-class.md)합니다.  
  
```  
static BOOL __stdcall IsKeyHandled(
    WORD nKey,  
    BYTE fVirt,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] `nKey`|확인할 키입니다.|  
|[in] `fVirt`|바로 가기 키의 동작을 지정 합니다. 가능한 값 목록은 참조 [가속 구조](http://msdn.microsoft.com/library/windows/desktop/ms646340)합니다.|  
|[in] `pWndFrame`|프레임 창입니다. 이 메서드는이 프레임에서 바로 가기 키를 처리 하는지 여부를 결정 합니다.|  
|[in] `bIsDefaultFrame`|나타내는 부울 매개 변수 여부 `pWndFrame` 기본 프레임 창입니다.|  
  
### <a name="return-value"></a>반환 값  
 `TRUE` 바로 가기 키를 처리 하는 경우 합니다. `FALSE` 키가 처리 되지 않은 경우 또는 경우 `pWndFrame` 은 `NULL`합니다.  
  
### <a name="remarks"></a>설명  
 입력된 매개 변수는 액셀러레이터 키 테이블에 모두에 대 한 항목과 일치 해야 함 `nKey` 및 `fVirt` 에 바로 가기 키를 처리 하는지 여부를 확인 하려면 `pWndFrame`합니다.  
  
##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable  
 인쇄 가능한 문자 인지를 나타냅니다.  
  
```  
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] `nChar`|이 메서드를 확인 하는 문자입니다.|  
  
### <a name="return-value"></a>반환 값  
 0이 아닌 문자 이면 인쇄할 수 없는 경우 0입니다.  
  
### <a name="remarks"></a>설명  
 호출 하는 경우이 방법이 실패 하면 [GetKeyboardState](http://msdn.microsoft.com/library/windows/desktop/ms646299) 실패 합니다.  
  
##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators  
 메뉴 명령과 연결 된 모든 바로 가기 키 또는 기본 바로 가기 키만 메뉴가 표시 여부를 나타냅니다.  
  
```  
static BOOL IsShowAllAccelerators();
```  
  
### <a name="return-value"></a>반환 값  
 메뉴 명령;에 대 한 모든 바로 가기 키를 나열 하는 응용 프로그램 0이 아닌 응용 프로그램은 기본 바로 가기 키만 표시 하는 경우 0입니다.  
  
### <a name="remarks"></a>설명  
 응용 프로그램 메뉴 모음에서 메뉴 명령에 대 한 바로 가기 키를 나열합니다. 함수를 사용 하 여 [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) 제어 여부 응용 프로그램에서는 모든 바로 가기 키 또는 기본 바로 가기 키만 합니다.  
  
##  <a name="loadstate"></a>  CKeyboardManager::LoadState  
 Windows 레지스트리에서 바로 가기 키 테이블을 로드합니다.  
  
```  
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `lpszProfileName`  
 레지스트리 경로 여기서 `CKeyboardManager` 데이터가 저장 됩니다.  
  
 [in] `pDefaultFrame`  
 기본 창으로 사용 하는 프레임 창에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 그렇지 않으면 상태는 0 또는 성공적으로 로드 하는 경우에 0이 아닙니다.  
  
### <a name="remarks"></a>설명  
 경우는 `lpszProfileName` 매개 변수는 `NULL`,이 메서드는 기본 레지스트리 위치에 대 한 확인 `CKeyboardManager` 데이터입니다. 지정 된 기본 레지스트리 위치는 [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)합니다. 방법으로 데이터를 이전에 써야 합니다 [CKeyboardManager::SaveState](#savestate)합니다.  
  
 기본 창을 지정 하지 않으면 응용 프로그램의 주 프레임 창이 사용 됩니다.  
  
##  <a name="resetall"></a>  CKeyboardManager::ResetAll  
 응용 프로그램 리소스에서 바로 가기 키 테이블을 다시 로드합니다.  
  
```  
void ResetAll();
```  
  
### <a name="remarks"></a>설명  
 이 함수에서 바로 가기 키에 저장 된 지웁니다는 `CKeyboardManager` 인스턴스. 그런 다음 응용 프로그램 리소스에서 키보드 관리자의 상태 다시 로드 됩니다.  
  
##  <a name="savestate"></a>  CKeyboardManager::SaveState  
 Windows 레지스트리에 바로 가기 키 테이블을 저장합니다.  
  
```  
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `lpszProfileName`  
 나중에 다시 레지스트리 경로 `CKeyboardManager` 상태입니다.  
  
 [in] `pDefaultFrame`  
 기본 창 되는 프레임 창에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 키보드 관리자 상태가 성공적으로 저장 된 경우 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 경우는 `lpszProfileName` 매개 변수는 `NULL`,이 메서드는 기록의 `CKeyboardManager` 로 지정 된 기본 위치에 상태는 [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)합니다. 메서드를 사용 하 여 나중에 데이터를 로드할 수 위치를 지정 하는 경우 [CKeyboardManager::LoadState](#loadstate)합니다.  
  
 기본 기간을 지정 하지 않으면 주 프레임 창의 기본 창으로 사용 됩니다.  
  
##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators  
 메뉴 명령과 연결 된 모든 바로 가기 키를 보여 줍니다.  
  
```  
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,  
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `bShowAll`  
 경우 `true`, 바로 가기 키를 모두 표시 됩니다. 경우 `false`, 첫 번째 바로 가기 키만 표시 됩니다.  
  
 [in] `lpszDelimiter`  
 바로 가기 키 사이 삽입할 문자열입니다. 이 구분 기호 하나만 하나의 바로 가기 키 표시 되는 경우에 영향이 없습니다.  
  
### <a name="remarks"></a>설명  
 기본적으로 명령에 연결 된 바로 가기 키를 둘 이상의 첫 번째 바로 가기 키만 표시 됩니다. 이 함수를 사용 하면 모든 명령과 연결 된 모든 바로 가기 키를 나열할 수 있습니다.  
  
 메뉴 모음에서 명령 옆에 있는 바로 가기 키를 나열 됩니다. 문자열에서 제공 하는 모든 바로 가기 키를 표시 되 면 `lpszDelimiter` 개별 바로 가기 키를 구분 합니다.  
  
##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper  
 문자 위쪽 해당 레지스터를 변환 합니다.  
  
```  
static UINT TranslateCharToUpper(const UINT nChar);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `nChar`  
 변환할 문자입니다.  
  
### <a name="return-value"></a>반환 값  
 문자는 입력된 매개 변수의 위쪽 레지스터입니다.  
  
##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable  
 새 바로 가기 키 테이블으로 바로 가기 키 테이블을 업데이트합니다.  
  
```  
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    LPACCEL lpAccel,  
    int nSize,  
    CFrameWnd* pDefaultFrame = NULL);

 
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    HACCEL hAccelNew,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `pTemplate`  
 문서 서식 파일에 대 한 포인터입니다.  
  
 [in] `lpAccel`  
 새 바로 가기 키에 대 한 포인터입니다.  
  
 [in] `nSize`  
 새 바로 가기 테이블의 크기입니다.  
  
 [in] `pDefaultFrame`  
 기본 프레임 창에 대 한 포인터입니다.  
  
 [in] `hAccelNew`  
 새 바로 가기 테이블에 대 한 핸들입니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공 하면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 사용 하 여 여러 프레임 창 개체에 대 한 새로운 바로 가기 키를 가진 기존 바로 가기 표를 대체 합니다. 함수는 지정 된 문서 서식 파일에 연결 된 모든 프레임 창 개체에 대 한 액세스를 얻으려고 매개 변수로 문서 서식 파일을 받습니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)   
 [키보드 및 마우스 사용자 지정](../../mfc/keyboard-and-mouse-customization.md)



