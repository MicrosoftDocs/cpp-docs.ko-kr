---
description: '자세한 정보: 사용자 지정 알림 처리'
title: 사용자 지정 알림 처리
ms.date: 11/04/2016
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
ms.openlocfilehash: b5e104f118ac0eeff96965692615ce9143c5c178
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254965"
---
# <a name="handling-customization-notifications"></a>사용자 지정 알림 처리

Windows 도구 모음 공용 컨트롤에 시스템 정의 사용자 지정 대화 상자를 포함한 기본 제공 사용자 지정 기능이 있으며 이 기능을 통해 사용자는 도구 모음 단추를 삽입, 삭제 또는 재정렬할 수 있습니다. 애플리케이션에서는 사용자 지정 기능이 사용 가능한지 및 사용자가 도구 모음을 사용자 지정할 수 있는 범위를 제어하는지 여부를 결정합니다.

도구 모음에 **CCS_ADJUSTABLE** 스타일을 제공 하 여 사용자가 이러한 사용자 지정 기능을 사용할 수 있도록 설정할 수 있습니다. 사용자 지정 기능을 통해 사용자가 단추를 새 위치로 끌거나 도구 모음 밖으로 끌어 단추를 제거할 수 있습니다. 또한 사용자는 도구 모음을 두 번 클릭하여 **도구 모음 사용자 지정** 대화 상자를 표시할 수 있습니다. 이 대화 상자를 통해 사용자는 도구 모음 단추를 추가, 삭제 및 재정렬할 수 있습니다. 애플리케이션에서는 [사용자 지정](reference/ctoolbarctrl-class.md#customize) 멤버 함수를 사용하여 대화 상자를 표시할 수 있습니다.

도구 모음 컨트롤에서는 사용자 지정 프로세스의 각 단계에서 부모 창에 알림 메시지를 전송합니다. 사용자가 Shift 키를 누른 채 단추를 끌기 시작하는 경우 도구 모음은 자동으로 끌기 작업을 처리합니다. 도구 모음은 단추를 삭제할 것인지 확인하기 위해 부모 창에 **TBN_QUERYDELETE** 알림 메시지를 전송합니다. 부모 창에서 **FALSE** 가 반환되는 경우 끌기 작업이 종료됩니다. 그렇지 않으면 도구 모음에서는 마우스 입력을 캡처하고 사용자가 마우스 단추를 놓을 때까지 기다립니다.

사용자가 마우스 단추를 놓으면 도구 모음 컨트롤에서는 마우스 커서의 위치를 확인합니다. 커서가 도구 모음 외부에 있는 경우 단추가 삭제됩니다. 커서가 도구 모음 단추에 있는 경우 도구 모음에서는 지정된 단추 왼쪽에 단추를 삽입할 것인지 확인하기 위해 부모 창에 **TBN_QUERYINSERT** 알림 메시지를 전송합니다. 부모 창에서 **TRUE** 가 반환되는 경우 단추가 삽입되고 그렇지 않은 경우에는 삽입되지 않습니다. 도구 모음에서는 끌기 작업의 종료를 표시하기 위해 **TBN_TOOLBARCHANGE** 알림 메시지를 전송합니다.

사용자가 Shift 키를 누르지 않고 끌기 작업을 시작하는 경우 도구 모음 컨트롤에서는 소유자 창에 **TBN_BEGINDRAG** 알림 메시지를 전송합니다. 고유한 단추 끌기 코드를 구현하는 애플리케이션에서는 이 메시지를 끌기 작업의 시작 표시로 사용할 수 있습니다. 도구 모음에서는 끌기 작업의 종료를 표시하기 위해 **TBN_ENDDRAG** 알림 메시지를 전송합니다.

도구 모음 컨트롤에서는 사용자가 **도구 모음 사용자 지정** 대화 상자를 사용하여 도구 모음을 사용자 지정하는 경우 알림 메시지를 전송합니다. 도구 모음에서는 사용자가 도구 모음을 두 번 클릭한 후 대화 상자가 만들어지기 전에 **TBN_BEGINADJUST** 알림 메시지를 전송합니다. 그런 다음 도구 모음에서는 해당 도구 모음에 단추를 삽입할 수 있는지 여부를 확인하기 위해 일련의 **TBN_QUERYINSERT** 알림 메시지를 전송하기 시작합니다. 부모 창에서 **TRUE** 가 반환되는 경우 도구 모음에서는 **TBN_QUERYINSERT** 알림 메시지의 전송을 중지합니다. 부모 창에서 모든 단추에 대해 **TRUE** 가 반환되지 않는 경우 도구 모음에서는 대화 상자가 소멸됩니다.

그런 다음 도구 모음 컨트롤에서는 도구 모음의 각 단추에 대해 **TBN_QUERYDELETE** 알림 메시지 하나를 전송하여 도구 모음에서 단추를 삭제할 수 있는지를 확인합니다. 단추를 삭제할 수 있음을 나타내는 경우 부모 창에서 **TRUE** 가 반환되고 그렇지 않은 경우 **FALSE** 가 반환됩니다. 도구 모음에서는 대화 상자에 모든 도구 모음 단추를 추가하지만 삭제할 수 없는 도구 모음 단추는 회색으로 표시됩니다.

도구 모음 컨트롤에서 도구 모음 사용자 지정 대화 상자의 단추에 대한 정보가 필요할 때마다 **TBN_GETBUTTONINFO** 알림 메시지를 전송하여 **TBNOTIFY** 구조체의 정보 및 주소가 필요한 단추의 인덱스를 지정합니다. 부모 창에서는 관련 정보로 구조체를 채워야 합니다.

**도구 모음 사용자 지정** 대화 상자에는 도움말 단추 및 다시 설정 단추가 포함되어 있습니다. 사용자가 도움말 단추를 선택하면 도구 모음 컨트롤에서는 **TBN_CUSTHELP** 알림 메시지를 전송합니다. 부모 창에서는 도움말 정보를 표시하여 응답해야 합니다. 사용자가 다시 설정 단추를 선택하면 대화 상자에서는 **TBN_RESET** 알림 메시지를 전송합니다. 이 메시지는 도구 모음에서 대화 상자가 다시 초기화됨을 표시합니다.

이러한 메시지는 모두 **WM_NOTIFY** 메시지이며 소유자 창에서 소유자 창의 메시지 맵에 다음 형식의 메시지 맵 항목을 추가하여 해당 메시지를 처리할 수 있습니다.

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   **TBN_BEGINADJUST** 같은 알림 메시지 식별자 코드

- **idControl**

   알림을 전송하는 컨트롤의 식별자

- **memberFxn**

   이 알림을 받을 때 호출되는 멤버 함수

멤버 함수는 다음과 같은 프로토타입으로 선언됩니다.

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

알림 메시지 처리기에서 값을 반환하는 경우 해당 값을 **result** 가 가리키는 *LRESULT* 에 두어야 합니다.

각 메시지의 경우 `pNotifyStruct` 는 **NMHDR** 구조체 또는 **TBNOTIFY** 구조체를 가리킵니다. 다음은 이러한 구조체에 대한 설명입니다.

**NMHDR** 구조체에는 다음 멤버가 포함되어 있습니다.

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   알림을 전송하는 컨트롤의 창 핸들입니다. 이 핸들을 `CWnd` 포인터로 변환하려면 [CWnd::FromHandle](reference/cwnd-class.md#fromhandle)을 사용하십시오.

- **idFrom**

   알림을 전송하는 컨트롤의 식별자입니다.

- **code**

   알림 코드입니다. 이 멤버는 **TBN_BEGINADJUST** 또는 **TTN_NEEDTEXT** 같은 컨트롤 형식에서만 사용될 수 있는 값이거나 아래에 나열된 공용 알림 값 중 하나일 수 있습니다.

  - **NM_CLICK** 사용자가 컨트롤 내에서 마우스 왼쪽 단추를 클릭했습니다.

  - **NM_DBLCLK** 사용자가 컨트롤 내에서 마우스 왼쪽 단추를 두 번 클릭했습니다.

  - **NM_KILLFOCUS** 컨트롤에서 입력 포커스가 손실되었습니다.

  - **NM_OUTOFMEMORY** 사용할 수 있는 메모리가 부족하여 컨트롤이 작업을 완료할 수 없습니다.

  - **NM_RCLICK** 사용자가 컨트롤 내에서 마우스 오른쪽 단추를 클릭했습니다.

  - **NM_RDBLCLK** 사용자가 컨트롤 내에서 마우스 오른쪽 단추를 두 번 클릭했습니다.

  - **NM_RETURN** 컨트롤에서 입력 포커스가 손실되었으며 사용자가 Enter 키를 눌렀습니다.

  - **NM_SETFOCUS** 컨트롤에서 입력 포커스를 받았습니다.

**TBNOTIFY** 구조체에는 다음 멤버가 포함되어 있습니다.

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   모든 **WM_NOTIFY** 메시지에 공통적인 정보입니다.

- **iItem**

   알림과 연결된 단추의 인덱스입니다.

- **tbButton**

   알림과 연결 된 도구 모음 단추에 대 한 정보를 포함 하는 **TBBUTTON** 구조체입니다.

- **cchText**

   단추 텍스트의 문자 수입니다.

- **lpszText**

   단추 텍스트에 대한 포인터입니다.

도구 모음에서 전송되는 알림은 다음과 같습니다.

- **TBN_BEGINADJUST**

   사용자가 도구 모음 컨트롤의 사용자 지정을 시작할 때 전송 됩니다. 알림에 대한 정보를 포함하는 **NMHDR** 구조체를 가리키는 포인터입니다. 처리기에서 특정 값을 반환할 필요가 없습니다.

- **TBN_BEGINDRAG**

   사용자가 도구 모음 컨트롤에서 단추를 끌기 시작 하면 전송 됩니다. **TBNOTIFY** 구조체를 가리키는 포인터입니다. **iItem** 멤버에는 0부터 시작하는 끌어 오는 단추의 인덱스가 포함되어 있습니다. 처리기에서 특정 값을 반환할 필요가 없습니다.

- **TBN_CUSTHELP**

   사용자가 도구 모음 사용자 지정 대화 상자에서 도움말 단추를 선택 하면 전송 됩니다. 반환 값이 없습니다. 알림 메시지에 대한 정보를 포함하는 **NMHDR** 구조체를 가리키는 포인터입니다. 처리기에서 특정 값을 반환할 필요가 없습니다.

- **TBN_ENDADJUST**

   사용자가 도구 모음 컨트롤의 사용자 지정을 중지할 때 전송 됩니다. 알림 메시지에 대한 정보를 포함하는 **NMHDR** 구조체를 가리키는 포인터입니다. 처리기에서 특정 값을 반환할 필요가 없습니다.

- **TBN_ENDDRAG**

   사용자가 도구 모음 컨트롤에서 단추 끌기를 중지할 때 전송 됩니다. **TBNOTIFY** 구조체를 가리키는 포인터입니다. **iItem** 멤버에는 0부터 시작하는 끌어 오는 단추의 인덱스가 포함되어 있습니다. 처리기에서 특정 값을 반환할 필요가 없습니다.

- **TBN_GETBUTTONINFO**

   사용자가 도구 모음 컨트롤을 사용자 지정할 때 전송 됩니다. 도구 모음에서는 이 알림 메시지를 사용하여 도구 모음 사용자 지정 대화 상자에 필요한 정보를 검색합니다. **TBNOTIFY** 구조체를 가리키는 포인터입니다. **iItem** 멤버는 0부터 시작하는 단추의 인덱스를 지정합니다. **pszText** 및 **cchText** 멤버는 현재 단추 텍스트 문자의 주소 및 길이를 지정합니다. 애플리케이션에서는 단추에 대한 정보로 구조체를 채워야 합니다. 단추 정보가 구조체로 복사된 경우에는 **TRUE** 를 반환하고 그렇지 않은 경우에는 **FALSE** 를 반환합니다.

- **TBN_QUERYDELETE**

   사용자가 도구 모음 컨트롤에서 단추를 삭제할 수 있는지 여부를 확인 하기 위해 도구 모음을 사용자 지정 하는 동안 전송 됩니다. **TBNOTIFY** 구조체를 가리키는 포인터입니다. **iItem** 멤버에는 0부터 시작하는 삭제할 단추의 인덱스가 포함되어 있습니다. 단추의 삭제를 허용하려면 **TRUE** 를 반환하고 단추의 삭제를 방지하려면 **FALSE** 를 반환합니다.

- **TBN_QUERYINSERT**

   사용자가 도구 모음 컨트롤을 사용자 지정 하 여 지정 된 단추의 왼쪽에 단추를 삽입할 수 있는지 여부를 결정 하는 동안 전송 됩니다. **TBNOTIFY** 구조체를 가리키는 포인터입니다. **iItem** 멤버에는 0부터 시작하는 삽입할 단추의 인덱스가 포함되어 있습니다. 지정된 단추 앞에 단추의 삽입을 허용하려면 **TRUE** 를 반환하고 단추의 삽입을 방지하려면 **FALSE** 를 반환합니다.

- **TBN_RESET**

   사용자가 도구 모음 사용자 지정 대화 상자의 콘텐츠를 다시 설정할 때 전송 됩니다. 알림 메시지에 대한 정보를 포함하는 **NMHDR** 구조체를 가리키는 포인터입니다. 처리기에서 특정 값을 반환할 필요가 없습니다.

- **TBN_TOOLBARCHANGE**

   사용자가 도구 모음 컨트롤을 사용자 지정한 후 전송 됩니다. 알림 메시지에 대한 정보를 포함하는 **NMHDR** 구조체를 가리키는 포인터입니다. 처리기에서 특정 값을 반환할 필요가 없습니다.

## <a name="see-also"></a>참고 항목

[CToolBarCtrl 사용](using-ctoolbarctrl.md)<br/>
[컨트롤](controls-mfc.md)
