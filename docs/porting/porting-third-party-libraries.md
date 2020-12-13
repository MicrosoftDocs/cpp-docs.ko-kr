---
description: '자세한 정보: 타사 라이브러리 포팅'
title: 타사 라이브러리 포팅
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: cead058a6d3995a77726bc995996871eba29047f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331240"
---
# <a name="porting-third-party-libraries"></a>타사 라이브러리 포팅

Visual Studio 2013 또는 이전 버전에서 Visual C++의 현재 버전으로 프로젝트를 업그레이드 하는 경우에도 프로젝트에서 사용 하는 모든 라이브러리를 업그레이드 하 여 라이브러리와 프로젝트가 동일한 버전 및 버전의 컴파일러를 사용 하 여 빌드됩니다. 라이브러리 소스 코드에 대 한 액세스 권한이 없고 vcpkg을 통해 라이브러리를 사용할 수 없는 경우 라이브러리 공급 업체에서 업데이트 된 이진 파일을 가져와야 합니다. (자세한 내용은 [잠재적인 업그레이드 문제 개요](overview-of-potential-upgrade-issues-visual-cpp.md)를 참조 하세요.)

응용 프로그램을 Visual Studio 2015 또는 Visual studio 2017에서 Visual Studio 2019로 업그레이드 하는 경우 해당 세 버전으로 생성 된 코드는 이진 호환성이 있으므로 종속성을 업그레이드할 필요가 없습니다. 자세한 내용은 [Visual studio 2015 및 Visual studio 2019 간 c + + 이진 호환성](binary-compat-2015-2017.md)을 참조 하세요.

## <a name="vcpkg-for-open-source-libraries"></a>오픈 소스 라이브러리의 vcpkg

과거에는 타사 라이브러리를 찾고 업그레이드하는 것이 그리 쉬운 작업이 아니었습니다. C + + 타사 오픈 소스 라이브러리를 쉽게 확보 하 고 다시 작성할 수 있도록 Visual C++ 팀에서는 **VC + + 패키징 도구나** **vcpkg** 라는 명령줄 도구를 만들었습니다. vcpkg에는 다양한 인기 C++ 오픈 소스 라이브러리의 검색 가능 카탈로그가 있습니다. vcpkg 명령줄에서 직접 카탈로그에 있는 모든 라이브러리를 설치할 수 있습니다. 라이브러리를 설치할 때 Vcpkg는 컴퓨터에 디렉터리 트리를 만들고 .h, .lib 및 이진 파일을 이 폴더에 추가합니다. 컴파일 명령줄에서 이 폴더를 사용하거나, vcpkg integrate install 명령을 사용하여 Visual Studio 2015 이상에 통합할 수 있습니다. 라이브러리 위치를 통합한 후에는 Visual Studio가 라이브러리를 찾고 생성되는 모든 새 프로젝트에 추가할 수 있습니다. 라이브러리를 사용하기 위해 `#include`하기만 하면 Visual Studio가 프로젝트 설정에 대한 .lib 경로를 자동으로 추가하고 솔루션 폴더에 dll을 복사합니다. 자세한 내용은 [vcpkg: C++용 패키지 관리자](../build/vcpkg.md)를 참조하세요.

## <a name="reporting-issues"></a>문제 보고

**Vcpkg** catalog에 오픈 소스 라이브러리가 없으면 커뮤니티와 Visual C++ 팀이이 라이브러리를 보고 잠재적으로이 라이브러리에 대 한 포트 파일을 만들 수 있는 [GitHub](https://github.com/Microsoft/vcpkg/issues) 리포지토리에서 문제를 열 수 있습니다.

## <a name="see-also"></a>참고 항목

[Visual C++ 포팅 및 업그레이드 가이드](visual-cpp-porting-and-upgrading-guide.md)
