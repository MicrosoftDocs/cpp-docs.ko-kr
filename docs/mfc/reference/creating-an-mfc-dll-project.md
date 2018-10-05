---
title: MFC DLL 프로젝트 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcdll.project
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c83ab1a42c62a4cb1afd0c7f49f55c40633d05b
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234569"
---
# <a name="creating-an-mfc-dll-project"></a>MFC DLL 프로젝트 만들기

MFC DLL은 동시에 여러 응용 프로그램에서 사용할 수 있는 함수의 공유 라이브러리로 사용 되는 이진 파일. MFC DLL 프로젝트를 만드는 가장 쉬운 방법은 MFC DLL 마법사를 사용 하는 것입니다.

> [!NOTE]
>  IDE의 기능이의 모양을 활성 설정이 나 버전에 따라 달라질 수 있습니다 및 도움말에 설명 된 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio IDE 개인 설정](/visualstudio/ide/personalizing-the-visual-studio-ide)을 참조하세요.

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>MFC DLL 마법사를 사용 하 여 MFC DLL 프로젝트를 만들려면

1. [Visual C++ 응용 프로그램 마법사를 사용하여 프로젝트 만들기](../../ide/creating-desktop-projects-by-using-application-wizards.md) 도움말 항목의 지침을 따릅니다.

**참고** 에 **새 프로젝트** 대화 상자를 선택 합니다 `MFC DLL` MFC DLL 마법사를 열려면 템플릿 창에서 아이콘입니다.

1. 사용 하 여 응용 프로그램 설정을 정의 합니다 [응용 프로그램 설정](../../mfc/reference/application-settings-mfc-dll-wizard.md) 페이지의 [MFC DLL 마법사](../../mfc/reference/mfc-dll-wizard.md)합니다.

    > [!NOTE]
    >  마법사의 기본 설정을 그대로 유지하려면 이 단계를 건너 뜁니다.

1. 클릭 **완료할** 마법사를 닫고에서 새 프로젝트를 열고 **솔루션 탐색기**합니다.

프로젝트가 만들어진 후에 만들어진 파일을 볼 수 있습니다 **솔루션 탐색기**합니다. 마법사에서 프로젝트용으로 만드는 파일에 대한 자세한 내용은 프로젝트 생성 파일인 ReadMe.txt를 참조하세요. 파일 형식에 대 한 자세한 내용은 참조 하세요. [Visual c + + 프로젝트용으로 만들어지는 파일 형식](../../ide/file-types-created-for-visual-cpp-projects.md)합니다.

## <a name="see-also"></a>참고 항목

[Visual C++ 프로젝트 형식](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[코드 마법사로 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[속성 페이지](../../ide/property-pages-visual-cpp.md)


