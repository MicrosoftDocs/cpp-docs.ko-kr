---
description: '자세한 정보: MFC DLL 마법사'
title: MFC DLL 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.overview
helpviewer_keywords:
- MFC DLLs [MFC], creating
- MFC DLL Wizard
- DLLs [MFC], MFC
- DLL wizard [MFC]
- MFC DLLs [MFC]
- DLLs [MFC], creating
ms.assetid: 4e936031-7e39-4f40-a295-42a09c5ff264
ms.openlocfilehash: 0f786255c22e644335c5154e0f14add59a2a418a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219163"
---
# <a name="mfc-dll-wizard"></a>MFC DLL 마법사

Mfc DLL 마법사를 사용 하 여 MFC DLL 프로젝트를 만드는 경우 기본 제공 기능이 포함 된 작업 시작 응용 프로그램을 가져옵니다 .이 기능은 컴파일될 때 [DLL](../../build/dlls-in-visual-cpp.md)의 기본 기능을 구현 합니다. MFC 스타터 프로그램에는 c + + 소스 파일 (.cpp), 리소스 (.rc) 파일 및 프로젝트 파일 (.vcxproj)이 포함 되어 있습니다. 이러한 스타터 파일에서 생성 된 코드는 MFC를 기반으로 합니다. 자세한 내용은 Visual Studio에서 프로젝트에 대해 생성 된 Readme.txt의 파일 세부 정보 및 [MFC DLL 마법사에 의해 생성 되는 클래스 및 함수](../../mfc/reference/classes-and-functions-generated-by-the-mfc-dll-wizard.md) 를 참조 하세요.

## <a name="overview"></a>개요

이 마법사 페이지에서는 사용자가 만드는 [MFC DLL 프로젝트에 대 한 현재 응용 프로그램 설정을](../../mfc/reference/application-settings-mfc-dll-wizard.md) 설명 합니다. 기본적으로 프로젝트는 추가 설정이 없는 일반 MFC DLL (MFC 공유) 프로젝트로 생성 됩니다.

이러한 기본값을 변경 하려면 마법사의 왼쪽 열에서 **응용 프로그램 설정** 을 클릭 하 고 MFC DLL 마법사의 해당 페이지에서 변경 합니다.

MFC DLL 프로젝트를 만든 후 Visual C++ [코드 마법사](../../ide/adding-functionality-with-code-wizards-cpp.md)를 사용 하 여 프로젝트에 개체 또는 컨트롤을 추가할 수 있습니다.

기본 MFC DLL 프로젝트에 대 한 다음과 같은 향상 된 기능 및 유형을 수행할 수 있습니다.

- [DLL에서 내보내기](../../build/exporting-from-a-dll.md)

- [DLL에 실행 파일 연결](../../build/linking-an-executable-to-a-dll.md)

- [DLL 초기화](../../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="see-also"></a>참조

[Visual Studio 프로젝트 - C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[속성 페이지](../../build/reference/property-pages-visual-cpp.md)<br/>
[컴파일러 설정 및 빌드 속성](../../build/working-with-project-properties.md)<br/>
[MFC 클래스](../../mfc/reference/adding-an-mfc-class.md)<br/>
[멤버 함수 추가](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[인터페이스 구현](../../ide/implementing-an-interface-visual-cpp.md)<br/>
