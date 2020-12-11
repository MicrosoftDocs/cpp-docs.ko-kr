---
description: '자세한 정보: ATL 프로젝트 마법사'
title: ATL 프로젝트 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.overview
helpviewer_keywords:
- ATL projects, creating
- ATL Project Wizard
ms.assetid: 564d2aaf-5b8e-4c2a-a925-ca40a283ea34
ms.openlocfilehash: a254447d0590abd3d68090dac04c3b6134f94b19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158675"
---
# <a name="atl-project-wizard"></a>ATL 프로젝트 마법사

ATL (액티브 템플릿 라이브러리)은 작고 빠른 COM 개체 작성을 간소화 하는 템플릿 기반 c + + 클래스 집합입니다. ATL 프로젝트 마법사는 COM 개체를 포함 하는 구조를 포함 하는 프로젝트를 만듭니다.

## <a name="overview"></a>개요

이 마법사 페이지에서는 만드는 [ATL 프로젝트에 대 한 현재 응용 프로그램 설정을](../../atl/reference/application-settings-atl-project-wizard.md) 설명 합니다. 기본적으로 프로젝트의 설정은 다음과 같습니다.

- 동적 연결 라이브러리는 서버가 DLL 이므로 in-process 서버 임을 지정 합니다.

- 특성 사용은 프로젝트에서 특성을 사용 하도록 지정 합니다.

이러한 기본값을 변경 하려면 마법사의 왼쪽 열에서 **응용 프로그램 설정** 을 클릭 하 고 ATL 프로젝트 마법사의 해당 페이지에서 변경 합니다.

문자 집합 선택 및 링크 기본값을 포함 한 기본 프로젝트 설정에 대 한 자세한 내용은 [기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)을 참조 하세요.

ATL 프로젝트를 만든 후 Visual C++ [코드 마법사](../../ide/adding-functionality-with-code-wizards-cpp.md)를 사용 하 여 프로젝트에 개체 또는 컨트롤을 추가할 수 있습니다. 코드 마법사를 사용 하 여 기본 ATL 프로젝트에 다음과 같은 향상 된 기능을 만들 수 있습니다.

- [ATL 프로젝트에 개체 및 컨트롤 추가](../../atl/reference/adding-objects-and-controls-to-an-atl-project.md)

- [ATL 프로젝트에 새 인터페이스 추가](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)

- [ATL 프로젝트에 COM + 1.0 구성 요소 추가](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

또한 ATL 프로젝트를 만들고 향상 시킬 때 다음 작업을 고려해 야 합니다.

- [ATL 개체를 noncreatable로 설정](../../atl/reference/making-an-atl-object-noncreatable.md)

- [ATL 프로젝트에 대 한 컴파일러 최적화](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

[프로젝트 속성 페이지에서](../../build/reference/general-property-page-project.md) 프로젝트 속성 (예: [CRT에 정적으로 연결](../../atl/programming-with-atl-and-c-run-time-code.md))을 지정 하 고, ATL 프로젝트에 대 한 [빌드 구성을](/visualstudio/ide/understanding-build-configurations) 설정할 수 있습니다.

## <a name="see-also"></a>참조

[Visual Studio 프로젝트 - C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Visual Studio의 C++ 프로젝트 형식](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[ATL 및 C Run-Time 코드를 사용한 프로그래밍](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[자습서](../../atl/active-template-library-atl-tutorial.md)
