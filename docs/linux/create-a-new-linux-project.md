---
title: Visual Studio에서 Linux MSBuild C++ 프로젝트 만들기
ms.date: 08/04/2020
description: Visual Studio에서 새로운 MSBuild 기반 Linux 프로젝트를 만듭니다.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 559a868ebdea7e3b835a82c31849d0e2fdeaa6c9
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686693"
---
# <a name="create-a-linux-msbuild-c-project-in-visual-studio"></a>Visual Studio에서 Linux MSBuild C++ 프로젝트 만들기

::: moniker range="vs-2015"

Linux 프로젝트는 Visual Studio 2017 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range="vs-2017"

먼저 Visual Studio용 **Linux 개발 작업 워크로드**가 설치되어 있는지 확인합니다. 자세한 내용은 [Linux 워크로드 다운로드, 설치, 설정](download-install-and-setup-the-linux-development-workload.md)을 참조하세요.

플랫폼 간 컴파일의 경우 CMake를 사용하는 것이 좋습니다. Visual Studio 2019에서는 CMake 지원이 더 완전합니다. CMake가 옵션이 아닌데 Linux용으로 컴파일되도록 확장하려는 기존 Windows Visual Studio 솔루션이 있는 경우 **공유 항목** 프로젝트와 함께 Visual Studio Linux 프로젝트를 Windows 솔루션에 추가할 수 있습니다. 공유 항목 프로젝트에 두 플랫폼 간에 공유되는 코드를 배치하고 Windows 및 Linux 프로젝트에서 해당 프로젝트에 대한 참조를 추가합니다.

## <a name="to-create-a-new-linux-project"></a>새 Linux 프로젝트를 만들려면

Visual Studio 2017에서 새 Linux 프로젝트를 만들려면 다음 단계를 수행합니다.

1. Visual Studio에서 **파일 > 새 프로젝트**를 선택하거나 **Ctrl + Shift + N**을 누릅니다.
1. **Visual C++ > 플랫폼 간 > Linux** 노드를 선택한 다음, 만들려는 프로젝트 형식을 선택합니다. **이름** 및 **위치**를 입력하고, **확인**을 선택합니다.

   ![Visual C++ > 플랫폼 간 > Linux가 선택되고 모든 프로젝트 형식이 호출되었으며 이름 및 위치 텍스트 상자도 호출된 새 프로젝트 대화 상자를 보여 주는 스크린샷](media/newproject.png)

   | 프로젝트 형식 | 설명 |
   | ------------ | --- |
   | **깜박임(Raspberry)**           | Raspberry Pi 디바이스를 대상으로 하는 프로젝트로, LED가 깜박이는 샘플 코드가 포함되어 있습니다. |
   | **콘솔 애플리케이션(Linux)** | Linux 컴퓨터를 대상으로 하는 프로젝트로, 콘솔에 텍스트를 출력하는 샘플 코드가 포함되어 있습니다. |
   | **빈 프로젝트(Linux)**       | Linux 컴퓨터를 대상으로 하는 프로젝트로, 샘플 코드가 없습니다. |
   | **메이크파일 프로젝트(Linux)**    | Linux 컴퓨터를 대상으로 하는 프로젝트로, 표준 메이크파일 빌드 시스템을 사용하여 빌드됩니다. |

## <a name="next-steps"></a>다음 단계

[MSBuild Linux 프로젝트 구성](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

먼저 Visual Studio용 **Linux 개발 작업 워크로드**가 설치되어 있는지 확인합니다. 자세한 내용은 [Linux 작업 다운로드, 설치, 설정](download-install-and-setup-the-linux-development-workload.md)을 참조하세요.

Visual Studio에서 Linux에 대한 새로운 C++ 프로젝트를 만들 때 Visual Studio 프로젝트 또는 CMake 프로젝트를 만들도록 선택할 수 있습니다. 이 문서에서는 Visual Studio 프로젝트를 만드는 방법을 설명합니다. 일반적으로 오픈 소스 코드를 포함할 수 있거나 플랫폼 간 개발용으로 컴파일하려는 새 프로젝트의 경우 Visual Studio와 함께 CMake를 사용하는 것이 좋습니다. CMake 프로젝트를 사용하면 Windows와 Linux 모두에서 같은 프로젝트를 빌드하고 디버그할 수 있습니다. 자세한 내용은 [Linux CMake 프로젝트 만들기 및 구성](cmake-linux-project.md)을 참조하세요.

Linux용으로 컴파일되도록 확장하려는 기존 Windows Visual Studio 솔루션이 있는데 CMake가 옵션이 아닌 경우 **공유 항목** 프로젝트와 함께 Visual Studio Linux 프로젝트를 Windows 솔루션에 추가할 수 있습니다. 공유 항목 프로젝트에 두 플랫폼 간에 공유되는 코드를 배치하고 Windows 및 Linux 프로젝트에서 해당 프로젝트에 대한 참조를 추가합니다.

## <a name="to-create-a-new-linux-project"></a>새 Linux 프로젝트를 만들려면

Visual Studio 2019에서 새 Linux 프로젝트를 만들려면 다음 단계를 수행합니다.

1. Visual Studio에서 **파일 > 새 프로젝트**를 선택하거나 **Ctrl + Shift + N**을 누릅니다.
1. **언어**를 **C++** 로 설정하고 "Linux"를 검색합니다. 만들려는 프로젝트 형식을 선택한 다음, **다음**을 선택합니다. **이름** 및 **위치**를 입력하고, **만들기**를 선택합니다.

   ![검색 텍스트 상자에 Linux가 입력된 새 프로젝트 추가 대화 상자의 스크린샷](media/newproject-vs2019.png)

   | 프로젝트 형식 | 설명 |
   | ------------ | --- |
   | **깜박임(Raspberry)**           | Raspberry Pi 디바이스를 대상으로 하는 프로젝트로, LED가 깜박이는 샘플 코드가 포함되어 있습니다. |
   | **콘솔 애플리케이션(Linux)** | Linux 컴퓨터를 대상으로 하는 프로젝트로, 콘솔에 텍스트를 출력하는 샘플 코드가 포함되어 있습니다. |
   | **빈 프로젝트(Linux)**       | Linux 컴퓨터를 대상으로 하는 프로젝트로, 샘플 코드가 없습니다. |
   | **메이크파일 프로젝트(Linux)**    | Linux 컴퓨터를 대상으로 하는 프로젝트로, 표준 메이크파일 빌드 시스템을 사용하여 빌드됩니다. |

## <a name="next-steps"></a>다음 단계

[Linux MSBuild 프로젝트 구성](configure-a-linux-project.md)

::: moniker-end
