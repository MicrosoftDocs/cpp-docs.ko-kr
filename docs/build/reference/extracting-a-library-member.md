---
description: '자세한 정보: 라이브러리 멤버 추출'
title: 라이브러리 멤버 추출
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 8797db6baa08fc36cf288f5b23d73ff730edd973
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192319"
---
# <a name="extracting-a-library-member"></a>라이브러리 멤버 추출

LIB를 사용 하 여 기존 라이브러리의 멤버 복사본을 포함 하는 개체 (.obj) 파일을 만들 수 있습니다. 멤버의 복사본을 추출 하려면 다음 구문을 사용 합니다.

```
LIB library /EXTRACT:member /OUT:objectfile
```

이 명령은 라이브러리의 복사본을 포함 하는 *objectfile* 이라는 .obj 파일을 만듭니다 `member` .  `member`이름은 대/소문자를 구분 합니다. 단일 명령에서 하나의 멤버만 추출할 수 있습니다. /OUT 옵션은 필수입니다. 기본 출력 이름이 없습니다. *Objectfile* 이라는 파일이 지정 된 디렉터리 (또는 *objectfile* 에 디렉터리가 지정 되지 않은 경우 현재 디렉터리)에 이미 있는 경우 추출 된 *objectfile* 이 기존 파일을 대체 합니다.

## <a name="see-also"></a>참고 항목

[LIB 참조](lib-reference.md)
