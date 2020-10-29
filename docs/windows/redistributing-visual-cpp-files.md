---
title: Visual C++ 파일 재배포
description: Visual Studio에는 앱과 함께 배포할 수 있는 재배포 가능 라이브러리 및 구성 요소가 포함 되어 있습니다.
ms.date: 07/16/2020
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: a660e67b2664417438ea9fa7acddbde4c20c307a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924139"
---
# <a name="redistributing-visual-c-files"></a>Visual C++ 파일 재배포

> [!NOTE]
> Visual C++ 런타임 파일 중 하나의 다운로드를 찾고 있나요? [Microsoft 웹 사이트로](https://www.microsoft.com/) 이동 하 고 검색 상자에 **Visual C++ 재배포 가능 패키지** 를 입력 합니다. 컴퓨터 아키텍처(예: 64비트 Windows를 실행하는 경우 x64) 및 필요한 Visual C++ 버전(예: 2015)의 재배포 가능 패키지를 다운로드하여 설치합니다.

## <a name="redistributable-files-and-licensing"></a>재배포 가능 파일 및 라이선스

애플리케이션을 배포할 때 이 애플리케이션을 지원하는 데 필요한 파일도 배포해야 합니다. Microsoft에서 이러한 파일을 제공 하는 경우 재배포할 수 있는지 여부를 확인 합니다. IDE에서 Visual Studio 사용 조건에 대 한 링크를 찾을 수 있습니다. 정보 Microsoft Visual Studio 대화 상자의 사용 조건 링크를 사용 합니다. 또는 Visual Studio [라이선스 디렉터리](https://visualstudio.microsoft.com/license-terms/)에서 관련 eula 및 라이선스를 다운로드 합니다.

::: moniker range="msvc-160"

Visual Studio 2019 Microsoft 소프트웨어 사용 조건의 "배포 가능 코드" 섹션에서 참조 하는 "REDIST 목록"을 보려면 [Microsoft Visual Studio 2019 용 배포 가능 코드 파일](/visualstudio/releases/2019/redistribution#-distributable-code-files-for-visual-studio-2019) 을 참조 하세요.

::: moniker-end

::: moniker range="msvc-150"

Visual Studio 2017 Microsoft 소프트웨어 사용 조건의 "배포 가능 코드" 섹션에서 참조 하는 "REDIST 목록"을 보려면 [Microsoft Visual Studio 2017 용 배포 가능 코드 파일](/visualstudio/productinfo/2017-redistribution-vs#-distributable-code-files-for-visual-studio-2017)을 참조 하세요.

::: moniker-end

::: moniker range="msvc-140"

Visual Studio 2015 Microsoft 소프트웨어 사용 조건의 "배포 가능 코드" 섹션에서 참조 하는 "REDIST 목록"을 보려면 [Microsoft Visual Studio 2015 용 배포 가능 코드 파일](/visualstudio/productinfo/2015-redistribution-vs#-distributable-code-files-for-visual-studio-2015)을 참조 하세요.

::: moniker-end

재배포 가능 파일에 대 한 자세한 내용은 [재배포할 Dll 확인](determining-which-dlls-to-redistribute.md) 및 [배포 예제](deployment-examples.md)를 참조 하세요.

## <a name="locate-the-redistributable-files"></a>재배포 가능 파일 찾기

재배포 가능 파일을 배포 하려면 Visual Studio에 설치 된 재배포 가능 패키지를 사용할 수 있습니다. 2017 이후의 Visual Studio 버전에서 이러한 파일의 이름은 *`vc_redist.arm64.exe`* , *`vc_redist.x64.exe`* 및 *`vc_redist.x86.exe`* 입니다. Visual Studio 2015, Visual Studio 2017 및 Visual Studio 2019에서는 이름 *`vcredist_x86.exe`* , *`vcredist_x64.exe`* 및 *`vcredist_arm.exe`* (2015만 해당) 에서도 사용할 수 있습니다.

재배포 가능 파일을 찾는 가장 쉬운 방법은 개발자 명령 프롬프트에서 설정 된 환경 변수를 사용 하는 것입니다. 최신 버전의 Visual Studio 2019에서는 재배포 가능 파일을 폴더에 찾을 수 있습니다 *`%VCINSTALLDIR%Redist\MSVC\v142`* . Visual Studio 2017 및 Visual Studio 2019에서 모두에도 있습니다 *`%VCToolsRedistDir%`* . Visual Studio 2015에서 이러한 파일은에서 찾을 수 있습니다 *`%VCINSTALLDIR%redist\<locale>`* . 여기서 *`<locale>`* 는 재배포 가능 패키지의 로캘입니다.

다른 배포 옵션은 재배포 가능 병합 모듈 (파일)을 사용 하는 것입니다 *`.msm`* . Visual Studio 2019에서 이러한 파일은 Visual Studio 설치 관리자에서 **c + + 2019 재배포 가능 MSMs** 라는 선택적 설치 가능 구성 요소의 일부입니다. 병합 모듈은 Visual Studio 2017 및 Visual Studio 2015에서 c + + 설치의 일부로 기본적으로 설치 됩니다. 최신 버전의 Visual Studio 2019에 설치 된 경우에서 재배포 가능 병합 모듈을 찾을 수 있습니다 *`%VCINSTALLDIR%Redist\MSVC\v142\MergeModules`* . Visual Studio 2019 및 Visual Studio 2017에서 모두에도 있습니다 *`%VCToolsRedistDir%MergeModules`* . Visual Studio 2015에서는에서 찾을 수 있습니다 *`Program Files [(x86)]\Common Files\Merge Modules`* .

## <a name="install-the-redistributable-packages"></a>재배포 가능 패키지 설치

Visual C++ 재배포 가능 패키지는 모든 Visual C++ 라이브러리를 설치하고 등록합니다. 하나를 사용 하는 경우 응용 프로그램을 설치 하기 전에 대상 시스템의 필수 구성 요소로 실행 합니다. Visual C++ 라이브러리의 자동 업데이트를 사용하기 때문에 이러한 배포 패키지를 사용하는 것이 좋습니다. 이러한 패키지를 사용하는 방법에 대한 예제는 [연습: Visual C++ 재배포 가능 패키지를 사용하여 Visual C++ 애플리케이션 배포](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)를 참조하세요.

각 Visual C++ 재배포 가능 패키지는 컴퓨터에 최신 버전이 있는지 여부를 확인합니다. 최신 버전이 있는 경우 패키지가 설치 되지 않습니다. Visual Studio 2015부터 재배포 가능 패키지에 설치 실패를 알리는 오류 메시지가 표시됩니다. 플래그를 사용 하 여 패키지를 실행 하는 경우 **`/quiet`** 오류 메시지가 표시 되지 않습니다. 어떤 경우든 오류가 Microsoft Installer에 기록되며, 오류 결과가 호출자에게 반환됩니다. Visual Studio 2015 패키지부터 레지스트리를 검사하여 최신 버전이 설치되어 있는지 확인함으로써 이 오류를 방지할 수 있습니다. 현재 설치 된 버전 번호는 키에 저장 됩니다 `HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\14.0\VC\Runtimes\{x86|x64|ARM}` . 최신 재배포 가능 요소가 2015 버전과 호환 되므로 버전 번호는 Visual Studio 2015, Visual Studio 2017 및 Visual Studio 2019에 14.0입니다. 키는 `ARM` `x86` `x64` 플랫폼에 대해 설치 된 vcredist 버전에 따라, 또는입니다. ( `Wow6432Node` X64 플랫폼에서 설치 된 x86 패키지의 버전을 확인 하는 데 Regedit를 사용 하는 경우에만 하위 키를 확인 해야 합니다.) 버전 번호는 REG_SZ 문자열 값에 저장 되 **`Version`** 고 **`Major`** ,, **`Minor`** **`Bld`** 및 **`Rbld`** `REG_DWORD` 값 집합에도 저장 됩니다. 설치 시 오류를 방지하려면 현재 설치된 버전이 최신 버전인 경우 재배포 가능 패키지 설치를 건너뛰어야 합니다.

## <a name="install-the-redistributable-merge-modules"></a>재배포 가능 병합 모듈 설치

재배포 가능 병합 모듈은 응용 프로그램을 배포 하는 데 사용 하는 Windows Installer 패키지 (또는 유사한 설치 패키지)에 포함 되어야 합니다. 자세한 내용은 [병합 모듈을 사용하여 재배포](redistributing-components-by-using-merge-modules.md)를 참조하세요. 예제는 [연습: 설치 프로젝트를 사용 하 여 Visual C++ 응용 프로그램 배포](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)를 참조 하세요.

## <a name="install-individual-redistributable-files"></a>개별 재배포 가능 파일 설치

재배포 가능 Dll을 *응용 프로그램 로컬 폴더* 에 직접 설치할 수도 있습니다. 실행 응용 프로그램 파일이 포함 된 폴더입니다. 서비스 상의 이유로이 설치 위치를 사용 하지 않는 것이 좋습니다.

## <a name="potential-run-time-errors"></a>잠재적 런타임 오류

Windows에서 응용 프로그램에 필요한 재배포 가능 라이브러리 Dll 중 하나를 찾을 수 없는 경우 다음과 유사한 메시지가 표시 될 수 있습니다. " *라이브러리* .dll을 찾을 수 없기 때문에이 응용 프로그램을 시작 하지 못했습니다. 응용 프로그램을 다시 설치 하면이 문제가 해결 될 수 있습니다. "

이러한 종류의 오류를 해결 하려면 응용 프로그램 설치 관리자가 올바르게 빌드되는지 확인 합니다. 재배포 가능 라이브러리가 대상 시스템에 올바르게 배포 되었는지 확인 합니다. 자세한 내용은 [Visual C++ 애플리케이션의 종속성 이해](understanding-the-dependencies-of-a-visual-cpp-application.md)를 참조하세요.

## <a name="related-articles"></a>관련 문서

[병합 모듈을 사용 하 여 재배포](redistributing-components-by-using-merge-modules.md)\
Visual C++ 재배포 가능 병합 모듈을 사용 하 여 Visual C++ 런타임 라이브러리를 폴더에 공유 Dll로 설치 하는 방법을 설명 합니다 *`%windir%\system32\`* .

[ActiveX 컨트롤 Visual C++ 재배포](redistributing-visual-cpp-activex-controls.md)\
ActiveX 컨트롤을 사용하는 애플리케이션을 재배포하는 방법에 대해 설명합니다.

[MFC 라이브러리 재배포](redistributing-the-mfc-library.md)\
MFC를 사용하는 애플리케이션을 재배포하는 방법에 대해 설명합니다.

[ATL 응용 프로그램 재배포](redistributing-an-atl-application.md)\
ATL을 사용하는 애플리케이션을 재배포하는 방법에 대해 설명합니다. Visual Studio 2012부터 ATL에 대한 재배포 가능 라이브러리가 필요하지 않습니다.

[배포 예제](deployment-examples.md)\
Visual C++ 애플리케이션을 배포하는 방법을 보여 주는 예제에 대한 링크입니다.

[데스크톱 응용 프로그램 배포](deploying-native-desktop-applications-visual-cpp.md)\
Visual C++ 배포 개념과 기술을 소개합니다.
