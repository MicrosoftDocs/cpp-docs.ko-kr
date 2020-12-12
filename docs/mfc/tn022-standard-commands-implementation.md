---
description: 'TN022: 표준 명령 구현에 대해 자세히 알아보세요.'
title: 'TN022: 표준 명령 구현'
ms.date: 11/04/2016
f1_keywords:
- vc.commands
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
ms.openlocfilehash: 7c8540dcf0e41e5f6d5f00a4f22568c4df0fcdbe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215809"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: 표준 명령 구현

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 MFC 2.0에서 제공 하는 표준 명령 구현에 대해 설명 합니다. [기술 참고 21](../mfc/tn021-command-and-message-routing.md) 은 다양 한 표준 명령을 구현 하는 데 사용 되는 메커니즘을 설명 하기 때문에 먼저 읽어 보세요.

이 설명에서는 MFC 아키텍처, Api 및 일반적인 프로그래밍 방법에 대해 알고 있다고 가정 합니다. 문서화 된 "구현 전용" Api에 대해서도 설명 합니다. 이는의 기능 또는 MFC에서 프로그래밍 하는 방법에 대 한 학습을 시작 하는 장소가 아닙니다. 자세한 내용과 문서화 된 Api에 대 한 자세한 내용은 Visual C++를 참조 하세요.

## <a name="the-problem"></a>문제

MFC는 헤더 파일 AFXRES.H에 많은 표준 명령 Id를 정의 합니다. 이러한 명령에 대 한 프레임 워크 지원은 다양 합니다. 프레임 워크 클래스가 이러한 명령을 처리 하는 위치와 방법을 이해 하는 것은 프레임 워크가 내부적으로 작동 하는 방식을 보여 주지만 표준 구현을 사용자 지정 하는 방법에 대 한 유용한 정보를 제공 하 고 사용자 고유의 명령 처리기를 구현 하기 위한 몇 가지 기법을 설명 합니다.

## <a name="contents-of-this-technical-note"></a>이 기술 정보 내용

각 명령 ID는 다음 두 섹션에서 설명 합니다.

- 제목: 명령 ID의 기호화 된 이름 (예: ID_FILE_SAVE) 뒤에 명령의 용도 (예: "현재 문서 저장")가 콜론으로 구분 되어 있습니다.

- 명령을 구현 하는 클래스와 기본 구현에서 수행 하는 작업을 설명 하는 하나 이상의 단락

대부분의 기본 명령 구현은 프레임 워크의 기본 클래스 메시지 맵에 미리 있습니다. 파생 클래스에서 명시적 와이어링이 필요한 몇 가지 명령 구현이 있습니다. 이러한 내용은 "참고" 아래에 설명 되어 있습니다. 응용 프로그램 마법사에서 올바른 옵션을 선택한 경우 이러한 기본 처리기는 생성 된 기본 응용 프로그램에서 연결 됩니다.

## <a name="naming-convention"></a>명명 규칙

표준 명령은 가능한 경우 사용 하는 것이 좋습니다. 대부분의 표준 명령은 응용 프로그램 메뉴 모음의 표준 위치에 있습니다. 명령의 기호화 된 이름은 "ID_"로 시작 하 고 그 뒤에 표준 팝업 메뉴 이름, 메뉴 항목 이름을 차례로 입력 합니다. 기호화 된 이름은 대문자로 된 단어를 밑줄로 구분 합니다. 표준 메뉴 항목 이름이 없는 명령의 경우 논리적 명령 이름은 "ID_" (예: ID_NEXT_PANE)로 시작 하 여 정의 됩니다.

"ID_" 접두사를 사용 하 여 메뉴 항목, 도구 모음 단추 또는 다른 명령 사용자 인터페이스 개체에 바인딩하기 위해 디자인 된 명령을 표시 합니다. "ID_" 명령을 처리 하는 명령 처리기는 MFC 명령 아키텍처의 ON_COMMAND 및 ON_UPDATE_COMMAND_UI 메커니즘을 사용 해야 합니다.

명령 아키텍처를 따르지 않는 메뉴 항목에 표준 "IDM_" 접두사를 사용 하 고 사용 하거나 사용 하지 않도록 설정 하는 데 메뉴 관련 코드가 필요한 것이 좋습니다. 물론, MFC 명령 아키텍처를 따라 명령 처리기를 더 강력 하 게 만들 수 있을 뿐만 아니라 도구 모음을 사용할 수 있지만 명령 처리기 코드를 다시 사용할 수 있기 때문에 메뉴 관련 명령의 수는 작아야 합니다.

## <a name="id-ranges"></a>ID 범위

MFC에서 ID 범위를 사용 하는 방법에 대 한 자세한 내용은 [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) 을 참조 하세요.

MFC 표준 명령은 0xE000 범위에 포함 됩니다. 이후 버전의 라이브러리에서 변경 될 수 있으므로 이러한 Id의 특정 값을 사용 하지 마세요.

응용 프로그램은 0x8000 범위에서 0xDFFF의 명령을 정의 해야 합니다.

## <a name="standard-command-ids"></a>표준 명령 Id

각 명령 ID에는 파일 프롬프트에서 찾을 수 있는 표준 메시지 줄 프롬프트 문자열이 있습니다. 스크립트. 해당 메뉴 프롬프트의 문자열 ID는 명령 ID와 동일 해야 합니다.

- ID_FILE_NEW 새/빈 문서를 만듭니다.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   `CWinApp::OnFileNew` 는 응용 프로그램의 문서 템플릿 수에 따라이 명령을 다르게 구현 합니다. 이 하나만 있는 경우 `CDocTemplate` 에 `CWinApp::OnFileNew` 는 해당 형식의 새 문서 뿐만 아니라 적절 한 프레임 및 뷰 클래스를 만듭니다.

   가 두 개 이상 있는 경우 `CDocTemplate` `CWinApp::OnFileNew` 사용자에 게 사용할 문서 유형을 선택할 수 있는 대화 상자 (AFX_IDD_NEWTYPEDLG)를 입력 하 라는 메시지가 표시 됩니다. 선택한는 `CDocTemplate` 문서를 만드는 데 사용 됩니다.

   ID_FILE_NEW를 일반적으로 사용자 지정 하는 것은 다양 한 언어의 문서 유형을 제공 하는 것입니다. 이 경우 자체를 구현 하 `CMyApp::OnFileNew` 고 대신 메시지 맵에 저장할 수 있습니다 `CWinApp::OnFileNew` . 기본 클래스 구현을 호출할 필요가 없습니다.

   ID_FILE_NEW의 또 다른 일반적인 사용자 지정은 각 형식의 문서를 만드는 별도의 명령을 제공 하는 것입니다. 이 경우 ID_FILE_NEW_CHART 및 ID_FILE_NEW_SHEET 같은 새 명령 Id를 정의 해야 합니다.

- ID_FILE_OPEN 기존 문서를 엽니다.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   `CWinApp::OnFileOpen` 에는를 호출 하 고, `CWinApp::DoPromptFileName` `CWinApp::OpenDocumentFile` 열려는 파일의 파일 또는 경로 이름을 가진를 매우 간단 하 게 구현할 수 있습니다. `CWinApp`구현 루틴은 `DoPromptFileName` 표준 FileOpen 대화 상자를 표시 하 고 현재 문서 템플릿에서 가져온 파일 확장명으로 채웁니다.

   ID_FILE_OPEN의 일반적인 사용자 지정 중 하나는 FileOpen 대화 상자를 사용자 지정 하거나 추가 파일 필터를 추가 하는 것입니다. 이를 사용자 지정 하는 권장 방법은 기본 구현을 사용자 지정 FileOpen 대화 상자로 바꾸고 `CWinApp::OpenDocumentFile` 문서의 파일 또는 경로 이름을 사용 하 여를 호출 하는 것입니다. 기본 클래스를 호출할 필요가 없습니다.

- ID_FILE_CLOSE 현재 열려 있는 문서를 닫습니다.

   `CDocument::OnFileClose``CDocument::SaveModified`을 호출 하 여 사용자가 문서를 수정한 후를 저장 하 라는 메시지를 표시 `OnCloseDocument` 합니다. 문서 제거를 비롯 한 모든 닫기 논리는 루틴에서 수행 됩니다 `OnCloseDocument` .

    > [!NOTE]
    >  ID_FILE_CLOSE은 WM_CLOSE 메시지 또는 문서 프레임 창으로 전송 된 SC_CLOSE 시스템 명령과 다르게 작동 합니다. 창을 닫으면 문서를 표시 하는 마지막 프레임 창인 경우에만 문서를 닫습니다. ID_FILE_CLOSE를 사용 하 여 문서를 닫으면 문서를 닫을 뿐만 아니라 문서를 표시 하는 모든 프레임 창이 종료 됩니다.

- ID_FILE_SAVE 현재 문서를 저장 합니다.

   구현에서는 `CDocument::DoSave` 및에 모두 사용 되는 도우미 루틴을 사용 합니다 `OnFileSave` `OnFileSaveAs` . 이전에 저장 하지 않은 문서를 저장 하는 경우 (즉, FileNew의 경우와 같이 경로 이름이 없음) 또는 읽기 전용 문서에서 읽은 문서를 저장 하는 경우 `OnFileSave` 논리는 ID_FILE_SAVE_AS 명령 처럼 동작 하 고 사용자에 게 새 파일 이름을 제공 하도록 요청 합니다. 파일을 열고 저장 하는 실제 프로세스는 가상 함수를 통해 수행 됩니다 `OnSaveDocument` .

   ID_FILE_SAVE를 사용자 지정 하는 두 가지 일반적인 이유는 다음과 같습니다. 저장 하지 않는 문서의 경우 사용자 인터페이스에서 ID_FILE_SAVE 메뉴 항목 및 도구 모음 단추를 제거 하면 됩니다. 또한 문서를 변경 하지 않도록 하 고 (즉, 호출 하지 않음 `CDocument::SetModifiedFlag` ) 프레임 워크가 문서를 저장 하지 않도록 해야 합니다. 디스크 파일이 아닌 다른 위치에 저장 하는 문서의 경우 해당 작업에 대 한 새 명령을 정의 합니다.

   의 경우 `COleServerDoc` 파일 저장 (일반 문서) 및 파일 업데이트 (포함 된 문서의 경우) 모두에 ID_FILE_SAVE 사용 됩니다.

   문서 데이터가 개별 디스크 파일에 저장 되지만 기본 직렬화 구현을 사용 하지 않으려는 경우 `CDocument` 대신를 재정의 해야 `CDocument::OnSaveDocument` `OnFileSave` 합니다.

- ID_FILE_SAVE_AS 현재 문서를 다른 파일 이름으로 저장 합니다.

   `CDocument::OnFileSaveAs`구현에서는와 동일한 도우미 루틴을 사용 합니다 `CDocument::DoSave` `OnFileSave` . `OnFileSaveAs`문서를 저장 하기 전에 문서에 파일 이름이 없는 경우 ID_FILE_SAVE와 마찬가지로 명령이 처리 됩니다. `COleServerDoc::OnFileSaveAs` 일반 문서 데이터 파일을 저장 하거나 다른 응용 프로그램에 포함 된 OLE 개체를 나타내는 서버 문서를 별도 파일로 저장 하는 논리를 구현 합니다.

   ID_FILE_SAVE 논리를 사용자 지정 하는 경우 비슷한 방식으로 ID_FILE_SAVE_AS를 사용자 지정 하거나 "다른 이름으로 저장" 작업을 문서에 적용할 수 없습니다. 메뉴 항목은 필요 하지 않은 경우 메뉴 모음에서 제거할 수 있습니다.

- ID_FILE_SAVE_COPY_AS 새 이름으로 복사본 현재 문서를 저장 합니다.

   `COleServerDoc::OnFileSaveCopyAs` `CDocument::OnFileSaveAs` 문서 개체가 저장 후 기본 파일에 "연결" 되지 않는다는 점을 제외 하 고 구현은와 매우 비슷합니다. 즉, 저장 하기 전에 메모리 내 문서가 "수정" 된 경우에도 "수정" 됩니다. 또한이 명령은 문서에 저장 된 경로 이름 또는 제목에는 영향을 주지 않습니다.

- ID_FILE_UPDATE는 컨테이너에 포함 문서를 저장 하도록 알립니다.

   `COleServerDoc::OnUpdateDocument`구현은 포함을 저장 해야 하는 컨테이너를 단순히 notifiies 합니다. 그런 다음 컨테이너는 포함 된 개체를 저장 하기 위해 적절 한 OLE Api를 호출 합니다.

- ID_FILE_PAGE_SETUP는 응용 프로그램별 페이지 설정/레이아웃 대화 상자를 호출 합니다.

   현재이 대화 상자에는 표준이 없으며 프레임 워크에는이 명령의 기본 구현이 없습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- 표준 인쇄 설정 대화 상자를 호출 ID_FILE_PRINT_SETUP 합니다.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   이 명령은 사용자가이 문서 이상 또는이 응용 프로그램의 모든 문서에 대 한 프린터 및 인쇄 설정을 사용자 지정할 수 있도록 하는 표준 인쇄 설정 대화 상자를 호출 합니다. 전체 시스템에 대 한 기본 프린터 설정을 변경 하려면 제어판을 사용 해야 합니다.

   `CWinApp::OnFilePrintSetup` 에는 개체를 만들고 `CPrintDialog` 구현 함수를 호출 하는 매우 간단한 구현이 있습니다 `CWinApp::DoPrintDialog` . 이렇게 하면 응용 프로그램 기본 프린터 설정이 설정 됩니다.

   이 명령을 사용자 지정 하는 일반적인 요구는 문서를 저장할 때 문서와 함께 저장 되는 문서 단위 프린터 설정을 허용 하는 것입니다. 이렇게 하려면 개체를 만드는 클래스에 메시지 맵 처리기를 추가 하 고 `CDocument` `CPrintDialog` 적절 한 프린터 특성 (일반적으로 *Hdevmode* 및 *hDevNames*)을 사용 하 여 초기화 한 다음를 호출 하 `CPrintDialog::DoModal` 고 변경 된 프린터 설정을 저장 해야 합니다. 강력한 구현을 위해의 구현을 확인 하 여 `CWinApp::DoPrintDialog` 오류를 감지 하 고 `CWinApp::UpdatePrinterSelection` 적절 한 기본값을 처리 하며 시스템 차원의 프린터 변경을 추적 해야 합니다.

- 현재 문서의 표준 인쇄 ID_FILE_PRINT

    > [!NOTE]
    >  이 `CView` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   이 명령은 현재 문서를 인쇄 하 고, 인쇄 프로세스를 시작 합니다. 여기에는 표준 인쇄 대화 상자를 호출 하 고 인쇄 엔진을 실행 하는 작업이 포함 됩니다.

   `CView::OnFilePrint` 이 명령과 주 인쇄 루프를 구현 합니다. 사용자에 게 `CView::OnPreparePrinting` 인쇄 대화 상자를 표시 하는 가상를 호출 합니다. 그런 다음 출력 DC가 프린터로 이동 하도록 준비 하 고, 인쇄 진행률 대화 상자 (AFX_IDD_PRINTDLG)를 표시 하 고, `StartDoc` 이스케이프를 프린터로 보냅니다. `CView::OnFilePrint` 에는 주 페이지 지향 인쇄 반복도 포함 되어 있습니다. 각 페이지에 대해 가상 `CView::OnPrepareDC` `StartPage` 및 이스케이프를 호출한 다음 `CView::OnPrint` 해당 페이지에 대 한 가상을 호출 합니다. 완료 되 면 가상 `CView::OnEndPrinting` 이 호출 되 고 인쇄 진행률 대화 상자가 닫힙니다.

   MFC 인쇄 아키텍처는 인쇄 및 인쇄 미리 보기를 위해 다양 한 방식으로 연결 하도록 디자인 되었습니다. 일반적으로 다양 한 재정의 가능 `CView` 함수를 페이지 기반 인쇄 작업에 적합 하 게 찾을 수 있습니다. 페이지를 사용 하지 않는 출력을 위해 프린터를 사용 하는 응용 프로그램의 경우에만 ID_FILE_PRINT 구현을 대체 해야 합니다.

- 현재 문서에 대 한 인쇄 미리 보기 모드를 입력 ID_FILE_PRINT_PREVIEW 합니다.

    > [!NOTE]
    >  이 `CView` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   `CView::OnFilePrintPreview` 문서화 된 도우미 함수를 호출 하 여 인쇄 미리 보기 모드를 시작 합니다 `CView::DoPrintPreview` . `CView::DoPrintPreview` 는 인쇄 루프의 주 엔진과 마찬가지로 인쇄 미리 보기 루프의 기본 엔진입니다 `OnFilePrint` .

   인쇄 미리 보기 작업은 다양 한 매개 변수를에 전달 하 여 다양 한 방법으로 사용자 지정할 수 있습니다 `DoPrintPreview` . 인쇄 미리 보기 및 사용자 지정 방법에 대 한 세부 정보를 설명 하는 [Technical Note 30](../mfc/tn030-customizing-printing-and-print-preview.md)을 참조 하십시오.

- ID_FILE_MRU_FILE1 ... FILE16 파일 **목록** 에 대 한 명령 id의 범위를 표시 합니다.

   `CWinApp::OnUpdateRecentFileMenu` 는 ON_UPDATE_COMMAND_UI 메커니즘의 고급 사용 중 하나인 업데이트 명령 UI 처리기입니다. 메뉴 리소스에서 ID ID_FILE_MRU_FILE1 단일 메뉴 항목만 정의 해야 합니다. 해당 메뉴 항목은 처음에는 사용할 수 없는 상태로 유지 됩니다.

   MRU 목록이 커지면 더 많은 메뉴 항목이 목록에 추가 됩니다. 표준 `CWinApp` 구현은 기본적으로 가장 최근에 사용 된 파일 4 개로 제한 됩니다. `CWinApp::LoadStdProfileSettings`더 크거나 작은 값을 사용 하 여를 호출 하 여 기본값을 변경할 수 있습니다. MRU 목록은 응용 프로그램의에 저장 됩니다. INI 파일. 이 목록은를 호출 하는 경우 응용 프로그램의 함수에 로드 되며 `InitInstance` `LoadStdProfileSettings` 응용 프로그램이 종료 될 때 저장 됩니다. 또한 MRU update 명령 UI 처리기는 파일 메뉴에 표시 하기 위해 절대 경로를 상대 경로로 변환 합니다.

   `CWinApp::OnOpenRecentFile` 는 실제 명령을 수행 하는 ON_COMMAND 처리기입니다. MRU 목록에서 파일 이름을 가져온 다음 `CWinApp::OpenDocumentFile` 파일을 열고 MRU 목록을 업데이트 하는 작업을 모두 수행 하는를 호출 하기만 하면 됩니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_EDIT_CLEAR 현재 선택을 취소 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 를 사용 하 여이 명령의 구현을 제공 `CEdit::Clear` 합니다. 현재 선택 영역이 없는 경우에는이 명령을 사용할 수 없습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_CLEAR_ALL 전체 문서를 지웁니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다. 예제 구현은 MFC 자습서 샘플 [SCRIBBLE](../overview/visual-cpp-samples.md) 을 참조 하세요.

- ID_EDIT_COPY 현재 선택 영역을 클립보드에 복사 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 을 사용 하 여 현재 선택한 텍스트를 CF_TEXT 클립보드에 복사 하는이 명령의 구현을 제공 `CEdit::Copy` 합니다. 현재 선택 영역이 없는 경우에는이 명령을 사용할 수 없습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- 현재 선택 영역을 클립보드에 ID_EDIT_CUT 잘라냅니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 를 사용 하 여 현재 선택 된 텍스트를 CF_TEXT 클립보드로 잘라내는이 명령의 구현을 제공 `CEdit::Cut` 합니다. 현재 선택 영역이 없는 경우에는이 명령을 사용할 수 없습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_FIND 찾기 작업을 시작 하 여 모덜리스 찾기 대화 상자를 표시 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 는 구현 도우미 함수를 호출 `OnEditFindReplace` 하 여 개인 구현 변수에서 이전 찾기/바꾸기 설정을 사용 하 고 저장 하는이 명령의 구현을 제공 합니다. `CFindReplaceDialog`클래스는 사용자에 게 메시지를 표시 하는 모덜리스 대화 상자를 관리 하는 데 사용 됩니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_PASTE 현재 클립보드 내용을 삽입 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 을 사용 하 여 선택한 텍스트를 바꾸는 현재 클립보드 데이터를 복사 하는이 명령의 구현을 제공 `CEdit::Paste` 합니다. 클립보드에 **CF_TEXT** 없는 경우 명령은 사용할 수 없습니다.

   `COleClientDoc` 는이 명령에 대 한 업데이트 명령 UI 처리기만 제공 합니다. 클립보드에 포함 된 OLE 항목/개체가 포함 되어 있지 않은 경우에는 명령을 사용할 수 없습니다. 실제 붙여넣기를 수행 하는 실제 명령에 대 한 처리기를 작성 해야 합니다. OLE 응용 프로그램에서 다른 형식을 붙여넣을 수도 있는 경우 보기 또는 문서에 사용자 고유의 업데이트 명령 UI 처리기를 제공 해야 합니다 (즉, `COleClientDoc` 명령 대상 라우팅의 앞에 있는 위치).

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

   표준 OLE 구현을 바꾸려면를 사용 `COleClientItem::CanPaste` 합니다.

- ID_EDIT_PASTE_LINK 현재 클립보드 내용의 링크를 삽입 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `COleDocument` 는이 명령에 대 한 업데이트 명령 UI 처리기만 제공 합니다. 클립보드에 linkable OLE item/object가 포함 되어 있지 않으면 명령이 비활성화 됩니다. 실제 붙여넣기를 수행 하는 실제 명령에 대 한 처리기를 작성 해야 합니다. OLE 응용 프로그램에서 다른 형식을 붙여넣을 수도 있는 경우 보기 또는 문서에 사용자 고유의 업데이트 명령 UI 처리기를 제공 해야 합니다 (즉, `COleDocument` 명령 대상 라우팅의 앞에 있는 위치).

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

   표준 OLE 구현을 바꾸려면를 사용 `COleClientItem::CanPasteLink` 합니다.

- ID_EDIT_PASTE_SPECIAL 현재 클립보드 내용을 옵션과 함께 삽입 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` . MFC는이 대화 상자를 제공 하지 않습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_REPEAT 마지막 작업을 반복 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 마지막 찾기 작업을 반복 하기 위해이 명령의 구현을 제공 합니다. 마지막 찾기에 대 한 private 구현 변수가 사용 됩니다. 찾기를 시도할 수 없는 경우에는이 명령을 사용할 수 없습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_REPLACE 바꾸기 작업을 시작 하 여 모덜리스 바꾸기 대화 상자를 표시 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 는 구현 도우미 함수를 호출 `OnEditFindReplace` 하 여 개인 구현 변수에서 이전 찾기/바꾸기 설정을 사용 하 고 저장 하는이 명령의 구현을 제공 합니다. `CFindReplaceDialog`클래스는 사용자에 게 메시지를 표시 하는 모덜리스 대화 상자를 관리 하는 데 사용 됩니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_SELECT_ALL 전체 문서를 선택 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 문서의 모든 텍스트를 선택 하는이 명령의 구현을 제공 합니다. 선택할 텍스트가 없는 경우 명령은 사용할 수 없습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_UNDO 마지막 작업을 실행 취소 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   `CEditView` 을 사용 하 여이 명령의 구현을 제공 `CEdit::Undo` 합니다. 에서 FALSE를 반환 하면이 명령은 사용할 수 없습니다 `CEdit::CanUndo` .

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_EDIT_REDO 마지막 작업을 다시 실행 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 각 파생 클래스에 대해이를 구현 해야 합니다 `CView` .

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_WINDOW_NEW 활성 문서에서 다른 창을 엽니다.

   `CMDIFrameWnd::OnWindowNew` 현재 문서의 문서 템플릿을 사용 하 여이 강력한 기능을 구현 하 여 현재 문서의 다른 뷰를 포함 하는 다른 프레임을 만듭니다.

   대부분 MDI (다중 문서 인터페이스) 창 메뉴 명령과 마찬가지로 활성 MDI 자식 창이 없으면 명령이 비활성화 됩니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다. 추가 보기 또는 프레임 창을 만드는 명령을 제공 하려는 경우 사용자의 명령에 고안 더 좋을 것입니다. 에서 코드를 복제 하 `CMDIFrameWnd::OnWindowNew` 고 원하는 특정 프레임 및 뷰 클래스로 수정할 수 있습니다.

- ID_WINDOW_ARRANGE MDI 창의 아래쪽에 아이콘을 정렬 합니다.

   `CMDIFrameWnd` 구현 도우미 함수에서이 표준 MDI 명령을 구현 `OnMDIWindowCmd` 합니다. 이 도우미는 명령 Id를 MDI Windows 메시지에 매핑하고 따라서 많은 코드를 공유할 수 있습니다.

   대부분의 MDI 창 메뉴 명령과 마찬가지로 활성 MDI 자식 창이 없으면 명령이 비활성화 됩니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_WINDOW_CASCADE 창을 겹치게 계단식으로 배열 합니다.

   `CMDIFrameWnd` 구현 도우미 함수에서이 표준 MDI 명령을 구현 `OnMDIWindowCmd` 합니다. 이 도우미는 명령 Id를 MDI Windows 메시지에 매핑하고 따라서 많은 코드를 공유할 수 있습니다.

   대부분의 MDI 창 메뉴 명령과 마찬가지로 활성 MDI 자식 창이 없으면 명령이 비활성화 됩니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- 타일 창을 가로로 ID_WINDOW_TILE_HORZ 합니다.

   이 명령은 `CMDIFrameWnd` 다른 MDI Windows 메시지를 작업에 사용 하는 것을 제외 하 고 ID_WINDOW_CASCADE와 마찬가지로에서 구현 됩니다.

   응용 프로그램의 기본 타일 방향을 선택 해야 합니다. 이렇게 하려면 창의 "타일" 메뉴 항목에 대 한 ID를 ID_WINDOW_TILE_HORZ 또는 ID_WINDOW_TILE_VERT로 변경 합니다.

- 타일 창을 세로로 ID_WINDOW_TILE_VERT 합니다.

   이 명령은 `CMDIFrameWnd` 다른 MDI Windows 메시지를 작업에 사용 하는 것을 제외 하 고 ID_WINDOW_CASCADE와 마찬가지로에서 구현 됩니다.

   응용 프로그램의 기본 타일 방향을 선택 해야 합니다. 이렇게 하려면 창의 "타일" 메뉴 항목에 대 한 ID를 ID_WINDOW_TILE_HORZ 또는 ID_WINDOW_TILE_VERT로 변경 합니다.

- 분할자에 대 한 키보드 인터페이스를 ID_WINDOW_SPLIT 합니다.

   `CView` 구현에 대해이 명령을 처리 `CSplitterWnd` 합니다. 뷰가 분할자 창의 일부인 경우이 명령은 구현 함수에 위임 `CSplitterWnd::DoKeyboardSplit` 합니다. 그러면 키보드 사용자가 분할자 창을 분할 하거나 분할 취소 하는 데 사용할 수 있는 모드로 분할자를 저장 합니다.

   뷰가 분할자에 없으면이 명령을 사용할 수 없습니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_APP_ABOUT는 정보 대화 상자를 호출 합니다.

   응용 프로그램의 정보 상자에 대 한 표준 구현이 없습니다. 기본 응용 프로그램 마법사가 만든 응용 프로그램은 응용 프로그램에 대 한 사용자 지정 대화 상자 클래스를 만들고 사용자 정보 상자로 사용 합니다. 또한 응용 프로그램 마법사는이 명령을 처리 하 고 대화 상자를 호출 하는 trivial 명령 처리기를 작성 합니다.

   거의 항상이 명령을 구현 합니다.

- ID_APP_EXIT 응용 프로그램을 종료 합니다.

   `CWinApp::OnAppExit` 응용 프로그램의 주 창에 WM_CLOSE 메시지를 전송 하 여이 명령을 처리 합니다. 응용 프로그램의 표준 종료 (더티 파일 등의 메시지 표시)는 구현에 의해 처리 됩니다 `CFrameWnd` .

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다. `CWinApp::SaveAllModified`또는 `CFrameWnd` 닫는 논리를 재정의 하는 것이 좋습니다.

   이 명령을 구현 하도록 선택 하는 경우이 명령 ID를 사용 하는 것이 좋습니다.

- ID_HELP_INDEX에서 도움말 항목을 나열 합니다. .HLP 파일.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   `CWinApp::OnHelpIndex` 는 일반적으로를 호출 하 여이 명령을 처리 `CWinApp::WinHelp` 합니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_HELP_USING 도움말을 사용 하는 방법에 대 한 도움말을 표시 합니다.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   `CWinApp::OnHelpUsing` 는 일반적으로를 호출 하 여이 명령을 처리 `CWinApp::WinHelp` 합니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_CONTEXT_HELP는 SHIFT-F1 도움말 모드로 전환 됩니다.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   `CWinApp::OnContextHelp` 도움말 모드 커서를 설정 하 고, 모달 루프를 입력 하 고, 사용자가 도움말을 볼 창을 선택할 때까지 대기 하 여이 명령을 처리 합니다. MFC 도움말 구현에 대 한 자세한 내용은 [Technical Note 28](../mfc/tn028-context-sensitive-help-support.md) 을 참조 하십시오.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_HELP 현재 컨텍스트에 대 한 도움말을 제공 합니다.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   `CWinApp::OnHelp` 현재 응용 프로그램 컨텍스트에 대 한 올바른 도움말 컨텍스트를 가져와이 명령을 처리 합니다. 이는 간단한 F1 도움말, 메시지 상자에 대 한 도움말 등을 처리 합니다. MFC 도움말 구현에 대 한 자세한 내용은 [Technical Note 28](../mfc/tn028-context-sensitive-help-support.md) 을 참조 하십시오.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_DEFAULT_HELP 컨텍스트에 대 한 기본 도움말이 표시 됩니다.

    > [!NOTE]
    >  이 `CWinApp` 기능을 사용 하려면이를 파생 클래스의 메시지 맵에 연결 해야 합니다.

   이 명령은 일반적으로에 매핑됩니다 `CWinApp::OnHelpIndex` .

   기본 도움말과 도움말 인덱스의 구분이 필요한 경우 다른 명령 처리기를 제공할 수 있습니다.

- 다음 창으로 이동 ID_NEXT_PANE

   `CView` 구현에 대해이 명령을 처리 `CSplitterWnd` 합니다. 뷰가 분할자 창의 일부인 경우이 명령은 구현 함수에 위임 `CSplitterWnd::OnNextPaneCmd` 합니다. 이렇게 하면 활성 뷰가 분할자의 다음 창으로 이동 합니다.

   뷰가 분할자에 없거나 다음 창이 이동할 수 없는 경우에는이 명령을 사용할 수 없습니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- 이전 창으로 이동 ID_PREV_PANE

   `CView` 구현에 대해이 명령을 처리 `CSplitterWnd` 합니다. 뷰가 분할자 창의 일부인 경우이 명령은 구현 함수에 위임 `CSplitterWnd::OnNextPaneCmd` 합니다. 이렇게 하면 활성 뷰가 분할자의 이전 창으로 이동 합니다.

   뷰가 분할자에 없거나 이동할 이전 창이 없는 경우에는이 명령을 사용할 수 없습니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_OLE_INSERT_NEW 새 OLE 개체를 삽입 합니다.

   현재이 명령에 대 한 표준 구현이 없습니다. 파생 클래스에 대해이를 구현 `CView` 하 여 현재 선택 영역에 새 OLE 항목/개체를 삽입 해야 합니다.

   모든 OLE 클라이언트 응용 프로그램은이 명령을 구현 해야 합니다. OLE 옵션을 사용 하는 응용 프로그램 마법사는 `OnInsertObject` 사용자가 완료 해야 하는 뷰 클래스에서의 기본 구현을 만듭니다.

   이 명령의 전체 구현은 MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 예를 참조 하세요.

- OLE 링크 편집 ID_OLE_EDIT_LINKS

   `COleDocument` 표준 OLE 링크 대화 상자의 MFC 제공 구현을 사용 하 여이 명령을 처리 합니다. 이 대화 상자의 구현은 클래스를 통해 액세스 됩니다 `COleLinksDialog` . 현재 문서에 링크가 없는 경우 명령은 사용할 수 없습니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_OLE_VERB_FIRST ... OLE 동사의 마지막 ID 범위

   `COleDocument` 현재 선택 된 OLE 항목/개체에서 지 원하는 동사에 대해이 명령 ID 범위를 사용 합니다. 지정 된 OLE 항목/개체 유형이 0 개 이상의 사용자 지정 동사를 지원할 수 있으므로이는 범위 여야 합니다. 응용 프로그램 메뉴에서 ID가 ID_OLE_VERB_FIRST 인 하나의 메뉴 항목이 있어야 합니다. 프로그램이 실행 되 면 메뉴는 적절 한 메뉴 동사 설명 (또는 여러 동사가 있는 팝업 메뉴)으로 업데이트 됩니다. OLE 메뉴의 관리는 `AfxOleSetEditMenu` 이 명령에 대 한 update 명령 UI 처리기에서 수행 되는에 의해 처리 됩니다.

   이 범위에서 각 명령 ID를 처리 하는 데는 명시적인 명령 처리기가 없습니다. `COleDocument::OnCmdMsg` 는이 범위의 모든 명령 Id를 트래핑 하 여 0부터 시작 하는 동사 번호로 변환 하 고 해당 동사에 대해 서버를 시작 하도록 재정의 됩니다 (사용 `COleClientItem::DoVerb` ).

   이 명령 ID 범위를 사용자 지정 하거나 다른 용도를 사용 하지 않는 것이 좋습니다.

- ID_VIEW_TOOLBAR 도구 모음을 설정/해제 합니다.

   `CFrameWnd` 도구 모음에 표시 되는 상태를 전환 하기 위해이 명령과 업데이트 명령 UI 처리기를 처리 합니다. 도구 모음은 AFX_IDW_TOOLBAR의 자식 창 ID가 있는 프레임의 자식 창 이어야 합니다. 명령 처리기는 실제로 도구 모음 창의 표시 여부를 전환 합니다. `CFrameWnd::RecalcLayout` 는 도구 모음이 있는 프레임 창을 새 상태로 다시 그리는 데 사용 됩니다. 도구 모음이 표시 되 면 업데이트 명령 UI 처리기가 메뉴 항목을 확인 합니다.

   이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다. 추가 도구 모음을 추가 하려는 경우이 명령에 대 한 명령 처리기 및 업데이트 명령 UI 처리기를 복제 하 고 수정 합니다.

- ID_VIEW_STATUS_BAR 상태 표시줄을 설정/해제 합니다.

   이 명령은 `CFrameWnd` 다른 자식 창 ID (AFX_IDW_STATUS_BAR)를 사용 하는 경우를 제외 하 고 ID_VIEW_TOOLBAR와 마찬가지로 구현 됩니다.

## <a name="update-only-command-handlers"></a>Update-Only 명령 처리기

상태 표시줄에서 여러 표준 명령 Id가 표시기로 사용 됩니다. 응용 프로그램 유휴 시간 동안 동일한 업데이트 명령 UI 처리 메커니즘을 사용 하 여 현재 시각적 상태를 표시 합니다. 사용자가 선택할 수 없기 때문에 (즉, 상태 표시줄 창을 푸시할 수 없음) 이러한 명령 Id에 ON_COMMAND 처리기를 사용 하지 않는 것이 좋습니다.

- ID_INDICATOR_CAPS: 단면 잠금 표시기입니다.

- ID_INDICATOR_NUM: NUM lock 표시기입니다.

- ID_INDICATOR_SCRL: SCRL lock 표시기.

- ID_INDICATOR_KANA:가 나 잠금 표시기 (일본어 시스템에만 적용 가능)

이러한 세 가지 모두는 `CFrameWnd::OnUpdateKeyIndicator` 명령 ID를 사용 하 여 적절 한 가상 키에 매핑하는 구현 도우미 인에서 구현 됩니다. 일반적인 구현에서는 `CCmdUI` 적절 한 가상 키가 현재 잠겨 있는지 여부에 따라 개체를 사용 하거나 사용 하지 않도록 설정 합니다 (상태 창 사용 안 함 = 텍스트 없음).

이 명령 처리기를 사용자 지정 하지 않는 것이 좋습니다.

- ID_INDICATOR_EXT: 확장 된 select 표시기입니다.

- ID_INDICATOR_OVR: 겹쳐쓰기 표시기.

- ID_INDICATOR_REC: 기록 표시기입니다.

현재는 이러한 지표에 대 한 표준 구현이 없습니다.

이러한 지표를 구현 하도록 선택 하는 경우 이러한 표시기 Id를 사용 하 고 상태 표시줄에서 표시기의 순서를 유지 하는 것이 좋습니다 (예: EXT, CAP, NUM, SCRL, OVR, REC).

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
