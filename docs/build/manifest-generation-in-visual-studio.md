---
description: '자세한 정보: Visual Studio에서 매니페스트 생성'
title: Visual Studio에서 매니페스트 생성
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: 88d6cac19e7a0c24a28252edda5ac22ca3cadd64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176446"
---
# <a name="manifest-generation-in-visual-studio"></a>Visual Studio에서 매니페스트 생성

특정 프로젝트의 매니페스트 파일 생성은 프로젝트 **속성 페이지** 대화 상자에서 제어할 수 있습니다. **구성 속성** 탭에서 **링커**, **매니페스트 파일**, **매니페스트 생성** 을 차례로 클릭합니다. 기본적으로 새 프로젝트의 프로젝트 속성은 매니페스트 파일을 생성하도록 설정됩니다. 그러나 프로젝트의 **매니페스트 생성** 속성을 사용하여 프로젝트의 매니페스트 생성을 사용하지 않도록 설정할 수 있습니다. 이 속성을 **예** 로 설정하면 프로젝트의 매니페스트가 생성됩니다. 그러지 않으면 링커가 애플리케이션 코드의 종속성을 확인할 때 어셈블리 정보를 무시하고 매니페스트를 생성하지 않습니다.

Visual Studio의 빌드 시스템을 사용하면 매니페스트를 최종 이진 애플리케이션 파일에 포함하거나 외부 파일로 생성할 수 있습니다. 이 동작은 **프로젝트 속성** 대화 상자에서 **매니페스트 포함** 옵션으로 제어합니다. 이 속성을 설정하려면 **매니페스트 도구** 노드를 연 다음 **입력 및 출력** 을 선택합니다. 매니페스트가 포함되지 않은 경우 외부 파일로 생성되어 최종 이진 파일과 같은 디렉터리에 저장됩니다. 매니페스트가 포함된 경우 Visual Studio는 다음 프로세스를 사용하여 최종 매니페스트를 포함합니다.

1. 소스 코드가 개체 파일로 컴파일되면 링커는 종속 어셈블리 정보를 수집합니다. 최종 이진 파일을 연결하는 동안 링커는 나중에 최종 매니페스트를 생성하는 데 사용되는 중간 매니페스트를 생성합니다.

1. 중간 매니페스트와 연결이 완료되면 매니페스트 도구가 실행되어 최종 매니페스트를 병합하고 외부 파일로 저장합니다.

1. 그런 다음 프로젝트 빌드 시스템은 매니페스트 도구에서 생성된 매니페스트가 이진 파일에 이미 포함된 매니페스트 외의 다른 정보를 포함하는지 검색합니다.

1. 이진 파일에 포함된 매니페스트가 매니페스트 도구에서 생성된 매니페스트와 다르거나 이진 파일에 포함된 매니페스트가 없는 경우 Visual Studio는 링커를 한 번 더 호출하여 외부 매니페스트 파일을 이진 파일 내에 리소스로 포함합니다.

1. 이진 파일에 포함된 매니페스트가 매니페스트 도구에서 생성된 매니페스트와 동일한 경우에는 빌드가 다음 빌드 단계로 진행됩니다.

매니페스트는 최종 이진 파일에 텍스트 리소스로 포함되며 Visual Studio에서 최종 이진 파일을 파일로 열어 볼 수 있습니다. 매니페스트가 올바른 라이브러리를 가리키는지 확인하려면 [Visual C++ 애플리케이션의 종속성 이해](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)에 설명된 단계를 수행하거나 [Troubleshooting](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)(문제 해결) 섹션에서 설명하는 제안을 따르세요.

## <a name="see-also"></a>참조

[ 프로그램의 매니페스트 생성 이해](understanding-manifest-generation-for-c-cpp-programs.md)
