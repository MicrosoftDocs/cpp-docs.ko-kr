---
description: '자세한 정보: 재배포할 Dll 확인'
title: 재배포할 DLL 확인
ms.date: 07/15/2019
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: 016351a6d204c71cfef516862c9b57bebafcc1a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329401"
---
# <a name="determining-which-dlls-to-redistribute"></a>재배포할 DLL 확인

Visual Studio에서 제공하는 라이브러리 DLL을 사용하는 애플리케이션을 빌드할 때, 애플리케이션 사용자는 해당 DLL을 컴퓨터에 설치해야 애플리케이션을 실행할 수 있습니다. 대부분의 사용자는 Visual Studio가 설치되어 있지 않기 때문에 이러한 DLL을 제공해야 합니다. Visual Studio는 이러한 DLL을 애플리케이션 설치 관리자에 포함할 수 있는 *재배포 가능 파일* 로 사용할 수 있도록 해줍니다.

재배포 가능 DLL을 설치 관리자에 보다 쉽게 포함하려면, 독립 실행형 *재배포 가능 패키지* 를 사용하면 됩니다. 이들은 중앙 배포를 사용하여 사용자의 컴퓨터에 재배포 가능 파일을 설치하는 아키텍처별 실행 파일입니다. 예를 들어 vcredist \_x86.exe는 x86 및 x64 컴퓨터 모두에 대해 32 비트 라이브러리를 설치 하 \_ 고, vcredistx64.exe x64 컴퓨터용 64 비트 라이브러리를 설치 하며, VCREDIST \_ARM.exe ARM 컴퓨터용 라이브러리를 설치 합니다. Microsoft는 Windows 업데이트 서비스를 사용하여 이러한 라이브러리를 독립적으로 업데이트할 수 있으므로 중앙 배포를 권장합니다. Visual Studio 설치의 복사본 외에도 현재 재배포 가능 패키지는 다운로드할 수 있습니다. 현재 및 이전 버전의 도구 집합에 지원되는 최신 재배포 가능 패키지에 대한 연결은 [지원되는 최신 Visual C++ 다운로드](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)를 참조하세요. 특정한 이전 버전의 재배포 가능 패키지는 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=158431)에서 "Visual C++ 재배포 가능 패키지"를 검색하면 찾을 수 있습니다.

배포할 재배포 가능 패키지의 주 버전 번호는 애플리케이션을 만드는 데 사용되는 Visual Studio 도구 집합의 버전과 일치해야 하며, 부 버전은 동일 버전 이상이어야 합니다. Visual Studio 2017 및 Visual Studio 2015 간에 호환되는 도구 집합 버전 번호가 있습니다. 즉, Visual Studio 2017 재배포 가능 파일은 2015 도구 집합을 사용하여 빌드된 앱에서 사용할 수 있습니다. 이러한 파일은 호환될 수 있지만, 2017 도구 집합을 사용하여 빌드된 앱에서는 2015 재배포 가능 파일을 사용할 수 없습니다. 도구 집합 버전과 동일하거나 최신 버전의 재배포 가능 패키지만 사용할 수 있습니다.

설치 관리자에 재배포 가능 DLL을 포함하는 또 다른 방법은 *병합 모듈* 을 사용하는 것입니다. 이러한 Microsoft Installer 모듈은 애플리케이션 설치 관리자에 포함되어 설치됩니다. 재배포 가능 Dll에 대 한 병합 모듈은 Visual Studio 설치 디렉터리의 \\ VC \\ Redist\MSVC \\ *version* \\ MergeModules 아래에 있습니다 \\ . 이전 버전의 Visual Studio에서 이러한 파일은 \\Program Files 또는 \\Program Files(x86) 디렉터리의 Common Files\\Merge Module 하위 디렉터리에 있습니다. 이러한 파일의 사용에 대한 자세한 내용은 [병합 모듈을 사용하여 구성 요소 재배포](redistributing-components-by-using-merge-modules.md)를 참조하세요.

재배포 가능한 개별 DLL도 Visual Studio 설치에 포함됩니다. 기본적으로, Visual Studio 설치 디렉터리의 \\VC\\Redist\\MSVC\\*version* 폴더에 설치됩니다. *version* 번호는 재배포 가능 파일의 단일 공통 집합의 다른 부 빌드 번호를 나타낼 수 있습니다. 이러한 디렉터리에 있는 라이브러리 DLL 파일, 재배포 가능 패키지 또는 병합 모듈의 최신 버전을 사용합니다. 이러한 라이브러리를 애플리케이션과 동일한 디렉터리에 설치하여 로컬 배포에 사용할 수 있습니다. 로컬 배포는 배포된 애플리케이션에 업데이트를 제공하는 역할을 해야 하므로 권장하지 않습니다. 재배포 가능 패키지를 사용하여 중앙 배포하는 것이 좋습니다.

애플리케이션과 함께 다시 배포해야 하는 DLL을 결정하려면 애플리케이션에서 사용되는 DLL 목록을 수집합니다. 이러한 입력은 일반적으로 링커에 대한 가져오기 라이브러리 입력으로 나열됩니다. vcruntime 및 UCRT(유니버설 C 런타임 라이브러리)와 같은 특정 라이브러리가 기본적으로 포함됩니다. 앱 또는 해당 종속성 중 하나가 LoadLibrary를 사용하여 DLL을 동적으로 로드하는 경우, 해당 DLL이 링커에 대한 입력에 나열되지 않을 수 있습니다. 동적으로 로드된 DLL 목록을 수집하는 한 가지 방법은 [Visual C++ 애플리케이션의 종속성 이해](understanding-the-dependencies-of-a-visual-cpp-application.md)에 설명된 대로 앱에서 Dependency Walker(depends.exe)를 실행하는 것입니다. 그러나 이 도구는 오래되어 특정 DLL을 찾을 수 없다고 보고할 수 있습니다.

종속성 목록이 있는 경우 Microsoft Visual Studio 설치 디렉터리에 있는 Redist.txt 파일에 연결된 목록 또는 Visual Studio 복사본에 대한 Microsoft 소프트웨어 사용 조건의 "배포 가능 코드 파일" 섹션에서 참조된 재배포 가능 DLL의 "REDIST 목록"과 비교합니다. Visual Studio 2017의 경우 [Microsoft Visual Studio 2017용 배포 가능 코드(유틸리티, 확장성 및 BuildServer 파일 포함)](/visualstudio/productinfo/2017-redistribution-vs)를 참조하세요. Visual Studio 2015의 경우 [Microsoft Visual Studio 2015 및 Microsoft Visual Studio 2015 SDK용 배포 가능 코드(유틸리티 및 BuildServer 파일 포함)](/visualstudio/productinfo/2015-redistribution-vs)를 참조하세요. Visual Studio 2013의 경우 [Microsoft Visual Studio 2013 및 Microsoft Visual Studio 2013 SDK용 배포 가능 코드](/visualstudio/productinfo/2013-redistribution-vs)에서 온라인으로 목록을 확인할 수 있습니다.

Visual Studio 2015 이전 버전의 Visual Studio에서는 CRT(C 런타임 라이브러리)가 msvc *version*.dll에 재배포 가능 DLL로 포함되어 있습니다. Visual Studio 2015부터 CRT의 함수가 vcruntime 및 UCRT로 리팩터링되었습니다. UCRT는 이제 Windows 10에서 Windows 업데이트로 관리되는 시스템 구성 요소입니다. 모든 Windows 10 운영 체제에서 사용할 수 있습니다. 이전 운영 체제에 애플리케이션을 배포하려면, UCRT도 재배포해야 할 수 있습니다. UCRT의 초기 버전은 Windows 10 이전의 운영 체제에만 설치되는 Visual Studio 재배포 가능 파일에 포함되어 있으며, UCRT의 버전이 이미 설치되어 있지 않은 경우에만 해당됩니다. Microsoft 시스템 업데이트 패키지 형태의 하위 시스템용 UCRT의 설치 가능한 버전은 Microsoft 다운로드 센터에서 [Windows 10 유니버설 C 런타임](https://www.microsoft.com/download/details.aspx?id=48234)을 참조하세요.

Visual Studio에 포함된 모든 파일을 다시 배포할 수는 없습니다. Redist.txt 또는 온라인 "REDIST 목록"에 지정된 파일만 다시 배포할 수 있습니다. 디버그 버전의 애플리케이션 및 다양한 Visual C++ 디버그 DLL은 다시 배포할 수 없습니다. 자세한 내용은 [배포 방법 선택](choosing-a-deployment-method.md)을 참조하세요.

다음 표에서는 애플리케이션에서 사용될 수 있는 일부 Visual C++ DLL에 대해 설명합니다.

|Visual C++ 라이브러리|설명|적용 대상|
|--------------------------|-----------------|----------------|
|vcruntime *버전*.dll|네이티브 코드용 런타임 라이브러리.|일반 C 및 C++ 언어 시작 및 종료 서비스를 사용하는 애플리케이션.|
|vccorlib *version*.dll|관리 코드용 런타임 라이브러리.|관리 코드에 C++ 언어 서비스를 사용하는 애플리케이션.|
|msvcp *version*.dll 및 msvcp *version* _ *dotnumber*.dll|네이티브 코드용 C++ 표준 라이브러리.|[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)를 사용하는 애플리케이션.|
|concrt *version*.dll|네이티브 코드용 동시성 런타임 라이브러리.|[동시성 런타임](../parallel/concrt/concurrency-runtime.md)을 사용하는 애플리케이션.|
|mfc *version*.dll|MFC(Microsoft Foundation Class) 라이브러리|[MFC 라이브러리](../mfc/mfc-desktop-applications.md)를 사용하는 애플리케이션.|
|mfc *version* *language*.dll|MFC(Microsoft Foundation Classes) 라이브러리 리소스.|MFC에 특정 언어 리소스를 사용하는 애플리케이션.|
|mfc *version* u.dll|유니코드를 지원하는 MFC 라이브러리|[MFC 라이브러리](../mfc/mfc-desktop-applications.md)를 사용하고 유니코드 지원이 필요한 애플리케이션.|
|mfcmifc80.dll|MFC 관리되는 인터페이스 라이브러리|[Windows Forms 컨트롤](/dotnet/framework/winforms/controls/index)과 함께 [MFC 라이브러리](../mfc/mfc-desktop-applications.md)를 사용하는 애플리케이션.|
|mfcm *version*.dll|MFC 관리되는 라이브러리|[Windows Forms 컨트롤](/dotnet/framework/winforms/controls/index)과 함께 [MFC 라이브러리](../mfc/mfc-desktop-applications.md)를 사용하는 애플리케이션.|
|mfcm *version* u.dll|유니코드를 지원하는 MFC 관리되는 라이브러리|[Windows Forms 컨트롤](/dotnet/framework/winforms/controls/index)과 함께 [MFC 라이브러리](../mfc/mfc-desktop-applications.md)를 사용하고 유니코드 지원이 필요한 애플리케이션.|
|vcamp *version*.dll|네이티브 코드용 AMP 라이브러리.|[C++ AMP 라이브러리](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) 코드를 사용하는 애플리케이션.|
|vcomp *version*.dll|네이티브 코드용 OpenMP 라이브러리.|[C++ OpenMP 라이브러리](../parallel/openmp/openmp-in-visual-cpp.md) 코드를 사용하는 애플리케이션.|

> [!NOTE]
> 더 이상 Active Template Library를 별도의 DLL로 재배포할 필요가 없습니다. 해당 기능은 헤더 및 정적 라이브러리로 이동되었습니다.

애플리케이션과 함께 이러한 DLL을 다시 배포하는 방법에 대한 자세한 내용은 [Visual C++ 파일 재배포](redistributing-visual-cpp-files.md)를 참조하세요. 예제는 [배포 예제](deployment-examples.md)를 참조하세요.

일반적으로 시스템 DLL은 운영 체제의 일부이므로 재배포할 필요가 없습니다. 하지만 애플리케이션이 여러 버전의 Microsoft 운영 체제에서 실행되는 경우와 같은 예외도 있을 수 있습니다. 이 경우 해당 사용 약관을 참조해야 합니다. 또한 Windows 업데이트, 서비스 팩 또는 Microsoft에서 제공하는 재배포 가능 패키지를 통해 업그레이드된 시스템 DLL을 가져오세요.

## <a name="see-also"></a>참고 항목

[배포 방법 선택](choosing-a-deployment-method.md)<br/>
[데스크톱 애플리케이션 배포](deploying-native-desktop-applications-visual-cpp.md)
