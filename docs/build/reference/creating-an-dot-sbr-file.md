---
description: '에 대 한 자세한 정보: 만들기 .Sbr 파일'
title: .Sbr 파일 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 7f3e056418fe1716dc0130330b09c369e9bdceff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196921"
---
# <a name="creating-an-sbr-file"></a>.Sbr 파일 만들기

> [!WARNING]
> BSCMAKE는 Visual Studio와 함께 설치되지만 더 이상 IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 및 기호 정보는 자동으로 솔루션 폴더의 SQL Server .sdf 파일에 저장됩니다.

BSCMAKE의 입력 파일은 .sbr 파일입니다. 컴파일러는 컴파일되는 각 개체 파일 (.obj)에 대해 .sbr 파일을 만듭니다. 찾아보기 정보 파일을 빌드하거나 업데이트할 때 프로젝트에 대 한 모든 .sbr 파일을 디스크에서 사용할 수 있어야 합니다.

가능한 모든 정보를 사용 하 여 .sbr 파일을 만들려면 [/fr](fr-fr-create-dot-sbr-file.md)를 지정 합니다.

로컬 기호를 포함 하지 않는 .sbr 파일을 만들려면 [/fr](fr-fr-create-dot-sbr-file.md)를 지정 합니다. .Sbr 파일에 로컬 기호가 포함 되어 있는 경우에도 BSCMAKE의 [/El 옵션](bscmake-options.md) 을 사용 하 여 .bsc 파일에서 해당 기호를 생략할 수 있습니다.`.`

전체 컴파일을 수행 하지 않고 .sbr 파일을 만들 수 있습니다. 예를 들어 컴파일러에/Zs 옵션을 지정 하 여 구문 검사를 수행 하 고/FR 또는/Fr.를 지정 하는 경우에도 .sbr 파일을 생성할 수 있습니다.

.Sbr 파일을 처음으로 압축 하 여 참조 되지 않은 정의를 제거 하는 경우 빌드 프로세스를 보다 효율적으로 수행할 수 있습니다. 컴파일러는 .sbr 파일을 자동으로 압축 합니다.

## <a name="see-also"></a>참고 항목

[빌드. .Bsc 파일](building-a-dot-bsc-file.md)
