---
description: '자세한 정보: MFC 데스크톱 응용 프로그램'
title: MFC 데스크톱 애플리케이션
ms.date: 07/28/2019
f1_keywords:
- MFC
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
ms.openlocfilehash: ac89ecfc603593a4328876bae061657fba26fed1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172793"
---
# <a name="mfc-desktop-applications"></a>MFC 데스크톱 애플리케이션

MFC(Microsoft Foundation Class) 라이브러리는 많은 Win32 및 COM API에 대한 개체 지향 래퍼를 제공합니다. 간단한 데스크톱 애플리케이션을 만드는 데도 사용되지만, 여러 컨트롤 간의 매우 복잡한 사용자 인터페이스를 개발해야 하는 경우에도 매우 유용합니다. MFC를 사용하여 Office 스타일의 사용자 인터페이스를 제공하는 애플리케이션을 만들 수 있습니다. Windows 플랫폼 자체에 대 한 설명서는 [windows 설명서](/windows/index)를 참조 하십시오. MFC 없이 c + +로 Windows 응용 프로그램을 빌드하는 방법에 대 한 자세한 내용은 [Win32 API 사용 하 여 데스크톱 windows 앱 빌드](/windows/win32/index)를 참조 하세요.

MFC 참조는 MFC 라이브러리를 구성하는 매크로, 전역 변수, 전역 함수 및 클래스를 포함합니다.

각 클래스에 포함된 개별 계층 구조 차트는 기본 클래스를 찾는 데 유용합니다. MFC 참조는 일반적으로 상속된 멤버 함수 또는 상속된 연산자를 설명하지 않습니다. 이러한 함수에 대한 자세한 내용을 보려면 계층 구조 다이어그램에 나와 있는 기본 클래스를 참조하십시오.

각 클래스에 대한 설명서는 클래스 개요, 범주별 멤버 요약과 멤버 함수, 오버로드된 연산자 및 데이터 멤버에 대한 항목을 포함합니다.

공용 및 보호된 클래스 멤버는 일반적으로 애플리케이션 또는 파생된 클래스에서 사용될 경우에만 기술됩니다. 전체 클래스 멤버 목록을 보려면 클래스 헤더 파일을 참조하십시오.

> [!IMPORTANT]
> MFC 클래스 및 해당 멤버는 Windows 런타임 환경에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.
>
> MBC(멀티바이트 문자 인코딩)용 MFC 라이브러리(DLL)은 Visual Studio에 더 이상 포함되지 않지만 Visual Studio 추가 기능으로 사용할 수 있습니다. 자세한 내용은 [MFC MBCS DLL 추가 기능](mfc-mbcs-dll-add-on.md)을 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[개념](mfc-concepts.md)<br/>
MFC 항목에 대한 개념 문서입니다.

[계층 구조 차트](hierarchy-chart.md)<br/>
클래스 라이브러리의 클래스 관계를 시각적으로 자세히 표시합니다.

[클래스 개요](class-library-overview.md)<br/>
범주에 따라 MFC 라이브러리의 클래스를 나열합니다.

[연습](walkthroughs-mfc.md)<br/>
MFC 라이브러리 기능과 관련된 다양한 작업을 안내하는 문서가 포함되어 있습니다.

[기술 참고 사항](mfc-technical-notes.md)<br/>
MFC 개발 팀에서 클래스 라이브러리에 대해 작성한 전문 항목에 대한 링크를 제공합니다.

[MFC에 대한 사용자 지정](customization-for-mfc.md)<br/>
MFC 애플리케이션을 사용자 지정하기 위한 몇 가지 팁을 제공합니다.

[클래스](reference/mfc-classes.md)<br/>
MFC 클래스에 대한 링크 및 헤더 파일 정보를 제공합니다.

[내부 클래스](reference/internal-classes.md)<br/>
MFC에서 내부적으로 사용됩니다. 완벽을 기하기 위해 이 단원에서는 이러한 내부 클래스에 대해 설명하지만 이러한 내부 클래스는 코드에서 직접 사용할 수 없습니다.

[매크로 및 전역](reference/mfc-macros-and-globals.md)<br/>
MFC 라이브러리의 매크로 및 전역 함수에 대한 링크를 제공합니다.

[구조체, 스타일, 콜백 및 메시지 맵](reference/structures-styles-callbacks-and-message-maps.md)<br/>
MFC 라이브러리에서 사용하는 구조, 스타일, 콜백 및 메시지 맵에 대한 링크를 제공합니다.

[MFC 마법사 및 대화 상자](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Visual Studio에서 MFC 애플리케이션을 만드는 기능을 안내하는 가이드입니다.

[리소스 파일 작업](../windows/working-with-resource-files.md)<br/>
리소스 파일을 사용하여 UI 문자열 및 대화 상자 레이아웃과 같은 정적 사용자 인터페이스 데이터를 관리하는 방법입니다.

## <a name="related-sections"></a>관련 단원

[계층 구조 차트 범주](hierarchy-chart-categories.md)<br/>
범주별 MFC 계층 구조 차트에 대해 설명합니다.

[ATL/MFC 공유 클래스](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
MFC와 ATL 간 공유되는 클래스에 대한 링크를 제공합니다.

[MFC 샘플](../overview/visual-cpp-samples.md#mfc-samples)<br/>
MFC 사용 방법을 보여 주는 샘플에 대한 링크를 제공합니다.

[Visual C++ 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
ATL, MFC, OLE DB 템플릿, C 런타임 라이브러리, C++ 표준 라이브러리를 포함하여 Visual C++에 제공되는 다양한 라이브러리에 대한 링크를 제공합니다.

[Visual Studio의 디버깅](/visualstudio/debugger/debugging-in-visual-studio)<br/>
Visual Studio 디버거를 사용하여 애플리케이션이나 저장 프로시저의 논리적 오류를 수정하는 방법을 설명하는 항목의 링크를 제공합니다.

## <a name="see-also"></a>참고 항목

[MFC 및 ATL](mfc-and-atl.md)
