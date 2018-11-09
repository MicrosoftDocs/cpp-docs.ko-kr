---
title: 문자 시퀀스
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: dea24a2ae5887ea8c0111d8251ba4d9d03ccba0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489663"
---
# <a name="character-sequences"></a>문자 시퀀스

**ANSI 3.8.2** 소스 파일 문자 시퀀스의 매핑

전처리기 문은 이스케이프 시퀀스가 지원되지 않는 경우를 제외하고 소스 파일 문과 같은 문자 설정을 사용합니다.

따라서 include 파일에 대한 경로를 지정하려면 백슬래시를 하나만 사용해야 합니다.

```
#include "path1\path2\myfile"
```

소스 코드 내에서는 두 개의 백슬래시가 필요합니다.

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>참고 항목

[전처리 지시문](../c-language/preprocessing-directives.md)