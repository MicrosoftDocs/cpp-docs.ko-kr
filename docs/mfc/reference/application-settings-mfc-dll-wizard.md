---
description: '자세히 알아보기: 응용 프로그램 설정, MFC DLL 마법사'
title: MFC DLL 마법사, 애플리케이션 설정
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.appset
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
ms.openlocfilehash: da9579ef9a834fa0c2362b1569c2efa808132faa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322800"
---
# <a name="application-settings-mfc-dll-wizard"></a>MFC DLL 마법사, 애플리케이션 설정

MFC DLL 마법사의이 페이지를 사용 하 여 기본 기능을 디자인 하 고 새 MFC DLL 프로젝트에 추가할 수 있습니다.

## <a name="dll-type"></a>DLL 형식

만들려는 DLL 유형을 선택 합니다.

- **공유 MFC DLL을 사용 하는 기본 MFC DLL**

   MFC 라이브러리를 프로그램에 공유 DLL로 연결 하려면이 옵션을 선택 합니다. 이 옵션을 사용 하면 DLL과 호출 하는 응용 프로그램 간에 MFC 개체를 공유할 수 없습니다. 프로그램은 런타임에 MFC 라이브러리를 호출 합니다. 이 옵션은 MFC 라이브러리를 사용 하는 여러 실행 파일로 구성 된 경우 프로그램의 디스크 및 메모리 요구 사항을 줄입니다. Win32 및 MFC 프로그램은 모두 DLL에서 함수를 호출할 수 있습니다. 이 형식의 프로젝트를 사용 하 여 MFC DLL을 다시 배포 해야 합니다.

- **정적으로 MFC가 연결 된 기본 MFC DLL**

   빌드 시 프로그램을 MFC 라이브러리에 정적으로 연결 하려면이 옵션을 선택 합니다. Win32 및 MFC 프로그램은 모두 DLL에서 함수를 호출할 수 있습니다. 이 옵션을 사용 하면 프로그램 크기가 늘어나지만 MFC DLL을이 형식의 프로젝트로 재배포할 필요가 없습니다. DLL과 호출 하는 응용 프로그램 간에는 MFC 개체를 공유할 수 없습니다.

- **MFC 확장 DLL**

   프로그램에서 런타임에 MFC 라이브러리를 호출 하 고 DLL과 호출 하는 응용 프로그램 간에 MFC 개체를 공유 하려는 경우이 옵션을 선택 합니다. 이 옵션을 사용 하면 모든 MFC 라이브러리를 사용 하는 여러 실행 파일로 구성 된 경우 프로그램의 디스크 및 메모리 요구 사항이 줄어듭니다. MFC 프로그램만 DLL에서 함수를 호출할 수 있습니다. 이 형식의 프로젝트를 사용 하 여 MFC DLL을 다시 배포 해야 합니다.

## <a name="additional-features"></a>추가 기능

MFC DLL에서 자동화를 지원 해야 하는지 여부와 Windows 소켓을 지원 해야 하는지 여부를 선택 합니다.

- **Automation**

   프로그램에서 다른 프로그램에 구현 된 개체를 조작할 수 있도록 하려면 **자동화** 를 선택 합니다. **자동화** 를 선택 하면 프로그램이 다른 자동화 클라이언트에도 노출 됩니다. 자세한 내용은 [자동화](../../mfc/automation.md) 를 참조 하세요.

- **Windows 소켓**

   프로그램에서 Windows 소켓을 지원함을 나타내려면이 옵션을 선택 합니다. Windows 소켓을 통해 TCP/IP 네트워크를 통해 통신 하는 프로그램을 작성할 수 있습니다.

   Windows 소켓을 지 원하는 MFC DLL을 만든 경우에는 [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 이 소켓에 대 한 지원을 초기화 하 고, mfc 헤더 파일 Stdafx.h는 AfxSock를 포함 합니다.

## <a name="see-also"></a>참고 항목

[MFC DLL 마법사](../../mfc/reference/mfc-dll-wizard.md)<br/>
[MFC DLL 프로젝트 만들기](../../mfc/reference/creating-an-mfc-dll-project.md)
