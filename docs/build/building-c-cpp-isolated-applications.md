---
description: '자세한 정보: C/C++ 격리된 애플리케이션 빌드'
title: C/C++ 격리된 애플리케이션 빌드
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: a8cd99032c27d21efaec7f213c470017e52777c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163212"
---
# <a name="building-cc-isolated-applications"></a>C/C++ 격리된 애플리케이션 빌드

격리된 애플리케이션은 side-by-side 어셈블리에만 종속되며 매니페스트를 사용하여 해당 종속성에 바인딩합니다. 애플리케이션이 완전히 격리되지 않아도 Windows에서 제대로 실행되지만 노력을 들여 애플리케이션을 완전히 격리하면 나중에 애플리케이션을 서비스해야 하는 경우 시간을 절약할 수 있습니다. 애플리케이션을 완전히 격리하는 경우의 이점에 대한 자세한 내용은 [격리된 애플리케이션](/windows/win32/SbsCs/isolated-applications)을 참조하세요.

Visual Studio를 사용하여 네이티브 C/C++ 애플리케이션을 빌드하는 경우 기본적으로 Visual Studio 프로젝트 시스템은 Visual Studio 라이브러리에 대한 애플리케이션의 종속성을 설명하는 매니페스트 파일을 생성합니다. 애플리케이션이 종속성만 있는 경우 Visual Studio로 다시 빌드하면 바로 격리된 애플리케이션이 됩니다. 애플리케이션이 런타임에 다른 라이브러리를 사용하는 경우에는 [C/C++ Side-by-side 어셈블리 빌드](building-c-cpp-side-by-side-assemblies.md)에 설명된 단계에 따라 라이브러리를 side-by-side 어셈블리로 다시 빌드해야 할 수 있습니다.

## <a name="see-also"></a>참조

[격리된 애플리케이션 및 side-by-side 어셈블리 개념](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
