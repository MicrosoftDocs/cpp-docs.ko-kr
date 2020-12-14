---
description: '자세한 정보: 연습: MFC 프로젝트에 D2D 개체 추가'
title: '연습: MFC 프로젝트에 D2D 개체 추가'
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: bbc59a943f6d8503370ddc8b7255275a6902b3c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344902"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>연습: MFC 프로젝트에 D2D 개체 추가

이 연습에서는 Visual C++, MFC 라이브러리 (MFC) 프로젝트에 D2D (기본 Direct2D) 개체를 추가한 다음 "Hello, 세계!"를 인쇄 하는 응용 프로그램에 프로젝트를 빌드하는 방법을 배웁니다. 그라데이션 배경의

이 연습에서는 다음 작업을 수행 하는 방법을 보여 줍니다.

- MFC 응용 프로그램을 만듭니다.

- 단색 브러시 및 선형 그라데이션 브러시를 만듭니다.

- 창의 크기를 조정할 때 적절 하 게 변경 되도록 그라데이션 브러시를 수정 합니다.

- D2D 그리기 처리기를 구현 합니다.

- 결과를 확인합니다.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 완료 하려면 **c + +를 사용한 데스크톱 개발** 워크 로드와 함께 Visual Studio를 설치 하 고 **x86 및 x64 구성 요소에 대 한 선택적 Visual C++ MFC** 를 설치 해야 합니다.

## <a name="to-create-an-mfc-application"></a>MFC 응용 프로그램을 만들려면

1. Mfc **응용 프로그램 마법사** 를 사용 하 여 mfc 응용 프로그램을 만듭니다. 사용 중인 Visual Studio 버전에 대 한 마법사를 여는 방법에 대 한 지침은 [연습: 새 MFC 셸 컨트롤 사용](walkthrough-using-the-new-mfc-shell-controls.md) 을 참조 하세요.

1. **이름** 상자에 *MFCD2DWalkthrough* 을 입력 합니다. **확인** 을 선택합니다.

1. **MFC 응용 프로그램 마법사** 에서 설정을 변경 하지 않고 **마침** 을 선택 합니다.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>단색 브러시 및 선형 그라데이션 브러시를 만들려면

1. **솔루션 탐색기** 의 **MFCD2DWalkthrough** 프로젝트에 있는 **헤더 파일** 폴더에서 MFCD2DWalkthroughView를 엽니다. 다음 코드를 클래스에 추가 `CMFCD2DWalkthroughView` 하 여 세 개의 데이터 변수를 만듭니다.

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   파일을 저장하고 닫습니다.

1. **원본 파일** 폴더에서 MFCD2DWalkthroughView을 엽니다. 클래스에 대 한 생성자에서 `CMFCD2DWalkthroughView` 다음 코드를 추가 합니다.

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   파일을 저장하고 닫습니다.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>창의 크기를 조정할 때 적절 하 게 변경 되도록 그라데이션 브러시를 수정 하려면

1. **프로젝트** 메뉴에서 **클래스 마법사** 를 선택 합니다.

1. **MFC 클래스 마법사** 의 **클래스 이름** 에서를 선택 `CMFCD2DWalkthroughView` 합니다.

1. **메시지** 탭의 **메시지** 상자에서를 선택 `WM_SIZE` 하 고 **처리기 추가** 를 선택 합니다. 이 작업을 수행 하면 `OnSize` 메시지 처리기가 `CMFCD2DWalkthroughView` 클래스에 추가 됩니다.

1. **기존 처리기** 상자에서를 선택 `OnSize` 합니다. **코드 편집** 을 선택 하 여 `CMFCD2DWalkthroughView::OnSize` 메서드를 표시 합니다. 메서드 끝에 다음 코드를 추가 합니다.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   파일을 저장하고 닫습니다.

## <a name="to-implement-a-d2d-drawing-handler"></a>D2D 그리기 처리기를 구현 하려면

1. **프로젝트** 메뉴에서 **클래스 마법사** 를 선택 합니다.

1. **MFC 클래스 마법사** 의 **클래스 이름** 에서를 선택 `CMFCD2DWalkthroughView` 합니다.

1. **메시지** 탭에서 **사용자 지정 메시지 추가** 를 선택 합니다.

1. 사용자 지정 **메시지 추가** 대화 상자의 **사용자 지정 Windows 메시지** 상자에 *AFX_WM_DRAW2D* 을 입력 합니다. **메시지 처리기 이름** 상자에 *OnDraw2D* 을 입력 합니다. 등록 된 **메시지** 옵션을 선택한 다음 **확인을** 선택 합니다. 이 작업을 수행 하면 AFX_WM_DRAW2D 메시지의 메시지 처리기가 클래스에 추가 `CMFCD2DWalkthroughView` 됩니다.

1. **기존 처리기** 상자에서를 선택 `OnDraw2D` 합니다. **코드 편집** 을 선택 하 여 `CMFCD2DWalkthroughView::OnDraw2D` 메서드를 표시 합니다. 메서드에 다음 코드를 사용 합니다 `CMFCD2DWalkthroughView::OnDrawD2D` .

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   파일을 저장하고 닫습니다.

## <a name="to-verify-the-results"></a>결과를 확인 하려면

애플리케이션을 빌드 및 실행합니다. 창의 크기를 조정할 때 그라데이션 사각형을 변경 해야 합니다. "Hello World!" 사각형의 가운데에 표시 됩니다.

## <a name="see-also"></a>참고 항목

[연습](../mfc/walkthroughs-mfc.md)
