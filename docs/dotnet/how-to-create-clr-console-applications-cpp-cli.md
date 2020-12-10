---
title: '방법: CLR 콘솔 애플리케이션 만들기(C++/CLI)'
description: Visual Studio에서 c + +/CLI를 사용 하는 CLR 콘솔 앱 프로젝트를 만드는 방법에 대해 알아봅니다.
ms.date: 12/08/2020
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.openlocfilehash: ef74ca4cc31884543ff18d63d981504f36d1838e
ms.sourcegitcommit: 754df5278f795f661d4eeb0d4cacc908aa630159
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933224"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>방법: CLR 콘솔 애플리케이션 만들기(C++/CLI)

::: moniker range="msvc-140"

**새 프로젝트** 대화 상자의 **CLR 콘솔 응용 프로그램** 템플릿을 사용 하 여 이미 필수 프로젝트 참조 및 파일이 있는 콘솔 응용 프로그램 프로젝트를 만들 수 있습니다.

::: moniker-end
::: moniker range="msvc-150"

**새 프로젝트** 대화 상자에서 **CLR 콘솔 응용 프로그램** 템플릿을 사용 하 여 이미 필수 프로젝트 참조 및 파일이 있는 콘솔 응용 프로그램 프로젝트를 만들 수 있습니다.

Visual Studio c + + 워크 로드를 설치 하면 c + +/CLI 지원이 기본적으로 설치 되지 않습니다. **새 프로젝트** 대화 상자의 VISUAL C++에 CLR 머리글이 표시 되지 않으면 c + +/cli 지원을 설치 해야 할 수 있습니다. 자세한 내용은 [c + +/cli를 사용한 .net 프로그래밍](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)을 참조 하세요.

::: moniker-end
::: moniker range="msvc-160"

**새 프로젝트 만들기** 대화 상자에서 **CLR 콘솔 앱 (.NET Framework)** 템플릿을 사용 하 여 이미 필수 프로젝트 참조 및 파일이 있는 콘솔 응용 프로그램 프로젝트를 만들 수 있습니다.

Visual Studio c + + 워크 로드를 설치 하면 c + +/CLI 지원이 기본적으로 설치 되지 않습니다. **새 프로젝트 만들기** 대화 상자에 CLR 프로젝트 템플릿이 표시 되지 않는 경우 c + +/cli 지원을 설치 해야 할 수 있습니다. 자세한 내용은 [c + +/cli를 사용한 .net 프로그래밍](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)을 참조 하세요.

::: moniker-end

일반적으로 콘솔 응용 프로그램은 독립 실행형 실행 파일로 컴파일되지만 그래픽 사용자 인터페이스가 없습니다. 사용자가 명령 프롬프트에서 콘솔 앱을 실행 합니다. 명령줄을 사용 하 여 실행 중인 앱에 대 한 지침을 실행할 수 있습니다. 앱은 명령 창에 텍스트로 출력 정보를 제공 합니다. 콘솔 앱에 대 한 즉각적인 피드백을 통해 프로그래밍을 배우는 좋은 방법입니다. 그래픽 사용자 인터페이스를 구현 하는 방법에 대해서는 걱정할 필요가 없습니다.

::: moniker range="msvc-140"

CLR 콘솔 응용 프로그램 템플릿을 사용 하 여 프로젝트를 만드는 경우 다음 참조 및 파일이 자동으로 추가 됩니다.

- 이러한.NET Framework 네임스페이스에 대한 참조:

  - <xref:System>, <xref:System.Data> , <xref:System.Xml> : 이러한 참조에는 일반적으로 사용 되는 형식, 이벤트, 인터페이스, 특성 및 예외를 정의 하는 기본 클래스가 포함 되어 있습니다.

  - *`mscorlib.dll`*: .NET Framework 개발을 지 원하는 어셈블리 DLL입니다.

- 소스 파일:

  - *`ConsoleApplicationName.cpp`*: 응용 프로그램에 대 한 주 소스 파일과 진입점입니다. 이 파일에는 프로젝트에 대해 지정한 기본 이름이 있습니다. 프로젝트 DLL 파일 및 프로젝트 네임 스페이스를 식별 합니다. 이 파일에 사용자 고유의 코드를 제공합니다.

  - *`AssemblyInfo.cpp`*: 프로젝트의 어셈블리 메타 데이터를 수정 하는 데 사용할 수 있는 특성 및 설정을 포함 합니다. 자세한 내용은 [어셈블리 콘텐츠](/dotnet/framework/app-domains/assembly-contents)를 참조 하세요.

  - *`stdafx.cpp`*: 라는 미리 컴파일된 헤더 파일과 *`ConsoleApplicationName.pch`* 이름이 인 미리 컴파일된 형식 파일을 빌드하는 데 사용 됩니다. *`stdafx.obj`*

- 헤더 파일:

  - *`stdafx.h`*: 라는 미리 컴파일된 헤더 파일과 *`ConsoleApplicationName.pch`* 이름이 인 미리 컴파일된 형식 파일을 빌드하는 데 사용 됩니다. *`stdafx.obj`*

  - *`resource.h`*:에 대해 생성 된 포함 파일 *`app.rc`* 입니다.

- 리소스 파일.

  - *`app.rc`*: 프로그램의 리소스 스크립트 파일입니다.

  - *`app.ico`*: 프로그램의 아이콘 파일입니다.

- *`ReadMe.txt`*: 프로젝트의 파일을 설명 합니다.

::: moniker-end
::: moniker range=">=msvc-150"

CLR 콘솔 응용 프로그램 템플릿을 사용 하 여 프로젝트를 만드는 경우 다음 참조 및 파일이 자동으로 추가 됩니다.

- 이러한.NET Framework 네임스페이스에 대한 참조:

  - <xref:System>, <xref:System.Data> , <xref:System.Xml> : 이러한 참조에는 일반적으로 사용 되는 형식, 이벤트, 인터페이스, 특성 및 예외를 정의 하는 기본 클래스가 포함 되어 있습니다.

  - *`mscorlib.dll`*: .NET Framework 개발을 지 원하는 어셈블리 DLL입니다.

- 소스 파일:

  - *`ConsoleApplicationName.cpp`*: 응용 프로그램에 대 한 주 소스 파일과 진입점입니다. 이 파일에는 프로젝트에 대해 지정한 기본 이름이 있습니다. 프로젝트 DLL 파일 및 프로젝트 네임 스페이스를 식별 합니다. 이 파일에 사용자 고유의 코드를 제공합니다.

  - *`AssemblyInfo.cpp`*: 프로젝트의 어셈블리 메타 데이터를 수정 하는 데 사용할 수 있는 특성 및 설정을 포함 합니다. 자세한 내용은 [어셈블리 콘텐츠](/dotnet/framework/app-domains/assembly-contents)를 참조 하세요.

  - *`pch.cpp`*: 라는 미리 컴파일된 헤더 파일과 *`ConsoleApplicationName.pch`* 이름이 인 미리 컴파일된 형식 파일을 빌드하는 데 사용 됩니다. *`pch.obj`*

- 헤더 파일:

  - *`pch.h`*: 라는 미리 컴파일된 헤더 파일과 *`ConsoleApplicationName.pch`* 이름이 인 미리 컴파일된 형식 파일을 빌드하는 데 사용 됩니다. *`pch.obj`*

  - *`Resource.h`*:에 대해 생성 된 포함 파일 *`app.rc`* 입니다.

- 리소스 파일.

  - *`app.rc`*: 프로그램의 리소스 스크립트 파일입니다.

  - *`app.ico`*: 프로그램의 아이콘 파일입니다.

::: moniker-end

## <a name="to-create-a-clr-console-app-project"></a>CLR 콘솔 응용 프로그램 프로젝트를 만들려면

::: moniker range="msvc-140"

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **설치** 된 > **템플릿** > **Visual C++** > **clr** 노드를 선택한 다음 **clr 콘솔 응용 프로그램** 템플릿을 선택 합니다.

1. **이름** 상자에 애플리케이션의 고유 이름을 입력합니다.

   다른 프로젝트 및 솔루션 설정을 지정할 수 있지만 필요 하지는 않습니다.

1. **확인** 단추를 선택 하 여 프로젝트 및 소스 파일을 생성 합니다.

::: moniker-end
::: moniker range="msvc-150"

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **설치** > **Visual C++** > **clr** 노드를 선택한 다음 **clr 콘솔 앱** 템플릿을 선택 합니다.

1. **이름** 상자에 애플리케이션의 고유 이름을 입력합니다.

   다른 프로젝트 및 솔루션 설정을 지정할 수 있지만 필요 하지는 않습니다.

1. **확인** 단추를 선택 하 여 프로젝트 및 소스 파일을 생성 합니다.

::: moniker-end
::: moniker range="msvc-160"

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트 만들기** 대화 상자에서 검색 상자에 "clr console"을 입력 합니다. **CLR 콘솔 앱 (.NET Framework)** 템플릿을 선택 하 고 **다음** 을 선택 합니다.

1. **이름** 상자에 애플리케이션의 고유 이름을 입력합니다.

   다른 프로젝트 및 솔루션 설정을 지정할 수 있지만 필요 하지는 않습니다.

1. **만들기** 단추를 선택 하 여 프로젝트 및 소스 파일을 생성 합니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[CLR 프로젝트](../build/reference/files-created-for-clr-projects.md)
