---
description: '자세한 정보: MFC 응용 프로그램 마법사'
title: MFC 애플리케이션 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 645f0e1ed3f1f35c109d524a8c63fa36231bc61a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219215"
---
# <a name="mfc-application-wizard"></a>MFC 애플리케이션 마법사

MFC 응용 프로그램 마법사는 컴파일되는 경우 Windows 실행 파일 (.exe) 응용 프로그램의 기본 기능을 구현 하는 응용 프로그램을 생성 합니다. MFC 시작 응용 프로그램에는 c + + 소스 파일 (.cpp), 리소스 (.rc) 파일, 헤더 (.h) 파일 및 프로젝트 파일 (.vcxproj)이 포함 됩니다. 이러한 스타터 파일에서 생성 되는 코드는 MFC를 기반으로 합니다.

> [!NOTE]
> 선택한 옵션에 따라 마법사는 프로젝트에 추가 파일을 만듭니다. 예를 들어 [고급 기능](../../mfc/reference/advanced-features-mfc-application-wizard.md) 페이지에서 상황에 맞는 **도움말** 을 선택 하면 마법사에서 프로젝트의 도움말 파일을 컴파일하는 데 필요한 파일을 만듭니다. 마법사에서 만드는 파일에 대 한 자세한 내용은 [Visual Studio c + + 프로젝트용으로 만들어지는 파일 형식](../../build/reference/file-types-created-for-visual-cpp-projects.md)을 참조 하 고 프로젝트에서 Readme.txt 파일을 참조 하세요.

## <a name="overview"></a>개요

이 마법사 페이지에서는 사용자가 만드는 MFC 응용 프로그램에 대 한 현재 응용 프로그램 설정을 설명 합니다. 기본적으로 마법사는 다음과 같이 프로젝트를 만듭니다.

- [MFC 응용 프로그램 마법사, 응용 프로그램 종류](../../mfc/reference/application-type-mfc-application-wizard.md)

  - 프로젝트는 탭 MDI (다중 문서 인터페이스) 지원을 사용 하 여 만들어집니다. 자세한 내용은 [SDI 및 MDI](../../mfc/sdi-and-mdi.md)를 참조 하세요.

  - 프로젝트는 [문서/뷰 아키텍처](../../mfc/document-view-architecture.md)를 사용 합니다.

  - 프로젝트는 유니코드 라이브러리를 사용 합니다.

  - Visual Studio 프로젝트 스타일을 사용 하 여 프로젝트를 만들고 비주얼 스타일 전환을 사용 하도록 설정 합니다.

  - 프로젝트는 공유 DLL에서 MFC를 사용 합니다. 자세한 내용은 [Visual Studio에서 c/c + + Dll 만들기](../../build/dlls-in-visual-cpp.md)를 참조 하세요.

- [MFC 응용 프로그램 마법사, 복합 문서 지원](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - 프로젝트는 복합 문서에 대 한 지원을 제공 하지 않습니다.

- [MFC 애플리케이션 마법사, 문서 템플릿 문자열](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - 프로젝트는 기본 문서 템플릿 문자열에 프로젝트 이름을 사용 합니다.

- [MFC 응용 프로그램 마법사, 데이터베이스 지원](../../mfc/reference/database-support-mfc-application-wizard.md)

  - 프로젝트에서는 데이터베이스를 지원 하지 않습니다.

- [MFC 응용 프로그램 마법사, 사용자 인터페이스 기능](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - 프로젝트는 시스템 메뉴, 상태 표시줄, 최대화 및 최소화 상자, **정보** 상자, 표준 메뉴 모음 및 도킹 도구 모음, 자식 프레임 등의 표준 Windows 사용자 인터페이스 기능을 구현 합니다.

- [MFC 응용 프로그램 마법사, 고급 기능](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - 프로젝트는 인쇄 및 인쇄 미리 보기를 지원 합니다.

  - 프로젝트는 ActiveX 컨트롤을 지원 합니다. 자세한 내용은 [ActiveX 컨트롤을 만드는 작업 시퀀스](../../mfc/sequence-of-operations-for-creating-activex-controls.md)를 참조 하세요.

  - 프로젝트는 [자동화](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows 소켓](../../mfc/windows-sockets-in-mfc.md)또는 Active Accessibility에 대 한 지원을 제공 하지 않습니다.

  - 프로젝트는 **탐색기** 도킹 창, **출력** 도킹 창 및 **속성** 도킹 창을 지원 합니다.

- [MFC 응용 프로그램 마법사, 생성 된 클래스](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - 프로젝트의 뷰 클래스는 [CView 클래스](../../mfc/reference/cview-class.md)에서 파생 됩니다.

  - 프로젝트의 응용 프로그램 클래스는 [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)에서 파생 됩니다.

  - 프로젝트의 문서 클래스는 [CDocument 클래스](../../mfc/reference/cdocument-class.md)에서 파생 됩니다.

  - 프로젝트의 주 프레임 클래스는 [CMDIFrameWndEx 클래스](../../mfc/reference/cmdiframewndex-class.md)에서 파생 됩니다.

  - 프로젝트의 자식 프레임 클래스는 [CMDIChildWndEx 클래스](../../mfc/reference/cmdichildwndex-class.md)에서 파생 됩니다.

이러한 기본 설정을 변경 하려면 마법사의 왼쪽 열에서 적절 한 탭 제목을 클릭 하 고 표시 되는 페이지를 변경 합니다.

MFC 응용 프로그램 프로젝트를 만든 후 Visual C++ [코드 마법사](../../ide/adding-functionality-with-code-wizards-cpp.md)를 사용 하 여 프로젝트에 개체 또는 컨트롤을 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[MFC 응용 프로그램 만들기](../../mfc/reference/creating-an-mfc-application.md)<br/>
[MFC 데스크톱 응용 프로그램](../../mfc/mfc-desktop-applications.md)<br/>
[클래스를 사용 하 여 Windows 용 응용 프로그램 작성](../../mfc/using-the-classes-to-write-applications-for-windows.md)
