---
title: Visual Studio에 C11 및 C17 지원 설치
description: Visual Studio에 C11 및 C17에 대한 Windows SDK 및 CRT 지원 설치
ms.date: 09/11/2020
helpviewer_keywords:
- Install preview Windows SDK
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 9310b0dbb4e436245de820622ec9dd0f52292871
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924417"
---
# <a name="install-c11-and-c17-support-in-visual-studio"></a>Visual Studio에 C11 및 C17 지원 설치

::: moniker range="<=msvc-150"

C11 및 C17 표준을 지원하려면 Visual Studio 2019 버전 16.8 이상이 필요합니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end

::: moniker range="msvc-160"

C11 및 C17 표준은 Visual Studio 2019 버전 16.8부터 지원됩니다. 규격 전처리기([`/Zc:preprocessor`](../build/reference/zc-preprocessor.md))가 제대로 작동하려면 업데이트된 UCRT(유니버설 C 런타임) 및 최신 Windows SDK 업데이트가 필요합니다.

Windows SDK 릴리스는 Windows OS 릴리스와 일치합니다. 이러한 변경 내용이 포함된 Windows 릴리스가 없기 때문에 *Insider Preview Windows SDK* 가 필요합니다. 이것은 Windows 참가자가 현재 플라이트(테스트) 중인 Windows 빌드에 해당하는 미리 보기 버전의 Windows SDK입니다. Insider Preview Windows 10 SDK를 설치하면 최신 Windows SDK를 사용하도록 구성된 Visual Studio 프로젝트가 Insider Preview를 사용합니다.

## <a name="prerequisites"></a>사전 준비 사항

- Visual Studio 2019 버전 16.8 Preview 3 이상이 컴퓨터에 설치되어 실행되고 있습니다. 설치에서 C++를 사용한 데스크톱 개발 워크로드를 포함합니다. [Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/) 페이지에서 최신 미리 보기를 다운로드할 수 있습니다. Visual Studio가 아직 설치되지 않은 경우 설치 지침은 [Visual studio에 C++ 지원 설치](../build/vscpp-step-0-installation.md)를 참조하세요.

## <a name="step-1-sign-in-by-using-an-insider-microsoft-account"></a>1단계: Insider Microsoft 계정을 사용하여 로그인

누구나 무료 [Microsoft 계정](https://signup.live.com/)을 만든 다음 참가자 프로그램을 옵트인할 수 있습니다. [개발자용 Windows 참가자 프로그램](https://insider.windows.com/for-developers) 페이지로 이동하여 **등록** 을 선택하고 로그인합니다.

등록한 후에는 Windows 참가자 버전의 플라이팅을 시작하는 옵션이 제공됩니다. 이 단계는 Insider Windows 10 SDK를 다운로드하고 사용하는 데 필요하지 않습니다. Windows 참가자를 등록하는 경우 자동으로 새 Windows 플라이트를 다운로드하도록 옵트인하지 않습니다.

**Windows 참가자 프로그램 시작** 페이지가 열릴 때 **지금 플라이트** 를 선택할 필요가 없습니다. 다음 단계를 계속 진행하여 Insider Preview Windows 10 SDK를 다운로드합니다.

## <a name="step-2-download-the-insider-preview-windows-10-sdk"></a>2단계: Insider Preview Windows 10 SDK 다운로드

[Windows Insider Preview 다운로드](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) 페이지에서 Insider Preview Windows SDK를 설치할 수 있습니다. "Windows 참가자 프로그램의 구성원이어야 합니다."라는 메시지가 표시되면 로그인했는지 확인합니다. 참가자 프로그램에 사용한 것과 동일한 Microsoft 계정을 사용합니다. "요청한 페이지를 찾을 수 없습니다."라는 메시지가 표시되면 URL에서 로캘을 *en-us* 로 변경합니다.

참가자 페이지는 Windows 10 Insider Preview OS를 사용할 것을 요구합니다. 이는 Windows SDK에 포함된 일부 콘텐츠에만 적용됩니다. 이러한 콘텐츠는 이전 버전의 Windows에서 제공하지 않는 새 API에 따라 달라질 수 있습니다. 그러나 Windows 및 유니버설 C 런타임 헤더는 Insider OS 없이 설치하고 사용할 수 있습니다.

**SDK Insider Preview 가져오기 – 빌드 20211** (이상)을 선택하여 다운로드를 시작합니다. 이후 버전의 Windows SDK도 작동합니다.

## <a name="step-3-install-the-insider-preview-windows-10-sdk"></a>3단계: Insider Preview Windows 10 SDK 설치

Insider Preview Windows SDK를 *`.iso`* 파일로 다운로드합니다. 파일 탐색기에서 다운로드한 파일이 포함된 폴더를 엽니다. *`.iso`* 파일을 탑재한 다음 *`WinSDKSetup.exe`* 를 실행하여 설치를 시작합니다.

**위치 지정** 페이지에서 **이 컴퓨터에 Windows 소프트웨어 개발 키트 - \<version> 설치** 를 선택하고 **다음** 을 선택합니다. **Windows 키트 개인 정보** 페이지에서 Microsoft가 Windows 10 키트에 대한 정보를 수집할 수 있도록 허용할지 여부를 선택하고 **다음** 을 선택합니다. **수락** 을 선택하여 사용권 계약에 동의합니다. **설치할 기능 선택** 페이지에서 다음 기능만 선택합니다.  

- 데스크톱 앱용 Windows SDK 서명 도구

- UWP 관리 앱용 Windows SDK

- UWP C++ 앱용 Windows SDK

- 데스크톱 C++ x86 앱용 Windows SDK(x86용 앱을 빌드하려는 경우)

- 데스크톱 C++ amd64 앱용 Windows SDK(amd64용 앱을 빌드하려는 경우)

- 데스크톱 C++ arm 앱용 Windows SDK(arm용 앱을 빌드하려는 경우)

- 데스크톱 C++ arm64 앱용 Windows SDK(arm64용 앱을 빌드하려는 경우)

![설치하도록 선택한 구성 요소를 보여 주는 Windows SDK 설치 관리자의 스크린샷](media/c11-7-windows-sdk-installer-select-features.png)

**설치** 를 선택하여 선택한 SDK 구성 요소를 설치합니다. SDK는 설치하는 데 몇 분 정도 걸립니다. 완료되면 Visual Studio를 엽니다.

## <a name="step-4-configuring-c11-or-c17-mode-in-visual-studio"></a>4단계: Visual Studio에서 C11 또는 C17 모드 구성

Visual Studio에서 신규 또는 기존 C 프로젝트를 열고 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

Insider Preview Windows 10 SDK를 사용하도록 프로젝트를 설정합니다. **구성 속성** > **일반** 페이지에서 **Windows SDK 버전** 속성을 **10.0(설치된 최신 버전)** 또는 설치한 특정 미리 보기 버전으로 설정합니다.

또한 새 옵션 **C++ 언어 표준** 이 표시됩니다. 이 속성을 **ISO C11 표준(`/std:c11`)** 또는 **ISO C17(2018) 표준(`/std:c17`)** 으로 설정합니다.  

![구성 속성 일반 페이지의 속성 페이지 대화 상자에서 ISO C 17이 선택된 C 언어 표준 속성 드롭다운을 보여 주는 스크린샷](media/c11-9-project-property-page-c-language-standard.png)

C++ 언어 표준 버전은 언어가 C++일 때 사용됩니다. 파일 확장명이 *`.cpp`* 일 경우 기본값입니다. C 언어 표준 버전은 언어가 C일 때 사용됩니다. 파일 확장명이 *`.c`* 일 경우 기본값입니다. C11 또는 C17을 사용하여 빌드하려면 소스 코드를 *`.c`* 파일에 배치하거나 C로 컴파일하도록 코드를 설정합니다. **구성 속성** > **C/C++**  > **고급** 페이지에서 프로젝트에 이 속성을 설정할 수 있습니다. **컴파일 옵션** 속성을 **C 코드로 컴파일(/TC)** 로 설정합니다.

축하합니다. Visual Studio 2019 버전 16.8 미리 보기 3에서 C11 및 C17 코드를 작성하는 데 필요한 모든 설정을 마쳤습니다.

## <a name="see-also"></a>추가 정보

[`/std`(언어 표준 버전 지정)](../build/reference/std-specify-language-standard-version.md)

::: moniker-end
