---
description: '자세한 정보: 연습: 새 MFC 셸 컨트롤 사용'
title: '연습: 새 MFC 셸 컨트롤 사용'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 26b2d5afbf3f74d98df122b00e5471f2a88563b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142911"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>연습: 새 MFC 셸 컨트롤 사용

이 연습에서는 파일 탐색기와 비슷한 응용 프로그램을 만듭니다. 두 개의 창이 있는 창을 만듭니다. 왼쪽 창에는 계층 구조 보기에서 바탕 화면을 표시 하는 [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) 개체가 포함 됩니다. 오른쪽 창에는 왼쪽 창에서 선택한 폴더의 파일을 보여 주는 [Cmfcshelllistctrl](../mfc/reference/cmfcshelllistctrl-class.md) 이 포함 됩니다.

## <a name="prerequisites"></a>사전 요구 사항

- Visual Studio 2017 이상에서는 MFC 지원이 선택적 구성 요소입니다. 설치 하려면 Windows 시작 메뉴에서 Visual Studio 설치 관리자를 엽니다. 사용 중인 Visual Studio 버전을 확인 하 고 **수정** 단추를 선택 합니다. **C + +를 사용한 데스크톱 개발** 타일이 선택 되어 있는지 확인 합니다. **선택적 구성 요소** 에서 **MFC 지원** 단추를 선택 합니다.

- 이 연습에서는 **일반 개발 설정을** 사용 하도록 Visual Studio를 설정 했다고 가정 합니다. 다른 개발 설정을 사용 하는 경우이 연습에서 사용 하는 일부 Visual Studio 창이 기본적으로 표시 되지 않을 수 있습니다.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>MFC 응용 프로그램 마법사를 사용 하 여 새 MFC 응용 프로그램을 만들려면

이러한 단계는 사용 중인 Visual Studio 버전에 따라 달라 집니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker range="msvc-160"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Visual Studio 2019에서 MFC 프로젝트를 만들려면

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 위쪽의 검색 상자에 **mfc** 를 입력 한 다음 결과 목록에서 **mfc 앱** 을 선택 합니다.

1. **다음** 을 클릭합니다. 다음 페이지에서 프로젝트의 이름을 입력하고 원하는 경우 프로젝트 위치를 지정합니다.

1. **만들기** 단추를 선택하여 프로젝트를 만듭니다.

   **MFC 응용 프로그램 마법사** 가 표시 되 면 다음 옵션을 사용 합니다.

   1. 왼쪽에서 **응용 프로그램 종류** 를 선택 합니다. 그런 다음 **단일 문서** 를 선택 하 고 **문서/뷰 아키텍처 지원** 을 선택 합니다. **프로젝트 스타일** 에서 **visual Studio** 를 선택 하 고 **비주얼 스타일 및 색** 드롭다운 목록에서 **Office 2007 (파란색 테마)** 를 선택 합니다.

   1. **복합 문서 지원** 창에서 **없음** 을 선택 합니다.

   1. **문서 템플릿 속성** 창을 변경 하지 마십시오.

   1. **사용자 인터페이스 기능** 창에서 **메뉴 모음 및 도구 모음 사용** 옵션을 선택 했는지 확인 합니다. 다른 모든 옵션은 그대로 둡니다.

   1. **고급 기능** 창에서 **ActiveX 컨트롤**, **공용 컨트롤 매니페스트** 및 **탐색 창** 옵션을 선택 합니다. 다른 모든 항목은 그대로 둡니다. **탐색 창** 옵션을 사용 하면 마법사가 창의 왼쪽에 이미 포함 된 창을 만들 수 `CMFCShellTreeCtrl` 있습니다.

   1. **생성 된 클래스** 창을 변경할 필요가 없으므로 **마침** 을 클릭 하 여 새 MFC 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Visual Studio 2017 이전 버전에서 MFC 프로젝트를 만들려면

1. **Mfc 응용 프로그램 마법사** 를 사용 하 여 새 mfc 응용 프로그램을 만듭니다. 마법사를 실행 하려면 **파일** 메뉴에서 **새로 만들기** 를 선택한 다음 **프로젝트** 를 선택 합니다. **새 프로젝트** 대화 상자가 표시 됩니다.

1. **새 프로젝트** 대화 상자의 **프로젝트 형식** 창에서 **Visual C++** 노드를 확장 하 고 **MFC** 를 선택 합니다. 그런 다음 **템플릿** 창에서 **MFC 응용 프로그램** 을 선택 합니다. 프로젝트 이름 (예:)을 입력 `MFCShellControls` 하 고 **확인** 을 클릭 합니다.

   **MFC 응용 프로그램 마법사** 가 표시 되 면 다음 옵션을 사용 합니다.

   1. **응용 프로그램 종류** 창의 **응용 프로그램 종류** 아래에서 **탭 문서** 옵션의 선택을 취소 합니다. 그런 다음 **단일 문서** 를 선택 하 고 **문서/뷰 아키텍처 지원** 을 선택 합니다. **프로젝트 스타일** 에서 **visual Studio** 를 선택 하 고 **비주얼 스타일 및 색** 드롭다운 목록에서 **Office 2007 (파란색 테마)** 를 선택 합니다.

   1. **복합 문서 지원** 창에서 **없음** 을 선택 합니다.

   1. **문서 템플릿 문자열** 창을 변경 하지 않습니다.

   1. 응용 프로그램에서 데이터베이스를 사용 하지 않으므로 **데이터베이스 지원** 창 (Visual Studio 2015 및 이전 버전)에서 **없음** 을 선택 합니다.

   1. **사용자 인터페이스 기능** 창에서 **메뉴 모음 및 도구 모음 사용** 옵션을 선택 했는지 확인 합니다. 다른 모든 옵션은 그대로 둡니다.

   1. **고급 기능** 창의 **고급 기능** 에서 **ActiveX 컨트롤** 및 **공용 컨트롤 매니페스트만** 을 선택 합니다. **고급 프레임 창** 에서 **탐색 창** 옵션만 선택 합니다. 이로 인해 마법사가 창 왼쪽에 이미 포함 된 창을 만들 수 `CMFCShellTreeCtrl` 있습니다.

   1. **생성 된 클래스** 창을 변경할 필요가 없으므로 **마침** 을 클릭 하 여 새 MFC 프로젝트를 만듭니다.

::: moniker-end

응용 프로그램을 빌드하고 실행 하 여 성공적으로 만들어졌는지 확인 합니다. 응용 프로그램을 빌드하려면 **빌드** 메뉴에서 **솔루션 빌드** 를 선택 합니다. 응용 프로그램이 성공적으로 빌드되면 **디버그** 메뉴에서 **디버깅 시작** 을 선택 하 여 응용 프로그램을 실행 합니다.

마법사는 표준 메뉴 모음, 표준 도구 모음, 표준 상태 표시줄 및 **폴더** 보기와 **달력** 보기가 있는 창의 왼쪽에 Outlook 표시줄을 포함 하는 응용 프로그램을 자동으로 만듭니다.

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>문서 보기에 셸 목록 컨트롤을 추가 하려면

1. 이 섹션에서는 마법사가 만든 뷰에 인스턴스를 추가 `CMFCShellListCtrl` 합니다. **솔루션 탐색기** 에서 **MFCShellControlsView** 를 두 번 클릭 하 여 뷰 헤더 파일을 엽니다.

   `#pragma once`헤더 파일의 위쪽 근처에 있는 지시문을 찾습니다. 바로 아래에이 코드를 추가 하 여에 대 한 헤더 파일을 포함 합니다 `CMFCShellListCtrl` .

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   이제 형식의 멤버 변수를 추가 `CMFCShellListCtrl` 합니다. 먼저 헤더 파일에서 다음 주석을 찾습니다.

   ```cpp
   // Generated message map functions
   ```

   해당 주석 바로 위에 다음 코드를 추가 합니다.

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **MFC 응용 프로그램 마법사** 가 `CMFCShellTreeCtrl` 클래스에서 개체를 이미 만들었지만 보호 된 `CMainFrame` 멤버입니다. 나중에 개체에 액세스 하므로 지금은 해당 개체에 대 한 접근자를 만듭니다. **솔루션 탐색기** 에서 mainfrm.cpp 헤더 파일을 두 번 클릭 하 여 엽니다. 다음 주석을 찾습니다.

   ```cpp
   // Attributes
   ```

   바로 아래에 다음 메서드 선언을 추가 합니다.

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   그런 다음 **솔루션 탐색기** 에서 mainfrm.cpp 소스 파일을 두 번 클릭 하 여 엽니다. 해당 파일의 아래쪽에 다음 메서드 정의를 추가 합니다.

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. 이제 `CMFCShellControlsView` windows 메시지를 처리 하도록 클래스를 업데이트 `WM_CREATE` 합니다. **클래스 뷰** 창을 열고 클래스를 선택 `CMFCShellControlsView` 합니다. 마우스 오른쪽 단추를 클릭하고 **속성** 을 선택합니다.

   그런 다음 [클래스 마법사](reference/mfc-class-wizard.md)에서 **메시지** 탭을 클릭 합니다. 메시지를 찾을 때까지 아래로 스크롤합니다 `WM_CREATE` . 옆의 드롭다운 목록에서 `WM_CREATE` **\<Add> OnCreate** 를 선택 합니다. 이 명령은 메시지 처리기를 만들고 MFC 메시지 맵을 자동으로 업데이트 합니다.

   `OnCreate`메서드에서 개체를 만듭니다 `CMFCShellListCtrl` . `OnCreate`MFCShellControlsView 소스 파일에서 메서드 정의를 찾고 해당 구현을 다음 코드로 바꿉니다.

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

1. 메시지에 대해 이전 단계를 반복 합니다 `WM_SIZE` . 그러면 사용자가 응용 프로그램 창의 크기를 변경할 때마다 응용 프로그램 보기가 다시 그려집니다. 메서드에 대 한 정의를 `OnSize` 다음 코드로 바꿉니다.

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. 마지막 단계는 `CMFCShellTreeCtrl` `CMFCShellListCtrl` [CMFCShellTreeCtrl:: SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) 메서드를 사용 하 여 및 개체를 연결 하는 것입니다. 를 호출 하면에서 `CMFCShellTreeCtrl::SetRelatedList` `CMFCShellListCtrl` 선택한 항목의 내용이 자동으로 표시 됩니다 `CMFCShellTreeCtrl` . `OnActivateView` [CView:: OnActivateView](../mfc/reference/cview-class.md#onactivateview)에서 재정의 된 메서드의 개체를 연결 합니다.

   MFCShellControlsView 헤더 파일의 `CMFCShellControlsView` 클래스 선언 내에 다음 메서드 선언을 추가 합니다.

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   다음으로 MFCShellControlsView 소스 파일에 메서드에 대 한 정의를 추가 합니다.

    ```cpp
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView)
    {
        if (bActivate&& AfxGetMainWnd() != NULL)
        {
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);
        }

        CView::OnActivateView(bActivate,
            pActivateView,
            pDeactiveView);
    }
    ```

   클래스에서 메서드를 호출 하 고 있으므로 `CMainFrame` `#include` MFCShellControlsView 소스 파일의 맨 위에 지시문을 추가 해야 합니다.

    ```cpp
    #include "MainFrm.h"
    ```

1. 응용 프로그램을 빌드하고 실행 하 여 성공적으로 만들어졌는지 확인 합니다. 응용 프로그램을 빌드하려면 **빌드** 메뉴에서 **솔루션 빌드** 를 선택 합니다. 응용 프로그램이 성공적으로 빌드되면 **디버그** 메뉴에서 **디버깅 시작** 을 선택 하 여 실행 합니다.

   이제 보기 창에서 선택한 항목에 대 한 세부 정보가 표시 됩니다 `CMFCShellTreeCtrl` . 에서 노드를 클릭 하면가 `CMFCShellTreeCtrl` `CMFCShellListCtrl` 자동으로 업데이트 됩니다. 마찬가지로에서 폴더를 두 번 클릭 하면가 `CMFCShellListCtrl` `CMFCShellTreeCtrl` 자동으로 업데이트 됩니다.

   트리 컨트롤이 나 목록 컨트롤에서 항목을 마우스 오른쪽 단추로 클릭 합니다. 실제 **파일 탐색기** 를 사용 하는 것과 같은 상황에 맞는 메뉴를 가져옵니다.

## <a name="next-steps"></a>다음 단계

- 마법사에서 **폴더** 창과 **달력** 창이 모두 포함 된 Outlook 표시줄을 만들었습니다. **탐색기** 창에 **달력** 창을 포함 하는 것이 적합 하지 않을 수 있으므로 이제 해당 창을 제거 합니다.

- 에서는 `CMFCShellListCtrl` 여러 가지 모드에서 파일을 볼 수 있습니다. 예를 들어, 작은 **아이콘,** **작은 아이콘**, **목록** 및 **세부 정보** 를 볼 수 있습니다. 응용 프로그램을 업데이트 하 여이 기능을 구현 합니다. 힌트: [Visual C++ 샘플](../overview/visual-cpp-samples.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[연습](../mfc/walkthroughs-mfc.md)
