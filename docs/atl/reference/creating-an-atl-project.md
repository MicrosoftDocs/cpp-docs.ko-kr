---
description: '자세히 알아보기: ATL 프로젝트 만들기'
title: ATL 프로젝트 만들기
ms.date: 05/06/2019
f1_keywords:
- vc.appwiz.ATL.project
helpviewer_keywords:
- ATL projects, creating
- ATL70.DLL
- _ATL_MIN_CRT macro
- distributing files with ATL components
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
ms.openlocfilehash: ef52e3b398b7c32acc626dc79f62a3e91d659893
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140948"
---
# <a name="creating-an-atl-project"></a>ATL 프로젝트 만들기

ATL 프로젝트를 만드는 가장 쉬운 방법은 **새 프로젝트** 대화 상자의 **Win32 프로젝트** 폴더에 있는 ATL 프로젝트 마법사를 사용하는 것입니다.

## <a name="to-create-an-atl-project-using-the-atl-project-wizard"></a>ATL 프로젝트 마법사를 사용하여 ATL 프로젝트를 만들려면

1. Visual Studio의 주 메뉴에서 **파일 > 새로 만들기 > 프로젝트** 를 선택합니다.

1. **템플릿** 창에서 **ATL 프로젝트** 아이콘을 선택하여 **ATL 프로젝트 마법사** 를 엽니다.

1. **ATL 프로젝트 마법사** 의 [애플리케이션 설정](../../atl/reference/application-settings-atl-project-wizard.md) 페이지를 사용하여 애플리케이션 설정을 정의합니다.

   > [!NOTE]
   > 마법사의 기본 설정을 그대로 유지하려면 이 단계를 건너 뜁니다.

1. **마침** 을 클릭하여 마법사를 닫고 새 프로젝트를 개발 환경에서 엽니다.

프로젝트를 만든 후 **솔루션 탐색기** 에서 프로젝트 관련 파일을 볼 수 있습니다. 마법사에서 프로젝트용으로 만드는 파일에 대한 자세한 내용은 프로젝트 생성 파일인 ReadMe.txt를 참조하세요. 파일 형식에 대한 자세한 내용은 [Visual Studio C++ 프로젝트용으로 만들어지는 파일 형식](../../build/reference/file-types-created-for-visual-cpp-projects.md)을 참조하세요. 새 ATL 프로젝트의 구성 및 구성 변경 방법에 대한 자세한 내용은 [기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[코드 마법사에서 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[속성 페이지](../../build/reference/property-pages-visual-cpp.md)
