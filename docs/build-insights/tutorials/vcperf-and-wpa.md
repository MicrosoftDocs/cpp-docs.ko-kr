---
title: '자습서: vcperf 및 Windows Performance Analyzer'
description: C++ 빌드 추적을 분석하는 데 vcperf 및 WPA를 사용하는 방법에 대한 자습서입니다.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b82c1f7105b3fd03d8c21dd79617dbc66f3e090c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507779"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>자습서: vcperf 및 Windows Performance Analyzer

::: moniker range="<=vs-2017"

C++ Build Insights 도구는 Visual Studio 2019에서 사용할 수 있습니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range="vs-2019"

이 자습서에서는 *vcperf.exe*를 사용하여 C++ 빌드의 추적을 수집하는 방법을 알아봅니다. Windows Performance Analyzer에서 이 추적을 보는 방법도 알아봅니다.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>1단계: Windows Performance Analyzer 설치 및 구성

WPA는 Windows ADK(평가 및 배포 키트)에서 사용할 수 있는 추적 뷰어입니다. Visual Studio 설치 관리자를 사용하여 설치할 수 있는 구성 요소에 속하지 않는 별도의 유틸리티입니다.

C++ Build Insights를 지원하는 WPA 버전은 현재 Windows ADK Insider Preview에서만 사용할 수 있습니다. 이 미리 보기에 액세스하려면 [Windows 참가자 프로그램](https://insider.windows.com)에 등록해야 합니다. Windows ADK 미리 보기를 얻기 위해 Windows 10 Insider Preview 운영 체제를 설치할 필요는 없습니다. Windows 참가자 프로그램에 Microsoft 계정을 등록하기만 하면 됩니다.

### <a name="to-download-and-install-wpa"></a>WPA를 다운로드하고 설치하려면

참고:  Windows Performance Analyzer를 설치하려면 Windows 8 이상이 필요합니다.

1. Windows ADK [다운로드 페이지](/windows-hardware/get-started/adk-install)로 이동합니다.

1. 최신 버전의 Windows ADK를 다운로드하고 설치합니다.

1. 설치하려는 기능에 대한 메시지가 표시되면 **Windows Performance Toolkit**를 선택합니다. 원하는 경우 다른 기능을 선택할 수 있지만 WPA 설치에는 필요하지 않습니다.

   ![Windows Performance Analyzer 설치 관리자의 기능 선택 화면](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a> WPA를 구성하려면

WPA에서 C++ Build Insights 추적을 보려면 특수한 추가 기능이 필요합니다. 다음 단계를 따라 설치하세요.

1. 아래 구성 요소 중 하나를 다운로드하여 추가 기능을 가져옵니다. 둘 다 가져올 필요는 없습니다. 가장 편리한 구성 요소 하나를 선택합니다.
    1. [Visual Studio 2019 버전 16.6 이상](https://visualstudio.microsoft.com/downloads/) 또는
    1. [C++ Build Insights NuGet 패키지](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/).

1. `perf_msvcbuildinsights.dll` 파일을 WPA 설치 디렉터리에 복사합니다.
    1. Visual Studio 2019 버전 16.6 이상에서 이 파일은 `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}`에 있습니다.
    1. C++ Build Insights NuGet 패키지에서 이 파일은 `wpa\{Architecture}`에 있습니다.
    1. 위의 경로에서 다음과 같이 중괄호로 묶은 변수를 바꿉니다.
        1. `{Edition}`은 Community, Professional 또는 Enterprise 등 Visual Studio 2019 버전입니다.
        1. `{Version}`은 MSVC 버전입니다. 사용 가능한 가장 높은 항목을 선택합니다.
        1. `{Architecture}`: 64비트 버전의 Windows가 있는 경우 `x64`를 선택합니다. 그렇지 않은 경우 `x86`을 선택합니다.
    1. WPA 설치 디렉터리는 일반적으로 `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit`입니다.

1. WPA 설치 디렉터리에서 `perfcore.ini` 파일을 열고 `perf_msvcbuildinsights.dll` 항목을 추가합니다.

## <a name="step-2-trace-your-build-with-vcperfexe"></a>2단계: vcperf.exe를 사용하여 빌드 추적

C++ Build Insights 데이터를 보려면 먼저 다음 단계에 따라 추적 파일에 수집합니다.

1. 관리자 모드에서 VS 2019 **x64** 또는 **x86 Native Tools 명령 프롬프트**를 엽니다. (시작 메뉴 항목을 마우스 오른쪽 단추로 클릭하고 **더 보기** > **관리자 권한으로 실행**을 선택합니다.)
    1. 64비트 버전의 Windows가 있는 경우 **x64**를 선택합니다. 그렇지 않은 경우 **x86**을 선택합니다.

1. 명령 프롬프트 창에 다음 명령을 입력합니다.

   **vcperf.exe /start _SessionName_**

   *SessionName*으로 기억할 세션 이름을 선택합니다.

1. 일반적인 방법으로 프로젝트를 빌드합니다. 동일한 명령 프롬프트 창을 사용하여 빌드할 필요는 없습니다.

1. 명령 프롬프트 창에 다음 명령을 입력합니다.

   **vcperf.exe /stop _SessionName_ _traceFile.etl_**

   이전에 *SessionName*으로 선택한 것과 동일한 세션 이름을 사용합니다. *traceFile.etl* 추적 파일로 적절한 이름을 선택합니다.

개발자 명령 프롬프트 창에서 일반적인 *vcperf.exe* 명령 시퀀스는 다음과 같습니다.

![간단한 vcperf.exe 사용 시나리오](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>vcperf.exe에 대한 중요 참고 사항

- *vcperf.exe* 추적을 시작하거나 중지하려면 관리자 권한이 필요합니다. **관리자 권한으로 실행**을 사용해서 연 개발자 명령 프롬프트 창을 사용하세요.

- 한 번에 하나의 추적 세션만 컴퓨터에서 실행할 수 있습니다.

- 추적을 시작하는 데 사용한 세션 이름을 기억해야 합니다. 이름을 모르면 실행 중인 세션을 중지할 때 문제가 생길 수 있습니다.

- *cl.exe* 및 *link.exe*와 마찬가지로 명령줄 유틸리티 *vcperf.exe*는 MSVC 설치에 포함되어 있습니다. 이 구성 요소를 얻는 데 필요한 추가 단계는 없습니다.

- *vcperf.exe*는 시스템에서 실행되는 모든 MSVC 도구에 대한 정보를 수집합니다. 따라서 추적을 수집하는 데 사용한 것과 동일한 명령 프롬프트에서 빌드를 시작할 필요가 없습니다. 다른 명령 프롬프트 또는 Visual Studio에서도 프로젝트를 빌드할 수 있습니다.

### <a name="vcperfexe-is-open-source"></a>vcperf.exe는 오픈 소스

자체 버전의 *vcperf.exe*를 빌드하고 실행하려면 [vcperf GitHub 리포지토리](https://github.com/microsoft/vcperf)에서 얼마든지 복제할 수 있습니다.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>3단계: Windows Performance Analyzer에서 추적 보기

WPA를 시작하고 방금 수집한 추적을 엽니다. WPA는 이 추적을 C++ Build Insights 추적으로 인식해야 하며, 왼쪽의 Graph 탐색기 패널에 다음 보기가 표시되어야 합니다.

- 빌드 탐색기
- 파일
- 함수
- 템플릿 인스턴스화

이러한 보기가 표시되지 않는 경우 [1단계](#configuration-steps)에 설명된 대로 WPA가 올바르게 구성되어 있는지 다시 확인합니다. 다음과 같이 보기를 오른쪽의 빈 분석 창으로 끌어서 빌드 데이터를 볼 수 있습니다.

![Windows Performance Analyzer에서 C++ Build Insights 추적 보기](media/wpa-viewing-trace.gif)

Graph 탐색기에서 다른 보기도 사용할 수 있습니다. 포함된 정보에 관심이 있는 경우 분석 창으로 끌어 놓습니다. 유용한 보기는 빌드 전체의 CPU 사용률을 보여 주는 CPU(샘플링됨) 보기입니다.

## <a name="more-information"></a>추가 정보

[자습서: Windows Performance Analyzer 기본 사항](wpa-basics.md)\
빌드 추적을 분석하는 데 도움이 되는 일반적인 WPA 작업에 대해 알아봅니다.

[참조: vcperf 명령](../reference/vcperf-commands.md)\
*vcperf.exe* 명령 참조는 사용 가능한 모든 명령 옵션을 나열합니다.

[참조: Windows Performance Analyzer 보기](../reference/wpa-views.md)\
WPA의 C++ Build Insights 보기에 대한 자세한 내용은 이 문서를 참조하세요.

[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)\
공식 WPA 설명서 사이트입니다.

::: moniker-end
