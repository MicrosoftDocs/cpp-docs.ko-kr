---
title: Visual C++의 개발
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 7ca65acef2395bca370aba9b6e435d3f3a152148
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568485"
---
# <a name="deployment-in-visual-c"></a>Visual C++의 개발

개발 컴퓨터 이외의 컴퓨터에서 응용 프로그램 설치는 *배포*라고 합니다. 다른 컴퓨터에 Visual C++ 응용 프로그램을 배포할 때는 응용 프로그램과 해당 응용 프로그램이 종속된 모든 라이브러리 파일을 설치해야 합니다. Visual Studio는 세 가지 방법(*중앙 배포*, *로컬 배포* 및 *정적 연결*)으로 Visual C++ 라이브러리를 응용 프로그램과 함께 배포할 수 있습니다. 중앙 배포는 Windows 업데이트 서비스가 자동으로 라이브러리 파일을 업데이트할 수 있는 Windows 디렉터리 아래 놓습니다. 로컬 배포는 응용 프로그램과 같은 디렉터리에 라이브러리 파일을 놓습니다. 로컬 배포된 모든 라이브러리를 직접 다시 배포해 업데이트해야 합니다. 정적 연결은 라이브러리 코드를 응용 프로그램에 바인딩합니다. 정적 연결을 사용하는 경우 모든 업데이트를 활용하려면 라이브러리에 응용 프로그램을 다시 배포하고 다시 컴파일해야 합니다.

Visual Studio 2015에서는 Microsoft C 런타임 라이브러리가 버전별 로컬 라이브러리 구성 요소 및 Windows의 새 일부인 새 유니버설 C 런타임 라이브러리에 리팩터링됐습니다. 범용 CRT 배포에 대한 세부 정보는 [범용 CRT 배포](universal-crt-deployment.md)를 참조하십시오.

## <a name="central-deployment"></a>중앙 배포

중앙 배포에서 라이브러리 DLL 파일은 Windows\System32 디렉터리에 설치되거나 x64 시스템 상의 32비트 라이브러리 파일은 Windows\SysWow64 디렉터리에 설치됩니다. Microsoft는 중앙 배포된 라이브러리를 자동으로 업데이트합니다. 로컬 배포 또는 정적 링크 Visual C++ 라이브러리의 경우 사용자가 업데이트를 제공해야 합니다.

Visual C++ 라이브러리를 중앙에서 배포하려면 설치할 파일에 대한 다음 두 소스 중 하나를 사용할 수 있습니다.

- *재배포 가능 패키지* 파일. 독립 실행형 명령줄 실행 파일로서 모든 Visual C++ 재배포 가능 라이브러리를 압축 형태로 포함합니다.

- *재배포 가능 병합 모듈*(.msm 파일). 특정 라이브러리 배포에 사용할 수 있고 응용 프로그램의 Windows Installer(.msi) 파일에 포함되는 모듈입니다.

재배포 가능 패키지 파일은 특정 시스템 아키텍처에 대해 모든 Visual C++ 라이브러리를 설치합니다. 예를 들어 응용 프로그램이 x64용으로 빌드되는 경우 응용 프로그램에서 사용하는 모든 Visual C++ 라이브러리를 설치하려면 vcredist_x64.exe 재배포 가능 패키지를 사용할 수 있습니다. 응용 프로그램 설치자를 프로그래밍하여 응용 프로그램을 설치하기 전에 필수 구성 요소로 재배포 가능 패키지를 실행할 수 있습니다.

병합 모듈을 사용하면 Windows Installer 응용 프로그램 설치 파일의 특정 Visual C++ 라이브러리에 대한 설치 논리를 포함할 수 있습니다. 응용 프로그램에 필요한 수의 병합 모듈을 포함할 수 있습니다. 배포 이진 파일의 크기를 최소화해야 할 때 병합 모듈을 사용 합니다.

중앙 배포는 병합 모듈 또는 재배포 가능 패키지를 사용하여 Windows Update가 Visual C++ 라이브러리를 자동으로 업데이트하게 할 수 있기 때문에 정적 라이브러리 대신 응용 프로그램에 라이브러리 DLL을 사용하고 로컬 배포 대신 중앙 배포를 사용하는 것이 좋습니다.

## <a name="local-deployment"></a>로컬 배포

로컬 배포의 경우 라이브러리 파일은 응용 프로그램 폴더에 실행 파일과 함께 설치됩니다. 각 버전의 파일 이름은 해당 버전 번호를 포함하기 때문에 다양한 버전의 Visual C++ 라이브러리를 같은 폴더에 설치할 수 있습니다. 예를 들어, 버전 12의 C++ 런타임 라이브러리는 msvcp120.dll이며 버전 14는 msvcp140.dll입니다.

라이브러리는 *점 라이브러리*라는 여러 추가 DLL에 분산될 수 있습니다. 예를 들어 Visual Studio 2017 버전 15.6에서 릴리스된 표준 라이브러리의 일부 기능은 msvcp140.dll의 ABI 호환성을 보존하기 위해 msvcp140_1.dll에 추가되었습니다. Visual Studio 2017 버전 15.6(도구 집합 14.13) 또는 Visual Studio 2017에서 최신 도구 집합을 사용하는 경우 이러한 점 라이브러리뿐만 아니라 주 라이브러리도 로컬로 배포해야 할 수 있습니다. 이러한 별도 점 라이브러리는 ABI가 변경될 때 다음 주요 버전의 기본 라이브러리로 롤링됩니다.

Microsoft는 로컬 배포된 Visual C++ 라이브러리를 자동으로 업데이트할 수 없기 때문에 이러한 라이브러리의 로컬 배포는 좋지 않습니다. 재배포 가능 라이브러리 로컬 배포를 사용하기로 결정하는 경우 로컬 배포된 라이브러리를 자동으로 업데이트하는 사용자 고유의 메서드를 구현하는 것이 좋습니다.

## <a name="static-linking"></a>정적 링크

동적으로 연결된 라이브러리 외에도 Visual Studio는 대부분의 라이브러리를 정적 라이브러리로 제공합니다. 응용 프로그램에 정적 라이브러리를 정적으로 연결할 수 있습니다. 즉, 라이브러리 개체 코드를 응용 프로그램에 직접 연결할 수 있습니다. 이렇게 하면 DLL 종속성 없는 단일 이진을 만들게 되므로 Visual C++ 라이브러리 파일을 별도로 배포할 필요가 없습니다. 그러나 정적으로 연결된 라이브러리는 적절하게 업데이트할 수 없기 때문에 이 방식은 좋지 않습니다. 정적 연결을 사용하고 연결된 라이브러리를 업데이트하려면 응용 프로그램을 다시 컴파일하고 다시 배포해야 합니다.

## <a name="troubleshooting-deployment-issues"></a>배포 문제 해결

Visual C++ 라이브러리의 로드 순서는 시스템에 따라 다릅니다. 로더 문제를 진단하려면 depends.exe 또는 where.exe를 사용합니다. 자세한 내용은 [동적 연결 라이브러리 순서(Windows)](/windows/desktop/Dlls/dynamic-link-library-search-order)를 참조하십시오.

## <a name="see-also"></a>참고 항목

- [데스크톱 응용 프로그램 배포](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [범용 CRT 배포](universal-crt-deployment.md)
