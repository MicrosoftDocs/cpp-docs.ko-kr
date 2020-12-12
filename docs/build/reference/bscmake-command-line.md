---
description: '자세한 정보: BSCMAKE 명령줄'
title: BSCMAKE 명령줄
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: a0d6cb81fb207c30cd89fbfe3a988380a865a399
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182660"
---
# <a name="bscmake-command-line"></a>BSCMAKE 명령줄

> [!WARNING]
> BSCMAKE는 Visual Studio와 함께 설치되지만 더 이상 IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 및 기호 정보는 자동으로 솔루션 폴더의 SQL Server .sdf 파일에 저장됩니다.

BSCMAKE를 실행 하려면 다음 명령줄 구문을 사용 합니다.

```
BSCMAKE [options] sbrfiles
```

옵션은 명령줄의 필드에만 나타날 수 있습니다 `options` .

*Sbrfiles* 필드는 컴파일러 또는 어셈블러에서 만든 .sbr 파일을 하나 이상 지정 합니다. .Sbr 파일의 이름을 공백이 나 탭으로 구분 합니다. 확장을 지정 해야 합니다. 기본값은 없습니다. 파일 이름으로 경로를 지정할 수 있으며 운영 체제 와일드 카드 (및?)를 사용할 수 있습니다 \* .

증분 빌드 중에 원래 빌드에 포함 되지 않은 새 .sbr 파일을 지정할 수 있습니다. 모든 기여를 찾아보기 정보 파일에 유지 하려면 .bsc 파일을 만드는 데 원래 사용 된 모든 .sbr 파일 (잘린 파일 포함)을 지정 해야 합니다. .Sbr 파일을 생략 하면 찾아보기 정보 파일에 대 한 해당 파일의 기여는 제거 됩니다.

전체 빌드에 대해 잘린 .sbr 파일을 지정 하지 마십시오. 전체 빌드에는 지정 된 모든 .sbr 파일의 기여를 요구 합니다. 전체 빌드를 수행 하기 전에 프로젝트를 다시 컴파일하고 비어 있는 각 파일에 대 한 새 .sbr 파일을 만듭니다.

다음 명령은 BSCMAKE를 실행 하 여 세 개의 .sbr 파일에서 기본 .bsc 라는 파일을 빌드합니다.

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

관련 정보는 [Bscmake 명령 파일](bscmake-command-file-response-file.md) 및 [bscmake 옵션](bscmake-options.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[BSCMAKE 참조](bscmake-reference.md)
