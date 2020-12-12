---
description: '자세히 알아보기: 마법사 및 리소스 편집기'
title: 마법사 및 리소스 편집기
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
ms.openlocfilehash: b493746365809ca6fd193a31d0e7f53917a9646f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284917"
---
# <a name="wizards-and-the-resource-editors"></a>마법사 및 리소스 편집기

Visual C++에는 여러 통합 리소스 편집기와 함께 MFC 프로그래밍에서 사용할 수 있는 여러 가지 마법사가 포함 되어 있습니다. Activex 컨트롤 프로그래밍의 경우 [Activex 컨트롤 마법사](../mfc/reference/mfc-activex-control-wizard.md) 는 MFC 응용 프로그램 마법사의 용도로 사용 하는 것과 매우 유사 합니다. 이러한 도구를 사용 하지 않고 MFC 응용 프로그램을 작성할 수 있지만 도구를 사용 하면 작업을 크게 간소화 하 고 속도를 높일 수 있습니다.

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a> Mfc 응용 프로그램 마법사를 사용 하 여 MFC 응용 프로그램 만들기

[Mfc 응용 프로그램 마법사](../mfc/reference/mfc-application-wizard.md) 를 사용 하 여 OLE 및 데이터베이스 지원을 포함할 수 있는 VISUAL C++에서 mfc 프로젝트를 만듭니다. 프로젝트의 파일에는 응용 프로그램, 문서, 뷰 및 프레임 창 클래스가 포함 됩니다. 메뉴 및 선택적 도구 모음을 비롯 한 표준 리소스 기타 필수 Windows 파일 프로그램의 도움말 파일을 만들기 위해 수정 하 고 확장할 수 있는 표준 Windows 도움말 항목을 포함 하는 선택적 .rtf 파일.

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> 클래스 뷰를 사용 하 여 클래스 및 Windows 메시지 관리

클래스 뷰를 사용 하 여 Windows 메시지 및 명령에 대 한 처리기 함수를 만들고, 클래스를 만들고 관리 하 고, 클래스 멤버 변수를 만들고, 자동화 메서드와 속성을 만들고, 데이터베이스 클래스를 만들 수 있습니다.

> [!NOTE]
> 클래스 뷰 MFC 클래스의 가상 함수를 재정의 하는 데에도 도움이 됩니다. 재정의할 클래스 및 가상 함수를 선택 합니다. 나머지 프로세스는 다음 단락에 설명 된 대로 메시지 처리와 비슷합니다.

Windows에서 실행 되는 응용 프로그램은 [메시지 구동 방식](../mfc/message-handling-and-mapping.md)입니다. 사용자 작업 및 실행 중인 프로그램에서 발생 하는 기타 이벤트로 인해 Windows에서 프로그램의 windows로 메시지를 보낼 수 있습니다. 예를 들어 사용자가 창에서 마우스를 클릭 하면 마우스 왼쪽 단추를 누를 때 WM_LBUTTONDOWN 메시지가 전송 되 고 단추를 놓으면 WM_LBUTTONUP 메시지가 전송 됩니다. 또한 Windows는 사용자가 메뉴 모음에서 명령을 선택할 때 WM_COMMAND 메시지를 보냅니다.

MFC 프레임 워크에서 문서, 뷰, 프레임 창, 문서 템플릿 및 응용 프로그램 개체와 같은 다양 한 개체가 메시지를 "처리할" 수 있습니다. 이러한 개체는 멤버 함수 중 하나로 "처리기 함수"를 제공 하 고 프레임 워크는 들어오는 메시지를 해당 처리기에 매핑합니다.

프로그래밍 작업의 많은 부분에서 개체에 매핑할 메시지를 선택한 다음 해당 매핑을 구현 하는 것입니다. 이렇게 하려면 클래스 뷰 및 [클래스 마법사](reference/mfc-class-wizard.md)를 사용 합니다.

[클래스 마법사](reference/mfc-class-wizard.md) 가 빈 메시지 처리기 멤버 함수를 만들고 소스 코드 편집기를 사용 하 여 처리기의 본문을 구현 합니다. 또한 클래스 (사용자 고유의 클래스, MFC 클래스에서 파생 되지 않은 클래스 포함)를 만들거나 편집 하 고 클래스 뷰 하 여 해당 멤버를 편집할 수 있습니다. 클래스 뷰 사용에 대 한 자세한 내용과 프로젝트에 코드를 추가 하는 마법사에 대 한 자세한 내용은 [코드 마법사로 기능 추가](../ide/adding-functionality-with-code-wizards-cpp.md)를 참조 하세요.

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> 리소스 편집기를 사용 하 여 리소스 만들기 및 편집

Visual C++ [리소스 편집기](../windows/resource-editors.md) 를 사용 하 여 메뉴, 대화 상자, 사용자 지정 컨트롤, 액셀러레이터 키, 비트맵, 아이콘, 커서, 문자열 및 버전 리소스를 만들고 편집할 수 있습니다. Visual C++ 버전 4.0을 사용 하는 경우 도구 모음 편집기를 사용 하면 도구 모음을 훨씬 쉽게 만들 수 있습니다.

더 많은 도움을 돕기 위해 MFC 라이브러리는 COMMON 이라는 파일을 제공 합니다. RES-공통에서 복사할 수 있는 "클립 아트" 리소스를 포함 합니다. RES를 만들어 사용자 고유의 리소스 파일에 붙여넣습니다. 일반적인. RES에는 도구 모음 단추, 일반 커서, 아이콘 등이 포함 됩니다. 응용 프로그램에서 이러한 리소스를 사용 하 고, 수정 하 고, 재배포할 수 있습니다. 일반에 대 한 자세한 내용은을 (를). RES ( [클립 아트) 샘플](../overview/visual-cpp-samples.md)을 참조 하세요.

MFC 응용 프로그램 마법사, Visual C++ 마법사, 리소스 편집기 및 MFC 프레임 워크는 많은 작업을 수행 하 고 코드를 훨씬 더 쉽게 관리할 수 있도록 합니다. 응용 프로그램 관련 코드의 대부분은 문서 및 뷰 클래스에 있습니다.

## <a name="see-also"></a>참고 항목

[클래스를 사용 하 여 Windows 용 응용 프로그램 작성](../mfc/using-the-classes-to-write-applications-for-windows.md)
