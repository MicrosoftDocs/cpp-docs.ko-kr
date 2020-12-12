---
description: '자세히 알아보기: 방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기'
title: '방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: d05d2132c4382365b1de16490481049cb43ffe22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328781"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기

다음 단계에서는 .NET Framework 사용자 정의 컨트롤을 만들고 컨트롤 클래스 라이브러리 (특히 Windows 컨트롤 라이브러리 프로젝트)에서 사용자 정의 컨트롤을 만든 다음 프로젝트를 어셈블리로 컴파일하는 방법을 보여 줍니다. 그런 다음 [CView 클래스](../mfc/reference/cview-class.md) 및 [CWinFormsView 클래스](../mfc/reference/cwinformsview-class.md)에서 파생 된 클래스를 사용 하는 MFC 응용 프로그램에서 컨트롤을 사용할 수 있습니다.

Windows Forms 사용자 정의 컨트롤을 만들고 컨트롤 클래스 라이브러리를 작성 하는 방법에 대 한 자세한 내용은 [방법: 사용자 정의 컨트롤 제작](/dotnet/framework/winforms/controls/how-to-author-composite-controls)을 참조 하세요.

> [!NOTE]
> 경우에 따라 타사 그리드 컨트롤과 같은 Windows Forms 컨트롤은 MFC 응용 프로그램에서 호스팅될 때 안정적으로 동작 하지 않을 수 있습니다. 사용자 정의 컨트롤 Windows Forms을 MFC 응용 프로그램에 추가 하 고 사용자 정의 컨트롤 내에 타사 Grid 컨트롤을 추가 하는 것이 좋습니다.

이 절차에서는 [방법: 대화 상자에서 사용자 정의 컨트롤 및 호스트 만들기](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)의 절차에 따라 WindowsFormsControlLibrary1 이라는 Windows Forms 컨트롤 라이브러리 프로젝트를 만들었다고 가정 합니다.

### <a name="to-create-the-mfc-host-application"></a>MFC 호스트 응용 프로그램을 만들려면

1. MFC 응용 프로그램 프로젝트를 만듭니다.

   **파일** 메뉴에서 **새로 만들기** 를 선택한 다음 **프로젝트** 를 클릭 합니다. **Visual C++** 폴더에서 **MFC 응용 프로그램** 을 선택 합니다.

   **이름** 상자에을 입력 하 `MFC02` 고 솔루션 설정을  **솔루션에 추가** 로 변경 합니다. **확인** 을 클릭합니다.

   **MFC 응용 프로그램 마법사** 에서 모든 기본값을 적용 한 다음 **마침** 을 클릭 합니다. 이렇게 하면 다중 문서 인터페이스를 사용 하 여 MFC 응용 프로그램을 만듭니다.

1. CLR (공용 언어 런타임) 지원에 대 한 프로젝트를 구성 합니다.

   **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 `MFC01` 하 고 상황에 맞는 메뉴에서 **속성** 을 선택 합니다. **속성 페이지** 대화 상자가 나타납니다.

   **구성 속성** 아래에서 **일반** 을 선택 합니다. **프로젝트 기본값** 섹션에서 **공용 언어 런타임 지원** 을 **공용 언어 런타임 지원 (/clr)** 으로 설정 합니다.

   **구성 속성** 에서 **C/c + +** 를 확장 하 고 **일반** 노드를 클릭 합니다. **디버그 정보 형식을** **Program Database (/zi)** 로 설정 합니다.

   **코드 생성** 노드를 클릭 합니다. **최소 다시 빌드 사용** 을 **아니요 (/gm-)** 로 설정 합니다. 또한 기본 **런타임 검사** 를 **기본** 으로 설정 합니다.

   **확인** 을 클릭 하 여 변경 내용을 적용 합니다.

1. *.Pch* (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에서 다음 줄을 추가 합니다.

    ```
    #using <System.Windows.Forms.dll>
    ```

1. .NET 컨트롤에 대 한 참조를 추가 합니다.

   **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 `MFC02` 하 고 **추가**, **참조** 를 선택 합니다. **속성 페이지** 에서 **새 참조 추가** 를 클릭 하 고 **프로젝트** 탭 아래에서 WindowsFormsControlLibrary1을 선택한 다음 **확인** 을 클릭 합니다. 그러면 프로그램에서 컴파일되도록 참조를 [/fu](../build/reference/fu-name-forced-hash-using-file.md) 컴파일러 옵션의 형태로 추가 합니다. 또한 프로그램을 실행 하기 위해 WindowsFormsControlLibrary1.dll를 `MFC02` 프로젝트 디렉터리로 복사 합니다.

1. Stdafx.h에서 다음 줄을 찾습니다.

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   위에 다음 줄을 추가 합니다.

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. [CWinFormsView](../mfc/reference/cwinformsview-class.md)에서 상속 되도록 뷰 클래스를 수정 합니다.

   MFC02View에서 다음과 같이 코드를 표시 하도록 [CView](../mfc/reference/cview-class.md) 를 [CWinFormsView](../mfc/reference/cwinformsview-class.md) 로 바꿉니다.

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   MDI 응용 프로그램에 다른 뷰를 추가 하려면 사용자가 만드는 각 뷰에 대해 [CWinApp:: AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) 을 호출 해야 합니다.

1. IMPLEMENT_DYNCREATE 매크로 및 메시지 맵에서 CView를 CWinFormsView로 변경 하도록 MFC02View 파일을 수정 하 고 기존 빈 생성자를 아래 표시 된 생성자로 바꿉니다.

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. 프로젝트를 빌드하고 실행합니다.

   **솔루션 탐색기** 에서 MFC02을 마우스 오른쪽 단추로 클릭 하 고 **시작 프로젝트로 설정** 을 선택 합니다.

   **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

   **디버그** 메뉴에서 **디버깅 하지 않고 시작** 을 클릭 합니다.

## <a name="see-also"></a>참고 항목

[Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
