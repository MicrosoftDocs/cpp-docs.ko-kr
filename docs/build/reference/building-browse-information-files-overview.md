---
title: '찾아보기 정보 파일 빌드: 개요'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320678"
---
# <a name="building-browse-information-files-overview"></a>찾아보기 정보 파일 빌드: 개요

> [!WARNING]
> BSCMAKE는 Visual Studio와 함께 설치되지만 더 이상 IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 및 기호 정보는 자동으로 솔루션 폴더의 SQL Server .sdf 파일에 저장됩니다.

심볼 브라우징을 위한 찾아보기 정보를 만들기 위해 컴파일러는 프로젝트의 각 소스 파일에 대해 .sbr 파일을 만든 다음 BSCMAKE를 만듭니다. EXE는 .sbr 파일을 하나의 .bsc 파일로 연결합니다.

.sbr 및 .bsc 파일을 생성하는 데는 시간이 걸리므로 Visual Studio는 기본적으로 이러한 기능을 해제합니다. 현재 정보를 찾아보려는 경우 찾아보기 옵션을 켜고 프로젝트를 다시 빌드해야 합니다.

[/FR](fr-fr-create-dot-sbr-file.md) 또는 [/Fr을](fr-fr-create-dot-sbr-file.md) 사용하여 컴파일러에 .sbr 파일을 만들라고 말합니다. .bsc 파일을 만들려면 명령줄에서 [BSCMAKE를](bscmake-command-line.md) 호출할 수 있습니다. 명령줄에서 BSCMAKE를 사용하면 찾아보기 정보 파일의 조작을 보다 정확하게 제어 할 수 있습니다. 자세한 내용은 [BSCMAKE 참조를](bscmake-reference.md) 참조하십시오.

> [!TIP]
> .sbr 파일 생성을 켤 수 있지만 .bsc 파일 생성을 해제한 상태로 둘 수 있습니다. 이렇게 하면 빌드가 빠르지만 .bsc 파일 생성을 켜고 프로젝트를 빌드하여 새로 이되는 .bsc 파일을 빠르게 만들 수 있습니다.

.bsc 파일의 크기를 줄여 .bsc 파일을 빌드하는 데 필요한 시간, 메모리 및 디스크 공간을 줄일 수 있습니다.

개발 환경에서 브라우저 파일을 빌드하는 방법에 대한 자세한 내용은 [일반 속성 페이지(프로젝트)를](general-property-page-project.md) 참조하십시오.

### <a name="to-create-a-smaller-bsc-file"></a>더 작은 .bsc 파일을 만들려면

1. [BSCMAKE 명령줄 옵션을](bscmake-options.md) 사용하여 찾아보기 정보 파일에서 정보를 제외합니다.

1. 컴파일하거나 어셈블할 때 하나 이상의 .sbr 파일에서 로컬 기호를 생략합니다.

1. 개체 파일에 현재 디버깅 단계에 필요한 정보가 포함되어 있지 않으면 찾아보기 정보 파일을 다시 빌드할 때 BSCMAKE 명령에서 .sbr 파일을 생략합니다.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>여러 프로젝트의 찾아보기 정보를 하나의 브라우저 파일(.bsc)으로 결합하려면

1. 프로젝트 수준에서 .bsc 파일을 빌드하지 않거나 /n 스위치를 사용하여 .sbr 파일이 잘리지 않도록 합니다.

1. 모든 프로젝트가 빌드된 후 모든 .sbr 파일을 입력으로 실행합니다. 와일드카드가 허용됩니다. 예를 들어 프로젝트 디렉토리 C:\X, C:\Y 및 C:\Z와 .sbr 파일을 모두 하나의 .bsc 파일로 결합하려는 경우 BSCMAKE\\\*C:\X .sbr C:\Sbr C:\Sbr\\\*C:\Z.sbr\\\*/o c:\whatever_directory 결합된 .bsc를 사용하여 결합된 .bsc 파일을 빌드합니다.

## <a name="see-also"></a>참고 항목

[추가 MSVC 빌드 도구](c-cpp-build-tools.md)<br/>
[BSCMAKE 참조](bscmake-reference.md)
