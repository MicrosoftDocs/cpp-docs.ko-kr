---
description: '자세한 정보: Windows에서 Linux 프로그램 실행'
title: Windows에서 Linux 프로그램 실행
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 0822fbb12198622232ff094435894e1a24c36635
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115185"
---
# <a name="running-linux-programs-on-windows"></a>Windows에서 Linux 프로그램 실행

Windows에서 Linux 프로그램을 실행하려면 다음과 같은 옵션이 있습니다.

- WSL(Linux 용 Windows 하위 시스템)에서 프로그램을 있는 그대로 실행합니다. WSL에서 프로그램은 가상 머신이 아닌 컴퓨터 하드웨어에서 직접 실행됩니다. 또한 WSL을 사용하면 Windows와 Linux 시스템 간에 직접 파일 시스템을 호출하여 SSL 전송이 필요하지 않습니다. WSL은 명령줄 환경으로 설계되었으며 그래픽을 많이 사용 하는 애플리케이션에는 사용하지 않는 것이 좋습니다. 자세한 내용은 [Linux용 Windows 하위 시스템 설명서](/windows/wsl/about)를 참조하세요.
- 로컬 컴퓨터 또는 Azure의 Linux 가상 머신 또는 Docker 컨테이너에서 프로그램을 있는 그대로 실행합니다. 자세한 내용은 [가상 머신](https://azure.microsoft.com/services/virtual-machines/) 및 [Azure의 Docker](/azure/docker/)를 참조하세요.
- Linux에서 Windows 시스템 호출로의 변환 계층을 제공하는 [MinGW](http://MinGW.org/) 또는 [MinGW-w64](https://sourceforge.net/p/mingw-w64/wiki2/Home/) 환경에서 gcc 또는 clang을 사용하여 프로그램을 컴파일합니다.
- MinGW 또는 MinGW-w64에 비해 Windows에서 더 복잡한 Linux 환경을 제공하는 [Cygwin](https://www.cygwin.com/) 환경에서 gcc 또는 clang을 사용하여 프로그램을 컴파일하고 실행합니다.
- Linux에서 수동으로 코드를 이식하고 Microsoft C++(MSVC)를 사용하여 Windows용으로 컴파일합니다. 여기에는 플랫폼 독립적인 코드를 별도의 라이브러리로 리팩터링한 다음 Windows 관련 코드(예: Win32 또는 DirectX API)를 사용하도록 Linux 관련 코드를 다시 작성하는 작업이 포함됩니다. 고성능 그래픽이 필요한 애플리케이션의 경우 이 옵션을 선택하는 것이 가장 좋습니다.
