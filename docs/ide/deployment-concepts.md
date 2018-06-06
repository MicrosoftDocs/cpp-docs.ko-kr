---
title: 배포 개념 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0960e94acdbe660474efbeeddd0f72fa4f0606f6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34257064"
---
# <a name="deployment-concepts"></a>배포 개념

이 섹션에서는 C++ 응용 프로그램 배포에 대한 주요 고려 사항을 설명합니다.

## <a name="windows-installer-deployment-in-c"></a>C++에서 Windows Installer 배포

Visual C++ 프로젝트는 일반적으로 배포를 위한 기존의 Windows Installer 설정을 사용합니다. Windows Installer 배포를 준비하려면 setup.exe 파일에서 응용 프로그램을 패키지하고 설치 관리자 패키지(.msi)와 함께 해당 파일을 배포합니다. 그런 다음, 사용자는 setup.exe를 실행하여 응용 프로그램을 설치합니다.

설치 프로젝트를 솔루션에 추가하여 응용 프로그램 패키지하고, 빌드할 때 사용자에게 배포하는 설정 및 설치 관리자 패키지 파일을 만듭니다. 자세한 내용은 [배포 방법 선택](../ide/choosing-a-deployment-method.md)을 참조하세요.

## <a name="library-dependencies"></a>라이브러리 종속성

Visual C++ 라이브러리에서 제공하는 기능을 사용하여 C/C++ 응용 프로그램을 빌드할 경우 이 응용 프로그램은 런타임 시 해당 라이브러리의 존재에 종속되게 됩니다. 응용 프로그램을 실행하려면 정적으로든 동적으로든 필요한 Visual C++ 라이브러리에 연결돼야 합니다. 응용 프로그램이 Visual C++ 라이브러리에 동적으로 연결되면 실행 시 해당 라이브러리가 존재해야 로드될 수 있습니다. 반면 응용 프로그램이 Visual C++ 라이브러리에 정적으로 연결되는 경우 해당 DLL이 사용자의 컴퓨터에 존재할 필요가 없습니다. 하지만 정적 연결에는 응용 프로그램 파일의 크기를 늘리고 유지 관리를 잠재적으로 더 어렵게 만드는 등 몇 가지 단점이 있습니다. 자세한 내용은 [DLL 사용의 장점](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls)을 참조합니다.

## <a name="packaging-and-redistributing"></a>패키징 및 재배포

Visual C++ 라이브러리는 DLL로 패키지되며, Visual Studio에서 C/C++ 응용 프로그램에 필요한 모든 라이브러리를 개발자의 컴퓨터에 설치합니다. 그러나 사용자에게 응용 프로그램을 배포할 때 대부분의 경우 응용 프로그램을 실행하기 위해 Visual Studio를 설치하도록 요구하는 것은 실현가능하지 않습니다. 응용 프로그램에서 올바르게 실행할 것을 요구하는 Visual C++의 해당 파트만 재배포할 수 있는 것이 중요합니다.

패키징 및 재배포에 대한 자세한 내용은 다음 항목을 참조합니다.

- [재배포할 DLL 확인](../ide/determining-which-dlls-to-redistribute.md).

- [배포 방법 선택](../ide/choosing-a-deployment-method.md).

- [범용 CRT 배포](universal-crt-deployment.md).

문제 해결에 대한 배포 예제 및 제안 사항은 다음을 참조합니다.

- [배포 예제](../ide/deployment-examples.md).

- [C/C++ 격리된 응용 프로그램 및 side-by-side 어셈블리 문제 해결](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>참고 항목

- [데스크톱 응용 프로그램 배포](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Visual C++ 응용 프로그램의 종속성 이해](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)
- [Windows Installer 배포](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
