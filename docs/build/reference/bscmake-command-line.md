---
title: BSCMAKE 명령줄
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: a5a1e8f8e1d022fab9dc1bf4f67713302c11f758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446724"
---
# <a name="bscmake-command-line"></a>BSCMAKE 명령줄

BSCMAKE를 실행 하려면 다음 명령줄 구문을 사용 합니다.

```
BSCMAKE [options] sbrfiles
```

옵션에만 나타날 수 있습니다는 `options` 명령줄에서 필드입니다.

합니다 *sbrfiles* 필드 컴파일러 또는 어셈블러에 의해 생성 된 하나 이상의.sbr 파일을 지정 합니다. .Sbr 파일의 이름은 공백이 나 탭으로 구분 합니다. 확장명을 지정 해야 기본값은 없습니다. 에 파일 이름을 사용 하 여 경로 지정할 수 있으며 운영 체제 와일드 카드를 사용할 수 있습니다 (\* 및?).

증분 빌드를 하는 동안 원래 빌드에 포함 되지 않은 새.sbr 파일을 지정할 수 있습니다. 찾아보기 정보 파일을 유지 하는 모든 기여를 하려는 경우에 모든.sbr 파일이 잘리지 파일 등.bsc 파일을 만드는 데 사용 된 원래는 지정 해야 합니다. .Sbr 파일을 생략 하는 경우 찾아보기 정보 파일에는 해당 파일의 작성 글 제거 됩니다.

전체 빌드 잘린된.sbr 파일을 지정 하지 마십시오. 전체 빌드를 모든 지정 된.sbr 파일 정보를 필요로 합니다. 전체 빌드를 수행 하기 전에 프로젝트를 컴파일하고 비어 있는 각 파일에 대 한 새.sbr 파일을 만듭니다.

다음 명령을 세.sbr 파일에서 MAIN.bsc 라는 파일을 빌드하는 BSCMAKE를 실행 합니다.

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

관련 정보를 참조 하세요 [BSCMAKE 명령 파일](../../build/reference/bscmake-command-file-response-file.md) 하 고 [BSCMAKE 옵션](../../build/reference/bscmake-options.md)합니다.

## <a name="see-also"></a>참고 항목

[BSCMAKE 참조](../../build/reference/bscmake-reference.md)