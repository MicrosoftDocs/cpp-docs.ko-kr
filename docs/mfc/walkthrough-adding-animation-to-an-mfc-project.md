---
description: '자세한 정보: 연습: MFC 프로젝트에 애니메이션 추가'
title: '연습: MFC 프로젝트에 애니메이션 추가'
ms.date: 04/25/2019
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
ms.openlocfilehash: ef6d6fc8e17c8e6dc4c6f0f4e8d7407f2690927f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143119"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>연습: MFC 프로젝트에 애니메이션 추가

이 연습에서는 Visual C++ MFC 라이브러리 (MFC) 프로젝트에 기본 애니메이션 개체를 추가 하는 방법을 배웁니다.

이 연습에서는 다음 작업을 수행 하는 방법을 보여 줍니다.

- MFC 응용 프로그램을 만듭니다.

- 메뉴를 추가 하 고 애니메이션을 시작 및 중지 하는 명령을 추가 합니다.

- 시작 및 중지 명령에 대 한 처리기를 만듭니다.

- 애니메이션 개체를 프로젝트에 추가 합니다.

- 애니메이션 개체를 창에 가운데 맞춤 합니다.

- 결과를 확인합니다.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 완료하려면 Visual Studio가 필요합니다.

### <a name="to-create-an-mfc-application"></a>MFC 응용 프로그램을 만들려면

1. Mfc **응용 프로그램 마법사** 를 사용 하 여 mfc 응용 프로그램을 만듭니다. 사용 중인 Visual Studio 버전에 대 한 마법사를 여는 방법에 대 한 지침은 [연습: 새 MFC 셸 컨트롤 사용](walkthrough-using-the-new-mfc-shell-controls.md) 을 참조 하세요.

1. **이름** 상자에 *MFCAnimationWalkthrough* 을 입력 합니다. **확인** 을 클릭합니다.

1. **MFC 응용 프로그램 마법사** 대화 상자에서 **응용 프로그램 유형이** **여러 문서** 이 고 **프로젝트 스타일이** **Visual Studio** 인지 확인 하 고 **문서/뷰 아키텍처 지원** 옵션을 선택 합니다. **Finish** 를 클릭합니다.

### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>메뉴를 추가 하 고 애니메이션을 시작 및 중지 하는 명령을 추가 하려면

1. **보기** 메뉴에서 **다른 창** 을 가리킨 다음 **리소스 뷰** 를 클릭 합니다.

1. **리소스 뷰** 에서 **메뉴** 폴더로 이동 하 여 엽니다. **IDR_MFCAnimationWalkthroughTYPE** 리소스를 두 번 클릭 하 여 수정할 수 있도록 엽니다.

1. 메뉴 모음에서 **여기에 입력** 상자에 *&nimation* 를 입력 하 여 애니메이션 메뉴를 만듭니다.

1. **애니메이션** 아래의 **여기에 입력** 상자에 *start &Forward* 를 입력 하 여 start forward 명령을 만듭니다.

1. **시작 앞** 의 **여기에 입력** 상자에 *start &뒤로* 를 입력 합니다.

1. **뒤로 시작** 의 **여기에 입력** 상자에 *S&Top* 을 입력 하 여 Stop 명령을 만듭니다.

1. MFCAnimationWalkthrough를 저장 하 고 닫습니다.

1. **솔루션 탐색기** 에서 mainfrm.cpp를 두 번 클릭 하 여 수정 하기 위해 엽니다. `CMainFrame::OnCreate`메서드에서에 대 한 여러 호출을 포함 하는 섹션을 찾습니다 `lstBasicCommands.AddTail` . 해당 섹션 바로 뒤에 다음 코드를 추가 합니다.

    ```cpp
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);
    ```

1. 파일을 저장하고 닫습니다.

### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>시작 및 중지 명령에 대 한 처리기를 만들려면

1. **프로젝트** 메뉴에서 **클래스 마법사** 를 클릭 합니다.

1. **MFC 클래스 마법사** 의 **클래스 이름** 아래에서 **CMFCAnimationWalkthroughView** 를 선택 합니다.

1. **명령** 탭의 **개체 id** 상자에서 **ID_ANIMATION_STARTFORWARD** 를 선택한 다음 **메시지** 상자에서 **명령** 을 선택 합니다. **처리기 추가** 를 클릭 합니다.

1. **멤버 함수 추가** 대화 상자에서 **확인** 을 클릭 합니다.

1. **개체 id** 상자에서 **ID_ANIMATION_STARTBACKWARD** 를 선택한 다음 **메시지** 상자에서 **명령** 을 선택 합니다. **처리기 추가** 를 클릭 합니다.

1. **멤버 함수 추가** 대화 상자에서 **확인** 을 클릭 합니다.

1. **개체 id** 상자에서 **ID_ANIMATION_STOP** 를 선택한 다음 **메시지** 상자에서 **명령** 을 선택 합니다. **처리기 추가** 를 클릭 한 다음 **확인** 을 클릭 합니다.

1. **멤버 함수 추가** 대화 상자에서 **확인** 을 클릭 합니다.

1. **MFC 클래스 마법사** 에서 **확인** 을 클릭 합니다.

1. 편집기에 열려 있지만 닫지 않는 MFCAnimationWalkthroughView를 저장 합니다.

### <a name="to-add-an-animated-object-to-the-project"></a>애니메이션 개체를 프로젝트에 추가 하려면

1. **솔루션 탐색기** 에서 MFCAnimationWalkthroughView를 두 번 클릭 하 여 수정할 수 있도록 엽니다. 클래스 정의 바로 앞에 `CMFCAnimationWalkthroughView` 다음 코드를 추가 하 여 애니메이션 개체와의 일정 충돌을 처리할 사용자 지정 애니메이션 컨트롤러를 만듭니다.

    ```cpp
    class CCustomAnimationController : public CAnimationController
    {
    public:
        CCustomAnimationController()
        {
        }

        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
            CAnimationGroup* pGroupNew,
            UI_ANIMATION_PRIORITY_EFFECT priorityEffect)
        {
            return TRUE;
        }
    };
    ```

1. 클래스의 끝에 `CMFCAnimationWalkthroughView` 다음 코드를 추가 합니다.

    ```cpp
    CCustomAnimationController m_animationController;
    CAnimationColor m_animationColor;
    CAnimationRect m_animationRect;
    ```

1. 줄 뒤에 `DECLARE_MESSAGE_MAP()` 다음 코드를 추가 합니다.

    ```cpp
    void Animate(BOOL bDirection);
    ```

1. 파일을 저장하고 닫습니다.

1. MFCAnimationWalkthroughView에서 문 뒤에 있는 파일의 맨 위에서 `#include` 클래스 메서드 앞에 다음 코드를 추가 합니다.

    ```cpp
    static int nAnimationGroup = 0;
    static int nInfoAreaHeight = 40;
    ```

1. 생성자의 끝에 `CMFCAnimationWalkthroughView` 다음 코드를 추가 합니다.

    ```cpp
    m_animationController.EnableAnimationTimerEventHandler();
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);
    m_animationColor = RGB(255, 255, 255);
    m_animationRect = CRect(0, 0, 0, 0);
    m_animationColor.SetID(-1, nAnimationGroup);
    m_animationRect.SetID(-1, nAnimationGroup);
    m_animationController.AddAnimationObject(&m_animationColor);
    m_animationController.AddAnimationObject(&m_animationRect);
    ```

1. 메서드를 찾은 `CAnimationWalthroughView::PreCreateWindow` 후 다음 코드로 바꿉니다.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)
    {
        // TODO: Modify the Window class or styles here by modifying
        //       the CREATESTRUCT cs
        m_animationController.SetRelatedWnd(this);

        return CView::PreCreateWindow(cs);
    }
    ```

1. 메서드를 찾은 `CAnimationWalkthroughView::OnDraw` 후 다음 코드로 바꿉니다.

    ```cpp
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)
    {
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
        ASSERT_VALID(pDoc);
        if (!pDoc)
            return;

        // TODO: add draw code for native data here
        CMemDC dcMem(*pDC, this);
        CDC& dc = dcMem.GetDC();
        CRect rect;
        GetClientRect(rect);

        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));

        CString strRGB;
        strRGB.Format(_T("Fill Color is: %d; %d; %d"),
            GetRValue(m_animationColor),
            GetGValue(m_animationColor),
            GetBValue(m_animationColor));

        dc.DrawText(strRGB, rect, DT_CENTER);
        rect.top += nInfoAreaHeight;

        CBrush br;
        br.CreateSolidBrush(m_animationColor);
        CBrush* pBrushOld = dc.SelectObject(&br);

        dc.Rectangle((CRect)m_animationRect);

        dc.SelectObject(pBrushOld);
    }
    ```

1. 파일의 끝에 다음 코드를 추가 합니다.

    ```cpp
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)
    {
        static UI_ANIMATION_SECONDS duration = 3;
        static DOUBLE dblSpeed = 35.;
        static BYTE nStartColor = 50;
        static BYTE nEndColor = 255;

        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;

        CLinearTransition* pRedTransition =
            new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

        CSmoothStopTransition* pGreenTransition =
            new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

        CLinearTransitionFromSpeed* pBlueTransition =
            new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

        m_animationColor.AddTransition(pRedTransition,
            pGreenTransition,
            pBlueTransition);

        CRect rectClient;
        GetClientRect(rectClient);

        rectClient.top += nInfoAreaHeight;

        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;

        CLinearTransition* pLeftTransition =
            new CLinearTransition(duration, nLeftFinal);

        CLinearTransition* pTopTransition =
            new CLinearTransition(duration, nTopFinal);

        CLinearTransition* pRightTransition =
            new CLinearTransition(duration, nRightFinal);

        CLinearTransition* pBottomTransition =
            new CLinearTransition(duration, nBottomFinal);

        m_animationRect.AddTransition(pLeftTransition,
            pTopTransition,
            pRightTransition,
            pBottomTransition);

        CBaseKeyFrame* pKeyframeStart =
            CAnimationController::GetKeyframeStoryboardStart();
        CKeyFrame* pKeyFrameEnd =
            m_animationController.CreateKeyframe(nAnimationGroup,
                pBlueTransition);

        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);

        m_animationController.AnimateGroup(nAnimationGroup);
    }
    ```

1. **프로젝트** 메뉴에서 **클래스 마법사** 를 클릭 합니다.

1. **MFC 클래스 마법사** 의 **클래스 이름** 아래에서 **CMFCAnimationWalkthroughView** 를 선택 합니다.

1. **메시지** 탭의 **메시지** 상자에서 **WM_ERASEBKGND** 를 선택 하 고 **처리기 추가** 를 클릭 한 다음 **확인** 을 클릭 합니다.

1. MFCAnimationWalkthroughView에서의 구현을 `OnEraseBkgnd` 다음 코드로 바꾸어 다시 그릴 때 애니메이션 개체의 깜박임을 줄입니다.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)
    {
        return TRUE;
    }
    ```

1. , 및의 구현을 `CMFCAnimationWalkthroughView::OnAnimationStartforward` `CMFCAnimationWalkthroughView::OnAnimationStartbackward` `CMFCAnimationWalkthroughView::OnAnimationStop` 다음 코드로 바꿉니다.

    ```cpp
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()
    {
        Animate(TRUE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()
    {
        Animate(FALSE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStop()
    {
        IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();
        if (pManager != NULL)
        {
            pManager->AbandonAllStoryboards();

        }
    }
    ```

1. 파일을 저장하고 닫습니다.

### <a name="to-center-the-animated-object-in-the-window"></a>애니메이션 개체를 창에 가운데 맞춤 하려면

1. **솔루션 탐색기** 에서 MFCAnimationWalkthroughView를 두 번 클릭 하 여 수정할 수 있도록 엽니다. 클래스의 끝에서 `CMFCAnimationWalkthroughView` 의 정의 바로 뒤에 `m_animationRect` 다음 코드를 추가 합니다.

    ```cpp
    BOOL m_bCurrentDirection;
    ```

1. 파일을 저장하고 닫습니다.

1. **프로젝트** 메뉴에서 **클래스 마법사** 를 클릭 합니다.

1. **MFC 클래스 마법사** 의 **클래스 이름** 아래에서 **CMFCAnimationWalkthroughView** 를 선택 합니다.

1. **메시지** 탭의 **메시지** 상자에서 **WM_SIZE** 를 선택 하 고 **처리기 추가** 를 클릭 한 다음 **확인** 을 클릭 합니다.

1. MFCAnimationWalkthroughView에서에 대 한 코드를 `CMFCAnimationWalkthroughView::OnSize` 다음 코드로 바꿉니다.

    ```cpp
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);
        CRect rect;
        GetClientRect(rect);

        rect.top += nInfoAreaHeight;

        CRect rectAnim = m_animationRect;
        m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,
        rect.CenterPoint().y - rectAnim.Height() / 2),
        rectAnim.Size());

        if (m_animationController.IsAnimationInProgress())
        {
            Animate(m_bCurrentDirection);
        }
    }
    ```

1. 생성자의 시작 부분에 `CMFCAnimationWalkthroughView` 다음 코드를 추가 합니다.

    ```cpp
    m_bCurrentDirection = TRUE;
    ```

1. 메서드의 시작 부분에 `CMFCAnimationWalkthroughView::Animate` 다음 코드를 추가 합니다.

    ```cpp
    m_bCurrentDirection = bDirection;
    ```

1. 파일을 저장하고 닫습니다.

### <a name="to-verify-the-results"></a>결과를 확인 하려면

1. 애플리케이션을 빌드 및 실행합니다. **애니메이션** 메뉴에서 **앞으로 시작** 을 클릭 합니다. 사각형이 나타나고 가운데 영역이 채워집니다. **뒤로 시작** 을 클릭 하면 애니메이션이 역순으로 표시 되 고 **중지** 를 클릭 하면 중지 됩니다. 애니메이션을 진행 하면서 사각형의 채우기 색이 변경 되 고 현재 색이 애니메이션 창의 맨 위에 표시 됩니다.

## <a name="see-also"></a>참고 항목

[연습](../mfc/walkthroughs-mfc.md)
