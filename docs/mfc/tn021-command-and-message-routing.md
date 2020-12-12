---
description: 'TN021: 명령 및 메시지 라우팅에 대 한 자세한 정보'
title: 'TN021: 명령 및 메시지 라우팅'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: 3cc481585fa2f1eacc3deb575e163d5a1644002c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215848"
---
# <a name="tn021-command-and-message-routing"></a>TN021: 명령 및 메시지 라우팅

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 정보는 명령 라우팅 및 디스패치 아키텍처와 일반 창 메시지 라우팅의 고급 항목에 대해 설명 합니다.

여기에 설명 된 아키텍처에 대 한 자세한 내용은 Visual C++을 참조 하세요. 특히 Windows 메시지, 컨트롤 알림 및 명령 간의 차이점을 참조 하세요. 이 노트에서는 인쇄 된 설명서에 설명 된 문제에 대해 잘 알고 있는 것으로 가정 하 고 매우 고급 항목만 다룹니다.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Mfc 1.0 기능이 MFC 2.0 아키텍처로 진화 하는 명령 라우팅 및 디스패치

Windows에는 메뉴 명령, 액셀러레이터 키 및 대화 상자 컨트롤 알림에 대 한 알림을 제공 하기 위해 오버 로드 된 WM_COMMAND 메시지가 있습니다.

파생 클래스에서 명령 처리기 (예: "OnFileNew")를 허용 하 여 `CWnd` 특정 WM_COMMAND에 대 한 응답으로 호출 되는 MFC 1.0는 약간의 영향을 받습니다. 메시지 맵 이라는 데이터 구조와 함께 붙으면 공간 효율성이 매우 높은 명령 메커니즘이 생성 됩니다.

또한 MFC 1.0에는 명령 메시지에서 제어 알림을 분리 하는 추가 기능이 제공 됩니다. 명령은 명령 ID 라고도 하는 16 비트 ID로 표시 됩니다. 명령은 일반적으로 (즉 `CFrameWnd` , 메뉴 선택 또는 번역 된 액셀러레이터)에서 시작 하 여 다양 한 창으로 라우팅합니다.

MFC 1.0는 MDI (다중 문서 인터페이스) 구현에 대해 제한 된 의미로 명령 라우팅을 사용 했습니다. MDI 프레임 창은 활성 MDI 자식 창에 명령을 위임 합니다.

이 기능은 windows 개체가 아닌 더 광범위 한 개체에 의해 명령이 처리 되도록 MFC 2.0에서 일반화 되 고 확장 되었습니다. 이 클래스는 메시지 라우팅에 대 한 보다 공식적인 확장 가능한 아키텍처를 제공 하 고 명령을 처리 하는 것 뿐만 아니라 UI 개체 (예: 메뉴 항목 및 도구 모음 단추)를 업데이트 하 여 현재 명령의 가용성을 반영 합니다.

## <a name="command-ids"></a>명령 ID

명령 라우팅 및 바인딩 프로세스에 대 한 설명은 Visual C++를 참조 하세요. [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) 에는 ID 이름 지정에 대 한 정보가 포함 되어 있습니다.

명령 Id에는 일반 접두사 "ID_"을 사용 합니다. 명령 Id는 >= 0x8000입니다. 명령 ID와 동일한 Id를 가진 STRINGTABLE 리소스가 있는 경우 메시지 줄 또는 상태 표시줄에 명령 설명 문자열이 표시 됩니다.

응용 프로그램의 리소스에서 명령 ID는 다음과 같은 여러 위치에 나타날 수 있습니다.

- 메시지 줄 프롬프트와 동일한 ID를 가진 하나의 STRINGTABLE 리소스에서

- 동일한 명령을 호출 하는 메뉴 항목에 연결 된 많은 메뉴 리소스

- (고급)을 클릭 합니다.

응용 프로그램의 소스 코드에서 명령 ID는 다음과 같은 여러 위치에 나타날 수 있습니다.

- 리소스에 있습니다. 응용 프로그램별 명령 Id를 정의 하는 H (또는 기타 기본 기호 헤더 파일)

- 아마도 도구 모음을 만드는 데 사용 되는 ID 배열입니다.

- ON_COMMAND 매크로.

- ON_UPDATE_COMMAND_UI 매크로 일 수도 있습니다.

현재는 명령 >Id가 0x8000 인 MFC의 유일한 구현은 GOSUB dialogs/command의 구현입니다.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB 명령, 대화 상자에서 명령 아키텍처 사용

라우팅 및 사용 명령에 대 한 명령 아키텍처는 프레임 창, 메뉴 항목, 도구 모음 단추, 대화 상자 단추, 다른 컨트롤 막대 및 요청 시 업데이트 하도록 디자인 된 기타 사용자 인터페이스 요소 및 주 명령 대상 (일반적으로 주 프레임 창)에 명령 또는 컨트롤 Id를 라우팅하는 데 적합 합니다. 주 명령 대상이 명령 또는 컨트롤 알림을 적절 하 게 다른 명령 대상 개체로 라우팅할 수 있습니다.

대화 상자 컨트롤의 컨트롤 ID를 적절 한 명령 ID에 할당 하는 경우 대화 상자 (모달 또는 모덜리스)는 명령 아키텍처의 일부 기능을 활용할 수 있습니다. 대화 상자가 자동으로 지원 되지 않으므로 몇 가지 추가 코드를 작성 해야 할 수도 있습니다.

이러한 모든 기능이 제대로 작동 하려면 명령 Id를 >= 0x8000 이어야 합니다. 많은 대화 상자가 동일한 프레임으로 라우팅될 수 있으므로 공유 명령은 >= 0x8000 이어야 하 고, 특정 대화 상자에서 비공유 IDCs는 <= 0x7FFF 여야 합니다.

단추 집합의 IDC가 적절 한 명령 ID로 설정 된 일반 모달 대화 상자에 일반 단추를 추가할 수 있습니다. 사용자가 단추를 선택 하면 대화 상자 (일반적으로 주 프레임 창)의 소유자가 다른 명령과 마찬가지로 명령을 가져옵니다. 이 명령은 일반적으로 다른 대화 상자를 표시 하는 데 사용 되기 때문에 (첫 번째 대화 상자를 표시 하는 데 사용 됨)에는 GOSUB 명령 이라고 합니다.

대화 상자에서 함수를 호출 하 `CWnd::UpdateDialogControls` 고 주 프레임 창의 주소를 전달할 수도 있습니다. 이 함수는 프레임에 명령 처리기가 있는지 여부에 따라 대화 상자 컨트롤을 활성화 하거나 비활성화 합니다. 이 함수는 응용 프로그램의 유휴 루프에서 컨트롤 막대에 대해 자동으로 호출 되지만이 기능을 사용할 수 있는 일반 대화 상자에 대해 직접 호출 해야 합니다.

## <a name="when-on_update_command_ui-is-called"></a>ON_UPDATE_COMMAND_UI를 호출 하는 경우

모든 프로그램의 메뉴 항목에 대 한 사용/선택 상태를 유지 관리 하면 계산 부담이 큰 문제가 발생할 수 있습니다. 일반적으로 사용자가 팝업을 선택 하는 경우에만 메뉴 항목을 활성화/체크 인하는 것이 좋습니다. 의 MFC 2.0 구현은 `CFrameWnd` WM_INITMENUPOPUP 메시지를 처리 하 고 명령 라우팅 아키텍처를 사용 하 여 ON_UPDATE_COMMAND_UI 처리기를 통해 메뉴의 상태를 확인 합니다.

`CFrameWnd` 는 또한 상태 표시줄 (메시지 줄이 라고도 함)에서 선택한 현재 메뉴 항목을 설명 하는 WM_ENTERIDLE 메시지를 처리 합니다.

Visual C++에서 편집 되는 응용 프로그램의 메뉴 구조는 WM_INITMENUPOPUP 시에 사용할 수 있는 명령을 나타내는 데 사용 됩니다. ON_UPDATE_COMMAND_UI 처리기는 메뉴의 상태나 텍스트를 수정할 수 있으며, 고급 사용의 경우 (예: MRU 목록 또는 OLE 동사 팝업 메뉴) 메뉴를 그리기 전에 메뉴 구조를 수정 합니다.

응용 프로그램이 유휴 루프로 들어가면 도구 모음 (및 기타 컨트롤 막대)에 대해 동일한 종류의 ON_UPDATE_COMMAND_UI 처리가 수행 됩니다. 컨트롤 막대에 대 한 자세한 내용은 *클래스 라이브러리 참조* 및 [기술 참고 31](../mfc/tn031-control-bars.md) 를 참조 하세요.

## <a name="nested-pop-up-menus"></a>중첩 된 팝업 메뉴

중첩 된 메뉴 구조를 사용 하는 경우 팝업 메뉴의 첫 번째 메뉴 항목에 대 한 ON_UPDATE_COMMAND_UI 처리기가 두 가지 다른 경우에 호출 되는 것을 알 수 있습니다.

먼저 팝업 메뉴 자체에 대해이 메서드를 호출 합니다. 팝업 메뉴에는 Id가 없고 팝업 메뉴의 첫 번째 메뉴 항목 ID를 사용 하 여 전체 팝업 메뉴를 참조 하기 때문에이 작업이 필요 합니다. 이 경우 개체의 *m_pSubMenu* 멤버 변수는 `CCmdUI` NULL이 아니고 팝업 메뉴를 가리킵니다.

둘째, 팝업 메뉴의 메뉴 항목을 그리기 직전에 호출 됩니다. 이 경우 ID는 첫 번째 메뉴 항목을 참조 하 고 개체의 *m_pSubMenu* 멤버 변수는 `CCmdUI` NULL입니다.

이렇게 하면 메뉴 항목과는 다른 팝업 메뉴를 사용 하도록 설정할 수 있지만 일부 메뉴 인식 코드를 작성 해야 합니다. 예를 들어 구조가 다음과 같은 중첩 된 메뉴에 있습니다.

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

ID_NEW_SHEET 및 ID_NEW_CHART 명령은 독립적으로 사용 하거나 사용 하지 않도록 설정할 수 있습니다. 둘 중 하나가 사용 하도록 설정 된 경우 **새** 팝업 메뉴를 사용 하도록 설정 해야 합니다.

ID_NEW_SHEET에 대 한 명령 처리기 (팝업의 첫 번째 명령)는 다음과 같습니다.

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

ID_NEW_CHART에 대 한 명령 처리기는 일반적인 업데이트 명령 처리기 이며 다음과 같습니다.

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND 및 ON_BN_CLICKED

**ON_COMMAND** 및 **ON_BN_CLICKED** 에 대 한 메시지 맵 매크로는 동일 합니다. MFC 명령 및 제어 알림 라우팅 메커니즘은 명령 ID를 사용 하 여 라우팅할 위치를 결정 합니다. 컨트롤 알림 코드가 0 인 컨트롤 알림은 명령으로 해석 됩니다 (**BN_CLICKED**).

> [!NOTE]
> 실제로 모든 제어 알림 메시지는 명령 처리기 체인을 통해 전달 됩니다. 예를 들어, 문서 클래스에서 **EN_CHANGE** 에 대 한 컨트롤 알림 처리기를 작성 하는 것이 기술적으로 가능 합니다. 일반적으로이 기능의 실제 응용 프로그램은,이 기능은 클래스 마법사에서 지원 되지 않으며,이 기능을 사용 하면 손상 된 코드를 초래할 수 있기 때문에 일반적으로 권장 되지 않습니다.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>단추 컨트롤의 자동 비활성화를 사용 하지 않도록 설정

사용자가 직접 **CWnd:: UpdateDialogControls** 를 호출 하는 위치를 사용 하 여 대화 상자 표시줄 또는 대화 상자에 단추 컨트롤을 저장 하는 경우 **ON_COMMAND** 또는 **ON_UPDATE_COMMAND_UI** 처리기가 없는 단추가 프레임 워크에서 자동으로 비활성화 됩니다. 일부 경우에는 처리기가 없어도 되지만 단추를 사용할 수 있도록 유지 하는 것이 좋습니다. 이 작업을 수행 하는 가장 쉬운 방법은 더미 명령 처리기를 추가 하는 것입니다 (클래스 마법사를 사용 하는 것이 용이 함).

## <a name="window-message-routing"></a>창 메시지 라우팅

다음은 MFC 클래스에 대 한 몇 가지 고급 항목과 Windows 메시지 라우팅 및 기타 항목에 영향을 주는 방법에 대 한 설명입니다. 이 정보는 간략하게 설명 되어 있습니다. 공용 Api에 대 한 자세한 내용은 *클래스 라이브러리 참조* 를 참조 하세요. 구현 세부 정보에 대 한 자세한 내용은 MFC 라이브러리 소스 코드를 참조 하세요.

모든 **CWnd** 파생 클래스에 대해 매우 중요 한 항목인 창 정리에 대 한 자세한 내용은 [Technical Note 17](../mfc/tn017-destroying-window-objects.md) 을 참조 하세요.

## <a name="cwnd-issues"></a>CWnd 문제

구현 멤버 함수 **CWnd:: OnChildNotify** 는 자식 창 (컨트롤이 라고도 함)에 대해 강력 하 고 확장 가능한 아키텍처를 제공 하 여 해당 부모 (또는 "소유자")로 이동 하는 메시지, 명령 및 제어 알림을 후크 하거나이에 대 한 알림을 받습니다. 자식 창 (/컨트롤)이 c + + **CWnd** 개체 자체인 경우에는 원래 메시지의 매개 변수 (즉, **MSG** 구조체)를 사용 하 여 **onchildnotify** 가상 함수가 먼저 호출 됩니다. 자식 창에서 메시지를 단독으로 두거나, 부모에 대 한 메시지를 수정할 수 있습니다 (드물게 발생).

기본 **CWnd** 구현은 다음 메시지를 처리 하 고 **onchildnotify** 후크를 사용 하 여 자식 창 (컨트롤)에서 메시지에 대 한 첫 번째 액세스를 허용 합니다.

- **WM_MEASUREITEM** 및 **WM_DRAWITEM** (자체 그리기)

- **WM_COMPAREITEM** 및 **WM_DELETEITEM** (자체 그리기)

- **WM_HSCROLL** 및 **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

**Onchildnotify** 후크는 소유자 그리기 메시지를 자체 그리기 메시지로 변경 하는 데 사용 됩니다.

**Onchildnotify** 후크 외에도 scroll 메시지는 추가 라우팅 동작을 포함 합니다. 스크롤 막대와 **WM_HSCROLL** 및 **WM_VSCROLL** 메시지의 출처에 대 한 자세한 내용은 아래를 참조 하세요.

## <a name="cframewnd-issues"></a>CFrameWnd 문제

**CFrameWnd** 클래스는 대부분의 명령 라우팅 및 사용자 인터페이스 업데이트 구현을 제공 합니다. 이는 주로 응용 프로그램의 주 프레임 창 (**CWinApp:: m_pMainWnd**)에 사용 되지만 모든 프레임 창에 적용 됩니다.

주 프레임 창은 메뉴 모음이 있는 창이 며 상태 표시줄 또는 메시지 줄의 부모입니다. 명령 라우팅 및 WM_INITMENUPOPUP에 대 한 위의 설명을 참조 하세요 **.**

**CFrameWnd** 클래스는 활성 뷰를 관리 합니다. 활성 뷰를 통해 라우팅되는 메시지는 다음과 같습니다.

- 모든 명령 메시지 (활성 보기는이에 대 한 첫 번째 액세스 권한을 가집니다.)

- 형제 스크롤 막대에서 메시지를 **WM_HSCROLL** 하 고 **WM_VSCROLL** 합니다 (아래 참조).

- **WM_ACTIVATE** (및 MDI의 **WM_MDIACTIVATE** )는 가상 함수 **CView:: onactivateview** 에 대 한 호출로 설정 됩니다.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd 문제

MDI 프레임 창 클래스는 모두 **CFrameWnd** 에서 파생 되므로 **CFrameWnd** 에 제공 된 것과 동일한 명령 라우팅과 사용자 인터페이스 업데이트를 모두 사용할 수 있습니다. 일반적인 MDI 응용 프로그램에서는 주 프레임 창 (즉, **CMDIFrameWnd** 개체)만 메뉴 모음과 상태 표시줄을 포함 하므로 명령 라우팅 구현의 주요 원본입니다.

일반 라우팅 체계는 활성 MDI 자식 창에서 명령에 처음으로 액세스 하는 것입니다. 기본 **PreTranslateMessage** 함수는 mdi 자식 창 (첫 번째) 및 mdi 프레임 (두 번째) 뿐만 아니라 **TranslateMDISysAccel** (last)에서 일반적으로 처리 하는 표준 mdi 시스템 명령 액셀러레이터에 대 한 액셀러레이터 키 테이블을 처리 합니다.

## <a name="scroll-bar-issues"></a>스크롤 막대 문제

스크롤 메시지 (**WM_HSCROLL** / **onhscroll** 및/또는 **WM_VSCROLL** / **onhscroll**)를 처리 하는 경우 스크롤 막대 메시지의 출처에 의존 하지 않도록 처리기 코드를 작성 해야 합니다. 이는 스크롤 메시지가 진정한 스크롤 막대 컨트롤에서 제공 되거나 스크롤 막대  / 컨트롤이 아닌 스크롤 막대 **WS_VSCROLL** WS_HSCROLL 될 수 있기 때문에 일반적인 Windows 문제가 아닙니다.

MFC는 스크롤 막대 컨트롤을 스크롤 하는 창의 자식이 나 형제로 사용할 수 있도록 확장 합니다. 즉, 스크롤 막대와 스크롤할 창의 부모/자식 관계는 모두 일 수 있습니다. 분할자 창이 있는 공유 스크롤 막대의 경우 특히 중요 합니다. 공유 스크롤 막대 문제에 대 한 자세한 내용은 **CSplitterWnd** 구현에 대 한 자세한 내용은 [Technical Note 29](../mfc/tn029-splitter-windows.md) 를 참조 하세요.

측면 메모에는 생성 시에 지정 된 스크롤 막대 스타일이 트래핑 되 고 Windows에 전달 되지 않는 두 개의 **CWnd** 파생 클래스가 있습니다. 만들기 루틴에 전달 될 때 **WS_HSCROLL** 및 **WS_VSCROLL** 를 독립적으로 설정할 수 있지만 만든 후에는 변경할 수 없습니다. 물론 자신이 만든 창의 WS_SCROLL 스타일 비트를 직접 테스트 하거나 설정 하면 안 됩니다.

**CMDIFrameWnd** 의 경우 **Create** 또는 **loadframe** 에 전달 하는 스크롤 막대 스타일을 사용 하 여 MDICLIENT를 만듭니다. 스크롤할 수 있는 MDICLIENT 영역 (예: Windows 프로그램 관리자)을 사용 하려는 경우 **CMDIFrameWnd** 를 만드는 데 사용 되는 스타일에 스크롤 막대 스타일 (**WS_HSCROLL** &#124; **WS_VSCROLL**)을 모두 설정 해야 합니다.

**CSplitterWnd** 의 경우 스크롤 막대 스타일이 분할자 영역에 대 한 특수 공유 스크롤 막대에 적용 됩니다. 정적 분할자 창의 경우 일반적으로 스크롤 막대 스타일을 설정 하지 않습니다. 동적 분할자 창의 경우 분할 방향에 대해 스크롤 막대 스타일을 설정 하는 것이 일반적입니다. 즉, 열을 분할할 수 있는 경우에는 행을 분할할 수 있는 경우 **WS_HSCROLL** **WS_VSCROLL** 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
