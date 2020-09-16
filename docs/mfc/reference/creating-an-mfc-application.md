---
title: MFC 애플리케이션 만들기
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 7e7435a8538c04867a810e525e053109a7abc04d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683457"
---
# <a name="creating-an-mfc-application"></a>MFC 애플리케이션 만들기

MFC 애플리케이션은 MFC(Microsoft Foundation Class) 라이브러리를 기반으로 하는 실행 가능한 Windows용 애플리케이션입니다. MFC 실행 파일은 일반적으로 표준 Windows 응용 프로그램, 대화 상자, 폼 기반 응용 프로그램, 탐색기 스타일 응용 프로그램, 웹 브라우저 스타일 응용 프로그램 등의 다섯 가지 형식으로 분류 됩니다. 자세한 내용은 다음을 참조하세요.

- [클래스를 사용하여 Windows 응용 프로그램 작성](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [대화 상자 만들기 및 표시](../../mfc/creating-and-displaying-dialog-boxes.md)

- [폼 기반 MFC 응용 프로그램 만들기](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [파일 탐색기 스타일 MFC 응용 프로그램 만들기](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [웹 브라우저 스타일 MFC 응용 프로그램 만들기](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

MFC 애플리케이션 마법사에서는 선택하는 옵션에 따라 위의 다섯 가지 애플리케이션 형식 모두에 적합한 클래스와 파일을 생성합니다.

Mfc 응용 프로그램을 만드는 가장 쉬운 방법은 MFC 응용 프로그램 마법사 (Visual Studio 2019의 Mfc 응용 프로그램**프로젝트** )를 사용 하는 것입니다. Mfc 콘솔 응용 프로그램 (MFC 라이브러리를 사용 하지만 콘솔 창에서 실행 되는 명령줄 프로그램)을 만들려면 Windows 바탕 화면 마법사를 사용 하 여 **콘솔 응용 프로그램** 및 **MFC 헤더** 옵션을 선택 합니다.

::: moniker range=">=vs-2019"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>MFC 양식 또는 대화 상자 기반 응용 프로그램을 만들려면

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택 합니다.
1. 검색 상자에 "MFC"를 입력 한 다음 결과 목록에서 **Mfc 앱** 을 선택 합니다.
1. 필요에 따라 기본값을 수정 하 고 **Create** 를 눌러 **MFC 응용 프로그램 마법사**를 엽니다.
1. 필요에 따라 구성 값을 수정한 후 **마침**을 누릅니다.

자세한 내용은 [폼 기반 MFC 응용 프로그램 만들기](creating-a-forms-based-mfc-application.md)를 참조 하세요.

![Visual 스튜디오 2019의 MFC 응용 프로그램 마법사 스크린샷](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>MFC 콘솔 응용 프로그램을 만들려면

MFC 콘솔 응용 프로그램은 MFC 라이브러리를 사용 하지만 콘솔 창에서 실행 되는 명령줄 프로그램입니다.

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택 합니다.
1. 검색 상자에 "Desktop"을 입력 한 다음 결과 목록에서 **Windows 바탕 화면 마법사** 를 선택 합니다.
1. 필요에 따라 프로젝트 이름을 수정 하 고 **다음** 을 눌러 **Windows 바탕 화면 마법사**를 엽니다.
1. **MFC 헤더** 상자를 확인 하 고 필요에 따라 다른 값을 설정한 후 **마침**을 누릅니다.

![Visual 스튜디오 2019의 Windows 바탕 화면 마법사 스크린샷](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=vs-2017"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>MFC 양식 또는 대화 상자 기반 응용 프로그램을 만들려면

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택 합니다.
1. **설치** 된 템플릿에서 **Visual C++**  >  **MFC/ATL**을 선택 합니다. 표시 되지 않는 경우 Visual Studio 설치 관리자를 사용 하 여 추가 합니다.
1. 가운데 창에서 **MFC 응용 프로그램** 을 선택 합니다.
1. 필요에 따라 구성 값을 수정한 후 **마침**을 누릅니다.

자세한 내용은 [폼 기반 MFC 응용 프로그램 만들기](creating-a-forms-based-mfc-application.md)를 참조 하세요.

![Visual 스튜디오 2017의 MFC 응용 프로그램 마법사 스크린샷](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>MFC 콘솔 응용 프로그램을 만들려면

MFC 콘솔 응용 프로그램은 MFC 라이브러리를 사용 하지만 콘솔 창에서 실행 되는 명령줄 프로그램입니다.

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택 합니다.
1. **설치** 된 템플릿에서 **Visual C++** > **Windows 데스크톱**을 선택 합니다.
1. 가운데 창에서 **Windows 바탕 화면 마법사** 를 선택 합니다.
1. 필요에 따라 프로젝트 이름을 수정한 다음 **확인** 을 눌러 **Windows 바탕 화면 마법사**를 엽니다.
1. **MFC 헤더** 상자를 확인 하 고 필요에 따라 다른 값을 설정한 후 **마침**을 누릅니다.

![Visual 스튜디오 2017의 Windows 바탕 화면 마법사 스크린샷](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=vs-2015"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>MFC 양식 또는 대화 상자 기반 응용 프로그램을 만들려면

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택 합니다.
1. **설치** 된 템플릿에서 **Visual C++** > **MFC**를 선택 합니다.
1. 가운데 창에서 **MFC 응용 프로그램** 을 선택 합니다.
1. **다음** 을 클릭 하 여 **MFC 응용 프로그램 마법사**를 시작 합니다.

자세한 내용은 [폼 기반 MFC 응용 프로그램 만들기](creating-a-forms-based-mfc-application.md)를 참조 하세요.

![Visual 스튜디오 2015의 MFC 응용 프로그램 마법사 스크린샷](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>MFC 콘솔 응용 프로그램을 만들려면

MFC 콘솔 응용 프로그램은 MFC 라이브러리를 사용 하지만 콘솔 창에서 실행 되는 명령줄 프로그램입니다.

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택 합니다.
1. **설치** 된 템플릿에서 **Visual C++** > **Win32**를 선택 합니다.
1. 가운데 창에서 **Win32 콘솔 응용 프로그램** 을 선택 합니다.
1. 필요에 따라 프로젝트 이름을 수정한 다음 **확인**을 누릅니다.
1. 마법사의 두 번째 페이지에서 **MFC에 대 한 공용 헤더 추가** 상자를 선택 하 고 필요에 따라 다른 값을 설정한 후 **마침**을 누릅니다.

::: moniker-end

프로젝트를 만든 후 **솔루션 탐색기**에서 프로젝트 관련 파일을 볼 수 있습니다. 마법사에서 프로젝트용으로 만드는 파일에 대한 자세한 내용은 프로젝트 생성 파일인 ReadMe.txt를 참조하세요. 파일 형식에 대한 자세한 내용은 [Visual Studio C++ 프로젝트용으로 만들어지는 파일 형식](../../build/reference/file-types-created-for-visual-cpp-projects.md)을 참조하세요.

## <a name="see-also"></a>추가 정보

[코드 마법사에서 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[속성 페이지](../../build/reference/property-pages-visual-cpp.md)
