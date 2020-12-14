---
description: '자세한 정보: c + + 프로젝트 템플릿'
title: Visual C++ 프로젝트 형식
ms.date: 08/13/2019
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: 924e53e0d977b4f9b3b40bf7444f8495dbe1d451
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253171"
---
# <a name="c-project-templates"></a>C++ 프로젝트 템플릿

Visual Studio 프로젝트 템플릿은 만들려는 프로젝트 종류에 적절 한 소스 코드 파일, 컴파일러 옵션, 메뉴, 도구 모음, 아이콘, 참조 및 `#include` 문을 생성 합니다. Visual Studio에는 다양 한 종류의 c + + 프로젝트 템플릿이 포함 되어 있으며, 프로젝트를 만들 때 프로젝트를 사용자 지정할 수 있도록 다양 한 마법사를 제공 합니다. 프로젝트를 만든 직후에 애플리케이션을 빌드하고 실행할 수 있으므로, 애플리케이션을 개발하면서 간간이 빌드하는 것이 좋습니다.

> [!NOTE]
> C++ 프로젝트 템플릿을 사용하여 C 언어 프로젝트를 만들 수 있습니다. 생성된 프로젝트에서 파일 이름 확장명이 .cpp인 파일을 찾아 확장명을 .c로 변경합니다. 그런 다음 솔루션이 아닌 프로젝트의 **프로젝트 속성** 페이지에서 **구성 속성**, **C/C++** 를 차례로 확장하고 **고급** 을 선택합니다. **컴파일 옵션** 설정을 **C 코드로 컴파일(/TC)** 로 변경합니다.

## <a name="project-templates"></a>프로젝트 템플릿

Visual Studio에 포함된 프로젝트 템플릿은 설치한 제품 버전 및 워크로드에 따라 다릅니다. C + +를 사용한 데스크톱 개발 워크 로드를 설치한 경우 Visual Studio에는 이러한 c + + 프로젝트 템플릿이 있습니다.

### <a name="windows-desktop"></a>Windows Desktop

|프로젝트 템플릿|설명|
|----------------------|-----------------------------|
|[Windows 콘솔 애플리케이션](../../windows/overview-of-windows-programming-in-cpp.md)|Windows 콘솔 애플리케이션을 만드는 프로젝트입니다.|
|[Windows 데스크톱 애플리케이션](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Windows 데스크톱(Win32) 애플리케이션을 만드는 프로젝트입니다.|
|[동적 연결 라이브러리](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|DLL(동적 연결 라이브러리)을 만드는 프로젝트입니다.|
|[정적 라이브러리](../walkthrough-creating-and-using-a-static-library-cpp.md)|정적 라이브러리(LIB)를 만드는 프로젝트입니다.|
|[Windows 데스크톱 마법사](../../windows/windows-desktop-wizard.md)|추가 옵션을 사용하여 Windows 데스크톱 애플리케이션 및 라이브러리를 만드는 마법사입니다.|

### <a name="general"></a>일반

|프로젝트 템플릿|설명|
|----------------------|-----------------------------|
|빈 프로젝트|애플리케이션, 라이브러리 또는 DLL을 만드는 빈 프로젝트입니다. 필요한 모든 코드 또는 리소스를 추가해야 합니다.|
|[메이크파일 프로젝트](creating-a-makefile-project.md)|Visual Studio 프로젝트에서 Windows 메이크파일을 래핑하는 프로젝트입니다. Visual Studio에서 메이크파일을 있는 그대로 열려면 [폴더 열기](../open-folder-projects-cpp.md)를 사용 합니다.|
|공유 항목 프로젝트|여러 프로젝트 간에 코드 파일이 나 리소스 파일을 공유 하는 데 사용 되는 프로젝트입니다. 이 프로젝트 형식은 실행 파일을 생성 하지 않습니다.|

### <a name="atl"></a>ATL

|프로젝트 템플릿|설명|
|----------------------|-----------------------------|
|[ATL 프로젝트](../../atl/reference/creating-an-atl-project.md)|액티브 템플릿 라이브러리를 사용하는 프로젝트입니다.|

### <a name="test"></a>테스트

|프로젝트 템플릿|설명|
|----------------------|-----------------------------|
|[기본 단위 테스트 프로젝트](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|기본 C++ 단위 테스트를 포함하는 프로젝트입니다.|

### <a name="mfc"></a>MFC

MFC 및 ATL 지원 구성 요소를 Visual Studio 설치에 추가하는 경우 이러한 프로젝트 템플릿이 Visual Studio에 추가됩니다.

|프로젝트 템플릿|설명|
|----------------------|-----------------------------|
|[MFC 애플리케이션](../../mfc/reference/creating-an-mfc-application.md)|MFC(Microsoft Foundation Class) 라이브러리를 사용하는 애플리케이션을 만드는 프로젝트입니다.|
|[MFC ActiveX 컨트롤](../../mfc/reference/creating-an-mfc-activex-control.md)|MFC 라이브러리를 사용하는 ActiveX 컨트롤을 만드는 프로젝트입니다.|
|[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)|MFC 라이브러리를 사용하는 동적 연결 라이브러리를 만드는 프로젝트입니다.|

### <a name="windows-universal-apps"></a>Windows 유니버설 앱

C++ Windows 유니버설 플랫폼 도구 구성 요소를 Visual Studio 설치에 추가하는 경우 이러한 프로젝트 템플릿이 Visual Studio에 추가됩니다.

C++에서 Windows 유니버설 앱의 개요는 [유니버설 Windows 앱(C++)](../../cppcx/universal-windows-apps-cpp.md)을 참조합니다.

|프로젝트 템플릿|설명|
|----------------------|-----------------------------|
|빈 앱|미리 정의된 컨트롤 또는 레이아웃이 없는 단일 페이지 UWP(유니버설 Windows 플랫폼) 앱용 프로젝트입니다.|
|DirectX 11 앱|DirectX 11을 사용하는 유니버설 Windows 플랫폼 앱용 프로젝트입니다.|
|DirectX 12 앱|DirectX 12를 사용하는 유니버설 Windows 플랫폼 앱용 프로젝트입니다.|
|DirectX 11 및 XAML 앱|DirectX 11 및 XAML을 사용하는 유니버설 Windows 플랫폼 앱용 프로젝트입니다.|
|단위 테스트 앱|UWP(유니버설 Windows 플랫폼) 앱용 단위 테스트 앱을 만드는 프로젝트입니다.|
|DLL|유니버설 Windows 플랫폼 앱 또는 런타임 구성 요소에서 사용할 수 있는 네이티브 DLL(동적 연결 라이브러리)에 대한 프로젝트입니다.|
|정적 라이브러리|유니버설 Windows 플랫폼 앱 또는 런타임 구성 요소에서 사용할 수 있는 네이티브 정적 연결 라이브러리(LIB)에 대한 프로젝트입니다.|
|Windows 런타임 구성 요소|앱이 작성된 프로그래밍 언어에 상관없이 유니버설 Windows 플랫폼 앱에서 사용할 수 있는 Windows 런타임 구성 요소에 대한 프로젝트입니다.|
|Windows 애플리케이션 패키징 프로젝트|Microsoft Store를 통해 배포되거나 테스트용으로 로드된 데스크톱 애플리케이션을 활성화하는 UWP 패키지를 만드는 프로젝트입니다.|

## <a name="todo-comments"></a>TODO 주석

프로젝트 템플릿에서 생성하는 대부분의 파일은 원하는 소스 코드를 입력할 위치를 확인할 수 있도록 TODO 주석을 포함합니다. 코드 추가 방법에 대한 자세한 내용은 [코드 마법사로 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md) 및 [리소스 파일 작업](../../windows/working-with-resource-files.md)을 참조합니다.
