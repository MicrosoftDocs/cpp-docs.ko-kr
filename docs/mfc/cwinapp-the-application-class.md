---
description: '자세한 정보: CWinApp: 응용 프로그램 클래스'
title: 'CWinApp: 애플리케이션 클래스'
ms.date: 11/04/2016
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
ms.openlocfilehash: 63979846ec5b4d5bb5452e98a3ac19474b4fcd0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301635"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: 애플리케이션 클래스

MFC의 주 응용 프로그램 클래스는 Windows 운영 체제에 대 한 응용 프로그램의 초기화, 실행 및 종료를 캡슐화 합니다. 프레임 워크를 기반으로 하는 응용 프로그램은 [CWinApp](reference/cwinapp-class.md)에서 파생 된 클래스의 개체를 하나만 포함 해야 합니다. 이 개체는 windows를 만들기 전에 생성 됩니다.

`CWinApp` 는 하나 이상의 `CWinThread` 스레드가 있을 수 있는 응용 프로그램의 주 실행 스레드를 나타내는에서 파생 됩니다. 최신 버전의 MFC에서,, `InitInstance` ,  `ExitInstance` 및 `OnIdle` 멤버 함수는 실제로 클래스에 있습니다 `CWinThread` . 이러한 함수는 멤버 였던 것 처럼 여기에 설명 되어 있습니다 `CWinApp` . 토론은 개체의 역할을 기본 스레드가 아닌 응용 프로그램 개체로 서 다룹니다.

> [!NOTE]
> 응용 프로그램 클래스는 응용 프로그램의 기본 실행 스레드를 구성 합니다. Win32 API 함수를 사용 하 여 실행의 보조 스레드를 만들 수도 있습니다. 이러한 스레드는 MFC 라이브러리를 사용할 수 있습니다. 자세한 내용은 [다중 스레딩](../parallel/multithreading-support-for-older-code-visual-cpp.md)을 참조 하세요.

Windows 운영 체제에 대 한 프로그램 처럼 프레임 워크 응용 프로그램에는 `WinMain` 함수가 있습니다. 그러나 프레임 워크 응용 프로그램에서는 작성 하지 않습니다 `WinMain` . 이 클래스는 클래스 라이브러리에서 제공 되며 응용 프로그램이 시작 될 때 호출 됩니다. `WinMain` 창 클래스 등록과 같은 표준 서비스를 수행 합니다. 그런 다음 응용 프로그램 개체의 멤버 함수를 호출 하 여 응용 프로그램을 초기화 하 고 실행 합니다. 를 `WinMain` `CWinApp` 호출 하는 멤버 함수를 재정의 하 여 사용자 지정할 수 있습니다 `WinMain` .

응용 프로그램을 초기화 하기 위해는 `WinMain` 응용 프로그램 개체의 `InitApplication` 및 `InitInstance` 멤버 함수를 호출 합니다. 응용 프로그램의 메시지 루프를 실행 하려면에서 `WinMain` **run** 멤버 함수를 호출 합니다. 종료 시는 `WinMain` 응용 프로그램 개체의 `ExitInstance` 멤버 함수를 호출 합니다.

> [!NOTE]
> 이 설명서에서 **굵게** 표시 된 이름은 MFC 라이브러리 및 Visual C++에서 제공 하는 요소를 표시 합니다. 형식에 표시 `monospaced` 된 이름은 사용자가 만들거나 재정의 하는 요소를 의미 합니다.

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](general-mfc-topics.md)<br/>
[CWinApp 및 MFC 응용 프로그램 마법사](cwinapp-and-the-mfc-application-wizard.md)<br/>
[재정의 가능 CWinApp 멤버 함수](overridable-cwinapp-member-functions.md)<br/>
[특수 CWinApp 서비스](special-cwinapp-services.md)
