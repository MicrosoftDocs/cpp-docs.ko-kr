---
description: '자세히 알아보기: CKeyboardManager 클래스'
title: CKeyboardManager 클래스
ms.date: 11/04/2016
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
ms.openlocfilehash: 9296c1d81cc2d915fe8ba84bfeedb64ae546fdd5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236895"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager 클래스

주 프레임 창 및 자식 프레임 창에 대한 바로 가기 키 테이블을 관리합니다.

## <a name="syntax"></a>구문

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|[CKeyboardManager:: CKeyboardManager](#ckeyboardmanager)|`CKeyboardManager` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CKeyboardManager:: CleanUp](#cleanup)|바로 가기 키 테이블을 지웁니다.|
|[CKeyboardManager:: FindDefaultAccelerator](#finddefaultaccelerator)|지정 된 명령 및 창에 대 한 기본 바로 가기 키를 검색 합니다.|
|[CKeyboardManager:: IsKeyHandled](#iskeyhandled)|액셀러레이터 키 테이블에서 키가 처리 되는지 여부를 결정 합니다.|
|[CKeyboardManager:: IsKeyPrintable](#iskeyprintable)|문자를 인쇄할 수 있는지 여부를 나타냅니다.|
|[CKeyboardManager:: IsShowAllAccelerators](#isshowallaccelerators)|메뉴에 명령에 대 한 모든 바로 가기 키를 표시할지 아니면 기본 바로 가기 키만 표시할지를 나타냅니다.|
|[CKeyboardManager:: LoadState](#loadstate)|Windows 레지스트리에서 바로 가기 키 테이블을 로드 합니다.|
|[CKeyboardManager:: ResetAll](#resetall)|응용 프로그램 리소스에서 바로 가기 키 테이블을 다시 로드 합니다.|
|[CKeyboardManager:: SaveState](#savestate)|바로 가기 키 테이블을 Windows 레지스트리에 저장 합니다.|
|[CKeyboardManager:: ShowAllAccelerators](#showallaccelerators)|프레임 워크에서 모든 명령에 대 한 바로 가기 키를 모두 표시할지, 아니면 각 명령에 대해 하나의 바로 가기 키를 표시할지를 지정 합니다. 이 메서드는 연결 된 바로 가기 키가 하나만 있는 명령에는 영향을 주지 않습니다.|
|[CKeyboardManager:: TranslateCharToUpper](#translatechartoupper)|문자를 상위 레지스터로 변환 합니다.|
|[CKeyboardManager:: UpdateAccelTable](#updateacceltable)|새 바로 가기 키 테이블을 사용 하 여 바로 가기 키 테이블을 업데이트 합니다.|

## <a name="remarks"></a>설명

이 클래스의 멤버를 사용 하 여 바로 가기 키 테이블을 Windows 레지스트리에 저장 및 로드 하 고, 템플릿을 사용 하 여 짧은 잘라내기 키 테이블을 업데이트 하 고, 프레임 창에서 명령의 기본 바로 가기 키를 찾을 수 있습니다. 또한 개체를 사용 하 여 `CKeyboardManager` 바로 가기 키가 사용자에 게 표시 되는 방식을 제어할 수 있습니다.

개체를 수동으로 만들지 마십시오 `CKeyboardManager` . 응용 프로그램의 프레임 워크에 의해 자동으로 생성 됩니다. 그러나 응용 프로그램의 초기화 프로세스 중에 [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) 를 호출 해야 합니다. 응용 프로그램에 대 한 키보드 관리자에 대 한 포인터를 가져오려면 [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)를 호출 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 개체에 대 한 포인터를 검색 하는 방법과 `CKeyboardManager` `CWinAppEx` 메뉴 명령과 관련 된 모든 바로 가기 키를 표시 하는 방법을 보여 줍니다. 이 코드 조각은 [사용자 지정 페이지 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxkeyboardmanager

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a> CKeyboardManager:: CKeyboardManager

`CKeyboardManager` 개체를 생성합니다.

```
CKeyboardManager();
```

### <a name="remarks"></a>설명

대부분의 경우를 직접 만들 필요가 없습니다 `CKeyboardManager` . 기본적으로 프레임 워크는 사용자를 위해 하나를 만듭니다. 에 대 한 포인터를 가져오려면 `CKeyboardManager` [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)를 호출 합니다. 수동으로 만들 경우 [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)메서드를 사용 하 여 초기화 해야 합니다.

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a> CKeyboardManager:: CleanUp

리소스를 해제 `CKeyboardManager` 하 고 모든 바로 가기 키 매핑을 지웁니다.

```
static void CleanUp();
```

### <a name="remarks"></a>설명

바로 가기 키에 대 한 자세한 내용은 [키보드 및 마우스 사용자 지정](../../mfc/keyboard-and-mouse-customization.md)을 참조 하세요.

응용 프로그램이 종료 되는 동안 프레임 워크에서 자동으로 호출 하므로 응용 프로그램이 종료 될 때이 함수를 호출할 필요가 없습니다.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a> CKeyboardManager:: FindDefaultAccelerator

지정 된 명령 및 창에 대 한 기본 바로 가기 키를 검색 합니다.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 명령 ID입니다.

*str*<br/>
[out] `CString` 개체에 대한 참조입니다.

*pWndFrame*<br/>
진행 프레임 창에 대 한 포인터입니다.

*bIsDefaultFrame*<br/>
진행 프레임 창이 기본 프레임 창 인지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

바로 가기가 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 *Uicmd* 에 지정 된 명령을 조회 하 고 기본 바로 가기 키를 검색 합니다. 그런 다음 메서드는이 바로 가기 키와 연결 된 문자열을 사용 하 여 *str* 매개 변수에 값을 씁니다.

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a> CKeyboardManager:: IsKeyHandled

지정 된 키가 [CKeyboardManager 클래스](../../mfc/reference/ckeyboardmanager-class.md)에서 처리 되는지 여부를 확인 합니다.

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>매개 변수

*nKey*\
진행 확인할 키입니다.

*fVirt*\
진행 바로 가기 키의 동작을 지정 합니다. 가능한 값 목록은 [가속 Structure](/windows/win32/api/winuser/ns-winuser-accel)를 참조 하세요.

*pWndFrame*\
진행 프레임 창입니다. 이 메서드는이 프레임에서 바로 가기 키가 처리 되는지 여부를 결정 합니다.

*bIsDefaultFrame*\
진행 *PWndFrame* 가 기본 프레임 창 인지 여부를 나타내는 부울 매개 변수입니다.

### <a name="return-value"></a>반환 값

바로 가기 키가 처리 되 면 TRUE입니다. 키가 처리 되지 않거나 *pWndFrame* 가 NULL 이면 FALSE입니다.

### <a name="remarks"></a>설명

입력 매개 변수는 *pWndFrame* 에서 바로 가기 키가 처리 되는지 여부를 확인 하기 위해 *Nkey* 및 *fVirt* 에 대 한 액셀러레이터 키 테이블의 항목과 일치 해야 합니다.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a> CKeyboardManager:: IsKeyPrintable

문자를 인쇄할 수 있는지 여부를 나타냅니다.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>매개 변수

*nChar*\
진행 이 메서드가 확인 하는 문자입니다.

### <a name="return-value"></a>반환 값

문자를 인쇄할 수 있으면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) 에 대 한 호출이 실패 하면이 메서드는 실패 합니다.

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a> CKeyboardManager:: IsShowAllAccelerators

메뉴 명령과 관련 된 바로 가기 키를 모두 메뉴에 표시할지 아니면 기본 바로 가기 키만 표시할지를 나타냅니다.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>반환 값

응용 프로그램이 메뉴 명령에 대 한 바로 가기 키를 모두 나열 하는 경우 0이 아닙니다. 응용 프로그램에 기본 바로 가기 키만 표시 되는 경우 0입니다.

### <a name="remarks"></a>설명

응용 프로그램은 메뉴 모음의 메뉴 명령에 대 한 바로 가기 키를 나열 합니다. [CKeyboardManager:: ShowAllAccelerators](#showallaccelerators) 함수를 사용 하 여 응용 프로그램에 모든 바로 가기 키 또는 기본 바로 가기 키만 표시 되는지 여부를 제어 합니다.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a> CKeyboardManager:: LoadState

Windows 레지스트리에서 바로 가기 키 테이블을 로드 합니다.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 `CKeyboardManager` 데이터가 저장 되는 레지스트리 경로입니다.

*pDefaultFrame*<br/>
진행 기본 창으로 사용할 프레임 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

상태가 성공적으로 로드 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*LpszProfileName* 매개 변수가 NULL 인 경우이 메서드는 데이터에 대 한 기본 레지스트리 위치를 확인 합니다 `CKeyboardManager` . 기본 레지스트리 위치는 [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)에 의해 지정 됩니다. 이전에 [CKeyboardManager:: SaveState](#savestate)메서드를 사용 하 여 데이터를 작성 해야 합니다.

기본 창을 지정 하지 않으면 응용 프로그램의 주 프레임 창이 사용 됩니다.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a> CKeyboardManager:: ResetAll

응용 프로그램 리소스에서 바로 가기 키 테이블을 다시 로드 합니다.

```cpp
void ResetAll();
```

### <a name="remarks"></a>설명

이 함수는 인스턴스에 저장 된 바로 가기를 지웁니다 `CKeyboardManager` . 그러면 응용 프로그램 리소스에서 키보드 관리자의 상태가 다시 로드 됩니다.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a> CKeyboardManager:: SaveState

바로 가기 키 테이블을 Windows 레지스트리에 저장 합니다.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 상태를 저장 하기 위한 레지스트리 경로 `CKeyboardManager` 입니다.

*pDefaultFrame*<br/>
진행 기본 창이 되는 프레임 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

키보드 관리자 상태가 성공적으로 저장 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*LpszProfileName* 매개 변수가 NULL 인 경우이 메서드는 `CKeyboardManager` [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)에 지정 된 기본 위치에 상태를 기록 합니다. 위치를 지정 하는 경우 나중에 [CKeyboardManager:: LoadState](#loadstate)메서드를 사용 하 여 데이터를 로드할 수 있습니다.

기본 창을 지정 하지 않으면 주 프레임 창이 기본 창으로 사용 됩니다.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a> CKeyboardManager:: ShowAllAccelerators

메뉴 명령과 관련 된 바로 가기 키를 모두 표시 합니다.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>매개 변수

*bShowAll*<br/>
진행 TRUE 이면 모든 바로 가기 키가 표시 됩니다. FALSE 이면 첫 번째 바로 가기 키만 표시 됩니다.

*lpszDelimiter*<br/>
진행 바로 가기 키 사이에 삽입할 문자열입니다. 바로 가기 키가 하나만 표시 되는 경우이 구분 기호는 영향을 주지 않습니다.

### <a name="remarks"></a>설명

기본적으로 명령에 연결 된 바로 가기 키가 두 개 이상 있으면 첫 번째 바로 가기 키만 표시 됩니다. 이 함수를 사용 하면 모든 명령과 관련 된 바로 가기 키를 모두 나열할 수 있습니다.

바로 가기 키는 메뉴 모음의 명령 옆에 나열 됩니다. 모든 바로 가기 키가 표시 되는 경우 *lpszDelimiter* 에서 제공 하는 문자열은 개별 바로 가기 키를 구분 합니다.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a> CKeyboardManager:: TranslateCharToUpper

문자를 상위 레지스터로 변환 합니다.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>매개 변수

*nChar*<br/>
진행 변환할 문자입니다.

### <a name="return-value"></a>반환 값

입력 매개 변수의 상위 레지스터가 되는 문자입니다.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a> CKeyboardManager:: UpdateAccelTable

새 바로 가기 키 테이블을 사용 하 여 바로 가기 키 테이블을 업데이트 합니다.

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

*pTemplate*<br/>
진행 문서 템플릿에 대 한 포인터입니다.

*lpAccel*<br/>
진행 새 바로 가기 키에 대 한 포인터입니다.

*nSize*<br/>
진행 새 바로 가기 테이블의 크기입니다.

*pDefaultFrame*<br/>
진행 기본 프레임 창에 대 한 포인터입니다.

*hAccelNew*<br/>
진행 새 바로 가기 테이블에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 기존 바로 가기 테이블을 여러 프레임 창 개체에 대 한 새 바로 가기 키로 바꿀 수 있습니다. 함수는 지정 된 문서 템플릿에 연결 된 모든 프레임 창 개체에 대 한 액세스 권한을 얻기 위해 문서 템플릿을 매개 변수로 받습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[키보드 및 마우스 사용자 지정](../../mfc/keyboard-and-mouse-customization.md)
