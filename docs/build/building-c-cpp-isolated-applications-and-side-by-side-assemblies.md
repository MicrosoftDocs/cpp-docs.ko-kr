---
description: '자세한 정보: C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드'
title: C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: a48e0e63b78e72d99241df84cdd9709198c1aa82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157076"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드

Visual Studio는 [격리된 애플리케이션](/windows/win32/SbsCs/isolated-applications) 및 [병렬 어셈블리](/windows/win32/SbsCs/about-side-by-side-assemblies-)에 대한 아이디어에 기반을 둔 Windows 클라이언트 애플리케이션의 배포 모델을 지원합니다. 기본적으로 Visual Studio는 모든 네이티브 C/C++ 애플리케이션을 [매니페스트](/windows/win32/sbscs/manifests)를 사용하여 Visual C++ 라이브러리에 대한 종속성을 설명하는 격리된 애플리케이션으로 빌드합니다.

C/C++ 프로그램을 격리된 애플리케이션으로 빌드하면 여러 가지 이점을 얻을 수 있습니다. 예를 들어 격리된 애플리케이션은 다른 C/C++ 애플리케이션이 Visual C++ 라이브러리를 설치 또는 제거하는 경우 영향을 받지 않습니다. 격리된 애플리케이션에서 사용하는 Visual C++ 라이브러리는 애플리케이션의 로컬 폴더에 재배포하거나 네이티브 어셈블리 캐시(WinSxS)를 설치하여 재배포할 수 있습니다. 그러나 [게시자 구성 파일](/windows/win32/SbsCs/publisher-configuration)을 사용하여 이미 배포된 애플리케이션에 대한 Visual C++ 라이브러리 서비스를 간소화할 수 있습니다. 이러한 격리된 애플리케이션 배포 모델을 사용하면 특정 컴퓨터에서 실행 중인 C/C++ 애플리케이션이 가장 최신 버전의 Visual C++ 라이브러리 사용을 보다 쉽게 보장함과 동시에 시스템 관리자 및 애플리케이션 작성자가 자신의 종속 DLL에 대한 명시적 버전 바인딩을 제어할 수 있는 가능성을 열어 둘 수 있습니다.

이 섹션에서는 C/C++ 애플리케이션을 격리된 애플리케이션으로 빌드하는 방법과 해당 애플리케이션이 매니페스트를 사용하여 Visual C++ 라이브러리로 바인딩되도록 보장하는 방법에 대해 설명합니다. 이 섹션의 정보는 주로 네이티브 또는 관리되지 않는 C++ 애플리케이션에 적용됩니다. Visual Studio로 빌드된 네이티브 C++ 애플리케이션 배포에 대한 자세한 내용은 [Visual C++ 파일 재배포](../windows/redistributing-visual-cpp-files.md)를 참조하세요.

## <a name="in-this-section"></a>섹션 내용

[격리된 애플리케이션 및 side-by-side 어셈블리 개념](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[ 격리된 애플리케이션 빌드](building-c-cpp-isolated-applications.md)

[ side-by-side 어셈블리 빌드](building-c-cpp-side-by-side-assemblies.md)

[방법: 등록이 필요 없는 COM 구성 요소 빌드](how-to-build-registration-free-com-components.md)

[방법: COM 구성 요소를 사용하는 격리된 애플리케이션 빌드](how-to-build-isolated-applications-to-consume-com-components.md)

[ 프로그램의 매니페스트 생성 이해](understanding-manifest-generation-for-c-cpp-programs.md)

[ 격리된 애플리케이션 및 side-by-side 어셈블리 문제 해결](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>관련 단원

[격리된 애플리케이션 및 side-by-side 어셈블리](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[데스크톱 애플리케이션 배포](../windows/deploying-native-desktop-applications-visual-cpp.md)
