---
description: '자세한 정보: 연습: MFC Scribble 응용 프로그램 업데이트 (1 부)'
title: '연습: MFC Scribble 응용 프로그램 업데이트 (1 부)'
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: bb60e535031670eddc84e7170431ad6622d434b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142976"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>연습: MFC Scribble 응용 프로그램 업데이트 (1 부)

이 연습에서는 리본 메뉴 사용자 인터페이스를 사용하여 기존 MFC 애플리케이션을 수정하는 방법을 보여 줍니다. Visual Studio는 Office 2007 리본과 Windows 7 Scenic 리본을 지원합니다. 리본 사용자 인터페이스에 대 한 자세한 [내용은 리본을 참조 하십시오](/windows/win32/uxguide/cmd-ribbons).

이 연습에서는 마우스를 사용하여 줄 그리기를 만들 수 있는 클래식 Scribble 1.0 MFC 샘플을 수정합니다. 이 연습 부분에서는 리본 표시줄에 표시되도록 Scribble 샘플을 수정하는 방법을 보여 줍니다. [2 부](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) 는 리본 표시줄에 더 많은 단추를 추가 합니다.

## <a name="prerequisites"></a>사전 요구 사항

[Scribble 1.0 MFC 샘플](https://github.com/microsoft/VCSamples/tree/master/VC2010Samples/MFC/general/Scribble)입니다. Visual Studio 2017 이상으로 변환 하는 방법에 대 한 도움말은 [포팅 가이드: MFC Scribble](../porting/porting-guide-mfc-scribble.md)을 참조 하세요.

## <a name="sections"></a><a name="top"></a> 섹션이

이 연습 부분에는 다음 단원이 있습니다.

- [기본 클래스 대체](#replaceclass)

- [프로젝트에 비트맵 추가](#addbitmap)

- [프로젝트에 리본 리소스 추가](#addribbon)

- [리본 표시줄의 인스턴스 만들기](#createinstance)

- [리본 범주 추가](#addcategory)

- [응용 프로그램의 모양 설정](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a> 기본 클래스 바꾸기

메뉴를 지원하는 애플리케이션을 리본을 지원하는 애플리케이션으로 변환하려면 업데이트된 기본 클래스에서 애플리케이션 프레임 창 및 도구 모음 클래스를 파생시켜야 합니다. (원래 Scribble 샘플을 수정 하지 않는 것이 좋습니다. 대신 Scribble 프로젝트를 정리 하 고 다른 디렉터리에 복사한 다음 복사본을 수정 합니다.

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Scribble 애플리케이션에서 기본 클래스를 대체하려면

1. Scribble에서 `CScribbleApp::InitInstance` [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)에 대 한 호출이 포함 되어 있는지 확인 합니다.

1. *.Pch* 파일 (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에 다음 코드를 추가 합니다.

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. `CScribbleApp` [CWinAppEx 클래스](../mfc/reference/cwinappex-class.md)에서 파생 되도록 클래스의 정의를 수정 합니다.

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Windows 애플리케이션이 사용자 기본 설정 데이터를 저장하기 위해 초기화(.ini) 파일을 사용한 경우 Scribble 1.0이 작성됩니다. 초기화 파일 대신 Scribble을 수정하여 레지스트리에 사용자 기본 설정을 저장합니다. 레지스트리 키와 기본 설정을 설정하려면 `CScribbleApp::InitInstance` 문 뒤의 `LoadStdProfileSettings()`에서 다음 코드를 입력합니다.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. MDI(다중 문서 인터페이스) 애플리케이션에 대한 주 프레임은 더 이상 `CMDIFrameWnd` 클래스로부터 파생되지 않습니다. 대신 [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) 클래스에서 파생 됩니다.

    mainfrm.h 및 mainfrm.cpp 파일에서 `CMDIFrameWnd`의 모든 참조를 `CMDIFrameWndEx`로 대체합니다.

1. childfrm.h 및 childfrm.cpp 파일에서 `CMDIChildWnd`를 `CMDIChildWndEx`로 대체합니다.

    Childfrm에 있습니다. h 파일,를 `CSplitterWnd` 로 바꿉니다 `CSplitterWndEx` .

1. 새 MFC 클래스를 사용하여 도구 모음 및 상태 표시줄을 수정합니다.

    mainfrm.h 파일에서

    1. `CToolBar`을 `CMFCToolBar`로 바꿉니다.

    1. `CStatusBar`을 `CMFCStatusBar`로 바꿉니다.

1. mainfrm.cpp 파일에서

    1. `m_wndToolBar.SetBarStyle`을 `m_wndToolBar.SetPaneStyle`로 바꿉니다.

    1. `m_wndToolBar.GetBarStyle`을 `m_wndToolBar.GetPaneStyle`로 바꿉니다.

    1. `DockControlBar(&m_wndToolBar)`을 `DockPane(&m_wndToolBar)`로 바꿉니다.

1. ipframe.cpp 파일에서 코드의 다음 세 줄을 주석으로 처리합니다.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a> 프로젝트에 비트맵 추가

이 연습의 다음 네 개의 단계에서는 비트맵 리소스가 필요합니다. 다음과 같은 다양 한 방법으로 적절 한 비트맵을 얻을 수 있습니다.

- [리소스 편집기](../windows/resource-editors.md) 를 사용 하 여 비트맵을 직접 작성 합니다. 또는 리소스 편집기를 사용 하 여 Visual Studio에 포함 되어 있으며 [Visual studio 이미지 라이브러리](/visualstudio/designers/the-visual-studio-image-library)에서 다운로드할 수 있는 이동식 네트워크 그래픽 (.png) 이미지에서 비트맵을 조합할 수 있습니다.

    그러나 **리본** 사용자 인터페이스에서는 특정 비트맵이 투명 이미지를 지원 해야 합니다. 투명 비트맵은 24 비트 색의 빨강, 녹색 및 파랑 구성 요소를 지정 하 고 8 비트는 색의 투명도를 지정 하는 *알파 채널* 을 정의 하는 32 비트 픽셀을 사용 합니다. 현재 리소스 편집기에서는 볼 수는 있지만 32비트 픽셀로 비트맵을 수정할 수 없습니다. 따라서, 리소스 편집기 대신에 외부 이미지 편집기를 사용하여 투명한 비트맵을 조작합니다.

- 프로젝트의 다른 애플리케이션에서 적절한 리소스 파일을 복사한 다음 해당 파일에서 비트맵을 가져옵니다.

이 연습에서는 [연습: MFC를 사용 하 여 리본 응용 프로그램 만들기](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)에서 만든 예제에서 리소스 파일을 복사 합니다.

### <a name="to-add-bitmaps-to-the-project"></a>프로젝트에 비트맵을 추가하려면

1. 파일 탐색기를 사용 하 여 리본 예제의 resources 디렉터리 ()에 있는 다음 .bmp 파일을 `res` Scribble 프로젝트의 리소스 디렉터리 ()에 복사 합니다 `res` .

   1. Scribble 프로젝트에 main.bmp를 복사합니다.

   1. Scribble 프로젝트에 filesmall.bmp 및 filelarge.bmp를 복사합니다.

   1. filelarge.bmp 및 filesmall.bmp 파일의 새 복사본을 만들고 리본 예제에서 복사본을 저장 합니다. 해당 복사본의 이름을 homesmall.bmp 및 homelarge.bmp로 바꾼 다음 Scribble 프로젝트로 복사본을 이동합니다.

   1. toolbar.bmp 파일의 복사본을 만들고 리본 예제에서 복사본을 저장 합니다. 복사본의 이름을 panelicons.bmp로 바꾼 다음 Scribble 프로젝트로 복사본을 이동합니다.

1. MFC 애플리케이션에 대한 비트맵을 가져옵니다. **리소스 뷰** 에서 **scribble** 노드를 두 번 클릭 하 고 **비트맵** 노드를 두 번 클릭 한 다음 **리소스 추가** 를 클릭 합니다. 표시 되는 대화 상자에서 **가져오기** 를 클릭 합니다. 디렉터리로 이동 하 고 `res` main.bmp 파일을 선택한 다음 **열기** 를 클릭 합니다.

   main.bmp 비트맵에는 26x26 이미지가 포함됩니다. 비트맵의 ID를로 변경 `IDB_RIBBON_MAIN` 합니다.

1. **응용 프로그램** 단추에 연결 된 파일 메뉴에 대 한 비트맵을 가져옵니다.

   1. 11 개의 16x16 (16x176) 이미지를 포함 하는 filesmall.bmp 파일을 가져옵니다. 비트맵의 ID를로 변경 `IDB_RIBBON_FILESMALL` 합니다.

   > [!NOTE]
   > 처음 8 개의 16x16 이미지 (16x128)만 필요 하기 때문에 필요에 따라이 비트맵의 오른쪽 너비를 176에서 128로 자를 수 있습니다.

   1. 9 개의 32x32 (32x288) 이미지를 포함 하는 filelarge.bmp을 가져옵니다. 비트맵의 ID를로 변경 `IDB_RIBBON_FILELARGE` 합니다.

1. 리본 범주와 패널에 대한 비트맵을 가져옵니다. 리본 표시줄의 각 탭은 범주이며 텍스트 레이블 및 선택적 이미지로 구성되어 있습니다.

   1. 작은 단추 비트맵에 대 한 11 개의 16x16 이미지를 포함 하는 homesmall.bmp 비트맵을 가져옵니다. 비트맵의 ID를로 변경 `IDB_RIBBON_HOMESMALL` 합니다.

   1. 대량 단추 비트맵에 대 한 8 개의 32x32 이미지를 포함 하는 homelarge.bmp 비트맵을 가져옵니다. 비트맵의 ID를로 변경 `IDB_RIBBON_HOMELARGE` 합니다.

1. 크기가 조정된 리본 패널의 비트맵을 가져옵니다. 전체 창을 표시하기에 리본이 너무 작다면 크기 조정 작업 후에 이러한 비트맵 또는 패널 아이콘이 사용됩니다.

   1. 8개의 16x16 이미지가 포함된 panelicons.bmp 비트맵을 가져옵니다. **비트맵 편집기** 의 **속성** 창에서 비트맵의 너비를 64 (16x64)으로 조정 합니다. 비트맵의 ID를로 변경 `IDB_PANEL_ICONS` 합니다.

   > [!NOTE]
   > 처음 네 개의 16x16 이미지 (16x64)만 필요 하기 때문에 필요에 따라이 비트맵의 오른쪽 너비를 128에서 64로 자를 수 있습니다.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a> 프로젝트에 리본 리소스 추가

메뉴를 사용 하는 응용 프로그램을 리본을 사용 하는 응용 프로그램으로 변환 하는 경우 기존 메뉴를 제거 하거나 사용 하지 않도록 설정할 필요가 없습니다. 리본 리소스를 만들고 리본 단추를 추가한 다음 새 단추를 기존 메뉴 항목과 연결 하기만 하면 됩니다. 메뉴가 더 이상 표시 되지 않지만 리본 표시줄의 메시지는 메뉴를 통해 라우팅되고 메뉴 바로 가기는 계속 작동 합니다.

리본은 리본의 왼쪽 상단에 있는 단추와 하나 이상의 범주 탭으로 구성 된 **응용 프로그램** 단추로 구성 됩니다. 각 범주 탭에는 리본 단추 및 컨트롤에 대한 컨테이너 역할을 하는 패널이 하나 이상 포함되어 있습니다. 다음 절차에서는 리본 리소스를 만든 다음 **응용 프로그램** 단추를 사용자 지정 하는 방법을 보여 줍니다.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>프로젝트에 리본 리소스를 추가하려면

1. **솔루션 탐색기** 에서 Scribble 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **리소스 추가** 를 클릭 합니다.

1. **리소스 추가** 대화 상자에서 **리본** 을 선택한 다음 **새로 만들기** 를 클릭 합니다.

   Visual Studio에서는 리본 리소스를 만들어 디자인 뷰에서 엽니다. 리본 리소스 ID는 리소스 뷰 표시 되는입니다 `IDR_RIBBON1` .  리본에는 범주 하나와 패널 하나가 포함되어 있습니다.

1. 속성을 수정 하 여 **응용 프로그램** 단추를 사용자 지정할 수 있습니다. 이 코드에 사용되는 메시지 ID는 Scribble 1.0에 대한 메뉴에 이미 정의되어 있습니다.

1. 디자인 뷰에서 **응용 프로그램** 단추를 클릭 하 여 해당 속성을 표시 합니다. 속성 값을 다음과 같이 변경 합니다. **이미지** - `IDB_RIBBON_MAIN` , **프롬프트** `File` , **키** , `f` **큼 이미지** `IDB_RIBBON_FILELARGE` 및 **작은 이미지** `IDB_RIBBON_FILESMALL` .

1. 다음과 같이 수정 하면 사용자가 **응용 프로그램** 단추를 클릭할 때 표시 되는 메뉴가 만들어집니다. **주 항목** 옆에 있는 줄임표 (**...**)를 클릭 하 여 **항목 편집기** 를 엽니다.

   1. **항목** 유형 **단추** 를 선택 하 고 **추가** 를 클릭 하 여 단추를 추가 합니다. **캡션** 을 `&New` , **ID** 에서로 `ID_FILE_NEW` , **이미지** 를로 `0` , **이미지를 큼** 으로 변경 `0` 합니다.

   1. **추가** 를 클릭 하 여 단추를 추가 합니다. **캡션** 을로 `&Save` , **ID** 를로, `ID_FILE_SAVE` **이미지** 를로 `2` , 이미지를으로 **크게** 변경 `2` 합니다.

   1. **추가** 를 클릭 하 여 단추를 추가 합니다. **캡션** 을로 `Save &As` , **ID** 를로, `ID_FILE_SAVE_AS` **이미지** 를로 `3` , 이미지를으로 **크게** 변경 `3` 합니다.

   1. **추가** 를 클릭 하 여 단추를 추가 합니다. **캡션** 을로 `&Print` , **ID** 를로, `ID_FILE_PRINT` **이미지** 를로 `4` , 이미지를으로 **크게** 변경 `4` 합니다.

   1. **항목** 형식을 **구분 기호** 로 변경한 다음 **추가** 를 클릭 합니다.

   1. **항목** 형식을 **단추로** 변경 합니다. **추가** 를 클릭 하 여 다섯 번째 단추를 추가 합니다. **캡션** 을로 `&Close` , **ID** 를로, `ID_FILE_CLOSE` **이미지** 를로 `5` , 이미지를으로 **크게** 변경 `5` 합니다.

1. 다음과 같이 수정 하면 이전 단계에서 만든 **인쇄** 단추 아래에 하위 메뉴가 만들어집니다.

   1. **인쇄** 단추를 클릭 하 고 **항목** 종류를 **레이블** 으로 변경한 다음 **삽입** 을 클릭 합니다. **캡션을** 로 변경 `Preview and print the document` 합니다.

   1. **인쇄** 단추를 클릭 하 고 **항목** 형식을 **단추로** 변경한 다음 **삽입** 을 클릭 합니다. **캡션** 을로 `&Print` , **ID** 를로, `ID_FILE_PRINT` **이미지** 를로 `4` , 이미지를으로 **크게** 변경 `4` 합니다.

   1. **인쇄** 단추를 클릭 한 다음 **삽입** 을 클릭 하 여 단추를 추가 합니다. **캡션** 을로 `&Quick Print` , **ID** 를로, `ID_FILE_PRINT_DIRECT` **이미지** 를로 `7` , 이미지를으로 **크게** 변경 `7` 합니다.

   1. **인쇄** 단추를 클릭 한 다음 **삽입** 을 클릭 하 여 다른 단추를 추가 합니다. **캡션** 을로 `Print Pre&view` , **ID** 를로, `ID_FILE_PRINT_PREVIEW` **이미지** 를로 `6` , 이미지를으로 **크게** 변경 `6` 합니다.

   1. 이제 **주 항목** 을 수정 했습니다. **닫기** 를 클릭 하 여 **항목 편집기** 를 종료 합니다.

1. 다음 수정 내용은 **응용 프로그램** 단추 메뉴의 아래쪽에 표시 되는 종료 단추를 만듭니다.

   1. **솔루션 탐색기** 에서 **리소스 뷰** 탭을 선택 합니다.
   1. **속성** 창에서 **단추** 옆에 있는 줄임표 (**...**)를 클릭 하 여 **항목 편집기** 를 엽니다.

   1. **항목** 유형 **단추** 를 선택 하 고 **추가** 를 클릭 하 여 단추를 추가 합니다. **캡션** 을로 `E&xit` , **ID** 를로 `ID_APP_EXIT` , **이미지** 를로 변경 `8` 합니다.

   1. **단추** 를 수정 했습니다. **닫기** 를 클릭 하 여 **항목 편집기** 를 종료 합니다.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a> 리본 표시줄의 인스턴스 만들기

다음 단계에서는 애플리케이션 시작 시 리본 표시줄의 인스턴스를 만드는 방법을 보여 줍니다. 애플리케이션에 리본 표시줄을 추가하려면 mainfrm.h 파일에 리본 표시줄을 선언합니다. 그런 다음 mainfrm.cpp 파일에서 리본 리소스를 로드하는 코드를 작성합니다.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>리본 표시줄의 인스턴스를 만들려면

1. mainfrm.h 파일에서 주 프레임에 대한 클래스 정의인 `CMainFrame`의 보호된 섹션에 데이터 멤버를 추가합니다. 이 멤버는 리본 표시줄에 대 한 멤버입니다.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Mainfrm.cpp 파일에서 함수 끝의 마지막 문 앞에 다음 코드를 추가 합니다 **`return`** `CMainFrame::OnCreate` . 리본 표시줄의 인스턴스를 만듭니다.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a> 리본 리소스 사용자 지정

이제 **응용 프로그램** 단추를 만들었으므로 리본에 요소를 추가할 수 있습니다.

> [!NOTE]
> 이 연습에서는 모든 패널에 대해 동일한 패널 아이콘을 사용합니다. 그러나 다른 아이콘을 표시하기 위해 다른 이미지 목록 인덱스를 사용할 수 있습니다.

### <a name="to-add-a-home-category-and-edit-panel"></a>홈 범주 및 편집 패널을 추가하려면

1. Scribble 프로그램에서는 하나의 범주만 필요로 합니다. 디자인 뷰의 **도구 상자** 에서 **범주** 를 두 번 클릭 하 여 하나를 추가 하 고 해당 속성을 표시 합니다. 속성 값을 다음과 같이 변경 합니다. **캡션** `&Home` , **초대형 이미지** `IDB_RIBBON_HOMELARGE` , **작은 이미지** `IDB_RIBBON_HOMESMALL` .

1. 각 리본 범주는 명명된 패널로 구성되어 있습니다. 각 패널에는 관련 작업을 완료 하는 컨트롤 집합이 포함 되어 있습니다. 이 범주에는 한 패널이 있습니다. **패널** 을 클릭 한 다음 **캡션** 을로 변경 `Edit` 합니다.

1. **편집** 패널에 문서의 내용 지우기를 담당 하는 단추를 추가 합니다. 이 단추에 대 한 메시지 ID가 이미 메뉴 리소스에 정의 되어 있습니다 `IDR_SCRIBBTYPE` . 단추 `Clear All` 텍스트와 단추를 데코레이팅하는 비트맵의 인덱스로를 지정 합니다. **도구 상자** 를 연 다음 **단추** 를 **편집** 패널로 끕니다. 단추를 클릭 한 다음 **캡션** 을 `Clear All` , **ID** 를 `ID_EDIT_CLEAR_ALL` , **이미지 인덱스** 를 `0` , **초대형 이미지 인덱스** 를로 변경 `0` 합니다.

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다. Scribble 애플리케이션은 표시되어야 하며 메뉴 모음 대신 창의 위쪽에 리본 표시줄이 있어야 합니다. 리본 표시줄에는 하나의 범주, **홈** 이 있어야 하 고, **홈** 패널은 **편집** 이 있어야 합니다. 추가한 리본 단추는 기존 이벤트 처리기와 연결 되어야 하며 **열기**, **닫기**, **저장**, **인쇄** 및 **모두 지우기** 단추가 예상 대로 작동 해야 합니다.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a> 응용 프로그램의 모양 설정

*비주얼 관리자* 는 응용 프로그램에 대 한 모든 그리기를 제어 하는 전역 개체입니다. 원래 Scribble 애플리케이션은 Office 2000 UI(사용자 인터페이스) 스타일을 사용하므로 해당 애플리케이션이 더 이상 사용되지 않는 것처럼 보일 수 있습니다. Office 2007 애플리케이션과 비슷하도록 Office 2007 비주얼 관리자를 사용하여 애플리케이션을 다시 설정할 수 있습니다.

### <a name="to-set-the-look-of-the-application"></a>애플리케이션의 모양을 설정하려면

1. 함수에서 `CMainFrame::OnCreate` 문 앞에 다음 코드를 입력 `return 0;` 하 여 기본 비주얼 관리자 및 스타일을 변경 합니다.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다. 애플리케이션 UI는 Office 2007 UI와 비슷해야 합니다.

## <a name="next-steps"></a>다음 단계

**리본 디자이너** 를 사용 하도록 클래식 SCRIBBLE 1.0 MFC 샘플을 수정 했습니다. 이제 [2 부](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)로 이동 합니다.

## <a name="see-also"></a>참고 항목

[연습](../mfc/walkthroughs-mfc.md)<br/>
[연습: MFC Scribble 응용 프로그램 업데이트 (2 부)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
