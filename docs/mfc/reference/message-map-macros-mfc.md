---
description: '자세한 정보: 메시지 맵 매크로 (MFC)'
title: 메시지 맵 매크로(MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: ece09b915da9e6f88191e90056158be82651e9ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219397"
---
# <a name="message-map-macros-mfc"></a>메시지 맵 매크로(MFC)

메시지 맵을 지원 하기 위해 MFC는 다음 매크로를 제공 합니다.

### <a name="message-map-declaration-and-demarcation-macros"></a>Message-Map 선언 및 경계 매크로

|Name|설명|
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|메시지 맵을 클래스에서 사용 하 여 메시지를 함수에 매핑하는 것을 선언 합니다 (클래스 선언에서 사용 되어야 함).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|메시지 맵의 정의를 시작 합니다 (클래스 구현에서 사용 되어야 함).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|단일 템플릿 인수를 포함 하는 클래스 형식에 대 한 메시지 맵의 정의를 시작 합니다. |
|[END_MESSAGE_MAP](#end_message_map)|메시지 맵의 정의를 끝냅니다 (클래스 구현에서 사용 되어야 함).|

### <a name="message-mapping-macros"></a>Message-Mapping 매크로

|Name|설명|
|-|-|
|[ON_COMMAND](#on_command)|지정 된 명령 메시지를 처리할 함수를 나타냅니다.|
|[ON_COMMAND_EX](#on_command_ex)|지정 된 명령 메시지를 처리할 함수를 나타냅니다.|
|[ON_CONTROL](#on_control)|지정 된 컨트롤 알림 메시지를 처리할 함수를 나타냅니다.|
|[ON_MESSAGE](#on_message)|사용자 정의 메시지를 처리할 함수를 나타냅니다.|
|[ON_OLECMD](#on_olecmd)|DocObject 또는 해당 컨테이너에서 메뉴 명령을 처리할 함수를 나타냅니다.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|등록 된 사용자 정의 메시지를 처리할 함수를 나타냅니다.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|클래스가 있는 경우 등록 된 사용자 정의 메시지를 처리할 함수를 나타냅니다 `CWinThread` .|
|[ON_THREAD_MESSAGE](#on_thread_message)|클래스가 있을 때 사용자 정의 메시지를 처리할 함수를 나타냅니다 `CWinThread` .|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|지정 된 사용자 인터페이스 업데이트 명령 메시지를 처리할 함수를 나타냅니다.|

### <a name="message-map-range-macros"></a>Message-Map 범위 매크로

|Name|설명|
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|매크로에 대 한 처음 두 매개 변수에 지정 된 명령 Id의 범위를 처리 하는 함수를 나타냅니다.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|매크로에 대 한 처음 두 매개 변수에 지정 된 명령 Id의 범위를 처리 하는 업데이트 처리기를 나타냅니다.|
|[ON_CONTROL_RANGE](#on_control_range)|매크로에 대 한 두 번째 및 세 번째 매개 변수에 지정 된 컨트롤 Id 범위에서 알림을 처리할 함수를 나타냅니다. 첫 번째 매개 변수는 BN_CLICKED와 같은 컨트롤 알림 메시지입니다.|

메시지 맵, 메시지 맵 선언 및 경계 매크로 및 메시지 매핑 매크로에 대 한 자세한 내용은 [메시지 맵](../../mfc/reference/message-maps-mfc.md) 및 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요. 메시지 맵 범위에 대 한 자세한 내용은 [Message-Map 범위에 대 한 처리기](../../mfc/handlers-for-message-map-ranges.md)를 참조 하세요.

## <a name="begin_message_map"></a><a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

메시지 맵의 정의를 시작 합니다.

### <a name="syntax"></a>구문

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
메시지 맵이 있는 클래스의 이름을 지정 합니다.

*baseClass*<br/>
*Theclass* 의 기본 클래스 이름을 지정 합니다.

### <a name="remarks"></a>설명

클래스의 멤버 함수를 정의 하는 구현 파일 (.cpp)에서 BEGIN_MESSAGE_MAP 매크로를 사용 하 여 메시지 맵을 시작 하 고 각 메시지 처리기 함수에 대해 매크로 항목을 추가 하 고 END_MESSAGE_MAP 매크로를 사용 하 여 메시지 맵을 완료 합니다.

메시지 맵에 대 한 자세한 내용은 [메시지 맵](message-maps-mfc.md) 을 참조 하세요.

### <a name="example"></a>예제

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a> BEGIN_TEMPLATE_MESSAGE_MAP

단일 템플릿 인수를 포함 하는 클래스 형식에 대 한 메시지 맵의 정의를 시작 합니다.

### <a name="syntax"></a>구문

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
메시지 맵이 있는 클래스의 이름을 지정 합니다.

*type_name*<br/>
클래스에 대해 지정 된 템플릿 매개 변수의 이름입니다.

*baseClass*<br/>
*Theclass* 의 기본 클래스 이름을 지정 합니다.

### <a name="remarks"></a>설명

이 매크로는 [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) 매크로와 비슷합니다. 그러나이 매크로는 단일 템플릿 인수를 포함 하는 클래스를 위한 것입니다.

클래스의 메서드 구현 섹션에서 BEGIN_TEMPLATE_MESSAGE_MAP 매크로를 사용 하 여 메시지 맵을 시작 합니다. 그런 다음 표준 메시지 맵과 마찬가지로 각 메시지 처리기 메서드에 대 한 매크로 항목을 추가 합니다. BEGIN_MESSAGE_MAP 매크로와 마찬가지로 [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) 매크로를 사용 하 여 템플릿 메시지 맵을 작성 합니다.

템플릿 클래스에 대 한 메시지 맵을 구현 하는 방법에 대 한 자세한 내용은 [방법: 템플릿 클래스에 대 한 메시지 맵 만들기](../how-to-create-a-message-map-for-a-template-class.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a> DECLARE_MESSAGE_MAP

클래스가 메시지 맵을 정의 함을 선언 합니다. `CCmdTarget`프로그램의 각 파생 클래스는 메시지 맵을 제공 하 여 메시지를 처리 해야 합니다.

### <a name="syntax"></a>구문

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>설명

클래스 선언 끝에 DECLARE_MESSAGE_MAP 매크로를 사용 합니다. 그런 다음 클래스의 멤버 함수를 정의 하는 .cpp 파일에서 BEGIN_MESSAGE_MAP 매크로, 각 메시지 처리기 함수에 대 한 매크로 항목 및 END_MESSAGE_MAP 매크로를 사용 합니다.

> [!NOTE]
> DECLARE_MESSAGE_MAP 후 멤버를 선언 하는 경우 **`public`** **`private`** 해당 멤버에 대 한 새 액세스 형식 (, 또는)을 지정 해야 합니다 **`protected`** .

메시지 맵과 DECLARE_MESSAGE_MAP 매크로에 대 한 자세한 내용은 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요.

### <a name="example"></a>예제

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a> END_MESSAGE_MAP

메시지 맵의 정의를 종료 합니다.

### <a name="syntax"></a>구문

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>설명

메시지 맵과 END_MESSAGE_MAP 매크로에 대 한 자세한 내용은 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a> ON_COMMAND

이 매크로는 명령 메시지를 멤버 함수에 매핑합니다.

### <a name="syntax"></a>구문

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>매개 변수

*commandId*<br/>
명령 ID입니다.

*memberFxn*<br/>
명령이 매핑되는 메시지-처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

메뉴 항목 또는 도구 모음 단추와 같은 명령 사용자 인터페이스 개체에서 명령 메시지를 처리 하는 함수를 나타냅니다.

명령 대상 개체가 지정 된 ID를 사용 하 여 Windows WM_COMMAND 메시지를 받으면 ON_COMMAND는 멤버 함수를 호출 `memberFxn` 하 여 메시지를 처리 합니다.

ON_COMMAND를 사용 하 여 단일 명령을 멤버 함수에 매핑할 수 있습니다. [ON_COMMAND_RANGE](#on_command_range) 를 사용 하 여 일련의 명령 id를 하나의 멤버 함수에 매핑할 수 있습니다. 하나의 메시지 맵 항목만 지정 된 명령 ID와 일치할 수 있습니다. 즉, 명령을 둘 이상의 처리기에 매핑할 수 없습니다. 자세한 내용 및 예제는 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요.

### <a name="example"></a>예제

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="on_command_ex"></a><a name="on_command_ex"></a> ON_COMMAND_EX

확장 된 명령 처리기 멤버 함수입니다.

### <a name="syntax"></a>구문

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>매개 변수

*commandId*<br/>
명령 ID입니다.

*memberFxn*<br/>
명령이 매핑되는 메시지-처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

고급 사용을 위해 명령 메시지 처리기의 확장 된 형태를 사용할 수 있습니다. ON_COMMAND_EX 매크로는 이러한 메시지 처리기에 사용 되며 [ON_COMMAND](message-map-macros-mfc.md#on_command) 기능의 상위 집합을 제공 합니다. 확장 된 명령 처리기 멤버 함수는 단일 매개 변수, 명령 ID를 포함 하는 UINT를 사용 하 고 BOOL을 반환 합니다. 명령이 처리 되었음을 나타내려면 반환 값은 TRUE 여야 합니다. 그렇지 않으면 라우팅은 다른 명령 대상 개체로 계속 됩니다.

자세한 내용은 기술 정보 [TN006: 메시지 맵] tm006-maps.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

헤더 파일: afxmsg_. h

## <a name="on_control"></a><a name="on_control"></a> ON_CONTROL

사용자 지정 컨트롤 알림 메시지를 처리할 함수를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>매개 변수

*wNotifyCode*<br/>
컨트롤의 알림 코드입니다.

*commandId*<br/>
명령 ID입니다.

*memberFxn*<br/>
명령이 매핑되는 메시지-처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

컨트롤 알림 메시지는 컨트롤에서 부모 창으로 전송 되는 메시지입니다.

메시지 맵에는 메시지 처리기 함수에 매핑해야 하는 모든 제어 알림 메시지에 대 한 ON_CONTROL macro 문이 정확히 하나씩 있어야 합니다.

자세한 내용 및 예제는 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="on_message"></a><a name="on_message"></a> ON_MESSAGE

사용자 정의 메시지를 처리할 함수를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>매개 변수

*message*<br/>
메시지 ID입니다.

*memberFxn*<br/>
메시지를 매핑할 메시지 처리기 함수의 이름입니다.

함수의 형식은 여야 합니다 `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)` .

### <a name="remarks"></a>설명

사용자 정의 메시지는 표준 Windows WM_MESSAGE 메시지가 아닌 모든 메시지입니다. 메시지 ID를 선택 하는 경우 WM_USER (0x0400) 범위 내에 있는 값을 0xBFFF로 0x7FFF 또는 WM_APP (0x8000)로 사용 해야 합니다. 메시지 Id에 대 한 자세한 내용은 [WM_APP](/windows/win32/winmsg/wm-app)를 참조 하세요.

메시지 맵에는 메시지 처리기 함수에 매핑해야 하는 모든 사용자 정의 메시지에 대 한 ON_MESSAGE macro 문이 정확히 하나씩 있어야 합니다.

> [!NOTE]
> ON_MESSAGE는 사용자 정의 메시지 외에도 자주 사용 하지 않는 Windows 메시지를 처리 합니다. 자세한 내용은 [메시지 맵](../../mfc/tn006-message-maps.md)을 참조 하세요.

자세한 내용 및 예제는 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md) 및 [사용자 정의 처리기](user-defined-handlers.md) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="on_olecmd"></a><a name="on_olecmd"></a> ON_OLECMD

명령 디스패치 인터페이스를 통해 명령을 라우팅합니다 `IOleCommandTarget` .

### <a name="syntax"></a>구문

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>매개 변수

*pguid*<br/>
명령이 속한 명령 그룹의 식별자입니다. 표준 그룹에 대해 NULL을 사용 합니다.

*olecmdid*<br/>
OLE 명령의 식별자입니다.

*commandId*<br/>
명령을 실행 하는 리소스 또는 개체의 메뉴 ID, 도구 모음 ID, 단추 ID 또는 기타 ID입니다.

### <a name="remarks"></a>설명

`IOleCommandTarget` 컨테이너가 DocObject의 사용자 인터페이스에서 발생 하는 명령을 받을 수 있도록 하 고, 컨테이너가 동일한 명령 (예: 파일 메뉴의 새로 만들기, 열기, 다음으로 인쇄 및 인쇄, 편집 메뉴에서 복사, 붙여넣기, 실행 취소 등)을 DocObject에 보낼 수 있도록 허용 합니다.

`IOleCommandTarget` 는 OLE Automation의 보다 간단 `IDispatch` 합니다. `IOleCommandTarget` 는 거의 인수를 포함 하지 않는 표준 명령 집합을 전적으로 사용 하 고, 형식 정보는 포함 되지 않습니다. 명령 인수의 경우 형식 안전성이 떨어집니다. 인수를 사용 하 여 명령을 디스패치하지 않아도 되는 경우 [COleServerDoc:: OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)를 사용 합니다.

`IOleCommandTarget`표준 메뉴 명령은 다음 매크로에서 MFC에 의해 구현 되었습니다.

**ON_OLECMD_CLEARSELECTION ()**

편집 지우기 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY ()**

Copy Edit 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT ()**

편집 잘라내기 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW ()**

File New 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN ()**

파일 열기 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP ()**

파일 페이지 설정 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE ()**

붙여넣기 편집 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL ()**

편집 붙여넣기 특수 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT ()**

파일 인쇄 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW ()**

파일 인쇄 미리 보기 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO ()**

편집 다시 실행 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE ()**

File Save 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS ()**

파일 다른 이름으로 저장 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS ()**

파일을 다른 이름으로 복사 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL ()**

편집 모두 선택 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO ()**

편집 취소 명령을 디스패치합니다. 다음으로 구현 됨:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>요구 사항

**헤더:** afxdocob

## <a name="on_registered_message"></a><a name="on_registered_message"></a> ON_REGISTERED_MESSAGE

Windows `RegisterWindowMessage` 함수는 시스템 전체에서 고유 하 게 보장 되는 새 창 메시지를 정의 하는 데 사용 됩니다.

### <a name="syntax"></a>구문

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>매개 변수

*nMessageVariable*<br/>
등록 된 창-메시지 ID 변수입니다.

*memberFxn*<br/>
메시지를 매핑할 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

이 매크로는 등록 된 메시지를 처리할 함수를 나타냅니다.

자세한 내용 및 예제는 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요.

### <a name="example"></a>예제

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a> ON_REGISTERED_THREAD_MESSAGE

Windows RegisterWindowMessage 함수에서 등록 한 메시지를 처리할 함수를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>매개 변수

*nMessageVariable*<br/>
등록 된 창-메시지 ID 변수입니다.

*memberFxn*<br/>
메시지가 매핑되는 CWinThread 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

RegisterWindowMessage는 시스템 전체에서 고유 하 게 보장 되는 새 창 메시지를 정의 하는 데 사용 됩니다. CWinThread 클래스를 사용 하는 경우 ON_REGISTERED_MESSAGE 대신 ON_REGISTERED_THREAD_MESSAGE를 사용 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="on_thread_message"></a><a name="on_thread_message"></a> ON_THREAD_MESSAGE

사용자 정의 메시지를 처리할 함수를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>매개 변수

*message*<br/>
메시지 ID입니다.

*memberFxn*<br/>
`CWinThread`메시지를 매핑할-메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

클래스가 있는 경우 ON_MESSAGE 대신 ON_THREAD_MESSAGE를 사용 해야 합니다 `CWinThread` . 사용자 정의 메시지는 표준 Windows WM_MESSAGE 메시지가 아닌 모든 메시지입니다. 메시지 맵에는 메시지 처리기 함수에 매핑해야 하는 모든 사용자 정의 메시지에 대 한 ON_THREAD_MESSAGE macro 문이 정확히 하나씩 있어야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a> ON_UPDATE_COMMAND_UI

이 매크로는 사용자 인터페이스 업데이트 명령 메시지를 처리 하는 함수를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>매개 변수

*있어*<br/>
메시지 ID입니다.

*memberFxn*<br/>
메시지를 매핑할 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

메시지 처리기에 매핑해야 하는 모든 사용자 인터페이스 업데이트 명령에 대해 메시지 맵에 정확히 하나의 ON_UPDATE_COMMAND_UI macro 문이 있어야 합니다.

자세한 내용 및 예제는 [메시지 처리 및 매핑 항목](../../mfc/message-handling-and-mapping.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="on_command_range"></a><a name="on_command_range"></a> ON_COMMAND_RANGE

이 매크로를 사용 하 여 연속 된 명령 Id 범위를 단일 메시지 처리기 함수에 매핑할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>매개 변수

*id1*<br/>
연속 된 명령 Id 범위의 시작 부분에 있는 명령 ID입니다.

*id2*<br/>
연속 된 명령 Id 범위의 끝에 있는 명령 ID입니다.

*memberFxn*<br/>
명령이 매핑되는 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

Id의 범위는 *id1* 로 시작 하 고 *id2* 로 끝납니다.

ON_COMMAND_RANGE를 사용 하 여 일련의 명령 Id를 하나의 멤버 함수에 매핑할 수 있습니다. [ON_COMMAND](#on_command) 를 사용 하 여 단일 명령을 멤버 함수에 매핑할 수 있습니다. 하나의 메시지 맵 항목만 지정 된 명령 ID와 일치할 수 있습니다. 즉, 명령을 둘 이상의 처리기에 매핑할 수 없습니다. 메시지 범위 매핑에 대 한 자세한 내용은 [Message-Map 범위에 대 한 처리기](../../mfc/handlers-for-message-map-ranges.md)를 참조 하세요.

메시지 맵 범위에 대 한 자동 지원은 없으므로 매크로를 직접 입력 해야 합니다.

### <a name="example"></a>예제

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a> ON_UPDATE_COMMAND_UI_RANGE

연속 하는 명령 Id 범위를 단일 업데이트 메시지 처리기 함수에 매핑합니다.

### <a name="syntax"></a>구문

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>매개 변수

*id1*<br/>
연속 된 명령 Id 범위의 시작 부분에 있는 명령 ID입니다.

*id2*<br/>
연속 된 명령 Id 범위의 끝에 있는 명령 ID입니다.

*memberFxn*<br/>
명령이 매핑되는 업데이트 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

메시지 처리기 업데이트 명령과 연결 된 메뉴 항목 및 도구 모음 단추의 상태를 업데이트 합니다. Id의 범위는 *id1* 로 시작 하 고 *id2* 로 끝납니다.

메시지 맵 범위에 대 한 자동 지원은 없으므로 매크로를 직접 입력 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="on_control_range"></a><a name="on_control_range"></a> ON_CONTROL_RANGE

이 매크로를 사용 하 여 BN_CLICKED와 같은 지정 된 Windows 알림 메시지에 대 한 연속 된 컨트롤 Id 범위를 단일 메시지 처리기 함수에 매핑할 수 있습니다.

### <a name="syntax"></a>구문

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>매개 변수

*wNotifyCode*<br/>
처리기가 응답 하는 알림 코드입니다.

*id1*<br/>
연속 된 컨트롤 Id 범위의 시작 부분에 있는 명령 ID입니다.

*id2*<br/>
연속 된 컨트롤 Id 범위의 끝에 있는 명령 ID입니다.

*memberFxn*<br/>
컨트롤이 매핑되는 메시지 처리기 함수의 이름입니다.

### <a name="remarks"></a>설명

Id의 범위는 *id1* 로 시작 하 고 *id2* 로 끝납니다. 매핑된 컨트롤에서 들어오는 지정 된 알림에 대해 처리기가 호출 됩니다.

메시지 맵 범위에 대 한 자동 지원은 없으므로 매크로를 직접 입력 해야 합니다.

컨트롤 Id 범위에 대 한 처리기 함수를 구현 하는 방법에 대 한 자세한 내용은 [Message-Map 범위에 대 한 처리기](../../mfc/handlers-for-message-map-ranges.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxmsg_. h

## <a name="see-also"></a>참고 항목

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: 메시지 맵](../tn006-message-maps.md)<br/>
[COleCmdUI 클래스](colecmdui-class.md)<br/>
[COleServerDoc:: OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[사용자 정의 처리기](user-defined-handlers.md)<br/>
[CCmdUI 클래스](ccmdui-class.md)
