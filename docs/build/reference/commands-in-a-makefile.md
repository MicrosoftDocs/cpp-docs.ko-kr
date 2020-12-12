---
description: '자세한 정보: 메이크파일의 명령'
title: 메이크파일의 명령
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: a4f3c6d3cc9b5d567548d7b3f2bd7679d492ebf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179085"
---
# <a name="commands-in-a-makefile"></a>메이크파일의 명령

설명 블록 또는 유추 규칙은 종속성이 만료 된 경우 실행할 명령 블록을 지정 합니다. NMAKE를 실행 하기 전에 각 명령이 표시 됩니다 (/S, 제외) **. 자동**, **! CMDSWITCHES** \@ 사용 됩니다. NMAKE는 설명 블록 뒤에 명령 블록이 오지 않는 경우 일치 하는 유추 규칙을 찾습니다.

명령 블록에는 각각 별도의 줄에 있는 명령이 하나 이상 포함 되어 있습니다. 종속성 또는 규칙과 명령 블록 사이에는 빈 줄이 표시 되지 않습니다. 그러나 공백이 나 탭만 포함 하는 줄이 표시 될 수 있습니다. 이 줄은 null 명령으로 해석 되며 오류가 발생 하지 않습니다. 명령줄 사이에 빈 줄을 사용할 수 있습니다.

명령줄은 하나 이상의 공백이 나 탭으로 시작 합니다. 백슬래시 (\) 뒤에 줄 바꿈 문자를 입력 하면 명령에서 공백으로 해석 됩니다. 줄의 끝에 백슬래시를 사용 하 여 명령을 다음 줄로 계속 합니다. NMAKE는 공백이 나 탭을 비롯 한 다른 문자가 백슬래시 뒤에 오면 백슬래시를 문자 그대로 해석 합니다.

뒤에 세미콜론이 오는 명령 (;) 는 명령 블록이 다음에 있는지 여부에 관계 없이 종속성 줄 또는 유추 규칙에 나타날 수 있습니다.

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

[명령 한정자](command-modifiers.md)

[파일 이름 부분 구문](filename-parts-syntax.md)

[메이크파일의 인라인 파일](inline-files-in-a-makefile.md)

## <a name="see-also"></a>참고 항목

[NMAKE 참조](nmake-reference.md)
