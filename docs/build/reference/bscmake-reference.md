---
description: '자세한 정보: BSCMAKE 참조'
title: BSCMAKE 참조
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 11a90561e22b9fb3a39f022ba188e5c9d155e45e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179431"
---
# <a name="bscmake-reference"></a>BSCMAKE 참조

> [!WARNING]
> BSCMAKE는 Visual Studio와 함께 설치되지만 더 이상 IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 및 기호 정보는 자동으로 솔루션 폴더의 SQL Server .sdf 파일에 저장됩니다.

Microsoft Browse Information Maintenance Utility(BSCMAKE.EXE)에서는 컴파일 중에 생성된 .sbr 파일에서 찾아보기 정보 파일(.bsc)이 빌드됩니다. 특정 타사 도구는 코드 분석에 .bsc 파일을 사용 합니다.

프로그램을 빌드할 때 BSCMAKE를 사용하여 파일을 빌드하면 프로그램에 대한 찾아보기 정보를 자동으로 만들 수 있습니다. Visual Studio 개발 환경에서 찾아보기 정보 파일을 만드는 경우 BSCMAKE를 실행 하는 방법을 알 필요가 없습니다. 그러나 이 항목을 읽으면 사용 가능한 선택 항목을 이해할 수 있습니다.

개발 환경 외부에서 프로그램을 빌드하면 해당 환경에서 검사할 수 있는 사용자 지정 .bsc를 만들 수 있습니다. 컴파일 중에 만든 .sbr 파일에서 BSCMAKE를 실행합니다.

> [!NOTE]
> 이 도구는 Visual Studio 개발자 명령 프롬프트 에서만 시작할 수 있습니다. 시스템 명령 프롬프트 또는 파일 탐색기에서는 시작할 수 없습니다.

이 단원에 포함된 항목은 다음과 같습니다.

- [찾아보기 정보 파일 빌드: 개요](building-browse-information-files-overview.md)

- [.Bsc 파일 빌드](building-a-dot-bsc-file.md)

- [BSCMAKE 명령줄](bscmake-command-line.md)

- [BSCMAKE 명령 파일](bscmake-command-file-response-file.md)

- [BSCMAKE 옵션](bscmake-options.md)

- [BSCMAKE 종료 코드](bscmake-exit-codes.md)

## <a name="see-also"></a>참고 항목

[추가 MSVC 빌드 도구](c-cpp-build-tools.md)
