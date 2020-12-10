---
title: C++/CLI를 사용한 .NET 프로그래밍
description: C + +/CLI를 사용 하 여 Visual Studio에서 .NET 앱 및 구성 요소를 만드는 방법에 대해 알아봅니다.
ms.date: 12/08/2020
helpviewer_keywords:
- programming [C++], .NET programming
- .NET Framework [C++]
- .NET applications [C++]
- Visual C++, .NET programming
ms.openlocfilehash: 80a9743016976e307158608134155dc7272d44a8
ms.sourcegitcommit: 754df5278f795f661d4eeb0d4cacc908aa630159
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933185"
---
# <a name="net-programming-with-ccli"></a>C++/CLI를 사용한 .NET 프로그래밍

::: moniker range="msvc-140"

기본적으로 Visual Studio 2015를 사용하여 만든 CLR 프로젝트는 .NET Framework 4.5.2를 대상으로 합니다. 새 프로젝트를 만들 때 .NET Framework 4.6를 대상으로 지정할 수 있습니다. **새 프로젝트** 대화 상자의 대화 상자 위쪽 가운데에 있는 드롭다운에서 대상 프레임 워크를 변경 합니다. 기존 프로젝트에 대 한 대상 프레임 워크를 변경 하려면 프로젝트를 닫고 프로젝트 파일 ()을 편집한 *`.vcxproj`* 다음 대상 프레임 워크 버전의 값을 4.6로 변경 합니다. 변경 내용은 다음에 프로젝트를 열 때 적용 됩니다.

::: moniker-end
::: moniker range="msvc-150"

Visual Studio 2017에서 기본 대상 .NET Framework는 4.6.1입니다. 프레임 워크 버전 선택기는 **새 프로젝트** 대화 상자 아래쪽에 있습니다.

## <a name="install-ccli-support-in-visual-studio-2017"></a>Visual Studio 2017에서 c + +/CLI 지원 설치

C + +/CLI 자체는 Visual Studio c + + 워크 로드를 설치할 때 기본적으로 설치 되지 않습니다. Visual Studio를 설치한 후에 구성 요소를 설치 하려면 Visual Studio 설치 관리자를 엽니다. 설치 된 Visual Studio 버전 옆에 있는 **수정** 단추를 선택 합니다. **설치 된 구성 요소** 탭을 선택 합니다. **컴파일러, 빌드 도구 및 런타임** 섹션까지 아래로 스크롤하고 **c + +/cli 지원** 을 선택 합니다. **수정** 을 선택 하 여 Visual Studio를 업데이트 합니다.

::: moniker-end
::: moniker range="msvc-160"

Visual Studio 2019에서 .NET Core 프로젝트에 대 한 기본 대상 프레임 워크는 5.0입니다. .NET Framework 프로젝트의 경우 기본값은 4.7.2입니다. .NET Framework 버전 선택기는 **새 프로젝트 만들기** 대화 상자의 **새 프로젝트 구성** 페이지에 있습니다.
## <a name="install-ccli-support-in-visual-studio-2019"></a>Visual Studio 2019에서 c + +/CLI 지원 설치

C + +/CLI 자체는 Visual Studio c + + 워크 로드를 설치할 때 기본적으로 설치 되지 않습니다. Visual Studio를 설치한 후에 구성 요소를 설치 하려면 Visual Studio 설치 관리자를 엽니다. 설치 된 Visual Studio 버전 옆에 있는 **수정** 단추를 선택 합니다. **설치 된 구성 요소** 탭을 선택 합니다. **컴파일러, 빌드 도구 및 런타임** 섹션까지 아래로 스크롤하고 **v142 빌드 도구 구성 요소에 대 한 최신 c + +/cli 지원** 을 선택 합니다. **수정** 을 선택 하 여 Visual Studio를 업데이트 합니다.

::: moniker-end

## <a name="in-this-section"></a>섹션 내용

[C++/CLI 작업](../dotnet/cpp-cli-tasks.md)

[네이티브 및 .NET 상호 운용성](../dotnet/native-and-dotnet-interoperability.md)

[순수형 및 안정형 코드 (c + +/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)

[정규식 (c + +/CLI)](../dotnet/regular-expressions-cpp-cli.md)

[파일 처리 및 i/o (c + +/CLI)](../dotnet/file-handling-and-i-o-cpp-cli.md)

[그래픽 작업 (c + +/CLI)](../dotnet/graphics-operations-cpp-cli.md)

[Windows 작업 (c + +/CLI)](../dotnet/windows-operations-cpp-cli.md)

[ADO.NET를 사용 하 여 데이터 액세스 (c + +/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)

[다른 .NET 언어와의 상호 운용성 (c + +/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)

[Serialization(C++/CLI)](../dotnet/serialization-cpp-cli.md)

[관리 되는 형식 (c + +/CLI)](../dotnet/managed-types-cpp-cli.md)

[리플렉션(C++/CLI)](../dotnet/reflection-cpp-cli.md)

[강력한 이름 어셈블리 (어셈블리 서명) (c + +/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)

[Debug 클래스 (c + +/CLI)](../dotnet/debug-class-cpp-cli.md)

[STL/CLR 라이브러리 참조](../dotnet/stl-clr-library-reference.md)

[C++ 지원 라이브러리](../dotnet/cpp-support-library.md)

[C++/CLI의 예외](../dotnet/exceptions-in-cpp-cli.md)

[Boxing(C++/CLI)](../dotnet/boxing-cpp-cli.md)

## <a name="see-also"></a>참고 항목

[네이티브 및 .NET 상호 운용성](../dotnet/native-and-dotnet-interoperability.md)
