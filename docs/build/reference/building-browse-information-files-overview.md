---
description: '자세히 알아보기: 찾아보기 정보 파일 빌드: 개요'
title: '찾아보기 정보 파일 빌드: 개요'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: e689a22ef982911526afb370764de913562a2557
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187080"
---
# <a name="building-browse-information-files-overview"></a>찾아보기 정보 파일 빌드: 개요

> [!WARNING]
> BSCMAKE는 Visual Studio와 함께 설치되지만 더 이상 IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 및 기호 정보는 자동으로 솔루션 폴더의 SQL Server .sdf 파일에 저장됩니다.

기호 검색에 대 한 찾아보기 정보를 만들기 위해 컴파일러는 프로젝트의 각 소스 파일에 대 한 .sbr 파일을 만든 다음 .sbr 파일을 .bsc 파일 하나에 연결 BSCMAKE.EXE.

.Sbr 및 .bsc 파일을 생성 하는 데 시간이 걸리므로 Visual Studio는 기본적으로 이러한 함수를 해제 합니다. 현재 정보를 찾아보려면 찾아보기 옵션을 설정 하 고 프로젝트를 다시 빌드해야 합니다.

[/Fr](fr-fr-create-dot-sbr-file.md) 또는 [/fr](fr-fr-create-dot-sbr-file.md) 를 사용 하 여 컴파일러에 .sbr 파일을 만들도록 지시 합니다. .Bsc 파일을 만들려면 명령줄에서 [BSCMAKE](bscmake-command-line.md) 를 호출 하면 됩니다. 명령줄에서 BSCMAKE를 사용 하면 찾아보기 정보 파일을 보다 정밀 하 게 제어할 수 있습니다. 자세한 내용은 [BSCMAKE 참조](bscmake-reference.md) 를 참조 하세요.

> [!TIP]
> .Sbr 파일 생성을 켤 수는 있지만 .bsc 파일 생성은 해제 되어 있습니다. 이는 빠른 빌드를 제공 하지만 .bsc 파일 생성을 설정 하 고 프로젝트를 빌드하여 새 .bsc 파일을 신속 하 게 만들 수 있습니다.

.Bsc 파일의 크기를 줄여서 .bsc 파일을 빌드하는 데 필요한 시간, 메모리 및 디스크 공간을 줄일 수 있습니다.

개발 환경에서 브라우저 파일을 빌드하는 방법에 대 한 자세한 내용은 [일반 속성 페이지 (프로젝트)](general-property-page-project.md) 를 참조 하세요.

### <a name="to-create-a-smaller-bsc-file"></a>더 작은 .bsc 파일을 만들려면

1. [BSCMAKE 명령줄 옵션](bscmake-options.md) 을 사용 하 여 찾아보기 정보 파일에서 정보를 제외 합니다.

1. 컴파일하거나 어셈블할 때 하나 이상의 .sbr 파일에서 로컬 기호를 생략 합니다.

1. 현재 디버깅 단계에 필요한 정보가 개체 파일에 포함 되어 있지 않으면 찾아보기 정보 파일을 다시 빌드할 때 BSCMAKE 명령에서 해당 .sbr 파일을 생략 합니다.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>여러 프로젝트의 찾아보기 정보를 하나의 브라우저 파일 (.bsc)로 결합 하려면

1. 프로젝트 수준에서 .bsc 파일을 빌드하지 않거나/n 스위치를 사용 하 여 .sbr 파일이 잘리지 않도록 합니다.

1. 모든 프로젝트를 빌드한 후에는 모든 .sbr 파일을 입력으로 사용 하 여 BSCMAKE를 실행 합니다. 와일드 카드가 허용 됩니다. 예를 들어 프로젝트 디렉터리 C:\X, C:\X, C:\X에 .sbr 파일이 있는 경우이 파일을 모두 하나의 .bsc 파일에 결합 한 다음, BSCMAKE C:\X .sbr c:\bbbbbbbbbbbbbbnebnebbb\combined.bsc \\ \* \\ \* \\ \* /o c:\ whatever_directory를 사용 하 여 결합 된 .bsc 파일을 빌드합니다.

## <a name="see-also"></a>참고 항목

[추가 MSVC 빌드 도구](c-cpp-build-tools.md)<br/>
[BSCMAKE 참조](bscmake-reference.md)
