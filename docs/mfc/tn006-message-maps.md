---
description: 'TN006: 메시지 맵에 대해 자세히 알아보세요.'
title: 'TN006: 메시지 맵'
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
ms.openlocfilehash: f9331e5523015a670a2a874c9e9b3021d41eed09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216056"
---
# <a name="tn006-message-maps"></a>TN006: 메시지 맵

이 참고는 MFC 메시지 맵 기능을 설명 합니다.

## <a name="the-problem"></a>문제

Microsoft Windows는 메시징 기능을 사용 하는 창 클래스에서 가상 함수를 구현 합니다. 메시지 수가 많기 때문에 각 Windows 메시지에 대 한 별도의 가상 함수를 제공 하면 매우 많은 vtable이 생성 됩니다.

시스템 정의 Windows 메시지의 수는 시간이 지남에 따라 변경 되며 응용 프로그램에서 자체 Windows 메시지를 정의할 수 있기 때문에 메시지 맵은 인터페이스 변경으로 인해 기존 코드를 분리 하지 못하도록 하는 간접 참조 수준을 제공 합니다.

## <a name="overview"></a>개요

MFC는 창에 전송 된 메시지를 처리 하기 위해 기존 Windows 기반 프로그램에서 사용 된 switch 문에 대 한 대안을 제공 합니다. 메시지가 창에서 수신 될 때 적절 한 메서드가 자동으로 호출 되도록 메시지에서 메서드로의 매핑을 정의할 수 있습니다. 이 메시지 맵 기능은 가상 함수와 유사 하 게 설계 되었지만 c + + 가상 함수에 사용할 수 없는 추가 이점을 제공 합니다.

## <a name="defining-a-message-map"></a>메시지 맵 정의

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) 매크로는 클래스에 대 한 세 개의 멤버를 선언 합니다.

- *_MessageEntries* 이라는 AFX_MSGMAP_ENTRY 항목의 전용 배열입니다.

- *_MessageEntries* 배열을 가리키는 *messagemap* 이라는 보호 된 AFX_MSGMAP 구조입니다.

- `GetMessageMap` *Messagemap* 주소를 반환 하는 라는 보호 된 가상 함수입니다.

이 매크로는 메시지 맵을 사용 하 여 클래스의 선언에 배치 해야 합니다. 규칙에 따라 클래스 선언의 끝에 있습니다. 예를 들어:

```cpp
class CMyWnd : public CMyParentWndClass
{
    // my stuff...

protected:
    //{{AFX_MSG(CMyWnd)
    afx_msg void OnPaint();
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};
```

이 형식은 새 클래스를 만들 때 응용 프로그램 마법사 및 클래스 마법사에서 생성 되는 형식입니다. 클래스 마법사에는//{{및//} 대괄호가 필요 합니다.

메시지 맵의 테이블은 메시지 맵 항목으로 확장 되는 매크로 집합을 사용 하 여 정의 됩니다. 테이블은이 메시지 맵에 의해 처리 되는 클래스와 처리 되지 않은 메시지가 전달 되는 부모 클래스를 정의 하는 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) 매크로 호출로 시작 합니다. 테이블이 [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) 매크로 호출로 끝납니다.

이러한 두 매크로 호출 사이에는이 메시지 맵에서 처리할 각 메시지에 대 한 항목이 있습니다. 모든 표준 Windows 메시지에는 해당 메시지에 대 한 항목을 생성 하는 *MESSAGE_NAME* ON_WM_ 형태의 매크로가 있습니다.

각 Windows 메시지의 매개 변수를 압축 해제 하 고 형식 안전성을 제공 하는 표준 함수 시그니처가 정의 되었습니다. 이러한 서명은 [CWnd](../mfc/reference/cwnd-class.md)의 선언에 있는 afxwin.h 파일에서 찾을 수 있습니다. 각 항목은 쉽게 식별할 수 있도록 **afx_msg** 키워드로 표시 됩니다.

> [!NOTE]
> 클래스 마법사를 사용 하려면 메시지 맵 처리기 선언에 **afx_msg** 키워드를 사용 해야 합니다.

이러한 함수 시그니처는 간단한 규칙을 사용 하 여 파생 되었습니다. 함수의 이름은 항상 "로 시작 `"On` 합니다. 다음에는 "WM_"가 제거 된 Windows 메시지의 이름과 각 단어의 첫 글자를 대문자로 표기 합니다. 매개 변수의 순서는 *wParam* `LOWORD` 다음에 (*lparam*) then `HIWORD` (*lparam*)이 옵니다. 사용 하지 않는 매개 변수가 전달 되지 않습니다. MFC 클래스로 래핑된 핸들은 적절 한 MFC 개체에 대 한 포인터로 변환 됩니다. 다음 예제에서는 WM_PAINT 메시지를 처리 하 고 함수를 호출 하는 방법을 보여 줍니다 `CMyWnd::OnPaint` .

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

메시지 맵 테이블은 함수 또는 클래스 정의의 범위 외부에서 정의 해야 합니다. Extern "C" 블록에 배치 하면 안 됩니다.

> [!NOTE]
> 클래스 마법사는//{{{및//}} 주석 대괄호 사이에 발생 하는 메시지 맵 항목을 수정 합니다.

## <a name="user-defined-windows-messages"></a>사용자 정의 Windows 메시지

사용자 정의 메시지는 [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) 매크로를 사용 하 여 메시지 맵에 포함 될 수 있습니다. 이 매크로는 다음과 같은 형식의 메시지 번호와 메서드를 허용 합니다.

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

이 예제에서는 사용자 정의 메시지의 표준 WM_USER 기반에서 파생 된 Windows 메시지 ID가 있는 사용자 지정 메시지에 대 한 처리기를 설정 합니다. 다음 예제에서는이 처리기를 호출 하는 방법을 보여 줍니다.

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

이 방법을 사용 하는 사용자 정의 메시지 범위는 0x7fff WM_USER 범위 내에 있어야 합니다.

> [!NOTE]
> 클래스 마법사는 클래스 마법사 사용자 인터페이스에서 ON_MESSAGE 처리기 루틴을 입력 하는 것을 지원 하지 않습니다. Visual C++ 편집기에서 수동으로 입력 해야 합니다. 클래스 마법사는 이러한 항목을 구문 분석 하 고 다른 메시지 맵 항목과 마찬가지로 검색할 수 있도록 합니다.

## <a name="registered-windows-messages"></a>등록 된 Windows 메시지

[Registerwindowmessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) 함수는 시스템 전체에서 고유 하 게 보장 되는 새 창 메시지를 정의 하는 데 사용 됩니다. 이러한 메시지를 처리 하는 데 사용 되는 매크로 ON_REGISTERED_MESSAGE입니다. 이 매크로는 등록 된 windows 메시지 ID를 포함 하는 *UINT NEAR* 변수의 이름을 허용 합니다. 예를 들면 다음과 같습니다.

```cpp
class CMyWnd : public CMyParentWndClass
{
public:
    CMyWnd();

    //{{AFX_MSG(CMyWnd)
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};

static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

ON_REGISTERED_MESSAGE 구현 되는 방식으로 인해 등록 된 Windows 메시지 ID 변수 (이 예제에서는 WM_FIND)가 *NEAR* 변수 여야 합니다.

이 접근 방식을 사용 하는 사용자 정의 메시지 범위는 0xC000 ~ 0xFFFF의 범위에 있습니다.

> [!NOTE]
> 클래스 마법사는 클래스 마법사 사용자 인터페이스에서 ON_REGISTERED_MESSAGE 처리기 루틴을 입력 하는 것을 지원 하지 않습니다. 텍스트 편집기에서 수동으로 입력 해야 합니다. 클래스 마법사는 이러한 항목을 구문 분석 하 고 다른 메시지 맵 항목과 마찬가지로 검색할 수 있도록 합니다.

## <a name="command-messages"></a>명령 메시지

메뉴 및 액셀러레이터의 명령 메시지는 ON_COMMAND 매크로를 사용 하 여 메시지 맵에서 처리 됩니다. 이 매크로는 명령 ID 및 메서드를 허용 합니다. 지정 된 명령 ID와 일치 하는 *wParam* 이 있는 특정 WM_COMMAND 메시지만 메시지 맵 항목에 지정 된 메서드에서 처리 됩니다. 명령 처리기 멤버 함수는 매개 변수를 사용 하지 않고을 반환 **`void`** 합니다. 매크로의 형식은 다음과 같습니다.

```cpp
ON_COMMAND(id, memberFxn)
```

명령 업데이트 메시지는 동일한 메커니즘을 통해 라우팅되고 대신 ON_UPDATE_COMMAND_UI 매크로를 사용 합니다. 명령 업데이트 처리기 멤버 함수는 단일 매개 변수 및 [CCmdUI](../mfc/reference/ccmdui-class.md) 개체에 대 한 포인터를 사용 하 고를 반환 **`void`** 합니다. 매크로의 형식은

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

고급 사용자는 명령 메시지 처리기의 확장 형식인 ON_COMMAND_EX 매크로를 사용할 수 있습니다. 매크로는 ON_COMMAND 기능의 상위 집합을 제공 합니다. 확장 된 명령 처리기 멤버 함수는 단일 매개 변수 (명령 ID를 포함 하는 **UINT** )를 사용 하 고 **BOOL** 을 반환 합니다. 명령이 처리 되었음을 나타내려면 반환 값이 **TRUE** 여야 합니다. 그렇지 않으면 라우팅은 다른 명령 대상 개체로 계속 됩니다.

이러한 형태의 예는 다음과 같습니다.

- Resource.h 내 (일반적으로 Visual C++에서 생성 됨)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- 클래스 선언 내부

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- 메시지 맵 정의 내부

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- 구현 파일에서

    ```cpp
    void CMyClass::OnMyCommand()
    {
        // handle the command
    }

    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)
    {
        // set the UI state with pCmdUI
    }

    BOOL CMyClass::OnComplexCommand(UINT nID)
    {
        // handle the command
        return TRUE;
    }
    ```

고급 사용자는 단일 명령 처리기 인 [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) 또는 ON_COMMAND_RANGE_EX를 사용 하 여 다양 한 명령을 처리할 수 있습니다. 이러한 매크로에 대 한 자세한 내용은 제품 설명서를 참조 하십시오.

> [!NOTE]
> 클래스 마법사는 ON_COMMAND 및 ON_UPDATE_COMMAND_UI 처리기 만들기를 지원 하지만 ON_COMMAND_EX 또는 ON_COMMAND_RANGE 처리기 만들기를 지원 하지 않습니다. 그러나 클래스 마법사는 구문을 분석 하 고 네 개의 명령 처리기 변형을 모두 찾아볼 수 있도록 합니다.

## <a name="control-notification-messages"></a>알림 메시지 제어

자식 컨트롤에서 창으로 전송 되는 메시지의 메시지 맵 항목에는 컨트롤의 ID와 같은 추가 정보가 포함 됩니다. 메시지 맵 항목에 지정 된 메시지 처리기는 다음 조건에 해당할 경우에만 호출 됩니다.

- BN_CLICKED와 같은 컨트롤 알림 코드 (예: *lParam*)는 메시지 맵 항목에 지정 된 알림 코드와 일치 합니다.

- 컨트롤 ID (*wParam*)는 메시지 맵 항목에 지정 된 컨트롤 id와 일치 합니다.

사용자 지정 컨트롤 알림 메시지는 [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) 매크로를 사용 하 여 사용자 지정 알림 코드를 사용 하 여 메시지 맵 항목을 정의할 수 있습니다. 이 매크로의 형식은 다음과 같습니다.

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

고급 사용 [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) 를 사용 하 여 동일한 처리기를 사용 하는 컨트롤 범위에서 특정 컨트롤 알림을 처리할 수 있습니다.

> [!NOTE]
> 클래스 마법사는 사용자 인터페이스에서 ON_CONTROL 또는 ON_CONTROL_RANGE 처리기 만들기를 지원 하지 않습니다. 텍스트 편집기를 사용 하 여 수동으로 입력 해야 합니다. 클래스 마법사는 이러한 항목을 구문 분석 하 고 다른 메시지 맵 항목과 마찬가지로 검색할 수 있도록 합니다.

Windows 공용 컨트롤은 복잡 한 컨트롤 알림에 대해 보다 강력한 [WM_NOTIFY](/windows/win32/controls/wm-notify) 을 사용 합니다. 이 버전의 MFC는 ON_NOTIFY 및 ON_NOTIFY_RANGE 매크로를 사용 하 여이 새 메시지를 직접 지원 합니다. 이러한 매크로에 대 한 자세한 내용은 제품 설명서를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
