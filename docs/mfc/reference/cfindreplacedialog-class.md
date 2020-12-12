---
description: '자세히 알아보기: CFindReplaceDialog 클래스'
title: CFindReplaceDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 3deeb485a9048ba986f548ed66329b66bd039c08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184480"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 클래스

응용 프로그램에서 표준 문자열 찾기/바꾸기 대화 상자를 구현할 수 있습니다.

## <a name="syntax"></a>구문

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|개체를 생성 하려면이 함수를 호출 `CFindReplaceDialog` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|대화 상자를 만들고 표시 `CFindReplaceDialog` 합니다.|
|[CFindReplaceDialog::FindNext](#findnext)|이 함수를 호출 하 여 사용자가 다음 번에 찾을 문자열을 찾으려고 하는지 여부를 확인 합니다.|
|[CFindReplaceDialog:: GetFindString](#getfindstring)|현재 찾기 문자열을 검색 하려면이 함수를 호출 합니다.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|등록 된 메시지 처리기에서 구조체를 검색 하려면이 함수를 호출 `FINDREPLACE` 합니다.|
|[CFindReplaceDialog:: GetReplaceString](#getreplacestring)|현재 replace 문자열을 검색 하려면이 함수를 호출 합니다.|
|[CFindReplaceDialog:: IsTerminating](#isterminating)|대화 상자를 종료 하 고 있는지 여부를 확인 하려면이 함수를 호출 합니다.|
|[CFindReplaceDialog:: MatchCase](#matchcase)|이 함수를 호출 하 여 사용자가 찾기 문자열의 대/소문자를 정확 하 게 일치 시 키 려 고 할지 여부를 결정 합니다.|
|[CFindReplaceDialog:: MatchWholeWord](#matchwholeword)|사용자가 전체 단어를 검색할지 여부를 결정 하려면이 함수를 호출 합니다.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|이 함수를 호출 하 여 사용자가 모든 문자열의 대체를 원하는 지 여부를 확인 합니다.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|사용자가 현재 단어를 바꿀 것인지 여부를 확인 하려면이 함수를 호출 합니다.|
|[CFindReplaceDialog:: SearchDown](#searchdown)|이 함수를 호출 하 여 사용자가 역방향으로 검색을 수행할지 여부를 결정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFindReplaceDialog:: m_fr](#m_fr)|개체를 사용자 지정 하는 데 사용 되는 구조체 `CFindReplaceDialog` 입니다.|

## <a name="remarks"></a>설명

다른 Windows 일반 대화 상자와 달리 `CFindReplaceDialog` 개체는 모덜리스 이므로 사용자가 화면에 있는 동안 다른 창과 상호 작용할 수 있습니다. 개체에는 `CFindReplaceDialog` 찾기 대화 상자 및 찾기/바꾸기 대화 상자와 같은 두 가지 종류가 있습니다. 사용자는 대화 상자에서 검색 및 검색/바꾸기 문자열을 입력할 수 있지만 검색 또는 바꾸기 함수는 수행 하지 않습니다. 이러한 응용 프로그램은 응용 프로그램에 추가 해야 합니다.

개체를 생성 하려면 `CFindReplaceDialog` 인수를 포함 하지 않는 제공 된 생성자를 사용 합니다. 모덜리스 대화 상자 이기 때문에 스택에서 개체를 할당 하는 대신 연산자를 사용 하 여 힙에 개체를 할당 합니다 **`new`** .

`CFindReplaceDialog` 개체를 생성 한 후에는 [create member](#create) 함수를 호출하여 대화 상자를 만들고 표시 해야합니다.

`Create`를 호출하기 전에 [m_fr](#m_fr) 구조체를 사용하여 대화 상자를 초기화합니다. `m_fr`구조는 [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)형식입니다. 이 구조에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

부모 창에 찾기/바꾸기 요청에 대 한 알림이 표시 되려면 Windows [Registerwindowmessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) 함수를 사용 하 여이 등록 된 메시지를 처리 하는 프레임 창에서 [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) 메시지 맵 매크로를 사용 해야 합니다.

사용자가 멤버 함수를 사용 하 여 대화 상자를 종료 하도록 결정 했는지 여부를 확인할 수 있습니다 `IsTerminating` .

`CFindReplaceDialog` 는 Windows 버전 3.1 이상과 함께 제공 되는 COMMDLG.DLL 파일을 기반으로 합니다.

대화 상자를 사용자 지정 하려면에서 클래스를 파생 시키고 `CFindReplaceDialog` , 사용자 지정 대화 상자 템플릿을 제공 하 고, 확장 된 컨트롤에서 알림 메시지를 처리 하는 메시지 맵을 추가 합니다. 처리 되지 않은 모든 메시지는 기본 클래스에 전달 되어야 합니다.

후크 함수 사용자 지정은 필요 하지 않습니다.

사용에 대 한 자세한 내용은 `CFindReplaceDialog` [일반 대화 상자 클래스](../../mfc/common-dialog-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a> CFindReplaceDialog:: CFindReplaceDialog

`CFindReplaceDialog` 개체를 생성합니다.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>설명

개체는 `CFindReplaceDialog` 모덜리스 대화 상자 이기 때문에 연산자를 사용 하 여 힙에서 생성 해야 합니다 **`new`** .

소멸 하는 동안 프레임 워크는 대화 상자에 대 한 포인터에서 **삭제** 를 수행 하려고 합니다. 스택에서 대화 상자를 만든 경우 **`this`** 포인터가 존재 하지 않고 정의 되지 않은 동작이 발생할 수 있습니다.

개체를 생성 하는 방법에 대 한 자세한 내용은 `CFindReplaceDialog` [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) 개요를 참조 하세요. [CFindReplaceDialog:: Create](#create) 멤버 함수를 사용 하 여 대화 상자를 표시 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a> CFindReplaceDialog:: Create

의 값에 따라 찾기 또는 찾기/바꾸기 대화 상자 개체를 만들고 표시 합니다 `bFindDialogOnly` .

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*bFindDialogOnly*<br/>
**찾기** 대화 상자를 표시 하려면이 매개 변수를 TRUE로 설정 합니다. **찾기/바꾸기** 대화 상자를 표시 하려면 FALSE로 설정 합니다.

*lpszFindWhat*<br/>
대화 상자가 나타나면 기본 검색 문자열에 대 한 포인터입니다. NULL 인 경우에는이 대화 상자에 기본 검색 문자열이 포함 되지 않습니다.

*lpszReplaceWith*<br/>
대화 상자가 표시 되는 경우 기본 대체 문자열에 대 한 포인터입니다. NULL 인 경우에는이 대화 상자에 기본 대체 문자열이 포함 되지 않습니다.

*dwFlags*<br/>
비트 OR 연산자를 사용 하 여 대화 상자의 설정을 사용자 지정 하는 데 사용할 수 있는 하나 이상의 플래그입니다. 기본값은 FR_DOWN입니다 .이 값은 검색이 하향 진행 되도록 지정 합니다. 이러한 플래그에 대 한 자세한 내용은 Windows SDK의 [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) 구조를 참조 하세요.

*pParentWnd*<br/>
대화 상자의 부모 또는 소유자 창에 대 한 포인터입니다. 이 창에는 찾기/바꾸기 작업이 요청 되었음을 나타내는 특수 메시지가 표시 됩니다. NULL 인 경우 응용 프로그램의 주 창이 사용 됩니다.

### <a name="return-value"></a>반환 값

대화 상자 개체가 성공적으로 만들어진 경우에는 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

부모 창에 찾기/바꾸기 요청에 대 한 알림이 표시 되려면 Windows [Registerwindowmessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) 함수를 사용 해야 합니다. 반환 값은 응용 프로그램의 인스턴스에 고유한 메시지 번호입니다. 사용자의 프레임 창에는 `OnFindReplace` 이 등록 된 메시지를 처리 하는 콜백 함수 (다음 예제에서)를 선언 하는 메시지 맵 항목이 있어야 합니다. 다음 코드 조각은 이라는 프레임 창 클래스에 대해이 작업을 수행 하는 방법의 예입니다 `CMyRichEditView` .

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

함수 내에서 `OnFindReplace` [CFindReplaceDialog:: FindNext](#findnext) 및 [CFindReplaceDialog:: IsTerminating](#isterminating) 메서드를 사용 하 여 사용자의 의도를 해석 하 고 찾기/바꾸기 작업을 위한 코드를 만듭니다.

### <a name="example"></a>예제

  [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog)의 예제를 참조 하세요.

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a> CFindReplaceDialog:: FindNext

콜백 함수에서이 함수를 호출 하 여 사용자가 다음 번에 검색 문자열을 찾으려고 하는지 여부를 확인 합니다.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>반환 값

사용자가 다음 번에 검색 문자열을 찾으려고 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a> CFindReplaceDialog:: GetFindString

찾을 기본 문자열을 검색 하려면 콜백 함수에서이 함수를 호출 합니다.

```
CString GetFindString() const;
```

### <a name="return-value"></a>반환 값

찾을 기본 문자열입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a> CFindReplaceDialog:: GetNotifier

현재 찾기 바꾸기 대화 상자에 대 한 포인터를 검색 하려면이 함수를 호출 합니다.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*lParam*<br/>
프레임 창의 멤버 함수에 전달 되는 *lparam* 값 `OnFindReplace` 입니다.

### <a name="return-value"></a>반환 값

현재 대화 상자에 대 한 포인터입니다.

### <a name="remarks"></a>설명

현재 대화 상자에 액세스 하 고, 해당 멤버 함수를 호출 하 고, 구조체에 액세스 하려면 콜백 함수 내에서 사용 해야 합니다 `m_fr` .

### <a name="example"></a>예제

찾기 바꾸기 대화 상자에서 알림을 수신 하도록 OnFindReplace 처리기를 등록 하는 방법에 대 한 예제는 [CFindReplaceDialog:: Create](#create) 를 참조 하세요.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a> CFindReplaceDialog:: GetReplaceString

현재 replace 문자열을 검색 하려면이 함수를 호출 합니다.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>반환 값

찾은 문자열을 바꿀 기본 문자열입니다.

### <a name="example"></a>예제

  [CFindReplaceDialog:: GetFindString](#getfindstring)의 예제를 참조 하세요.

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a> CFindReplaceDialog:: IsTerminating

사용자가 대화 상자를 종료 하도록 결정 했는지 여부를 확인 하려면 콜백 함수 내에서이 함수를 호출 합니다.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>반환 값

사용자가 대화 상자를 종료 하기로 결정 한 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수가 0이 아닌 값을 반환 하는 경우 `DestroyWindow` 현재 대화 상자의 멤버 함수를 호출 하 고 모든 대화 상자 포인터 변수를 NULL로 설정 해야 합니다. 필요에 따라 마지막으로 입력 한 찾기/바꾸기 텍스트를 저장 하 고이를 사용 하 여 다음 찾기/바꾸기 대화 상자를 초기화할 수도 있습니다.

### <a name="example"></a>예제

  [CFindReplaceDialog:: GetFindString](#getfindstring)의 예제를 참조 하세요.

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a> CFindReplaceDialog:: m_fr

개체를 사용자 지정 하는 데 사용 `CFindReplaceDialog` 됩니다.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>설명

`m_fr`[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)형식의 구조입니다. 해당 멤버는 대화 상자 개체의 특성을 저장 합니다. 개체를 생성 한 후에 `CFindReplaceDialog` `m_fr` 는를 사용 하 여 대화 상자에서 다양 한 값을 수정할 수 있습니다.

이 구조에 대 한 자세한 내용은 `FINDREPLACE` Windows SDK 구조를 참조 하세요.

### <a name="example"></a>예제

  [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog)의 예제를 참조 하세요.

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a> CFindReplaceDialog:: MatchCase

이 함수를 호출 하 여 사용자가 찾기 문자열의 대/소문자를 정확 하 게 일치 시 키 려 고 할지 여부를 결정 합니다.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>반환 값

사용자가 검색 문자열의 대/소문자와 정확히 일치 하는 검색 문자열을 찾으려고 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a> CFindReplaceDialog:: MatchWholeWord

사용자가 전체 단어를 검색할지 여부를 결정 하려면이 함수를 호출 합니다.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>반환 값

사용자가 검색 문자열의 전체 단어만 일치 시 키 려 고 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a> CFindReplaceDialog:: ReplaceAll

이 함수를 호출 하 여 사용자가 모든 문자열의 대체를 원하는 지 여부를 확인 합니다.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>반환 값

사용자가 replace 문자열과 일치 하는 모든 문자열을 바꾸도록 요청한 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a> CFindReplaceDialog:: ReplaceCurrent

사용자가 현재 단어를 바꿀 것인지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>반환 값

사용자가 현재 선택 된 문자열이 replace 문자열로 대체 되도록 요청한 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a> CFindReplaceDialog:: SearchDown

이 함수를 호출 하 여 사용자가 역방향으로 검색을 수행할지 여부를 결정 합니다.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>반환 값

사용자가 역방향으로 검색을 진행 하려는 경우 0이 아닌 값입니다. 사용자가 위쪽 방향으로 검색을 진행 하려는 경우 0입니다.

## <a name="see-also"></a>참고 항목

[CCommonDialog 클래스](../../mfc/reference/ccommondialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
