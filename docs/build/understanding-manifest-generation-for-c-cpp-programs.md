---
description: '자세한 정보: C/C++ 프로그램의 매니페스트 생성 이해'
title: C/C++ 프로그램의 매니페스트 생성 이해
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 78169dd6d8185e1ae8470dea93ab145fc05dbc7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277273"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>C/C++ 프로그램의 매니페스트 생성 이해

[매니페스트](/windows/win32/sbscs/manifests)는 애플리케이션이나 어셈블리 내부에 포함된 외부 XML 파일이나 리소스일 수 있는 XML 문서입니다. [격리된 애플리케이션](/windows/win32/SbsCs/isolated-applications)의 매니페스트는 런타임에 애플리케이션을 바인딩해야 하는 공유 side-by-side 어셈블리의 이름과 버전을 관리하는 데 사용됩니다. side-by-side 어셈블리의 매니페스트는 이름, 버전, 리소스 및 다른 어셈블리에 대한 어셈블리의 종속성을 지정합니다.

격리된 애플리케이션 또는 side-by-side 어셈블리의 매니페스트를 만드는 방법은 두 가지입니다. 먼저 어셈블리 작성자가 규칙 및 명명 요구 사항에 따라 매니페스트 파일을 수동으로 만들 수 있습니다. 또는 프로그램이 CRT, MFC, ATL 등의 Visual C++ 어셈블리에만 종속되는 경우 링커에서 매니페스트를 자동으로 생성할 수 있습니다.

Visual C++ 라이브러리의 헤더에는 어셈블리 정보가 포함되어 있으며, 라이브러리가 애플리케이션 코드에 포함되어 있으면 링커에서 이 어셈블리 정보를 사용하여 최종 이진 파일의 매니페스트를 구성합니다. 링커는 매니페스트 파일을 이진 파일 안에 포함하지 않고 매니페스트를 외부 파일로만 생성할 수 있습니다. 매니페스트를 외부 파일로 사용하는 경우 일부 시나리오에서는 작동하지 않을 수 있습니다. 예를 들어 프라이빗 어셈블리에는 매니페스트를 포함하는 것이 좋습니다. nmake를 사용하여 코드를 빌드하는 것과 같은 명령줄 빌드에서는 매니페스트 도구를 사용하여 매니페스트를 포함할 수 있습니다. 자세한 내용은 [명령줄에서 매니페스트 생성](manifest-generation-at-the-command-line.md)을 참조하세요. Visual Studio에서 빌드할 때는 **프로젝트 속성** 대화 상자에서 매니페스트 도구의 속성을 설정하여 매니페스트를 포함할 수 있습니다. [Visual Studio에서 매니페스트 생성](manifest-generation-in-visual-studio.md)을 참조하세요.

## <a name="see-also"></a>참조

[격리된 애플리케이션 및 side-by-side 어셈블리 개념](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
