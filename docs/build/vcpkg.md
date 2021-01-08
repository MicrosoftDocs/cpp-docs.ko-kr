---
title: 'vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자'
description: vcpkg는 Windows, macOS 및 Linux에서 오픈 소스 C++ 라이브러리 획득 및 설치를 크게 간소화하는 명령줄 패키지 관리자입니다.
ms.custom: contperf-fy21q2
ms.date: 12/11/2020
ms.topic: overview
ms.technology: cpp-ide
ms.openlocfilehash: f937f1df718bf8dfcc0ae5166d8b9eb671d2d8ab
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97682468"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자

vcpkg는 C 및 C++ 라이브러리용 플랫폼 간 명령줄 패키지 관리자입니다. vcpkg는 Windows, Linux 및 macOS에서 타사 라이브러리 다운로드 및 설치를 간소화합니다. 프로젝트에서 타사 라이브러리를 사용하는 경우 vcpkg를 사용하여 설치하는 것이 좋습니다. vcpkg는 오픈 소스와 독점 라이브러리를 모두 지원합니다. vcpkg Windows 카탈로그의 모든 라이브러리가 isual Studio 2015, Visual Studio 2017 및 Visual Studio 2019와의 호환성 테스트를 거쳤습니다. vcpkg는 이제 Windows 카탈로그와 Linux/macOS 카탈로그 간에 수천 개의 라이브러리를 지원합니다. C++ 커뮤니티는 지속해서 두 카탈로그에 더 많은 라이브러리를 추가하고 있습니다.

## <a name="how-to-get-and-use-vcpkg"></a>vcpkg를 가져오고 사용하는 방법

vcpkg GitHub 리포지토리 [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg)에서 로컬 클론을 만들어 vcpkg를 설치합니다. 그런 다음, vcpkg 부트스트래퍼 스크립트를 실행하여 설정합니다. 자세한 설치 지침은 [vcpkg 설치](install-vcpkg.md)를 참조하세요. vcpkg를 Visual Studio 또는 Visual Studio Code 개발 환경과 통합하려면 [vcpkg 통합](integrate-vcpkg.md)을 참조하세요. 그런 다음, vcpkg를 사용하여 라이브러리를 설치하거나 업데이트하려면 [vcpkg를 사용하여 라이브러리 관리](manage-libraries-with-vcpkg.md)를 참조하세요. vcpkg 명령에 대한 자세한 내용은 [vcpkg 명령줄 참조](vcpkg-command-line-reference.md)를 참조하세요.

## <a name="how-vcpkg-works"></a>vcpkg 작동 방식

vcpkg 프로젝트는 GitHub에서 사용할 수 있는 오픈 소스입니다. vcpkg 리포지토리의 ‘클론’ 또는 로컬 복사본에는 vcpkg 실행 파일 및 ‘카탈로그’, 라이브러리 및 해당 옵션을 설명하는 패키지 목록이 포함되어 있습니다.  각 패키지에는 하나 이상의 ‘포트’가 포함되어 있으며, 소스에서 라이브러리를 가져오고 빌드하거나 특정 대상 환경용 이진 버전을 다운로드하는 방법에 대한 정보도 포함되어 있습니다. vcpkg를 사용하여 라이브러리를 설치하면 패키지 및 포트 정보를 사용하여 vcpkg 디렉터리의 하위 디렉터리에 라이브러리의 로컬 복사본을 다운로드하고 생성하므로 바로 사용할 수 있습니다.

소스 폼에서 라이브러리를 사용할 수 있으면 vcpkg는 이진 파일 대신 소스를 다운로드합니다. 그리고 찾을 수 있는 최신 버전의 C 또는 C++ 컴파일러를 사용하여 해당 소스를 컴파일합니다. C++ ABI 호환성을 위해 애플리케이션 코드와 사용하는 모든 라이브러리가 모두 동일한 버전의 동일한 컴파일러로 컴파일되어야 합니다. vcpkg를 사용하여 이진 파일 불일치 및 이로 인해 발생할 수 있는 문제를 제거하거나 적어도 크게 줄일 수 있습니다. 특정 버전의 컴파일러를 표준화한 팀에서는 한 팀원이 vcpkg를 사용하여 소스를 다운로드하고 이진 파일 세트를 컴파일할 수 있습니다. 팀의 모든 사용자가 공통 라이브러리를 다운로드하고 작성하는 것은 비효율적입니다. 한 팀원은 **`vcpkg export`** 명령을 사용하여 이진 파일 및 헤더의 일반 Zip 파일 또는 NuGet 패키지를 만들 수 있습니다. 그런 다음 다른 팀 멤버와 공유하기가 쉽습니다.

## <a name="customize-vcpkg-instances-for-different-targets"></a>다른 대상에 맞게 vcpkg 인스턴스 사용자 지정

머신에 있는 vcpkg의 여러 복사본 또는 ‘인스턴스’를 복제하고 특정 용도에 맞게 각각을 사용자 지정할 수 있습니다. 각 인스턴스에서 다른 라이브러리를 설치하거나 퍼블릭 카탈로그의 버전과 다른 버전의 라이브러리를 설치할 수 있습니다. 각 인스턴스는 원하는 컴파일러 옵션을 사용하여 라이브러리의 사용자 지정 컬렉션을 생성하도록 설정될 수 있습니다. 각 인스턴스는 자체 계층 구조에서만 작동하는 vcpkg.exe의 자체 복사본이 포함된 자체 포함 환경입니다. vcpkg는 어떤 환경 변수에도 추가되지 않으며 Windows 레지스트리 또는 Visual Studio에 종속되지 않습니다.

또한 포트 컬렉션에 프라이빗 라이브러리가 있는 vcpkg 클론을 만들 수 있습니다. 미리 빌드된 이진 파일 및 헤더를 다운로드하는 포트를 추가할 수 있습니다. 그런 다음, 해당 파일을 기본 위치에 단순히 복사하는 *portfile.cmake* 파일을 작성합니다.

## <a name="the-vcpkg-folder-hierarchy"></a>Vcpkg 폴더 계층 구조

모든 vcpkg 기능 및 데이터는 인스턴스별로 단일 디렉터리 계층 구조에 자체 포함됩니다. 레지스트리 설정 또는 환경 변수는 없습니다. 한 컴퓨터에 vcpkg의 인스턴스가 얼마든지 있을 수 있으며 서로를 방해하지 않습니다.

Vcpkg 인스턴스의 내용:

- *`buildtrees`* - 각 라이브러리가 빌드되는 소스의 하위 폴더 포함
- *`docs`* - 설명서 및 예제
- *`downloads`* - 다운로드된 도구 또는 소스의 캐시된 복사본. 설치 명령을 실행하면 vcpkg는 여기를 먼저 검색합니다.
- *`installed`* - 설치된 각 라이브러리의 헤더 및 이진 파일 포함. Visual Studio와 통합하는 것은 본질적으로 이 폴더를 검색 경로에 추가하는 것입니다.
- *`packages`* - 설치 간 스테이징을 위한 내부 폴더
- *`ports`* - 카탈로그의 각 라이브러리, 해당 버전, 다운로드 위치를 설명하는 파일. 필요한 경우 고유한 포트를 추가할 수 있습니다.
- *`scripts`* - vcpkg가 사용하는 스크립트(CMake, PowerShell)
- *`toolsrc`* - vcpkg 및 관련 구성 요소에 대한 C++ 소스 코드
- *`triplets`* - 지원되는 각 대상 플랫폼에 대한 설정(예: x86-windows 또는 x64-uwp) 포함

## <a name="telemetry"></a>원격 분석

vcpkg는 사용자 환경을 개선하는 데 도움이 되도록 사용량 현황 데이터를 수집합니다. Microsoft에서 수집하는 데이터는 익명입니다. **`bootstrap-vcpkg.bat`** 또는 **`bootstrap-vcpkg.sh`** 스크립트를 **`-disableMetrics`** 옵션을 사용하여 다시 실행함으로써 원격 분석을 옵트아웃할 수 있습니다. 또는 명령줄에서 **`--disable-metrics`** 옵션을 vcpkg에 전달할 수 있습니다. `VCPKG_DISABLE_METRICS` 환경 변수를 설정하여 메트릭을 사용하지 않도록 설정할 수도 있습니다.

## <a name="send-feedback-about-vcpkg"></a>vcpkg에 대한 사용자 의견 보내기

**`vcpkg contact --survey`** 명령을 사용하여 버그 신고 및 기능 제안을 비롯한 vcpkg 관련 피드백을 Microsoft에 보냅니다. 자세한 내용은 [vcpkg 명령줄 참조](vcpkg-command-line-reference.md)를 참조하세요.

## <a name="see-also"></a>추가 정보

[GitHub의 vcpkg](https://github.com/Microsoft/vcpkg)\
[vcpkg 설치](install-vcpkg.md)\
[vcpkg 통합](integrate-vcpkg.md)\
[vcpkg를 사용하여 라이브러리 관리](manage-libraries-with-vcpkg.md)\
[vcpkg 명령줄 참조](vcpkg-command-line-reference.md)\
[빠른 시작](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[자주 묻는 질문](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
