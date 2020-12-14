---
description: '자세한 정보: 심각한 오류 C1052'
title: 심각한 오류 C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: 818210cc4c3658167de30b9e666c600695389330
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251741"
---
# <a name="fatal-error-c1052"></a>심각한 오류 C1052

> 프로그램 데이터베이스 파일 '*filename*'이 (가)/debug: fastlink;을 (를) 사용 하 여 링커에 의해 생성 되었습니다. 컴파일러가 이러한 PDB 파일을 업데이트할 수 없습니다. 다른 PDB 파일 이름을 지정 하려면 삭제 하거나/Fd를 사용 하십시오.

컴파일러는 [/debug: fastlink](../../build/reference/debug-generate-debug-info.md) 옵션이 지정 된 경우 링커에서 생성 되는 동일한 PDB (프로그램 데이터베이스) 파일을 업데이트할 수 없습니다. 일반적으로 컴파일러에서 생성 된 PDB 파일 및 링커 생성 PDB 파일의 이름이 다릅니다. 그러나 동일한 이름을 사용 하도록 설정 된 경우이 오류가 발생할 수 있습니다.

이 문제를 해결 하려면 다시 컴파일하기 전에 PDB 파일을 명시적으로 삭제 하거나 컴파일러 생성 및 링커 생성 PDB 파일에 대해 다른 이름을 만들 수 있습니다.

명령줄에서 컴파일러 생성 PDB 파일 이름을 지정 하려면 [/fd](../../build/reference/fd-program-database-file-name.md) 컴파일러 옵션을 사용 합니다. IDE에서 컴파일러 생성 PDB 파일 이름을 지정 하려면 프로젝트에 대 한 **속성 페이지** 대화 상자를 열고 **구성 속성**, **C/c + +**, **출력 파일** 페이지에서 **프로그램 데이터베이스 파일 이름** 속성을 설정 합니다. 기본적으로이 속성은 `$(IntDir)vc$(PlatformToolsetVersion).pdb` 입니다.

또는 링커 생성 PDB 파일 이름을 설정할 수 있습니다. 명령줄에서 링커 생성 PDB 파일 이름을 지정 하려면 [/pdb](../../build/reference/pdb-use-program-database.md) 링커 옵션을 사용 합니다. IDE에서 링커 생성 PDB 파일 이름을 지정 하려면 프로젝트에 대 한 **속성 페이지** 대화 상자를 열고 **구성 속성**, **링커**, **디버깅** 페이지에서 **프로그램 데이터베이스 파일 생성** 속성을 설정 합니다. 기본적으로 이 속성은 `$(OutDir)$(TargetName).pdb`로 설정됩니다.
