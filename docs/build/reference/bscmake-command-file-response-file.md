---
description: '자세한 정보: BSCMAKE 명령 파일 (지시 파일)'
title: BSCMAKE 명령 파일(지시 파일)
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: 4bb321cd7aa705d7e33d0f539ab3e0aa2e3cb8bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187158"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE 명령 파일(지시 파일)

> [!WARNING]
> BSCMAKE는 Visual Studio와 함께 설치되지만 더 이상 IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 및 기호 정보는 자동으로 솔루션 폴더의 SQL Server .sdf 파일에 저장됩니다.

명령 파일에서 명령줄 입력의 일부 또는 전부를 제공할 수 있습니다. 다음 구문을 사용 하 여 명령 파일을 지정 합니다.

```
BSCMAKE @filename
```

명령 파일은 하나만 허용 됩니다. *파일 이름* 으로 경로를 지정할 수 있습니다. *Filename* 앞에 at 기호 ()를 붙입니다 **\@** . BSCMAKE는 확장을 가정 하지 않습니다. 명령줄에서 *파일 이름* 뒤에 추가 *sbrfiles* 을 지정할 수 있습니다. 명령 파일은 명령줄에서 지정 하는 것과 동일한 순서로 BSCMAKE에 대 한 입력을 포함 하는 텍스트 파일입니다. 하나 이상의 공백, 탭 또는 줄 바꿈 문자를 사용 하 여 명령줄 인수를 구분 합니다.

다음 명령은 명령 파일을 사용 하 여 BSCMAKE를 호출 합니다.

```
BSCMAKE @prog1.txt
```

다음은 샘플 명령 파일입니다.

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>참고 항목

[BSCMAKE 참조](bscmake-reference.md)
