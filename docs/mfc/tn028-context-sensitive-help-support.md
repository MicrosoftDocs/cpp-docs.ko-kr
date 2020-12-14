---
description: 'TN028: Context-Sensitive 도움말 지원에 대해 자세히 알아보세요.'
title: 'TN028: 상황에 맞는 도움말 지원'
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: 96dd1d4356ac226d9377e14985de46e3d0f680ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215653"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: 상황에 맞는 도움말 지원

이 참고에서는 MFC에서 도움말 컨텍스트 Id 및 기타 도움말 문제를 할당 하는 규칙을 설명 합니다. 상황에 맞는 도움말 지원에는 Visual C++에서 사용할 수 있는 도움말 컴파일러가 필요 합니다.

> [!NOTE]
> WinHelp를 사용 하 여 상황에 맞는 도움말을 구현 하는 것 외에도 MFC는 HTML 도움말 사용을 지원 합니다. 이 지원 및 HTML 도움말을 사용한 프로그래밍에 대 한 자세한 내용은 [Html 도움말: 프로그램에 대 한 도움말 Context-Sensitive](../mfc/html-help-context-sensitive-help-for-your-programs.md)를 참조 하세요.

## <a name="types-of-help-supported"></a>지원 되는 도움말 형식

Windows 응용 프로그램에서 구현 되는 상황에 맞는 도움말에는 두 가지 유형이 있습니다. 첫 번째 "F1 도움말" 이라고 하는는 현재 활성화 된 개체를 기반으로 하는 적절 한 컨텍스트를 사용 하 여 WinHelp를 시작 하는 것입니다. 두 번째는 "Shift + F1" 모드입니다. 이 모드에서 마우스 커서는 도움말 커서로 바뀌고 사용자가 개체를 클릭 하 여 계속 진행 합니다. 이 시점에서 사용자가 클릭 한 개체에 대 한 도움말을 제공 하기 위해 WinHelp가 시작 됩니다.

Microsoft Foundation Classes은 이러한 형식의 도움말을 구현 합니다. 또한 프레임 워크는 두 가지 간단한 도움말 명령인 도움말 인덱스 및 도움말 사용을 지원 합니다.

## <a name="help-files"></a>도움말 파일

Microsoft Foundation 클래스는 단일 도움말 파일을 가정 합니다. 해당 도움말 파일의 이름과 경로는 응용 프로그램과 동일 해야 합니다. 예를 들어 실행 파일이 C:\MyApplication\MyHelp.exe 경우 도움말 파일은 C:\MyApplication\MyHelp.hlp. 이어야 합니다. [CWinApp 클래스](../mfc/reference/cwinapp-class.md)의 *m_pszHelpFilePath* 멤버 변수를 통해 경로를 설정 합니다.

## <a name="help-context-ranges"></a>도움말 컨텍스트 범위

MFC의 기본 구현에는 도움말 컨텍스트 Id의 할당에 대 한 몇 가지 규칙을 따르는 프로그램이 필요 합니다. 이러한 규칙은 특정 컨트롤에 할당 되는 Id의 범위입니다. 다양 한 도움말 관련 멤버 함수의 다양 한 구현을 제공 하 여 이러한 규칙을 재정의할 수 있습니다.

```
0x00000000 - 0x0000FFFF : user defined
0x00010000 - 0x0001FFFF : commands (menus/command buttons)
0x00010000 + ID_
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)
0x00020000 - 0x0002FFFF : windows and dialogs
0x00020000 + IDR_
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)
0x00030000 - 0x0003FFFF : error messages (based on error string ID)
0x00030000 + IDP_
0x00040000 - 0x0004FFFF : special purpose (non-client areas)
0x00040000 + HitTest area
0x00050000 - 0x0005FFFF : controls (those that are not commands)
0x00040000 + IDW_
```

## <a name="simple-help-commands"></a>간단한 "Help" 명령

Microsoft Foundation Classes에서 구현 하는 두 가지 간단한 도움말 명령이 있습니다.

- [CWinApp:: OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex) 에서 구현 하는 ID_HELP_INDEX

- ID_HELP_USING [CWinApp:: OnHelpUsing 구현 하](../mfc/reference/cwinapp-class.md#onhelpusing) 는

첫 번째 명령은 응용 프로그램에 대 한 도움말 인덱스를 표시 합니다. 두 번째는 WinHelp 프로그램 사용에 대 한 사용자 도움말을 보여 줍니다.

## <a name="context-sensitive-help-f1-help"></a>Context-Sensitive 도움말 (F1 도움말)

F1 키는 일반적으로 주 창의 액셀러레이터 키 테이블에 배치 된 액셀러레이터에 의해 ID_HELP ID가 인 명령으로 변환 됩니다. 주 창이 나 대화 상자에서 ID가 ID_HELP 인 단추를 사용 하 여 ID_HELP 명령을 생성할 수도 있습니다.

ID_HELP 명령이 생성 되는 방법에 관계 없이 명령 처리기에 도달할 때까지 일반 명령으로 라우팅됩니다. MFC 명령 라우팅 아키텍처에 대 한 자세한 내용은 [Technical Note 21](../mfc/tn021-command-and-message-routing.md)을 참조 하십시오. 응용 프로그램에 도움말이 설정 된 경우 ID_HELP 명령은 [CWinApp:: OnHelp](../mfc/reference/cwinapp-class.md#onhelp)에 의해 처리 됩니다. 응용 프로그램 개체는 도움말 메시지를 받은 다음 명령을 적절 하 게 라우팅합니다. 기본 명령 라우팅이 가장 구체적인 컨텍스트를 결정 하는 데 적합 하지 않기 때문에이 작업이 필요 합니다.

`CWinApp::OnHelp` 는 다음과 같은 순서로 WinHelp를 시작 하려고 시도 합니다.

1. `AfxMessageBox`도움말 ID를 사용 하 여 활성 호출을 확인 합니다. 메시지 상자가 현재 활성화 되어 있으면 해당 메시지 상자에 적합 한 컨텍스트를 사용 하 여 WinHelp를 시작 합니다.

1. WM_COMMANDHELP 메시지를 활성 창으로 보냅니다. 이 창이 WinHelp를 시작 하 여 응답 하지 않는 경우 메시지가 처리 되거나 현재 창이 최상위 창인 경우에도 동일한 메시지가 해당 창의 상위 항목으로 전송 됩니다.

1. 주 창에 ID_DEFAULT_HELP 명령을 보냅니다. 이렇게 하면 기본 도움말이 호출 됩니다. 이 명령은 일반적으로에 매핑됩니다 `CWinApp::OnHelpIndex` .

기본 ID 기준 값 (예: 대화 상자와 같은 리소스의 경우 0x10000 및 0x20000)을 전역적으로 재정의 하기 위해 응용 프로그램은 [CWinApp:: WinHelp](../mfc/reference/cwinapp-class.md#winhelp)를 재정의 해야 합니다.

이 기능과 도움말 컨텍스트를 결정 하는 방법을 재정의 하려면 WM_COMMANDHELP 메시지를 처리 해야 합니다. 프레임 워크에서 제공 하는 것 보다 더 구체적인 도움말 라우팅을 제공 하는 것이 좋습니다 .이는 현재 MDI 자식 창의 deep 으로만 이동 하기 때문입니다. 또한 대화 상자 내의 활성 컨트롤이 나 해당 개체의 현재 내부 상태에 따라 특정 창이 나 대화 상자에 대 한 보다 구체적인 도움말을 제공할 수 있습니다.

## <a name="wm_commandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP은 도움말이 요청 될 때 활성 창에서 수신 하는 개인 Windows MFC 메시지입니다. 창에서이 메시지를 받으면 `CWinApp::WinHelp` 창의 내부 상태와 일치 하는 컨텍스트를 사용 하 여를 호출할 수 있습니다.

*lParam*<br/>
현재 사용할 수 있는 도움말 컨텍스트를 포함 합니다. 도움말 컨텍스트가 결정 되지 않은 경우에는 *lParam* 이 0입니다. 의 구현에서는 `OnCommandHelp` *lParam* 의 컨텍스트 ID를 사용 하 여 다른 컨텍스트를 확인 하거나에 전달 하기만 하면 `CWinApp::WinHelp` 됩니다.

*wParam*<br/>
는 사용 되지 않으며 0이 됩니다.

함수에서 `OnCommandHelp` 를 호출 하는 경우 `CWinApp::WinHelp` **TRUE** 를 반환 해야 합니다. **TRUE** 를 반환 하면이 명령을 다른 클래스 및 다른 창으로 라우팅하는 것을 중지 합니다.

## <a name="help-mode-shiftf1-help"></a>도움말 모드 (Shift + F1 도움말)

이는 상황에 맞는 도움말의 두 번째 형식입니다. 일반적으로이 모드는 SHIFT + f 1을 누르거나 메뉴/도구 모음을 통해 입력 합니다. 명령 (ID_CONTEXT_HELP)으로 구현 됩니다. 모달 대화 상자 또는 메뉴가 활성화 되어 있는 동안에는 메시지 필터 후크를 사용 하 여이 명령을 변환 하지 않으므로 응용 프로그램에서 기본 메시지 펌프 ()를 실행 하는 경우에만이 명령을 사용할 수 있습니다 `CWinApp::Run` .

이 모드를 입력 한 후에는 응용 프로그램에서 일반적으로 해당 영역에 대 한 자체 커서를 표시 하는 경우에도 (예: 창 주위의 크기 조정 테두리) 응용 프로그램의 모든 영역에 대 한 도움말 마우스 커서가 표시 됩니다. 사용자는 마우스나 키보드를 사용 하 여 명령을 선택할 수 있습니다. 명령을 실행 하는 대신 해당 명령의 도움말이 표시 됩니다. 또한 사용자는 화면에서 표시 되는 개체 (예: 도구 모음의 단추)를 클릭할 수 있고 해당 개체에 대 한 도움말이 표시 됩니다. 이 도움말 모드는에서 제공 됩니다 `CWinApp::OnContextHelp` .

이 루프를 실행 하는 동안 메뉴에 액세스 하는 키를 제외 하 고 모든 키보드 입력은 비활성 상태입니다. 또한 `PreTranslateMessage` 사용자가 액셀러레이터 키를 누르고 해당 명령에 대 한 도움말을 받을 수 있도록 하기 위해를 통해 여전히 명령 변환이 수행 됩니다.

`PreTranslateMessage`SHIFT + F1 도움말 모드에서 발생 하지 않아야 하는 함수에서 특정 변환이 나 작업을 수행 하는 경우 해당 작업을 수행 하기 전에의 *m_bHelpMode* 멤버를 확인 해야 합니다 `CWinApp` . 를 `CDialog` `PreTranslateMessage` 호출 하기 전에의 구현에서이 `IsDialogMessage` 를 확인 합니다. 그러면 SHIFT + F1 모드 중 모덜리스 대화 상자에서 "대화 상자 탐색" 키를 사용할 수 없습니다. 또한 `CWinApp::OnIdle` 이 루프 중에가 계속 호출 됩니다.

사용자가 메뉴에서 명령을 선택 하는 경우 해당 명령에 대 한 도움말로 처리 됩니다 (WM_COMMANDHELP을 통해 아래 참조). 사용자가 응용 프로그램 창의 표시 영역을 클릭 하면 비클라이언트 클릭 인지 또는 클라이언트 클릭 인지를 결정 하는 작업이 수행 됩니다. `OnContextHelp` 비클라이언트 클릭에 대 한 클라이언트 클릭 자동 매핑을 처리 합니다. 클라이언트 클릭 인 경우 클릭 한 창에 WM_HELPHITTEST를 보냅니다. 해당 창에서 0이 아닌 값을 반환 하는 경우 해당 값이 도움말의 컨텍스트로 사용 됩니다. 0을 반환 하는 경우는 `OnContextHelp` 부모 창 (및 해당 부모 등)을 시도 합니다. 도움말 컨텍스트를 확인할 수 없는 경우 기본적으로 기본 창에 ID_DEFAULT_HELP 명령을 보내고 (일반적으로)에 매핑됩니다 `CWinApp::OnHelpIndex` .

## <a name="wm_helphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST는 SHIFT + F1 도움말 모드에서 클릭 한 활성 창에서 받은 MFC private windows 메시지입니다. 창에서이 메시지를 받으면 WinHelp에서 사용할 **DWORD** 도움말 ID를 반환 합니다.

LOWORD (lParam)는 창의 클라이언트 영역을 기준으로 마우스를 클릭 한 X 축 장치 좌표를 포함 합니다.

WORD (lParam)는 Y 축 좌표를 포함 합니다.

*wParam*<br/>
는 사용 되지 않으며 0이 됩니다. 반환 값이 0이 아니면 해당 컨텍스트를 사용 하 여 WinHelp를 호출 합니다. 반환 값이 0 이면 부모 창에 도움말을 쿼리 합니다.

대부분의 경우 이미 있을 수 있는 적중 테스트 코드를 활용할 수 있습니다. WM_HELPHITTEST 메시지를 처리 하는 예제는의 구현을 참조 하십시오 `CToolBar::OnHelpHitTest` . 코드는의 단추 및 도구 설명에 사용 되는 적중 테스트 코드를 활용 합니다 `CControlBar` .

## <a name="mfc-application-wizard-support-and-makehm"></a>MFC 응용 프로그램 마법사 지원 및 MAKEHM

MFC 응용 프로그램 마법사는 도움말 파일 (cnt 및 .hpj 파일)을 빌드하는 데 필요한 파일을 만듭니다. 또한 Microsoft 도움말 컴파일러에서 허용 하는 여러 개의 미리 작성 된 .rtf 파일도 포함 합니다. 대부분의 항목은 완료 되었지만 특정 응용 프로그램에 대해 수정 해야 할 수도 있습니다.

"도움말 매핑" 파일의 자동 생성은 MAKEHM 이라는 유틸리티에서 지원 됩니다. MAKEHM 유틸리티는 응용 프로그램의 리소스를 변환할 수 있습니다. H 파일의 도움말 매핑 파일입니다. 예를 들어:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

다음과 같이 변환 됩니다.

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

이 형식은 항목 이름 (왼쪽에 있는 기호)과 컨텍스트 Id (오른쪽의 숫자)를 매핑하는 도움말 컴파일러의 기능과 호환 됩니다.

MAKEHM에 대 한 소스 코드는 MFC 프로그래밍 유틸리티 샘플 [MAKEHM](../overview/visual-cpp-samples.md)에서 사용할 수 있습니다.

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>MFC 응용 프로그램 마법사를 실행 한 후 도움말 지원 추가

응용 프로그램에 도움말을 추가 하는 가장 좋은 방법은 응용 프로그램을 만들기 전에 MFC 응용 프로그램 마법사의 고급 기능 페이지에서 "상황에 맞는 도움말" 옵션을 확인 하는 것입니다. 이렇게 하면 MFC 응용 프로그램 마법사가 필요한 메시지 맵 항목을 파생 클래스에 자동으로 추가 하 여 `CWinApp` 도움말을 지원 합니다.

## <a name="help-on-message-boxes"></a>메시지 상자에 대 한 도움말

메시지 상자에 대 한 도움말 (경고 라고도 함)은 `AfxMessageBox` WINDOWS API에 대 한 래퍼로 함수를 통해 지원 됩니다 `MessageBox` .

에는 두 가지 버전이 있습니다 `AfxMessageBox` . 하나는 문자열 ID에 사용 하 고 다른 하나는 문자열 ()에 대 한 포인터와 함께 사용 됩니다 `LPCSTR` .

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

두 경우 모두 선택적 도움말 ID가 있습니다.

첫 번째 경우에 nIDHelp의 기본값은 0 이며이 메시지 상자에 대 한 도움말이 없음을 나타냅니다. 사용자가 F1 키를 누를 때 메시지 상자가 활성화 되어 있는 경우에는 사용자에 게 도움말이 표시 되지 않습니다 (응용 프로그램이 도움말을 지 원하는 경우에도). 바람직하지 않은 경우 nIDHelp에 대 한 도움말 ID를 제공 해야 합니다.

두 번째 경우에 nIDHelp의 기본값은-1입니다 .이 값은 도움말 ID가 nIDPrompt와 동일 함을 나타냅니다. 도움말은 물론 응용 프로그램이 도움말을 사용할 수 있는 경우에만 작동 합니다. 메시지 상자에 도움말이 지원 되지 않도록 하려면 nIDHelp에 0을 지정 해야 합니다. 메시지를 사용 하도록 설정 하는 것이 좋습니다. 하지만 nIDPrompt와 다른 도움말 ID를 원하는 경우 nIDPrompt의 nIDHelp에 대해 양수 값을 제공 하면 됩니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
