---
description: '자세한 정보: Status-Bar 창의 텍스트 업데이트'
title: 상태 표시줄 창의 텍스트 업데이트
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: 2c3a922072fe117719c1cea803b16ca9c998ce1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263727"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>상태 표시줄 창의 텍스트 업데이트

이 문서에서는 MFC 상태 표시줄 창에 표시 되는 텍스트를 변경 하는 방법을 설명 합니다. 상태 표시줄 ( [Cstatusbar](../mfc/reference/cstatusbar-class.md) 클래스의 창 개체)에는 여러 개의 "창"이 포함 되어 있습니다. 각 창은 정보를 표시 하는 데 사용할 수 있는 상태 표시줄의 사각형 영역입니다. 예를 들어 대부분의 응용 프로그램은 가장 오른쪽 창에 Caps lock, NUM LOCK 및 기타 키의 상태를 표시 합니다. 응용 프로그램은 종종 가장 왼쪽 창 (창 0)에 정보 텍스트를 표시 합니다 (예를 들어 "메시지 창" 이라고 함). 예를 들어, 기본 MFC 상태 표시줄은 메시지 창을 사용 하 여 현재 선택 된 메뉴 항목 또는 도구 모음 단추를 설명 하는 문자열을 표시 합니다. [상태](../mfc/status-bar-implementation-in-mfc.md) 표시줄의 그림은 응용 프로그램 마법사에서 만든 MFC 응용 프로그램의 상태 표시줄을 표시 합니다.

기본적으로 MFC는 `CStatusBar` 창을 만들 때 창을 사용 하도록 설정 하지 않습니다. 창을 활성화 하려면 상태 표시줄의 각 창에 대 한 ON_UPDATE_COMMAND_UI 매크로를 사용 하 고 창을 업데이트 해야 합니다. 창에 WM_COMMAND 메시지가 전송 되지 않으므로 (도구 모음 단추와 같지 않음) 코드를 수동으로 입력 해야 합니다.

예를 들어 한 창에 `ID_INDICATOR_PAGE` 해당 명령 식별자가 있고 문서의 현재 페이지 번호가 포함 되어 있다고 가정 합니다. 다음 절차에서는 상태 표시줄에서 새 창을 만드는 방법을 설명 합니다.

### <a name="to-make-a-new-pane"></a>새 창을 만들려면

1. 창의 명령 ID를 정의 합니다.

   **보기** 메뉴에서 **리소스 뷰** 를 클릭 합니다. 프로젝트 리소스를 마우스 오른쪽 단추로 클릭 하 고 **리소스 기호** 를 클릭 합니다. 리소스 기호 대화 상자에서를 클릭 `New` 합니다. 명령 ID 이름 (예:)을 입력 `ID_INDICATOR_PAGE` 합니다. ID에 대 한 값을 지정 하거나 리소스 기호 대화 상자에서 제안 된 값을 적용 합니다. 예를 들어의 경우 `ID_INDICATOR_PAGE` 기본값을 적용 합니다. 리소스 기호 대화 상자를 닫습니다.

1. 창에 표시할 기본 문자열을 정의 합니다.

   리소스 뷰 열린 상태에서 응용 프로그램에 대 한 리소스 종류를 나열 하는 창에서 **문자열 테이블** 을 두 번 클릭 합니다. **문자열 테이블** 편집기를 열고 **삽입** 메뉴에서 **새 문자열** 을 선택 합니다. 창의 명령 ID (예 `ID_INDICATOR_PAGE` :)를 선택 하 고 "페이지"와 같은 기본 문자열 값을 입력 합니다. 문자열 편집기를 닫습니다. 컴파일러 오류를 방지 하려면 기본 문자열이 필요 합니다.

1. *표시기* 배열에 창을 추가 합니다.

   MAINFRM.CPP 파일에 있습니다. CPP에서 *표시기* 배열을 찾습니다. 이 배열에는 왼쪽에서 오른쪽 순서로 모든 상태 표시줄의 표시기에 대 한 명령 Id가 나열 됩니다. 배열의 해당 지점에서 다음과 같이 창의 명령 ID를 입력 합니다 `ID_INDICATOR_PAGE` .

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

창에 텍스트를 표시 하는 권장 방법은 `SetText` `CCmdUI` 창의 업데이트 처리기 함수에서 클래스의 멤버 함수를 호출 하는 것입니다. 예를 들어 현재 페이지 번호를 포함 하는 *m_nPage* 정수 변수를 설정 하 고를 사용 하 여 `SetText` 이 숫자의 문자열 버전으로 창의 텍스트를 설정 하는 것이 좋습니다.

> [!NOTE]
> `SetText`이 방법이 권장 됩니다. 멤버 함수를 호출 하 여 약간 낮은 수준에서이 작업을 수행할 수 있습니다 `CStatusBar` `SetPaneText` . 이 경우에도 업데이트 처리기가 필요 합니다. 창에 대 한 처리기가 없는 경우 MFC는 창을 자동으로 사용 하지 않도록 설정 하 여 해당 콘텐츠를 지웁니다.

다음 절차에서는 업데이트 처리기 함수를 사용 하 여 창에 텍스트를 표시 하는 방법을 보여 줍니다.

#### <a name="to-make-a-pane-display-text"></a>창에 텍스트를 표시 하려면

1. 명령에 대 한 명령 업데이트 처리기를 추가 합니다.

   (MAINFRM.CPP)에 대해 여기에 표시 된 대로 처리기의 프로토타입을 수동으로 추가 `ID_INDICATOR_PAGE` 합니다. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. 해당 하는입니다. MAINFRM.CPP에 대해 여기에 표시 된 대로 처리기의 정의를 추가 합니다 `ID_INDICATOR_PAGE` . CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   이 처리기의 마지막 세 줄은 텍스트를 표시 하는 코드입니다.

1. 적절 한 메시지 맵에서 (MAINFRM.CPP)에 대해 여기에 표시 된 대로 ON_UPDATE_COMMAND_UI 매크로를 추가 `ID_INDICATOR_PAGE` 합니다. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

*M_nPage* 멤버 변수 (클래스의) 값을 정의 하면 `CMainFrame` 응용 프로그램에서 다른 표시기를 업데이트 하는 것과 같은 방식으로 유휴 처리 중에 페이지 번호가 창에 표시 됩니다. *M_nPage* 변경 되 면 다음 유휴 루프 중에 표시를 변경 합니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [사용자 인터페이스 개체 업데이트 (프로그램 조건이 변경 되 면 도구 모음 단추 및 메뉴 항목을 업데이트 하는 방법)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>참고 항목

[MFC의 상태 표시줄 구현](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar 클래스](../mfc/reference/cstatusbar-class.md)
