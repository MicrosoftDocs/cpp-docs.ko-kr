---
description: '자세한 정보: 연습: MFC Scribble 응용 프로그램 업데이트 (2 부)'
title: '연습: MFC 자유 곡선 애플리케이션 업데이트(파트 2)'
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: 2520ac8fc1c66a2fc388738d22f4851547b6d03b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142963"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>연습: MFC 자유 곡선 애플리케이션 업데이트(파트 2)

이 연습의 [1 부](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) 에서는 클래식 Scribble 응용 프로그램에 Office 흐름 리본을 추가 하는 방법을 살펴보았습니다. 이 파트에서는 메뉴 및 명령 대신 사용자가 사용할 수 있는 리본 패널 및 컨트롤을 추가 하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>사전 요구 사항

[Visual C++ 샘플](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a> 섹션이

이 연습 부분에는 다음 단원이 있습니다.

- [리본에 새 패널 추가](#addnewpanel)

- [리본 메뉴에 도움말 패널 추가](#addhelppanel)

- [리본 메뉴에 펜 패널 추가](#addpenpanel)

- [리본에 색 단추 추가](#addcolorbutton)

- [문서 클래스에 색 멤버 추가](#addcolormember)

- [펜 초기화 및 기본 설정 저장](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a> 리본에 새 패널 추가

이러한 단계에서는 도구 모음과 상태 표시줄의 표시 여부를 제어 하는 두 개의 확인란이 포함 된 **보기** 패널을 추가 하는 방법 및 MDI (다중 문서 인터페이스)의 생성 및 정렬을 제어 하는 세로 방향 분할 단추가 포함 된 **창** 패널을 추가 하는 방법을 보여 줍니다.

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>리본 표시줄에 보기 패널 및 창 패널을 추가 하려면

1. `View`상태 표시줄 및 도구 모음을 설정/해제 하는 두 개의 확인란이 있는 이라는 패널을 만듭니다.

   1. **도구 상자** 에서 **패널** 을 **홈** 범주로 끌어 옵니다. 그런 다음 두 개의 **확인란** 을 패널로 끌어 옵니다.

   1. 패널을 클릭 하 여 해당 속성을 수정 합니다. **캡션을** 로 변경 `View` 합니다.

   1. 첫 번째 확인란을 클릭 하 여 속성을 수정 합니다. **ID** 를로 변경 하 `ID_VIEW_TOOLBAR` 고 **캡션을** 로 변경 `Toolbar` 합니다.

   1. 두 번째 확인란을 클릭 하 여 속성을 수정 합니다. **ID** 를로 변경 하 `ID_VIEW_STATUS_BAR` 고 **캡션을** 로 변경 `Status Bar` 합니다.

1. 분할 단추가 있는 이라는 패널을 만듭니다 `Window` . 사용자가 분할 단추를 클릭 하면 바로 가기 메뉴에는 Scribble 응용 프로그램에 이미 정의 되어 있는 세 가지 명령이 표시 됩니다.

   1. **도구 상자** 에서 **패널** 을 **홈** 범주로 끌어 옵니다. 그런 다음 **단추** 를 패널로 끌어 옵니다.

   1. 패널을 클릭 하 여 해당 속성을 수정 합니다. **캡션을** 로 변경 `Window` 합니다.

   1. 이 단추를 클릭합니다. **캡션** 을 `Windows` , **키** 를 `w` , **큼 이미지 인덱스** 를로 `1` , **분할 모드** 를로 변경 `False` 합니다. 그런 다음 **메뉴 항목** 옆에 있는 줄임표 (**...**)를 클릭 하 여 **항목 편집기** 대화 상자를 엽니다.

   1. **추가** 를 세 번 클릭 하 여 세 개의 단추를 추가 합니다.

   1. 첫 번째 단추를 클릭 한 다음 **캡션** 을로 `New Window` , **ID** 를로 변경 `ID_WINDOW_NEW` 합니다.

   1. 두 번째 단추를 클릭 한 다음 **Caption** 을로 `Cascade` , **ID** 를로 변경 `ID_WINDOW_CASCADE` 합니다.

   1. 세 번째 단추를 클릭 한 다음 **Caption** 을로 `Tile` , **ID** 를로 변경 `ID_WINDOW_TILE_HORZ` 합니다.

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다. **보기** 창과 **창** 패널이 표시 됩니다. 단추를 클릭 하 여 제대로 작동 하는지 확인 합니다.

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a> 리본 메뉴에 도움말 패널 추가

이제 Scribble 응용 프로그램에 정의 된 두 개의 메뉴 항목을 **도움말 항목** 이라는 리본 단추나 **scribble에** 할당할 수 있습니다. 단추가 **Help** 라는 새 패널에 추가 됩니다.

### <a name="to-add-a-help-panel"></a>도움말 패널을 추가 하려면

1. **도구 상자** 에서 **패널** 을 **홈** 범주로 끌어 옵니다. 그런 다음 두 **단추** 를 패널로 끌어 옵니다.

1. 패널을 클릭 하 여 해당 속성을 수정 합니다. **캡션을** 로 변경 `Help` 합니다.

1. 첫 번째 단추를 클릭 합니다. **Caption** 을로 `Help Topics` , **ID** 를로 변경 `ID_HELP_FINDER` 합니다.

1. 두 번째 단추를 클릭 합니다. **Caption** 을로 `About Scribble...` , **ID** 를로 변경 `ID_APP_ABOUT` 합니다.

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다. 두 개의 리본 단추가 포함 된 **도움말** 패널이 표시 됩니다.

   > [!IMPORTANT]
   > **도움말 항목** 단추를 클릭 하면 Scribble 응용 프로그램은 *your_project_name* 라는 압축 된 HTML (.chm) 도움말 파일을 엽니다. 따라서 프로젝트의 이름을 Scribble으로 지정 하지 않은 경우에는 도움말 파일의 이름을 프로젝트 이름으로 바꾸어야 합니다.

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a> 리본 메뉴에 펜 패널 추가

이제 펜의 두께와 색을 제어 하는 단추를 표시 하는 패널을 추가 합니다. 이 패널에는 굵은 펜과 씬 펜 간을 전환 하는 확인란이 있습니다. 해당 기능은 Scribble 응용 프로그램의 **굵은 선** 메뉴 항목의 기능과 유사 합니다.

원래 Scribble 응용 프로그램을 사용 하면 사용자가 메뉴에서 **펜 너비** 를 클릭할 때 표시 되는 대화 상자에서 펜 너비를 선택할 수 있습니다. 리본 표시줄에는 새 컨트롤을 위한 충분 한 공간이 있으므로 리본 메뉴에서 두 개의 콤보 상자를 사용 하 여 대화 상자를 바꿀 수 있습니다. 하나의 콤보 상자가 씬 펜의 너비를 조정 하 고 다른 콤보 상자는 두꺼운 펜의 너비를 조정 합니다.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>리본 메뉴에 펜 패널 및 콤보 상자를 추가 하려면

1. **도구 상자** 에서 **패널** 을 **홈** 범주로 끌어 옵니다. 그런 다음 **확인란과** 두 개의 **콤보 상자** 를 패널로 끌어 옵니다.

1. 패널을 클릭 하 여 해당 속성을 수정 합니다. **캡션을** 로 변경 `Pen` 합니다.

1. 확인란을 선택합니다. **Caption** 을로 `Use Thick` , **ID** 를로 변경 `ID_PEN_THICK_OR_THIN` 합니다.

1. 첫 번째 콤보 상자를 클릭 합니다. **캡션** 을 `Thin Pen` , **ID** 를 `ID_PEN_THIN_WIDTH` , **형식** 에, `Drop List` **데이터** 를 `1;2;3;4;5;6;7;8;9;` , **텍스트** 를로 변경 `2` 합니다.

1. 두 번째 콤보 상자를 클릭 합니다. **캡션** 을 `Thick Pen` , **ID** 를 `ID_PEN_THICK_WIDTH` , **형식** 에, `Drop List` **데이터** 를 `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;` , **텍스트** 를로 변경 `5` 합니다.

1. 새 콤보 상자는 기존 메뉴 항목에 해당 하지 않으므로 모든 펜 옵션에 대 한 메뉴 항목을 만들어야 합니다.

   1. **리소스 뷰** 창에서 **IDR_SCRIBBTYPE** 메뉴 리소스를 엽니다.

   1. 펜 **을 클릭 하** 여 펜 메뉴를 엽니다. 여기에서 **형식** 을 클릭 하 고을 입력 `Thi&n Pen` 합니다.

   1. 입력 한 텍스트를 마우스 오른쪽 단추로 클릭 하 여 **속성** 창을 연 다음 ID 속성을으로 변경 `ID_PEN_THIN_WIDTH` 합니다.

   1. 모든 펜 메뉴 항목에 대 한 이벤트 처리기를 만듭니다. 만든 **Thi&n 펜** 메뉴 항목을 마우스 오른쪽 단추로 클릭 한 다음 **이벤트 처리기 추가** 를 클릭 합니다. **이벤트 처리기 마법사** 가 표시 됩니다.

   1. 마법사의 **클래스 목록** 상자에서 **CScribbleDoc** 를 선택 하 고 **추가 및 편집** 을 클릭 합니다. 이 명령은 이라는 이벤트 처리기를 만듭니다 `CScribbleDoc::OnPenThinWidth` .

   1. 다음 코드를 `CScribbleDoc::OnPenThinWidth`에 추가합니다.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. 다음으로, 두꺼운 펜에 대 한 메뉴 항목 및 이벤트 처리기를 만듭니다.

   1. **리소스 뷰** 창에서 **IDR_SCRIBBTYPE** 메뉴 리소스를 엽니다.

   1. 펜 **을 클릭 하** 여 펜 메뉴를 엽니다. 여기에서 **형식** 을 클릭 하 고을 입력 `Thic&k Pen` 합니다.

   1. 입력 한 텍스트를 마우스 오른쪽 단추로 클릭 하 여 **속성** 창을 표시 합니다. ID 속성을로 변경 `ID_PEN_THICK_WIDTH` 합니다.

   1. 만든 **굵은 펜** 메뉴 항목을 마우스 오른쪽 단추로 클릭 한 다음 **이벤트 처리기 추가** 를 클릭 합니다. **이벤트 처리기 마법사** 가 표시 됩니다.

   1. 마법사의 **클래스 목록** 상자에서 **CScribbleDoc** 를 선택 하 고 **추가 및 편집** 을 클릭 합니다. 이 명령은 이라는 이벤트 처리기를 만듭니다 `CScribbleDoc::OnPenThickWidth` .

   1. 다음 코드를 `CScribbleDoc::OnPenThickWidth`에 추가합니다.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다. 새 단추와 콤보 상자가 표시 됩니다. 다른 펜 너비를 사용 하 여 scribble을 시도 합니다.

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a> 펜 패널에 색 단추 추가

그런 다음 사용자에 게 색을 자유롭게 지정할 수 있는 [Cmfc리본 Colorbutton](../mfc/reference/cmfcribboncolorbutton-class.md) 개체를 추가 합니다.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>펜 패널에 색 단추를 추가 하려면

1. 색 단추를 추가 하기 전에 해당 단추에 대 한 메뉴 항목을 만듭니다. **리소스 뷰** 창에서 **IDR_SCRIBBTYPE** 메뉴 리소스를 엽니다. **펜 메뉴 항목** 을 클릭 하 여 펜 메뉴를 엽니다. 여기에서 **형식** 을 클릭 하 고을 입력 `&Color` 합니다. 입력 한 텍스트를 마우스 오른쪽 단추로 클릭 하 여 **속성** 창을 표시 합니다. ID를 `ID_PEN_COLOR`로 변경합니다.

1. 이제 색 단추를 추가 합니다. **도구 상자** 에서 **색 단추** 를 **펜** 패널로 끌어 옵니다.

1. 색 단추를 클릭 합니다. **캡션** 을 `Color` , **ID** `ID_PEN_COLOR` 에서, **간단한 모양** 으로 `True` , **큼 이미지 인덱스** 를로 `1` , **분할 모드** 를로 변경 `False` 합니다.

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다. 새 색 단추가 **펜** 패널에 표시 됩니다. 그러나 이벤트 처리기가 아직 없기 때문에 사용할 수 없습니다. 다음 단계에서는 색 단추에 대 한 이벤트 처리기를 추가 하는 방법을 보여 줍니다.

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a> 문서 클래스에 색 멤버 추가

원래 Scribble 응용 프로그램에는 색 펜이 없으므로 해당 응용 프로그램에 대 한 구현을 작성 해야 합니다. 문서의 펜 색을 저장 하려면 문서 클래스에 새 멤버를 추가 `CscribbleDoc` 합니다.

### <a name="to-add-a-color-member-to-the-document-class"></a>문서 클래스에 색 멤버를 추가 하려면

1. Scribdoc의 `CScribbleDoc` 클래스에서 섹션을 찾습니다 `// Attributes` . 데이터 멤버의 정의 뒤에 다음 코드 줄을 추가 합니다 `m_nThickWidth` .

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. 모든 문서에는 사용자가 이미 그린 stokes가 목록이 포함 되어 있습니다. 모든 스트로크는 개체에 의해 정의 됩니다 `CStroke` . 클래스에는 `CStroke` 펜 색에 대 한 정보가 포함 되어 있지 않으므로 클래스를 수정 해야 합니다. Scribdoc의 `CStroke` 클래스에서 데이터 멤버의 정의 뒤에 다음 코드 줄을 추가 합니다 `m_nPenWidth` .

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. Scribdoc에서 `CStroke` 매개 변수가 너비 및 색을 지정 하는 새 생성자를 추가 합니다. 문 뒤에 다음 코드 줄을 추가 `CStroke(UINT nPenWidth);` 합니다.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. Scribdoc에서 새 생성자의 구현을 추가 합니다. `CStroke` 생성자의 구현 뒤에 다음 코드를 추가 합니다 `CStroke::CStroke(UINT nPenWidth)` .

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. 메서드의 두 번째 줄을 `CStroke::DrawStroke` 다음과 같이 변경 합니다.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. 문서 클래스에 대 한 기본 펜 색을 설정 합니다. Scribdoc에서 문 뒤에 다음 줄을 추가 합니다 `CScribbleDoc::InitDocument` `m_nThickWidth = 5;` .

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. Scribdoc에서 메서드의 첫 번째 줄을 다음과 같이 변경 합니다 `CScribbleDoc::NewStroke` .

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. 메서드의 마지막 줄 `CScribbleDoc::ReplacePen` 을 다음으로 변경 합니다.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. `m_penColor`이전 단계에서 멤버를 추가 했습니다. 이제 멤버를 설정 하는 색 단추에 대 한 이벤트 처리기를 만듭니다.

   1. **리소스 뷰** 창에서 IDR_SCRIBBTYPE 메뉴 리소스를 엽니다.

   1. **색** 메뉴 항목을 마우스 오른쪽 단추로 클릭 하 고 **이벤트 처리기 추가** 를 클릭 합니다. **이벤트 처리기 마법사** 가 나타납니다.

   1. 마법사의 **클래스 목록** 상자에서 **CScribbleDoc** 를 선택 하 고 **추가 및 편집** 단추를 클릭 합니다. 이 명령은 `CScribbleDoc::OnPenColor` 이벤트 처리기 스텁을 만듭니다.

1. 이벤트 처리기에 대 한 스텁을 `CScribbleDoc::OnPenColor` 다음 코드로 바꿉니다.

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. 변경 사항을 저장한 다음 애플리케이션을 빌드하고 실행합니다. 이제 색 단추를 누르고 펜의 색을 변경할 수 있습니다.

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a> 펜 초기화 및 기본 설정 저장

다음으로 펜의 색과 너비를 초기화 합니다. 마지막으로 파일에서 색 그리기를 저장 하 고 로드 합니다.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>리본 표시줄에서 컨트롤을 초기화 하려면

1. 리본 표시줄에서 펜을 초기화 합니다.

   메서드에서 문 뒤에 있는 scribdoc에 다음 코드를 추가 합니다 `CScribbleDoc::InitDocument` `m_sizeDoc = CSize(200,200)` .

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. 색 그리기를 파일에 저장 합니다. `CStroke::Serialize`메서드에서 문 뒤에 있는 scribdoc에 다음 문을 추가 합니다. `ar << (WORD)m_nPenWidth;`

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. 마지막으로 파일에서 색 그리기를 로드 합니다. 메서드에서 문 뒤에 다음 코드 줄을 추가 `CStroke::Serialize` `m_nPenWidth = w;` 합니다.

   ```cpp
   ar >> m_penColor;
   ```

1. 이제 색을 자유롭게 그리고 드로잉을 파일에 저장 합니다.

## <a name="conclusion"></a>결론

MFC Scribble 응용 프로그램을 업데이트 했습니다. 기존 응용 프로그램을 수정 하는 경우이 연습을 지침으로 사용 합니다.

## <a name="see-also"></a>참고 항목

[연습](../mfc/walkthroughs-mfc.md)<br/>
[연습: MFC Scribble 응용 프로그램 업데이트 (1 부)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
